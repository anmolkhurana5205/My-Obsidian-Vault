#typescript #oop

## public / private / protected

```typescript
class BankAccount {
  public owner: string;
  private balance: number;
  protected interestRate: number = 0.05;

  constructor(owner: string, balance: number) {
    this.owner = owner;
    this.balance = balance;
  }

  public deposit(amount: number) {
    this.balance += amount;
  }

  private validate() { /* internal */ }
}
```

|Modifier|Same Class|Subclass|Outside|
|---|---|---|---|
|`public`|✅|✅|✅|
|`protected`|✅|✅|❌|
|`private`|✅|❌|❌|

## `#` Private Fields (ES2022 native)

```typescript
class Counter {
  #count = 0;
  increment() { this.#count++; }
}
// #count is truly private, even at runtime
```

> [!info] `private` in TS is compile-time only. `#` is enforced at runtime too.

---

← [[15 - Classes]] | → [[17 - Abstract Classes]]