### 🔹 What are Props in React?

- **Props** stands for **properties**.
- They are used to **pass data from a parent component to a child component**.
- Props are **read-only** (immutable). You cannot change them inside the child component.

### 🔹 How Props Work

1. A **parent component** sends data to a **child component** via props.
2. The child component **receives** these props as an object.

### some rules of props
1. **Props read-only होते हैं**
2. **Props हमेशा parent → child pass होते हैं**
3. **Props को object की तरह treat किया जाता है**
4. Props default values रख सकते हैं
```
function Item({ name = "Unknown" }) {
  return <p>{name}</p>;
}
```
5. **Props dynamic हो सकते हैं**
	- आप string ही नहीं, बल्कि number, array, object, function, या JSX भी props में भेज सकते हो।

### Prop Drilling
Prop drilling in **React** means passing data (via props) from a **parent component** down to **deeply nested child components**, even if some of those intermediate components **don’t actually need** that data — they just pass it along.