## 🧩 What is **ethers.js**?

**ethers.js** is a **JavaScript library** that allows you to **interact with the Ethereum blockchain** — for example:

- Deploy and call **smart contracts**
- Read and write **data on the blockchain**
- Connect your **frontend (React, Next.js, etc.)** to a wallet like **MetaMask**

- Think of `ethers.js` as a **bridge between your dApp (frontend)** and the **Ethereum network**.

---

## ⚙️ Why Developers Love ethers.js

✅ Lightweight and modern (smaller and cleaner than web3.js)  
✅ Works perfectly with MetaMask and Hardhat  
✅ Supports multiple Ethereum networks (mainnet, testnets, local Ganache, etc.)  
✅ Provides tools for signing, encoding, and contract interaction

## 🧠 How It Works

The library mainly revolves around 3 key concepts:

|Concept|Description|
|---|---|
|**Provider**|Connects to the blockchain (read-only access)|
|**Signer**|Represents an Ethereum account (can sign transactions)|
|**Contract**|Lets you interact with smart contracts (read/write data)|

## 🧰 Installation
``` bash
npm install ethers
```
or
``` bash
yarn add ethers
```

## ⚡ Basic Example

### 1️⃣ Connect to Ethereum
``` solidity
import { ethers } from "ethers";  

// Connect to public network (like mainnet) 
const provider = new ethers.JsonRpcProvider("https://mainnet.infura.io/v3/YOUR_INFURA_KEY");
```

|Network|Example URL|Purpose|
|---|---|---|
|Local Ganache|`http://127.0.0.1:7545`|Local testing|
|Local Hardhat|`http://127.0.0.1:8545`|Local testing|
|Ethereum Mainnet (via Infura)|`https://mainnet.infura.io/v3/YOUR_KEY`|Real blockchain|
|Sepolia/Testnet (via Infura)|`https://sepolia.infura.io/v3/YOUR_KEY`|Test network|

### 2️⃣ Read from Blockchain

``` js
const blockNumber = await provider.getBlockNumber(); 
console.log("Current Block:", blockNumber);
```

### 3️⃣ Connect Wallet (like MetaMask)

``` js
const provider = new ethers.BrowserProvider(window.ethereum);
const signer = await provider.getSigner();
console.log("Your Address:", await signer.getAddress());
```

### 4️⃣ Interact with a Smart Contract
``` js
const contractAddress = "0xYourContractAddress";
const abi = [ "function getValue() view returns (uint)" ];

const contract = new ethers.Contract(contractAddress, abi, provider);
const value = await contract.getValue();
console.log("Stored Value:", value.toString());
```

### 5️⃣ Write to Blockchain (Send Transaction)

``` js
const contractWithSigner = contract.connect(signer);
const tx = await contractWithSigner.setValue(42);
await tx.wait();
console.log("Transaction complete!");
```
