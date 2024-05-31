## Title
Stake on an invalid assertion can be withdrawn. 

## Impact
Validators that staked on an invalid assertion can withdraw their stake if another validator references the invalid assertion as its prevAssertion.

We can say that the validators that reference an invalid assertion inherits the punishment of the parent validator, while the parent validator goes unpunished(even though they submitted an invalid assertion.)

## Proof of Concept
Once a validator makes an invalid assertion, the associated stake is meant to be seized.

In order to withdraw one's stake, one has to call `returnOldDeposit` or `reduceDeposit` so that his withdrawable stake would be increased, then he can call `withdrawStake` to withdraw the stake.

Looking into `reduceDeposit`(and `returnOldDeposit`), we can see that there is a check called `requireInactiveStaker`:
```solidity
    function requireInactiveStaker(address stakerAddress) internal view {
        require(isStaked(stakerAddress), "NOT_STAKED");
     
        bytes32 lastestAssertion = latestStakedAssertion(stakerAddress);
        bool isLatestConfirmed = lastestAssertion == latestConfirmed();
@>      bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0; //@audit-info by creatingNewChildAssertion on an invalid assertion, this check may be bypassed.
        require(isLatestConfirmed || haveChild, "STAKE_ACTIVE");
    }
```

The check ensures that the last assertion the validator staked on is the latest confirmed assertion
or that the last assertion of the user has a child. 

- Invalid assertions can have children cos stakeOnNewAssertion does not enforce that the prevAssertion is confirmed, so if another validator stakes on that invalid assertion, adversary can withdraw his stake.


## Recommmendation
Reduce the withdrawableStake of validators whose assertion was not confirmed.