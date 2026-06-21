#typescript #oop #classes

## Basic Class

```typescript
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  speak(): void {
    console.log(`${this.name} makes a sound.`);
  }
}

const a = new Animal("Dog");
a.speak();
```

## Shorthand Constructor (Parameter Properties)

```typescript
class User {
  constructor(
    public name: string,
    private age: number
  ) {}
}
// 'name' and 'age' are auto-assigned as properties
```

## Getters & Setters

```typescript
class Circle {
  private _radius: number = 0;

  get radius() { return this._radius; }
  set radius(val: number) {
    if (val < 0) throw new Error("Negative radius");
    this._radius = val;
  }
}
```

## Static Members

```typescript
class MathUtils {
  static PI = 3.14159;
  static area(r: number) { return MathUtils.PI * r * r; }
}
MathUtils.area(5);
```

## Readonly Fields

```typescript
class Config {
  readonly apiUrl: string = "https://api.example.com";
}
```

---

← [[14 - Arrow Functions & this]] | → [[16 - Access Modifiers]]