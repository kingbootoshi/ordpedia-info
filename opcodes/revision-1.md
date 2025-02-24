**Opcodes** 



**What are Opcodes?** 

Opcodes (operational codes) are instructions that allow setting transaction conditions on the Bitcoin protocol, with each opcode designed to execute a specific command on the network. 

Bitcoin users and developers can utilize opcodes to remove, add, move, or rotate elements on the stack, invalidate or validate transactions, execute calculations, and perform other functions. The opcodes serve as tools to ensure network transactions function seamlessly. 

Bitcoin’s programming language, Bitcoin Script, allows people to utilize opcodes to perform different operations. Bitcoin Script is a simple programming language designed to limit its functionality and prevent instances of error execution and endless looping. The design helps ensure complicated operations cannot slow the network down.  

Opcodes are the foundation of Bitcoin’s scripting capabilities that enable automated, customizable transactions. Users can input the code as a word command with the “OP” prefix.

As a digital currency, Bitcoin is programmable money, and using opcodes, you can program various commands. Bitcoin’s structure allows users to define up to 256 opcodes, with the opcodes assigned a number between 0 and 255. Currently, less than half of them are active.


*(deeper dive)*

In Bitcoin, opcodes (short for "operation codes") are the building blocks of Bitcoin Script, the language used for writing scripts that define the conditions under which transactions can be spent. Bitcoin Script is a stack-based language, and opcodes perform operations on the data stored in the stack.

Each opcode is a single byte and represents a specific operation. These opcodes manipulate the stack, perform cryptographic operations, control flow (e.g., conditional branches), and more.

*Key Features of Opcodes:*

Stack-based: Operations are performed on the stack, where data (such as values, public keys, signatures, etc.) is pushed and popped.

Non-Turing Complete: Bitcoin Script is intentionally designed to be non-Turing complete, meaning it can't perform arbitrary loops or complex computations, which makes it more secure.

No Side Effects: Opcodes themselves don’t modify the blockchain directly; they only affect the logic of the transaction verification process.
Most Commonly Used Opcodes in Bitcoin

*Here’s a list of some of the most commonly used opcodes in Bitcoin:*

1. *OP_DUP*
Purpose: Duplicates the top item on the stack.
Usage: Often used with OP_HASH160 to verify a signature, ensuring the public key is duplicated before hashing.
Example:

OP_DUP OP_HASH160 <pubKeyHash> OP_EQUALVERIFY

This ensures the public key hashes to the correct value.

2. *OP_HASH160*

Purpose: Performs a RIPEMD-160 hash after a SHA-256 hash on the item at the top of the stack (commonly used to hash a public key).

Usage: This opcode is used in many Bitcoin scripts for public key hashes.
Example:

OP_DUP OP_HASH160 <pubKeyHash> OP_EQUALVERIFY

3. *OP_EQUALVERIFY*

Purpose: Verifies that the two items on top of the stack are equal. It also removes them from the stack.

Usage: Typically used to verify signatures or public key hashes.
Example:


OP_DUP OP_HASH160 <pubKeyHash> OP_EQUALVERIFY


4. *OP_CHECKSIG*
Purpose: Verifies a signature. The top item on the stack must be a public key, and the second item must be a signature.

Usage: Used in most standard Bitcoin transactions to verify that a signature matches the public key.
Example:


<signature> <publicKey> OP_CHECKSIG

5. *OP_CHECKMULTISIG*

Purpose: Verifies multiple signatures. The stack contains multiple public keys and signatures, and this opcode ensures that the signatures match the public keys.

Usage: Used for multisignature transactions, where multiple participants must sign a transaction.
Example:


<signature1> <signature2> <pubKey1> <pubKey2> OP_CHECKMULTISIG

6. *OP_RETURN*

Purpose: Marks an output as "unspendable" and allows for the embedding of arbitrary data into the blockchain.
Usage: Used for storing metadata or creating data that cannot be spent (e.g., tokens or proofs).
Example:

OP_RETURN <data>

7. *OP_VERIFY*

Purpose: Verifies the top stack item is true (non-zero). If the item is false (zero), the script fails.
Usage: Used after certain operations, such as signature verification, to ensure that a condition is true.
Example:

<result> OP_VERIFY

8. *OP_IF / OP_ELSE / OP_ENDIF*

Purpose: Implements conditional logic.
OP_IF: If the top stack item is true, the following block of code is executed.
OP_ELSE: The block after OP_ELSE is executed if the condition is false.
OP_ENDIF: Marks the end of the conditional block.
Usage: Used for complex spending conditions, such as requiring signatures under certain conditions or time locks.
Example:

<condition> OP_IF
    <code for true>
OP_ELSE
    <code for false>
OP_ENDIF

9. *OP_CHECKLOCKTIMEVERIFY* (CLTV)

Purpose: Ensures that a transaction cannot be spent before a specific time (timestamp or block height).
Usage: Used for implementing timelocks to prevent spending of funds before a certain block or time.
Example:


<locktime> OP_CHECKLOCKTIMEVERIFY OP_DROP

10. *OP_CHECKSEQUENCEVERIFY* (CSV)

Purpose: Used to enforce a relative locktime on a transaction. This enables sequential time locks relative to the previous transaction.
Usage: Used in more advanced scenarios like payment channels or HTLCs (Hashed Time-Locked Contracts).
Example:

<sequence> OP_CHECKSEQUENCEVERIFY

*Key Takeaways:*

OP_DUP, OP_CHECKSIG, OP_EQUALVERIFY, and OP_HASH160 are frequently used in typical Bitcoin transactions for public key and signature verification.

OP_RETURN is used for embedding data into the blockchain.

OP_IF, OP_ELSE, and OP_ENDIF enable conditional logic in scripts, allowing for more complex contract-like behavior.

OP_CHECKLOCKTIMEVERIFY and OP_CHECKSEQUENCEVERIFY help enforce time and sequence-based conditions for spending funds.

*How These Opcodes Are Used:*

Most Bitcoin transactions use a small set of opcodes to check signatures and verify ownership of funds. More complex use cases, such as multisignature wallets, time-locked vaults, and payment channels, make use of a broader range of opcodes.



**What Do Opcodes Do in Bitcoin?**

On the Bitcoin network, opcodes play a central role in defining the formulation and execution of transactions. Users need transactions to take various forms. Opcodes help ensure seamless operations regardless of the complexity of the conditions and rules of each transaction.

Bitcoin Script allows users to write programs that execute commands. Script opcodes are the users’ way of communicating to indicate the functions they wish to implement. The opcodes include instructions on the access and utilization of the bitcoins involved in that transaction. 

The OP_CAT Bitcoin opcode would be an example of what opcodes do in Bitcoin. In 2010, it became inactive due to the community’s concerns about memory-related issues. Over time, alleviation of those concerns led to OP_CAT’s recent re-emergence. 

When it comes to OP_CAT, the opcode can potentially implement covenants that spell out conditions for issuing Bitcoin outputs. This introduces scalable, controlled transactions. Additionally, the opcode plays a role in optimizing and simplifying the Bitcoin Virtual Machine (BitVM). An efficient and user-friendly BitVM raises Bitcoin’s profile as a platform for innovation. 

**Types of Opcodes in Bitcoin**

Opcodes fall into various categories based on their functions. Let’s look at the existing types of opcodes in Bitcoin. 

***Cryptography***: Users can utilize such opcodes to execute cryptographic commands on the target data. An example is OP_HASH256, which hashes the input twice using SHA-256, a cryptographic algorithm that improves security. 

**OP_RIPEMD160**

Opcode number: 166

Byte representation: 0xa6

Short Description: Hash the top stack item using RIPEMD160. (The input is hashed using RIPEMD-160.)

The OP_RIPEMD160 opcode replaces the top stack item with its RIPEMD160 hash. If the stack is empty the script fails.

**OP_SHA1**

Opcode number: 167

Byte representation: 0xa7

Short Description: Hash the top stack item using SHA1. (The input is hashed using SHA-1.)

The OP_SHA1 opcode replaces the top stack item with its SHA1 hash. If the stack is empty the script fails.

Note that SHA1 is not considered a secure hash function anymore.

**OP_SHA256**

Opcode number: 168

Byte representation: 0xa8

Short Description: Hash the top stack item using SHA256. (The input is hashed using SHA-256.)

The OP_SHA256 opcode replaces the top stack item with its SHA256 hash. If the stack is empty the script fails.

**OP_HASH160**

Opcode number: 169

Byte representation: 0xa9

Short Description: Hash the top stack item using SHA256 and then RIPEMD160. (The input is hashed twice: first with SHA-256 and then with RIPEMD-160.)

The OP_HASH160 opcode replaces the top stack item with the RIPEMD160 hash of its SHA256 hash. If the stack is empty the script fails.

**OP_HASH256**

Opcode number: 170

Byte representation: 0xaa

Short Description: Hash the top stack item using double SHA256. (The input is hashed two times with SHA-256.)

The OP_HASH256 opcode replaces the top stack item with its double SHA256 hash. If the stack is empty the script fails.

**OP_CODESEPARATOR**

Opcode number: 171

Byte representation: 0xab

OP_CODESEPARATOR is an opcode that changes what data is used when a signature commits to a script. The opcode has been available since the original version of Bitcoin Script, but its use and behavior have changed over time (with further changes having been proposed). (All of the signature checking words will only match signatures to the data after the most recently-executed OP_CODESEPARATOR.)

The main purpose of OP_CODESEPARATOR is to act as a delimiter, separating the signature script from the public key script in a script. In particular, it is used in SegWit transactions where there may be a difference between the two sections of the script being validated.

When an OP_CODESEPARATOR is encountered, it causes the script execution to reset the "code separation point," meaning that any previous operations in the script before the OP_CODESEPARATOR are excluded from affecting the current execution context. It allows for better separation of the witness data from the rest of the script execution.

**OP_CHECKSIG**

Opcode number: 172

Byte representation: 0xac

The OP_CHECKSIG opcode in Bitcoin Script is used to verify that a digital signature matches the public key associated with the input being spent in a transaction. Specifically, it checks if the signature provided in the scriptSig (the unlocking script) is valid for the public key and transaction data provided in the scriptPubKey (the locking script).

(The entire transaction's outputs, inputs, and script (from the most recently-executed OP_CODESEPARATOR to the end) are hashed. The signature used by OP_CHECKSIG must be a valid signature for this hash and public key. If it is, 1 is returned, 0 otherwise.)

The primary purpose of OP_CHECKSIG is to ensure that the person spending the Bitcoin has the private key corresponding to the public key in the script, thus proving ownership of the funds.

**OP_CHECKSIGVERIFY**

Opcode number: 173

Byte representation: 0xad

The OP_CHECKSIGVERIFY opcode in Bitcoin Script combines the functionality of OP_CHECKSIG with a verification step. It performs the same operation as OP_CHECKSIG, which is to verify a digital signature against the provided public key, but with the added behavior of automatically halting execution if the signature check fails. (Same as OP_CHECKSIG, but OP_VERIFY is executed afterward.)

The purpose of OP_CHECKSIGVERIFY is to simplify the process of signature verification by combining the signature check and the verification step in one opcode, reducing the need for additional flow control or result handling in the script.

**OP_CHECKMULTISIG**

Opcode number: 174

Byte representation: 0xae

OP_CHECKMULTISIG is a Bitcoin Script opcode that enables multi-signature functionality. It allows a script to require multiple signatures from a set of public keys in order to authorize a transaction. This is commonly used in scenarios where more than one party needs to sign off on a transaction before it is valid.

(Compares the first signature against each public key until it finds an ECDSA match. Starting with the subsequent public key, it compares the second signature against each remaining public key until it finds an ECDSA match. The process is repeated until all signatures have been checked or not enough public keys remain to produce a successful result. All signatures need to match a public key. Because public keys are not checked again if they fail any signature comparison, signatures must be placed in the scriptSig using the same order as their corresponding public keys were placed in the scriptPubKey or redeemScript. If all signatures are valid, 1 is returned, 0 otherwise. Due to a bug, one extra unused value is removed from the stack.)

Purpose: Verifies that a required number of signatures (m) from a list of public keys (n) have been provided in the unlocking script, making it possible to implement multi-signature logic in Bitcoin transactions.

Stack Handling: One subtle aspect of OP_CHECKMULTISIG is that it manipulates the stack in a specific way. It removes an extra item from the stack when verifying signatures. The exact stack behavior is something to be aware of when working with this opcode in Bitcoin Script.

Use Cases: Multi-signature scripts are often used in:

Escrow transactions: For example, in a 2-of-3 multi-signature setup, two parties can approve a transaction, while a trusted third party can act as a backup.

Corporate wallets: Requiring multiple signatures from different people or systems.
Secure wallet backups: Requiring multiple signatures to protect funds.

**OP_CHECKMULTISIGVERIFY**

Opcode number: 175

Byte representation: 0xaf

OP_CHECKMULTISIGVERIFY is a variant of OP_CHECKMULTISIG in Bitcoin Script, and it functions similarly, but with an important difference: it automatically fails the script execution if the multi-signature verification fails. (Same as OP_CHECKMULTISIG, but OP_VERIFY is executed afterward.)

OP_CHECKMULTISIG checks whether the required number of signatures from a list of public keys are provided in the unlocking script (scriptSig), but it leaves the result on the stack, meaning you need additional logic to handle the result.

OP_CHECKMULTISIGVERIFY, on the other hand, performs the same signature verification but with an additional behavior: if the verification fails, the script execution stops immediately. This means that if the multi-signature check fails, the script fails without needing to manually handle the failure in subsequent script logic.

OP_CHECKMULTISIG: Leaves a result on the stack (a 1 or 0 indicating success or failure).

OP_CHECKMULTISIGVERIFY: Fails immediately and aborts script execution if the multi-signature check fails, providing a cleaner way to enforce multi-signature validation in a script.

Purpose: It performs a multi-signature verification like OP_CHECKMULTISIG but with the added feature that the script execution stops immediately if the verification fails, making it useful for simplifying multi-signature validation in Bitcoin scripts.

**OP_CHECKSIGADD**

Opcode number: 186

Byte representation: 0xba

The OP_CHECKSIGADD opcode is part of a set of opcodes designed to perform signature aggregation in Bitcoin Script. Specifically, OP_CHECKSIGADD allows for the accumulation of the result of a signature verification check, meaning that it can be used in conjunction with other operations to track how many valid signatures are provided in a script.

(Three values are popped from the stack. The integer n is incremented by one and returned to the stack if the signature is valid for the public key and transaction. The integer n is returned to the stack unchanged if the signature is the empty vector (OP_0). In any other case, the script is invalid. This opcode is only available in tapscript.[2])

OP_CHECKSIGADD works as follows:

It checks the validity of a signature against the provided public key (similar to OP_CHECKSIG).

However, instead of directly returning a success or failure value, OP_CHECKSIGADD adds the result of the signature check to the top of the stack.

If the signature is valid, it adds 1 to the stack.

If the signature is invalid, it adds 0 to the stack.

This functionality is useful when you want to keep track of the total number of valid signatures provided in a multi-signature context.

Purpose: It checks the validity of a signature and adds the result (1 for valid, 0 for invalid) to the stack, allowing for aggregation of signature verifications in a Bitcoin Script.


***Flow control***: When you need an opcode to determine the script’s flow, those in this category come in handy. An example is OP_VERIFY, which marks a transaction as invalid if the top stack is false. 

**OP_NOP**

Opcode number: 176

Byte representation: 0xb0

OP_NOP is a Bitcoin Script opcode that does nothing — it essentially acts as a no-operation (NOP) instruction. When OP_NOP is encountered in a script, it has no effect on the stack or the script's execution flow. It can be used as a placeholder or for future upgrades or modifications of Bitcoin Script, where certain opcodes may be reserved for future use.

**OP_IF**

Opcode number: 99

Byte representation: 0x63

Short description: Pop and execute the next statements if a nonzero element was popped.(If the top stack value is not False, the statements are executed. The top stack value is removed.)

OP_IF checks the top item on the stack. If the value is true (non-zero), the subsequent block of code is executed. If the value is false (zero), the script skips to the matching OP_ELSE (if present) or OP_ENDIF.

Usage
It’s used to create conditional branches in a Bitcoin Script. This is particularly useful for implementing complex spending conditions, like multisig setups, time locks, or optional clauses.

**OP_NOTIF**

Opcode number: 100

Byte representation: 0x64

Short description: Pop and execute the next statements if a zero element was popped. (If the top stack value is False, the statements are executed. The top stack value is removed.)

OP_NOTIF enables conditional logic where the code block is executed only if the stack's top item evaluates to false (0). If the item is true (non-zero), the script skips to the matching OP_ELSE (if present) or OP_ENDIF.

Usage
You’d use OP_NOTIF when you want to handle conditions based on something not being true.

Both OP_IF and OP_NOTIF consume the top item of the stack (removing it).
They help create more nuanced smart contract scripts for spending conditions.

**OP_ELSE**

Opcode number: 103

Byte representation: 0x67

Short description: Execute following script if the previous OP_IF or OP_NOTIF condition was not met. (If the preceding OP_IF or OP_NOTIF or OP_ELSE was not executed then these statements are and if the preceding OP_IF or OP_NOTIF or OP_ELSE was executed then these statements are not.)

OP_ELSE in Bitcoin Script is part of the conditional logic flow, and it acts as the "else" branch in an OP_IF or OP_NOTIF block. It's used to define what happens if the condition evaluated by OP_IF (or OP_NOTIF) is not satisfied.

Purpose
OP_ELSE separates the "if true" code from the "if false" code within a conditional structure.

A common example is a two-factor authentication script where:

A user can either sign a transaction immediately with a standard key (if true), or
They must wait for a timelock to expire and then provide a different key (if false).

**OP_ENDIF**

Opcode number: 104

Byte representation: 0x68

Short description: Ends a conditional block. (Ends an if/else block. All blocks must end, or the transaction is invalid. An OP_ENDIF without OP_IF earlier is also invalid.)

OP_ENDIF is used to conclude conditional structures in Bitcoin scripting initiated by OP_IF or OP_NOTIF. It denotes the end of the conditional execution paths and allows the script to continue with any subsequent commands outside of the conditional block.

OP_ENDIF marks the end of a conditional block started by OP_IF or OP_NOTIF. It's essentially a closing tag for the conditional logic. Once the script execution reaches OP_ENDIF, it resumes processing the rest of the script after the conditional block.

It signals the conclusion of the "if-else" logic so the script can move forward. Without OP_ENDIF, the script wouldn't know where the conditional block ends.

*What Happens Without OP_ENDIF?*

If you omit OP_ENDIF, the script will fail to process correctly because it won't know where the conditional block ends. This would result in an invalid or incomplete script.

Key Takeaways
OP_ENDIF is mandatory to close any OP_IF or OP_NOTIF block.
It does not evaluate anything itself; it simply acts as a structural marker.

**OP_VERIFY**

Opcode number: 105

Byte representation: 0x69

Short description: Checks the top stack value. If it's 0 or an empty string, the script fails; otherwise, it continues and the value is popped. (Marks transaction as invalid if top stack value is not true. The top stack value is removed.)

OP_VERIFY is an opcode that allows for quick validation of conditions without explicitly ending the script. It's used to ensure certain requirements are met.

OP_VERIFY is an important opcode in Bitcoin Script that checks the top item on the stack to ensure it is true (non-zero). If the value is false (zero), the script execution fails immediately, causing the transaction to be invalid.

*Purpose*

OP_VERIFY is typically used to enforce conditions in scripts. It ensures that certain checks pass before allowing the script to continue.

*Without OP_VERIFY*:

If OP_VERIFY isn’t used, the script would still evaluate the stack's state but wouldn’t enforce an immediate failure on a false condition. This could lead to unintended script execution unless explicitly checked later.

*Key Use Cases*

Ensuring Signature Validity: After using OP_CHECKSIG or OP_CHECKMULTISIG, OP_VERIFY enforces that the verification succeeded.
Custom Conditions: When implementing custom spending conditions, OP_VERIFY can enforce that a specific condition is satisfied before proceeding.

**OP_RETURN**

Opcode number: 106

Byte representation: 0x6a

OP_RETURN is an opcode in bitcoin's scripting system that allows for the inclusion of a small amount of arbitrary data in a transaction. This opcode immediately marks the transaction output as unspendable, ensuring that the output can't be used as an input in a subsequent transaction. It's primarily used to embed arbitrary data in the blockchain.


(Marks transaction as invalid. Since bitcoin 0.9, a standard way of attaching extra data to transactions is to add a zero-value output with a scriptPubKey consisting of OP_RETURN followed by data. Such outputs are provably unspendable and specially discarded from storage in the UTXO set, reducing their cost to the network. Since 0.12, standard relay rules allow a single output with OP_RETURN, that contains any sequence of push statements (or OP_RESERVED[1]) after the OP_RETURN provided the total scriptPubKey length is at most 83 bytes.)

OP_RETURN is a special opcode in Bitcoin Script that marks a transaction output as unspendable. It is commonly used to embed arbitrary data into the blockchain.

*Purpose*

The primary purposes of OP_RETURN are:

To store data in the Bitcoin blockchain.

To prevent anyone from spending the associated output, effectively making it unspendable.

To serve as a cost-effective method for attaching metadata to transactions.

*Key Features*

Non-spendable Output: Any transaction output containing OP_RETURN is invalid for spending, meaning the associated funds are effectively "burned."
Data Storage: The Bitcoin network allows a limited amount of arbitrary data to be included in OP_RETURN outputs (typically up to 80 bytes, depending on the implementation).

***Constants***: With this category of opcodes, you can push a specific amount of data to the stack. An example is OP_1NEGATE, which executes a command to push the number -1 onto the stack. 

When talking about scripts, these value-pushing words are usually omitted.

**OP_0, OP_FALSE** 

Opcode number: 0

Byte representation: 0x00

Other names: OP_FALSE, OP_PUSHBYTES_0Short 

Description: Push an empty byte array onto the stack. (This is not a no-op: an item is added to the stack.)

The OP_0 opcode, which corresponds to the byte 0x00, doesn't push the numeric value 0 onto the stack; rather, it pushes a zero-length byte array.

**N/A**

The next opcode bytes is data to be pushed onto the stack

**OP_PUSHDATA1**

Opcode number: 1

Byte representation: 0x01

Push the next byte onto the stack

(For the bytes 0x01 to 0x10 it is more efficient (and required by standardness rules) to use opcodes OP_1 to OP_16, and for the byte 0x81 to use OP_1NEGATE)


**OP_PUSHDATA2**

Opcode number: 2

Byte representation: 0x02

The next two bytes contain the number of bytes to be pushed onto the stack in little endian order. (Push the next 2 bytes onto the stack, from OP_PUSHBYTES_1 to OP_PUSHBYTES_75.)

**OP_PUSHDATA4**

Opcode number: 4

Byte representation: 0x04

The next four bytes contain the number of bytes to be pushed onto the stack in little endian order. (Push the next 4 bytes onto the stack,  from OP_PUSHBYTES_1 to OP_PUSHBYTES_75.)

**OP_1NEGATE**

Opcode number: 79

Byte representation: 0x4f

Other names: OP_PUSHNUM_NEG1

The number -1 is pushed onto the stack.

The OP_1NEGATE opcode will push 0x81 (representing -1 in the context of script execution) onto the stack. This opcode utilizes the minimally encoded integers format.

**OP_1, OP_TRUE**

Opcode number: 81

Byte representation: 0x51

Other names: OP_TRUE, OP_PUSHNUM_1

The number 1 is pushed onto the stack.

The OP_1 opcode, which corresponds to the byte 0x51, pushes the number 1 onto the stack. OP_1` is a fundamental opcode in Bitcoin Script, enabling a variety of operations and serving as a building block for more complex scripts.

**OP_2-OP_16**

The number in the word name (2-16) is pushed onto the stack.

***Stack***: Users deploy this opcode type to move items on the stack as they wish. An example is OP_2DROP, which removes the top two stack items.  

**OP_TOALTSTACK**

Opcode number: 107

Byte representation: 0x6b

Short description: Move the top item from the main stack and pushes it onto the alternate stack.

This operation is useful for temporarily storing values when you need to manipulate the main stack but still want to access those values later. The counterpart to OP_TOALTSTACK is OP_FROMALTSTACK, which retrieves the top element from the alt stack and pushes it back onto the main stack.

**OP_FROMALTSTACK**	

Opcode number: 108

Byte representation: 0x6c

Short description: Moves the top item from the alternate stack and pushes it onto the main stack.

**OP_IFDUP**

Opcode number: 115

Byte representation: 0x73

Short description: duplicates the top item on the stack if and only if it is non-zero. If the top item is zero, the stack remains unchanged.

This opcode is useful in conditional operations, where duplication occurs based on the value of the top stack item.

**OP_DEPTH**

Opcode number: 116

Byte representation: 0x74

Short description: is used to determine the number of items on the stack and push that count onto the stack as a new item.

This opcode is useful when you need to know the size of the stack, for example, before performing operations that require a certain number of stack items.
The value pushed by OP_DEPTH does not affect the other items on the stack.

**OP_DROP**

Opcode number: 117

Byte representation: 0x75

Short description: is used to remove the top item from the stack, effectively discarding it. This opcode is useful when you no longer need the top item and want to proceed with other operations on the remaining stack items.

OP_DROP is often used to clean up intermediate values that are no longer needed in a script.
If the stack is empty when OP_DROP is executed, the script will fail.

**OP_DUP**

Opcode number: 118

Byte representation: 0x76

Short description: Duplicate the top item on the stack.

Used to duplicate the top item on the stack, pushing a copy of it onto the stack. This opcode is frequently used in Bitcoin scripts to create copies of data, especially for validation purposes like signature checking.

OP_DUP is commonly used in scripts like Pay-to-PubKeyHash (P2PKH) to duplicate the public key for signature verification.
If the stack is empty when OP_DUP is executed, the script will fail.

**OP_NIP**

Opcode number: 119

Byte representation: 0x77

Short description: Remove the second item from the top of the stack.

Used to remove the second item from the top of the stack, while leaving the top item and the rest of the stack intact. This opcode is useful when you need to discard an intermediate value but keep the top item for further operations.

OP_NIP allows you to efficiently discard the second stack item without disturbing the top of the stack.
If there are fewer than two items on the stack when OP_NIP is executed, the script will fail.

**OP_OVER**

Opcode number: 120

Byte representation: 0x78

Short description: Duplicates the second item from the top of the stack.

Used to duplicate the second item from the stack (i.e., the value one over from the top)

This opcode is part of a family of opcodes (OP_OVER, OP_2OVER, OP_DUP, and a few others) designed for duplication of stack items.
If there are fewer than two items on the stack when OP_OVER is executed, the script will fail.

**OP_PICK**

Opcode number: 121

Byte representation: 0x79

Short description: Copy an item from the stack at a specified depth and push it to the top.

Used to select a stack item and copy it to the top.

If there are fewer than two items on the stack, if n is negative, or if n is larger than the stack when OP_PICK is executed, the script will fail.
The stack item just before OP_PICK dictates 'n', the location of the item to be copied.

Counting begins at 0, not 1; so an n value of 2 would reach the third stack item (0 is first, 1 is second, 2 is third, and so on).

**OP_ROLL**

Opcode number: 122

Byte representation: 0x7a

Short description: Move the stack item at position n to the top of the stack.

Used to select a stack item and move it to the top.

If there are fewer than two items on the stack, if n is negative, or if n is larger than the stack when OP_ROLL is executed, the script will fail.
The stack item just before OP_ROLL dictates 'n', the location of the item to be moved.

Counting begins at 0, not 1; so an n value of 2 would reach the third stack item (0 is first, 1 is second, 2 is third, and so on).

**OP_ROT**

Opcode number: 123

Byte representation: 0x7b

Short description: Rotate the top three stack items.

Used to pull the third item from the top of the stack and move it to the top, while shifting the other two items down. This operation essentially rotates the top three stack items.

OP_ROT is useful when you need to rearrange the top three items of the stack.
If there are fewer than three items on the stack when OP_ROT is executed, the script will fail.

**OP_SWAP**

Opcode number: 124

Byte representation: 0x7c

Short description: Swap the top two stack items.

Used to swap the positions of the top two items on the stack. This operation is commonly used when you need to reorder the top items without affecting the rest of the stack.

OP_SWAP only affects the top two items on the stack and leaves the rest of the stack unchanged.
If there are fewer than two items on the stack when OP_SWAP is executed, the script will fail.

**OP_TUCK**

Opcode number: 125

Byte representation: 0x7d

Short description: Copy the top item and insert it below the second item.

Used to duplicate the top item on the stack and insert the duplicate below the second item. This effectively "tucks" the top item into the third position while leaving a copy of it on the top.

OP_TUCK is useful when you need to use the top stack item twice, both at the top and immediately below the second item.
If there are fewer than two items on the stack when OP_TUCK is executed, the script will fail.

**OP_2DROP**

Opcode number: 109

Byte representation: 0x6d

Short description: Drop the top two items from the stack.

Used to discard the top two items from the stack.

Discarding Temporary Data: In scripts where temporary values are pushed onto the stack for interim calculations, OP_2DROP can be used to remove them once they are no longer needed.

This opcode is part of a family of opcodes (OP_DROP, OP_2DROP, OP_2DUP, OP_3DUP, and a few others) designed for stack item management.

**OP_2DUP**

Opcode number: 110

Byte representation: 0x6e

Short description: Duplicates the top two stack items.

Duplicates the top two items on the stack, pushing two additional copies of these items onto the stack. This can be useful for operations where the same values are needed multiple times without removing the original values.

When OP_2DUP is executed, it takes the top two items from the stack, duplicates them, and pushes the duplicates back onto the stack in the same order. This means the stack will grow by two items, and the original items will remain in their places.

If there are fewer than two items on the stack when OP_2DUP is executed, the script will fail.

**OP_3DUP**

Opcode number: 111

Byte representation: 0x6f

Short description: Duplicates the top three stack items.

Duplicates the top three items on the stack, pushing three additional copies of these items onto the stack. This can be useful for operations where the same values are needed multiple times without removing the original values.

When OP_3DUP is executed, it takes the top three items from the stack, duplicates them, and pushes the duplicates back onto the stack in the same order. This means the stack will grow by three items, and the original items will remain in their places.

If there are fewer than three items on the stack when OP_3DUP is executed, the script will fail.

**OP_2OVER**

Opcode number: 112

Byte representation: 0x70

Short description: Duplicates the third and fourth items from the top of the stack.

Used to duplicate the third and fourth items from the stack (i.e., the values two over from the top).

This opcode is part of a family of opcodes (OP_OVER, OP_2OVER, OP_DUP, and a few others) designed for duplication of stack items.
If there are fewer than four items on the stack when OP_2OVER is executed, the script will fail.

**OP_2ROT**

Opcode number: 113

Byte representation: 0x71

Short description: Rotates the fifth and sixth items from the top of the stack to the top.

Used to bring the fifth and sixth stack items to the top of the stack, leaving the other items in place.

This opcode is part of a family of rotation opcodes designed for stack reordering.
If there are fewer than six items on the stack when OP_2ROT is executed, the script will fail.

**OP_2SWAP**

Opcode number: 114

Byte representation: 0x72

Short description: Swap the top two pairs of stack items.

Used to swap the top two pairs of items on the stack. The first and second stack items are swapped with the third and fourth items.

This opcode works with pairs of stack items. If there are fewer than four items on the stack when OP_2SWAP is executed, the script will fail.
OP_SWAP is a related opcode for swapping just the top two items.


***Splice***: If any opcode marked as disabled is present in a script, it must abort and fail.

**OP_CAT**

Opcode number: 126

Byte representation: 0x7e

Concatenates two strings. *disabled*.

Because OP_CAT is disabled, any script that contains it will cause the transaction to be invalid regardless of context. This opcode was originally intended to concatenate two strings but due to concerns about potential vulnerabilities, it was disabled early in bitcoin's history.

OP_CAT is a defunct opcode – short for operation code – that was part of Bitcoin’s original scripting system. This bit of code was used to concatenate (aka combine) multiple data sets from a stack, which together could create complex instructions. Think of an individual opcode as one line of instructions; when joined together, they could create more complicated rules for how bitcoin could be spent.

OP_CAT was removed by Bitcoin creator Satoshi Nakamoto all the way back in 2010, but recently, it has been back in the limelight, spurring debates about whether or not it should be revived. This is in large part due to Taproot Wizards, the company behind a new series of Bitcoin recursive inscriptions known as the Quantum Cats collection.

*Why Do Some Want OP_CAT Back?*

Potential use cases are at the heart of the argument. Adherents believe that OP_CAT would create more opportunities for scaling up, as well as for enhancing security. They point to the idea that it can enable covenants, which would provide added utility in the Bitcoin space and alter the dynamics of scripting. They also say it would create stronger protections, such as vaults, for users to rely on. 

According to its supporters, OP_CAT could enable the creation of a unique hash, which zero-knowledge rollups on L1 could use. It would also allow for other functionalities, including bridging assets. Taken as a whole, the premise of the pro-OP_CAT argument seems to be that it will expand opportunities for builders on the Bitcoin network.

But it’s not without its detractors. Opponents point to the uncertainty that surrounds OP_CAT, highlighting that we don’t know all the risks that come along with re-enabling this code and that it disappeared for a reason.

*So, Why Was OP_CAT Abandoned?*

OP_CAT was among the earliest opcodes to be disabled. While the concept may sound simple on its face, it carried significant risks to the platform when first written. At the time, it was possible to combine OP_CAT with other opcodes, building huge transactions that the original protocol’s nodes would be unable to handle. Today, a maximum Bitcoin Script stack element size exists, lessening that risk.

But in its infancy, Bitcoin also had far fewer of the safeguards that are in place today, and there were not many options for how to counter this problem. Satoshi also had concerns that the then-young network could be vulnerable to security failings, attacks and breaches. Ultimately, the threat that bad actors could use OP_CAT (particularly the risk of them generating denial-of-service attacks) was among the potential dangers that led to its disabling.

**OP_SUBSTR**

Opcode number: 127

Byte representation: 0x7f

Returns a section of a string. *disabled*.

In the original design of Bitcoin's scripting language, OP_SUBSTR was intended to extract a substring from a string. It would pop three items from the stack: the original string, a start position, and a length. It would then push the substring (starting at the given position and with the specified length) back onto the stack.

However, concerns about potential vulnerabilities and the complexity it would introduce to the scripting system led to its deactivation.

**OP_LEFT**

Opcode number: 128

Byte representation: 0x80

Keeps only characters left of the specified point in a string. *disabled*.

Originally, the OP_LEFT opcode was intended to keep only the leftmost N bytes of a string. The operation would pop two items from the stack: the original string and a byte count. It would then push back onto the stack the leftmost bytes of the string, as specified by the byte count.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_LEFT (along with several other string manipulation opcodes) was disabled early in bitcoin's development.

**OP_RIGHT**

Opcode number: 129

Byte representation: 0x81

Keeps only characters right of the specified point in a string. *disabled*.

Initially, the OP_RIGHT opcode was designed to retain only the rightmost N bytes of a string. During its operation, it would pop two items from the stack: the original string and a byte count. Subsequently, it would push back onto the stack the rightmost bytes of the string, determined by the byte count.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_RIGHT (along with several other string manipulation opcodes) was disabled early in bitcoin's development.

**OP_SIZE**

Opcode number: 130

Byte representation: 0x82

Pushes the length of the top stack item in bytes onto the stack.

The stack item that was previously the top stack item is unaffected and simply becomes the second item on the stack following the output from OP_SIZE
If the stack is empty the script fails.


***Bitwise logic***: This group of opcodes comes in handy when you need a command that activates based on specified input data. An example is OP_INVERT, which flips all of the bits in an input.

If any opcode marked as *disabled* is present in a script, it must abort and fail.

**OP_INVERT**

Opcode number: 131

Byte representation: 0x83

Flips all of the bits in the input. *disabled*.

Originally, the OP_INVERT opcode was intended to invert all the bits of the top item on the stack. This bitwise operation would flip every 1 to 0 and every 0 to 1 in the binary representation of the number.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_INVERT (along with several other opcodes) was disabled early in bitcoin's development.

**OP_AND**

Opcode number: 132

Byte representation: 0x84

Boolean *and* between each bit in the inputs. *disabled*.

Initially, the OP_AND opcode was designed to perform a bitwise AND operation on the top two items on the stack. This means it would take two numbers and return a new number, where each bit in the result is the logical AND of the corresponding bits in the input numbers.

However, as part of a broader effort to reduce potential vulnerabilities and to simplify bitcoin's scripting language, OP_AND was disabled early in bitcoin's history along with several other opcodes.

**OP_OR**

Opcode number: 133

Byte representation: 0x85

Boolean *or* between each bit in the inputs. *disabled*.

Originally, OP_OR was intended to perform a bitwise OR operation on the top two items on the stack. This operation would take two numbers and produce a new number. In this result, each bit is the logical OR of the corresponding bits in the input numbers.

However, as part of a broader effort to reduce potential vulnerabilities and to simplify bitcoin's scripting language, OP_OR was disabled early in bitcoin's history along with several other opcodes.

**OP_XOR**

Opcode number: 134

Byte representation: 0x86

Boolean *exclusive* or between each bit in the inputs. *disabled*.

Originally designed for Bitcoin's script, the OP_XOR opcode was intended to carry out a bitwise XOR (exclusive or) operation on the top two items on the stack. This operation would take two numbers and produce a new number wherein each bit is the result of the logical XOR between the corresponding bits in the input numbers.

However, as part of a broader effort to reduce potential vulnerabilities and to simplify bitcoin's scripting language, OP_XOR was disabled early in bitcoin's history along with several other opcodes.

**OP_EQUAL**

Opcode number: 135

Byte representation: 0x87

Returns 1 if the inputs are exactly equal, 0 otherwise.

Short description: Compare the top two items on the stack and push 1 if they are equal, 0 otherwise.

OP_EQUAL is used to compare the top two items on the stack. If they are equal, it pushes 1 (true) onto the stack; if they are not equal, it pushes 0 (false). Both items being compared are removed from the stack.

OP_EQUAL is commonly used in scripts that require equality checks, such as verifying if two hash values or public keys match.
Both items being compared are consumed (removed) from the stack.
If there are fewer than two items on the stack when OP_EQUAL is executed, the script will fail.

**OP_EQUALVERIFY**

Opcode number: 136

Byte representation: 0x88

Short description: Compare the top two items on the stack and halts the script if they are not equal.

OP_EQUALVERIFY combines the functionality of OP_EQUAL and OP_VERIFY. It compares the top two items on the stack and removes them. If they are equal, the script continues execution. If they are not equal, the script fails immediately. This opcode is commonly used in scripts to ensure that two values match without leaving a true or false result on the stack.

OP_EQUALVERIFY is frequently used in Pay-to-PubKeyHash (P2PKH) scripts, where it ensures the provided public key hash matches the expected hash.
Unlike OP_EQUAL, OP_EQUALVERIFY does not leave a result (true or false) on the stack. Instead, it either allows the script to continue or fails immediately. 

***Arithmetic***: You can execute mathematical operations using the group of opcodes. An example is OP_MUL, which performs a multiplication operation. 

Note: Arithmetic inputs are limited to signed 32-bit integers, but may overflow their output.

If any input value for any of these commands is longer than 4 bytes, the script must abort and fail. If any opcode marked as disabled is present in a script - it must also abort and fail.

**OP_1ADD**

Opcode number: 139

Byte representation: 0x8b

Short description: Add 1 to the top item on the stack.

OP_1ADD increments the top item on the stack by 1. This operation is used in Bitcoin Script when simple arithmetic is needed, often for counting or adjusting values during script execution.

Arithmetic inputs are limited to signed 32-bit integers, but may overflow their output.
If the input value for OP_1ADD is longer than 4 bytes, the script will fail.
If the stack is empty when OP_1ADD is executed, the script will fail.

**OP_1SUB**

Opcode number: 140

Byte representation: 0x8c

Short description: Decrement the top stack element in place.
decrements the top item on the stack by 1. This opcode is used in bitcoin Script to perform basic arithmetic, such as reducing a counter or adjusting a value in more complex scripts.

OP_1SUB only works with integer values (4 bytes). If the top item cannot be interpreted as an integer, the script will fail.
If the stack is empty when OP_1SUB is executed, the script will fail.


**OP_2MUL**

Opcode number: 141

Byte representation: 0x8d

The input is multiplied by 2. *disabled*.

OP_2MUL was originally intended for multiplication operations, specifically to multiply the top item on the stack by 2.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_2MUL (along with several other opcodes) was disabled early in bitcoin's development.

**OP_2DIV**

Opcode number: 142

Byte representation: 0x8e

The input is divided by 2. *disabled*.

OP_2DIV was initially designed to perform division operations by dividing the top item on the stack by 2.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_2DIV (along with several other opcodes) was disabled early in bitcoin's development.

**OP_NEGATE**

Opcode number: 143

Byte representation: 0x8f

Short description: Multiply the top stack item by -1 in place. (The sign of the input is flipped.)

Changes the sign of the top item on the stack. If the item is positive, it becomes negative; if it is negative, it becomes positive.

OP_NEGATE works only on items that can be interpreted as integers, which in Bitcoin Script means byte arrays up to 4 bytes in length.
If the top item is zero, applying OP_NEGATE has no effect (zero remains zero).
If there are no items on the stack when OP_NEGATE is executed, the script will fail.

**OP_ABS**

Opcode number: 144

Byte representation: 0x90

Short description: Converts the top item on the stack to its absolute value. (The input is made positive.)

Changes the top item on the stack to its absolute value, effectively removing any negative sign if present. This operation is useful when only the magnitude of a number is needed, regardless of its original sign.

OP_ABS works only on items that can be interpreted as integers, which in Bitcoin Script means byte arrays up to 4 bytes in length.
If the top item is already positive or zero, applying OP_ABS has no effect.
If the stack is empty when OP_ABS is executed, the script will fail.

**OP_NOT**

Opcode number: 145

Byte representation: 0x91

Short description: Pop the top item and push 1 if it is zero; otherwise, push 0. (If the input is 0 or 1, it is flipped. Otherwise the output will be 0.)

Pops the top item on the stack and checks if it is zero. If it is, OP_NOT pushes 1 (true) onto the stack. If the item is non-zero, it pushes an empty array (false). This operation is often used in conditional scripts to invert the truthiness of a value.

In Bitcoin Script, an empty array represents false, while 1 represents true.
If the stack is empty when OP_NOT is executed, the script will fail.

**OP_0NOTEQUAL**

Opcode number: 146

Byte representation: 0x92

Short description: Pop the top item and push 1 if the top item is not zero; otherwise, push an empty array. (Returns 0 if the input is 0. 1 otherwise.)

OP_0NOTEQUAL pops the top item and checks whether it is not zero. If the item is non-zero, it pushes 1 (true) onto the stack. If the item is zero (or an empty array), it pushes an empty array (false).

**OP_ADD**

Opcode number: 147

Byte representation: 0x93

Short Description: Pop two stack items and push their sum. (a is added to b.)

OP_ADD adds two numbers together and returns their sum on the stack.

**OP_SUB**

Opcode number: 148

Byte representation: 0x94

Short description: Pop two stack items and push the second minus the top.(b is subtracted from a.)

OP_SUB performs subtraction on the top two items on the stack. It subtracts the second item (just below the top item) from the top item and pushes the result back onto the stack. This operation is useful for basic arithmetic calculations within a bitcoin script.

OP_SUB requires the top two items on the stack to be interpretable as integers (byte arrays up to 4 bytes).
If there are fewer than two items on the stack, the script will fail.
The result of b - a is pushed back onto the stack as the new top item.

**OP_MUL**

Opcode number: 149

Byte representation: 0x95

a is multiplied by b. *disabled*.

OP_MUL was intended to perform multiplication operations between the two topmost items on the stack.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_MUL (along with several other opcodes) was disabled early in bitcoin's development.

**OP_DIV**

Opcode number: 150

Byte representation: 0x96

a is divided by b. *disabled*.

OP_DIV was initially intended for division operations, specifically to divide the second-to-top stack item by the top stack item.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_DIV (along with several other opcodes) was disabled early in bitcoin's development.

**OP_MOD**

Opcode number: 151

Byte representation: 0x97

Returns the remainder after dividing a by b. *disabled*.

OP_MOD was designed to perform a modulus operation, which would find the remainder after dividing the second-to-top stack item by the top stack item.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_MOD (along with several other opcodes) was disabled early in bitcoin's development.

**OP_LSHIFT**

Opcode number: 152

Byte representation: 0x98

Shifts a left b bits, preserving sign. *disabled*.

OP_LSHIFT was intended for bitwise left shift operations, which would shift the bits of the top stack item to the left by a number of positions specified by the second-to-top stack item.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_LSHIFT (along with several other opcodes) was disabled early in bitcoin's development.

**OP_RSHIFT**

Opcode number: 153

Byte representation: 0x99

Shifts a right b bits, preserving sign. *disabled*.

OP_RSHIFT was designed to perform bitwise right shift operations. This operation would shift the bits of the top stack item to the right by the number of positions specified by the second-to-top stack item.

Due to concerns about potential vulnerabilities and the desire to simplify the scripting language, OP_RSHIFT (along with several other opcodes) was disabled early in bitcoin's development.

**OP_BOOLAND**

Opcode number: 154

Byte representation: 0x9a

Short description: Pop the top two stack items and push 1 if both are nonzero, else push 0. (If both a and b are not 0, the output is 1. Otherwise 0.)

OP_BOOLAND performs a logical AND operation on the top two items on the stack. If both items are non-zero, it pushes 1 (true) onto the stack. If either item is zero (or an empty array), it pushes an empty array (false). Both items are interpreted as integers, and must therefore be 4 bytes long or less. If either is above 4 bytes in length, the script is invalid.

If there are fewer than two items on the stack when OP_BOOLAND is executed, the script will fail.

**OP_BOOLOR**

Opcode number: 155

Byte representation: 0x9b

Short description: Pop the top two stack items and push 1 if either is nonzero, else push 0. (If a or b is not 0, the output is 1. Otherwise 0.)

OP_BOOLOR performs a logical OR operation on the top two items on the stack. If either item is non-zero, it pushes 1 (true) onto the stack. If both items are zero (or empty arrays), it pushes an empty array (false). Both items are interpreted as integers, and must therefore be 4 bytes long or less. If either is above 4 bytes in length, the script is invalid.

If there are fewer than two items on the stack when OP_BOOLOR is executed, the script will fail.

**OP_NUMEQUAL**

Opcode number: 156

Byte representation: 0x9c

Short description: Pop the top two stack items and push 1 if both are numerically equal, else push 0. (Returns 1 if the numbers are equal, 0 otherwise.)

OP_NUMEQUAL compares the top two items on the stack as integers. If they are numerically equal, it pushes 1 (true) onto the stack. If they are not equal, it pushes an empty array (false). Both items are removed from the stack after the comparison.

**OP_NUMEQUALVERIFY**

Opcode number: 157

Byte representation: 0x9d

Short description: Pop the top two stack items and check are numerically equal; fail the script if they are not. (Same as OP_NUMEQUAL, but runs OP_VERIFY afterward.)

OP_NUMEQUALVERIFY combines the functionality of OP_NUMEQUAL and an implicit verification step. It compares the top two items on the stack as integers. If they are numerically equal, both items are removed, and the script continues execution. If they are not equal, the script fails immediately.

Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as integers.
Unlike OP_NUMEQUAL, this opcode does not push a result onto the stack; it either succeeds (continue execution) or fails.
If there are fewer than two items on the stack, the script will fail.

**OP_NUMNOTEQUAL**

Opcode number: 158

Byte representation: 0x9e

Short description: Pop the top two stack items and push 0 if both are numerically equal, else push 1. (Returns 1 if the numbers are not equal, 0 otherwise.)

OP_NUMNOTEQUAL compares the top two items on the stack as integers. If they are not numerically equal, it pushes 1 (true) onto the stack. If they are equal, it pushes an empty array (false). Both items are removed from the stack after the comparison.

Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as signed integers.
An empty array ([]) is treated as 0 when compared.
If there are fewer than two items on the stack when OP_NUMNOTEQUAL is executed, the script will fail.

**OP_LESSTHAN**

Opcode number: 159

Byte representation: 0x9f

Short description: Pop the top two items; push 1 if the second is less than the top, 0 otherwise. (Returns 1 if a is less than b, 0 otherwise.)

OP_LESSTHAN compares the top two items on the stack as integers. If the second item is less than the top item, it pushes 1 (true) onto the stack. If not, it pushes an empty array (false). Both items are removed from the stack after the comparison.

Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as integers.
An empty array ([]) is treated as 0 when compared.
If there are fewer than two items on the stack when OP_LESSTHAN is executed, the script will fail.

**OP_GREATERTHAN**

Opcode number: 160

Byte representation: 0xa0

Short description: Pop the top two items; push 1 if the second is greater than the top, 0 otherwise. (Returns 1 if a is greater than b, 0 otherwise.)

OP_GREATERTHAN compares the top two items on the stack as integers. If the second item is greater than the top item, it pushes 1 (true) onto the stack. If not, it pushes an empty array (false). Both items are removed from the stack after the comparison.

Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as integers.
An empty array ([]) is treated as 0 when compared.
If there are fewer than two items on the stack when OP_GREATERTHAN is executed, the script will fail.

**OP_LESSTHANOREQUAL**

Opcode number: 161

Byte representation: 0xa1

Short description: Pop the top two items; push 1 if the second is less than or equal to the top, 0 otherwise. (Returns 1 if a is less than or equal to b, 0 otherwise.)

OP_LESSTHANOREQUAL compares the top two items on the stack as integers. If the second item is less than or equal to the top item, it pushes 1 (true) onto the stack. If not, it pushes an empty array (false). Both items are removed from the stack after the comparison.

Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as integers.
An empty array ([]) is treated as 0 when compared.
If there are fewer than two items on the stack when OP_GREATERTHAN is executed, the script will fail.

**OP_GREATERTHANOREQUAL**

Opcode number: 162

Byte representation: 0xa2

Short description: Pop the top two items; push 1 if the second is greater than or equal to the top, 0 otherwise. (Returns 1 if a is greater than or equal to b, 0 otherwise.)

OP_GREATERTHANOREQUAL compares the top two items on the stack as integers. If the second item is greater than or equal to the top item, it pushes 1 (true) onto the stack. If not, it pushes an empty array (false). Both items are removed from the stack after the comparison.

Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as integers.
An empty array ([]) is treated as 0 when compared.
If there are fewer than two items on the stack when OP_GREATERTHAN is executed, the script will fail.

**OP_MIN**

Opcode number: 163

Byte representation: 0xa3

Short description: Pop the top two items; push the smaller of the two onto the stack. (Returns the smaller of a and b.)

OP_MIN compares the top two items on the stack as integers and pushes the smaller value back onto the stack. Both original items are removed, and the smaller value becomes the new top item.

Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as integers.
An empty array ([]) is treated as 0 when compared.
If there are fewer than two items on the stack when OP_MIN is executed, the script will fail.

**OP_MAX**

Opcode number: 164

Byte representation: 0xa4

Short description: Pop the top two items; push the larger of the two onto the stack. (Returns the larger of a and b.)

OP_MAX compares the top two items on the stack as integers and pushes the larger value back onto the stack. Both original items are removed, and the larger value becomes the new top item.

Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as integers.
An empty array ([]) is treated as 0 when compared.
If there are fewer than two items on the stack when OP_MAX is executed, the script will fail.

**OP_WITHIN**

Opcode number: 165

Byte representation: 0xa5

Short description: Pop the top three items; if the first item is within the range specified by the second and third stack items, push 1, otherwise, push an empty array. (Returns 1 if x is within the specified range (left-inclusive), 0 otherwise.)

OP_WITHIN checks if the top item on the stack is within a specified range. Specifically, it evaluates whether the first item is greater than or equal to the second item and less than the third item (min <= x < max). If true, it pushes 1 (true) onto the stack; otherwise, it pushes an empty array (false).

The range is inclusive of the lower bound (min <= x) and exclusive of the upper bound (x < max).
Both items must be valid integers. Bitcoin Script interprets byte arrays up to 4 bytes as integers.
An empty array ([]) is treated as 0 when compared.
If there are fewer than two items on the stack when OP_GREATERTHAN is executed, the script will fail.


**Conclusion**

Bitcoin opcodes shape the network’s functionality and provide avenues for the ecosystem’s evolution. Opcodes’ versatility presents a pathway towards improving the Bitcoin network’s adaptability and encouraging innovation, thus playing an essential role in the future of Bitcoin. 



*Sources*: 

https://unchainedcrypto.com/opcodes-in-bitcoin/

https://trustmachines.co/blog/the-history-of-op-cat-and-the-evolution-of-the-bitcoin-network/#:~:text=So%2C%20Why%20Was%20OP_CAT%20Abandoned,that%20led%20to%20its%20disabling.

https://opcodeexplained.com/opcodes/

https://en.bitcoin.it/wiki/Script#Opcodes



**Terminology:**

**Byte**: a group of binary digits or bits (usually eight) operated on as a unit. A unit of memory size. The byte was the number of bits used to encode a single character of text in a computer of text in a computer and for this reason it is the smallest addressable unit of memory in many computer architectures. 

**Endian order**: is the order in which bytes are stored in a computer's memory. It's also known as byte order.

**Big endian**- the most significant byte is stored first, at the lowest memory address- used by network protocals and architectures. 

**Little endian**- the least significant byte is stored first, at the lowest memory address- used by architectures like x86 and ARM

Bitcoin script reads numbers in *little endian format*. For example, when using OP_PUSHDATA2 and providing 2 following bytes that must be interpreted as an integer for the number of following bytes to push on the stack, the number 400 would be encoded as 9001 (400 in hexadecimal is 0190, which reversed in little endian becomes 9001).

**Minimally encoded integers format**:

Number-related opcodes like OP_2, OP_16, OP_1NEGATE, etc. in Script use *minimally encoded integers*.

The concept of minimally encoded integers is specific to bitcoin's Script system and it's part of an effort to make the system more efficient.

Integers in Bitcoin Script are represented as little-endian byte arrays (least significant byte first).

An empty byte array is considered to represent the number 0.

Otherwise, the most significant byte of an integer should be between 0x01 and 0x80 to represent positive numbers, and between 0x81 and 0x8000 to represent negative numbers. If the most significant byte equals to 0x80 or 0x8000, one more byte is added.

If the most significant byte is greater than 0x50, to prevent it being interpreted as a negative number (Bitcoin Script uses a format known as "sign-magnitude"), an extra 0x00 is added to the end of the array. This represents a positive number. The analogous applies for negative numbers.

The least number of bytes possible is used to represent a number. This is the "minimal" part of "minimally-encoded": if a number can be represented using fewer bytes, it must be.

Here are some examples:

1. The number 0 is represented as an empty byte array.

2. The number 1 is represented as 0x01.

3. The number -1 is represented as 0x81.

4. The number 127 is represented as 0x7f00.
The 0x00 is added because 0x7f is greater than 0x50, and without the 0x00, it could be interpreted as a negative number.

5. The number -127 is represented as 0xff00. The 0x00 is added because 0xff is greater than 0x80, and without the 0x00, it could be interpreted as a positive number.

The main idea here is to save space: by using the fewest number of bytes possible to represent a number, Bitcoin transactions can be smaller, which saves space in blocks and reduces fees for users. It also avoids the ambiguity that can arise when there are multiple valid representations for the same number.



**More**:

**OP_CHECKTEMPLATEVERIFY** (CTV)

CTV (CheckTemplateVerify) is proposed as an opcode, specifically OP_CHECKTEMPLATEVERIFY, in BIP-119. However, it is not currently an active or implemented opcode in Bitcoin. It remains in the proposal stage and has not been included in the Bitcoin protocol.

It remains a proposed upgrade to the Bitcoin protocol under BIP-119, introduced by Jeremy Rubin. While the proposal has been discussed extensively within the Bitcoin community, it has not yet been activated as a soft fork.

*Current Status of CTV*:

Proposal Stage: CTV was formalized in BIP-119, which outlines its functionality, use cases, and benefits.

Community Discussion: The Bitcoin community has debated CTV’s merits, drawbacks, and its potential impact on the Bitcoin ecosystem.

No Activation Yet: As of now, OP_CHECKTEMPLATEVERIFY is not an active opcode, and implementing it would require community consensus and adoption through a soft fork.


is designed to enhance Bitcoin's scripting capabilities by enabling the use of transaction templates. With CTV, Bitcoin users can commit to a specific transaction structure in advance, ensuring that any future transaction built from that template must match the defined parameters. This would allow for more efficient and flexible transaction structures while also improving scalability and programmability.

*What Would CTV Do?*

Enforce Transaction Templates:

CTV allows users to commit to a specific transaction template (like a set of inputs, outputs, amounts, and other parameters). The transaction must then match that template to be valid.
This means that a Bitcoin transaction could be pre-defined, with strict conditions that must be met for the transaction to be executed. Any deviations from the template would result in an invalid transaction.
Improve Efficiency with Batching:

CTV can be used to create templates for batch payments. For example, a business could pre-define a template for sending payments to multiple recipients in a single transaction, making the process more efficient and reducing fees.
Instead of creating a new transaction for each payment, the business could use the template and just fill in the required details for each recipient.
Facilitate Payment Channels:

Payment channels (like Lightning Network) could be enhanced using CTV. With CTV, users could commit to a set of transactions that would only be valid if they match the pre-defined template. This could streamline the process of opening and closing channels or performing other off-chain operations.
Enable Vaults with Time-Locked Conditions:

CTV can be used to create secure Bitcoin vaults. In such vaults, funds are locked under a predefined template that requires certain conditions (e.g., time locks or multiple signatures) to unlock them.
The predefined template ensures that the withdrawal or transfer of funds from the vault must happen according to a set of predetermined rules, making it more secure and predictable.
Enhance Smart Contract Programmability:

By allowing for predefined templates, CTV enables more advanced use cases for Bitcoin smart contracts. For instance, you could create a contract that ensures a certain payment is made only if certain conditions (like a certain number of signatures or a time window) are met.

*Key Benefits of CTV*

Scalability: By reducing the need for unique transaction scripts, CTV can make Bitcoin more scalable. Instead of every transaction needing to be validated from scratch, pre-defined templates would reduce computational overhead.

Transaction Efficiency: Templates allow for batch payments and pre-signed transactions, reducing transaction size and fees.

Flexibility: CTV provides a building block for more complex smart contract functionality on Bitcoin, such as vaults, payment channels, and conditional payments.

*Example: A Vault Scenario*

Imagine you have a Bitcoin vault where funds are locked for a certain period before they can be spent. With CTV, you could define a template for this vault, such that:

The template requires a time lock (say, 30 days).
During those 30 days, no one can spend the funds unless they meet the specific criteria in the template.
After the time lock expires, the funds can be spent under the specified conditions, like by a particular public key or with multiple signatures.
Once the template is set, no one can create a transaction that doesn't match these conditions, making the vault more secure.

*Example: Batch Payments*

Let's say a company needs to send payments to hundreds of employees. Instead of creating a new transaction for each payment, CTV would allow the company to create a template that defines how the payments should be structured (e.g., a certain amount to each recipient).

Later, the company can use the same template for each set of payments, reducing transaction costs and streamlining the process.

*Conclusion*

While CTV is not yet implemented, its potential to improve Bitcoin's transaction model is significant. It could lead to greater efficiency, scalability, and flexibility, especially for use cases like payment channels, vaults, and batch payments.