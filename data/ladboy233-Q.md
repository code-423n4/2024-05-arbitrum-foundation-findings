# Issue summary

Here is the updated table with the issue numbers changed to L-1, L-2, L-3, etc., and the issue number centered in the first column:

| Issue Number | Title                                                                                                       |
|--------------|-------------------------------------------------------------------------------------------------------------|
|     L-1      | User does not know how the edge id is computed when they want to stake for an edge pool                     |
|     L-2      | Lack of incentive for staker to stake fund to assertion staking pool and edge staking pool                  |
|     L-3      | Staking pool cannot distribute reward if the assertion/edge are confirmed                                   |
|     L-4      | If a withdrawal address is a smart contract that is not capable of calling withdrawStakerFunds, fund is locked |
|     L-5      | More documentation and comment and testing should be added in BOLDUpgradeAction.sol                         |
|     L-6      | BoldUpgradeAction.sol does not follow the gov-action-contracts documentation and guideline                   |
|     L-7      | Should consider using block.timestamp instead of block.number to track time elapse                          |
|     L-8      | User may lose fee when creating Rollup                                                                      |
|     L-9      | Refunded ETH is not handled when creating Rollup                                                            |
|    L-10      | Inconsistent check for validatorWhitelistDisabledfor in EdgeChallangeManager                                |
|    L-11      | EdgeChallangeManger function missing onlyValidator check and whenNotPaused modifier                         |                                             |

# user do not know the how the edge id computed when they wants to stake for a edge pool

anyone can create an edge pool with edge id
```solidity
  constructor(
        address _challengeManager,
        bytes32 _edgeId
    ) AbsBoldStakingPool(address(EdgeChallengeManager(_challengeManager).stakeToken())) {
        challengeManager = _challengeManager;
        edgeId = _edgeId;
    }
```

then after there are enough user stake fund, [an edge can be created.](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L44)
```solidity
 function createEdge(CreateEdgeArgs calldata args) external {
        uint256 requiredStake = EdgeChallengeManager(challengeManager).stakeAmounts(args.level);
        IERC20(stakeToken).safeIncreaseAllowance(address(challengeManager), requiredStake);
        bytes32 newEdgeId = EdgeChallengeManager(challengeManager).createLayerZeroEdge(args);
        if (newEdgeId != edgeId) {
            revert IncorrectEdgeId(newEdgeId, edgeId);
        }
    }
```

this is how the [edge id is computed](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L189):

```solidity
function idMem(ChallengeEdge memory edge) internal pure returns (bytes32) {
        return idComponent(
            edge.level, edge.originId, edge.startHeight, edge.startHistoryRoot, edge.endHeight, edge.endHistoryRoot
        );
    }
```

and 

```solidity
  function idComponent(
        uint8 level,
        bytes32 originId,
        uint256 startHeight,
        bytes32 startHistoryRoot,
        uint256 endHeight,
        bytes32 endHistoryRoot
    ) internal pure returns (bytes32) {
        return keccak256(
            abi.encodePacked(
                mutualIdComponent(level, originId, startHeight, startHistoryRoot, endHeight), endHistoryRoot
            )
        );
    }
```

given that the one way deterministic property of keccak256 hash function,

if we know the level, originId, startHeight, startHistoryRoot, endHeight and endHistoryRoot, we can compute the edge id,

but as a user that wants to stake for the edge staking pool,

he only knows the edge id hash, 

but he cannot compute the level, originId, startHeight, startHistoryRoot, endHeight and endHistoryRoot

using the edge id hash backward.

then the user may think the parameter to create an edge is too opaque and are not willing to stake fund to help create an edge.

the recommendation is set the transparent CreateEdgeArgs calldata args in the constructor of the edge staking pool.

# lack of incentive for staker to stake fund to assertion staking pool and edge staking pool

In the current implementation,

a user can create an assertion pool / edge staking pool, and anyone can deposit fund,

after the assertion / edge are confirmed / resolved, the fund is returned to the pool and the staker can withdraw fund.

but from staker perspective,

if a assertion / edge are incorrect, they lose their fund.

if a assertion / edge are correct, they just get their fund back and earns no money.

so there is lack of incentive for staker to stake fund to assertion staking pool and edge staking pool

# Staking pool cannot distribute reward if the assertion / edge are confirmed. 

when a user make a incorrect assertion / create a incorrect edge,

the fund [goes to loserStakeEscrow address](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L210),

```solidity
if (!getAssertionStorage(newAssertionHash).isFirstChild) {
    // We assume assertion.beforeStateData is valid here as it will be validated in createNewAssertion
    // only 1 of the children can be confirmed and get their stake refunded
    // so we send the other children's stake to the loserStakeEscrow
    // NOTE: if the losing staker have staked more than requiredStake, the excess stake will be stuck
    IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);
}
```

but even in the future when the protocol decides to distribute the loser stake to winner stake from loserStakeEscrow,

transferring the bond directly to stake pool would cause lose of fund, 

because the code only support that the user get their original staking fund back,

not reward distribution.

# if a withdrawal address is a smart contract that is not capable of calling withdrawStakerFunds, fund is locked,

when creating a new assertion, the user [can input a withdrawal address](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L329),


```solidity
    /**
     * @notice Create a new stake on a new assertion
     * @param tokenAmount Amount of the rollups staking token to stake
     * @param assertion Assertion describing the state change between the old assertion and the new one
     * @param expectedAssertionHash Assertion hash of the assertion that will be created
     * @param withdrawalAddress The address the send the stake back upon withdrawal
     */
    function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
    ) public {
```

but when withdraw fund, the code always requires the withdrawal address to call [withdrawStakerFunds](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L358)

```solidity
 function withdrawStakerFunds() external override whenNotPaused returns (uint256) {
        uint256 amount = withdrawFunds(msg.sender);
        require(amount > 0, "NO_FUNDS_TO_WITHDRAW");
        // This is safe because it occurs after all checks and effects
        IERC20(stakeToken).safeTransfer(msg.sender, amount);
        return amount;
    }
```

but if a withdrawal address is a smart contract that is not capable of calling withdrawStakerFunds, fund is locked,

the recommendation is implement a support interface style hook check when setting withdrawal contract to make sure the withdrawal contract

is capable of withdraw the fund.


```solidity
function newStakeOnNewAssertion(
        uint256 tokenAmount,
        AssertionInputs calldata assertion,
        bytes32 expectedAssertionHash,
        address withdrawalAddress
    ) public {
        if(address(withdrawalAddress).code.size > 0) {
            require(IStakeFundReceiver(withdrawalAddress).canWithdrawalAssertionStake(), "address cannot withdraw fund");
            ....
        }
```

# More documentation and comment and testing should be added in BOLDUpgradeAction.sol

the [BOLDUpgradeAction.sol](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L94) is a complex contract that in charge upgrade all arbitrum contract

-> rollup contract, inbox contract, etc...

documentation and comment and testing should be added in BOLDUpgradeAction.sol

to make sure the upgrade works as expectedly.

# BoldUpgradeAction.sol does not follow the gov-action-contracts documentation and guideline

there is a general documentation about the action contracts framework here: 

https://github.com/ArbitrumFoundation/governance/blob/main/src/gov-action-contracts/README.md

according to the guideline:

> A GAC should have only one external function; it should be named perform and it should take no parameters.

but BoldUpgradeAction.sol [has a function perform](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L464) but take a list of validator array as parameter

> GACs should preform checks on the expected state before and after the action's execution if possible, and should explicity revert on failure.

the BoldUpgradeAction.sol should add more post-upgrade validation to make sure the upgrade works as intended.

# should consider use block.timestamp instead of using block.number to track time elapse

while the ethereum mainnet produce one block per 12 seconds, 

it is still recommend to trace time elapse using block.timestamp instead of block.number

because in different blockchain network, the block production may differ,

for example, metis l2 usually produce block in 2 - 4 seconds

when a user create a rollup layer using roll up creator, they may want to deal with consistent timestamp elapse instead of inconsistent block production time.

# user may lose fee when creatingRollup

when create roll up, the contract may involve the logic that [deploys the factories to L2](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L244)

```solidity
if (deployParams.deployFactoriesToL2) {
        _deployFactories(
            address(bridgeContracts.inbox),
            deployParams.nativeToken,
            deployParams.maxFeePerGasForRetryables
        );
    }
```

which calls [the function perform](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L300)

```solidity
 function _deployFactories(
        address _inbox,
        address _nativeToken,
        uint256 _maxFeePerGas
    ) internal {
        if (_nativeToken == address(0)) {
            // we need to fund 4 retryable tickets
            uint256 cost = l2FactoriesDeployer.getDeploymentTotalCost(
                IInboxBase(_inbox),
                _maxFeePerGas
            );

            // do it
            l2FactoriesDeployer.perform{value: cost}(_inbox, _nativeToken, _maxFeePerGas);

            // refund the caller
            // solhint-disable-next-line avoid-low-level-calls
            (bool sent, ) = msg.sender.call{value: address(this).balance}("");
            require(sent, "Refund failed");
        }
```

the code compute the cost and then [call perform in deployer helper](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/DeployHelper.sol#L96)

```solidity
 function perform(
        address _inbox,
        address _nativeToken,
        uint256 _maxFeePerGas
    ) external payable {
        bool isUsingFeeToken = _nativeToken != address(0);

        _fundAndDeploy(
            _inbox,
            NICK_CREATE2_VALUE,
            NICK_CREATE2_DEPLOYER,
            NICK_CREATE2_PAYLOAD,
            isUsingFeeToken,
            _maxFeePerGas
        )
```

it will call _fundAndDeploy

```solidity
  function _fundAndDeploy(
        address inbox,
        uint256 _value,
        address _l2Address,
        bytes memory payload,
        bool _isUsingFeeToken,
        uint256 maxFeePerGas
    ) internal {
        uint256 submissionCost = IInboxBase(inbox).calculateRetryableSubmissionFee(
            0,
            block.basefee
        );
        uint256 feeAmount = _value + submissionCost + GASLIMIT * maxFeePerGas;

        // fund the target L2 address
        if (_isUsingFeeToken) {
            IERC20Inbox(inbox).createRetryableTicket({
                to: _l2Address,
                l2CallValue: _value,
                maxSubmissionCost: submissionCost,
 @               excessFeeRefundAddress: msg.sender,
 @               callValueRefundAddress: msg.sender,
                gasLimit: GASLIMIT,
                maxFeePerGas: maxFeePerGas,
                tokenTotalFeeAmount: feeAmount,
                data: ""
            });
        }
```

the [excessFeeRefundAddress and callValueRefundAddress](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/DeployHelper.sol#L66) will be msg.sender, which is the roll up creator address,

not the original caller that create the rollup, this cause loss of refunded fee and value.

# refunded eth is not handled when create rollup

when create roll up, the contract may involve the logic that deploys the factories to L2

```solidity
if (deployParams.deployFactoriesToL2) {
        _deployFactories(
            address(bridgeContracts.inbox),
            deployParams.nativeToken,
            deployParams.maxFeePerGasForRetryables
        );
    }
```

which calls 

```solidity
 function _deployFactories(
        address _inbox,
        address _nativeToken,
        uint256 _maxFeePerGas
    ) internal {
        if (_nativeToken == address(0)) {
            // we need to fund 4 retryable tickets
            uint256 cost = l2FactoriesDeployer.getDeploymentTotalCost(
                IInboxBase(_inbox),
                _maxFeePerGas
            );

            // do it
            l2FactoriesDeployer.perform{value: cost}(_inbox, _nativeToken, _maxFeePerGas);

            // refund the caller
            // solhint-disable-next-line avoid-low-level-calls
            (bool sent, ) = msg.sender.call{value: address(this).balance}("");
            require(sent, "Refund failed");
        }
```

the code compute the cost and then call perform,

```solidity
 function perform(
        address _inbox,
        address _nativeToken,
        uint256 _maxFeePerGas
    ) external payable {
        bool isUsingFeeToken = _nativeToken != address(0);

        ...

        // if paying with ETH refund the caller
        if (!isUsingFeeToken) {
@            payable(msg.sender).transfer(address(this).balance);
        }
    }
```

but msg.sender will be the roll up creator and roll up creator does not refund the excessive ETH to original rollup creator

after the helper contract [refund the ETH](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/DeployHelper.sol#L131) to the RollupCreater.sol

```solidity
 if (!isUsingFeeToken) {
@            payable(msg.sender).transfer(address(this).balance);
 }
```

# Inconsistent check for validatorWhitelistDisabledfor in EdgeChallangeManager

In EdgeChallangeManager#createLayerZeroEdge, [the check for validatorWhitelistDisabledfor](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L374) is done below:

```solidity
function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
    // Check if whitelist is enabled in the Rollup
    // We only enforce whitelist in this function as it may exhaust resources
    bool whitelistEnabled = !assertionChain.validatorWhitelistDisabled();

    if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {
        revert NotValidator(msg.sender);
    }
```

while in RollUserLogic, the onlyValidator modifer is used,

```solidity
  modifier onlyValidator() {
        require(isValidator[msg.sender] || validatorWhitelistDisabled, "NOT_VALIDATOR");
        _;
    }
```

it is recommended to use the onlyValidator modifer as well in EdgeChallangeManager for coding consistency.

# EdgeChallangeManger function missing onlyValidator check and whenNotPaused modifier

In Rollup user logic, the function all guarded with onlyValidator and whenNotPaused modifier

```solidity
  modifier onlyValidator() {
        require(isValidator[msg.sender] || validatorWhitelistDisabled, "NOT_VALIDATOR");
        _;
    }
```

but in challange manager, only when [create layerzero edge](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L374), the  validatorWhitelistDisabled is checked:

```solidity
function createLayerZeroEdge(CreateEdgeArgs calldata args) external returns (bytes32) {
    // Check if whitelist is enabled in the Rollup
    // We only enforce whitelist in this function as it may exhaust resources
    bool whitelistEnabled = !assertionChain.validatorWhitelistDisabled();

    if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {
        revert NotValidator(msg.sender);
    }
```

but the function createLayerZeroEdge is missing whenNotPaused modifier,

the function [bisect edge](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L451) and [confirm by time](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L511) and [confirm by one step proof](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L539) are missing the validatorWhitelistDisabled check and whenNotPaused modifier,

the impact is that when the validatorWhitelistDisabled is false or the roll up is falsed, the challange can continue to be confirmed when the challange should not be confirmed.

