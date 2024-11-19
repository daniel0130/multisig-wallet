# Bitcoin Multisig Wallet

A secure and flexible Bitcoin wallet that requires multiple signatures from different parties to authorize a transaction. This wallet is designed for situations where you want to increase the security of your Bitcoin holdings or require multiple participants to authorize a transaction.

## Features

- **Multi-Signature Security**: Requires multiple private keys to authorize a transaction. Reduces the risk of losing funds due to a single compromised key.
- **Customizable Thresholds**: Define the number of signatures needed to authorize a transaction (e.g., 2-of-3, 3-of-5, etc.).
- **Easy Integration**: Designed to integrate with Bitcoin infrastructure and supports a variety of use cases.
- **Full Bitcoin Compatibility**: Built on Bitcoin's native script system for multisig addresses (P2SH or P2WSH).

## How It Works

A **multisig wallet** requires multiple parties to sign a transaction before it can be broadcasted to the Bitcoin network. The number of signatures required is customizable, such as:

- **2-of-3**: Two out of three keys must sign a transaction.
- **3-of-5**: Three out of five keys must sign a transaction.

The wallet leverages Bitcoin's **P2SH** (Pay-to-Script-Hash) or **P2WSH** (Pay-to-Witness-Script-Hash) addresses, which allow for the creation of Bitcoin addresses with complex conditions (like multisig) that must be fulfilled to spend the funds.

### 1. **Setting Up a Multisig Wallet**

To create a multisig wallet, you will need to:

- **Generate the public keys** of all participants (the keys that will control the wallet).
- **Define the threshold** (e.g., 2-of-3, 3-of-5) to specify how many signatures are needed to authorize a transaction.
- **Create the multisig address** using a script that specifies the required signatures.

For example, a **2-of-3 multisig wallet** would generate a script requiring 2 out of 3 keys to sign a transaction before funds can be spent.

### 2. **Creating a Transaction**

When creating a transaction from the multisig wallet:

- **Input**: The wallet will specify which UTXOs (unspent transaction outputs) are being spent.
- **Output**: The transaction will specify the destination address and amount.
- **Signature Request**: The wallet will generate a partially signed Bitcoin transaction (PSBT), which is shared with the other participants.
- **Signing**: Each participant signs the PSBT with their private key. Once the required number of signatures is reached, the transaction can be broadcast to the Bitcoin network.

### 3. **Transaction Finalization**

- Once all the required signatures are collected, the transaction is finalized and broadcasted to the Bitcoin network.
- The Bitcoin network validates the multisig transaction and, if valid, includes it in a block, confirming the transfer of funds.

### Example Setup

For a **2-of-3 multisig wallet**, you would:

1. **Generate 3 keys**: Key1, Key2, Key3.
2. **Create a 2-of-3 multisig address** using these keys.
3. **Fund the wallet** by sending Bitcoin to the 2-of-3 multisig address.
4. **Initiate a transaction**: Create a transaction from the multisig address and sign it with the required number of keys (e.g., Key1 and Key2).
5. **Finalise and broadcast** the transaction once the second signature is added.

### Benefits of a Multisig Wallet

- **Increased Security**: If one key is compromised or lost, funds are still secure as additional signatures are required.
- **Redundancy**: Multiple participants can be involved in the wallet's operation, which is useful for organizations, partnerships, or joint accounts.
- **Backup**: Losing one key doesn’t mean losing access to the wallet — as long as the threshold of signatures is met, the funds can still be spent.

### Use Cases

- **Corporate or Team Accounts**: Use for joint business accounts where multiple members need to approve transactions.
- **Cold Storage**: Multisig wallets are often used in conjunction with cold storage solutions to enhance security.
- **Estate Planning**: Secure access to Bitcoin with multiple trusted parties for inheritance purposes.
- **Shared Custody**: Shared access to funds for friends or family members.

## Technologies Used

- **Bitcoin Script**: Utilizes Bitcoin's native scripting system to create multisig addresses (P2SH or P2WSH).
- **PSBT (Partially Signed Bitcoin Transactions)**: Used to facilitate secure, incremental signing of multisig transactions.
- **Bitcoin Core/Full Node**: Interaction with Bitcoin's blockchain for creating and verifying transactions.
- **HD Wallets (Hierarchical Deterministic)**: Supports key generation from seed phrases for multisig setups.

## Getting Started

### Prerequisites

- **Node.js** (for backend implementation)
- A **Bitcoin full node** or access to a Bitcoin node for creating and broadcasting transactions.
- **Bitcoin libraries** such as [bitcoinjs-lib](https://github.com/bitcoinjs/bitcoinjs-lib) to handle multisig address generation and PSBT signing.
