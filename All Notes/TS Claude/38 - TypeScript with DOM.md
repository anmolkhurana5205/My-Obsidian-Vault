#typescript #dom

## Querying Elements

```typescript
const btn = document.querySelector<HTMLButtonElement>("#submit")!;
const input = document.getElementById("name") as HTMLInputElement;
```

## Event Listeners

```typescript
btn.addEventListener("click", (e: MouseEvent) => {
  console.log(e.clientX, e.clientY);
});

input.addEventListener("input", (e: Event) => {
  const target = e.target as HTMLInputElement;
  console.log(target.value);
});
```

## Creating Elements

```typescript
const div = document.createElement("div");
div.className = "card";
document.body.appendChild(div);
```

## Type-safe `fetch`

```typescript
interface Post { id: number; title: string; body: string; }

async function getPost(id: number): Promise<Post> {
  const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`);
  if (!res.ok) throw new Error("Fetch failed");
  return res.json() as Promise<Post>;
}
```

---

