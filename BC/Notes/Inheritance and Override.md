### 🔹 Inheritance in Solidity

Inheritance allows you to create a new contract by reusing code from an existing contract. This helps reduce duplication and organize smart contracts better.

- You use the `is` keyword to inherit.
- A derived (child) contract automatically gets access to **all public and internal** state variables and functions from the parent contract.
- Multiple inheritance is supported, but Solidity uses **C3 linearization** (a specific order resolution for parent contracts) to avoid ambiguity.

```
// Parent contract
contract Animal {
    function sound() public pure returns (string memory) {
        return "Some sound";
    }
}

// Child contract
contract Dog is Animal {
    function breed() public pure returns (string memory) {
        return "Labrador";
    }
}
Here, `Dog` inherits `sound()` from `Animal`, so you can call both `sound()` and `breed()` on `Dog`.
```

### 🔹 Function Override in Solidity

If the child contract wants to **change the behavior** of a function from the parent contract, it uses **override**.

Rules:

1. The parent function must be marked `virtual`.
2. The child function must be marked `override`.
3. If there are multiple parents with the same function, you must specify **all of them** inside `override(A, B)`.

```
// Parent contract
contract Animal {
    function sound() public pure virtual returns (string memory) {
        return "Some sound";
    }
}

// Child contract
contract Dog is Animal {
    function sound() public pure override returns (string memory) {
        return "Bark";
    }
}
Parent function `sound()` is `virtual`, meaning it _can_ be overridden.   
Child function `sound()` uses `override` to replace the parent’s implementation.
```

### 🔹 Multiple Inheritance & Override
When two parent contracts have the same function name, you need to resolve it explicitly.

```
contract A {
    function foo() public pure virtual returns (string memory) {
        return "A";
    }
}

contract B {
    function foo() public pure virtual returns (string memory) {
        return "B";
    }
}

contract C is A, B {
    function foo() public pure override(A, B) returns (string memory) {
        return "C";
    }
}
Here, contract `C` inherits both `A` and `B`, so it must explicitly say `override(A, B)` when redefining `foo()` to avoid ambiguity.
```

