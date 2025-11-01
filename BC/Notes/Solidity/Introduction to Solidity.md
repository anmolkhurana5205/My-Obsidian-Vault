### What You Can Return in Solidity
| Type                                                | Example               | Return Allowed? |
| --------------------------------------------------- | --------------------- | --------------- |
| **Single values** (`uint`, `bool`, `address`, etc.) | `return a;`           | ✅ Yes           |
| **Multiple values (tuples)**                        | `return (a, b);`      | ✅ Yes           |
| **Arrays (fixed or dynamic)**                       | `return arr;`         | ✅ Yes           |
| **Structs**                                         | `return myStruct;`    | ✅ Yes           |
| **Mappings**                                        | ❌ `return myMapping;` | ❌ _Not allowed_ |
| **Enums**                                           | `return myEnum;`      | ✅ Yes           |

