React.js is a **JavaScript library** (not a full framework) developed by **Facebook** for building **user interfaces (UI)**. It’s **component-based**, **declarative**, and focuses on building **fast, interactive, and reusable** front-end applications.

### Props

- Short for “properties.”
    
- Data passed **from parent to child**.
    
- Immutable inside the child.

### Virtual DOM

- A lightweight copy of the real DOM.
    
- React updates only the parts of the UI that change, making it **fast**.

### One-Way Data Flow

- Data flows from parent → child. Easy to track changes.

### Hooks

- Functions like `useState`, `useEffect`, `useContext` for managing state, side effects, and more in functional components.

### State

- Internal data storage for components.
    
- Changes trigger **re-renders**.
    
- Managed with `useState`, `useReducer`, etc.

### 🔄 Lifecycle (Concept)

React components go through:

1. **Mounting** (creation)
    
2. **Updating** (re-rendering)
    
3. **Unmounting** (removal)