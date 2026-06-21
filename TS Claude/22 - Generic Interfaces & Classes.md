#typescript #generics

## Generic Interface

```typescript
interface Repository<T> {
  findById(id: number): T;
  save(item: T): void;
  getAll(): T[];
}
```

## Generic Class

```typescript
class Stack<T> {
  private items: T[] = [];

  push(item: T) { this.items.push(item); }
  pop(): T | undefined { return this.items.pop(); }
  peek(): T | undefined { return this.items[this.items.length - 1]; }
}

const stack = new Stack<number>();
stack.push(1);
stack.push(2);
stack.pop(); // 2
```

## Default Generic Type

```typescript
interface ApiResponse<T = unknown> {
  data: T;
  status: number;
}
```

---

← [[17 - Abstract Classes & Inheritance]] | → [[23 - Utility Types]]