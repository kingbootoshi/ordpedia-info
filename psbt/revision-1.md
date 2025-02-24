A PSBT (Partially Signed Bitcoin Transaction) is a special Bitcoin transaction format that helps multiple people or devices work together to create and sign a transaction. Think of it as a draft version of a transaction that you pass around. Each person checks the details, adds their approval (signature), and then passes it to the next person. It’s useful in situations like using hardware wallets, multi-signature wallets, or privacy tools like CoinJoin. 

- **Partially Signed**: A PSBT isn’t fully signed yet. It can start with no signatures, and participants gradually add their signatures until it’s complete.

**What is it Used for?**

- **Multi-Signature Wallets**: When more than one person needs to sign a transaction.

- **Hardware Wallets**: Letting a secure, offline device sign the transaction without exposing private keys.

- **Privacy Tools**: Like CoinJoin, where participants pool transactions for privacy.

**PSBT Structure:**

- Global Data: Metadata relevant to the entire transaction.
- Input Data: Information about each input (e.g., UTXOs being spent).
- Output Data: Details about where the Bitcoin is being sent.
- Signatures: Any added signatures for the transaction.

**Resources:**

[BIP174](https://github.com/bitcoin/bips/blob/master/bip-0174.mediawiki)

[BIP370](https://github.com/bitcoin/bips/blob/master/bip-0370.mediawiki)
