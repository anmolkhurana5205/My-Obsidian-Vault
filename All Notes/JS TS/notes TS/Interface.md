- It’s used to **define the shape (structure) of an object** — basically, what properties and types an object should have.

### Example in plain TypeScript
```
interface User {
  id: number;
  name: string;
  email?: string; // optional property
}

const user1: User = {
  id: 1,
  name: "Anmol"
};
```

### How it’s used in React / Next.js (in `.tsx` files)
- In React (or Next.js, which is built on React), you’ll most often use **interfaces to define props**.
```
import React from 'react';

interface ButtonProps {
  label: string;
  onClick: () => void;
  disabled?: boolean;
}

const Button: React.FC<ButtonProps> = ({ label, onClick, disabled }) => {
  return (
    <button onClick={onClick} disabled={disabled}>
      {label}
    </button>
  );
};

export default Button;
```

Here:
- `interface ButtonProps` defines what props the component should accept.
- `React.FC<ButtonProps>` ensures the component follows that shape.
- If you try to pass a prop that doesn’t exist (like `color`), TypeScript will warn you.

### Interface vs Type (common confusion)
You can also use `type` in TS:
```
type ButtonProps = {
  label: string;
  onClick: () => void;
};
```

Both work similarly, but:
- **Interface** is extendable (`extends` another interface).
- **Type** is more flexible (can use unions, intersections, etc.).
In React/Next.js projects, you can use **either** — it’s a matter of preference or team convention.

