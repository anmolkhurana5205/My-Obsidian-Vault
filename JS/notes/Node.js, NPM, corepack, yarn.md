### What is Node.js
- **Node.js** is a **JavaScript runtime** that lets you **run JavaScript outside the browser**.

- Normally, JavaScript runs in a browser (like Chrome or Firefox) to make websites interactive.  
- With Node.js, you can run JS on your **computer/server**, just like Python, Java, or C++.
### ⚡ Key Points

1. **Built on Chrome V8 Engine** – This is the same engine that powers Google Chrome, so Node.js runs JavaScript really fast.
2. **Event-driven & Non-blocking I/O** – Node.js handles multiple tasks at the same time without waiting for one to finish, which is perfect for **real-time apps** like chat apps or streaming.
3. **Server-side JavaScript** – You can build **web servers, APIs, backend services** all in JavaScript.
4. **npm (Node Package Manager)** – Node comes with **npm**, a huge ecosystem of packages/modules you can use in your projects.

### 🧩 What is **Corepack**?

**Corepack** is a **tool that comes with Node.js (from v16.9 onwards)**.  
It acts as a **bridge** between Node.js and different **package managers** like **npm**, **Yarn**, and **pnpm**.

Think of it as a **package manager manager** 😄

Corepack lets you easily use **Yarn** or **pnpm** without installing them globally — it automatically fetches the right version for your project.

Some commands
- `corepack enable`
- `corepack disable`

## 🧩 What is **Yarn**?

**Yarn** is a **JavaScript package manager**, similar to **npm**, used to **install, manage, and run dependencies** (libraries and tools) in your Node.js projects.

It was created by **Facebook (Meta)** in **2016** to solve problems they faced with npm at that time — mainly **speed**, **reliability**, and **deterministic installs**.