# ARBITRUM QA REPORT

## Summary

| No | Title |
| --- | --- |
| [L-01] | No way to enable `ValidatorWhiteList` after disabling in `RollupUserLogic` |
| [L-02] | Upgrade of Rollups can be DOSsed by predeploying a contract to the computed CREATE2 address  |
| [L-03] | It is possible to bloat the inbox with spam messages by forceInclusion using a low enough `l1BlockAndTime` |
| [L-04] | The sync status of a Buffer can be manipulated by forceInclusion with low `l1BlockAndTime` |
| [L-05] | It may be possible to claim an edge multiple times and manually increase timerCache |

## Low Findings

### [L-01]  No way to enable `ValidatorWhiteList` after disabling in `RollupUserLogic`

- Lines of Code: https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L20-L22
#### Impact
Only validators are expected to create and confirm assertions on the arbitrum rollups, and also create edges in the challenge manager. Most core functions rely on these validators to stake, create assertions and confirm assertions. 
```
 modifier onlyValidator() {
        require(isValidator[msg.sender] || validatorWhitelistDisabled, "NOT_VALIDATOR");
        _;
    }
```
However, if a fork occurs or if validators go afk i.e. no new assertion is confirmed after a number of blocks, this validator whitelist can be disabled by any user.
```
 function removeWhitelistAfterValidatorAfk() external {
        require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
        require(_validatorIsAfk(), "VALIDATOR_NOT_AFK");
        validatorWhitelistDisabled = true;
    }
```
This would allow any external user to create assertions, create edges and confirm assertions. However, there is no easy way to enable the validator whitelist after being disabled unless the contracts are upgraded or redeployed.

#### Recommendation
1. Allow a trusted entity to re-enable whitelist after some conditions are met.

### [L-02] Upgrade of Rollups can be DOSsed by predeploying a contract to the computed CREATE2 address 

- Lines of Code: https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L498-L501
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L498-L501

#### Impact
During upgrade of the Bold contracts, the new `Rollup` is created using the Create2Upgradeable method which allows deployment of smart contracts with deterministic addresses. 
```
src: BOLDUpgradeAction.perform

        bytes32 rollupSalt = keccak256(abi.encode(config));
        address expectedRollupAddress =
 @>     Create2Upgradeable.computeAddress(rollupSalt, keccak256(type(RollupProxy).creationCode));
..................................................
@>      RollupProxy rollup = new RollupProxy{salt: rollupSalt}();
```
However, the salt used in computation of this new address is not unique and can be easily computed. It relies on encoding the config which is a struct of the upgrade params.
```
src: BoldUpgradeAction::createConfig

    return Config({
            confirmPeriodBlocks: CONFIRM_PERIOD_BLOCKS,
            stakeToken: STAKE_TOKEN,
            baseStake: STAKE_AMOUNT,
            wasmModuleRoot: ROLLUP_READER.wasmModuleRoot(),
            owner: address(this), // upgrade executor is the owner
            loserStakeEscrow: L1_TIMELOCK, // additional funds get sent to the l1 timelock
            chainId: CHAIN_ID,
            chainConfig: "", // we can use an empty chain config it wont be used in the rollup initialization because we check if the rei is already connected there
            miniStakeValues: ConstantArrayStorage(MINI_STAKE_AMOUNTS_STORAGE).array(),
            sequencerInboxMaxTimeVariation: maxTimeVariation,
            layerZeroBlockEdgeHeight: BLOCK_LEAF_SIZE,
            layerZeroBigStepEdgeHeight: BIGSTEP_LEAF_SIZE,
            layerZeroSmallStepEdgeHeight: SMALLSTEP_LEAF_SIZE,
            genesisAssertionState: genesisAssertionState,
            genesisInboxCount: inboxMaxCount,
            anyTrustFastConfirmer: ANY_TRUST_FAST_CONFIRMER,
            numBigStepLevel: NUM_BIGSTEP_LEVEL,
            challengeGracePeriodBlocks: CHALLENGE_GRACE_PERIOD_BLOCKS,
            bufferConfig: bufferConfig
        });
```
These parameters are easily readable from the `BOLDUpgradeAction` contract and therefore the CREATE2 address can be computed from these parameters. 
By deploying a contract to that address, an attacker can DOS the creation of the new Rollup during the upgrade execution

#### Recommendation
Include a unique parameter such as a nonce into the salt to make computation more  prohibitive for an attacker.

### [L-03]  It is possible to bloat the inbox with spam messages by forceInclusion using a low enough `l1BlockAndTime`

- Lines of Code: https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L337

#### Impact
Delayed messages can be forcefully included into the `SequencerInbox` through `SequencerInbox::forceInclusion`.

```
 function forceInclusion(
        uint256 _totalDelayedMessagesRead,
        uint8 kind,
        uint64[2] calldata l1BlockAndTime,
        uint256 baseFeeL1,
        address sender,
        bytes32 messageDataHash
    ) external { ............... }
```
Within this function there is a check for if the Sequencer update window has passed. This checks the user supplied `l1BlockAndTime[0]` and delayBlocks against the current block.number
```
        // Can only force-include after the Sequencer-only window has expired.
        if (l1BlockAndTime[0] + delayBlocks_ >= block.number) revert ForceIncludeBlockTooSoon();
```

However, since `l1BlockAndTime[0]` is usersupplied, the user can enter a low enough l1BlockAndTime[0] such that when  added to `delayBlocks_`, it is always less than the current block.number. 
This would allow the user to force include any message even before sequencer update time has passed, and potentially bloat the sequencerInbox.

#### Recommendation
1. Require that `l1BlockAndTime[0]` supplied by the user is checked against a min value.

### [L-04] The sync and updatable status of a Buffer can be manipulated by forceInclusion with low `l1BlockAndTime` 

- Lines of Code:  https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L73
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L104-L105
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L112

#### Impact
By setting a low `l1BlockAndTime[0]` in `SequencerInbox::forceInclusion`, a user can manually manipulate the `Buffer::prevBlockNumber`. 

```
src: DelayedBuffer.sol

  function update(BufferData storage self, uint64 blockNumber) internal {
        self.bufferBlocks = calcPendingBuffer(self, blockNumber);

        // store a new starting reference point
        // any buffer updates will be applied retroactively in the next batch post
@>      self.prevBlockNumber = blockNumber;
        self.prevSequencedBlockNumber = uint64(block.number);
    }

```
This parameter is necessary to identify if a buffer is synced or updatable. 

```
   function isSynced(BufferData storage self) internal view returns (bool) {
@>        return block.number - self.prevBlockNumber <= self.threshold;
    }

```
The user can therefore manipulate the current BufferConfig to show synced or updatable at anytime even when it shouldn't be. 

#### Recommendation
1. Before updating the buffer with the `l1BlockAndTime[0]`, ensure this value meets some requirements such as a minimum value. 

### [L-05] It may be possible to claim an edge multiple times and manually increase timerCache

- Lines of Code: https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L520-L530

#### Impact
Creators of an edge can update the timers for their edge by claiming an edge which is one step below their created edge. 
```
function updateTimerCacheByClaim(
        EdgeStore storage store,
        bytes32 edgeId,
        bytes32 claimingEdgeId,
        uint8 numBigStepLevel
    ) internal returns (bool, uint256) {
        // calculate the time unrivaled without inheritance
        uint256 totalTimeUnrivaled = timeUnrivaled(store, edgeId);
        checkClaimIdLink(store, edgeId, claimingEdgeId, numBigStepLevel);
@>        totalTimeUnrivaled += store.edges[claimingEdgeId].totalTimeUnrivaledCache;
@>        return updateTimerCache(store, edgeId, totalTimeUnrivaled);
    }
```
Each time an edge is claimed the timer cache is updated with the newly incremented `totalTimeUnrivaled`. 
However, there is no check for if that claim has been claimed by that edge. 

- https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L689C5-L701C41

Everytime this function is called, the totalTimeUnrivaled of the edgeId is increased. With sufficient time, the edge can be claimed to be the winning edge

#### Recommendation
1. Include a check for if that claimEdge has already been claimed within `checkClaimIdLink`
