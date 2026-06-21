#typescript #modules

Namespaces group code under a named scope. Mostly used in older codebases.

```typescript
namespace Validators {
  export interface StringValidator {
    isValid(s: string): boolean;
  }

  export class EmailValidator implements StringValidator {
    isValid(s: string) { return s.includes("@"); }
  }
}

const v = new Validators.EmailValidator();
```

> [!warning] Prefer ES Modules (`import`/`export`) over namespaces in modern TS.

---

