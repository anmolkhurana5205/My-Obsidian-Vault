A **Promise** in JavaScript represents a **value that will be available in the future** — like a **placeholder** for something that hasn’t finished yet (for example, fetching data from an API).

In simple words:

> A Promise is like saying “I promise I’ll give you the result later.”

It helps handle **asynchronous operations** — things that take time to complete (like file reading, database queries, or network requests).

---

### ⚙️ Promise States

A Promise can be in **one of three states**:

| State         | Meaning                                |
| ------------- | -------------------------------------- |
| **Pending**   | Still waiting (operation not done yet) |
| **Fulfilled** | Operation completed successfully       |
| **Rejected**  | Operation failed with an error         |

🪄 Basic Syntax
```
const myPromise = new Promise((resolve, reject) => {
  let success = true;

  if (success) {
    resolve("✅ Task completed!");
  } else {
    reject("❌ Something went wrong.");
  }
});
```
Here:
- `resolve()` → means the promise succeeded
- `reject()` → means the promise failed.

### 💡 Handling the Promise

You can handle the result using `.then()` and `.catch()`:
```
myPromise
  .then((message) => {
    console.log(message); // runs if resolved
  })
  .catch((error) => {
    console.log(error); // runs if rejected
  });
```

### 🧩 Real Example (fetching data)
```
fetch("https://api.example.com/data")
  .then((response) => response.json()) // converts data to JSON
  .then((data) => console.log(data))   // handles the data
  .catch((error) => console.log("Error:", error)); // handles errors
```
✅ `fetch()` returns a Promise, which resolves when the network request completes.

### ⏳ Async/Await (modern, cleaner way)

Instead of chaining `.then()`, we can use `async` and `await`:
```
async function getData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log("Error:", error);
  }
}
```
Here:
- `await` pauses execution until the promise resolves.
- `try...catch` handles errors instead of `.catch()`.

| Concept         | Description                       |
| --------------- | --------------------------------- |
| **Promise**     | Handles async operations          |
| **resolve()**   | Marks promise as successful       |
| **reject()**    | Marks promise as failed           |
| **then()**      | Runs when promise succeeds        |
| **catch()**     | Runs when promise fails           |
| **async/await** | Cleaner syntax to handle promises |