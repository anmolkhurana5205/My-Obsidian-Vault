When you pass variables to functions, Solidity needs to know **where the data will live**:

- **`storage`** → permanent data stored on the blockchain (contract state variables).
- **`memory`** → temporary data stored only during function execution, deleted afterward.
- **`calldata`** → similar to memory but **read-only**, used for external function inputs.

``` solidity
EXAMPLE (MEMORY)
function addPerson(string memory _name, uint256 _favNumber) public{

        People memory newPerson = People({favNumber: _favNumber, name: _name});

        people.push(newPerson);

    }
```

### ✅ Key Rule
- **Reference types** → must specify data location (`storage`, `memory`, or `calldata`) when used in function parameters.  
    Examples: `string`, `bytes`, `array`, `struct`, `mapping`.
- **Value types** → don’t need a location specifier.  
    Examples: `uint`, `int`, `bool`, `address`, `bytes32`.

| Feature           | **Storage** 🗄️                                            | **Memory** 💾                                                                        | **Calldata** 📩                                                             |
| ----------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------- |
| **Lifetime**      | Permanent (lives on blockchain as long as contract exists) | Temporary (exists only during function execution)                                    | Temporary (exists only during external function call)                       |
| **Mutability**    | Read & Write                                               | Read & Write                                                                         | Read-only                                                                   |
| **Gas Cost**      | Highest (writing is very expensive)                        | Medium (cheaper than storage)                                                        | Lowest (cheaper than memory, no copy made)                                  |
| **Used For**      | State variables (contract-level data)                      | Local variables inside functions (reference types like array, struct, string, bytes) | Function parameters of external functions (arrays, structs, strings, bytes) |
| **Accessibility** | Accessible across contract and persists between calls      | Accessible only inside the function where defined                                    | Accessible only inside the external function call, cannot be modified       |
| **Example**       | `uint public count;`                                       | `string memory name = "Anmol";`                                                      | `function setName(string calldata _name) external { ... }`                  |
