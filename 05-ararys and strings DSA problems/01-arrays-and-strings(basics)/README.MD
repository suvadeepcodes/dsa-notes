# Arrays and Strings 

## What is an Array?

- An **array** is an **ordered collection of elements**.

## JavaScript Arrays

- JavaScript arrays are **dynamic**.

- Each element can be accessed using its **index**.

  ```bash
  const arr = [10, 20, 30, 40];
  
  arr[0]; // 10
  arr[2]; // 30
  Index:  0   1   2   3
          ↓   ↓   ↓   ↓
  Array: 10  20  30  40
  ```

- You don't need to specify the size when creating an array. `const arr = []`;

- The array can grow as elements are added.

## Strings

### What is a String?

- A **string** is an **ordered sequence of characters**.

```
const s = "abc";

s[0]; // "a"
s[2]; // "c"
Index:  0   1   2
        ↓   ↓   ↓
String: a   b   c
```

## Mutable vs Immutable

### Arrays → Mutable

- JavaScript arrays are **mutable**.

- Their elements can be changed after the array is created.

  ```bash
  const arr = ["a", "b", "c"];
  
  arr[2] = "d"; ✅
  ```

Result:

```
["a", "b", "d"]
```

### Strings → Immutable

- JavaScript strings are **immutable**.
- Individual characters cannot be changed directly.

```
const s = "abc";

s[2] = "d"; // ❌
```

- If you want `"abd"`, you need to **create a new string**.

## Why Does Immutability Matter?

- For a small string, creating a new string is not a big concern.
- But if a string contains a large number of characters, creating a new version can be expensive.
- For a string of size `n`, creating a new version can take:`O(n)`

## Time Complexity of array and string operations 

| Operation                  | Array   | String |
| -------------------------- | ------- | ------ |
| Adding to end              | `*O(1)` | `O(n)` |
| Removing from end          | `O(1)`  | `O(n)` |
| Insertion , not from end   | `O(n)`  | `O(n)` |
| Deletion , not from end    | `O(n)`  | `O(n)` |
| Modifying an element       | `O(1)`  | `O(n)` |
| Random Access              | `O(1)`  | `O(1)` |
| Checking if element exists | `O(n)`  | `O(n)` |

Note ➡️ Appending to the end of a arrays is amortized O(1).(**Amortized `O(1)`** → An operation that is **usually `O(1)` but occasionally takes longer due to operations like reallocation and copying; averaged over many operations, its cost is `O(1)`.**)



