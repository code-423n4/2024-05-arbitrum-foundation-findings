
# QA for Arbitrum

## Table of Contents

| Issue ID | Description |
| -------- | ----------- |
| [QA-01](#qa-01-inconsistent-delay-period-calculation-in-forceinclusion-function) | Inconsistent Delay Period Calculation in `forceInclusion` Function |
| [QA-02](#qa-02-potential-race-condition-in-setconfirmedrival-function) | Potential Race Condition in `setConfirmedRival` Function |
| [QA-03](#qa-03-potential-manipulation-of-claimedassertionunrivaledblocks-in-confirmedgebytime-function) | Potential Manipulation of `claimedAssertionUnrivaledBlocks` in `confirmEdgeByTime` Function |
| [QA-04](#qa-04-potential-hash-collision-in-setvalidkeyset-function-due-to-xor-operation) | Potential Hash Collision in `setValidKeyset` Function Due to XOR Operation |
| [QA-05](#qa-05-redundant-and-inefficient-use-of-mostsignificantbit-in-leastsignificantbit-function) | Redundant and Inefficient Use of `mostSignificantBit` in `leastSignificantBit` Function |
| [QA-06](#qa-06-strict-level-requirement-in-appendcompletesubtree-function) | Strict Level Requirement in `appendCompleteSubTree` Function |
| [QA-07](#qa-07-fix-natspec-multiple-instances) | Fix Natspec _(Multiple Instances)_ |
| [QA-08](#qa-08-fix-typos-multiple-instances) | Fix Typos _(Multiple Instances)_ |





## [QA-01]  Inconsistent Delay Period Calculation in `forceInclusion` Function

The `forceInclusion` function may incorrectly revert with `ForceIncludeBlockTooSoon` due to an inconsistent delay period calculation. This can prevent the forceful inclusion of delayed messages even when the sequencer-only window has expired, potentially leading to delays in the protocol.

Look at this part: 
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L308-L314

```solidity
if (isDelayBufferable) {
    // proactively apply any pending delay buffer updates before the force included message l1BlockAndTime
    buffer.update(l1BlockAndTime[0]);
    delayBlocks_ = delayBufferableBlocks(buffer.bufferBlocks);
}
// Can only force-include after the Sequencer-only window has expired.
if (l1BlockAndTime[0] + delayBlocks_ >= block.number) revert ForceIncludeBlockTooSoon();
```

The `delayBlocks_` value is recalculated based on the buffer state at the time of the force inclusion call. This recalculated value might somewhat not accurately reflect the intended delay period for the message being force-included, especially if the buffer state has changed since the message was originally delayed.

#### Recommended Mitigation Steps
To address this issue, ensure that the delay period used for the force inclusion check is consistent with the delay period that was in effect when the message was originally delayed. One way to achieve this is to store the delay period for each delayed message when it is first delayed and use that stored value for the force inclusion check. 








## [QA-02] Potential Race Condition in `setConfirmedRival` Function

#### Impact
The `setConfirmedRival` function could theoretically be susceptible to a race condition when two transactions attempt to confirm rival edges simultaneously. This could lead to both transactions passing the check and setting their respective edges as confirmed, which violates the intended logic that only one edge can be confirmed.

## Proof of Concept
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L662-L669

```solidity
function setConfirmedRival(EdgeStore storage store, bytes32 edgeId) internal {
    bytes32 mutualId = store.edges[edgeId].mutualId();
    bytes32 confirmedRivalId = store.confirmedRivals[mutualId];
    if (confirmedRivalId != bytes32(0)) {
        revert RivalEdgeConfirmed(edgeId, confirmedRivalId);
    }
    store.confirmedRivals[mutualId] = edgeId;
}
```

#### Recommended Mitigation Steps:
To mitigate this race condition concern, ensure that the check and set operation is atomic. Given the single-threaded nature of the EVM, the current implementation is already atomic. However, if there are more complex operations or multiple steps involved, you would need to ensure atomicity more explicitly. Something like this:

```solidity
function setConfirmedRival(EdgeStore storage store, bytes32 edgeId) internal {
    bytes32 mutualId = store.edges[edgeId].mutualId();
    bytes32 confirmedRivalId = store.confirmedRivals[mutualId];
    if (confirmedRivalId != bytes32(0)) {
        revert RivalEdgeConfirmed(edgeId, confirmedRivalId);
    }
    // Set the confirmed rival in a single step to avoid race conditions
    store.confirmedRivals[mutualId] = edgeId;
}
```







## [QA-03] Potential Manipulation of `claimedAssertionUnrivaledBlocks` in `confirmEdgeByTime` Function

The `confirmEdgeByTime` function in  `EdgeChallengeManagerLib` is vulnerable to manipulation. A caller can provide an arbitrarily large value for the `claimedAssertionUnrivaledBlocks` parameter to artificially inflate the total unrivaled time, allowing an edge to be confirmed prematurely. This could undermine the integrity of the challenge process, allowing edges to be confirmed before they have legitimately reached the required confirmation threshold.

## Proof of Concept
The issue lies in the `confirmEdgeByTime` function, which adds the `claimedAssertionUnrivaledBlocks` to the `totalTimeUnrivaled` without any validation. Here is the relevant part of the code:

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L723-L752

```solidity
function confirmEdgeByTime(
    EdgeStore storage store,
    bytes32 edgeId,
    uint64 claimedAssertionUnrivaledBlocks,
    uint64 confirmationThresholdBlock
) internal returns (uint256) {
    if (!store.edges[edgeId].exists()) {
        revert EdgeNotExists(edgeId);
    }

    uint256 totalTimeUnrivaled = timeUnrivaledTotal(store, edgeId);

    // Potential issue: blindly adding claimedAssertionUnrivaledBlocks
    totalTimeUnrivaled += claimedAssertionUnrivaledBlocks;

    if (totalTimeUnrivaled < confirmationThresholdBlock) {
        revert InsufficientConfirmationBlocks(totalTimeUnrivaled, confirmationThresholdBlock);
    }

    // Confirm the edge
    store.edges[edgeId].setConfirmed();

    // Also checks that no other rival has been confirmed
    setConfirmedRival(store, edgeId);

    return totalTimeUnrivaled;
}
```

Let's consider this scenario: 
1. Assume the `totalTimeUnrivaled` for an edge is 100 blocks.
2. The `confirmationThresholdBlock` is set to 1000 blocks.
3. Normally, this edge would not be eligible for confirmation.
4. However, if a caller provides a `claimedAssertionUnrivaledBlocks` value of 900 or more, it would push the `totalTimeUnrivaled` above the threshold, allowing the edge to be confirmed prematurely.

#### Recommended Mitigation Steps
Validate the `claimedAssertionUnrivaledBlocks` parameter to ensure it represents a valid and reasonable value. We can do this by checking that the value is within an acceptable range or verifying it against the actual unrivaled time of the claimed assertion.







## [QA-04] Potential Hash Collision in `setValidKeyset` Function Due to XOR Operation

The current implementation of the `setValidKeyset` function in the `SequencerInbox` contract can lead to hash collisions. Specifically, two different `keysetBytes` values could produce the same `ksHash` if their hashes differ only in the most significant bit. This can result in a valid keyset being incorrectly invalidated or a new keyset being incorrectly marked as already valid.

#### Proof of Concept

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L904-L905
The issue lies in the calculation of `ksHash` using the XOR operation with `(1 << 255)`:

```solidity
uint256 ksWord = uint256(keccak256(bytes.concat(hex"fe", keccak256(keysetBytes))));
bytes32 ksHash = bytes32(ksWord ^ (1 << 255));
```

This operation can lead to collisions. For example, if `keccak256(keysetBytes1)` results in a hash where the most significant bit is `0` and `keccak256(keysetBytes2)` results in a hash where the most significant bit is `1`, the XOR operation will produce the same `ksHash` for both `keysetBytes1` and `keysetBytes2`.

#### Recommended Mitigation Steps
So as to avoid this issue, we can use a different method to ensure the uniqueness of the `ksHash`. One approach may be to avoid the XOR operation altogether and use the direct hash of the concatenated bytes





## [QA-05] Redundant and Inefficient Use of `mostSignificantBit` in `leastSignificantBit` Function

#### Impact
The `leastSignificantBit` function calls the `mostSignificantBit` function on a value (`isolated`) that is guaranteed to have only one bit set. This makes the call to `mostSignificantBit` redundant and inefficient, as it performs unnecessary operations to determine the position of the single bit.

## Proof of Concept

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L14-L22

```solidity
function leastSignificantBit(uint256 x) internal pure returns (uint256 lsb) {
    require(x > 0, "Zero has no significant bits");

    // isolate the least sig bit
    uint256 isolated = ((x - 1) & x) ^ x;
    
    // since we removed all higher bits, least sig == most sig
    return mostSignificantBit(isolated);
}
```

The `mostSignificantBit` function is designed to find the most significant bit in a number with multiple bits set, which is unnecessary for a number with only one bit set.

#### Recommended Mitigation Steps
Replace the call to `mostSignificantBit` with a more efficient method to find the position of the single bit in `isolated`. Instead of calling mostSignificantBit, we can directly compute the position of the isolated bit using a loop or bitwise operations.







## [QA-06] Strict Level Requirement in `appendCompleteSubTree` Function

#### Impact
The current implementation of the `appendCompleteSubTree` function enforces a strict requirement that the level must be less than the length of the merkle expansion (`me`). This requirement might be too strict and can prevent valid appending operations, potentially causing the function to revert unnecessarily.

#### Proof of Concept
Look at this part of the code:
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L170

```solidity
require(level < me.length, "Level greater than highest level of current expansion");
```

According to the NatSpec comments, if `me` is empty, the function should append directly. However, if `me` is not empty, the function should allow appending at the level of the lowest complete subtree or below. The current requirement enforces that the level must be less than the length of `me`, which might not always be the case.

#### Recommended Mitigation Steps:
Modify the requirement to allow appending at the level of the lowest complete subtree or below:

```solidity
require(level <= me.length, "Level greater than highest level of current expansion");
```

This will ensure that the function can append at the level of the lowest complete subtree or below, as described in the NatSpec comments.







## [QA-07] Fix Natspec _(Multiple Instances)_

### First Instance: 
The NatSpec comment for the `smallStepHeight` parameter in the `confirmEdgeByOneStepProof` function contains an incorrect description. This can lead to confusion for developers and auditors trying to understand the function's behavior and the role of the `smallStepHeight` parameter.

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L765

##### Proof of Concept
The current NatSpec comment for the `smallStepHeight` parameter is:
```solidity
/// @param smallStepHeight The height of the zero layer levels of big step type
```

However, this should describe the height of the zero layer levels of the small step type, not the big step type.

##### Recommended Mitigation Steps:
Update the NatSpec comment for the `smallStepHeight` parameter to correctly describe its purpose. The corrected comment should be:
```solidity
/// @param smallStepHeight The height of the zero layer levels of small step type
```



### Second Instance: 
The NatSpec comment for the `mandatoryBisectionHeight` function inaccurately describes the function's implementation. 

##### Proof of Concept

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L573-L588

The current NatSpec comment states:
```solidity
/// @notice Given a start and an endpoint determine the bisection height
/// @dev    Returns the highest power of 2 in the differing lower bits of start and end
```

However, the function actually returns the highest power of 2 in the differing bits of `(end - 1)` and `start`.

Look at this:
```solidity
function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {
    if (end - start < 2) {
        revert HeightDiffLtTwo(start, end);
    }
    if (end - start == 2) {
        return start + 1;
    }

    uint256 diff = (end - 1) ^ start;
    uint256 mostSignificantSharedBit = UintUtilsLib.mostSignificantBit(diff);
    uint256 mask = type(uint256).max << mostSignificantSharedBit;
    return ((end - 1) & mask);
}
```

##### Recommended Mitigation Steps:
Update the NatSpec comments to accurately reflect the function's behavior:
```solidity
/// @notice Given a start and an endpoint determine the bisection height
/// @dev    Returns the highest power of 2 in the differing bits of (end - 1) and start
```


### Third Instance: 
The `isPowerOfTwo` function checks if a given number is a power of two. Here is the function for reference:

```solidity
function isPowerOfTwo(uint256 x) internal pure returns (bool) {
    // zero is not a power of 2
    if (x == 0) {
        return false;
    }

    // if x is a power of 2, then this will be 0111111
    uint256 y = x - 1;

    // if x is a power of 2 then y will share no bits with x
    return ((x & y) == 0);
}
```

The function is logically correct and efficiently checks if a number is a power of two. However, there is a minor issue in the comment:

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L333

```solidity
// if x is a power of 2, then this will be 0111111
```

This comment is misleading because it suggests a specific bit pattern that is not universally applicable. The correct explanation is that if `x` is a power of two, then `x - 1` will have all bits set to 1 up to the position of the highest bit in `x`. For example:

- If `x = 8` (which is `1000` in binary), then `x - 1 = 7` (which is `0111` in binary).
- If `x = 16` (which is `10000` in binary), then `x - 1 = 15` (which is `01111` in binary).

To make the comment more accurate, it can be updated as follows:

```solidity
// if x is a power of 2, then x - 1 will have all bits set to 1 up to the position of the highest bit in x
```

This change makes the comment clearer and more accurate. The function itself does not need any changes as it correctly implements the logic to check if a number is a power of two.










## [QA-08] Fix typos _(Multiple Instances)_

### First Instance:
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L13

`preveneted` should be corrected to `prevented`. Here is the corrected comment:

```solidity
/**
 * @notice  Messages are expected to be delayed up to a threshold, beyond which they are unexpected
 *          and deplete a delay buffer. Buffer depletion is prevented from decreasing too quickly by only
 *          depleting by as many blocks as elapsed in the delayed message queue.
 */
```


### Second Instance:
`sigificant` and `signficant` should be corrected to `significant`

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L13

```solidity
 /// @param x Cannot be zero, since zero that has no signficant bits
```


https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L28

```solidity
/// @param x Cannot be zero, since zero has no sigificant bits
```



### Third Instance:
`Leve` and `Storeage` should be corrected to `Level` and `Storage`

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L156


https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L221
