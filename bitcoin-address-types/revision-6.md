# Introduction

In Bitcoin, there are several types of addresses that have emerged as the protocol evolved. Each offers unique features, advantages, and applications. Below, you'll find detailed explanations of how SegWit, Nested SegWit, Taproot, and Legacy addresses work, along with a comparison table of their characteristics.

**1. Legacy (Traditional Addresses)**

- Description: Traditional addresses, also known as P2PKH (Pay-to-PubKey-Hash) addresses, were the first type of addresses introduced in Bitcoin.

- Format: Starts with the number 1 (e.g., 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa).

- Advantages: Most compatible with the entire ecosystem.

- Disadvantages: Higher transaction fees due to greater block space usage.

**2. SegWit (Segregated Witness)**

- Description: Introduced in 2017, SegWit separates transaction signature data (the "witness") from the main transaction block, improving efficiency and reducing transaction costs.

- Format: Native SegWit addresses start with bc1 (e.g., bc1qw4sk0k...).

- Advantages: Lower fees, increased block capacity, reduced risk of "transaction malleability."

- Disadvantages: Requires compatibility from wallets and exchanges.

**3. Nested SegWit (P2SH)**

- Description: P2SH (Pay-to-Script-Hash) addresses allow the use of SegWit on addresses that start with 3. This transitional format enhances compatibility with systems that did not yet support native SegWit.

- Format: Starts with 3 (e.g., 3J98t1WpEZ73CNmQviecrnyiWrnqRhWNLy).

- Advantages: Better compatibility with older systems.

- Disadvantages: Higher fees compared to native SegWit.

**4. Taproot**

- Description:  Introduced in 2021 as part of a Bitcoin protocol upgrade, Taproot extends SegWit with new capabilities such as simplifying multi-signature (multisig) transactions and enhancing privacy. Taproot uses Schnorr signatures and is integral to the Ordinals protocol, enabling unique data (like NFTs) to be assigned to individual satoshis.

- Format: Starts with bc1p (e.g., bc1p4sk0k...).

- Advantages: Enhanced privacy, more efficient multisig transactions, support for advanced script functionalities, and essential for Ordinals.

- Disadvantages: Limited adoption at the time of introduction.

**Comparison Table**

| Address Type | Format | Advantages | Disadvantages | Applications |
|----------|----------|----------|----------|----------|
| Legacy   | 1 | Highest compatibility | Higher transaction fees | All types of transactions |
| SegWit   | bc1 | Lower fees, greater efficiency | Requires compatibility | Low-cost transactions |
| Nested SegWit   | 3 | Better compatibility | Higher fees than SegWit | Cross-system transactions |
| Taproot   | bc1p | Privacy, efficiency, multisig | Requires adoption | Advanced scripts, multisig, Ordinals, Runes |

**Summary**

Each address type has its own use cases and characteristics. Legacy is the most compatible but expensive, SegWit offers efficiency and lower fees, Nested SegWit bridges compatibility with modern features, and Taproot introduces advanced functionality and enhanced privacy. Taproot is also critical for the Ordinals protocol, making it essential for applications like unique data assigned to satoshis. The choice of format depends on the user's needs and the level of technical support available in the tools being used.
