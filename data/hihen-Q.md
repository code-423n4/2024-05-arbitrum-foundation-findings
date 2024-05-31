# QA Report

## Summary

### Low Issues

Total **91 instances** over **13 issues**:

|ID|Issue|Instances|
|:--:|:---|:--:|
| [[L-01]](#l-01-passing-concat-with-dynamic-arguments-to-a-hash-can-cause-collisions) | Passing `concat()` with dynamic arguments to a hash can cause collisions | 2 |
| [[L-02]](#l-02-variables-shadowing-other-definitions) | Variables shadowing other definitions | 2 |
| [[L-03]](#l-03-upgradable-contracts-need-a-constructor-to-init-and-lock-the-implementation-contract) | Upgradable contracts need a constructor to init and lock the implementation contract | 3 |
| [[L-04]](#l-04-missing-zero-address-check-in-initializer) | Missing zero address check in initializer | 1 |
| [[L-05]](#l-05-state-variables-not-limited-to-reasonable-values) | State variables not limited to reasonable values | 2 |
| [[L-06]](#l-06-contracts-are-not-using-their-oz-upgradeable-counterparts) | Contracts are not using their OZ Upgradeable counterparts | 2 |
| [[L-07]](#l-07-vulnerable-versions-of-packages-are-being-used) | Vulnerable versions of packages are being used | 8 |
| [[L-08]](#l-08-constructor--initialization-function-lacks-parameter-validation) | Constructor / initialization function lacks parameter validation | 17 |
| [[L-09]](#l-09-unsafe-solidity-low-level-call-can-cause-gas-grief-attack) | Unsafe solidity low-level call can cause gas grief attack | 1 |
| [[L-10]](#l-10-functions-calling-contractsaddresses-with-transfer-hooks-should-be-protected-by-reentrancy-guard) | Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard | 9 |
| [[L-11]](#l-11-critical-functions-should-be-controlled-by-time-locks) | Critical functions should be controlled by time locks | 11 |
| [[L-12]](#l-12-duplicate-data-may-be-pushed-to-the-array) | Duplicate data may be pushed to the array | 1 |
| [[L-13]](#l-13-code-does-not-follow-the-best-practice-of-check-effects-interaction) | Code does not follow the best practice of check-effects-interaction | 32 |

### Non Critical Issues

Total **1078 instances** over **68 issues**:

|ID|Issue|Instances|
|:--:|:---|:--:|
| [[N-01]](#n-01-import-declarations-should-import-specific-identifiers-rather-than-the-whole-file) | Import declarations should import specific identifiers, rather than the whole file | 153 |
| [[N-02]](#n-02-visibility-of-state-variables-is-not-explicitly-defined) | Visibility of state variables is not explicitly defined | 1 |
| [[N-03]](#n-03-names-of-privateinternal-functions-should-be-prefixed-with-an-underscore) | Names of `private`/`internal` functions should be prefixed with an underscore | 99 |
| [[N-04]](#n-04-names-of-privateinternal-state-variables-should-be-prefixed-with-an-underscore) | Names of `private`/`internal` state variables should be prefixed with an underscore | 10 |
| [[N-05]](#n-05-use-of-override-is-unnecessary) | Use of `override` is unnecessary | 33 |
| [[N-06]](#n-06-add-inline-comments-for-unnamed-parameters) | Add inline comments for unnamed parameters | 5 |
| [[N-07]](#n-07-consider-providing-a-ranged-getter-for-array-state-variables) | Consider providing a ranged getter for array state variables | 1 |
| [[N-08]](#n-08-consider-splitting-complex-checks-into-multiple-steps) | Consider splitting complex checks into multiple steps | 1 |
| [[N-09]](#n-09-cast-to-bytes-for-clearer-semantic-meaning) | Cast to `bytes` for clearer semantic meaning | 1 |
| [[N-10]](#n-10-missing-checks-for-empty-bytes-when-updating-bytes-state-variables) | Missing checks for empty bytes when updating bytes state variables | 4 |
| [[N-11]](#n-11-consider-adding-a-blockdeny-list) | Consider adding a block/deny-list | 4 |
| [[N-12]](#n-12-constantsimmutables-redefined-elsewhere) | Constants/Immutables redefined elsewhere | 4 |
| [[N-13]](#n-13-convert-simple-if-statements-to-ternary-expressions) | Convert simple `if`-statements to ternary expressions | 2 |
| [[N-14]](#n-14-contracts-should-each-be-defined-in-separate-files) | Contracts should each be defined in separate files | 2 |
| [[N-15]](#n-15-contract-name-does-not-match-its-filename) | Contract name does not match its filename | 3 |
| [[N-16]](#n-16-upper_case-names-should-be-reserved-for-constantimmutable-variables) | UPPER_CASE names should be reserved for `constant`/`immutable` variables | 5 |
| [[N-17]](#n-17-consider-emitting-an-event-at-the-end-of-the-constructor) | Consider emitting an event at the end of the constructor | 10 |
| [[N-18]](#n-18-empty-function-body-without-comments) | Empty function body without comments | 3 |
| [[N-19]](#n-19-events-are-emitted-without-the-sender-information) | Events are emitted without the sender information | 34 |
| [[N-20]](#n-20-inconsistent-floating-version-pragma) | Inconsistent floating version pragma | 4 |
| [[N-21]](#n-21-function-state-mutability-can-be-restricted-to-pure) | Function state mutability can be restricted to pure | 2 |
| [[N-22]](#n-22-imports-could-be-organized-more-systematically) | Imports could be organized more systematically | 28 |
| [[N-23]](#n-23-there-is-no-need-to-initialize-bool-variables-with-false) | There is no need to initialize bool variables with `false` | 1 |
| [[N-24]](#n-24-openzeppelincontracts-should-be-upgraded-to-a-newer-version) | @openzeppelin/contracts should be upgraded to a newer version | 20 |
| [[N-25]](#n-25-lib-openzeppelincontracts-upgradeable-should-be-upgraded-to-a-newer-version) | Lib @openzeppelin/contracts-upgradeable should be upgraded to a newer version | 3 |
| [[N-26]](#n-26-expressions-for-constant-values-should-use-immutable-rather-than-constant) | Expressions for constant values should use `immutable` rather than `constant` | 1 |
| [[N-27]](#n-27-consider-moving-duplicated-strings-to-constants) | Consider moving duplicated strings to constants | 22 |
| [[N-28]](#n-28-contracts-containing-only-utility-functions-should-be-made-into-libraries) | Contracts containing only utility functions should be made into libraries | 3 |
| [[N-29]](#n-29-functions-should-be-named-in-mixedcase-style) | Functions should be named in mixedCase style | 7 |
| [[N-30]](#n-30-variable-names-for-immutables-should-use-upper_case_with_underscores) | Variable names for `immutable`s should use UPPER_CASE_WITH_UNDERSCORES | 14 |
| [[N-31]](#n-31-names-of-publicexternal-functions-and-state-variables-should-not-be-prefixed-with-underscore) | Names of `public`/`external` functions and state variables should NOT be prefixed with underscore | 1 |
| [[N-32]](#n-32-overridden-function-has-no-body) | Overridden function has no body | 2 |
| [[N-33]](#n-33-named-imports-of-parent-contracts-are-missing) | Named imports of parent contracts are missing | 25 |
| [[N-34]](#n-34-constants-should-be-put-on-the-left-side-of-comparisons) | Constants should be put on the left side of comparisons | 106 |
| [[N-35]](#n-35-else-block-not-required) | `else`-block not required | 12 |
| [[N-36]](#n-36-large-multiples-of-ten-should-use-scientific-notation) | Large multiples of ten should use scientific notation | 1 |
| [[N-37]](#n-37-todos-left-in-the-code) | `TODO`s left in the code | 1 |
| [[N-38]](#n-38-high-cyclomatic-complexity) | High cyclomatic complexity | 1 |
| [[N-39]](#n-39-typos) | Typos | 18 |
| [[N-40]](#n-40-consider-bounding-input-array-length) | Consider bounding input array length | 4 |
| [[N-41]](#n-41-unnecessary-casting) | Unnecessary casting | 11 |
| [[N-42]](#n-42-unused-contract-variables) | Unused contract variables | 1 |
| [[N-43]](#n-43-unused-function-parameters) | Unused function parameters | 2 |
| [[N-44]](#n-44-unused-named-return) | Unused named return | 2 |
| [[N-45]](#n-45-use-delete-instead-of-assigning-values-to-false) | Use delete instead of assigning values to `false` | 1 |
| [[N-46]](#n-46-consider-using-delete-rather-than-assigning-zero-to-clear-values) | Consider using `delete` rather than assigning zero to clear values | 3 |
| [[N-47]](#n-47-use-the-latest-solidity-version) | Use the latest Solidity version | 24 |
| [[N-48]](#n-48-use-transfer-libraries-instead-of-low-level-calls-to-transfer-native-tokens) | Use transfer libraries instead of low level calls to transfer native tokens | 1 |
| [[N-49]](#n-49-using-underscore-at-the-end-of-variable-name) | Using underscore at the end of variable name | 27 |
| [[N-50]](#n-50-use-a-struct-to-encapsulate-multiple-function-parameters) | Use a struct to encapsulate multiple function parameters | 9 |
| [[N-51]](#n-51-returning-a-struct-instead-of-a-bunch-of-variables-is-better) | Returning a struct instead of a bunch of variables is better | 7 |
| [[N-52]](#n-52-contract-variables-should-have-comments) | Contract variables should have comments | 11 |
| [[N-53]](#n-53-missing-event-when-a-state-variables-is-set-in-constructor) | Missing event when a state variables is set in constructor | 3 |
| [[N-54]](#n-54-empty-bytes-check-is-missing) | Empty bytes check is missing | 5 |
| [[N-55]](#n-55-dont-define-functions-with-the-same-name-in-a-contract) | Don't define functions with the same name in a contract | 7 |
| [[N-56]](#n-56-multiple-mappings-with-same-keys-can-be-combined-into-a-single-struct-mapping-for-readability) | Multiple mappings with same keys can be combined into a single struct mapping for readability | 7 |
| [[N-57]](#n-57-do-not-cache-immutable-variables) | Do not cache immutable variables | 5 |
| [[N-58]](#n-58-missing-event-for-critical-changes) | Missing event for critical changes | 17 |
| [[N-59]](#n-59-consider-adding-emergency-stop-functionality) | Consider adding emergency-stop functionality | 6 |
| [[N-60]](#n-60-avoid-the-use-of-sensitive-terms) | Avoid the use of sensitive terms | 63 |
| [[N-61]](#n-61-missing-checks-for-uint-state-variable-assignments) | Missing checks for uint state variable assignments | 6 |
| [[N-62]](#n-62-use-the-modern-upgradeable-contract-paradigm) | Use the Modern Upgradeable Contract Paradigm | 11 |
| [[N-63]](#n-63-large-or-complicated-code-bases-should-implement-invariant-tests) | Large or complicated code bases should implement invariant tests | 1 |
| [[N-64]](#n-64-the-default-value-is-manually-set-when-it-is-declared) | The default value is manually set when it is declared | 23 |
| [[N-65]](#n-65-contracts-should-have-all-publicexternal-functions-exposed-by-interfaces) | Contracts should have all `public`/`external` functions exposed by `interface`s | 9 |
| [[N-66]](#n-66-top-level-declarations-should-be-separated-by-at-least-two-lines) | Top-level declarations should be separated by at least two lines | 120 |
| [[N-67]](#n-67-consider-adding-formal-verification-proofs) | Consider adding formal verification proofs | 39 |
| [[N-68]](#n-68-use-scopes-sparingly) | Use scopes sparingly | 6 |

## Low Issues

### [L-01] Passing `concat()` with dynamic arguments to a hash can cause collisions

Passing `bytes.concat()`/`string.concat()` with **multiple dynamic arguments** can cause hash collisions. It is recommended to use `abi.encode()` instead which will pad items to 32 bytes and [prevent hash collisions](https://docs.soliditylang.org/en/v0.8.20/abi-spec.html#non-standard-packed-mode).

There are 2 instances:

- *SequencerInbox.sol* ( [717-717](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L717-L717), [744-744](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L744-L744) ):

```solidity
717:         return (keccak256(bytes.concat(header, data)), timeBounds);

744:             keccak256(bytes.concat(header, DATA_BLOB_HEADER_FLAG, abi.encodePacked(dataHashes))),
```

### [L-02] Variables shadowing other definitions

A variable declaration shadowing any other existing definition is error-prone. It can cause confusion for developers, potentially introduce bugs, and reduce the readability and maintainability.

There are 2 instances:

- *BOLDUpgradeAction.sol* ( [344-344](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L344-L344), [516-516](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L516-L516) ):

```solidity
/// @audit Shadows `function stakerCount()`
344:         uint64 stakerCount = ROLLUP_READER.stakerCount();

/// @audit Shadows `state variable rollup`
516:         RollupProxy rollup = new RollupProxy{salt: rollupSalt}();
```

### [L-03] Upgradable contracts need a constructor to init and lock the implementation contract

An uninitialized contract can be taken over by an attacker. For an upgradable contract, this applies to both the proxy and its implementation contract, which may impact the proxy.
To prevent the implementation contract from being used, we should trigger the initialization in the constructor to automatically lock it when it is deployed.
For contracts that inherit `Initializable`, the `_disableInitializers()` function [is suggested to do this job](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/4d9d9073b84f56fe3eea360e5067c6ffd864c43d/contracts/proxy/utils/Initializable.sol#L43-L56).

There are 3 instances:

- *RollupAdminLogic.sol* ( [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L15) ):

```solidity
/// @audit Missing constructor to initialize the implementation contract
15: contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {
```

- *RollupCore.sol* ( [22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L22) ):

```solidity
/// @audit Missing constructor to initialize the implementation contract
22: abstract contract RollupCore is IRollupCore, PausableUpgradeable {
```

- *RollupUserLogic.sol* ( [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L15) ):

```solidity
/// @audit Missing constructor to initialize the implementation contract
15: contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {
```

### [L-04] Missing zero address check in initializer

Consider adding a zero address check for each address type parameter in initializer.

There is 1 instance:

- *EdgeChallengeManager.sol* ( [305-316](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L305-L316) ):

```solidity
/// @audit `_stakeToken not checked`
305:     function initialize(
306:         IAssertionChain _assertionChain,
307:         uint64 _challengePeriodBlocks,
308:         IOneStepProofEntry _oneStepProofEntry,
309:         uint256 layerZeroBlockEdgeHeight,
310:         uint256 layerZeroBigStepEdgeHeight,
311:         uint256 layerZeroSmallStepEdgeHeight,
312:         IERC20 _stakeToken,
313:         address _excessStakeReceiver,
314:         uint8 _numBigStepLevel,
315:         uint256[] calldata _stakeAmounts
316:     ) public initializer {
```

### [L-05] State variables not limited to reasonable values

Consider adding appropriate minimum/maximum value checks to ensure that the following state variables can never be used to excessively harm users, including via griefing.

There are 2 instances:

- *EdgeChallengeManager.sol* ( [328-328](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L328-L328) ):

```solidity
328:         challengePeriodBlocks = _challengePeriodBlocks;
```

- *RollupAdminLogic.sol* ( [205-205](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L205-L205) ):

```solidity
205:         minimumAssertionPeriod = newPeriod;
```

### [L-06] Contracts are not using their OZ Upgradeable counterparts

The non-upgradeable standard version of OpenZeppelin’s library are inherited / used by the contracts. It would be safer to use the upgradeable versions of the library contracts to avoid unexpected behavior.
Where applicable, use the contracts from `@openzeppelin/contracts-upgradeable` instead of `@openzeppelin/contracts`. See [this](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/tree/master/contracts) for list of available upgradeable contracts

There are 2 instances:

- *EdgeChallengeManager.sol* ( [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L15) ):

```solidity
15: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *BOLDUpgradeAction.sol* ( [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L8) ):

```solidity
8: import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
```

### [L-07] Vulnerable versions of packages are being used

This project is using specific package versions which are vulnerable to the specific CVEs listed below. Consider switching to more recent versions of these packages that don't have these vulnerabilities.
- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`@openzeppelin/contracts >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **MEDIUM** - (`@openzeppelin/contracts >=4.7.0 <4.9.2`): OpenZeppelin Contracts is a library for smart contract development. Starting in version 4.7.0 and prior to version 4.9.2, when the `verifyMultiProof`, `verifyMultiProofCalldata`, `procesprocessMultiProof`, or `processMultiProofCalldat` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertedly for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe. The problem has been patched in version 4.9.2. Some workarounds are available. For those using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the @openzeppelin/merkle-tree package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=4.7.0 <4.9.2`): OpenZeppelin Contracts is a library for smart contract development. Starting in version 4.7.0 and prior to version 4.9.2, when the `verifyMultiProof`, `verifyMultiProofCalldata`, `procesprocessMultiProof`, or `processMultiProofCalldat` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertedly for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe. The problem has been patched in version 4.9.2. Some workarounds are available. For those using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the @openzeppelin/merkle-tree package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.

- [CVE-2023-30542](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30542) - **HIGH** - (`@openzeppelin/contracts >=4.7.0 <4.8.2`): OpenZeppelin Contracts is a library for secure smart contract development. The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata. This issue has been patched in 4.8.3. As a workaround, ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters.

- [CVE-2023-30542](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30542) - **HIGH** - (`@openzeppelin/contracts-upgradeable >=4.7.0 <4.8.2`): OpenZeppelin Contracts is a library for secure smart contract development. The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata. This issue has been patched in 4.8.3. As a workaround, ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters.

- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** - (`@openzeppelin/contracts >=3.2.0 <4.8.3`): OpenZeppelin Contracts is a library for secure smart contract development. A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.

- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=3.2.0 <4.8.3`): OpenZeppelin Contracts is a library for secure smart contract development. A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.

There are 8 instances:

- Global finding

### [L-08] Constructor / initialization function lacks parameter validation

Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

<details>
<summary>There are 17 instances (click to show):</summary>

- *AssertionStakingPool.sol* ( [31-34](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L31-L34) ):

```solidity
/// @audit `_assertionHash`
31:     constructor(
32:         address _rollup,
33:         bytes32 _assertionHash
34:     ) AbsBoldStakingPool(IRollupCore(_rollup).stakeToken()) {
```

- *EdgeStakingPool.sol* ( [35-38](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L35-L38) ):

```solidity
/// @audit `_edgeId`
35:     constructor(
36:         address _challengeManager,
37:         bytes32 _edgeId
38:     ) AbsBoldStakingPool(address(EdgeChallengeManager(_challengeManager).stakeToken())) {
```

- *SequencerInbox.sol* ( [140-145](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L140-L145), [177-181](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L177-L181) ):

```solidity
/// @audit `_maxDataSize`
/// @audit `_isUsingFeeToken`
/// @audit `_isDelayBufferable`
140:     constructor(
141:         uint256 _maxDataSize,
142:         IReader4844 reader4844_,
143:         bool _isUsingFeeToken,
144:         bool _isDelayBufferable
145:     ) {

/// @audit `maxTimeVariation_`
/// @audit `bufferConfig_`
177:     function initialize(
178:         IBridge bridge_,
179:         ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,
180:         BufferConfig memory bufferConfig_
181:     ) external onlyDelegated {
```

- *EdgeChallengeManager.sol* ( [305-316](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L305-L316) ):

```solidity
/// @audit `layerZeroBlockEdgeHeight`
/// @audit `layerZeroBigStepEdgeHeight`
/// @audit `layerZeroSmallStepEdgeHeight`
305:     function initialize(
306:         IAssertionChain _assertionChain,
307:         uint64 _challengePeriodBlocks,
308:         IOneStepProofEntry _oneStepProofEntry,
309:         uint256 layerZeroBlockEdgeHeight,
310:         uint256 layerZeroBigStepEdgeHeight,
311:         uint256 layerZeroSmallStepEdgeHeight,
312:         IERC20 _stakeToken,
313:         address _excessStakeReceiver,
314:         uint8 _numBigStepLevel,
315:         uint256[] calldata _stakeAmounts
316:     ) public initializer {
```

- *BOLDUpgradeAction.sol* ( [169-169](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L169-L169), [287-292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L287-L292) ):

```solidity
/// @audit `__array`
169:     constructor(uint256[] memory __array) {

/// @audit `contracts`
/// @audit `proxyAdmins`
/// @audit `implementations`
/// @audit `settings`
287:     constructor(
288:         Contracts memory contracts,
289:         ProxyAdmins memory proxyAdmins,
290:         Implementations memory implementations,
291:         Settings memory settings
292:     ) {
```

- *BridgeCreator.sol* ( [45-48](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L45-L48) ):

```solidity
/// @audit `_ethBasedTemplates`
/// @audit `_erc20BasedTemplates`
45:     constructor(
46:         BridgeTemplates memory _ethBasedTemplates,
47:         BridgeTemplates memory _erc20BasedTemplates
48:     ) Ownable() {
```

</details>

### [L-09] Unsafe solidity low-level call can cause gas grief attack

Using the low-level calls of a solidity address can leave the contract open to gas grief attacks. These attacks occur when the called contract returns a large amount of data.
So when calling an external contract, it is necessary to check the length of the return data before reading/copying it (using `returndatasize()`).

There is 1 instance:

- *RollupCreator.sol* ( [304-304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L304-L304) ):

```solidity
304:             (bool sent, ) = msg.sender.call{value: address(this).balance}("");
```

### [L-10] Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks opens the users of this protocol up to [read-only reentrancy vulnerability](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect them except by block-listing the entire protocol.

<details>
<summary>There are 9 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [35-35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L35-L35), [51-51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L51-L51) ):

```solidity
35:         IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), amount);

51:         IERC20(stakeToken).safeTransfer(msg.sender, amount);
```

- *EdgeChallengeManager.sol* ( [434-434](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L434-L434), [581-581](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L581-L581) ):

```solidity
434:             st.safeTransferFrom(msg.sender, receiver, sa);

581:             st.safeTransfer(edge.staker, sa);
```

- *RollupCreator.sol* ( [312-312](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L312-L312) ):

```solidity
312:             IERC20(_nativeToken).safeTransferFrom(msg.sender, _inbox, totalFee);
```

- *RollupUserLogic.sol* ( [215-215](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L215-L215), [295-295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L295-L295), [362-362](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L362-L362), [367-367](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L367-L367) ):

```solidity
215:             IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);

295:                 IERC20(stakeToken).safeTransfer(loserStakeEscrow, assertion.beforeStateData.configData.requiredStake);

362:         IERC20(stakeToken).safeTransfer(msg.sender, amount);

367:         IERC20(stakeToken).safeTransferFrom(msg.sender, address(this), tokenAmount);
```

</details>

### [L-11] Critical functions should be controlled by time locks

It is a good practice to give time for users to react and adjust to critical changes. A timelock provides more guarantees and reduces the level of trust required, thus decreasing risk for users. It also indicates that the project is legitimate (less risk of a malicious owner making a sandwich attack on a user).

<details>
<summary>There are 11 instances (click to show):</summary>

- *SequencerInbox.sol* ( [894-897](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L894-L897), [933-936](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L933-L936), [942-942](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L942-L942) ):

```solidity
894:     function setIsBatchPoster(address addr, bool isBatchPoster_)
895:         external
896:         onlyRollupOwnerOrBatchPosterManager
897:     {

933:     function setIsSequencer(address addr, bool isSequencer_)
934:         external
935:         onlyRollupOwnerOrBatchPosterManager
936:     {

942:     function setBatchPosterManager(address newBatchPosterManager) external onlyRollupOwner {
```

- *BOLDUpgradeAction.sol* ( [411-411](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L411-L411) ):

```solidity
411:     function upgradeSurroundingContracts(address newRollupAddress) private {
```

- *BridgeCreator.sol* ( [53-53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L53-L53), [58-58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L58-L58) ):

```solidity
53:     function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {

58:     function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {
```

- *RollupAdminLogic.sol* ( [195-195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L195-L195) ):

```solidity
195:     function setOwner(address newOwner) external override {
```

- *RollupCore.sol* ( [355-355](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L355-L355) ):

```solidity
355:     function deleteStaker(address stakerAddress) private {
```

- *RollupCreator.sol* ( [63-72](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L63-L72) ):

```solidity
63:     function setTemplates(
64:         BridgeCreator _bridgeCreator,
65:         IOneStepProofEntry _osp,
66:         IEdgeChallengeManager _challengeManagerLogic,
67:         IRollupAdmin _rollupAdminLogic,
68:         IRollupUser _rollupUserLogic,
69:         IUpgradeExecutor _upgradeExecutorLogic,
70:         address _validatorWalletCreator,
71:         DeployHelper _l2FactoriesDeployer
72:     ) external onlyOwner {
```

- *RollupUserLogic.sol* ( [232-232](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L232-L232), [349-349](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L349-L349) ):

```solidity
232:     function _addToDeposit(address stakerAddress, uint256 depositAmount) internal onlyValidator whenNotPaused {

349:     function addToDeposit(address stakerAddress, uint256 tokenAmount) external onlyValidator whenNotPaused {
```

</details>

### [L-12] Duplicate data may be pushed to the array

When data is pushed into the array, it does not overwrite or remove the existing identical elements. Duplicate data added to the state array can cause problems such as operations being repeated incorrectly, assets being assigned repeatedly or weights being calculated repeatedly.

There is 1 instance:

- *RollupCore.sol* ( [276-276](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L276-L276) ):

```solidity
/// @audit createNewStake()
276:         _stakerList.push(stakerAddress);
```

### [L-13] Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

<details>
<summary>There are 32 instances (click to show):</summary>

- *EdgeStakingPool.sol* ( [39-39](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L39-L39), [40-40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L40-L40) ):

```solidity
/// @audit `stakeToken()` is called on line 38
39:         challengeManager = _challengeManager;

/// @audit `stakeToken()` is called on line 38
40:         edgeId = _edgeId;
```

- *SequencerInbox.sol* ( [816-816](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L816-L816) ):

```solidity
/// @audit `delayedMessageCount()` is called on line 807
816:         totalDelayedMessagesRead = afterDelayedMessagesRead;
```

- *BOLDUpgradeAction.sol* ( [348-348](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L348-L348), [350-350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L350-L350), [355-355](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L355-L355), [522-522](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L522-L522), [528-528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L528-L528), [530-530](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L530-L530) ):

```solidity
/// @audit `pause()` is called on line 342
348:             stakerCount = 50;

/// @audit `pause()` is called on line 342
350:         for (uint64 i = 0; i < stakerCount; i++) {

/// @audit `pause()` is called on line 342
355:                 stakersToRefund[0] = stakerAddr;

/// @audit `cleanupOldRollup()` is called on line 466, triggering an external call - `pause()`
522:         config.owner = address(this);

/// @audit `cleanupOldRollup()` is called on line 466, triggering an external call - `pause()`
528:             for (uint256 i = 0; i < validators.length; i++) {

/// @audit `cleanupOldRollup()` is called on line 466, triggering an external call - `pause()`
530:                 _vals[i] = true;
```

- *RollupAdminLogic.sol* ( [29-29](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L29-L29), [30-30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L30-L30), [32-32](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L32-L32), [44-44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L44-L44), [45-45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L45-L45), [47-47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L47-L47), [48-48](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L48-L48), [49-49](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L49-L49), [50-50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L50-L50), [52-52](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L52-L52), [53-53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L53-L53), [58-58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L58-L58), [60-60](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L60-L60), [61-61](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L61-L61), [74-74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L74-L74), [89-89](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L89-L89), [102-102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L102-L102) ):

```solidity
/// @audit `setDelayedInbox()` is called on line 26
29:         inbox = connectedContracts.inbox;

/// @audit `setDelayedInbox()` is called on line 26
30:         outbox = connectedContracts.outbox;

/// @audit `setDelayedInbox()` is called on line 26
32:         rollupEventInbox = connectedContracts.rollupEventInbox;

/// @audit `setDelayedInbox()` is called on line 26
44:         validatorWalletCreator = connectedContracts.validatorWalletCreator;

/// @audit `setDelayedInbox()` is called on line 26
45:         challengeManager = connectedContracts.challengeManager;

/// @audit `setDelayedInbox()` is called on line 26
47:         confirmPeriodBlocks = config.confirmPeriodBlocks;

/// @audit `setDelayedInbox()` is called on line 26
48:         chainId = config.chainId;

/// @audit `setDelayedInbox()` is called on line 26
49:         baseStake = config.baseStake;

/// @audit `setDelayedInbox()` is called on line 26
50:         wasmModuleRoot = config.wasmModuleRoot;

/// @audit `setDelayedInbox()` is called on line 26
52:         minimumAssertionPeriod = 75;

/// @audit `setDelayedInbox()` is called on line 26
53:         challengeGracePeriodBlocks = config.challengeGracePeriodBlocks;

/// @audit `setDelayedInbox()` is called on line 26
58:         loserStakeEscrow = config.loserStakeEscrow;

/// @audit `setDelayedInbox()` is called on line 26
60:         stakeToken = config.stakeToken;

/// @audit `setDelayedInbox()` is called on line 26
61:         anyTrustFastConfirmer = config.anyTrustFastConfirmer;

/// @audit `setDelayedInbox()` is called on line 26
74:             currentInboxCount += 1;

/// @audit `setDelayedInbox()` is called on line 26
89:         assertionInputs.afterState = config.genesisAssertionState;

/// @audit `setDelayedInbox()` is called on line 26
102:             _assertionCreatedAtArbSysBlock[genesisHash] = ArbSys(address(100)).arbBlockNumber();
```

- *RollupCore.sol* ( [263-263](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L263-L263), [264-264](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L264-L264) ):

```solidity
/// @audit `updateSendRoot()` is called on line 261
263:         _latestConfirmed = assertionHash;

/// @audit `updateSendRoot()` is called on line 261
264:         assertion.status = AssertionStatus.Confirmed;
```

- *RollupCreator.sol* ( [208-208](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L208-L208), [225-225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L225-L225), [235-235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L235-L235), [236-236](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L236-L236) ):

```solidity
/// @audit `()` is called on line 188
208:         deployParams.config.owner = address(this);

/// @audit `()` is called on line 188
225:         for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {

/// @audit `()` is called on line 188
235:             for (uint256 i = 0; i < deployParams.validators.length; i++) {

/// @audit `()` is called on line 188
236:                 _vals[i] = true;
```

</details>

## Non Critical Issues

### [N-01] Import declarations should import specific identifiers, rather than the whole file

Using import declarations of the form `import {<identifier_name>} from "some/file.sol"` avoids polluting the symbol namespace making flattened files smaller, and speeds up compilation (but does not save any gas).

<details>
<summary>There are 153 instances (click to show):</summary>

- *AssertionStakingPool.sol* ( [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L11) ):

```solidity
8: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

9: import "../rollup/IRollupLogic.sol";

10: import "./AbsBoldStakingPool.sol";

11: import "./interfaces/IAssertionStakingPool.sol";
```

- *AssertionStakingPoolCreator.sol* ( [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L10) ):

```solidity
8: import "./AssertionStakingPool.sol";

9: import "./StakingPoolCreatorUtils.sol";

10: import "./interfaces/IAssertionStakingPoolCreator.sol";
```

- *EdgeStakingPool.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L9), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L12) ):

```solidity
7: import "./AbsBoldStakingPool.sol";

8: import "./interfaces/IEdgeStakingPool.sol";

9: import "../challengeV2/EdgeChallengeManager.sol";

11: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

12: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *EdgeStakingPoolCreator.sol* ( [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L10) ):

```solidity
8: import "./EdgeStakingPool.sol";

9: import "./StakingPoolCreatorUtils.sol";

10: import "./interfaces/IEdgeStakingPoolCreator.sol";
```

- *StakingPoolCreatorUtils.sol* ( [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L9) ):

```solidity
8: import "@openzeppelin/contracts/utils/Create2.sol";

9: import "@openzeppelin/contracts/utils/Address.sol";
```

- *IAssertionStakingPool.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L8) ):

```solidity
7: import "../../rollup/IRollupLogic.sol";

8: import "./IAbsBoldStakingPool.sol";
```

- *IAssertionStakingPoolCreator.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L8) ):

```solidity
7: import "../../rollup/IRollupLogic.sol";

8: import "./IAssertionStakingPool.sol";
```

- *IEdgeStakingPool.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L8) ):

```solidity
7: import "../../challengeV2/EdgeChallengeManager.sol";

8: import "./IAbsBoldStakingPool.sol";
```

- *IEdgeStakingPoolCreator.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L7) ):

```solidity
7: import "./IEdgeStakingPool.sol";
```

- *DelayBuffer.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L8) ):

```solidity
7: import "./Messages.sol";

8: import "./DelayBufferTypes.sol";
```

- *DelayBufferTypes.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBufferTypes.sol#L5) ):

```solidity
5: import "./Messages.sol";
```

- *ISequencerInbox.sol* ( [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L13) ):

```solidity
9: import "../libraries/IGasRefunder.sol";

10: import "./IDelayedMessageProvider.sol";

11: import "./IBridge.sol";

12: import "./Messages.sol";

13: import "./DelayBufferTypes.sol";
```

- *SequencerInbox.sol* ( [40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L40), [41](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L41), [42](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L42), [43](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L43), [44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L44), [45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L45), [46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L46), [47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L47), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L50), [53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L53), [55](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L55) ):

```solidity
40: import "./IBridge.sol";

41: import "./IInboxBase.sol";

42: import "./ISequencerInbox.sol";

43: import "../rollup/IRollupLogic.sol";

44: import "./Messages.sol";

45: import "../precompiles/ArbGasInfo.sol";

46: import "../precompiles/ArbSys.sol";

47: import "../libraries/IReader4844.sol";

50: import "../libraries/DelegateCallAware.sol";

53: import "../libraries/ArbitrumChecker.sol";

55: import "./DelayBuffer.sol";
```

- *EdgeChallengeManager.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L12), [14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L14), [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L15) ):

```solidity
7: import "../rollup/Assertion.sol";

8: import "./libraries/UintUtilsLib.sol";

9: import "./IAssertionChain.sol";

10: import "./libraries/EdgeChallengeManagerLib.sol";

11: import "../libraries/Constants.sol";

12: import "../state/Machine.sol";

14: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";

15: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *IAssertionChain.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/IAssertionChain.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/IAssertionChain.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/IAssertionChain.sol#L9) ):

```solidity
7: import "../bridge/IBridge.sol";

8: import "../osp/IOneStepProofEntry.sol";

9: import "../rollup/Assertion.sol";
```

- *ChallengeEdgeLib.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L8) ):

```solidity
7: import "./Enums.sol";

8: import "./ChallengeErrors.sol";
```

- *ChallengeErrors.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeErrors.sol#L7) ):

```solidity
7: import "./Enums.sol";
```

- *EdgeChallengeManagerLib.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L13) ):

```solidity
7: import "./UintUtilsLib.sol";

8: import "./MerkleTreeLib.sol";

9: import "./ChallengeEdgeLib.sol";

10: import "../../osp/IOneStepProofEntry.sol";

11: import "../../rollup/AssertionState.sol";

12: import "../../libraries/Constants.sol";

13: import "./ChallengeErrors.sol";
```

- *MerkleTreeLib.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L9) ):

```solidity
7: import "../../libraries/MerkleLib.sol";

8: import "./ArrayUtilsLib.sol";

9: import "./UintUtilsLib.sol";
```

- *Assertion.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L7) ):

```solidity
7: import "./AssertionState.sol";
```

- *AssertionState.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L9) ):

```solidity
7: import "../state/GlobalState.sol";

8: import "../state/Machine.sol";

9: import "../osp/IOneStepProofEntry.sol";
```

- *BOLDUpgradeAction.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L11) ):

```solidity
7: import "@openzeppelin/contracts-upgradeable/utils/Create2Upgradeable.sol";

8: import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";

9: import "./RollupProxy.sol";

10: import "./RollupLib.sol";

11: import "./RollupAdminLogic.sol";
```

- *BridgeCreator.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L13), [14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L14), [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L15), [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L17), [18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L18), [19](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L19) ):

```solidity
7: import "../bridge/Bridge.sol";

8: import "../bridge/SequencerInbox.sol";

9: import "../bridge/Inbox.sol";

10: import "../bridge/Outbox.sol";

11: import "./RollupEventInbox.sol";

12: import "../bridge/ERC20Bridge.sol";

13: import "../bridge/ERC20Inbox.sol";

14: import "../rollup/ERC20RollupEventInbox.sol";

15: import "../bridge/ERC20Outbox.sol";

17: import "../bridge/IBridge.sol";

18: import "@openzeppelin/contracts/access/Ownable.sol";

19: import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
```

- *Config.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L13), [14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L14), [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L15) ):

```solidity
7: import "../state/GlobalState.sol";

8: import "../state/Machine.sol";

9: import "../bridge/ISequencerInbox.sol";

10: import "../bridge/IBridge.sol";

11: import "../bridge/IOutbox.sol";

12: import "../bridge/IInboxBase.sol";

13: import "./IRollupEventInbox.sol";

14: import "./IRollupLogic.sol";

15: import "../challengeV2/EdgeChallengeManager.sol";
```

- *IRollupAdmin.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L11) ):

```solidity
7: import "./IRollupCore.sol";

8: import "../bridge/ISequencerInbox.sol";

9: import "../bridge/IOutbox.sol";

10: import "../bridge/IOwnable.sol";

11: import "./Config.sol";
```

- *IRollupCore.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L13) ):

```solidity
7: import "./Assertion.sol";

8: import "../bridge/IBridge.sol";

9: import "../bridge/IOutbox.sol";

10: import "../bridge/IInboxBase.sol";

11: import "./IRollupEventInbox.sol";

12: import "../challengeV2/EdgeChallengeManager.sol";

13: import "../challengeV2/IAssertionChain.sol";
```

- *IRollupLogic.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L10) ):

```solidity
7: import "./IRollupCore.sol";

8: import "../bridge/ISequencerInbox.sol";

9: import "../bridge/IOutbox.sol";

10: import "../bridge/IOwnable.sol";
```

- *RollupAdminLogic.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L13) ):

```solidity
7: import "./IRollupAdmin.sol";

8: import "./IRollupLogic.sol";

9: import "./RollupCore.sol";

10: import "../bridge/IOutbox.sol";

11: import "../bridge/ISequencerInbox.sol";

12: import "../libraries/DoubleLogicUUPSUpgradeable.sol";

13: import "@openzeppelin/contracts/proxy/beacon/UpgradeableBeacon.sol";
```

- *RollupCore.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L7), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L12), [14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L14), [16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L16), [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L17), [18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L18), [19](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L19), [20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L20) ):

```solidity
7: import "@openzeppelin/contracts-upgradeable/security/PausableUpgradeable.sol";

9: import "./Assertion.sol";

10: import "./RollupLib.sol";

11: import "./IRollupEventInbox.sol";

12: import "./IRollupCore.sol";

14: import "../state/Machine.sol";

16: import "../bridge/ISequencerInbox.sol";

17: import "../bridge/IBridge.sol";

18: import "../bridge/IOutbox.sol";

19: import "../challengeV2/EdgeChallengeManager.sol";

20: import "../libraries/ArbitrumChecker.sol";
```

- *RollupCreator.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L9), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L13) ):

```solidity
7: import "./RollupProxy.sol";

8: import "./IRollupAdmin.sol";

9: import "./BridgeCreator.sol";

10: import "@offchainlabs/upgrade-executor/src/IUpgradeExecutor.sol";

11: import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";

12: import "@openzeppelin/contracts/proxy/transparent/TransparentUpgradeableProxy.sol";

13: import "@openzeppelin/contracts/access/Ownable.sol";
```

- *RollupLib.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L8), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L13), [14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L14), [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L15) ):

```solidity
7: import "../state/GlobalState.sol";

8: import "../bridge/ISequencerInbox.sol";

10: import "../bridge/IBridge.sol";

11: import "../bridge/IOutbox.sol";

12: import "../bridge/IInboxBase.sol";

13: import "./Assertion.sol";

14: import "./IRollupEventInbox.sol";

15: import "../challengeV2/EdgeChallengeManager.sol";
```

- *RollupProxy.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L9) ):

```solidity
7: import "../libraries/AdminFallbackProxy.sol";

8: import "./IRollupAdmin.sol";

9: import "./Config.sol";
```

- *RollupUserLogic.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L7), [10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L10), [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L12) ):

```solidity
7: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

10: import "../libraries/UUPSNotUpgradeable.sol";

11: import "./RollupCore.sol";

12: import "./IRollupLogic.sol";
```

</details>

### [N-02] Visibility of state variables is not explicitly defined

To avoid misunderstandings and unexpected state accesses, it is recommended to explicitly define the visibility of each state variable.

There is 1 instance:

- *BOLDUpgradeAction.sol* ( [167-167](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L167-L167) ):

```solidity
167:     uint256[] _array;
```

### [N-03] Names of `private`/`internal` functions should be prefixed with an underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

<details>
<summary>There are 99 instances (click to show):</summary>

- *StakingPoolCreatorUtils.sol* ( [13-13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L13-L13) ):

```solidity
13:     function getPool(bytes memory creationCode, bytes memory args) internal view returns (address) {
```

- *DelayBuffer.sol* ( [33-41](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L33-L41), [68-68](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L68-L68), [82-85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L82-L85), [104-104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L104-L104), [108-108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L108-L108), [115-115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L115-L115) ):

```solidity
33:     function calcBuffer(
34:         uint256 start,
35:         uint256 end,
36:         uint256 buffer,
37:         uint256 sequenced,
38:         uint256 threshold,
39:         uint256 max,
40:         uint256 replenishRateInBasis
41:     ) internal pure returns (uint256) {

68:     function update(BufferData storage self, uint64 blockNumber) internal {

82:     function calcPendingBuffer(BufferData storage self, uint64 blockNumber)
83:         internal
84:         view
85:         returns (uint64)

104:     function isSynced(BufferData storage self) internal view returns (bool) {

108:     function isUpdatable(BufferData storage self) internal view returns (bool) {

115:     function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {
```

- *SequencerInbox.sol* ( [216-216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L216-L216), [269-277](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L269-L277), [455-460](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L455-L460), [512-519](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L512-L519), [605-607](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L605-L607), [628-628](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L628-L628), [637-640](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L637-L640), [659-662](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L659-L662), [675-675](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L675-L675), [688-691](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L688-L691), [725-733](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L725-L733), [755-760](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L755-L760), [791-804](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L791-L804), [843-843](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L843-L843) ):

```solidity
216:     function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {

269:     function maxTimeVariationInternal()
270:         internal
271:         view
272:         returns (
273:             uint64,
274:             uint64,
275:             uint64,
276:             uint64
277:         )

455:     function addSequencerL2BatchFromBlobsImpl(
456:         uint256 sequenceNumber,
457:         uint256 afterDelayedMessagesRead,
458:         uint256 prevMessageCount,
459:         uint256 newMessageCount
460:     ) internal {

512:     function addSequencerL2BatchFromCalldataImpl(
513:         uint256 sequenceNumber,
514:         bytes calldata data,
515:         uint256 afterDelayedMessagesRead,
516:         uint256 prevMessageCount,
517:         uint256 newMessageCount,
518:         bool isFromOrigin
519:     ) internal {

605:     function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)
606:         internal
607:     {

628:     function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {

637:     function packHeader(uint256 afterDelayedMessagesRead)
638:         internal
639:         view
640:         returns (bytes memory, IBridge.TimeBounds memory)

659:     function formEmptyDataHash(uint256 afterDelayedMessagesRead)
660:         internal
661:         view
662:         returns (bytes32, IBridge.TimeBounds memory)

675:     function isValidCallDataFlag(bytes1 headerByte) internal pure returns (bool) {

688:     function formCallDataHash(bytes calldata data, uint256 afterDelayedMessagesRead)
689:         internal
690:         view
691:         returns (bytes32, IBridge.TimeBounds memory)

725:     function formBlobDataHash(uint256 afterDelayedMessagesRead)
726:         internal
727:         view
728:         virtual
729:         returns (
730:             bytes32,
731:             IBridge.TimeBounds memory,
732:             uint256
733:         )

755:     function submitBatchSpendingReport(
756:         bytes32 dataHash,
757:         uint256 seqMessageIndex,
758:         uint256 gasPrice,
759:         uint256 extraGas
760:     ) internal {

791:     function addSequencerL2BatchImpl(
792:         bytes32 dataHash,
793:         uint256 afterDelayedMessagesRead,
794:         uint256 calldataLengthPosted,
795:         uint256 prevMessageCount,
796:         uint256 newMessageCount
797:     )
798:         internal
799:         returns (
800:             uint256 seqMessageIndex,
801:             bytes32 beforeAcc,
802:             bytes32 delayedAcc,
803:             bytes32 acc
804:         )

843:     function delayBufferableBlocks(uint64 _buffer) internal view returns (uint64) {
```

- *ArrayUtilsLib.sol* ( [13-13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L13-L13), [27-30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L27-L30), [45-45](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L45-L45) ):

```solidity
13:     function append(bytes32[] memory arr, bytes32 newItem) internal pure returns (bytes32[] memory) {

27:     function slice(bytes32[] memory arr, uint256 startIndex, uint256 endIndex)
28:         internal
29:         pure
30:         returns (bytes32[] memory)

45:     function concat(bytes32[] memory arr1, bytes32[] memory arr2) internal pure returns (bytes32[] memory) {
```

- *ChallengeEdgeLib.sol* ( [69-75](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L69-L75), [93-102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L93-L102), [133-140](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L133-L140), [166-172](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L166-L172), [180-180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L180-L180), [184-184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L184-L184), [189-196](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L189-L196), [208-208](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L208-L208), [215-215](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L215-L215), [222-222](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L222-L222), [228-228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L228-L228), [239-239](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L239-L239), [249-249](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L249-L249), [258-258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L258-L258), [264-264](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L264-L264), [279-279](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L279-L279) ):

```solidity
69:     function newEdgeChecks(
70:         bytes32 originId,
71:         bytes32 startHistoryRoot,
72:         uint256 startHeight,
73:         bytes32 endHistoryRoot,
74:         uint256 endHeight
75:     ) internal pure {

93:     function newLayerZeroEdge(
94:         bytes32 originId,
95:         bytes32 startHistoryRoot,
96:         uint256 startHeight,
97:         bytes32 endHistoryRoot,
98:         uint256 endHeight,
99:         bytes32 claimId,
100:         address staker,
101:         uint8 level
102:     ) internal view returns (ChallengeEdge memory) {

133:     function newChildEdge(
134:         bytes32 originId,
135:         bytes32 startHistoryRoot,
136:         uint256 startHeight,
137:         bytes32 endHistoryRoot,
138:         uint256 endHeight,
139:         uint8 level
140:     ) internal view returns (ChallengeEdge memory) {

166:     function mutualIdComponent(
167:         uint8 level,
168:         bytes32 originId,
169:         uint256 startHeight,
170:         bytes32 startHistoryRoot,
171:         uint256 endHeight
172:     ) internal pure returns (bytes32) {

180:     function mutualId(ChallengeEdge storage ce) internal view returns (bytes32) {

184:     function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {

189:     function idComponent(
190:         uint8 level,
191:         bytes32 originId,
192:         uint256 startHeight,
193:         bytes32 startHistoryRoot,
194:         uint256 endHeight,
195:         bytes32 endHistoryRoot
196:     ) internal pure returns (bytes32) {

208:     function idMem(ChallengeEdge memory edge) internal pure returns (bytes32) {

215:     function id(ChallengeEdge storage edge) internal view returns (bytes32) {

222:     function exists(ChallengeEdge storage edge) internal view returns (bool) {

228:     function length(ChallengeEdge storage edge) internal view returns (uint256) {

239:     function setChildren(ChallengeEdge storage edge, bytes32 lowerChildId, bytes32 upperChildId) internal {

249:     function setConfirmed(ChallengeEdge storage edge) internal {

258:     function isLayerZero(ChallengeEdge storage edge) internal view returns (bool) {

264:     function setRefunded(ChallengeEdge storage edge) internal {

279:     function levelToType(uint8 level, uint8 numBigStepLevels) internal pure returns (EdgeType eType) {
```

- *EdgeChallengeManagerLib.sol* ( [141-141](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L141-L141), [152-152](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L152-L152), [160-160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L160-L160), [213-219](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L213-L219), [327-327](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L327-L327), [344-347](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L344-L347), [391-394](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L391-L394), [411-419](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L411-L419), [443-443](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L443-L443), [463-463](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L463-L463), [483-483](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L483-L483), [488-488](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L488-L488), [502-504](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L502-L504), [516-516](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L516-L516), [520-525](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L520-L525), [537-537](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L537-L537), [576-576](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L576-L576), [604-606](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L604-L606), [662-662](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L662-L662), [674-674](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L674-L674), [689-692](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L689-L692), [723-728](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L723-L728), [766-777](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L766-L777) ):

```solidity
141:     function get(EdgeStore storage store, bytes32 edgeId) internal view returns (ChallengeEdge storage) {

152:     function getNoCheck(EdgeStore storage store, bytes32 edgeId) internal view returns (ChallengeEdge storage) {

160:     function add(EdgeStore storage store, ChallengeEdge memory edge) internal returns (EdgeAddedData memory) {

213:     function layerZeroTypeSpecificChecks(
214:         EdgeStore storage store,
215:         CreateEdgeArgs calldata args,
216:         AssertionReferenceData memory ard,
217:         IOneStepProofEntry oneStepProofEntry,
218:         uint8 numBigStepLevel
219:     ) private view returns (ProofData memory, bytes32) {

327:     function isPowerOfTwo(uint256 x) internal pure returns (bool) {

344:     function layerZeroCommonChecks(ProofData memory proofData, CreateEdgeArgs calldata args, uint256 expectedEndHeight)
345:         private
346:         pure
347:         returns (bytes32)

391:     function toLayerZeroEdge(bytes32 originId, bytes32 startHistoryRoot, CreateEdgeArgs calldata args)
392:         private
393:         view
394:         returns (ChallengeEdge memory)

411:     function createLayerZeroEdge(
412:         EdgeStore storage store,
413:         CreateEdgeArgs calldata args,
414:         AssertionReferenceData memory ard,
415:         IOneStepProofEntry oneStepProofEntry,
416:         uint256 expectedEndHeight,
417:         uint8 numBigStepLevel,
418:         bool whitelistEnabled
419:     ) internal returns (EdgeAddedData memory) {

443:     function getPrevAssertionHash(EdgeStore storage store, bytes32 edgeId) internal view returns (bytes32) {

463:     function hasRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {

483:     function hasLengthOneRival(EdgeStore storage store, bytes32 edgeId) internal view returns (bool) {

488:     function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {

502:     function updateTimerCache(EdgeStore storage store, bytes32 edgeId, uint256 newValue)
503:         internal
504:         returns (bool, uint256)

516:     function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {

520:     function updateTimerCacheByClaim(
521:         EdgeStore storage store,
522:         bytes32 edgeId,
523:         bytes32 claimingEdgeId,
524:         uint8 numBigStepLevel
525:     ) internal returns (bool, uint256) {

537:     function timeUnrivaled(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {

576:     function mandatoryBisectionHeight(uint256 start, uint256 end) internal pure returns (uint256) {

604:     function bisectEdge(EdgeStore storage store, bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes memory prefixProof)
605:         internal
606:         returns (bytes32, EdgeAddedData memory, EdgeAddedData memory)

662:     function setConfirmedRival(EdgeStore storage store, bytes32 edgeId) internal {

674:     function nextEdgeLevel(uint8 level, uint8 numBigStepLevel) internal pure returns (uint8) {

689:     function checkClaimIdLink(EdgeStore storage store, bytes32 edgeId, bytes32 claimingEdgeId, uint8 numBigStepLevel)
690:         private
691:         view
692:     {

723:     function confirmEdgeByTime(
724:         EdgeStore storage store,
725:         bytes32 edgeId,
726:         uint64 claimedAssertionUnrivaledBlocks,
727:         uint64 confirmationThresholdBlock
728:     ) internal returns (uint256) {

766:     function confirmEdgeByOneStepProof(
767:         EdgeStore storage store,
768:         bytes32 edgeId,
769:         IOneStepProofEntry oneStepProofEntry,
770:         OneStepData calldata oneStepData,
771:         ExecutionContext memory execCtx,
772:         bytes32[] calldata beforeHistoryInclusionProof,
773:         bytes32[] calldata afterHistoryInclusionProof,
774:         uint8 numBigStepLevel,
775:         uint256 bigStepHeight,
776:         uint256 smallStepHeight
777:     ) internal {
```

- *MerkleTreeLib.sol* ( [110-110](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L110-L110), [151-154](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L151-L154), [238-238](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L238-L238), [251-251](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L251-L251), [292-292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L292-L292), [312-319](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L312-L319), [359-362](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L359-L362) ):

```solidity
110:     function root(bytes32[] memory me) internal pure returns (bytes32) {

151:     function appendCompleteSubTree(bytes32[] memory me, uint256 level, bytes32 subtreeRoot)
152:         internal
153:         pure
154:         returns (bytes32[] memory)

238:     function appendLeaf(bytes32[] memory me, bytes32 leaf) internal pure returns (bytes32[] memory) {

251:     function maximumAppendBetween(uint256 startSize, uint256 endSize) internal pure returns (uint256) {

292:     function treeSize(bytes32[] memory me) internal pure returns (uint256) {

312:     function verifyPrefixProof(
313:         bytes32 preRoot,
314:         uint256 preSize,
315:         bytes32 postRoot,
316:         uint256 postSize,
317:         bytes32[] memory preExpansion,
318:         bytes32[] memory proof
319:     ) internal pure {

359:     function verifyInclusionProof(bytes32 rootHash, bytes32 leaf, uint256 index, bytes32[] memory proof)
360:         internal
361:         pure
362:     {
```

- *UintUtilsLib.sol* ( [14-14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L14-L14), [29-29](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L29-L29) ):

```solidity
14:     function leastSignificantBit(uint256 x) internal pure returns (uint256 msb) {

29:     function mostSignificantBit(uint256 x) internal pure returns (uint256 msb) {
```

- *Assertion.sol* ( [70-73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L70-L73), [85-85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L85-L85), [93-93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L93-L93) ):

```solidity
70:     function createAssertion(
71:         bool _isFirstChild,
72:         bytes32 _configHash
73:     ) internal view returns (AssertionNode memory) {

85:     function childCreated(AssertionNode storage self) internal {

93:     function requireExists(AssertionNode memory self) internal pure {
```

- *AssertionState.sol* ( [18-18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L18-L18), [22-22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L22-L22) ):

```solidity
18:     function toExecutionState(AssertionState memory state) internal pure returns (ExecutionState memory) {

22:     function hash(AssertionState memory state) internal pure returns (bytes32) {
```

- *BOLDUpgradeAction.sol* ( [341-341](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L341-L341), [367-367](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L367-L367), [411-411](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L411-L411), [433-433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L433-L433) ):

```solidity
341:     function cleanupOldRollup() private {

367:     function createConfig() private view returns (Config memory) {

411:     function upgradeSurroundingContracts(address newRollupAddress) private {

433:     function upgradeSequencerInbox() private {
```

- *RollupCore.sol* ( [126-126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L126-L126), [225-225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L225-L225), [236-241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L236-L241), [274-274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L274-L274), [286-286](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L286-L286), [300-300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L300-L300), [317-317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L317-L317), [331-331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L331-L331), [343-343](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L343-L343), [355-355](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L355-L355), [365-369](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L365-L369), [565-565](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L565-L565) ):

```solidity
126:     function getAssertionStorage(bytes32 assertionHash) internal view returns (AssertionNode storage) {

225:     function initializeCore(AssertionNode memory initialAssertion, bytes32 assertionHash) internal {

236:     function confirmAssertionInternal(
237:         bytes32 assertionHash,
238:         bytes32 parentAssertionHash,
239:         AssertionState calldata confirmState,
240:         bytes32 inboxAcc
241:     ) internal {

274:     function createNewStake(address stakerAddress, uint256 depositAmount, address withdrawalAddress) internal {

286:     function increaseStakeBy(address stakerAddress, uint256 amountAdded) internal {

300:     function reduceStakeTo(address stakerAddress, uint256 target) internal returns (uint256) {

317:     function withdrawStaker(address stakerAddress) internal {

331:     function withdrawFunds(address account) internal returns (uint256) {

343:     function increaseWithdrawableFunds(address account, uint256 amount) internal {

355:     function deleteStaker(address stakerAddress) private {

365:     function createNewAssertion(
366:         AssertionInputs calldata assertion,
367:         bytes32 prevAssertionHash,
368:         bytes32 expectedAssertionHash
369:     ) internal returns (bytes32 newAssertionHash, bool overflowAssertion) {

565:     function requireInactiveStaker(address stakerAddress) internal view {
```

- *RollupCreator.sol* ( [85-87](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L85-L87) ):

```solidity
85:     function createChallengeManager(address rollupAddr, address proxyAdminAddr, Config memory config)
86:         internal
87:         returns (IEdgeChallengeManager)
```

- *RollupLib.sol* ( [23-27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L23-L27), [37-41](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L37-L41), [54-60](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L54-L60), [73-76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L73-L76) ):

```solidity
23:     function assertionHash(
24:         bytes32 parentAssertionHash,
25:         AssertionState memory afterState,
26:         bytes32 inboxAcc
27:     ) internal pure returns (bytes32) {

37:     function assertionHash(
38:         bytes32 parentAssertionHash,
39:         bytes32 afterStateHash,
40:         bytes32 inboxAcc
41:     ) internal pure returns (bytes32) {

54:     function configHash(
55:         bytes32 wasmModuleRoot,
56:         uint256 requiredStake,
57:         address challengeManager,
58:         uint64 confirmPeriodBlocks,
59:         uint64 nextInboxPosition
60:     ) internal pure returns (bytes32) {

73:     function validateConfigHash(
74:         ConfigData calldata configData,
75:         bytes32 _configHash
76:     ) internal pure {
```

- *RollupUserLogic.sol* ( [366-366](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L366-L366) ):

```solidity
366:     function receiveTokens(uint256 tokenAmount) private {
```

</details>

### [N-04] Names of `private`/`internal` state variables should be prefixed with an underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

<details>
<summary>There are 10 instances (click to show):</summary>

- *SequencerInbox.sol* ( [91-91](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L91-L91), [119-119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L119-L119), [120-120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L120-L120), [121-121](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L121-L121), [122-122](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L122-L122), [129-129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L129-L129), [131-131](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L131-L131) ):

```solidity
91:     uint256 internal constant GAS_PER_BLOB = 1 << 17;

119:     uint64 internal delayBlocks;

120:     uint64 internal futureBlocks;

121:     uint64 internal delaySeconds;

122:     uint64 internal futureSeconds;

129:     uint256 internal immutable deployTimeChainId = block.chainid;

131:     bool internal immutable hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();
```

- *EdgeChallengeManager.sol* ( [266-266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L266-L266) ):

```solidity
266:     EdgeStore internal store;
```

- *BOLDUpgradeAction.sol* ( [99-99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L99-L99) ):

```solidity
99:     mapping(bytes32 => bytes) internal preImages;
```

- *RollupUserLogic.sol* ( [31-31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L31-L31) ):

```solidity
31:     uint256 internal immutable deployTimeChainId = block.chainid;
```

</details>

### [N-05] Use of `override` is unnecessary

[Starting from Solidity 0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), the override keyword is not required when overriding an interface function, except for the case where the function is defined in multiple bases.

<details>
<summary>There are 33 instances (click to show):</summary>

- *SequencerInbox.sol* ( [560-567](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L560-L567) ):

```solidity
560:     function addSequencerL2Batch(
561:         uint256 sequenceNumber,
562:         bytes calldata data,
563:         uint256 afterDelayedMessagesRead,
564:         IGasRefunder gasRefunder,
565:         uint256 prevMessageCount,
566:         uint256 newMessageCount
567:     ) external override refundsGas(gasRefunder, IReader4844(address(0))) {
```

- *RollupAdminLogic.sol* ( [18-23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L18-L23), [117-117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L117-L117), [127-127](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L127-L127), [138-138](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L138-L138), [150-150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L150-L150), [158-158](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L158-L158), [166-166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L166-L166), [171-171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L171-L171), [180-180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L180-L180), [195-195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L195-L195), [204-204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L204-L204), [213-213](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L213-L213), [223-223](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L223-L223), [228-228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L228-L228), [237-241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L237-L241), [258-263](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L258-L263), [269-269](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L269-L269), [281-281](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L281-L281), [290-290](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L290-L290) ):

```solidity
18:     function initialize(Config calldata config, ContractDependencies calldata connectedContracts)
19:         external
20:         override
21:         onlyProxy
22:         initializer
23:     {

117:     function setOutbox(IOutbox _outbox) external override {

127:     function removeOldOutbox(address _outbox) external override {

138:     function setDelayedInbox(address _inbox, bool _enabled) external override {

150:     function pause() external override {

158:     function resume() external override {

166:     function _authorizeUpgrade(address newImplementation) internal override {}

171:     function _authorizeSecondaryUpgrade(address newImplementation) internal override {}

180:     function setValidator(address[] calldata _validator, bool[] calldata _val) external override {

195:     function setOwner(address newOwner) external override {

204:     function setMinimumAssertionPeriod(uint256 newPeriod) external override {

213:     function setConfirmPeriodBlocks(uint64 newConfirmPeriod) external override {

223:     function setBaseStake(uint256 newBaseStake) external override {

228:     function forceRefundStaker(address[] calldata staker) external override whenPaused {

237:     function forceCreateAssertion(
238:         bytes32 prevAssertionHash,
239:         AssertionInputs calldata assertion,
240:         bytes32 expectedAssertionHash
241:     ) external override whenPaused {

258:     function forceConfirmAssertion(
259:         bytes32 assertionHash,
260:         bytes32 parentAssertionHash,
261:         AssertionState calldata confirmState,
262:         bytes32 inboxAcc
263:     ) external override whenPaused {

269:     function setLoserStakeEscrow(address newLoserStakerEscrow) external override {

281:     function setWasmModuleRoot(bytes32 newWasmModuleRoot) external override {

290:     function setSequencerInbox(address _sequencerInbox) external override {
```

- *RollupCore.sol* ( [134-134](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L134-L134), [145-145](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L145-L145), [162-162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L162-L162), [171-171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L171-L171), [180-180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L180-L180), [189-189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L189-L189), [198-198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L198-L198), [207-207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L207-L207), [212-212](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L212-L212), [217-217](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L217-L217) ):

```solidity
134:     function getAssertion(bytes32 assertionHash) public view override returns (AssertionNode memory) {

145:     function getAssertionCreationBlockForLogLookup(bytes32 assertionHash) external view override returns (uint256) {

162:     function getStakerAddress(uint64 stakerNum) external view override returns (address) {

171:     function isStaked(address staker) public view override returns (bool) {

180:     function latestStakedAssertion(address staker) public view override returns (bytes32) {

189:     function amountStaked(address staker) public view override returns (uint256) {

198:     function getStaker(address staker) external view override returns (Staker memory) {

207:     function withdrawableFunds(address user) external view override returns (uint256) {

212:     function latestConfirmed() public view override returns (bytes32) {

217:     function stakerCount() public view override returns (uint64) {
```

- *RollupUserLogic.sol* ( [27-27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L27-L27), [222-222](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L222-L222), [358-358](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L358-L358) ):

```solidity
27:     function initialize(address _stakeToken) external view override onlyProxy {

222:     function returnOldDeposit() external override onlyValidator whenNotPaused {

358:     function withdrawStakerFunds() external override whenNotPaused returns (uint256) {
```

</details>

### [N-06] Add inline comments for unnamed parameters

`function func(address a, address)` -> `function func(address a, address /* b */)`

There are 5 instances:

- *ISequencerInbox.sol* ( [95-95](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L95-L95), [97-97](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L97-L97), [124-124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L124-L124) ):

```solidity
95:     function isBatchPoster(address) external view returns (bool);

97:     function isSequencer(address) external view returns (bool);

124:     function dasKeySetInfo(bytes32) external view returns (bool, uint64);
```

- *SequencerInbox.sol* ( [356-361](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L356-L361) ):

```solidity
356:     function addSequencerL2BatchFromOrigin(
357:         uint256,
358:         bytes calldata,
359:         uint256,
360:         IGasRefunder
361:     ) external pure {
```

- *IAssertionChain.sol* ( [26-26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/IAssertionChain.sol#L26-L26) ):

```solidity
26:     function isValidator(address) external view returns (bool);
```

### [N-07] Consider providing a ranged getter for array state variables

While the compiler automatically provides a getter for accessing single elements within a public state variable array, it doesn't provide a way to fetch the whole array, or subsets thereof. Consider adding a function to allow the fetching of slices of the array, especially if the contract doesn't already have multicall functionality.

There is 1 instance:

- *EdgeChallengeManager.sol* ( [279-279](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L279-L279) ):

```solidity
279:     uint256[] public stakeAmounts;
```

### [N-08] Consider splitting complex checks into multiple steps

Assign the expression's parts to intermediate local variables, and check against those instead.

There is 1 instance:

- *RollupProxy.sol* ( [16-18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L16-L18) ):

```solidity
16:             _getAdmin() == address(0) &&
17:             _getImplementation() == address(0) &&
18:             _getSecondaryImplementation() == address(0)
```

### [N-09] Cast to `bytes` for clearer semantic meaning

Using a [cast](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739) on a single argument, rather than `abi.encodePacked()` makes the intended operation more clear, leading to less reviewer confusion.

There is 1 instance:

- *EdgeChallengeManagerLib.sol* ( [135-135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L135-L135) ):

```solidity
135:     bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));
```

### [N-10] Missing checks for empty bytes when updating bytes state variables

Unless the code is attempting to `delete` the state variable, the caller shouldn't have to write `""` to the state variable

There are 4 instances:

- *AssertionStakingPool.sol* ( [36-36](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L36-L36) ):

```solidity
36:         assertionHash = _assertionHash;
```

- *EdgeStakingPool.sol* ( [40-40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L40-L40) ):

```solidity
40:         edgeId = _edgeId;
```

- *RollupAdminLogic.sol* ( [282-282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L282-L282) ):

```solidity
282:         wasmModuleRoot = newWasmModuleRoot;
```

- *RollupCore.sol* ( [229-229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L229-L229) ):

```solidity
229:         _latestConfirmed = assertionHash;
```

### [N-11] Consider adding a block/deny-list

Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens

There are 4 instances:

- *AbsBoldStakingPool.sol* ( [16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L16) ):

```solidity
16: abstract contract AbsBoldStakingPool is IAbsBoldStakingPool {
```

- *EdgeChallengeManager.sol* ( [206](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L206) ):

```solidity
206: contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {
```

- *RollupCreator.sol* ( [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L17) ):

```solidity
17: contract RollupCreator is Ownable {
```

- *RollupUserLogic.sol* ( [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L15) ):

```solidity
15: contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {
```

### [N-12] Constants/Immutables redefined elsewhere

Consider defining in only one contract so that values cannot become out of sync when only one location is updated. A [cheap way](https://medium.com/coinmonks/gas-cost-of-solidity-library-functions-dbe0cedd4678) to store constants/immutables in a single location is to create an `internal constant` in a `library`. If the variable is a local cache of another contract's value, consider making the cache variable internal or private, which will require external users to query the contract with the source of truth, so that callers don't get out of sync.

There are 4 instances:

- *AssertionStakingPool.sol* ( [25-25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L25-L25) ):

```solidity
/// @audit Seen in src/rollup/BOLDUpgradeAction.sol#124
25:     address public immutable rollup;
```

- *SequencerInbox.sol* ( [129-129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L129-L129) ):

```solidity
/// @audit Seen in src/rollup/RollupUserLogic.sol#31
129:     uint256 internal immutable deployTimeChainId = block.chainid;
```

- *BOLDUpgradeAction.sol* ( [124-124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L124-L124) ):

```solidity
/// @audit Seen in src/assertionStakingPool/AssertionStakingPool.sol#25
124:     IOldRollup public immutable rollup;
```

- *RollupUserLogic.sol* ( [31-31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L31-L31) ):

```solidity
/// @audit Seen in src/bridge/SequencerInbox.sol#129
31:     uint256 internal immutable deployTimeChainId = block.chainid;
```

### [N-13] Convert simple `if`-statements to ternary expressions

Converting some if statements to ternaries (such as `z = (a < b) ? x : y`) can make the code more concise and easier to read.

There are 2 instances:

- *MerkleTreeLib.sol* ( [129-136](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L129-L136) ):

```solidity
129:             } else if (val != 0) {
130:                 // accum represents the smaller sub trees, since it is earlier in the expansion
131:                 // we put the larger subtrees on the left
132:                 accum = keccak256(abi.encodePacked(val, accum));
133:             } else {
134:                 // by definition we always complete trees by appending zeros to the right
135:                 accum = keccak256(abi.encodePacked(accum, bytes32(0)));
136:             }
```

- *RollupCore.sol* ( [451-461](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L451-L461) ):

```solidity
451:             if (afterInboxPosition == currentInboxPosition) {
452:                 // No new messages have been added to the inbox since the last assertion
453:                 // In this case if we set the next inbox position to the current one we would be insisting that
454:                 // the next assertion process no messages. So instead we increment the next inbox position to current
455:                 // plus one, so that the next assertion will process exactly one message.
456:                 // Thus, no assertion can be empty (except the genesis assertion, which is created
457:                 // via a different codepath).
458:                 nextInboxPosition = currentInboxPosition + 1;
459:             } else {
460:                 nextInboxPosition = currentInboxPosition;
461:             }
```

### [N-14] Contracts should each be defined in separate files

Keeping each contract in a separate file makes it easier to work with multiple people, makes the code easier to maintain, and is a common practice on most projects. The following files each contains more than one contract/library/interface.

There are 2 instances:

- [*EdgeChallengeManager.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol)

- [*BOLDUpgradeAction.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol)

### [N-15] Contract name does not match its filename

According to the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#contract-and-library-names), contract and library names should also match their filenames.

There are 3 instances:

- *Assertion.sol* ( [66](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L66) ):

```solidity
/// @audit Not match filename `Assertion.sol`
66: library AssertionNodeLib {
```

- *AssertionState.sol* ( [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L17) ):

```solidity
/// @audit Not match filename `AssertionState.sol`
17: library AssertionStateLib {
```

- *IRollupLogic.sol* ( [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L12) ):

```solidity
/// @audit Not match filename `IRollupLogic.sol`
12: interface IRollupUser is IRollupCore, IOwnable {
```

### [N-16] UPPER_CASE names should be reserved for `constant`/`immutable` variables

If the variable needs to be different based on which class it comes from, a `view`/`pure` _function_ should be used instead (e.g. like [this](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59)).

There are 5 instances:

- *SequencerInbox.sol* ( [99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L99) ):

```solidity
99:     ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;
```

- *EdgeChallengeManager.sol* ( [291](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L291), [293](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L293), [295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L295), [298](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L298) ):

```solidity
291:     uint256 public LAYERZERO_BLOCKEDGE_HEIGHT;

293:     uint256 public LAYERZERO_BIGSTEPEDGE_HEIGHT;

295:     uint256 public LAYERZERO_SMALLSTEPEDGE_HEIGHT;

298:     uint8 public NUM_BIGSTEP_LEVEL;
```

### [N-17] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

<details>
<summary>There are 10 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [24-24](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L24-L24) ):

```solidity
24:     constructor(address _stakeToken) {
```

- *AssertionStakingPool.sol* ( [31-34](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L31-L34) ):

```solidity
31:     constructor(
32:         address _rollup,
33:         bytes32 _assertionHash
34:     ) AbsBoldStakingPool(IRollupCore(_rollup).stakeToken()) {
```

- *EdgeStakingPool.sol* ( [35-38](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L35-L38) ):

```solidity
35:     constructor(
36:         address _challengeManager,
37:         bytes32 _edgeId
38:     ) AbsBoldStakingPool(address(EdgeChallengeManager(_challengeManager).stakeToken())) {
```

- *SequencerInbox.sol* ( [140-145](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L140-L145) ):

```solidity
140:     constructor(
141:         uint256 _maxDataSize,
142:         IReader4844 reader4844_,
143:         bool _isUsingFeeToken,
144:         bool _isDelayBufferable
145:     ) {
```

- *EdgeChallengeManager.sol* ( [300-300](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L300-L300) ):

```solidity
300:     constructor() {
```

- *BOLDUpgradeAction.sol* ( [126-126](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L126-L126), [169-169](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L169-L169), [287-292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L287-L292) ):

```solidity
126:     constructor(IOldRollup _rollup) {

169:     constructor(uint256[] memory __array) {

287:     constructor(
288:         Contracts memory contracts,
289:         ProxyAdmins memory proxyAdmins,
290:         Implementations memory implementations,
291:         Settings memory settings
292:     ) {
```

- *BridgeCreator.sol* ( [45-48](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L45-L48) ):

```solidity
45:     constructor(
46:         BridgeTemplates memory _ethBasedTemplates,
47:         BridgeTemplates memory _erc20BasedTemplates
48:     ) Ownable() {
```

- *RollupCreator.sol* ( [58-58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L58-L58) ):

```solidity
58:     constructor() Ownable() {}
```

</details>

### [N-18] Empty function body without comments

Empty function body in solidity is not recommended, consider adding some comments to the body.

There are 3 instances:

- *RollupAdminLogic.sol* ( [166-166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L166-L166), [171-171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L171-L171) ):

```solidity
166:     function _authorizeUpgrade(address newImplementation) internal override {}

171:     function _authorizeSecondaryUpgrade(address newImplementation) internal override {}
```

- *RollupCreator.sol* ( [61-61](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L61-L61) ):

```solidity
61:     receive() external payable {}
```

### [N-19] Events are emitted without the sender information

When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the `msg.sender` the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

<details>
<summary>There are 34 instances (click to show):</summary>

- *AssertionStakingPoolCreator.sol* ( [20-20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L20-L20) ):

```solidity
20:         emit NewAssertionPoolCreated(_rollup, _assertionHash, address(assertionPool));
```

- *EdgeStakingPoolCreator.sol* ( [20-20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L20-L20) ):

```solidity
20:         emit NewEdgeStakingPoolCreated(challengeManager, edgeId);
```

- *SequencerInbox.sol* ( [344-352](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L344-L352), [488-496](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L488-L496) ):

```solidity
344:         emit SequencerBatchDelivered(
345:             seqMessageIndex,
346:             beforeAcc,
347:             afterAcc,
348:             delayedAcc,
349:             totalDelayedMessagesRead,
350:             timeBounds,
351:             IBridge.BatchDataLocation.NoData
352:         );

488:         emit SequencerBatchDelivered(
489:             sequenceNumber,
490:             beforeAcc,
491:             afterAcc,
492:             delayedAcc,
493:             totalDelayedMessagesRead,
494:             timeBounds,
495:             IBridge.BatchDataLocation.Blob
496:         );
```

- *EdgeChallengeManager.sol* ( [437-446](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L437-L446), [462-471](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L462-L471), [474-483](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L474-L483), [485-485](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L485-L485), [494-494](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L494-L494), [501-501](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L501-L501), [507-507](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L507-L507), [535-535](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L535-L535), [568-568](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L568-L568), [584-584](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L584-L584) ):

```solidity
437:         emit EdgeAdded(
438:             edgeAdded.edgeId,
439:             edgeAdded.mutualId,
440:             edgeAdded.originId,
441:             edgeAdded.claimId,
442:             edgeAdded.length,
443:             edgeAdded.level,
444:             edgeAdded.hasRival,
445:             edgeAdded.isLayerZero
446:         );

462:             emit EdgeAdded(
463:                 lowerChildAdded.edgeId,
464:                 lowerChildAdded.mutualId,
465:                 lowerChildAdded.originId,
466:                 lowerChildAdded.claimId,
467:                 lowerChildAdded.length,
468:                 lowerChildAdded.level,
469:                 lowerChildAdded.hasRival,
470:                 lowerChildAdded.isLayerZero
471:             );

474:         emit EdgeAdded(
475:             upperChildAdded.edgeId,
476:             upperChildAdded.mutualId,
477:             upperChildAdded.originId,
478:             upperChildAdded.claimId,
479:             upperChildAdded.length,
480:             upperChildAdded.level,
481:             upperChildAdded.hasRival,
482:             upperChildAdded.isLayerZero
483:         );

485:         emit EdgeBisected(edgeId, lowerChildId, upperChildAdded.edgeId, lowerChildAlreadyExists);

494:             if (updated) emit TimerCacheUpdated(edgeIds[i], newValue);

501:         if (updated) emit TimerCacheUpdated(edgeId, newValue);

507:         if (updated) emit TimerCacheUpdated(edgeId, newValue);

535:         emit EdgeConfirmedByTime(edgeId, store.edges[edgeId].mutualId(), totalTimeUnrivaled);

568:         emit EdgeConfirmedByOneStepProof(edgeId, store.edges[edgeId].mutualId());

584:         emit EdgeRefunded(edgeId, store.edges[edgeId].mutualId(), address(st), sa);
```

- *BOLDUpgradeAction.sol* ( [109-109](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L109-L109) ):

```solidity
109:         emit HashSet(h, executionState, inboxMaxCount);
```

- *RollupAdminLogic.sol* ( [120-120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L120-L120), [130-130](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L130-L130), [140-140](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L140-L140), [152-152](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L152-L152), [160-160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L160-L160), [187-187](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L187-L187), [206-206](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L206-L206), [216-216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L216-L216), [225-225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L225-L225), [234-234](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L234-L234), [255-255](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L255-L255), [266-266](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L266-L266), [274-274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L274-L274), [283-283](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L283-L283), [292-292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L292-L292), [301-301](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L301-L301), [310-310](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L310-L310), [319-319](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L319-L319), [328-328](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L328-L328) ):

```solidity
120:         emit OwnerFunctionCalled(0);

130:         emit OwnerFunctionCalled(1);

140:         emit OwnerFunctionCalled(2);

152:         emit OwnerFunctionCalled(3);

160:         emit OwnerFunctionCalled(4);

187:         emit OwnerFunctionCalled(6);

206:         emit OwnerFunctionCalled(8);

216:         emit OwnerFunctionCalled(9);

225:         emit OwnerFunctionCalled(12);

234:         emit OwnerFunctionCalled(22);

255:         emit OwnerFunctionCalled(23);

266:         emit OwnerFunctionCalled(24);

274:         emit OwnerFunctionCalled(25);

283:         emit OwnerFunctionCalled(26);

292:         emit OwnerFunctionCalled(27);

301:         emit OwnerFunctionCalled(28);

310:         emit OwnerFunctionCalled(30);

319:         emit OwnerFunctionCalled(31);

328:         emit OwnerFunctionCalled(32);
```

</details>

### [N-20] Inconsistent floating version pragma

Source files are using different floating version syntax, this is prone to compilation errors, and is not conducive to the code reliability and maintainability.

There are 4 instances:

- *AbsBoldStakingPool.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *DelayBufferTypes.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBufferTypes.sol#L7) ):

```solidity
7: pragma solidity >=0.6.9 <0.9.0;
```

- *EdgeChallengeManager.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L5) ):

```solidity
5: pragma solidity ^0.8.17;
```

- *Error.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/libraries/Error.sol#L5) ):

```solidity
5: pragma solidity ^0.8.4;
```

### [N-21] Function state mutability can be restricted to pure

Function state mutability can be restricted to pure

There are 2 instances:

- *RollupAdminLogic.sol* ( [166-166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L166-L166), [171-171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L171-L171) ):

```solidity
166:     function _authorizeUpgrade(address newImplementation) internal override {}

171:     function _authorizeSecondaryUpgrade(address newImplementation) internal override {}
```

### [N-22] Imports could be organized more systematically

The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

<details>
<summary>There are 28 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [9-9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L9-L9) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
9: import {IAbsBoldStakingPool} from "./interfaces/IAbsBoldStakingPool.sol";
```

- *AssertionStakingPool.sol* ( [11-11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L11-L11) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
11: import "./interfaces/IAssertionStakingPool.sol";
```

- *AssertionStakingPoolCreator.sol* ( [10-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L10-L10) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
10: import "./interfaces/IAssertionStakingPoolCreator.sol";
```

- *EdgeStakingPool.sol* ( [8-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L8-L8), [11-11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L11-L11) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import "./interfaces/IEdgeStakingPool.sol";

/// @audit Out of order with the prev import️ ⬆
11: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *EdgeStakingPoolCreator.sol* ( [10-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L10-L10) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
10: import "./interfaces/IEdgeStakingPoolCreator.sol";
```

- *IEdgeStakingPool.sol* ( [8-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L8-L8) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import "./IAbsBoldStakingPool.sol";
```

- *SequencerInbox.sol* ( [40-40](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L40-L40), [47-47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L47-L47), [51-51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L51-L51), [54-54](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L54-L54) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
40: import "./IBridge.sol";

/// @audit Out of order with the prev import️ ⬆
47: import "../libraries/IReader4844.sol";

/// @audit Out of order with the prev import️ ⬆
51: import {IGasRefunder} from "../libraries/IGasRefunder.sol";

/// @audit Out of order with the prev import️ ⬆
54: import {IERC20Bridge} from "./IERC20Bridge.sol";
```

- *EdgeChallengeManager.sol* ( [9-9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L9-L9) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
9: import "./IAssertionChain.sol";
```

- *EdgeChallengeManagerLib.sol* ( [10-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L10-L10) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
10: import "../../osp/IOneStepProofEntry.sol";
```

- *AssertionState.sol* ( [9-9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L9-L9) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
9: import "../osp/IOneStepProofEntry.sol";
```

- *BridgeCreator.sol* ( [17-17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L17-L17) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
17: import "../bridge/IBridge.sol";
```

- *Config.sol* ( [9-9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L9-L9) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
9: import "../bridge/ISequencerInbox.sol";
```

- *IRollupCore.sol* ( [8-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L8-L8), [13-13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L13-L13) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import "../bridge/IBridge.sol";

/// @audit Out of order with the prev import️ ⬆
13: import "../challengeV2/IAssertionChain.sol";
```

- *RollupAdminLogic.sol* ( [10-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L10-L10) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
10: import "../bridge/IOutbox.sol";
```

- *RollupCore.sol* ( [11-11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L11-L11), [16-16](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L16-L16) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
11: import "./IRollupEventInbox.sol";

/// @audit Out of order with the prev import️ ⬆
16: import "../bridge/ISequencerInbox.sol";
```

- *RollupCreator.sol* ( [8-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L8-L8), [10-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L10-L10), [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L15-L15) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import "./IRollupAdmin.sol";

/// @audit Out of order with the prev import️ ⬆
10: import "@offchainlabs/upgrade-executor/src/IUpgradeExecutor.sol";

/// @audit Out of order with the prev import️ ⬆
15: import {SafeERC20, IERC20} from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *RollupLib.sol* ( [8-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L8-L8), [14-14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L14-L14) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import "../bridge/ISequencerInbox.sol";

/// @audit Out of order with the prev import️ ⬆
14: import "./IRollupEventInbox.sol";
```

- *RollupProxy.sol* ( [8-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L8-L8) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import "./IRollupAdmin.sol";
```

- *RollupUserLogic.sol* ( [12-12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L12-L12) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
12: import "./IRollupLogic.sol";
```

</details>

### [N-23] There is no need to initialize bool variables with `false`

Since the bool variables are automatically set to `false` when created, it is redundant to initialize it with `false` again.

There is 1 instance:

- *SequencerInbox.sol* ( [187-187](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L187-L187) ):

```solidity
187:         bool actualIsUsingFeeToken = false;
```

### [N-24] @openzeppelin/contracts should be upgraded to a newer version

These contracts import contracts from `@openzeppelin/contracts`, but they are not using [the latest version](https://github.com/OpenZeppelin/openzeppelin-contracts/releases). Using the latest version ensures contract security with fixes for known vulnerabilities, access to the latest feature updates, and enhanced community support and engagement.

The imported version is `4.7.3`.

<details>
<summary>There are 20 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L8) ):

```solidity
7: import {IERC20} from "@openzeppelin/contracts/token/ERC20/IERC20.sol";

8: import {SafeERC20} from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *AssertionStakingPool.sol* ( [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L8) ):

```solidity
8: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *EdgeStakingPool.sol* ( [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L12) ):

```solidity
11: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

12: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *StakingPoolCreatorUtils.sol* ( [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L8), [9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L9) ):

```solidity
8: import "@openzeppelin/contracts/utils/Create2.sol";

9: import "@openzeppelin/contracts/utils/Address.sol";
```

- *EdgeChallengeManager.sol* ( [14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L14), [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L15) ):

```solidity
14: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";

15: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *BOLDUpgradeAction.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L7), [8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L8) ):

```solidity
7: import "@openzeppelin/contracts-upgradeable/utils/Create2Upgradeable.sol";

8: import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
```

- *BridgeCreator.sol* ( [18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L18), [19](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L19) ):

```solidity
18: import "@openzeppelin/contracts/access/Ownable.sol";

19: import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
```

- *RollupAdminLogic.sol* ( [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L13) ):

```solidity
13: import "@openzeppelin/contracts/proxy/beacon/UpgradeableBeacon.sol";
```

- *RollupCore.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L7) ):

```solidity
7: import "@openzeppelin/contracts-upgradeable/security/PausableUpgradeable.sol";
```

- *RollupCreator.sol* ( [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L11), [12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L12), [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L13), [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L15) ):

```solidity
11: import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";

12: import "@openzeppelin/contracts/proxy/transparent/TransparentUpgradeableProxy.sol";

13: import "@openzeppelin/contracts/access/Ownable.sol";

15: import {SafeERC20, IERC20} from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *RollupUserLogic.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L7) ):

```solidity
7: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

</details>

### [N-25] Lib @openzeppelin/contracts-upgradeable should be upgraded to a newer version

These contracts import contracts from `@openzeppelin/contracts-upgradeable`, but they are not using [the latest version](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/releases). Using the latest version ensures contract security with fixes for known vulnerabilities, access to the latest feature updates, and enhanced community support and engagement.

The imported version is `4.7.3`.

There are 3 instances:

- *EdgeChallengeManager.sol* ( [14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L14) ):

```solidity
14: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```

- *BOLDUpgradeAction.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L7) ):

```solidity
7: import "@openzeppelin/contracts-upgradeable/utils/Create2Upgradeable.sol";
```

- *RollupCore.sol* ( [7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L7) ):

```solidity
7: import "@openzeppelin/contracts-upgradeable/security/PausableUpgradeable.sol";
```

### [N-26] Expressions for constant values should use `immutable` rather than `constant`

While it doesn't save any gas because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.

There is 1 instance:

- *EdgeChallengeManagerLib.sol* ( [135-135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L135-L135) ):

```solidity
135:     bytes32 public constant UNRIVALED = keccak256(abi.encodePacked("UNRIVALED"));
```

### [N-27] Consider moving duplicated strings to constants

Moving duplicate strings to constants can improve code maintainability and readability.

<details>
<summary>There are 22 instances (click to show):</summary>

- *ArrayUtilsLib.sol* ( [32-32](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L32-L32) ):

```solidity
32:         require(startIndex < endIndex, "Start not less than end");
```

- *MerkleTreeLib.sol* ( [112-112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L112-L112), [160-160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L160-L160), [265-265](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L265-L265) ):

```solidity
112:         require(me.length <= MAX_LEVEL, "Merkle expansion too large");

160:         require(me.length <= MAX_LEVEL, "Merkle expansion too large");

265:         require(startSize < endSize, "Start not less than end");
```

- *UintUtilsLib.sol* ( [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L15-L15), [30-30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L30-L30) ):

```solidity
15:         require(x > 0, "Zero has no significant bits");

30:         require(x != 0, "Zero has no significant bits");
```

- *RollupAdminLogic.sol* ( [57-57](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L57-L57), [181-181](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L181-L181), [229-229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L229-L229), [272-272](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L272-L272) ):

```solidity
57:         require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");

181:         require(_validator.length > 0, "EMPTY_ARRAY");

229:         require(staker.length > 0, "EMPTY_ARRAY");

272:         require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");
```

- *RollupCore.sol* ( [357-357](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L357-L357), [566-566](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L566-L566) ):

```solidity
357:         require(staker.isStaked, "NOT_STAKED");

566:         require(isStaked(stakerAddress), "NOT_STAKED");
```

- *RollupCreator.sol* ( [154-154](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L154-L154), [158-158](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L158-L158), [160-160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L160-L160), [172-172](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L172-L172), [176-176](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L176-L176), [180-180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L180-L180) ):

```solidity
154:                 "SI_MAX_DATA_SIZE_MISMATCH"

158:                 "SI_MAX_DATA_SIZE_MISMATCH"

160:             require(deployParams.maxDataSize == ethInbox.maxDataSize(), "I_MAX_DATA_SIZE_MISMATCH");

172:                 "SI_MAX_DATA_SIZE_MISMATCH"

176:                 "SI_MAX_DATA_SIZE_MISMATCH"

180:                 "I_MAX_DATA_SIZE_MISMATCH"
```

- *RollupUserLogic.sol* ( [63-63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L63-L63), [72-72](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L72-L72), [175-175](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L175-L175), [233-233](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L233-L233) ):

```solidity
63:         require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");

72:         require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");

175:         require(isStaked(msg.sender), "NOT_STAKED");

233:         require(isStaked(stakerAddress), "NOT_STAKED");
```

</details>

### [N-28] Contracts containing only utility functions should be made into libraries

Consider using a `library` instead of a `contract` to provide utility functions.

There are 3 instances:

- *AssertionStakingPoolCreator.sol* ( [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L13) ):

```solidity
13: contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {
```

- *EdgeStakingPoolCreator.sol* ( [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L13) ):

```solidity
13: contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {
```

- *RollupProxy.sol* ( [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L11) ):

```solidity
11: contract RollupProxy is AdminFallbackProxy {
```

### [N-29] Functions should be named in mixedCase style

As the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.21/style-guide.html#function-names) suggests: functions should be named in mixedCase style.

There are 7 instances:

- *ISequencerInbox.sol* ( [55](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L55), [61](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L61), [67](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L67), [73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L73), [79](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L79), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L85), [91](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L91) ):

```solidity
55:     function HEADER_LENGTH() external view returns (uint256);

61:     function DATA_AUTHENTICATED_FLAG() external view returns (bytes1);

67:     function DATA_BLOB_HEADER_FLAG() external view returns (bytes1);

73:     function DAS_MESSAGE_HEADER_FLAG() external view returns (bytes1);

79:     function TREE_DAS_MESSAGE_HEADER_FLAG() external view returns (bytes1);

85:     function BROTLI_MESSAGE_HEADER_FLAG() external view returns (bytes1);

91:     function ZERO_HEAVY_MESSAGE_HEADER_FLAG() external view returns (bytes1);
```

### [N-30] Variable names for `immutable`s should use UPPER_CASE_WITH_UNDERSCORES

For `immutable` variable names, each word should use all capital letters, with underscores separating each word (UPPER_CASE_WITH_UNDERSCORES)

<details>
<summary>There are 14 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [20-20](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L20-L20) ):

```solidity
20:     address public immutable stakeToken;
```

- *AssertionStakingPool.sol* ( [25-25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L25-L25), [27-27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L27-L27) ):

```solidity
25:     address public immutable rollup;

27:     bytes32 public immutable assertionHash;
```

- *EdgeStakingPool.sol* ( [29-29](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L29-L29), [31-31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L31-L31) ):

```solidity
29:     address public immutable challengeManager;

31:     bytes32 public immutable edgeId;
```

- *SequencerInbox.sol* ( [116-116](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L116-L116), [128-128](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L128-L128), [129-129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L129-L129), [131-131](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L131-L131), [133-133](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L133-L133), [135-135](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L135-L135) ):

```solidity
116:     IReader4844 public immutable reader4844;

128:     uint256 public immutable maxDataSize;

129:     uint256 internal immutable deployTimeChainId = block.chainid;

131:     bool internal immutable hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();

133:     bool public immutable isUsingFeeToken;

135:     bool public immutable isDelayBufferable;
```

- *BOLDUpgradeAction.sol* ( [124-124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L124-L124) ):

```solidity
124:     IOldRollup public immutable rollup;
```

- *RollupCore.sol* ( [112-112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L112-L112) ):

```solidity
112:     bool internal immutable _hostChainIsArbitrum = ArbitrumChecker.runningOnArbitrum();
```

- *RollupUserLogic.sol* ( [31-31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L31-L31) ):

```solidity
31:     uint256 internal immutable deployTimeChainId = block.chainid;
```

</details>

### [N-31] Names of `public`/`external` functions and state variables should NOT be prefixed with underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

There is 1 instance:

- *RollupCore.sol* ( [102-102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L102-L102) ):

```solidity
102:     mapping(address => Staker) public _stakerMap;
```

### [N-32] Overridden function has no body

Consider adding a NatSpec comment describing why the function doesn't need a body and or the purpose it serves.

There are 2 instances:

- *RollupAdminLogic.sol* ( [166-166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L166-L166), [171-171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L171-L171) ):

```solidity
166:     function _authorizeUpgrade(address newImplementation) internal override {}

171:     function _authorizeSecondaryUpgrade(address newImplementation) internal override {}
```

### [N-33] Named imports of parent contracts are missing

Consider adding named imports for all parent contracts.

<details>
<summary>There are 25 instances (click to show):</summary>

- *AssertionStakingPool.sol* ( [21-21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L21-L21) ):

```solidity
/// @audit AbsBoldStakingPool
/// @audit IAssertionStakingPool
21: contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {
```

- *AssertionStakingPoolCreator.sol* ( [13-13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L13-L13) ):

```solidity
/// @audit IAssertionStakingPoolCreator
13: contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {
```

- *EdgeStakingPool.sol* ( [25-25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L25-L25) ):

```solidity
/// @audit AbsBoldStakingPool
/// @audit IEdgeStakingPool
25: contract EdgeStakingPool is AbsBoldStakingPool, IEdgeStakingPool {
```

- *EdgeStakingPoolCreator.sol* ( [13-13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L13-L13) ):

```solidity
/// @audit IEdgeStakingPoolCreator
13: contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {
```

- *IAssertionStakingPool.sol* ( [10-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L10-L10) ):

```solidity
/// @audit IAbsBoldStakingPool
10: interface IAssertionStakingPool is IAbsBoldStakingPool {
```

- *IEdgeStakingPool.sol* ( [10-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L10-L10) ):

```solidity
/// @audit IAbsBoldStakingPool
10: interface IEdgeStakingPool is IAbsBoldStakingPool {
```

- *ISequencerInbox.sol* ( [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L15-L15) ):

```solidity
/// @audit IDelayedMessageProvider
15: interface ISequencerInbox is IDelayedMessageProvider {
```

- *SequencerInbox.sol* ( [64-64](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L64-L64) ):

```solidity
/// @audit DelegateCallAware
/// @audit ISequencerInbox
64: contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {
```

- *EdgeChallengeManager.sol* ( [206-206](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L206-L206) ):

```solidity
/// @audit Initializable
206: contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {
```

- *BridgeCreator.sol* ( [21-21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L21-L21) ):

```solidity
/// @audit Ownable
21: contract BridgeCreator is Ownable {
```

- *IRollupCore.sol* ( [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L15-L15) ):

```solidity
/// @audit IAssertionChain
15: interface IRollupCore is IAssertionChain {
```

- *IRollupLogic.sol* ( [12-12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L12-L12) ):

```solidity
/// @audit IRollupCore
/// @audit IOwnable
12: interface IRollupUser is IRollupCore, IOwnable {
```

- *RollupAdminLogic.sol* ( [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L15-L15) ):

```solidity
/// @audit RollupCore
/// @audit IRollupAdmin
/// @audit DoubleLogicUUPSUpgradeable
15: contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {
```

- *RollupCore.sol* ( [22-22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L22-L22) ):

```solidity
/// @audit IRollupCore
/// @audit PausableUpgradeable
22: abstract contract RollupCore is IRollupCore, PausableUpgradeable {
```

- *RollupCreator.sol* ( [17-17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L17-L17) ):

```solidity
/// @audit Ownable
17: contract RollupCreator is Ownable {
```

- *RollupProxy.sol* ( [11-11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L11-L11) ):

```solidity
/// @audit AdminFallbackProxy
11: contract RollupProxy is AdminFallbackProxy {
```

- *RollupUserLogic.sol* ( [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L15-L15) ):

```solidity
/// @audit RollupCore
/// @audit UUPSNotUpgradeable
15: contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {
```

</details>

### [N-34] Constants should be put on the left side of comparisons

Putting constants on the left side of comparison statements is a best practice known as [Yoda conditions](https://en.wikipedia.org/wiki/Yoda_conditions).
Although solidity's static typing system prevents accidental assignments within conditionals, adopting this practice can improve code readability and consistency, especially when working across multiple languages.

<details>
<summary>There are 106 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L30), [42](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L42) ):

```solidity
/// @audit put `0` on the left
30:         if (amount == 0) {

/// @audit put `0` on the left
42:         if (amount == 0) {
```

- *DelayBuffer.sol* ( [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L117), [118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L118), [119](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L119) ):

```solidity
/// @audit put `0` on the left
117:             config.threshold != 0 &&

/// @audit put `0` on the left
118:             config.max != 0 &&

/// @audit put `BASIS` on the left
119:             config.replenishRateInBasis <= BASIS &&
```

- *SequencerInbox.sol* ( [148](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L148), [150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L150), [170](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L170), [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L182), [183](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L183), [189](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L189), [484](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L484), [538](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L538), [651](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L651), [677](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L677), [678](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L678), [680](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L680), [711](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L711), [736](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L736), [851](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L851), [906](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L906), [959](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L959) ):

```solidity
/// @audit put `IReader4844(address(0))` on the left
148:             if (reader4844_ != IReader4844(address(0))) revert DataBlobsNotSupported();

/// @audit put `IReader4844(address(0))` on the left
150:             if (reader4844_ == IReader4844(address(0))) revert InitParamZero("Reader4844");

/// @audit put `0` on the left
170:         if (buffer.bufferBlocks != 0) {

/// @audit put `IBridge(address(0))` on the left
182:         if (bridge != IBridge(address(0))) revert AlreadyInit();

/// @audit put `IBridge(address(0))` on the left
183:         if (bridge_ == IBridge(address(0))) revert HadZeroInit();

/// @audit put `address(0)` on the left
189:             if (feeToken != address(0)) {

/// @audit put `~uint256(0)` on the left
484:         if (seqMessageIndex != sequenceNumber && sequenceNumber != ~uint256(0)) {

/// @audit put `~uint256(0)` on the left
538:         if (seqMessageIndex != sequenceNumber && sequenceNumber != ~uint256(0)) {

/// @audit put `HEADER_LENGTH` on the left
651:         assert(header.length == HEADER_LENGTH);

/// @audit put `BROTLI_MESSAGE_HEADER_FLAG` on the left
677:             headerByte == BROTLI_MESSAGE_HEADER_FLAG ||

/// @audit put `DAS_MESSAGE_HEADER_FLAG` on the left
678:             headerByte == DAS_MESSAGE_HEADER_FLAG ||

/// @audit put `ZERO_HEAVY_MESSAGE_HEADER_FLAG` on the left
680:             headerByte == ZERO_HEAVY_MESSAGE_HEADER_FLAG;

/// @audit put `33` on the left
711:             if (data[0] & DAS_MESSAGE_HEADER_FLAG != 0 && data.length >= 33) {

/// @audit put `0` on the left
736:         if (dataHashes.length == 0) revert MissingDataHashes();

/// @audit put `0` on the left
851:         if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {

/// @audit put `64 * 1024` on the left
906:         if (keysetBytes.length >= 64 * 1024) revert KeysetTooLarge();

/// @audit put `0` on the left
959:         if (ksInfo.creationBlock == 0) revert NoSuchKeyset(ksHash);
```

- *EdgeChallengeManager.sol* ( [325](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L325), [331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L331), [350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L350), [387](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L387), [429](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L429), [458](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L458), [580](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L580) ):

```solidity
/// @audit put `0` on the left
325:         if (_challengePeriodBlocks == 0) {

/// @audit put `address(0)` on the left
331:         if (_excessStakeReceiver == address(0)) {

/// @audit put `0` on the left
350:         if (_numBigStepLevel == 0) {

/// @audit put `0` on the left
387:             if (args.proof.length == 0) {

/// @audit put `0` on the left
429:         if (address(st) != address(0) && sa != 0) {

/// @audit put `0` on the left
458:         bool lowerChildAlreadyExists = lowerChildAdded.edgeId == 0;

/// @audit put `0` on the left
580:         if (address(st) != address(0) && sa != 0) {
```

- *ChallengeEdgeLib.sol* ( [76](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L76), [82](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L82), [85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L85), [103](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L103), [106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L106), [224](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L224), [231](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L231), [240](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L240), [240](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L240), [259](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L259), [259](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L259), [271](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L271), [280](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L280) ):

```solidity
/// @audit put `0` on the left
76:         if (originId == 0) {

/// @audit put `0` on the left
82:         if (startHistoryRoot == 0) {

/// @audit put `0` on the left
85:         if (endHistoryRoot == 0) {

/// @audit put `address(0)` on the left
103:         if (staker == address(0)) {

/// @audit put `0` on the left
106:         if (claimId == 0) {

/// @audit put `0` on the left
224:         return edge.createdAtBlock != 0;

/// @audit put `0` on the left
231:         if (len == 0) {

/// @audit put `0` on the left
240:         if (edge.lowerChildId != 0 || edge.upperChildId != 0) {

/// @audit put `0` on the left
240:         if (edge.lowerChildId != 0 || edge.upperChildId != 0) {

/// @audit put `0` on the left
259:         return edge.claimId != 0 && edge.staker != address(0);

/// @audit put `address(0)` on the left
259:         return edge.claimId != 0 && edge.staker != address(0);

/// @audit put `true` on the left
271:         if (edge.refunded == true) {

/// @audit put `0` on the left
280:         if (level == 0) {
```

- *EdgeChallengeManagerLib.sol* ( [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L182), [184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L184), [198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L198), [199](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L199), [229](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L229), [248](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L248), [294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L294), [329](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L329), [378](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L378), [472](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L472), [477](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L477), [490](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L490), [545](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L545), [551](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L551), [665](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L665) ):

```solidity
/// @audit put `0` on the left
182:         if (firstRival == 0) {

/// @audit put `UNRIVALED` on the left
184:         } else if (firstRival == UNRIVALED) {

/// @audit put `0` on the left
198:             firstRival != 0,

/// @audit put `0` on the left
199:             edge.claimId != 0

/// @audit put `0` on the left
229:             if (ard.assertionHash == 0) {

/// @audit put `0` on the left
248:             if (args.proof.length == 0) {

/// @audit put `0` on the left
294:             if (args.proof.length == 0) {

/// @audit put `0` on the left
329:         if (x == 0) {

/// @audit put `0` on the left
378:         if (args.prefixProof.length == 0) {

/// @audit put `0` on the left
472:         if (firstRival == 0) {

/// @audit put `UNRIVALED` on the left
477:         return firstRival != UNRIVALED;

/// @audit put `bytes32(0)` on the left
490:         if (store.edges[edgeId].lowerChildId != bytes32(0)) {

/// @audit put `0` on the left
545:         if (firstRival == 0) {

/// @audit put `UNRIVALED` on the left
551:         if (firstRival == UNRIVALED) {

/// @audit put `bytes32(0)` on the left
665:         if (confirmedRivalId != bytes32(0)) {
```

- *MerkleTreeLib.sol* ( [112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L112), [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L117), [118](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L118), [129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L129), [159](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L159), [160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L160), [162](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L162), [183](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L183), [195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L195), [198](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L198), [203](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L203), [222](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L222), [228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L228), [275](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L275), [282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L282), [295](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L295) ):

```solidity
/// @audit put `MAX_LEVEL` on the left
112:         require(me.length <= MAX_LEVEL, "Merkle expansion too large");

/// @audit put `0` on the left
117:             if (accum == 0) {

/// @audit put `0` on the left
118:                 if (val != 0) {

/// @audit put `0` on the left
129:             } else if (val != 0) {

/// @audit put `0` on the left
159:         require(subtreeRoot != 0, "Cannot append empty subtree");

/// @audit put `MAX_LEVEL` on the left
160:         require(me.length <= MAX_LEVEL, "Merkle expansion too large");

/// @audit put `0` on the left
162:         if (me.length == 0) {

/// @audit put `MAX_LEVEL` on the left
183:         require(next.length <= MAX_LEVEL, "Append creates oversize tree");

/// @audit put `0` on the left
195:                 require(me[i] == 0, "Append above least significant bit");

/// @audit put `0` on the left
198:                 if (accumHash == 0) {

/// @audit put `0` on the left
203:                     if (me[i] == 0) {

/// @audit put `0` on the left
222:         if (accumHash != 0) {

/// @audit put `0` on the left
228:         require(next[next.length - 1] != 0, "Last entry zero");

/// @audit put `0` on the left
275:         if (y != 0) {

/// @audit put `0` on the left
282:         if (z != 0) {

/// @audit put `0` on the left
295:             if (me[i] != 0) {
```

- *UintUtilsLib.sol* ( [30](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L30), [33](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L33), [38](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L38), [43](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L43), [48](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L48), [53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L53), [58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L58), [63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L63), [68](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L68) ):

```solidity
/// @audit put `0` on the left
30:         require(x != 0, "Zero has no significant bits");

/// @audit put `0x100000000000000000000000000000000` on the left
33:         if (x >= 0x100000000000000000000000000000000) {

/// @audit put `0x10000000000000000` on the left
38:         if (x >= 0x10000000000000000) {

/// @audit put `0x100000000` on the left
43:         if (x >= 0x100000000) {

/// @audit put `0x10000` on the left
48:         if (x >= 0x10000) {

/// @audit put `0x100` on the left
53:         if (x >= 0x100) {

/// @audit put `0x10` on the left
58:         if (x >= 0x10) {

/// @audit put `0x4` on the left
63:         if (x >= 0x4) {

/// @audit put `0x2` on the left
68:         if (x >= 0x2) msb += 1;
```

- *Assertion.sol* ( [86](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L86), [88](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L88) ):

```solidity
/// @audit put `0` on the left
86:         if (self.firstChildBlock == 0) {

/// @audit put `0` on the left
88:         } else if (self.secondChildBlock == 0) {
```

- *BOLDUpgradeAction.sol* ( [114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L114), [353](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L353), [526](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L526) ):

```solidity
/// @audit put `0` on the left
114:         require(inboxMaxCount != 0, "Hash not yet set");

/// @audit put `0` on the left
353:             if (staker.isStaked && staker.currentChallenge == 0) {

/// @audit put `0` on the left
526:         if (validators.length != 0) {
```

- *BridgeCreator.sol* ( [107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L107), [112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L112), [117](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L117) ):

```solidity
/// @audit put `0` on the left
107:         bool isDelayBufferable = bufferConfig.threshold != 0;

/// @audit put `address(0)` on the left
112:             nativeToken == address(0) ? ethBasedTemplates : erc20BasedTemplates,

/// @audit put `address(0)` on the left
117:         if (nativeToken == address(0)) {
```

- *RollupAdminLogic.sol* ( [57](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L57), [272](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L272) ):

```solidity
/// @audit put `address(0)` on the left
57:         require(config.loserStakeEscrow != address(0), "INVALID_ESCROW_0");

/// @audit put `address(0)` on the left
272:         require(newLoserStakerEscrow != address(0), "INVALID_ESCROW_0");
```

- *RollupCore.sol* ( [127](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L127), [427](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L427), [466](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L466), [478](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L478), [489](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L489) ):

```solidity
/// @audit put `bytes32(0)` on the left
127:         require(assertionHash != bytes32(0), "ASSERTION_ID_CANNOT_BE_ZERO");

/// @audit put `0` on the left
427:             require(afterStateCmpMaxInbox <= 0, "INBOX_TOO_FAR");

/// @audit put `0` on the left
466:             require(afterInboxPosition != 0, "EMPTY_INBOX_COUNT");

/// @audit put `bytes32(0)` on the left
478:             newAssertionHash == expectedAssertionHash || expectedAssertionHash == bytes32(0),

/// @audit put `0` on the left
489:             prevAssertion.firstChildBlock == 0, // assumes block 0 is impossible
```

- *RollupCreator.sol* ( [228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L228), [233](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L233), [292](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L292) ):

```solidity
/// @audit put `address(0)` on the left
228:         if (deployParams.batchPosterManager != address(0)) {

/// @audit put `0` on the left
233:         if (deployParams.validators.length != 0) {

/// @audit put `address(0)` on the left
292:         if (_nativeToken == address(0)) {
```

- *RollupUserLogic.sol* ( [28](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L28), [53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L53), [120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L120), [170](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L170), [278](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L278), [337](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L337) ):

```solidity
/// @audit put `address(0)` on the left
28:         require(_stakeToken != address(0), "NEED_STAKE_TOKEN");

/// @audit put `0` on the left
53:         if (latestConfirmedAssertion.createdAtBlock == 0) return false;

/// @audit put `0` on the left
120:             require(winningEdge.confirmedAtBlock != 0, "ZERO_CONFIRMED_AT_BLOCK");

/// @audit put `bytes32(0)` on the left
170:             expectedAssertionHash == bytes32(0)

/// @audit put `bytes32(0)` on the left
278:         require(expectedAssertionHash != bytes32(0), "EXPECTED_ASSERTION_HASH");

/// @audit put `address(0)` on the left
337:         require(withdrawalAddress != address(0), "EMPTY_WITHDRAWAL_ADDRESS");
```

</details>

### [N-35] `else`-block not required

One level of nesting can be removed by not having an `else` block when the `if`-block always jumps at the end. For example:
```solidity
if (condition) {
    body1...
    return x;
} else {
    body2...
}
```
can be changed to:
```solidity
if (condition) {
    body1...
    return x;
}
body2...
```

<details>
<summary>There are 12 instances (click to show):</summary>

- *StakingPoolCreatorUtils.sol* ( [16-18](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L16-L18) ):

```solidity
16:         if (Address.isContract(pool)) {
17:             return pool;
18:         } else {
```

- *SequencerInbox.sol* ( [279-281](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L279-L281) ):

```solidity
279:         if (_chainIdChanged()) {
280:             return (1, 1, 1, 1);
281:         } else {
```

- *EdgeChallengeManager.sol* ( [592-594](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L592-L594), [594-596](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L594-L596), [596-598](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L596-L598) ):

```solidity
592:         if (eType == EdgeType.Block) {
593:             return LAYERZERO_BLOCKEDGE_HEIGHT;
594:         } else if (eType == EdgeType.BigStep) {

594:         } else if (eType == EdgeType.BigStep) {
595:             return LAYERZERO_BIGSTEPEDGE_HEIGHT;
596:         } else if (eType == EdgeType.SmallStep) {

596:         } else if (eType == EdgeType.SmallStep) {
597:             return LAYERZERO_SMALLSTEPEDGE_HEIGHT;
598:         } else {
```

- *ChallengeEdgeLib.sol* ( [280-282](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L280-L282), [282-284](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L282-L284), [284-286](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L284-L286) ):

```solidity
280:         if (level == 0) {
281:             return EdgeType.Block;
282:         } else if (level <= numBigStepLevels) {

282:         } else if (level <= numBigStepLevels) {
283:             return EdgeType.BigStep;
284:         } else if (level == numBigStepLevels + 1) {

284:         } else if (level == numBigStepLevels + 1) {
285:             return EdgeType.SmallStep;
286:         } else {
```

- *EdgeChallengeManagerLib.sol* ( [220-267](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L220-L267), [551-553](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L551-L553), [562-566](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L562-L566) ):

```solidity
220:         if (ChallengeEdgeLib.levelToType(args.level, numBigStepLevel) == EdgeType.Block) {
221:             // origin id is the assertion which is the root of challenge
222:             // all rivals and their children share the same origin id - it is a link to the information
223:             // they agree on
224:             bytes32 originId = ard.predecessorId;
225: 
226:             // Sanity check: The assertion reference data should be related to the claim
227:             // Of course the caller can provide whatever args they wish, so this is really just a helpful
228:             // check to avoid mistakes
229:             if (ard.assertionHash == 0) {
230:                 revert AssertionHashEmpty();
231:             }
232:             if (ard.assertionHash != args.claimId) {
233:                 revert AssertionHashMismatch(ard.assertionHash, args.claimId);
234:             }
235: 
236:             // if the assertion is already confirmed or rejected then it cant be referenced as a claim
237:             if (!ard.isPending) {
238:                 revert AssertionNotPending();
239:             }
240: 
241:             // if the claim doesnt have a sibling then it is undisputed, there's no need
242:             // to open challenge edges for it
243:             if (!ard.hasSibling) {
244:                 revert AssertionNoSibling();
245:             }
246: 
247:             // parse the inclusion proof for later use
248:             if (args.proof.length == 0) {
249:                 revert EmptyEdgeSpecificProof();
250:             }
251:             (bytes32[] memory inclusionProof,,) =
252:                 abi.decode(args.proof, (bytes32[], AssertionStateData, AssertionStateData));
253: 
254:             // check the start and end execution states exist, the block hash entry should be non zero
255:             if (ard.startState.machineStatus == MachineStatus.RUNNING) {
256:                 revert EmptyStartMachineStatus();
257:             }
258:             if (ard.endState.machineStatus == MachineStatus.RUNNING) {
259:                 revert EmptyEndMachineStatus();
260:             }
261: 
262:             // Create machine hashes out of the proven state
263:             bytes32 startStateHash = oneStepProofEntry.getMachineHash(ard.startState.toExecutionState());
264:             bytes32 endStateHash = oneStepProofEntry.getMachineHash(ard.endState.toExecutionState());
265: 
266:             return (ProofData(startStateHash, endStateHash, inclusionProof), originId);
267:         } else {

551:         if (firstRival == UNRIVALED) {
552:             return block.number - store.edges[edgeId].createdAtBlock;
553:         } else {

562:             if (firstRivalCreatedAtBlock > edgeCreatedAtBlock) {
563:                 // if this edge was created before the first rival then we return the difference
564:                 // in createdAtBlock number
565:                 return firstRivalCreatedAtBlock - edgeCreatedAtBlock;
566:             } else {
```

- *RollupCore.sol* ( [146-150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L146-L150) ):

```solidity
146:         if (_hostChainIsArbitrum) {
147:             uint256 blockNum = _assertionCreatedAtArbSysBlock[assertionHash];
148:             require(blockNum > 0, "NO_ASSERTION");
149:             return blockNum;
150:         } else {
```

</details>

### [N-36] Large multiples of ten should use scientific notation

Use a scientific notation rather than decimal literals (e.g. `1e6` instead of `1000000`), for better code readability.

There is 1 instance:

- *DelayBuffer.sol* ( [17-17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L17-L17) ):

```solidity
/// @audit 10000 -> 1e4
17:     uint256 public constant BASIS = 10000;
```

### [N-37] `TODO`s left in the code

TODOs may signal that a feature is missing or not ready for audit, consider resolving the issue and removing the TODO comment

There is 1 instance:

- *ChallengeEdgeLib.sol* ( [63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L63) ):

```solidity
63:     /// @notice TODO
```

### [N-38] High cyclomatic complexity

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

<details>
<summary>There is 1 instance (click to show):</summary>

- *EdgeChallengeManager.sol* ( [305-364](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L305-L364) ):

```solidity
305:     function initialize(
306:         IAssertionChain _assertionChain,
307:         uint64 _challengePeriodBlocks,
308:         IOneStepProofEntry _oneStepProofEntry,
309:         uint256 layerZeroBlockEdgeHeight,
310:         uint256 layerZeroBigStepEdgeHeight,
311:         uint256 layerZeroSmallStepEdgeHeight,
312:         IERC20 _stakeToken,
313:         address _excessStakeReceiver,
314:         uint8 _numBigStepLevel,
315:         uint256[] calldata _stakeAmounts
316:     ) public initializer {
317:         if (address(_assertionChain) == address(0)) {
318:             revert EmptyAssertionChain();
319:         }
320:         assertionChain = _assertionChain;
321:         if (address(_oneStepProofEntry) == address(0)) {
322:             revert EmptyOneStepProofEntry();
323:         }
324:         oneStepProofEntry = _oneStepProofEntry;
325:         if (_challengePeriodBlocks == 0) {
326:             revert EmptyChallengePeriod();
327:         }
328:         challengePeriodBlocks = _challengePeriodBlocks;
329: 
...... OMITTED ......
340:         if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroBigStepEdgeHeight)) {
341:             revert NotPowerOfTwo(layerZeroBigStepEdgeHeight);
342:         }
343:         LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;
344:         if (!EdgeChallengeManagerLib.isPowerOfTwo(layerZeroSmallStepEdgeHeight)) {
345:             revert NotPowerOfTwo(layerZeroSmallStepEdgeHeight);
346:         }
347:         LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;
348: 
349:         // ensure that there is at least on of each type of level
350:         if (_numBigStepLevel == 0) {
351:             revert ZeroBigStepLevels();
352:         }
353:         // ensure there's also space for the block level and the small step level
354:         // in total level parameters
355:         if (_numBigStepLevel > 253) {
356:             revert BigStepLevelsTooMany(_numBigStepLevel);
357:         }
358:         NUM_BIGSTEP_LEVEL = _numBigStepLevel;
359: 
360:         if (_numBigStepLevel + 2 != _stakeAmounts.length) {
361:             revert StakeAmountsMismatch(_stakeAmounts.length, _numBigStepLevel + 2);
362:         }
363:         stakeAmounts = _stakeAmounts;
364:     }
```

</details>

### [N-39] Typos

All typos should be corrected.

<details>
<summary>There are 18 instances (click to show):</summary>

- *SequencerInbox.sol* ( [608](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L608) ):

```solidity
/// @audit proccessed
608:         // buffer update depends on new delayed messages. if none are read, no buffer update is proccessed
```

- *ArrayUtilsLib.sol* ( [23](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L23), [26](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L26) ):

```solidity
/// @audit exlusive
23:     /// @dev    End index exlusive so slice(arr, 0, 5) gets the first 5 elements of arr

/// @audit exlusive
26:     /// @param endIndex     The end index of the slice in the original array - exlusive
```

- *EdgeChallengeManagerLib.sol* ( [274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L274), [793](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L793) ):

```solidity
/// @audit existance
274:             // hasLengthOneRival checks existance, so we can use getNoCheck

/// @audit preceeding
793:         // To do this we sum the machine steps of the edges in each of the preceeding levels.
```

- *MerkleTreeLib.sol* ( [156](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L156), [176](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L176), [221](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L221) ):

```solidity
/// @audit leve
156:         // we use number representations of the levels elsewhere, so we need to ensure we're appending a leve

/// @audit numbe
176:         // if by appending the sub tree we increase the numbe of most sig bits of the size, that means

/// @audit storeage
221:         // increased the storeage above
```

- *UintUtilsLib.sol* ( [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L13), [28](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L28) ):

```solidity
/// @audit signficant
13:     /// @param x Cannot be zero, since zero that has no signficant bits

/// @audit sigificant
28:     /// @param x Cannot be zero, since zero has no sigificant bits
```

- *Error.sol* ( [35](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/libraries/Error.sol#L35) ):

```solidity
/// @audit adddress
35: /// @param addr The adddress in question
```

- *BOLDUpgradeAction.sol* ( [517](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L517) ):

```solidity
/// @audit UNEXPCTED
517:         require(address(rollup) == expectedRollupAddress, "UNEXPCTED_ROLLUP_ADDR");
```

- *RollupCore.sol* ( [570](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L570), [571](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L571), [572](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L572) ):

```solidity
/// @audit lastest
570:         bytes32 lastestAssertion = latestStakedAssertion(stakerAddress);

/// @audit lastest
571:         bool isLatestConfirmed = lastestAssertion == latestConfirmed();

/// @audit lastest
572:         bool haveChild = getAssertionStorage(lastestAssertion).firstChildBlock > 0;
```

- *RollupLib.sol* ( [53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L53) ):

```solidity
/// @audit emited
53:     // All these should be emited in AssertionCreated event
```

- *RollupUserLogic.sol* ( [220](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L220), [238](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L238) ):

```solidity
/// @audit chlid
220:      * @notice Refund a staker that is currently staked on an assertion that either has a chlid assertion or is the latest confirmed assertion.

/// @audit creditted
238:      * @notice Reduce the amount staked for the sender (difference between initial amount staked and target is creditted back to the sender).
```

</details>

### [N-40] Consider bounding input array length

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to require() that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.

There are 4 instances:

- *EdgeChallengeManager.sol* ( [492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L492) ):

```solidity
492:         for (uint256 i = 0; i < edgeIds.length; i++) {
```

- *BOLDUpgradeAction.sol* ( [528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L528) ):

```solidity
528:             for (uint256 i = 0; i < validators.length; i++) {
```

- *RollupAdminLogic.sol* ( [184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L184), [230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L230) ):

```solidity
184:         for (uint256 i = 0; i < _validator.length; i++) {

230:         for (uint256 i = 0; i < staker.length; i++) {
```

### [N-41] Unnecessary casting

Unnecessary castings can be removed.

<details>
<summary>There are 11 instances (click to show):</summary>

- *EdgeStakingPool.sol* ( [46-46](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L46-L46) ):

```solidity
/// @audit address(challengeManager)
46:         IERC20(stakeToken).safeIncreaseAllowance(address(challengeManager), requiredStake);
```

- *SequencerInbox.sol* ( [209-209](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L209-L209), [210-210](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L210-L210) ):

```solidity
/// @audit IOwnable(rollup)
209:         if (msg.sender != IOwnable(rollup).owner())

/// @audit IOwnable(rollup)
210:             revert NotOwner(msg.sender, IOwnable(rollup).owner());
```

- *BOLDUpgradeAction.sol* ( [475-475](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L475-L475) ):

```solidity
/// @audit address(IMPL_CHALLENGE_MANAGER)
475:                     address(IMPL_CHALLENGE_MANAGER),
```

- *BridgeCreator.sol* ( [122-122](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L122-L122) ):

```solidity
/// @audit IBridge(frame.bridge)
122:         frame.sequencerInbox.initialize(IBridge(frame.bridge), maxTimeVariation, bufferConfig);
```

- *RollupAdminLogic.sol* ( [139-139](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L139-L139) ):

```solidity
/// @audit address(_inbox)
139:         bridge.setDelayedInbox(address(_inbox), _enabled);
```

- *RollupCreator.sol* ( [204-204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L204-L204), [241-241](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L241-L241), [261-261](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L261-L261), [262-262](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L262-L262) ):

```solidity
/// @audit address(upgradeExecutor)
204:         proxyAdmin.transferOwnership(address(upgradeExecutor));

/// @audit address(upgradeExecutor)
241:         IRollupAdmin(address(rollup)).setOwner(address(upgradeExecutor));

/// @audit address(upgradeExecutor)
261:             address(upgradeExecutor),

/// @audit address(validatorWalletCreator)
262:             address(validatorWalletCreator)
```

- *RollupProxy.sol* ( [21-21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L21-L21) ):

```solidity
/// @audit address(connectedContracts.rollupAdminLogic)
21:                 address(connectedContracts.rollupAdminLogic),
```

</details>

### [N-42] Unused contract variables

The following state variables are defined but not used.
It is recommended to check the code for logical omissions that cause them not to be used. If it's determined that they are not needed anywhere, it's best to remove them from the codebase to improve code clarity and minimize confusion.

There is 1 instance:

- *SequencerInbox.sol* ( [99-99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L99-L99) ):

```solidity
99:     ISequencerInbox.MaxTimeVariation private __LEGACY_MAX_TIME_VARIATION;
```

### [N-43] Unused function parameters

Function parameters that are defined but not used may be logical errors and need to be checked to see if any logic is missing.
If the parameter is not really needed, it should be removed, otherwise it will repeatedly cause confusion and make code maintenance difficult.
If the parameter cannot be removed directly (for example, if it is an override function), its name should be removed and some comment can be appended.

There are 2 instances:

- *RollupAdminLogic.sol* ( [166-166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L166-L166), [171-171](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L171-L171) ):

```solidity
/// @audit newImplementation
166:     function _authorizeUpgrade(address newImplementation) internal override {}

/// @audit newImplementation
171:     function _authorizeSecondaryUpgrade(address newImplementation) internal override {}
```

### [N-44] Unused named return

Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment. This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

There are 2 instances:

- *ChallengeEdgeLib.sol* ( [279-279](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L279-L279) ):

```solidity
/// @audit eType
279:     function levelToType(uint8 level, uint8 numBigStepLevels) internal pure returns (EdgeType eType) {
```

- *UintUtilsLib.sol* ( [14-14](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L14-L14) ):

```solidity
/// @audit msb
14:     function leastSignificantBit(uint256 x) internal pure returns (uint256 msb) {
```

### [N-45] Use delete instead of assigning values to `false`

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

There is 1 instance:

- *SequencerInbox.sol* ( [927-927](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L927-L927) ):

```solidity
927:         dasKeySetInfo[ksHash].isValidKeyset = false;
```

### [N-46] Consider using `delete` rather than assigning zero to clear values

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

There are 3 instances:

- *MerkleTreeLib.sol* ( [207-207](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L207-L207), [212-212](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L212-L212) ):

```solidity
207:                         accumHash = 0;

212:                         next[i] = 0;
```

- *RollupCore.sol* ( [333-333](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L333-L333) ):

```solidity
333:         _withdrawableFunds[account] = 0;
```

### [N-47] Use the latest Solidity version

Upgrading to the [latest solidity version](https://github.com/ethereum/solc-js/tags) (0.8.19 for L2s) can optimize gas usage, take advantage of new features and improve overall contract efficiency. Where possible, based on compatibility requirements, it is recommended to use newer/latest solidity version to take advantage of the latest optimizations and features.

<details>
<summary>There are 24 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *AssertionStakingPool.sol* ( [6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L6) ):

```solidity
6: pragma solidity ^0.8.0;
```

- *AssertionStakingPoolCreator.sol* ( [6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L6) ):

```solidity
6: pragma solidity ^0.8.0;
```

- *EdgeStakingPool.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *EdgeStakingPoolCreator.sol* ( [6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L6) ):

```solidity
6: pragma solidity ^0.8.0;
```

- *StakingPoolCreatorUtils.sol* ( [6](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L6) ):

```solidity
6: pragma solidity ^0.8.0;
```

- *DelayBuffer.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *SequencerInbox.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *EdgeChallengeManager.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L5) ):

```solidity
5: pragma solidity ^0.8.17;
```

- *ArrayUtilsLib.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L5) ):

```solidity
5: pragma solidity ^0.8.17;
```

- *ChallengeEdgeLib.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L5) ):

```solidity
5: pragma solidity ^0.8.17;
```

- *EdgeChallengeManagerLib.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L5) ):

```solidity
5: pragma solidity ^0.8.17;
```

- *MerkleTreeLib.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L5) ):

```solidity
5: pragma solidity ^0.8.17;
```

- *UintUtilsLib.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol#L5) ):

```solidity
5: pragma solidity ^0.8.17;
```

- *Assertion.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *AssertionState.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *BOLDUpgradeAction.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *BridgeCreator.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *RollupAdminLogic.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *RollupCore.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *RollupCreator.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *RollupLib.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *RollupProxy.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

- *RollupUserLogic.sol* ( [5](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L5) ):

```solidity
5: pragma solidity ^0.8.0;
```

</details>

### [N-48] Use transfer libraries instead of low level calls to transfer native tokens

Consider using [`SafeTransferLib.safeTransferETH`](https://github.com/transmissions11/solmate/blob/fadb2e2778adbf01c80275bfb99e5c14969d964b/src/utils/SafeTransferLib.sol#L15) or [`Address.sendValue`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/9e3f4d60c581010c4a3979480e07cc7752f124cc/contracts/utils/Address.sol#L41) for clearer semantic meaning instead of using a low level `call`.

There is 1 instance:

- *RollupCreator.sol* ( [304-304](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L304-L304) ):

```solidity
304:             (bool sent, ) = msg.sender.call{value: address(this).balance}("");
```

### [N-49] Using underscore at the end of variable name

The use of the underscore at the end of the variable name is unusual, consider refactoring it.

<details>
<summary>There are 27 instances (click to show):</summary>

- *ISequencerInbox.sol* ( [247-247](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L247-L247), [254-254](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L254-L254), [274-274](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L274-L274), [288-288](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L288-L288), [289-289](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L289-L289), [290-290](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L290-L290) ):

```solidity
/// @audit maxTimeVariation_
247:     function setMaxTimeVariation(MaxTimeVariation memory maxTimeVariation_) external;

/// @audit isBatchPoster_
254:     function setIsBatchPoster(address addr, bool isBatchPoster_) external;

/// @audit isSequencer_
274:     function setIsSequencer(address addr, bool isSequencer_) external;

/// @audit bridge_
288:         IBridge bridge_,

/// @audit maxTimeVariation_
289:         MaxTimeVariation calldata maxTimeVariation_,

/// @audit bufferConfig_
290:         BufferConfig calldata bufferConfig_
```

- *SequencerInbox.sol* ( [142-142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L142-L142), [161-161](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L161-L161), [178-178](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L178-L178), [179-179](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L179-L179), [180-180](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L180-L180), [219-219](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L219-L219), [220-220](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L220-L220), [221-221](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L221-L221), [222-222](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L222-L222), [255-255](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L255-L255), [256-256](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L256-L256), [257-257](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L257-L257), [258-258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L258-L258), [306-306](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L306-L306), [847-847](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L847-L847), [867-867](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L867-L867), [885-885](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L885-L885), [894-894](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L894-L894), [933-933](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L933-L933), [947-947](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L947-L947) ):

```solidity
/// @audit reader4844_
142:         IReader4844 reader4844_,

/// @audit bufferConfig_
161:     function postUpgradeInit(BufferConfig memory bufferConfig_)

/// @audit bridge_
178:         IBridge bridge_,

/// @audit maxTimeVariation_
179:         ISequencerInbox.MaxTimeVariation calldata maxTimeVariation_,

/// @audit bufferConfig_
180:         BufferConfig memory bufferConfig_

/// @audit delayBlocks_
219:             uint64 delayBlocks_,

/// @audit futureBlocks_
220:             uint64 futureBlocks_,

/// @audit delaySeconds_
221:             uint64 delaySeconds_,

/// @audit futureSeconds_
222:             uint64 futureSeconds_

/// @audit delayBlocks_
255:             uint64 delayBlocks_,

/// @audit futureBlocks_
256:             uint64 futureBlocks_,

/// @audit delaySeconds_
257:             uint64 delaySeconds_,

/// @audit futureSeconds_
258:             uint64 futureSeconds_

/// @audit delayBlocks_
306:         uint256 delayBlocks_ = delayBlocks;

/// @audit bufferConfig_
847:     function _setBufferConfig(BufferConfig memory bufferConfig_) internal {

/// @audit maxTimeVariation_
867:     function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)

/// @audit maxTimeVariation_
885:     function setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)

/// @audit isBatchPoster_
894:     function setIsBatchPoster(address addr, bool isBatchPoster_)

/// @audit isSequencer_
933:     function setIsSequencer(address addr, bool isSequencer_)

/// @audit bufferConfig_
947:     function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {
```

- *BOLDUpgradeAction.sol* ( [84-84](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L84-L84) ):

```solidity
/// @audit bufferConfig_
84:     function postUpgradeInit(BufferConfig memory bufferConfig_) external;
```

</details>

### [N-50] Use a struct to encapsulate multiple function parameters

If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

<details>
<summary>There are 9 instances (click to show):</summary>

- *ISequencerInbox.sol* ( [139-146](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L139-L146), [179-186](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L179-L186), [188-195](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L188-L195), [197-203](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L197-L203), [207-214](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L207-L214), [219-227](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L219-L227), [231-239](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L231-L239) ):

```solidity
139:     function forceInclusion(
140:         uint256 _totalDelayedMessagesRead,
141:         uint8 kind,
142:         uint64[2] calldata l1BlockAndTime,
143:         uint256 baseFeeL1,
144:         address sender,
145:         bytes32 messageDataHash
146:     ) external;

179:     function addSequencerL2BatchFromOrigin(
180:         uint256 sequenceNumber,
181:         bytes calldata data,
182:         uint256 afterDelayedMessagesRead,
183:         IGasRefunder gasRefunder,
184:         uint256 prevMessageCount,
185:         uint256 newMessageCount
186:     ) external;

188:     function addSequencerL2Batch(
189:         uint256 sequenceNumber,
190:         bytes calldata data,
191:         uint256 afterDelayedMessagesRead,
192:         IGasRefunder gasRefunder,
193:         uint256 prevMessageCount,
194:         uint256 newMessageCount
195:     ) external;

197:     function addSequencerL2BatchFromBlobs(
198:         uint256 sequenceNumber,
199:         uint256 afterDelayedMessagesRead,
200:         IGasRefunder gasRefunder,
201:         uint256 prevMessageCount,
202:         uint256 newMessageCount
203:     ) external;

207:     function addSequencerL2BatchFromBlobsDelayProof(
208:         uint256 sequenceNumber,
209:         uint256 afterDelayedMessagesRead,
210:         IGasRefunder gasRefunder,
211:         uint256 prevMessageCount,
212:         uint256 newMessageCount,
213:         DelayProof calldata delayProof
214:     ) external;

219:     function addSequencerL2BatchFromOriginDelayProof(
220:         uint256 sequenceNumber,
221:         bytes calldata data,
222:         uint256 afterDelayedMessagesRead,
223:         IGasRefunder gasRefunder,
224:         uint256 prevMessageCount,
225:         uint256 newMessageCount,
226:         DelayProof calldata delayProof
227:     ) external;

231:     function addSequencerL2BatchDelayProof(
232:         uint256 sequenceNumber,
233:         bytes calldata data,
234:         uint256 afterDelayedMessagesRead,
235:         IGasRefunder gasRefunder,
236:         uint256 prevMessageCount,
237:         uint256 newMessageCount,
238:         DelayProof calldata delayProof
239:     ) external;
```

- *SequencerInbox.sol* ( [287-294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L287-L294), [366-373](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L366-L373) ):

```solidity
287:     function forceInclusion(
288:         uint256 _totalDelayedMessagesRead,
289:         uint8 kind,
290:         uint64[2] calldata l1BlockAndTime,
291:         uint256 baseFeeL1,
292:         address sender,
293:         bytes32 messageDataHash
294:     ) external {

366:     function addSequencerL2BatchFromOrigin(
367:         uint256 sequenceNumber,
368:         bytes calldata data,
369:         uint256 afterDelayedMessagesRead,
370:         IGasRefunder gasRefunder,
371:         uint256 prevMessageCount,
372:         uint256 newMessageCount
373:     ) external refundsGas(gasRefunder, IReader4844(address(0))) {
```

</details>

### [N-51] Returning a struct instead of a bunch of variables is better

If a function returns [too many variables](https://docs.soliditylang.org/en/v0.8.21/contracts.html#returning-multiple-values), replacing them with a struct can improve code readability, maintainability and reusability.

<details>
<summary>There are 7 instances (click to show):</summary>

- *ISequencerInbox.sol* ( [114-122](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L114-L122), [124-124](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L124-L124) ):

```solidity
114:     function maxTimeVariation()
115:         external
116:         view
117:         returns (
118:             uint256 delayBlocks,
119:             uint256 futureBlocks,
120:             uint256 delaySeconds,
121:             uint256 futureSeconds
122:         );

124:     function dasKeySetInfo(bytes32) external view returns (bool, uint64);
```

- *SequencerInbox.sol* ( [244-252](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L244-L252), [269-277](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L269-L277), [637-640](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L637-L640), [659-662](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L659-L662), [688-691](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L688-L691) ):

```solidity
244:     function maxTimeVariation()
245:         external
246:         view
247:         returns (
248:             uint256,
249:             uint256,
250:             uint256,
251:             uint256
252:         )

269:     function maxTimeVariationInternal()
270:         internal
271:         view
272:         returns (
273:             uint64,
274:             uint64,
275:             uint64,
276:             uint64
277:         )

637:     function packHeader(uint256 afterDelayedMessagesRead)
638:         internal
639:         view
640:         returns (bytes memory, IBridge.TimeBounds memory)

659:     function formEmptyDataHash(uint256 afterDelayedMessagesRead)
660:         internal
661:         view
662:         returns (bytes32, IBridge.TimeBounds memory)

688:     function formCallDataHash(bytes calldata data, uint256 afterDelayedMessagesRead)
689:         internal
690:         view
691:         returns (bytes32, IBridge.TimeBounds memory)
```

</details>

### [N-52] Contract variables should have comments

Consider adding some comments on non-public contract variables to explain what they are supposed to do. This will help for future code reviews.

<details>
<summary>There are 11 instances (click to show):</summary>

- *SequencerInbox.sol* ( [120-120](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L120-L120), [121-121](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L121-L121), [122-122](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L122-L122), [129-129](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L129-L129) ):

```solidity
120:     uint64 internal futureBlocks;

121:     uint64 internal delaySeconds;

122:     uint64 internal futureSeconds;

129:     uint256 internal immutable deployTimeChainId = block.chainid;
```

- *BOLDUpgradeAction.sol* ( [99-99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L99-L99), [167-167](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L167-L167) ):

```solidity
99:     mapping(bytes32 => bytes) internal preImages;

167:     uint256[] _array;
```

- *RollupCore.sol* ( [98-98](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L98-L98), [99-99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L99-L99), [101-101](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L101-L101), [104-104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L104-L104) ):

```solidity
98:     bytes32 private _latestConfirmed;

99:     mapping(bytes32 => AssertionNode) private _assertions;

101:     address[] private _stakerList;

104:     mapping(address => uint256) private _withdrawableFunds;
```

- *RollupUserLogic.sol* ( [31-31](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L31-L31) ):

```solidity
31:     uint256 internal immutable deployTimeChainId = block.chainid;
```

</details>

### [N-53] Missing event when a state variables is set in constructor

The initial states set in a constructor are important and should be recorded in the event.

There are 3 instances:

- *BOLDUpgradeAction.sol* ( [170](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L170) ):

```solidity
170:         _array = __array;
```

- *BridgeCreator.sol* ( [49](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L49), [50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L50) ):

```solidity
49:         ethBasedTemplates = _ethBasedTemplates;

50:         erc20BasedTemplates = _erc20BasedTemplates;
```

### [N-54] Empty bytes check is missing

Passing empty bytes to a function can cause unexpected behavior, such as certain operations failing, producing incorrect results, or wasting gas. It is recommended to check that all byte parameters are not empty.

<details>
<summary>There are 5 instances (click to show):</summary>

- *SequencerInbox.sol* ( [366-373](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L366-L373), [430-438](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L430-L438), [560-567](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L560-L567), [582-590](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L582-L590) ):

```solidity
/// @audit data
366:     function addSequencerL2BatchFromOrigin(
367:         uint256 sequenceNumber,
368:         bytes calldata data,
369:         uint256 afterDelayedMessagesRead,
370:         IGasRefunder gasRefunder,
371:         uint256 prevMessageCount,
372:         uint256 newMessageCount
373:     ) external refundsGas(gasRefunder, IReader4844(address(0))) {

/// @audit data
430:     function addSequencerL2BatchFromOriginDelayProof(
431:         uint256 sequenceNumber,
432:         bytes calldata data,
433:         uint256 afterDelayedMessagesRead,
434:         IGasRefunder gasRefunder,
435:         uint256 prevMessageCount,
436:         uint256 newMessageCount,
437:         DelayProof calldata delayProof
438:     ) external refundsGas(gasRefunder, IReader4844(address(0))) {

/// @audit data
560:     function addSequencerL2Batch(
561:         uint256 sequenceNumber,
562:         bytes calldata data,
563:         uint256 afterDelayedMessagesRead,
564:         IGasRefunder gasRefunder,
565:         uint256 prevMessageCount,
566:         uint256 newMessageCount
567:     ) external override refundsGas(gasRefunder, IReader4844(address(0))) {

/// @audit data
582:     function addSequencerL2BatchDelayProof(
583:         uint256 sequenceNumber,
584:         bytes calldata data,
585:         uint256 afterDelayedMessagesRead,
586:         IGasRefunder gasRefunder,
587:         uint256 prevMessageCount,
588:         uint256 newMessageCount,
589:         DelayProof calldata delayProof
590:     ) external refundsGas(gasRefunder, IReader4844(address(0))) {
```

- *EdgeChallengeManager.sol* ( [451-454](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L451-L454) ):

```solidity
/// @audit prefixProof
451:     function bisectEdge(bytes32 edgeId, bytes32 bisectionHistoryRoot, bytes calldata prefixProof)
452:         external
453:         returns (bytes32, bytes32)
454:     {
```

</details>

### [N-55] Don't define functions with the same name in a contract

In Solidity, while function overriding allows for functions with the same name to coexist, it is advisable to avoid this practice to enhance code readability and maintainability. Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the likelihood of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function, but also helps prevent unintended function calls or incorrect overriding. By adopting a clear and consistent naming convention, developers can create more comprehensible and maintainable smart contracts.

<details>
<summary>There are 7 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [57](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L57) ):

```solidity
/// @audit Different function with same name found on line 41
57:     function withdrawFromPool() external {
```

- *IAbsBoldStakingPool.sol* ( [27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L27) ):

```solidity
/// @audit Different function with same name found on line 24
27:     function withdrawFromPool() external;
```

- *ISequencerInbox.sol* ( [179](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L179) ):

```solidity
/// @audit Different function with same name found on line 171
179:     function addSequencerL2BatchFromOrigin(
```

- *SequencerInbox.sol* ( [366](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L366) ):

```solidity
/// @audit Different function with same name found on line 356
366:     function addSequencerL2BatchFromOrigin(
```

- *IRollupLogic.sol* ( [44](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L44) ):

```solidity
/// @audit Different function with same name found on line 38
44:     function newStakeOnNewAssertion(
```

- *RollupLib.sol* ( [37](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L37) ):

```solidity
/// @audit Different function with same name found on line 23
37:     function assertionHash(
```

- *RollupUserLogic.sol* ( [331](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L331) ):

```solidity
/// @audit Different function with same name found on line 316
331:     function newStakeOnNewAssertion(
```

</details>

### [N-56] Multiple mappings with same keys can be combined into a single struct mapping for readability

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related.

There are 7 instances:

- *SequencerInbox.sol* ( [95-95](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L95-L95), [115-115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L115-L115) ):

```solidity
95:     mapping(address => bool) public isBatchPoster;

115:     mapping(address => bool) public isSequencer;
```

- *RollupCore.sol* ( [96-96](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L96-L96), [99-99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L99-L99), [102-102](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L102-L102), [104-104](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L104-L104), [114-114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L114-L114) ):

```solidity
96:     mapping(address => bool) public isValidator;

99:     mapping(bytes32 => AssertionNode) private _assertions;

102:     mapping(address => Staker) public _stakerMap;

104:     mapping(address => uint256) private _withdrawableFunds;

114:     mapping(bytes32 => uint256) internal _assertionCreatedAtArbSysBlock;
```

### [N-57] Do not cache immutable variables

Instead of caching immutable variables, using them directly can make code more consistent and less prone to errors.

There are 5 instances:

- *BOLDUpgradeAction.sol* ( [415-415](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L415-L415), [421-421](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L421-L421), [424-424](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L424-L424), [428-428](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L428-L428), [434-434](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L434-L434) ):

```solidity
415:         TransparentUpgradeableProxy bridge = TransparentUpgradeableProxy(payable(BRIDGE));

421:         TransparentUpgradeableProxy inbox = TransparentUpgradeableProxy(payable(INBOX));

424:         TransparentUpgradeableProxy rollupEventInbox = TransparentUpgradeableProxy(payable(REI));

428:         TransparentUpgradeableProxy outbox = TransparentUpgradeableProxy(payable(OUTBOX));

434:         TransparentUpgradeableProxy sequencerInbox = TransparentUpgradeableProxy(payable(SEQ_INBOX));
```

### [N-58] Missing event for critical changes

Events should be emitted when critical changes are made to the contracts.

<details>
<summary>There are 17 instances (click to show):</summary>

- *DelayBuffer.sol* ( [68-75](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L68-L75) ):

```solidity
68:     function update(BufferData storage self, uint64 blockNumber) internal {
69:         self.bufferBlocks = calcPendingBuffer(self, blockNumber);
70: 
71:         // store a new starting reference point
72:         // any buffer updates will be applied retroactively in the next batch post
73:         self.prevBlockNumber = blockNumber;
74:         self.prevSequencedBlockNumber = uint64(block.number);
75:     }
```

- *SequencerInbox.sol* ( [208-214](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L208-L214), [236-242](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L236-L242), [791-804](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L791-L804), [847-865](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L847-L865), [867-882](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L867-L882) ):

```solidity
208:     function updateRollupAddress() external {
209:         if (msg.sender != IOwnable(rollup).owner())
210:             revert NotOwner(msg.sender, IOwnable(rollup).owner());
211:         IOwnable newRollup = bridge.rollup();
212:         if (rollup == newRollup) revert RollupNotChanged();
213:         rollup = newRollup;
214:     }

236:     function removeDelayAfterFork() external {
237:         if (!_chainIdChanged()) revert NotForked();
238:         delayBlocks = 1;
239:         futureBlocks = 1;
240:         delaySeconds = 1;
241:         futureSeconds = 1;
242:     }

791:     function addSequencerL2BatchImpl(
792:         bytes32 dataHash,
793:         uint256 afterDelayedMessagesRead,
794:         uint256 calldataLengthPosted,
795:         uint256 prevMessageCount,
796:         uint256 newMessageCount
797:     )
798:         internal
799:         returns (
800:             uint256 seqMessageIndex,
801:             bytes32 beforeAcc,
802:             bytes32 delayedAcc,
803:             bytes32 acc
804:         )

847:     function _setBufferConfig(BufferConfig memory bufferConfig_) internal {
848:         if (!isDelayBufferable) revert NotDelayBufferable();
849:         if (!DelayBuffer.isValidBufferConfig(bufferConfig_)) revert BadBufferConfig();
850: 
851:         if (buffer.bufferBlocks == 0 || buffer.bufferBlocks > bufferConfig_.max) {
852:             buffer.bufferBlocks = bufferConfig_.max;
853:         }
854:         if (buffer.bufferBlocks < bufferConfig_.threshold) {
855:             buffer.bufferBlocks = bufferConfig_.threshold;
856:         }
857:         buffer.max = bufferConfig_.max;
858:         buffer.threshold = bufferConfig_.threshold;
859:         buffer.replenishRateInBasis = bufferConfig_.replenishRateInBasis;
860: 
861:         // if all delayed messages are read, the buffer is considered synced
862:         if (bridge.delayedMessageCount() == totalDelayedMessagesRead) {
863:             buffer.update(uint64(block.number));
864:         }
865:     }

867:     function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)
868:         internal
869:     {
870:         if (
871:             maxTimeVariation_.delayBlocks > type(uint64).max ||
872:             maxTimeVariation_.futureBlocks > type(uint64).max ||
873:             maxTimeVariation_.delaySeconds > type(uint64).max ||
874:             maxTimeVariation_.futureSeconds > type(uint64).max
875:         ) {
876:             revert BadMaxTimeVariation();
877:         }
878:         delayBlocks = uint64(maxTimeVariation_.delayBlocks);
879:         futureBlocks = uint64(maxTimeVariation_.futureBlocks);
880:         delaySeconds = uint64(maxTimeVariation_.delaySeconds);
881:         futureSeconds = uint64(maxTimeVariation_.futureSeconds);
882:     }
```

- *ChallengeEdgeLib.sol* ( [239-245](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L239-L245), [249-255](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L249-L255), [264-276](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L264-L276) ):

```solidity
239:     function setChildren(ChallengeEdge storage edge, bytes32 lowerChildId, bytes32 upperChildId) internal {
240:         if (edge.lowerChildId != 0 || edge.upperChildId != 0) {
241:             revert ChildrenAlreadySet(ChallengeEdgeLib.id(edge), edge.lowerChildId, edge.upperChildId);
242:         }
243:         edge.lowerChildId = lowerChildId;
244:         edge.upperChildId = upperChildId;
245:     }

249:     function setConfirmed(ChallengeEdge storage edge) internal {
250:         if (edge.status != EdgeStatus.Pending) {
251:             revert EdgeNotPending(ChallengeEdgeLib.id(edge), edge.status);
252:         }
253:         edge.status = EdgeStatus.Confirmed;
254:         edge.confirmedAtBlock = uint64(block.number);
255:     }

264:     function setRefunded(ChallengeEdge storage edge) internal {
265:         if (edge.status != EdgeStatus.Confirmed) {
266:             revert EdgeNotConfirmed(ChallengeEdgeLib.id(edge), edge.status);
267:         }
268:         if (!isLayerZero(edge)) {
269:             revert EdgeNotLayerZero(ChallengeEdgeLib.id(edge), edge.staker, edge.claimId);
270:         }
271:         if (edge.refunded == true) {
272:             revert EdgeAlreadyRefunded(ChallengeEdgeLib.id(edge));
273:         }
274: 
275:         edge.refunded = true;
276:     }
```

- *EdgeChallengeManagerLib.sol* ( [160-160](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L160-L160), [502-514](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L502-L514), [520-531](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L520-L531), [662-669](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L662-L669) ):

```solidity
160:     function add(EdgeStore storage store, ChallengeEdge memory edge) internal returns (EdgeAddedData memory) {

502:     function updateTimerCache(EdgeStore storage store, bytes32 edgeId, uint256 newValue)
503:         internal
504:         returns (bool, uint256)
505:     {
506:         uint256 currentAccuTimer = store.edges[edgeId].totalTimeUnrivaledCache;
507:         newValue = newValue > type(uint64).max ? type(uint64).max : newValue;
508:         // only update when increased
509:         if (newValue > currentAccuTimer) {
510:             store.edges[edgeId].totalTimeUnrivaledCache = uint64(newValue);
511:             return (true, newValue);
512:         }
513:         return (false, currentAccuTimer);
514:     }

520:     function updateTimerCacheByClaim(
521:         EdgeStore storage store,
522:         bytes32 edgeId,
523:         bytes32 claimingEdgeId,
524:         uint8 numBigStepLevel
525:     ) internal returns (bool, uint256) {
526:         // calculate the time unrivaled without inheritance
527:         uint256 totalTimeUnrivaled = timeUnrivaled(store, edgeId);
528:         checkClaimIdLink(store, edgeId, claimingEdgeId, numBigStepLevel);
529:         totalTimeUnrivaled += store.edges[claimingEdgeId].totalTimeUnrivaledCache;
530:         return updateTimerCache(store, edgeId, totalTimeUnrivaled);
531:     }

662:     function setConfirmedRival(EdgeStore storage store, bytes32 edgeId) internal {
663:         bytes32 mutualId = store.edges[edgeId].mutualId();
664:         bytes32 confirmedRivalId = store.confirmedRivals[mutualId];
665:         if (confirmedRivalId != bytes32(0)) {
666:             revert RivalEdgeConfirmed(edgeId, confirmedRivalId);
667:         }
668:         store.confirmedRivals[mutualId] = edgeId;
669:     }
```

- *RollupCore.sol* ( [355-363](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L355-L363) ):

```solidity
355:     function deleteStaker(address stakerAddress) private {
356:         Staker storage staker = _stakerMap[stakerAddress];
357:         require(staker.isStaked, "NOT_STAKED");
358:         uint64 stakerIndex = staker.index;
359:         _stakerList[stakerIndex] = _stakerList[_stakerList.length - 1];
360:         _stakerMap[_stakerList[stakerIndex]].index = stakerIndex;
361:         _stakerList.pop();
362:         delete _stakerMap[stakerAddress];
363:     }
```

- *RollupCreator.sol* ( [267-285](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L267-L285) ):

```solidity
267:     function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)
268:         internal
269:         returns (address)
270:     {
271:         IUpgradeExecutor upgradeExecutor = IUpgradeExecutor(
272:             address(
273:                 new TransparentUpgradeableProxy(
274:                     address(upgradeExecutorLogic),
275:                     address(proxyAdmin),
276:                     bytes("")
277:                 )
278:             )
279:         );
280:         address[] memory executors = new address[](1);
281:         executors[0] = rollupOwner;
282:         upgradeExecutor.initialize(address(upgradeExecutor), executors);
283: 
284:         return address(upgradeExecutor);
285:     }
```

- *RollupUserLogic.sol* ( [62-66](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L62-L66), [71-75](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L71-L75) ):

```solidity
62:     function removeWhitelistAfterFork() external {
63:         require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
64:         require(_chainIdChanged(), "CHAIN_ID_NOT_CHANGED");
65:         validatorWhitelistDisabled = true;
66:     }

71:     function removeWhitelistAfterValidatorAfk() external {
72:         require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");
73:         require(_validatorIsAfk(), "VALIDATOR_NOT_AFK");
74:         validatorWhitelistDisabled = true;
75:     }
```

</details>

### [N-59] Consider adding emergency-stop functionality

Adding a way to quickly halt protocol functionality in an emergency, rather than having to pause individual contracts one-by-one, will make in-progress hack mitigation faster and much less stressful.

<details>
<summary>There are 6 instances (click to show):</summary>

- *EdgeChallengeManager.sol* ( [206-206](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L206-L206) ):

```solidity
206: contract EdgeChallengeManager is IEdgeChallengeManager, Initializable {
```

- *BridgeCreator.sol* ( [21-21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L21-L21) ):

```solidity
21: contract BridgeCreator is Ownable {
```

- *RollupAdminLogic.sol* ( [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L15-L15) ):

```solidity
15: contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {
```

- *RollupCreator.sol* ( [17-17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L17-L17) ):

```solidity
17: contract RollupCreator is Ownable {
```

- *RollupProxy.sol* ( [11-11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L11-L11) ):

```solidity
11: contract RollupProxy is AdminFallbackProxy {
```

- *RollupUserLogic.sol* ( [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L15-L15) ):

```solidity
15: contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {
```

</details>

### [N-60] Avoid the use of sensitive terms

Use [alternative variants](https://www.zdnet.com/article/mysql-drops-master-slave-and-blacklist-whitelist-terminology/), e.g. allowlist/denylist instead of whitelist/blacklist.

<details>
<summary>There are 63 instances (click to show):</summary>

- *EdgeChallengeManager.sol* ( [194](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L194), [372](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L372), [373](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L373), [374](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L374), [376](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L376), [418](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L418) ):

```solidity
194:     ///         This is only tracked when the validator whitelist is enabled

372:         // Check if whitelist is enabled in the Rollup

373:         // We only enforce whitelist in this function as it may exhaust resources

374:         bool whitelistEnabled = !assertionChain.validatorWhitelistDisabled();

376:         if (whitelistEnabled && !assertionChain.isValidator(msg.sender)) {

418:             args, ard, oneStepProofEntry, expectedEndHeight, NUM_BIGSTEP_LEVEL, whitelistEnabled
```

- *IAssertionChain.sol* ( [27](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/IAssertionChain.sol#L27) ):

```solidity
27:     function validatorWhitelistDisabled() external view returns (bool);
```

- *ChallengeErrors.sol* ( [107](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeErrors.sol#L107) ):

```solidity
107: /// @dev Thrown when the validator whitelist is enabled and the account attempting to create a layer zero edge is not whitelisted
```

- *EdgeChallengeManagerLib.sol* ( [112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L112), [226](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L226), [361](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L361), [418](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L418), [428](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L428), [429](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L429), [430](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L430), [471](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L471), [544](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L544), [554](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L554), [684](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L684) ):

```solidity
112:     /// @notice The id of the assertion - will be used in a sanity check

226:             // Sanity check: The assertion reference data should be related to the claim

361:         // However it's a nice sanity check for the calling code to check that their local edge

418:         bool whitelistEnabled

428:         // if the validator whitelist is enabled, we can enforce that a single party cannot create two layer zero edges that rival each other

429:         // if the validator whitelist is disabled, this check serves no purpose since an attacker can create new accounts

430:         if (whitelistEnabled) {

471:         // Sanity check: it should never be possible to create an edge without having an entry in firstRivals

544:         // Sanity check: it's not possible to have a 0 first rival for an edge that exists

554:             // Sanity check: it's not possible an edge does not exist for a first rival record

684:     /// @dev    Does some additional sanity checks to ensure that the claim id link is valid
```

- *MerkleTreeLib.sol* ( [227](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L227) ):

```solidity
227:         // so this is just a sanity check
```

- *BOLDUpgradeAction.sol* ( [204](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L204), [245](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L245), [327](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L327), [534](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L534), [535](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L535) ):

```solidity
204:     bool public immutable DISABLE_VALIDATOR_WHITELIST;

245:         bool disableValidatorWhitelist;

327:         DISABLE_VALIDATOR_WHITELIST = settings.disableValidatorWhitelist;

534:         if (DISABLE_VALIDATOR_WHITELIST) {

535:             IRollupAdmin(address(rollup)).setValidatorWhitelistDisabled(DISABLE_VALIDATOR_WHITELIST);
```

- *IRollupAdmin.sol* ( [48](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L48), [51](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L51), [52](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L52), [110](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L110), [111](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L111), [113](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L113) ):

```solidity
48:      * @notice Set the addresses of the validator whitelist

51:      * @param _validator addresses to set in the whitelist

52:      * @param _val value to set in the whitelist for corresponding address

110:      * @notice set the validatorWhitelistDisabled flag

111:      * @param _validatorWhitelistDisabled new value of validatorWhitelistDisabled, i.e. true = disabled

113:     function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external;
```

- *IRollupLogic.sol* ( [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L17), [19](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L19) ):

```solidity
17:     function removeWhitelistAfterFork() external;

19:     function removeWhitelistAfterValidatorAfk() external;
```

- *RollupAdminLogic.sol* ( [174](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L174), [177](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L177), [178](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L178), [305](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L305), [306](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L306), [308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L308), [309](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L309) ):

```solidity
174:      * @notice Set the addresses of the validator whitelist

177:      * @param _validator addresses to set in the whitelist

178:      * @param _val value to set in the whitelist for corresponding address

305:      * @notice set the validatorWhitelistDisabled flag

306:      * @param _validatorWhitelistDisabled new value of validatorWhitelistDisabled, i.e. true = disabled

308:     function setValidatorWhitelistDisabled(bool _validatorWhitelistDisabled) external {

309:         validatorWhitelistDisabled = _validatorWhitelistDisabled;
```

- *RollupCore.sol* ( [108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L108), [377](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L377) ):

```solidity
108:     bool public validatorWhitelistDisabled;

377:         // we can do a quick sanity check here
```

- *RollupUserLogic.sol* ( [21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L21), [38](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L38), [41](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L41), [62](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L62), [63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L63), [65](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L65), [69](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L69), [71](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L71), [72](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L72), [74](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L74) ):

```solidity
21:         require(isValidator[msg.sender] || validatorWhitelistDisabled, "NOT_VALIDATOR");

38:      * @notice Number of blocks since the last confirmed assertion before the validator whitelist is removed

41:      *         a further 14 days before the validator whitelist is removed.

62:     function removeWhitelistAfterFork() external {

63:         require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");

65:         validatorWhitelistDisabled = true;

69:      * @notice Remove the whitelist after the validator has been inactive for too long

71:     function removeWhitelistAfterValidatorAfk() external {

72:         require(!validatorWhitelistDisabled, "WHITELIST_DISABLED");

74:         validatorWhitelistDisabled = true;
```

</details>

### [N-61] Missing checks for uint state variable assignments

Consider whether reasonable bounds checks for variables would be useful.

There are 6 instances:

- *EdgeChallengeManager.sol* ( [328-328](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L328-L328), [339-339](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L339-L339), [343-343](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L343-L343), [347-347](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L347-L347) ):

```solidity
328:         challengePeriodBlocks = _challengePeriodBlocks;

339:         LAYERZERO_BLOCKEDGE_HEIGHT = layerZeroBlockEdgeHeight;

343:         LAYERZERO_BIGSTEPEDGE_HEIGHT = layerZeroBigStepEdgeHeight;

347:         LAYERZERO_SMALLSTEPEDGE_HEIGHT = layerZeroSmallStepEdgeHeight;
```

- *RollupAdminLogic.sol* ( [205-205](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L205-L205), [224-224](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L224-L224) ):

```solidity
205:         minimumAssertionPeriod = newPeriod;

224:         baseStake = newBaseStake;
```

### [N-62] Use the Modern Upgradeable Contract Paradigm

Modern smart contract development often employs upgradeable contract structures, utilizing proxy patterns like OpenZeppelin’s Upgradeable Contracts. This paradigm separates logic and state, allowing developers to amend and enhance the contract's functionality without altering its state or the deployed contract address. Transitioning to this approach enhances long-term maintainability.
Resolution: Adopt a well-established proxy pattern for upgradeability, ensuring proper initialization and employing transparent proxies to mitigate potential risks. Embrace comprehensive testing and audit practices, particularly when updating contract logic, to ensure state consistency and security are preserved across upgrades. This ensures your contract remains robust and adaptable to future requirements.

<details>
<summary>There are 11 instances (click to show):</summary>

- *AssertionStakingPool.sol* ( [21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L21) ):

```solidity
21: contract AssertionStakingPool is AbsBoldStakingPool, IAssertionStakingPool {
```

- *AssertionStakingPoolCreator.sol* ( [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L13) ):

```solidity
13: contract AssertionStakingPoolCreator is IAssertionStakingPoolCreator {
```

- *EdgeStakingPool.sol* ( [25](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L25) ):

```solidity
25: contract EdgeStakingPool is AbsBoldStakingPool, IEdgeStakingPool {
```

- *EdgeStakingPoolCreator.sol* ( [13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L13) ):

```solidity
13: contract EdgeStakingPoolCreator is IEdgeStakingPoolCreator {
```

- *SequencerInbox.sol* ( [64](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L64) ):

```solidity
64: contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {
```

- *BOLDUpgradeAction.sol* ( [94](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L94), [123](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L123), [166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L166), [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L182) ):

```solidity
94: contract StateHashPreImageLookup {

123: contract RollupReader is IOldRollup {

166: contract ConstantArrayStorage {

182: contract BOLDUpgradeAction {
```

- *BridgeCreator.sol* ( [21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L21) ):

```solidity
21: contract BridgeCreator is Ownable {
```

- *RollupCreator.sol* ( [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L17) ):

```solidity
17: contract RollupCreator is Ownable {
```

</details>

### [N-63] Large or complicated code bases should implement invariant tests

This includes: large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts.
Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold.
Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers may help significantly.

There is 1 instance:

- Global finding

### [N-64] The default value is manually set when it is declared

In instances where a new variable is defined, there is no need to set it to it's default value.

<details>
<summary>There are 23 instances (click to show):</summary>

- *SequencerInbox.sol* ( [85-85](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L85-L85), [317-317](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L317-L317) ):

```solidity
85:     bytes1 public constant BROTLI_MESSAGE_HEADER_FLAG = 0x00;

317:         bytes32 prevDelayedAcc = 0;
```

- *EdgeChallengeManager.sol* ( [492-492](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L492-L492), [517-517](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L517-L517) ):

```solidity
492:         for (uint256 i = 0; i < edgeIds.length; i++) {

517:         uint64 assertionBlocks = 0;
```

- *ArrayUtilsLib.sol* ( [15-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L15-L15), [47-47](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L47-L47), [50-50](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol#L50-L50) ):

```solidity
15:         for (uint256 i = 0; i < arr.length; i++) {

47:         for (uint256 i = 0; i < arr1.length; i++) {

50:         for (uint256 i = 0; i < arr2.length; i++) {
```

- *MerkleTreeLib.sol* ( [114-114](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L114-L114), [115-115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L115-L115), [188-188](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L188-L188), [293-293](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L293-L293), [294-294](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L294-L294), [326-326](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L326-L326) ):

```solidity
114:         bytes32 accum = 0;

115:         for (uint256 i = 0; i < me.length; i++) {

188:         for (uint256 i = 0; i < me.length; i++) {

293:         uint256 sum = 0;

294:         for (uint256 i = 0; i < me.length; i++) {

326:         uint256 proofIndex = 0;
```

- *BOLDUpgradeAction.sol* ( [350-350](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L350-L350), [528-528](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L528-L528) ):

```solidity
350:         for (uint64 i = 0; i < stakerCount; i++) {

528:             for (uint256 i = 0; i < validators.length; i++) {
```

- *RollupAdminLogic.sol* ( [63-63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L63-L63), [64-64](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L64-L64), [184-184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L184-L184), [230-230](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L230-L230) ):

```solidity
63:         bytes32 parentAssertionHash = bytes32(0);

64:         bytes32 inboxAcc = bytes32(0);

184:         for (uint256 i = 0; i < _validator.length; i++) {

230:         for (uint256 i = 0; i < staker.length; i++) {
```

- *RollupCore.sol* ( [523-523](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L523-L523), [524-524](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L524-L524) ):

```solidity
523:         bytes32 parentAssertionHash = bytes32(0);

524:         bytes32 inboxAcc = bytes32(0);
```

- *RollupCreator.sol* ( [225-225](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L225-L225), [235-235](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L235-L235) ):

```solidity
225:         for (uint256 i = 0; i < deployParams.batchPosters.length; i++) {

235:             for (uint256 i = 0; i < deployParams.validators.length; i++) {
```

</details>

### [N-65] Contracts should have all `public`/`external` functions exposed by `interface`s

All `external`/`public` functions should extend an `interface`. This is useful to ensure that the whole API is extracted and can be more easily integrated by other projects.

<details>
<summary>There are 9 instances (click to show):</summary>

- *SequencerInbox.sol* ( [64](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L64) ):

```solidity
64: contract SequencerInbox is DelegateCallAware, GasRefundEnabled, ISequencerInbox {
```

- *BOLDUpgradeAction.sol* ( [94](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L94), [166](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L166), [182](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L182) ):

```solidity
94: contract StateHashPreImageLookup {

166: contract ConstantArrayStorage {

182: contract BOLDUpgradeAction {
```

- *BridgeCreator.sol* ( [21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L21) ):

```solidity
21: contract BridgeCreator is Ownable {
```

- *RollupAdminLogic.sol* ( [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L15) ):

```solidity
15: contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {
```

- *RollupCreator.sol* ( [17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L17) ):

```solidity
17: contract RollupCreator is Ownable {
```

- *RollupProxy.sol* ( [11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L11) ):

```solidity
11: contract RollupProxy is AdminFallbackProxy {
```

- *RollupUserLogic.sol* ( [15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L15) ):

```solidity
15: contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {
```

</details>

### [N-66] Top-level declarations should be separated by at least two lines

-

<details>
<summary>There are 120 instances (click to show):</summary>

- *AbsBoldStakingPool.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol#L5-L7) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import {IERC20} from "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *AssertionStakingPool.sol* ( [6-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol#L6-L8) ):

```solidity
6: pragma solidity ^0.8.0;
7: 
8: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *AssertionStakingPoolCreator.sol* ( [6-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol#L6-L8) ):

```solidity
6: pragma solidity ^0.8.0;
7: 
8: import "./AssertionStakingPool.sol";
```

- *EdgeStakingPool.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol#L5-L7) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./AbsBoldStakingPool.sol";
```

- *EdgeStakingPoolCreator.sol* ( [6-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol#L6-L8) ):

```solidity
6: pragma solidity ^0.8.0;
7: 
8: import "./EdgeStakingPool.sol";
```

- *StakingPoolCreatorUtils.sol* ( [6-8](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L6-L8), [9-11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol#L9-L11) ):

```solidity
6: pragma solidity ^0.8.0;
7: 
8: import "@openzeppelin/contracts/utils/Create2.sol";

9: import "@openzeppelin/contracts/utils/Address.sol";
10: 
11: library StakingPoolCreatorUtils {
```

- *IAbsBoldStakingPool.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol#L5-L7) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: interface IAbsBoldStakingPool {
```

- *IAssertionStakingPool.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L5-L7), [8-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol#L8-L10) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "../../rollup/IRollupLogic.sol";

8: import "./IAbsBoldStakingPool.sol";
9: 
10: interface IAssertionStakingPool is IAbsBoldStakingPool {
```

- *IAssertionStakingPoolCreator.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L5-L7), [8-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol#L8-L10) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "../../rollup/IRollupLogic.sol";

8: import "./IAssertionStakingPool.sol";
9: 
10: interface IAssertionStakingPoolCreator {
```

- *IEdgeStakingPool.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L5-L7), [8-10](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol#L8-L10) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "../../challengeV2/EdgeChallengeManager.sol";

8: import "./IAbsBoldStakingPool.sol";
9: 
10: interface IEdgeStakingPool is IAbsBoldStakingPool {
```

- *IEdgeStakingPoolCreator.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L5-L7), [7-9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol#L7-L9) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./IEdgeStakingPool.sol";

7: import "./IEdgeStakingPool.sol";
8: 
9: interface IEdgeStakingPoolCreator {
```

- *DelayBuffer.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L5-L7), [106-108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L106-L108), [113-115](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol#L113-L115) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./Messages.sol";

106:     }
107: 
108:     function isUpdatable(BufferData storage self) internal view returns (bool) {

113:     }
114: 
115:     function isValidBufferConfig(BufferConfig memory config) internal pure returns (bool) {
```

- *ISequencerInbox.sol* ( [7-9](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L7-L9), [13-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol#L13-L15) ):

```solidity
7: pragma experimental ABIEncoderV2;
8: 
9: import "../libraries/IGasRefunder.sol";

13: import "./DelayBufferTypes.sol";
14: 
15: interface ISequencerInbox is IDelayedMessageProvider {
```

- *SequencerInbox.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L5-L7), [106-108](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L106-L108), [155-157](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L155-L157), [159-161](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L159-L161), [175-177](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L175-L177), [214-216](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L214-L216), [242-244](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L242-L244), [267-269](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L267-L269), [453-455](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L453-L455), [510-512](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L510-L512), [603-605](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L603-L605), [626-628](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L626-L628), [635-637](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L635-L637), [789-791](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L789-L791), [822-824](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L822-L824), [826-828](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L826-L828), [845-847](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L845-L847), [865-867](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L865-L867), [945-947](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L945-L947), [950-952](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol#L950-L952) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import {

106:     }
107: 
108:     modifier onlyRollupOwnerOrBatchPosterManager() {

155:     }
156: 
157:     function _chainIdChanged() internal view returns (bool) {

159:     }
160: 
161:     function postUpgradeInit(BufferConfig memory bufferConfig_)

175:     }
176: 
177:     function initialize(

214:     }
215: 
216:     function getTimeBounds() internal view virtual returns (IBridge.TimeBounds memory) {

242:     }
243: 
244:     function maxTimeVariation()

267:     }
268: 
269:     function maxTimeVariationInternal()

453:     }
454: 
455:     function addSequencerL2BatchFromBlobsImpl(

510:     }
511: 
512:     function addSequencerL2BatchFromCalldataImpl(

603:     }
604: 
605:     function delayProofImpl(uint256 afterDelayedMessagesRead, DelayProof memory delayProof)

626:     }
627: 
628:     function isDelayProofRequired(uint256 afterDelayedMessagesRead) internal view returns (bool) {

635:     }
636: 
637:     function packHeader(uint256 afterDelayedMessagesRead)

789:     }
790: 
791:     function addSequencerL2BatchImpl(

822:     }
823: 
824:     function inboxAccs(uint256 index) external view returns (bytes32) {

826:     }
827: 
828:     function batchCount() external view returns (uint256) {

845:     }
846: 
847:     function _setBufferConfig(BufferConfig memory bufferConfig_) internal {

865:     }
866: 
867:     function _setMaxTimeVariation(ISequencerInbox.MaxTimeVariation memory maxTimeVariation_)

945:     }
946: 
947:     function setBufferConfig(BufferConfig memory bufferConfig_) external onlyRollupOwner {

950:     }
951: 
952:     function isValidKeysetHash(bytes32 ksHash) external view returns (bool) {
```

- *EdgeChallengeManager.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol#L5-L7) ):

```solidity
5: pragma solidity ^0.8.17;
6: 
7: import "../rollup/Assertion.sol";
```

- *IAssertionChain.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/IAssertionChain.sol#L5-L7) ):

```solidity
5: pragma solidity ^0.8.17;
6: 
7: import "../bridge/IBridge.sol";
```

- *ChallengeEdgeLib.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L5-L7), [65-67](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L65-L67), [182-184](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol#L182-L184) ):

```solidity
5: pragma solidity ^0.8.17;
6: 
7: import "./Enums.sol";

65: }
66: 
67: library ChallengeEdgeLib {

182:     }
183: 
184:     function mutualIdMem(ChallengeEdge memory ce) internal pure returns (bytes32) {
```

- *ChallengeErrors.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeErrors.sol#L5-L7) ):

```solidity
5: pragma solidity ^0.8.17;
6: 
7: import "./Enums.sol";
```

- *EdgeChallengeManagerLib.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L5-L7), [486-488](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L486-L488), [514-516](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L514-L516), [518-520](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L518-L520) ):

```solidity
5: pragma solidity ^0.8.17;
6: 
7: import "./UintUtilsLib.sol";

486:     }
487: 
488:     function timeUnrivaledTotal(EdgeStore storage store, bytes32 edgeId) internal view returns (uint256) {

514:     }
515: 
516:     function updateTimerCacheByChildren(EdgeStore storage store, bytes32 edgeId) internal returns (bool, uint256) {

518:     }
519: 
520:     function updateTimerCacheByClaim(
```

- *MerkleTreeLib.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L5-L7) ):

```solidity
5: pragma solidity ^0.8.17;
6: 
7: import "../../libraries/MerkleLib.sol";
```

- *Assertion.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L5-L7), [91-93](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol#L91-L93) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./AssertionState.sol";

91:     }
92: 
93:     function requireExists(AssertionNode memory self) internal pure {
```

- *AssertionState.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L5-L7), [15-17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L15-L17), [20-22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol#L20-L22) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "../state/GlobalState.sol";

15: }
16: 
17: library AssertionStateLib {

20:     }
21: 
22:     function hash(AssertionState memory state) internal pure returns (bytes32) {
```

- *BOLDUpgradeAction.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L5-L7), [47-49](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L47-L49), [75-77](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L75-L77), [81-83](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L81-L83), [104-106](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L104-L106), [110-112](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L110-L112), [128-130](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L128-L130), [132-134](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L132-L134), [136-138](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L136-L138), [140-142](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L140-L142), [144-146](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L144-L146), [148-150](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L148-L150), [152-154](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L152-L154), [156-158](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L156-L158), [171-173](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L171-L173), [409-411](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L409-L411), [431-433](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L431-L433), [462-464](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol#L462-L464) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "@openzeppelin/contracts-upgradeable/utils/Create2Upgradeable.sol";

47: }
48: 
49: interface IOldRollup {

75: }
76: 
77: interface IOldRollupAdmin {

81: }
82: 
83: interface ISeqInboxPostUpgradeInit {

104:     }
105: 
106:     function set(bytes32 h, ExecutionState calldata executionState, uint256 inboxMaxCount) public {

110:     }
111: 
112:     function get(bytes32 h) public view returns (ExecutionState memory executionState, uint256 inboxMaxCount) {

128:     }
129: 
130:     function wasmModuleRoot() external view returns (bytes32) {

132:     }
133: 
134:     function latestConfirmed() external view returns (uint64) {

136:     }
137: 
138:     function getNode(uint64 nodeNum) external view returns (Node memory) {

140:     }
141: 
142:     function getStakerAddress(uint64 stakerNum) external view returns (address) {

144:     }
145: 
146:     function stakerCount() external view returns (uint64) {

148:     }
149: 
150:     function getStaker(address staker) external view returns (OldStaker memory) {

152:     }
153: 
154:     function isValidator(address validator) external view returns (bool) {

156:     }
157: 
158:     function validatorWalletCreator() external view returns (address) {

171:     }
172: 
173:     function array() public view returns (uint256[] memory) {

409:     }
410: 
411:     function upgradeSurroundingContracts(address newRollupAddress) private {

431:     }
432: 
433:     function upgradeSequencerInbox() private {

462:     }
463: 
464:     function perform(address[] memory validators) external {
```

- *BridgeCreator.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L5-L7), [19-21](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L19-L21), [51-53](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L51-L53), [56-58](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L56-L58), [61-63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L61-L63), [97-99](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol#L97-L99) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "../bridge/Bridge.sol";

19: import "@openzeppelin/contracts/proxy/transparent/ProxyAdmin.sol";
20: 
21: contract BridgeCreator is Ownable {

51:     }
52: 
53:     function updateTemplates(BridgeTemplates calldata _newTemplates) external onlyOwner {

56:     }
57: 
58:     function updateERC20Templates(BridgeTemplates calldata _newTemplates) external onlyOwner {

61:     }
62: 
63:     function _createBridge(

97:     }
98: 
99:     function createBridge(
```

- *Config.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol#L5-L7) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "../state/GlobalState.sol";
```

- *IRollupAdmin.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L5-L7), [11-13](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol#L11-L13) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./IRollupCore.sol";

11: import "./Config.sol";
12: 
13: interface IRollupAdmin {
```

- *IRollupCore.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L5-L7), [13-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol#L13-L15) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./Assertion.sol";

13: import "../challengeV2/IAssertionChain.sol";
14: 
15: interface IRollupCore is IAssertionChain {
```

- *IRollupLogic.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L5-L7), [10-12](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol#L10-L12) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./IRollupCore.sol";

10: import "../bridge/IOwnable.sol";
11: 
12: interface IRollupUser is IRollupCore, IOwnable {
```

- *RollupAdminLogic.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L5-L7), [13-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L13-L15), [226-228](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L226-L228), [235-237](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L235-L237), [256-258](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L256-L258), [267-269](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol#L267-L269) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./IRollupAdmin.sol";

13: import "@openzeppelin/contracts/proxy/beacon/UpgradeableBeacon.sol";
14: 
15: contract RollupAdminLogic is RollupCore, IRollupAdmin, DoubleLogicUUPSUpgradeable {

226:     }
227: 
228:     function forceRefundStaker(address[] calldata staker) external override whenPaused {

235:     }
236: 
237:     function forceCreateAssertion(

256:     }
257: 
258:     function forceConfirmAssertion(

267:     }
268: 
269:     function setLoserStakeEscrow(address newLoserStakerEscrow) external override {
```

- *RollupCore.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L5-L7), [20-22](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L20-L22), [363-365](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L363-L365), [518-520](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L518-L520), [530-532](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L530-L532), [534-536](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L534-L536), [538-540](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L538-L540), [547-549](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L547-L549), [551-553](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L551-L553), [555-557](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L555-L557) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "@openzeppelin/contracts-upgradeable/security/PausableUpgradeable.sol";

20: import "../libraries/ArbitrumChecker.sol";
21: 
22: abstract contract RollupCore is IRollupCore, PausableUpgradeable {

363:     }
364: 
365:     function createNewAssertion(

518:     }
519: 
520:     function genesisAssertionHash() external pure returns (bytes32) {

530:     }
531: 
532:     function getFirstChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {

534:     }
535: 
536:     function getSecondChildCreationBlock(bytes32 assertionHash) external view returns (uint64) {

538:     }
539: 
540:     function validateAssertionHash(

547:     }
548: 
549:     function validateConfig(bytes32 assertionHash, ConfigData calldata configData) external view {

551:     }
552: 
553:     function isFirstChild(bytes32 assertionHash) external view returns (bool) {

555:     }
556: 
557:     function isPending(bytes32 assertionHash) external view returns (bool) {
```

- *RollupCreator.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L5-L7), [15-17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L15-L17), [61-63](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L61-L63), [265-267](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L265-L267), [285-287](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L285-L287) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "./RollupProxy.sol";

15: import {SafeERC20, IERC20} from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
16: 
17: contract RollupCreator is Ownable {

61:     receive() external payable {}
62: 
63:     function setTemplates(

265:     }
266: 
267:     function _deployUpgradeExecutor(address rollupOwner, ProxyAdmin proxyAdmin)

285:     }
286: 
287:     function _deployFactories(
```

- *RollupLib.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L5-L7), [15-17](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L15-L17), [71-73](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol#L71-L73) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "../state/GlobalState.sol";

15: import "../challengeV2/EdgeChallengeManager.sol";
16: 
17: library RollupLib {

71:     }
72: 
73:     function validateConfigHash(
```

- *RollupProxy.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L5-L7), [9-11](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol#L9-L11) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "../libraries/AdminFallbackProxy.sol";

9: import "./Config.sol";
10: 
11: contract RollupProxy is AdminFallbackProxy {
```

- *RollupUserLogic.sol* ( [5-7](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L5-L7), [13-15](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L13-L15), [60-62](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L60-L62), [306-308](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L306-L308), [364-366](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol#L364-L366) ):

```solidity
5: pragma solidity ^0.8.0;
6: 
7: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

13: import {ETH_POS_BLOCK_TIME} from "../libraries/Constants.sol";
14: 
15: contract RollupUserLogic is RollupCore, UUPSNotUpgradeable, IRollupUser {

60:     }
61: 
62:     function removeWhitelistAfterFork() external {

306:     }
307: 
308:     function owner() external view returns (address) {

364:     }
365: 
366:     function receiveTokens(uint256 tokenAmount) private {
```

</details>

### [N-67] Consider adding formal verification proofs

Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).

<details>
<summary>There are 39 instances (click to show):</summary>

- [*AbsBoldStakingPool.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AbsBoldStakingPool.sol)

- [*AssertionStakingPool.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPool.sol)

- [*AssertionStakingPoolCreator.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/AssertionStakingPoolCreator.sol)

- [*EdgeStakingPool.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPool.sol)

- [*EdgeStakingPoolCreator.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/EdgeStakingPoolCreator.sol)

- [*StakingPoolCreatorUtils.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/StakingPoolCreatorUtils.sol)

- [*IAbsBoldStakingPool.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAbsBoldStakingPool.sol)

- [*IAssertionStakingPool.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPool.sol)

- [*IAssertionStakingPoolCreator.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IAssertionStakingPoolCreator.sol)

- [*IEdgeStakingPool.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPool.sol)

- [*IEdgeStakingPoolCreator.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/assertionStakingPool/interfaces/IEdgeStakingPoolCreator.sol)

- [*DelayBuffer.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBuffer.sol)

- [*DelayBufferTypes.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/DelayBufferTypes.sol)

- [*ISequencerInbox.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/ISequencerInbox.sol)

- [*SequencerInbox.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/bridge/SequencerInbox.sol)

- [*EdgeChallengeManager.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/EdgeChallengeManager.sol)

- [*IAssertionChain.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/IAssertionChain.sol)

- [*ArrayUtilsLib.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ArrayUtilsLib.sol)

- [*ChallengeEdgeLib.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeEdgeLib.sol)

- [*ChallengeErrors.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/ChallengeErrors.sol)

- [*EdgeChallengeManagerLib.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol)

- [*Enums.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/Enums.sol)

- [*MerkleTreeLib.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol)

- [*UintUtilsLib.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/UintUtilsLib.sol)

- [*Error.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/libraries/Error.sol)

- [*Assertion.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Assertion.sol)

- [*AssertionState.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/AssertionState.sol)

- [*BOLDUpgradeAction.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BOLDUpgradeAction.sol)

- [*BridgeCreator.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/BridgeCreator.sol)

- [*Config.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/Config.sol)

- [*IRollupAdmin.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupAdmin.sol)

- [*IRollupCore.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupCore.sol)

- [*IRollupLogic.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/IRollupLogic.sol)

- [*RollupAdminLogic.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupAdminLogic.sol)

- [*RollupCore.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol)

- [*RollupCreator.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol)

- [*RollupLib.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupLib.sol)

- [*RollupProxy.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupProxy.sol)

- [*RollupUserLogic.sol*](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupUserLogic.sol)

</details>

### [N-68] Use scopes sparingly

The use of scoped blocks, denoted by `{}` without a preceding control structure like `if`, `for`, etc., allows for the creation of isolated scopes within a function. While this can be useful for managing memory and preventing naming conflicts, it should be used sparingly. Excessive use of these scope blocks can obscure the code's logic flow and make it more difficult to understand, impeding code maintainability. As a best practice, only employ scoped blocks when necessary for memory management or to avoid clear naming conflicts. Otherwise, aim for clarity and simplicity in your code structure for optimal readability and maintainability.

There are 6 instances:

- *EdgeChallengeManagerLib.sol* ( [622-623](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L622-L623), [631-632](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L631-L632), [645-646](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L645-L646), [797-798](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/EdgeChallengeManagerLib.sol#L797-L798) ):

```solidity
622:         {
623:             (bytes32[] memory preExpansion, bytes32[] memory proof) = abi.decode(prefixProof, (bytes32[], bytes32[]));

631:         {
632:             // midpoint proof it valid, create and store the children

645:         {
646:             ChallengeEdge memory upperChild = ChallengeEdgeLib.newChildEdge(

797:         {
798:             bytes32 cursor = edgeId;
```

- *RollupCore.sol* ( [405-406](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCore.sol#L405-L406) ):

```solidity
405:         {
406:             // This new assertion consumes the messages from prevInboxPosition to afterInboxPosition
```

- *RollupCreator.sol* ( [142-143](https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/rollup/RollupCreator.sol#L142-L143) ):

```solidity
142:         {
143:             // Make sure the immutable maxDataSize is as expected
```
