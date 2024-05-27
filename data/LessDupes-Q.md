### [L-01] Root collision in Merkle tree expansions

https://github.com/code-423n4/2024-05-arbitrum-foundation/blob/6f861c85b281a29f04daacfe17a2099d7dad5f8f/src/challengeV2/libraries/MerkleTreeLib.sol#L110

The function `MerkleTreeLib.root` is used to calculate the root of Merkle tree expansions.

It does so by incrementally hashing the expansion elements from the lowest-order to the highest-order elements.

However, in its loop, the state of the calculation `accum` is left unchanged until the first non-zero subtree is found, and this means that the number of leading zeros in the expansion doesn't influence the root calculation at all.

For example, the tree `[bytes32(uint(0)), bytes32(uint(1))]` has the same root as `[bytes32(uint(1))]` and `[bytes32(uint(0)), bytes32(uint(0)), bytes32(uint(0)), bytes32(uint(1))]`.

While this is in general not a problem, it can be more problematic when dealing with Merkle trees having an even number of elements which are known.

Since such Merkle trees have an even number of elements, their first element is zero, so the full expansion can be shifted left without changing the root.

These left-shifted Merkle trees could theoretically pass the `verifyInclusionProof` check logic because:
- despite being a forged expansion, they reduce to a legitimate root
- the caller is able to provide a `proof` because by knowing the elements of the original expansion, they know the preimage of elements that build up to the legitimate root

There doesn't seem to be any way to directly exploit this issue because all practical usages of expansions within the protocol scope have odd numbers of elements, however, it is warmly recommended to also hash the leading zeros when computing the Merkle trees to have an in-depth defense against this kind of attack.
