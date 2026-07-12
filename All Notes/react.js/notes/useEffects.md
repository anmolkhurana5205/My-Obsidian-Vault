- It is basically a react hook that lets you perform side effects in functional components.
- the side effect is anything that effects somethings outside the component's scope:
	- Fetching data from an API.
	- Subscribing to events
	- Updating the DOM manually
	- Setting up timers (like `setTimeout` or `setInterval`)

### Basic Syntax
```
useEffect(() => {
  // your side effect code here
});
```


### The Dependency Array
```
useEffect(() => {
  // effect logic
}, [dependencies]);
```
- The first argument — a **function** — is your effect (what you want to do).
- The second argument — the **dependency array** — tells React **when to re-run the effect**.
- So, if you include certain **states or props** in that array, React will automatically **re-run the effect whenever any of them change.**

### Use it with No Dependency Array
```
useEffect(() => {
  console.log("I run after every render");
});
```
- Runs after **every render** (mount + update).
- Be careful: if your effect updates state, it can cause **infinite re-renders**.

### Empty Dependency Array `[]`
```
useEffect(() => {
  console.log("I run only once on mount");
}, []);
```
- Runs **only once** when the component mounts.
- Perfect for:
    - Fetching data from APIs
    - Setting up subscriptions
    - Initializing values

### With Specific Dependencies
```
useEffect(() => {
  console.log("I run when `count` changes");
}, [count]);
```

## Cleanup Function
Many side effects need **cleanup** — for example:
- Removing event listeners
- Clearing timeouts
- Canceling network requests

- You can return a function from your `useEffect` for cleanup:
```
useEffect(() => {
  console.log("Component mounted");

  return () => {
    console.log("Component unmounted or dependencies changed");
  };
}, []);
```
React automatically calls the cleanup function:
- **Before** running the effect again (on dependency change)
- **When the component unmounts**

## Order of Execution in `useEffect`
When React re-renders a component that uses `useEffect`, here’s what actually happens:
### On the **first render**
- React renders the component (calls your function to produce the UI).
- After painting to the screen, React runs the **effect function** (the first argument of `useEffect`).
- There’s **no cleanup yet**, because it’s the first run.
```
useEffect(() => {
  console.log("Effect runs");
  return () => {
    console.log("Cleanup runs");
  };
}, []);
```
Output:
```
Effect runs
```


### On **subsequent renders (when dependencies change)**
- Before React runs the _new_ effect, it first **runs the cleanup function from the previous effect.**
- This ensures that old effects are properly removed before setting up new ones.
- So if your dependency changes, the order is:
```
useEffect(() => {
  console.log("Effect runs with count:", count);
  return () => {
    console.log("Cleanup runs before next effect");
  };
}, [count]);
```
If `count` goes from 0 → 1 → 2, you’ll see:
```
Effect runs with count: 0
Cleanup runs before next effect
Effect runs with count: 1
Cleanup runs before next effect
Effect runs with count: 2
```

### On **unmounting**
- When the component is removed from the UI, React calls the **cleanup function one last time**.
- This is how you remove listeners, intervals, or subscriptions safely.

### React’s Rule of Thumb:
> Every **reactive value** (state, prop, or derived variable) that you **use inside** the effect should be listed in the dependency array.

