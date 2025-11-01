Note: Space is non alphanumeric.
#### SQL treats characters in three main types:
| Type                    | Examples                                 | Meaning                                       |
| ----------------------- | ---------------------------------------- | --------------------------------------------- |
| **Alphabet Characters** | A–Z, a–z                                 | Basic letters                                 |
| **Numeric Characters**  | 0–9                                      | Digits / numbers                              |
| **Special Characters**  | `@ # $ % ^ & * ( ) - + _ ! ~ . , /` etc. | Characters that are **not letters or digits** |

### Character Handling Tools in SQL
| Tool                            | Purpose                                      |
| ------------------------------- | -------------------------------------------- |
| `LIKE`                          | Simple pattern match                         |
| `REGEXP` / `RLIKE`              | Advanced pattern match (regular expressions) |
| `REPLACE()` / `SUBSTRING()`     | Modify strings                               |
| `REGEXP_REPLACE()` _(MySQL 8+)_ | Remove or replace patterns                   |

### **Patterns (Regular Expressions)**
| Symbol | Meaning                                    |
| ------ | ------------------------------------------ |
| `[ ]`  | Character group                            |
| `[^ ]` | NOT this group                             |
| `\w`   | Word character → **A–Z, a–z, 0–9, _**      |
| `\W`   | Anything **not** `\w` (special characters) |
| `+`    | One or more repetitions                    |
| `*`    | Zero or more repetitions                   |
| `^`    | Start of string                            |
| `$`    | End of string                              |

### **Detect Different Character Types**
1. **Only Letters**
```
column_name REGEXP '^[A-Za-z]+$'
```
2. **Only Numbers**
```
column_name REGEXP '^[0-9]+$'
```
3. **Only Alphanumeric (no special chars)**
```
column_name REGEXP '^[A-Za-z0-9]+$'
```
4. **Contains Special Characters**
```
column_name REGEXP '[^A-Za-z0-9]'
```

```
column_name REGEXP '[^A-Za-z0-9]'
```
means: Does the column contain at least one character that is _not_ A–Z, a–z, or 0–9?

and 

```
column_name REGEXP '^[^A-Za-z0-9]+$'
```
means: The entire value must consist only of special characters (no letters, no digits).

### LIKE Wildcards
|Symbol|Meaning|
|---|---|
|`%`|any number of characters|
|`_`|exactly one character|

### Escape Special Characters in LIKE
If the value itself contains `%` or `_`:
```
WHERE column_name LIKE '%\_%' ESCAPE '\';
```

### Why we need escape character in regexp
certain characters have **special meanings**, like: .  *  +  ?  ^  $  (  )  [  ]  {  }  |  \
So, if you want to **match them literally**,  
you must **escape them with a backslash (`\`)** in regex.

Example:
- `.` → any character (special meaning)
- `\.` → literal dot (like in `leetcode.com`) ✅

### The double-escape problem in SQL
In MySQL, your regex sits **inside a SQL string**,  
and **SQL itself also uses backslash (`\`)** as an escape character.
so to fix this issue
you should double backlash.


### Remove Special Characters
MySQL 8+:
```
SELECT REGEXP_REPLACE(column_name, '[^A-Za-z0-9]', '') AS cleaned_value
FROM table_name;
```

### Extract Only Special Characters
```
SELECT REGEXP_REPLACE(column_name, '[A-Za-z0-9]', '') AS only_special
FROM table_name;
```

### Check if a String Contains at Least One Letter + One Number
```
WHERE column_name REGEXP '[A-Za-z]' AND column_name REGEXP '[0-9]';
```

### Validate Email (Basic Pattern)
```
WHERE email REGEXP '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$';
```
#### Explanation
|Symbol|Meaning|
|---|---|
|`^`|Start of string|
|`$`|End of string|
|`+`|One or more occurrences|
|`[]`|Allowed characters (character set)|
|`\.`|Literal dot `.` (escaped, because `.` normally means "any character")|
#### **1. Username part (before @)**
```
[A-Za-z0-9._%+-]+
```

| Allowed Character | Meaning           |
| ----------------- | ----------------- |
| `A-Z`             | Uppercase letters |
| `a-z`             | Lowercase letters |
| `0-9`             | Digits            |
| `.`               | Dot               |
| `_`               | Underscore        |
| `%`               | Percent           |
| `+`               | Plus              |
| `-`               | Dash              |
#### 2. The `@` symbol
#### 3. Domain name part (after @ but before .)
```
[A-Za-z0-9.-]+
```

|Allowed|Meaning|
|---|---|
|A–Z|Uppercase letters|
|a–z|Lowercase letters|
|0–9|Digits|
|`.`|Dot in domain (like `co.in`)|
|`-`|Dash allowed in domain|
#### 4. Dot before extension
```
\.
```
This means a **literal dot** (e.g., between `gmail` and `com`).
#### 5. Extension (TLD)
```
[A-Za-z]{2,}
```
- {2,} means: At least **2 characters** long (no upper limit)