| Field                                                                         | Description                                                                                                                                                                      |
| ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`nonce`**                                                                   | A counter that ensures each transaction from an account is processed only once and in order. Increments with every transaction.                                                  |
| **`to`**                                                                      | The recipient address. If it’s an existing account, ETH or data is sent. If it’s empty (no `to`), it means a **contract creation transaction**.                                  |
| **`value`**                                                                   | Amount of Ether (in wei) to send along with the transaction.                                                                                                                     |
| **`gasPrice`** (or **`maxFeePerGas` / `maxPriorityFeePerGas`** with EIP-1559) | The price per unit of gas (in wei). This incentivizes miners/validators to include the transaction.                                                                              |
| **`gasLimit`**                                                                | The maximum amount of gas the sender is willing to use for the transaction. Prevents accidental infinite loops from draining all ETH.                                            |
| **`data`**                                                                    | The input data for the transaction. For contract calls, this includes function selectors and encoded arguments. For contract creation, it includes the bytecode of the contract. |
| **`v, r, s`**                                                                 | Cryptographic signature values that prove the transaction was signed by the sender’s private key.                                                                                |
| **`chainId`**                                                                 | Identifies which Ethereum chain/network the transaction is for (to prevent replay attacks across chains).                                                                        |

### 🔹 Extra Context in Solidity

When inside a contract, Solidity exposes some transaction-related information through **global variables**:

- **`msg.sender`** → The address that sent the transaction or call.
    
- **`msg.value`** → The amount of Ether (in wei) sent with the transaction.
    
- **`gasleft()`** → Remaining gas available for execution.
    
- **`tx.gasprice`** → Gas price of the transaction.
    
- **`tx.origin`** → Original external account that started the transaction (not recommended for auth checks).

### ✅ **In short:**  
A transaction is basically `{ nonce, to, value, gas, gasPrice, data, v, r, s }` + `chainId`.  
Solidity gives us `msg.*` and `tx.*` variables to read details when executing smart contracts.