
## ✅ 1. Built-in Browser Popups (Blocking dialogs)
### 🔹 `alert()`

- Shows a simple message with an **OK** button.
    
- Informational only.

```
alert("Hello! This is an alert box.");
```

### 🔹 `confirm()`

- Shows a message with **OK** and **Cancel** buttons.
    
- Returns `true` if OK is pressed, `false` if Cancel.

```
const result = confirm("Are you sure?");
if (result) {
  console.log("User pressed OK");
} else {
  console.log("User pressed Cancel");
}
```

### 🔹 `prompt()`

- Shows a message with a text input field.
    
- Returns the entered string, or `null` if Cancel is pressed.

```
const name = prompt("What is your name?");
console.log("Hello", name);
```

### ⚠️ Note: 
These dialogs are **synchronous and blocking** → they freeze page interaction until closed.  
That’s why modern UIs often replace them with **custom modal popups**.

## ✅ 2. Window Popups (New Browser Window/Tab)
