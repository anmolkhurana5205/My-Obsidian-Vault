```
yarn solcjs --bin --abi --include-path node_modules/ --base-path . -o . SimpleStorage.sol
```
This command uses **Yarn** to run **`solcjs`**, which is the **JavaScript version of the Solidity compiler (solc)**.

|Part|Meaning|
|---|---|
|`yarn solcjs`|Runs the `solcjs` compiler (installed via Yarn or npm)|
|`--bin`|Generates the **binary (bytecode)** for the contract — this is what gets deployed on the blockchain|
|`--abi`|Generates the **ABI (Application Binary Interface)** — used to interact with the contract from frontend or scripts|
|`--include-path node_modules/`|Tells the compiler where to look for imported files (e.g., `@openzeppelin/contracts`)|
|`--base-path .`|Defines the base folder for your Solidity project (here, the current directory `.`)|
|`-o .`|Output directory — `.` means “save the compiled files in the current directory”|
|`SimpleStorage.sol`|The Solidity source file you want to compile|
## 🧠 **What Happens When You Run It**

1. Yarn runs the **solidity compiler (`solcjs`)**.
2. It looks at `SimpleStorage.sol`.
3. Compiles it and generates two output files:
    - `SimpleStorage_sol_SimpleStorage.bin` → bytecode
    - `SimpleStorage_sol_SimpleStorage.abi` → ABI
4. Both files appear in the **current directory (`-o .`)**.
