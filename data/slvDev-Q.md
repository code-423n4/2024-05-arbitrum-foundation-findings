## [01] `stakerCount` limited to 50 by design, with 3 external calls in a loop

Looping through a 50-element array with 3 external calls in each iteration may lead to gas exhaustion.

```solidity
src/rollup/BOLDUpgradeAction.sol
// if (stakerCount > 50) {
//    stakerCount = 50;
// }

350: for (uint64 i = 0; i < stakerCount; i++) {
// @> address stakerAddr = ROLLUP_READER.getStakerAddress(i);
// @> OldStaker memory staker = ROLLUP_READER.getStaker(stakerAddr);
// @> IOldRollupAdmin(address(OLD_ROLLUP)).forceRefundStaker(stakersToRefund);
```

### Recommendation

Consider lowering the number of iterations.

## [02] Using `uint64` for loop counter

Since `stakerCount` is limited to 50, using `uint64` for the loop counter is unnecessary.
You can safely use `uint8` or you can use `uint256` to avoid padding overhead.

```solidity
src/rollup/BOLDUpgradeAction.sol

350: for (uint64 i = 0; i < stakerCount; i++) {
```

### Recommendation

Consider using `uint8` or `uint256` for the loop counter.

## [03] `_maxDataSize` is not validated before assignment

Missing validation for `_maxDataSize` before assignment.

```solidity
src/bridge/SequencerInbox.sol

// `_maxDataSize` is not validated before assignment
140: constructor(
        uint256 _maxDataSize,
        IReader4844 reader4844_,
        bool _isUsingFeeToken,
        bool _isDelayBufferable
    ) {
```

### Recommendation

Add a check to ensure that the `_maxDataSize` is in the expected range.

## [04] `assert()` should only be used for tests

From [documentation](https://docs.soliditylang.org/en/v0.8.20/controstructures.html#panic-via-assert-and-error-via-require):

```text
The assert function creates an error of type Panic(uint256). The same error is created by the compiler in certain situations as listed below.
Assert should only be used to test for internal errors, and to check invariants. Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix. Language analysis tools can evaluate your contract to identify the conditions and function calls which will cause a Panic.
```

```solidity
src/bridge/SequencerInbox.sol

651: assert(header.length == HEADER_LENGTH)
```

```solidity
src/challengeV2/libraries/MerkleTreeLib.sol

340: assert(size <= postSize)
```

### Recommended

Consider using `require()` instead of `assert()`

## [05] `minimumAssertionPeriod` and `baseStake` variables are not limited

There are some missing limits when setting the `minimumAssertionPeriod` and `baseStake` variables.

```solidity
src/rollup/RollupAdminLogic.sol

205: minimumAssertionPeriod = newPeriod;
224: baseStake = newBaseStake;
```

### Recommendation

Consider adding a min/max limit for the state variables.

## [06] `block.number` on Arbitrum returns value close to (but not necessarily exactly) the L1 block number

Accessing block numbers within an Arbitrum smart contract (i.e., block.number in Solidity) will return a value close to (but not necessarily exactly) the L1 block number at which the sequencer received the transaction.

As a general rule, any timing assumptions a contract makes about block numbers and timestamps should be considered generally reliable in the longer term (i.e., on the order of at least several hours) but unreliable in the shorter term (minutes). (It so happens these are generally the same assumptions one should operate under when using block numbers directly on Ethereum!)

```solidity
src/bridge/DelayBuffer.sol

74: self.prevSequencedBlockNumber = uint64(block.number);
105: return block.number - self.prevBlockNumber <= self.threshold;
```

```solidity
src/bridge/SequencerInbox.sol

228: if (block.number > delayBlocks_) {
229: bounds.minBlockNumber = uint64(block.number) - delayBlocks_;
231: bounds.maxBlockNumber = uint64(block.number) + futureBlocks_;
314: if (l1BlockAndTime[0] + delayBlocks_ >= block.number) revert ForceIncludeBlockTooSoon();
863: buffer.update(uint64(block.number));
909: uint256 creationBlock = block.number;
```

```solidity
src/challengeV2/libraries/ChallengeEdgeLib.sol

120: createdAtBlock: uint64(block.number),
151: createdAtBlock: uint64(block.number),
254: edge.confirmedAtBlock = uint64(block.number);
```

```solidity
src/challengeV2/libraries/EdgeChallengeManagerLib.sol

552: return block.number - store.edges[edgeId].createdAtBlock;
```

```solidity
src/rollup/Assertion.sol

75: assertion.createdAtBlock = uint64(block.number);
87: self.firstChildBlock = uint64(block.number);
89: self.secondChildBlock = uint64(block.number);
```

```solidity
src/rollup/RollupAdminLogic.sol

24: rollupDeploymentBlock = block.number;
```

```solidity
src/rollup/RollupUserLogic.sol

57: return latestConfirmedAssertion.firstChildBlock + VALIDATOR_AFK_BLOCKS < block.number;
59: return latestConfirmedAssertion.createdAtBlock + VALIDATOR_AFK_BLOCKS < block.number;
110: require(block.number >= assertion.createdAtBlock + prevConfig.confirmPeriodBlocks, "BEFORE_DEADLINE");
125: block.number >= winningEdge.confirmedAtBlock + challengeGracePeriodBlocks,
205: uint256 timeSincePrev = block.number - getAssertionStorage(prevAssertion).createdAtBlock;
```

## [07] Use `_disableInitializers()` in Upgradeable contracts constructors

[\_disableInitializers()](https://docs.openzeppelin.com/contracts/4.x/api/proxy#Initializable-_disableInitializers--) was added in Contracts v4.6.0 as part of the reinitializers support.
The Caution note in [Initializer](https://docs.openzeppelin.com/contracts/4.x/api/proxy#Initializable) provides more details on why this is needed.

By putting it in the constructor, this prevents initialization of the implementation contract itself, as extra protection [to prevent an attacker from initializing it](https://forum.openzeppelin.com/t/uupsupgradeable-vulnerability-post-mortem/15680).

```solidity
src/rollup/RollupAdminLogic.sol

14: contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {
```

```solidity
src/rollup/RollupUserLogic.sol

14: contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {
```

### Recommendation

Add `_disableInitializers()` to the constructor of the Upgradeable contracts. Like it done in other contracts.

```solidity
src/challengeV2/EdgeChallengeManager.sol

    constructor() {
        _disableInitializers();
    }
```

## [08] `base.fee` can reach `0` under certain conditions

It is possible that miners will mine empty blocks until such time as the base fee is very low and then proceed to mine half full blocks and revert to sorting transactions by the priority fee. While this attack is possible, it is not a particularly stable equilibrium as long as mining is decentralized. Any defector from this strategy will be more profitable than a miner participating in the attack for as long as the attack continues (even after the base fee reached 0).

https://eips.ethereum.org/EIPS/eip-1559#miners-mining-empty-blocks

If this will happen, following code will revert because of division by zero.

```solidity
src/bridge/SequencerInbox.sol

746: block.basefee > 0 ? blobCost / block.basefee : 0
771: extraGas += l1Fees / block.basefee;
```

### Recommendation

Consider adding a check for `block.basefee` to prevent division by zero.

## [09] `proxyAdmin` transfer ownership in a single step

It's a good practice to use a two-step process for transferring ownership to avoid human error.

```solidity
src/rollup/RollupCreator.sol

204: proxyAdmin.transferOwnership(address(upgradeExecutor));
```

### Recommendation

Consider use a OpenZeppelin's `Ownable2Step` and use a two-step process for transferring ownership.

## [10] Consider rename `withdrawFromPool()` for better clarity

`withdrawFromPool(uint256 amount)` is a function that withdraws the user's stake from the pool.
`withdrawFromPool()` without arguments withdraws the user's entire stake from the pool.
But it can be unclear since function names are the same.
Consider renaming the function without arguments for better clarity.

```diff
    function withdrawFromPool(uint256 amount) public {
        if (amount == 0) {
            revert ZeroAmount();
        }
        uint256 balance = depositBalance[msg.sender];
        if (amount > balance) {
            revert AmountExceedsBalance(msg.sender, amount, balance);
        }

        depositBalance[msg.sender] = balance - amount;
        IERC20(stakeToken).safeTransfer(msg.sender, amount);

        emit StakeWithdrawn(msg.sender, amount);
    }

    /// @inheritdoc IAbsBoldStakingPool
-   function withdrawFromPool() external {
+    function withdrawAllFromPool() external {
        withdrawFromPool(depositBalance[msg.sender]);
    }
```

### Recommendation

Rename `withdrawFromPool()` to `withdrawAllFromPool()` for better clarity.

## [01] Hardcoded `salt` in `createPool()` has less flexibility

A hard-coded `salt` in the `createPool()` function is needed to create a contract with the same address but it reduces the flexibility of the contract

```solidity
src/assertionStakingPool/AssertionStakingPoolCreator.sol

function createPool(
        address _rollup,
        bytes32 _assertionHash
    ) external returns (IAssertionStakingPool) {
@>      AssertionStakingPool assertionPool = new AssertionStakingPool{salt: 0}(_rollup, _assertionHash);
        emit NewAssertionPoolCreated(_rollup, _assertionHash, address(assertionPool));
        return assertionPool;
    }
```

```solidity
src/assertionStakingPool/EdgeStakingPoolCreator.sol

    function createPool(
        address challengeManager,
        bytes32 edgeId
    ) external returns (IEdgeStakingPool) {
@>      EdgeStakingPool pool = new EdgeStakingPool{salt: 0}(challengeManager, edgeId);
        emit NewEdgeStakingPoolCreated(challengeManager, edgeId);
        return pool;
    }
```

### Recommendation

Consider include `salt` as a parameter in the `createPool()` function or create a state variable to store the `salt` value.

## [10] Initializers can be front-run

User can front-run the `initialize` function to set the contract state before the owner does.
Witch lead to contract redeployment.

```solidity
src/challengeV2/EdgeChallengeManager.sol

305: function initialize( ... ) public initializer {
```

```solidity
src/rollup/RollupProxy.sol

12: function initializeProxy(Config memory config, ContractDependencies memory connectedContracts) external {
```

### Recommendation

Protect initializers with access control modifier.

## [12] Input Arrays Lengths Not Checked

When a function takes two or more arrays as arguments, it is important to ensure that their lengths are equal.

```solidity
src/challengeV2/EdgeChallengeManager.sol

539: function confirmEdgeByOneStepProof(
        ...
        bytes32[] calldata beforeHistoryInclusionProof,
        bytes32[] calldata afterHistoryInclusionProof
    ) public {
```

### Recommendation

Add a check to ensure that the lengths of the input arrays are equal.

## [13] Use of abi.encodePacked() with Dynamic Types

The use of abi.encodePacked() with dynamic types can lead to hash collisions when the result is passed to a hash function like keccak256().
It's safer to use abi.encode() as it pads items to 32 bytes, preventing hash collisions.

For example, abi.encodePacked(0x123,0x456) results in 0x123456 which is the same as abi.encodePacked(0x1,0x23456), but abi.encode(0x123,0x456) gives 0x0...1230...456.

```solidity
src/assertionStakingPool/StakingPoolCreatorUtils.sol

// bytes memory creationCode
// bytes memory args
14: bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));
```

### Recommendation

Use abi.encode() instead of abi.encodePacked() when hashing dynamic types.

## [14] Unsafe downcast from larger to smaller integer types

When a type is downcast to a smaller type, the higher order bits are discarded, resulting in the application of a modulo operation to the original value.

```solidity
src/bridge/SequencerInbox.sol

// cast from `uint256` to `uint64`
648: uint64(afterDelayedMessagesRead)
// cast from `uint256` to `uint64`
780: uint64(extraGas)
// cast from `uint256` to `uint64`
915: creationBlock: uint64(creationBlock)
```

```solidity
src/challengeV2/libraries/EdgeChallengeManagerLib.sol

// cast from `uint256` to `uint64`
510: store.edges[edgeId].totalTimeUnrivaledCache = uint64(newValue);
```

```solidity
src/rollup/RollupAdminLogic.sol

// cast from `uint256` to `uint64`
83: nextInboxPosition: uint64(currentInboxCount)
```

```solidity
src/rollup/RollupCore.sol

// cast from `uint256` to `uint64`
495: nextInboxPosition: uint64(nextInboxPosition)
```

### Recommendation

Use OpenZeppelin's SafeCast library for safe downcasting.

## [15] Missing `__gap[50]` storage variable in Upgradeable contracts

In the context of upgradeable contracts, ensuring forward compatibility between different contract versions is a critical concern. One key strategy for ensuring this compatibility is the use of a `__gap` storage variable.

The `__gap` variable acts as a reserved space in the contract's storage layout. This space can then be utilized for adding new state variables in future contract upgrades, while maintaining the original storage layout of the contract.

Without the `__gap` storage variable, adding new state variables in a contract upgrade can risk overwriting the existing contract storage.

It's crucial to include a `__gap` storage variable to Upgradable smart contracts.

```solidity
src/rollup/RollupAdminLogic.sol

14: contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {
```

```solidity
src/rollup/RollupUserLogic.sol

14: contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {
```

### Recommendation

Add a `__gap` storage variable to the contract.

## [16] Use of Ownable contract for single-step ownership change

A single step ownership change is risky due to the fact that the new owner address could be wrong.

```solidity
src/rollup/BridgeCreator.sol

18: import "@openzeppelin/contracts/access/Ownable.sol";
21: contract BridgeCreator is Ownable {
```

```solidity
src/rollup/RollupCreator.sol

13: import "@openzeppelin/contracts/access/Ownable.sol";
17: contract RollupCreator is Ownable {
```

### Recommendation

Consider using a [Ownable2Step](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable2Step.sol) contract, which provides a two-step ownership.

## [17] Using a vulnerable dependency of OpenZeppelin Contracts

The package.json configuration file says that the project is using OZ which has a not last update version.
Latest non vulnerable version `4.9.3` / `5.0.0` for @openzeppelin/contracts and @openzeppelin/contracts-upgradeable.

```solidity
app/2024-05-arbitrum-foundation/package.json

52: "@openzeppelin/contracts": "4.7.3",
53: "@openzeppelin/contracts-upgradeable": "4.7.3",
```

### Recommendation

Upgrade to the latest version of OpenZeppelin Contracts.

## [18] Input Validation Missing in Setter Functions

Setter functions are utilized to update the state variables of a contract.
It is critical to ensure these functions have input sanitization.

```solidity
src/rollup/RollupAdminLogic.sol

223: function setBaseStake(uint256 newBaseStake) external override {
281: function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
```

```solidity
src/rollup/RollupCreator.sol

63: function setTemplates( ... ) external onlyOwner {
```

### Recommendation

Add input validation checks to setter functions to ensure that the inputs are expected and valid.

## [19] Owner can renounce Ownership

Renouncing ownership will leave the contract without an owner, thereby removing any functionality that is only available to the owner.

```solidity
src/rollup/BridgeCreator.sol

18: import "@openzeppelin/contracts/access/Ownable.sol";
```

```solidity
src/rollup/RollupCreator.sol

13: import "@openzeppelin/contracts/access/Ownable.sol";
```

### Recommendation

Override the `renounceOwnership` function.

## [20] Events may be emitted out of order due to reentrancy

Emitting events post external interactions may cause them to be out of order due to reentrancy, which can be misleading or erroneous for event listeners.
[Refer to the Solidity Documentation for best practices.](https://solidity.readthedocs.io/en/latest/security-considerations.html#reentrancy)

```solidity
src/assertionStakingPool/AbsBoldStakingPool.sol

// `safeTransferFrom()` before `StakeDeposited` event emit
36: emit StakeDeposited(msg.sender, amount);
// `safeTransfer()` before `StakeWithdrawn` event emit
52: emit StakeWithdrawn(msg.sender, amount);
```

### Recommendation

Emits events before safeTransferFrom() and safeTransfer() calls.

## [21] Consider make setters (critical functions) in two-step procedure

Critical functions in contracts should follow a two-step procedure to minimize human error.

```solidity
src/bridge/SequencerInbox.sol

885: function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_) external onlyRollupOwner {
894: function setIsBatchPoster(address addr, bool isBatchPoster_) external onlyRollupOwnerOrBatchPosterManager {
903: function setValidKeyset(bytes calldata keysetBytes) external onlyRollupOwner {
933: function setIsSequencer(address addr, bool isSequencer_) external onlyRollupOwnerOrBatchPosterManager {
942: function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
946: function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
```

```solidity
src/rollup/BridgeCreator.sol

52: function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
57: function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
```

```solidity
src/rollup/RollupAdminLogic.sol

117: function setOutbox(IOutbox _outbox) external override {
138: function setDelayedInbox(address _inbox, bool _enabled) external override {
180: function setValidator(address[] calldata _validator, bool[] calldata _val) external override {
195: function setOwner(address newOwner) external override {
204: function setMinimumAssertionPeriod(uint256 newPeriod) external override {
213: function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {
223: function setBaseStake(uint256 newBaseStake) external override {
268: function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
281: function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {
290: function setSequencerInbox(address _sequencerInbox) external override {
299: function setInbox(IInboxBase newInbox) external {
308: function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {
317: function setAnyTrustFastConfirmer(address _anyTrustFastConfirmer) external {
326: function setChallengeManager(address _challengeManager) external {
```

### Recommendation

Implement a two-step procedure for critical functions.

## [22] `onlyOwner` functions not accessible if `owner` renounces ownership

Since contract don't override `renounceOwnership` function, these functions will not be accessible if `owner` renounces ownership.

```solidity
src/rollup/BridgeCreator.sol

52: function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {
57: function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
```

```solidity
src/rollup/RollupCreator.sol

62: function setTemplates( ... ) external onlyOwner {
```

### Recommendation

Override the `renounceOwnership` function.

## [23] Loss of precision on division

Solidity doesn't support fractions, so divisions by large numbers could result in the quotient being zero.
This behavior should always be considered.

```solidity
src/bridge/DelayBuffer.sol

46: buffer += (elapsed * replenishRateInBasis) / BASIS;
```

```solidity
src/bridge/SequencerInbox.sol

746: block.basefee > 0 ? blobCost / block.basefee : 0
771: extraGas += l1Fees / block.basefee;
```

### Recommendation

Ensure that the division loss of precision is not critical for the contract logic.

## [24] Missing checks for `address(0)` when updating address state variables

Check for zero-address to avoid the risk of setting `address(0)` for state variables after an update.

```solidity
src/bridge/SequencerInbox.sol

943: batchPosterManager = newBatchPosterManager;
```

```solidity
src/rollup/RollupCreator.sol

73: bridgeCreator = _bridgeCreator;
74: osp = _osp;
75: challengeManagerTemplate = _challengeManagerLogic;
76: rollupAdminLogic = _rollupAdminLogic;
77: rollupUserLogic = _rollupUserLogic;
78: upgradeExecutorLogic = _upgradeExecutorLogic;
79: validatorWalletCreator = _validatorWalletCreator;
80: l2FactoriesDeployer = _l2FactoriesDeployer;
```

### Recommendation

Add a check to ensure that the new address is not `address(0)`.

## [25] Lack of two-step update for updating protocol addresses

Add a two-step process for any critical address changes.

```solidity
src/bridge/SequencerInbox.sol

943: batchPosterManager = newBatchPosterManager;
```

```solidity
src/rollup/RollupAdminLogic.sol

118: outbox = _outbox;
273: loserStakeEscrow = newLoserStakerEscrow;
300: inbox = newInbox;
318: anyTrustFastConfirmer = _anyTrustFastConfirmer;
```

```solidity
src/rollup/RollupCreator.sol

73: bridgeCreator = _bridgeCreator;
74: osp = _osp;
75: challengeManagerTemplate = _challengeManagerLogic;
76: rollupAdminLogic = _rollupAdminLogic;
77: rollupUserLogic = _rollupUserLogic;
78: upgradeExecutorLogic = _upgradeExecutorLogic;
79: validatorWalletCreator = _validatorWalletCreator;
80: l2FactoriesDeployer = _l2FactoriesDeployer;
```

### Recommendation

Two-step process for updating protocol addresses minimizes human error.

## [26] Potential Re-org Attack Vector

The contract appears to deploy new contracts using the `new` keyword.
In a re-org attack scenario, such deployments can be exploited by a malicious actor who might rewrite the blockchain's history and deploy the contract at an expected address.

Consider deploying the contract via `CREATE2` opcode with a specific salt that includes `msg.sender` and the existing contract address.
This will ensure a predictable contract address, reducing the chances of such an attack.

```solidity
src/rollup/BOLDUpgradeAction.sol

307: PREIMAGE_LOOKUP = new StateHashPreImageLookup();
308: ROLLUP_READER = new RollupReader(contracts.rollup);
325: MINI_STAKE_AMOUNTS_STORAGE = address(new ConstantArrayStorage(settings.miniStakeAmounts));
474: new TransparentUpgradeableProxy(
```

[307](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L307) | [308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L308) | [325](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L325) | [474](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BOLDUpgradeAction.sol#L474)

```solidity
src/rollup/BridgeCreator.sol

70: address(new TransparentUpgradeableProxy(address(templates.bridge), adminProxy, ""))
74: new TransparentUpgradeableProxy(
86: address(new TransparentUpgradeableProxy(address(templates.inbox), adminProxy, ""))
90: new TransparentUpgradeableProxy(address(templates.rollupEventInbox), adminProxy, "")
94: address(new TransparentUpgradeableProxy(address(templates.outbox), adminProxy, ""))
```

[70](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L70) | [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L74) | [86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L86) | [90](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L90) | [94](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/BridgeCreator.sol#L94)

```solidity
src/rollup/RollupCreator.sol

91: new TransparentUpgradeableProxy(
185: ProxyAdmin proxyAdmin = new ProxyAdmin();
273: new TransparentUpgradeableProxy(
```

[91](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L91) | [185](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L185) | [273](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/main/src/rollup/RollupCreator.sol#L273)

## [27] Constructor/Initializer missing `address(0)` Check before assignment

It's a good practice to check for `address(0)` in the constructor/initializer before assigning to minimize human error.

```solidity
src/assertionStakingPool/AbsBoldStakingPool.sol

23: constructor(address _stakeToken) {
```

```solidity
src/rollup/BOLDUpgradeAction.sol

125: constructor(IOldRollup _rollup) {
```

```solidity
src/challengeV2/EdgeChallengeManager.sol

// `_stakeToken`
305: function initialize(
        ...
        IERC20 _stakeToken,
        ...
    ) public initializer {
```

### Recommendation

Add a check to ensure that the new address is not `address(0)`.

## [28] Empty `receive()/fallback()` function

It's a good practice to emit an event in the `receive()` function.

```solidity
src/rollup/RollupCreator.sol

61: receive() external payable
```

### Recommendation

Emit an event after contract receives ETH.

## [29] Unbounded loop may run out of gas

Unbounded loops always have the potential to run out of gas.

```solidity
src/challengeV2/EdgeChallengeManager.sol

492: for (uint256 i = 0; i < edgeIds.length; i++)
```

```solidity
src/challengeV2/libraries/ArrayUtilsLib.sol

15: for (uint256 i = 0; i < arr.length; i++)
47: for (uint256 i = 0; i < arr1.length; i++)
50: for (uint256 i = 0; i < arr2.length; i++)
```

```solidity
src/challengeV2/libraries/MerkleTreeLib.sol

115: for (uint256 i = 0; i < me.length; i++)
188: for (uint256 i = 0; i < me.length; i++)
294: for (uint256 i = 0; i < me.length; i++)
```

```solidity
src/rollup/BOLDUpgradeAction.sol

528: for (uint256 i = 0; i < validators.length; i++)
```

```solidity
src/rollup/RollupAdminLogic.sol

184: for (uint256 i = 0; i < _validator.length; i++)
230: for (uint256 i = 0; i < staker.length; i++)
```

```solidity
src/rollup/RollupCreator.sol

225: for (uint256 i = 0; i < deployParams.batchPosters.length; i++)
235: for (uint256 i = 0; i < deployParams.validators.length; i++)
```

### Recommendation

Limit the number of iterations in the loop by adding `if` or `require` statements.

## [30] Errors that dont have `@param` in natSpec but other errors have it

Consider add `@param` to these errors if you want to keep the consistency.

```solidity
src/libraries/Error.sol
/// @dev msg.value sent to the inbox isn't high enough
error InsufficientValue(uint256 expected, uint256 actual);

/// @dev submission cost provided isn't enough to create retryable ticket
error InsufficientSubmissionCost(uint256 expected, uint256 actual);

/// @dev address not allowed to interact with the given contract
error NotAllowedOrigin(address origin);

/// @dev used to convey retryable tx data in eth calls without requiring a tx trace
/// this follows a pattern similar to EIP-3668 where reverts surface call information
error RetryableData(
    address from,
    address to,
    uint256 l2CallValue,
    uint256 deposit,
    uint256 maxSubmissionCost,
    address excessFeeRefundAddress,
    address callValueRefundAddress,
    uint256 gasLimit,
    uint256 maxFeePerGas,
    bytes data
);

/// @dev The sequence number provided to this message was inconsistent with the number of batches already included
error BadSequencerNumber(uint256 stored, uint256 received);

/// @dev The sequence message number provided to this message was inconsistent with the previous one
error BadSequencerMessageNumber(uint256 stored, uint256 received);

/// @dev Thrown when an init param was supplied as empty
error InitParamZero(string name);

```
