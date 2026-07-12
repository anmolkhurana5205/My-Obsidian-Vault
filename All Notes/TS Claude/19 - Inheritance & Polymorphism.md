#typescript #oop

## Inheritance with `extends`

```typescript
class Animal {
  constructor(public name: string) {}
  speak(): string { return `${this.name} makes a sound`; }
}

class Dog extends Animal {
  speak(): string { return `${this.name} barks`; }
}

class Cat extends Animal {
  speak(): string { return `${this.name} meows`; }
}

const animals: Animal[] = [new Dog("Rex"), new Cat("Whiskers")];
animals.forEach(a => console.log(a.speak())); // Polymorphism
```

## `super` Keyword

```typescript
class Vehicle {
  constructor(public brand: string) {}
  describe() { return `Brand: ${this.brand}`; }
}

class Car extends Vehicle {
  constructor(brand: string, public model: string) {
    super(brand); // call parent constructor
  }
  describe() { return super.describe() + `, Model: ${this.model}`; }
}
```

## Implementing Interfaces in Classes

```typescript
interface Flyable {
  fly(): void;
}

class Plane extends Vehicle implements Flyable {
  fly() { console.log("Flying!"); }
}
```

---

← [[16 - Access Modifiers]] | → [[20 - Generics Basics]]