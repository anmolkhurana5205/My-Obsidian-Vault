#typescript #advanced

## Iterable Interface

```typescript
class Range implements Iterable<number> {
  constructor(private start: number, private end: number) {}

  [Symbol.iterator](): Iterator<number> {
    let current = this.start;
    const end = this.end;
    return {
      next(): IteratorResult<number> {
        if (current <= end) return { value: current++, done: false };
        return { value: 0, done: true };
      }
    };
  }
}

for (const n of new Range(1, 5)) console.log(n); // 1 2 3 4 5
```

## Generator Functions

```typescript
function* counter(start: number): Generator<number> {
  while (true) yield start++;
}

const gen = counter(1);
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
```

## Async Generator

```typescript
async function* fetchPages(url: string): AsyncGenerator<string> {
  let page = 1;
  while (true) {
    const res = await fetch(`${url}?page=${page++}`);
    if (!res.ok) break;
    yield await res.text();
  }
}
```

---
