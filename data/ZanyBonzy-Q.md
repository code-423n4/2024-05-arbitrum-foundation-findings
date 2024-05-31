## 1. EdgeChallengerManager.sol is intended to be upgradeable but cannot be upgraded

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L206

## Impact
EdgeChallengeManager.sol is inended to be upgradeable as can be noted from the prescence of an Initializer and also the [comment](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L19) made in the interface. It however does not derive from UUPS contract that handles Openzepplin's UUPSUpgradeable contract. Therefore, it is missing the authoriseUpgrade method, and the contract cannot be upgraded incase it needs to be upgraded at later point.

```solidity
contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {
```

***

## 2. Unused errors can be removed or incorporated

### Impact

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/libraries/Error.sol#L80-L88

```solidity
/// @dev The contract is paused, so cannot be paused
error AlreadyPaused(); 

/// @dev The contract is unpaused, so cannot be unpaused
error AlreadyUnpaused(); 

/// @dev The contract is paused
error Paused(); 

```

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeErrors.sol#L4


```solidity
error EdgeTypeNotBlock(uint8 level);
```

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeErrors.sol#L56

```solidity
error EdgeClaimMismatch(bytes32 edgeId, bytes32 claimingEdgeId); 
```

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeErrors.sol#L60

```solidity
error EdgeNotAncestor( //@ qa unused errors
    bytes32 edgeId, bytes32 lowerChildId, bytes32 upperChildId, bytes32 ancestorEdgeId, bytes32 claimId
);
```

***

## 3. Consider introducing functions for on-behalf deposits into pool

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L29

### Impact

```solidity
    function depositIntoPool(uint256 amount) external {
        if (amount == 0) {
            revert ZeroAmount();
        }

        depositBalance[msg.sender] += amount;
        IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), amount);

        emit StakeDeposited(msg.sender, amount);
    }
```

***

## 4. Can allow users to specify a recipient during withdrawals

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L41-L54

### Impact


```solidity
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
```

***

## 5. Redeundant check in `postUpgradeInit` can be removed, since it is also performed in `_setBufferConfig`

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L160-L175

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L848
### Impact

```solidity

    function postUpgradeInit(BufferConfig memory bufferConfig_)
        external
        onlyDelegated
        onlyProxyOwner
    {
        if (!isDelayBufferable) revert NotDelayBufferable(); //
...
        _setBufferConfig(bufferConfig_);
    }
```
and in `_setBufferConfig`, there's the same check.
```solidity
    function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
        if (!isDelayBufferable) revert NotDelayBufferable();
        ...
    }
```

***

## 6. Can allow ETH NATIVE Token to also be set as 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L177-L195


https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L110-L121


### Impact

Users passing in 0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE will have ERC20 bridges created for them instead.

```solidity
        BridgeContracts memory frame = _createBridge(
            adminProxy,
            nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,
            isDelayBufferable
        );

        // init contracts
        if (nativeToken == address(0)) {
            IEthBridge(address(frame.bridge)).initialize(IOwnable(rollup));
        } else {
            IERC20Bridge(address(frame.bridge)).initialize(IOwnable(rollup), nativeToken);
        }
```

And will sequencerInbox can be successfully initializated with the bridge depending on if they [select](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L143) using fee token in the constructor.

```solidity
    function initialize(
        IBridge bridge_,
        ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
        BufferConfig memory bufferConfig_
    ) external onlyDelegated {
        if (bridge != IBridge(address(0))) revert AlreadyInit();
        if (bridge_ == IBridge(address(0))) revert HadZeroInit();

        // Make sure logic contract was created by proper value for 'isUsingFeeToken'.
        // Bridge in ETH based chains doesn't implement nativeToken(). In future it might implement it and return address(0)
        bool actualIsUsingFeeToken = false;
        try IERC20Bridge(address(bridge_)).nativeToken() returns (address feeToken) {
            if (feeToken != address(0)) {
                actualIsUsingFeeToken = true;
            }
        } catch {}
        if (isUsingFeeToken != actualIsUsingFeeToken) {
            revert NativeTokenMismatch();
        }
```

***

## 7. Redundant check as ERC20Bridge cannot be created with 0 address

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L189


### Impact

When bridge is created with address(0) as native token, EthBridge is automatically created.
```solidity
        BridgeContracts memory frame = _createBridge(
            adminProxy,
            nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,
            isDelayBufferable
        );

        // init contracts
        if (nativeToken == address(0)) {
            IEthBridge(address(frame.bridge)).initialize(IOwnable(rollup));
        } else {
            IERC20Bridge(address(frame.bridge)).initialize(IOwnable(rollup), nativeToken);
        }
```

Upon SequencerInbox initialization, a check is the made to see if `nativeToken` from ERC20Bridge is address(0), which as established will not be.
```solidity
    function initialize(
        IBridge bridge_,
        ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
        BufferConfig memory bufferConfig_
    ) external onlyDelegated {
        if (bridge != IBridge(address(0))) revert AlreadyInit();
        if (bridge_ == IBridge(address(0))) revert HadZeroInit();

        // Make sure logic contract was created by proper value for 'isUsingFeeToken'.
        // Bridge in ETH based chains doesn't implement nativeToken(). In future it might implement it and return address(0)
        bool actualIsUsingFeeToken = false;
        try IERC20Bridge(address(bridge_)).nativeToken() returns (address feeToken) {
            if (feeToken != address(0)) {
                actualIsUsingFeeToken = true;
            }
        } catch {}
        if (isUsingFeeToken != actualIsUsingFeeToken) {
            revert NativeTokenMismatch();
        }
```


***


## 8. Consider adding a check for 0 when setting children

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L239-L245

### Impact

The function is intended to be settable only once and holds a check for just that. The check is however not effective if the children are set to 0. 

```solidity
    function setChildren(ChallengeEdge storage edge, bytes32 lowerChildId, bytes32 upperChildId) internal {
        if (edge.lowerChildId != 0 || edge.upperChildId != 0) {
            revert ChildrenAlreadySet(ChallengeEdgeLib.id(edge), edge.lowerChildId, edge.upperChildId);
        }
        edge.lowerChildId = lowerChildId;
        edge.upperChildId = upperChildId;
    }
```

***

## 9. `mostSignificantBit` should wrapped in unchecked blocks as overflow wrapping behaviour is desired

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L29-L70

### Impact

`mostSignificantBit` in UintUtilsLib.sol appears to be a fork of uniswapV3 [bitmath](https://github.com/Uniswap/v3-core/blob/d8b1c635c275d2a9450bd6a78f3fa2484fef73eb/contracts/libraries/BitMath.sol#L2-L45) contract. And it can be observed that its being compiled with a solidity version less than 0.8.0, which allows for overflow wrapping. In the 0.8 [version](https://github.com/Uniswap/v3-core/blob/6562c52e8f75f0c10f9deaf44861847585fc8129/contracts/libraries/BitMath.sol#L13-L47) of the contract, the `unchecked` blocks can be noticed indicating that the overflow wrapping behaviour is quite important in bitmath calculations. Consider doing the same in UintUtilsLib.sol

```solidity
    function mostSignificantBit(uint256 x) internal pure returns (uint256 msb) {
        require(x != 0, "Zero has no significant bits");

        // x >= 2 ** 128
        if (x >= 0x100000000000000000000000000000000) {
            x >>= 128;
            msb += 128;
        }
        // x >= 2 ** 64
        if (x >= 0x10000000000000000) {
            x >>= 64;
            msb += 64;
        }
        // x >= 2 ** 32
        if (x >= 0x100000000) {
            x >>= 32;
            msb += 32;
        }
        // x >= 2 ** 16
        if (x >= 0x10000) {
            x >>= 16;
            msb += 16;
        }
        // x >= 2 ** 8
        if (x >= 0x100) {
            x >>= 8;
            msb += 8;
        }
        // x >= 2 ** 4
        if (x >= 0x10) {
            x >>= 4;
            msb += 4;
        }
        // x >= 2 ** 2
        if (x >= 0x4) {
            x >>= 2;
            msb += 2;
        }
        // x >= 2 ** 1
        if (x >= 0x2) msb += 1;
    }
}
```

***


## 10. Should not hardcode block number because arbitrum and ethereum have different time measurements per block

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L48-L49

### Impact

The contracts are to be deployed on Ethereum and Arbitrum which have different units of time measurements per block. Consider setting the value in the constructor instead.
```solidity

    uint256 public constant VALIDATOR_AFK_BLOCKS = 201600;
```

***


## 11. Should refund difference between msg.value sent and token spent not contract balance

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L292-L305

### Impact

RollupCreator.sol holds a receive function which makes it able to receive ETH.

```solidity
    receive() external payable {}

```
Upon factory deployment, the cost is calculated, and for refunds, the entire contract balance is sent to the caller. Considering that the function that deploys the factories is [payable](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L139), users can call the function sending ETH too. They should be refunded the difference between the amount sent and the cost of factory deployment, not the entire contract balance. A user monitoring the mempool can frontrun another user's deployment transaction if the first user had sent tokens to the contract first, before calling the `createRollup` function.

```solidity
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
        } else {
```

***

## 12. Minimum assertion period is set to 15 seconds not 15 minutes contrary to the comment. Minimum assertion period will be too small.

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L51-L54

### Impact

```solidity
        // A little over 15 minutes
        minimumAssertionPeriod = 75;
        challengeGracePeriodBlocks = config.challengeGracePeriodBlocks;

```


## 13. Introduce a function to change stake amounts or stake token in EdgeChallengerManager or should use pricing method instead.

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L276

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L279

### Impact

Stake amount is current denoted as a definite amount of the stake token in use (not in terms of usd or oracle pricing). This cost of creating edges fluctuates depending the current value of the stake token. Depending on the direction of the staketoken price, creating assertions and edges can either be too expensive (even for pools), potentially allowing incorrect assertions to slip through, or can be extremely cheap, allowing excessive edge and assertion creation leading to spam.

Consider using a stake token price instead, or introducing a function to change the stake amount.

***

## 14. `getPool` might be  vulnerable to address collisions

Links to affected code *

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L30
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L30
https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L15

### Impact

The `CREATE2`'s `computeAddress` function employs deterministic address computation to verify the authenticity of the deployed assertion and edge staking pools. This approach is based on the assumption that the address derived from the contract's creation bytecode and the creator's address is unique. However, this method is susceptible to address collision risks, where a different contract, under specific circumstances, might share the same computed address, leading to erroneous validation and possible draining of the pool's funds.

```solidity
        bytes32 bytecodeHash = keccak256(abi.encodePacked(creationCode, args));
        address pool = Create2.computeAddress(0, bytecodeHash, address(this));
```