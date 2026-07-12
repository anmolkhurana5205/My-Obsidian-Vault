#typescript #oop

Mixins allow composing behavior from multiple sources without multiple inheritance.

```typescript
type Constructor<T = {}> = new (...args: any[]) => T;

function Timestamped<TBase extends Constructor>(Base: TBase) {
  return class extends Base {
    createdAt = new Date();
  };
}

function Activatable<TBase extends Constructor>(Base: TBase) {
  return class extends Base {
    isActive = false;
    activate() { this.isActive = true; }
    deactivate() { this.isActive = false; }
  };
}

class User { constructor(public name: string) {} }
const TimestampedActivatableUser = Activatable(Timestamped(User));

const u = new TimestampedActivatableUser("Alice");
u.activate();
console.log(u.createdAt, u.isActive);
```

---

