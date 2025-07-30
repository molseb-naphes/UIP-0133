# UIP-0133
uip_0133_crosschain_identities
```
UIP-0133: Tokenized Moons and Comets for Cross-Chain Identity and Privacy
Title: Multi-Asset Identity Extensions and Cross-Chain Integration for Urbit
Author: ~molseb-naphes
Status: Draft
Created: 2025-07-30
License: MIT
```

## Abstract

This proposal broadens Urbit’s identity model by integrating evolving Ethereum token standards and zero-knowledge Layer 2 (L2) infrastructures to enable programmable, scalable, and private identities. It upgrades the `ecliptic.eth` contract to support:

* **ERC-1155**-based moons: representing multi-asset token containers issued by planets from a unified URI.
* **ERC-404**-based comets: ephemeral identities signed by parent planets but usable as hybrid NFTs/fungible tokens.
* **ERC-7683** cross-chain messaging: allowing Urbit ships to interoperate securely across blockchain ecosystems.
* **Aztec zkEVM**: providing L2 privacy, shielding Urbit’s identity operations from public ledgers.

The system maintains the hierarchical nature of Urbit identities (planet → moon → comet) while granting moons and comets autonomous, on-chain capabilities. It enables token-gated apps, DAOs, DeFi agents, and ephemeral agents to operate under delegated identity structures with verifiable sponsorship and secure revocation.

---

## Motivation

Urbit's current identity management exposes all state changes on the Ethereum L1, making private or fine-grained delegation infeasible. Additionally, moons and comets lack general-purpose asset programmability, reducing their utility in modern blockchain and 'real world' applications.

This UIP introduces an extensible system to:

* Empower **moons** to represent complex tokenized sub-identities.
* Use **comets** as ephemeral actors in DAOs, cross-chain workflows, and zk proving and verification environments.
* Preserve Urbit's sponsorship logic while extending its utility into DeFi, cross-chain apps, and privacy-preserving operations.

---

## Specification

### 1. ERC-1155 Moons

* Moons minted as ERC-1155 tokens by planets.
* Shared base URI allows moons to inherit metadata and logic.
* Moons can:

  * Act as custodians of fungible (ERC-20) and non-fungible (ERC-721) assets.
  * Serve as programmable identities in DAOs and apps.
  * Participate in on-chain governance.

**References:**

* [https://eips.ethereum.org/EIPS/eip-1155](https://eips.ethereum.org/EIPS/eip-1155)
* [https://github.com/OpenZeppelin/openzeppelin-contracts](https://github.com/OpenZeppelin/openzeppelin-contracts)

### 2. ERC-404 Comets

* Comets minted as ERC-404 tokens.
* Signed by a parent planet and optionally linked to a moon.
* Self-expiring / revocable agents for ephemeral actions.
* Useful in privacy contexts, task automation, or per-session delegation.

**References:**

* [https://ethereum-magicians.org/t/erc-404](https://ethereum-magicians.org/t/erc-404)
* [https://github.com/Vectorized/erc404](https://github.com/Vectorized/erc404)

### 3. ERC-7683 Cross-Chain Functionality

* Enables moons and comets to interface with other chains.
* Messaging routed through LayerZero-like infrastructure.
* Attestations signed by planets included in payloads.

**References:**

* [https://eips.ethereum.org/EIPS/eip-7683](https://eips.ethereum.org/EIPS/eip-7683)
* [https://github.com/LayerZero-Labs](https://github.com/LayerZero-Labs)

### 4. Aztec.network &  L1 zkEVM Integration

* Moons and comets shielded via zk-rollup architecture.
* Transactions anonymized, accessible only to authorized parties.
* Comet revocation and identity delegation are auditable but private.

**References:**

* [https://docs.aztec.network](https://docs.aztec.network)
* [https://github.com/AztecProtocol](https://github.com/AztecProtocol)
* (https://blog.ethereum.org/2025/07/10/realtime-proving)

---

## Rationale

* **Why ERC-1155 for moons?** Allows diverse asset types with shared logic.
* **Why ERC-404 for comets?** Supports ephemeral, hybrid identity/asset roles.
* **Why LayerZero/7683?** Enables ecosystem interoperability.
* **Why Aztec?** Ensures confidentiality in identity lifecycle.

This approach retains Urbit’s hierarchical ship model while unlocking real-world use cases: token-gated access, identity-differentiated dApps, zkDAO membership, temporary worker agents, and sovereign asset vaults.

---

## Backwards Compatibility

* No changes to galaxy/star/planet minting.
* `ecliptic.eth` extended via proxy-compatible methods.
* Sponsor signatures remain verifiable and cryptographically anchored to L1.

---

## Test Cases

1. **Moon DAO Membership**

   * A moon is issued an ERC-1155 token with DAO voting logic.
   * It holds and manages an ERC-20 balance.

2. **Comet zk Agent**

   * A comet is granted limited access to a moon-controlled vault.
   * Its revocation occurs privately on Aztec L2.

3. **Cross-Chain Operation**

   * A comet signs a LayerZero message invoking a remote call on Arbitrum.

---

## Security Considerations

* **Revocation Semantics**: Comet expiration must be cryptographically enforced.
* **L2 Trust Models**: Shielding relies on Aztec’s correctness guarantees.
* **Reentrancy and Delegation**: Delegate patterns must be audited rigorously.
* **URI Spoofing**: Prevent overlapping moon metadata or duplicate IDs.

---

---
## References

* UIP-132: [https://github.com/urbit/UIPs/blob/main/UIPS/UIP-0132.md](https://github.com/urbit/UIPs/blob/main/UIPS/UIP-0132.md)
* Aztec zkEVM: [https://docs.aztec.network](https://docs.aztec.network)
* ERC-1155: [https://eips.ethereum.org/EIPS/eip-1155](https://eips.ethereum.org/EIPS/eip-1155)
* ERC-404 (Draft): [https://ethereum-magicians.org/t/erc-404](https://ethereum-magicians.org/t/erc-404)
* ERC-7683: [https://eips.ethereum.org/EIPS/eip-7683](https://eips.ethereum.org/EIPS/eip-7683)

---

## Copyright

This document is licensed under the MIT License.
