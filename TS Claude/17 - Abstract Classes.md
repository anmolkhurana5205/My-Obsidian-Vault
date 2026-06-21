#typescript #oop

## Abstract Class

Cannot be instantiated directly. Provides a blueprint for subclasses.

```typescript
abstract class Shape {
  abstract area(): number; // must be implemented

  describe() {
    console.log(`Area is ${this.area()}`);
  }
}

class Circle extends Shape {
  constructor(private radius: number) { super(); }
  area() { return Math.PI * this.radius ** 2; }
}

class Rectangle extends Shape {
  constructor(private w: number, private h: number) { super(); }
  area() { return this.w * this.h; }
}

const c = new Circle(5);
c.describe();
```

---

