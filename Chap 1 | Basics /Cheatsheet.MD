# Chap 1 | Basics

## Big O — Cheatsheet

### Variables

- Variables represent **values that affect the algorithm** and can change between inputs.
- `n` → Usually represents the **input size**.

### How Big O Works

- Operations increase with `n` → **`O(n)`**
- Operations increase with `n²` → **`O(n²)`**
- Operations increase with `log n` → **`O(log n)`**
- Operations stay the same → **`O(1)`**

### Rules

- **Ignore constants:** `O(5n) = O(n)`
- **Keep dominant term:** `O(n² + n) = O(n²)`
- Analyze as **`n → ∞`**.
- Usually report the **Worst Case**.

### Logarithmic Complexity

- `O(log n)` → Input/search space is **reduced by a percentage at every step**.
- Binary Search → **`O(log n)`**
- Efficient sorting algorithms → **`O(n · log n)`**

### Space Complexity

- **Input space is not counted.**
- **Output space is usually not counted**, unless asked.
- Extra memory that grows with input size **is counted**.

### Recursion 

- **Recursion** → Function calls itself.
- **Base Case** → Stops recursion.
- **Recursive Case** → Calls itself with changed input.
- **Pattern:** Big problem → Smaller problem → Base case → Combine.



