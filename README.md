# multisig-wallet
A Solidity implementation of a Multi-Signature Wallet that requires multiple owner approvals before executing transactions, enhancing security for shared fund management.
# MultiSig Wallet Smart Contract

A simple Multi-Signature Wallet implemented in Solidity.  
This smart contract requires multiple owners to approve a transaction before it can be executed, improving security for shared fund management.

## Features

- Multiple wallet owners
- Transactions must receive a required number of confirmations
- Automatic execution once enough confirmations are collected
- Ether transfer support
- Event logging for transaction lifecycle

## Smart Contract Structure

### State Variables

- `owners` – list of wallet owners
- `numConfirmationsRequired` – number of confirmations required to execute a transaction
- `transactions` – list of submitted transactions
- `isConfirmed` – mapping to track which owner confirmed which transaction

### Transaction Structure
  struct Transaction {
  address to;
  uint value;
  bool executed;
  }

## Functions

### submitTransaction(address _to)

Allows a user to submit a transaction and send Ether to the contract.

### confirmTransaction(uint transactionId)

Allows an owner to confirm a transaction.

### executeTransaction(uint transactionId)

Executes the transaction once the required number of confirmations is reached.

### isTransactionConfirmed(uint transactionId)

Internal function that checks if enough confirmations were collected.

## Events

- `TransactionSubmitted`
- `TransactionConfirmed`
- `TransactionExecuted`

These events help track contract activity on the blockchain.

## Deployment

You can deploy this contract using:

- Remix IDE
- Hardhat
- Foundry

Example constructor parameters:
  owners = [owner1, owner2, owner3]
  numConfirmationsRequired = 2

## Example Flow

1. Deploy contract with a list of owners
2. Submit a transaction with Ether
3. Owners confirm the transaction
4. Once confirmations reach the required number, the transaction executes automatically

## Security Considerations

This contract is a simplified implementation and **should not be used in production without proper security audits**.

Possible improvements:

- owner access control
- transaction revocation
- reentrancy protection
- confirmation tracking optimization

## License

GPL-3.0
