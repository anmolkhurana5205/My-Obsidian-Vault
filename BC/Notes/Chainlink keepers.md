**Chainlink Keepers** (now called **Chainlink Automation**) are a decentralized service that let your smart contracts run **automated tasks** without you having to manually trigger them.

Normally, a smart contract just sits idle on-chain — it only does something when someone sends it a transaction. But what if you need it to run **regularly or conditionally** (like a cron job in Web2)? That’s where Keepers come in.

---

### 🔑 How Chainlink Keepers work

- You register your contract with the Chainlink Automation Network.
- You define a function (usually called `checkUpkeep`) that tells Keepers **when your contract needs work**.
- You also define a function (called `performUpkeep`) that contains the **action to run**.
- The Chainlink node operators monitor conditions off-chain and when it’s time, they send a transaction on-chain to trigger your function.

---

### ✅ Example Use Cases

1. **Automated Yield Harvesting** — claim rewards from DeFi protocols at regular intervals.
2. **NFT Minting Windows** — open/close minting at a certain time automatically.    
3. **Liquidation Bots** — automatically liquidate unhealthy loans in DeFi without needing your own bot.
4. **Scheduled Payments** — send tokens every month without manual action.
5. **Gaming / Random Events** — trigger in-game events automatically on schedule.

---

### ⚡ Why it’s useful

- **Trustless & decentralized** → not dependent on a single server/bot.    
- **Reliable** → powered by Chainlink’s decentralized node network.
- **Gas efficient** → only executed when the condition is met.
- **No need to babysit your contract** → automation keeps it running smoothly.