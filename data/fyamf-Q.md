## Issue1
When the buffer config is set through `setBufferConfig`, it is not checked that `bufferConfig_.max` be lower than `bufferConfig_.threshold`.
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L947
```solidity
function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
        if (!isDelayBufferable) revert NotDelayBufferable();
        if (!DelayBuffer.isValidBufferConfig(bufferConfig_)) revert BadBufferConfig();

        if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {
            buffer.bufferBlocks = bufferConfig_.max;
        }
        if (buffer.bufferBlocks < bufferConfig_.threshold) {
            buffer.bufferBlocks = bufferConfig_.threshold;
        }
        buffer.max = bufferConfig_.max;
        buffer.threshold = bufferConfig_.threshold;
        buffer.replenishRateInBasis = bufferConfig_.replenishRateInBasis;

        // if all delayed messages are read, the buffer is considered synced
        if (bridge.delayedMessageCount() == totalDelayedMessagesRead) {
            buffer.update(uint64(block.number));
        }
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L847

If `threshold` is set higher than `max`, then during updating the buffer, the following line will always return `max` which is incorrect.
```solidity
function calcBuffer(
        uint256 start,
        uint256 end,
        uint256 buffer,
        uint256 sequenced,
        uint256 threshold,
        uint256 max,
        uint256 replenishRateInBasis
    ) internal pure returns (uint256) {
        //....
        if (buffer > threshold) {
                // saturating above at the max
                return buffer > max ? max : buffer;
            }
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/DelayBuffer.sol#L58

## Issue2
If the batch poster is an EOA and calls `addSequencerL2Batch` or `addSequencerL2BatchDelayProof`, the `isFromOrigin` is set to **false** when the internal faunction `addSequencerL2BatchFromCalldataImpl` is invoked.
```solidity
function addSequencerL2Batch(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) external override refundsGas(gasRefunder, IReader4844(address(0))) {
        //....
        addSequencerL2BatchFromCalldataImpl(
            sequenceNumber,
            data,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount,
            false
        );
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L577
```solidity
function addSequencerL2BatchDelayProof(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        IGasRefunder gasRefunder,
        uint256 prevMessageCount,
        uint256 newMessageCount,
        DelayProof calldata delayProof
    ) external refundsGas(gasRefunder, IReader4844(address(0))) {
        //.....

        delayProofImpl(afterDelayedMessagesRead, delayProof);
        addSequencerL2BatchFromCalldataImpl(
            sequenceNumber,
            data,
            afterDelayedMessagesRead,
            prevMessageCount,
            newMessageCount,
            false
        );
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L601

In this function, since the parameter `isFromOrigin` is **false**, the `calldataLengthPosted` is considered as zero when the internal function `addSequencerL2BatchImpl` is invoked.
```solidity
function addSequencerL2BatchFromCalldataImpl(
        uint256 sequenceNumber,
        bytes calldata data,
        uint256 afterDelayedMessagesRead,
        uint256 prevMessageCount,
        uint256 newMessageCount,
        bool isFromOrigin
    ) internal {
        //...
         (
            uint256 seqMessageIndex,
            bytes32 beforeAcc,
            bytes32 delayedAcc,
            bytes32 afterAcc
        ) = addSequencerL2BatchImpl(
                dataHash,
                afterDelayedMessagesRead,
                isFromOrigin ? data.length : 0,
                prevMessageCount,
                newMessageCount
            );
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L532

As a result, the batch poster will not be reimbursed, as shows in the following line:

```solidity
function addSequencerL2BatchImpl(
        bytes32 dataHash,
        uint256 afterDelayedMessagesRead,
        uint256 calldataLengthPosted,
        uint256 prevMessageCount,
        uint256 newMessageCount
    )
        internal
        returns (
            uint256 seqMessageIndex,
            bytes32 beforeAcc,
            bytes32 delayedAcc,
            bytes32 acc
        )
    {
        //....
        if (calldataLengthPosted > 0 && !isUsingFeeToken) {
            // only report batch poster spendings if chain is using ETH as native currency
            submitBatchSpendingReport(dataHash, seqMessageIndex, block.basefee, 0);
        }
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L818

It is recommended to enforce that the batch poster not be an EOA `require(msg.sender != tx.origin,"should not be an EOA");` when is calls `addSequencerL2Batch` or `addSequencerL2BatchDelayProof`. So, an EOA batch poster must only call `addSequencerL2BatchFromOrigin` or `addSequencerL2BatchFromOriginDelayProof` to be reimbursed.

## Issue3

When a batch poster adds an L2 batch, it will be reimbursed by posting the refund tx. This is done by calling the function `submitBatchSpendingReport` during adding sequencer L2 batch from blob or adding sequence L2 batch from calldata.
```solidity
function addSequencerL2BatchImpl(
        bytes32 dataHash,
        uint256 afterDelayedMessagesRead,
        uint256 calldataLengthPosted,
        uint256 prevMessageCount,
        uint256 newMessageCount
    )
        internal
        returns (
            uint256 seqMessageIndex,
            bytes32 beforeAcc,
            bytes32 delayedAcc,
            bytes32 acc
        )
    {
        //......

        if (calldataLengthPosted > 0 && !isUsingFeeToken) {
            // only report batch poster spendings if chain is using ETH as native currency
            submitBatchSpendingReport(dataHash, seqMessageIndex, block.basefee, 0);
        }
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L820

```solidity
function addSequencerL2BatchFromBlobsImpl(
        uint256 sequenceNumber,
        uint256 afterDelayedMessagesRead,
        uint256 prevMessageCount,
        uint256 newMessageCount
    ) internal {
        //......
        if (msg.sender == tx.origin && !isUsingFeeToken) {
            submitBatchSpendingReport(dataHash, seqMessageIndex, block.basefee, blobGas);
        }
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L508

In this function, the refund tx is added to the delayed inbox accumulator, to be sequenced by the sequencer later.

```solidity
function submitBatchSpendingReport(
        bytes32 dataHash,
        uint256 seqMessageIndex,
        uint256 gasPrice,
        uint256 extraGas
    ) internal {
        //....
        uint256 msgNum = bridge.submitBatchSpendingReport(
            batchPoster,
            keccak256(spendingReportMsg)
        );
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/SequencerInbox.sol#L783
```solidity
function submitBatchSpendingReport(address sender, bytes32 messageDataHash)
        external
        onlySequencerInbox
        returns (uint256)
    {
        return
            addMessageToDelayedAccumulator(
                L1MessageType_batchPostingReport,
                sender,
                uint64(block.number),
                uint64(block.timestamp), // solhint-disable-line not-rely-on-time,
                block.basefee,
                messageDataHash
            );
    }
```
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/bridge/AbsBridge.sol#L141

Later, when the batch poster adds a new L2 batch, he includes this refund tx to be sequenced. Again, for including this tx, he will be reimbursed by adding the a new refund tx to the delayed inbox accumulator. In other words, the batch poster is refunded on sequencing a refund tx. So, it is kind of a loop. This leads to waste of resources. 

For example the batch poster should be refunded 10 token. So, this refund tx is added to the inbox. Later the batch poster to sequence this 10 token refund tx, he must be refunded another 3 token. So, this 3 token refund tx is again added to the inbox. Later to sequence this 3 token refund tx, he is refunded another amount. 

