# Ordinal Numbers

Ordinal Numbers in the context of Bitcoin Ordinals refer to a unique serial number assigned to each satoshi, allowing them to be individually tracked and identified. This system was introduced by Casey Rodarmor with the Ordinal Theory protocol.

## Concept

- **Definition**: An ordinal number is a unique identifier given to each satoshi based on the order in which it was mined or transferred. This number starts from 0 for the first satoshi in the genesis block and continues sequentially.

- **Assignment**: Ordinals are assigned through a first-in, first-out (FIFO) approach, following the transaction history of each satoshi. If a satoshi is spent, its ordinal number transfers to the new UTXO (Unspent Transaction Output) it creates.

## Technical Details

- **Mining and Transfer**: When satoshis are mined, they are given ordinal numbers based on their position in the block. During transactions, the ordinal number follows the satoshi, ensuring each retains its unique identifier.

- **Inscriptions**: By associating data with these ordinal numbers, satoshis can become non-fungible, hosting digital artifacts like art or documents, creating what is akin to NFTs on Bitcoin.

## Significance

- **Non-Fungibility**: Ordinal numbers enable satoshis to be treated as non-fungible, opening up new use cases for Bitcoin beyond mere currency.

- **Tracking**: The assignment of ordinal numbers allows for the tracking of satoshis through the blockchain, providing a history of ownership and use.

## Challenges and Considerations

- **Scalability**: As each satoshi gets a unique number, this system adds complexity to Bitcoin's data management, potentially affecting scalability.

- **Privacy**: While beneficial for tracking, it could be seen as a privacy concern since it allows tracing the history of every satoshi.

## Conclusion

Ordinal numbers have transformed how we perceive Bitcoin's smallest unit, turning satoshis into trackable, potentially unique digital assets. This innovation has sparked both creativity and debate within the crypto community regarding Bitcoin's role and functionality.

### Further Reading

- [Ordinal Theory Handbook](https://docs.ordinals.com/) - Detailed explanation of how ordinal numbers are assigned and their implications.
