## Dates in SQL
SQL stores dates in data types like:
- `DATE` → `YYYY-MM-DD` (only date)
- `DATETIME` or `TIMESTAMP` → `YYYY-MM-DD HH:MM:SS` (date + time)
- `TIME` → `HH:MM:SS` (time only)

### Common Date Functions
| Function         | Description                | Example                                      |
| ---------------- | -------------------------- | -------------------------------------------- |
| `NOW()`          | Current date and time      | `2025-10-24 10:15:00`                        |
| `CURDATE()`      | Current date               | `2025-10-24`                                 |
| `CURTIME()`      | Current time               | `10:15:00`                                   |
| `DATE(column)`   | Extract date from datetime | `DATE('2025-10-24 12:30:00') → '2025-10-24'` |
| `YEAR(column)`   | Extract year               | `YEAR('2025-10-24') → 2025`                  |
| `MONTH(column)`  | Extract month              | `MONTH('2025-10-24') → 10`                   |
| `DAY(column)`    | Extract day                | `DAY('2025-10-24') → 24`                     |
| `HOUR(column)`   | Extract hour               | `HOUR('2025-10-24 12:30:00') → 12`           |
| `MINUTE(column)` | Extract minute             | `MINUTE('12:30:45') → 30`                    |
| `SECOND(column)` | Extract second             | `SECOND('12:30:45') → 45`                    |

### Date Arithmetic
| Operation                                   | Description        | Example                                                                 |
| ------------------------------------------- | ------------------ | ----------------------------------------------------------------------- |
| `DATE_ADD(date, INTERVAL n DAY)`            | Add days           | `DATE_ADD('2025-10-24', INTERVAL 5 DAY) → '2025-10-29'`                 |
| `DATE_SUB(date, INTERVAL n DAY)`            | Subtract days      | `DATE_SUB('2025-10-24', INTERVAL 5 DAY) → '2025-10-19'`                 |
| `DATEDIFF(date1, date2)`                    | Difference in days | `DATEDIFF('2025-10-24', '2025-10-20') → 4`                              |
| `TIMESTAMPDIFF(unit, datetime1, datetime2)` | Difference in unit | `TIMESTAMPDIFF(HOUR, '2025-10-24 10:00:00', '2025-10-24 15:30:00') → 5` |

### Formatting Dates
- `DATE_FORMAT(date, format)` → format date as string
```
SELECT DATE_FORMAT('2025-10-24', '%Y/%m/%d'); -- '2025/10/24'
SELECT DATE_FORMAT('2025-10-24 12:30:45', '%d-%b-%Y %H:%i:%s'); -- '24-Oct-2025 12:30:45'
```
Format codes:
- `%Y` → 4-digit year
- `%y` → 2-digit year
- `%m` → month number (01-12)
- `%b` → abbreviated month name
- `%d` → day of month (01-31)
- `%H` → hour (00-23)
- `%i` → minutes
- `%s` → seconds

### Date Comparisons
```
SELECT * 
FROM orders
WHERE order_date BETWEEN '2025-10-01' AND '2025-10-31';
```
- `>` , `<`, `>=`, `<=`, `=` operators work directly with dates.
- `BETWEEN` is inclusive.

## Strings in SQL
Common SQL string types:
- `CHAR(n)` → fixed-length string, padded with spaces
- `VARCHAR(n)` → variable-length string, max n characters
- `TEXT` → large text

### String Functions
| Function                                        | Description                    | Example                                           |
| ----------------------------------------------- | ------------------------------ | ------------------------------------------------- |
| `CONCAT(str1, str2, ...)`                       | Concatenate strings            | `CONCAT('Hello', ' ', 'World') → 'Hello World'`   |
| `CONCAT_WS(sep, str1, str2, ...)`               | Concatenate with separator     | `CONCAT_WS('-', '2025','10','24') → '2025-10-24'` |
| `LENGTH(str)`                                   | Number of bytes                | `LENGTH('abc') → 3`                               |
| `CHAR_LENGTH(str)` / `LENGTH(str)`              | Number of characters           | `CHAR_LENGTH('abc') → 3`                          |
| `LOWER(str)`                                    | Convert to lowercase           | `LOWER('ABC') → 'abc'`                            |
| `UPPER(str)`                                    | Convert to uppercase           | `UPPER('abc') → 'ABC'`                            |
| `TRIM(str)`                                     | Remove leading/trailing spaces | `TRIM(' abc ') → 'abc'`                           |
| `LTRIM(str)` / `RTRIM(str)`                     | Remove left/right spaces       | `LTRIM(' abc') → 'abc'`                           |
| `SUBSTRING(str, start, length)`                 | Extract substring              | `SUBSTRING('abcdef', 2, 3) → 'bcd'`               |
| `REPLACE(str, from, to)`                        | Replace substring              | `REPLACE('2025-10-24','-','/') → '2025/10/24'`    |
| `INSTR(str, substr)`                            | Position of substring          | `INSTR('abcdef','cd') → 3`                        |
| `LEFT(str, n)` / `RIGHT(str, n)`                | First n / last n chars         | `LEFT('abcdef', 3) → 'abc'`                       |
| `LPAD(str, n, padstr)` / `RPAD(str, n, padstr)` | Pad string                     | `LPAD('5',3,'0') → '005'`                         |

### String Comparisons
- Strings can be compared using `=`, `!=`, `<`, `>`, etc.
- `LIKE` operator for pattern matching:

```
SELECT * FROM users
WHERE name LIKE 'A%'; -- starts with A
WHERE name LIKE '%son'; -- ends with 'son'
WHERE name LIKE '%art%'; -- contains 'art'
```
- `_` → any single character
- `%` → any number of characters

### Casting Between Date and String
```
-- Date to string
SELECT DATE_FORMAT(order_date, '%Y-%m-%d') AS date_str FROM orders;

-- String to date
SELECT STR_TO_DATE('24-10-2025', '%d-%m-%Y') AS date_val;
```

### Combining Dates and Strings
```
-- Create a YYYY-MM-DD string from year, month, day columns
SELECT CONCAT(year, '-', LPAD(month,2,'0'), '-', LPAD(day,2,'0')) AS order_date
FROM orders;

-- Format date as readable string
SELECT DATE_FORMAT(order_date, '%d %b %Y') AS formatted_date
FROM orders;
```

### **Best Practices**
1. Always use `DATE` or `DATETIME` column types for dates — don’t store as strings.
2. Use `BETWEEN` or date functions for filtering ranges.
3. Use `CONCAT` / `CONCAT_WS` instead of `+` (MySQL doesn’t support string +).
4. Use `TRIM` to clean user input strings.
5. For pattern matching, prefer `LIKE` with `%` or `_`.

