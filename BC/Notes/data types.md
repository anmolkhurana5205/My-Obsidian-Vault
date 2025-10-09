## value types

- **Boolean (`bool`)** → `true` or `false`
- **Integer (`int` and `uint`)** → Signed (`int`) and unsigned (`uint`) integers with different bit sizes (`uint8`, `uint16`, …, up to `uint256`). Default is `uint256` / `int256`.
- **Address (`address`)** → Holds a 20-byte Ethereum address.
- `address payable` → can receive Ether with `.transfer()` or `.send()`.
- **Fixed-size byte arrays** → `bytes1` to `bytes32`
- **Enums (`enum`)** → User-defined type for constant values (like states).

#### default values
- **`bool`** → `false`
- **`int` / `uint`** → `0` (regardless of size, e.g., `uint8`, `int256`, etc.)
- **`address`** → `0x0000000000000000000000000000000000000000` (zero address)
- **`address payable`** → also `0x0000000000000000000000000000000000000000`
- **Fixed-size byte arrays (`bytes1` → `bytes32`)** → filled with `0x00...00` (all zero bytes)
- **`enum`** → the first value in the enum definition (index `0`)
## reference types

### 1. **Arrays**

- Can be **fixed-size** or **dynamic-size**.    
- Elements can be any type (even other arrays or structs).
- Examples:
    `uint[3] fixedArr;       // fixed size uint[] dynamicArr;      // dynamic size`
---
### **2. Strings**

- A dynamically sized UTF-8 encoded sequence of characters.
- Internally stored as `bytes`.
- Example:
    `string public name = "Anmol";`
---

### **3. Bytes (Dynamic)** (if you give size to it, then it became fixed and value data type)

- A dynamically sized array of bytes.
- Similar to `string`, but cheaper in gas and meant for raw data.
- Example:
    `bytes public data; // dynamic bytes`
---

### **4. Structs**

- User-defined types that can group variables.
- Can include both value and reference types.    
- Example:
    `struct Person {     string name;     uint age; }  Person public p1;`
---

### **5. Mappings**

- Key-value pairs (like a hash table).
- Keys must be value types, values can be any type (including reference types).
- **However, there’s a special exception: `string` and `bytes` can be used as keys in mappings starting from Solidity 0.8.0 because internally Solidity hashes the string/bytes to `bytes32` using `keccak256` before storing**
- Example:
    
    `mapping(address => uint) public balances;`
    

---

### 🔹 Important Notes on Reference Types

- **Must specify data location** when used in function parameters or variables inside functions:
    
    - `storage` → permanent, blockchain-persisted
        
    - `memory` → temporary, editable, lasts only during function execution
        
    - `calldata` → temporary, read-only, cheaper (external functions only)