State is a **JavaScript object** that stores **dynamic data** for a React component. When this data changes, React **re-renders** the component automatically to reflect those changes in the UI.

State is basically the memory of the component.

### Why State Exists

Without state, your React components would be **static**—you’d render something once and that’s it.  
State makes components **interactive**.

### State Rules

1. **Never mutate state directly**
    
    `// ❌ Wrong 
    count = count + 1; 
    // ✅ Correct 
    setCount(count + 1);
    `
	    NOTE => so what happen when we try to update state manually ?  react will not be able to know that we change the state by changing the value of a variable so it will not re - render that component so that's why it is very important to change the state by hooks setter function.
		It will only schedule the re - render when we change the state in a correct way.
		
1. **Initialize state inside the component**  
    State must be **declared per component**.
    
2. **Don’t rely on immediate updates**  
    React updates state asynchronously.
    
3. **Minimal state principle**  
    Store only what you need. Don’t duplicate values that can be derived.
    
4. when a piece of state is passed into the child element and that state changes then the parent element re-renders (very obvious) but the different thing is that child element in which the piece of state is passes also re-renders if not then there is no other way for react to sync everything.

Some best practices when dealing with state is 
use callback function in hook to change the state when the changes is based on previous value of the state.
Ex - do like this 
setStep((s) => s + 1);
and not like below 
setStep(step + 1);

because : in this setStep(step + 1); you’re directly using the **current `step` value** from this render cycle. React schedules state updates asynchronously (they don’t happen immediately). If multiple updates happen in quick succession before React re-renders, each one will still use the same stale `step` value.

// Suppose step = 0 initially
setStep(step + 1); // schedules: set to 1
setStep(step + 1); // also schedules: set to 1 (NOT 2, because "step" was 0 in this render)

in this setStep((s) => s + 1); 
setStep((s) => s + 1); // schedules: s = 0 → 1
setStep((s) => s + 1); // schedules: s = 1 → 2
step = 2


## Some Practical Guidelines about State

- Use a state variable for any data that the component should keep track of ("remember") over time. This is data that will change at some point. In Vanilla JS, that's a let variable, or an [] or {}

- ➡ Whenever you want something in the component to be dynamic, create a piece of state related to that "thing", and update the state when the "thing" should change (aka "be dynamic")

Example: A modal window can be open or closed. So we create a state variable isopen that tracks whether the modal is open or not. On isopen true we display the window, on isopen = false we hide it.

- If you want to change the way a component looks, or the data it displays, update its state. This usually happens in an event handler function.

- When building a component, imagine its view as a reflection of state changing over time

- For data that should not trigger component re-renders, don't use state. Use a regular variable instead. This is a common beginner mistake.

### when and where to use state ?
![[Pasted image 20250922185741.jpg]]

### Inverse data flow
child updating parents state, this can be done by passing the setAnything function as prop to the child so this trick allow us to change the state resides in the parent element (also did the same thing in far away project with setItems function)

### Local State vs global state
