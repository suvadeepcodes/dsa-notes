# Introduction to Big O

## Algorithms

### What is an algorithm ?

- An **algorithm** is a **step-by-step set of instructions** used to solve a problem.
- It takes an **input** and produces an **output**.
- Think of an algorithm as a **recipe for a computer**.

### Example: Find the largest number in an array `nums`

- Algorithm
  - Initialize `maxNum` with the first element of `nums`.
  - Traverse the array.
  - If `num > maxNum`, update `maxNum = num`.
  - Return `maxNum`.

### Properties of an algorithm

- **Deterministic**
  - Same input → **same output** every time.
  - No randomness.
- **Correct**
  - Must produce the correct answer for **every valid input**.
- **Handles Edge Cases**
  - The algorithm should work for all inputs allowed by the problem.

------

## Big O

- **Big O** is a notation used to describe the **computational complexity** of an algorithm.
- Computational complexity has two parts:
  - **Time Complexity** → As the input size grows, how much longer does the algorithm take to complete?
  - **Space Complexity** → As the input size grows, how much more memory does the algorithm use?

------

## How Complexity Works

### Variables in Complexity

- Complexity is described using a **mathematical function**.
- The variables in the function should represent values that:
  - **Change between different inputs**
  - **Affect the algorithm**

### Common Variable: `n`

- `n` usually represents the **length of an input array or string**.
- Example: For `nums`:
  - `n = length of nums`
- A longer `nums` means more elements to process, which can increase the algorithm's running time.
- `n` is not mandatory. The programmer decides which variables represent which values.
- `n` is simply the commonly accepted standard.

### Multiple Variables

- We can define multiple variables when the input has multiple relevant sizes.
- Example: If there are two arrays:
  - `n` = length of the first array
  - `m` = length of the second array
- This can result in a complexity such as `O(n · m)`.

### LeetCode Convention

- Although larger integers technically take more time for operations such as addition, multiplication, or printing, we **typically ignore this difference**.
- For an array of integers, we generally use `n` to represent the **length of the array**, rather than introducing a variable for the values of the integers.

### Writing Big O

- Complexity is written by wrapping the function in a capital **`O`**:
  - `O(n)`
  - `O(n²)`
  - `O(2ⁿ)`
  - `O(log n)`
  - `O(n · m)`

------

## Calculating Complexity

### What does Complexity Measure ?

- **Time complexity:** Roughly measures the **number of operations** an algorithm performs relative to the input size.
- **Space complexity:** Roughly measures the **amount of memory** an algorithm uses relative to the input size.

### Example: Finding the largest element in `nums`

- `n = length of nums`
- We iterate over all `n` elements.
- Therefore, time complexity = **`O(n)`**.

Note ➡️

- `n = 10` → approximately 10 iterations
- `n = 10,000,000,000` → approximately 10 billion iterations
- Complexity is **not an exact count of operations**.
- We care about **how the number of operations changes as the input size changes**.

------

## Rules for Calculating Complexity

### Ignore Constants

- We ignore **constant factors** in Big O notation.

```text
O(9999999n) = O(8n) = O(n)
```

- Example:
  - Algorithm A ➡️ `n` operations
  - Algorithm B ➡️ `5n` operations
- When `n` increases, both algorithms' operations increase **linearly** with `n`.
- We care about **how complexity grows as the input grows**, not the constant difference between them.
- Therefore, both algorithms are **`O(n)`**.

### Keep the Dominant Term

- When analyzing complexity, consider the variables as they **tend to infinity**.
- For terms involving the **same variable**, keep only the **most significant term**.
- Example:

```text
O(2n + n² - 500n) = O(n²)
```

- As `n` becomes very large, `n²` grows much faster than `n`.
- Example:

```text
O(n + 500) = O(n)
```

- As `n` becomes very large, the constant `500` becomes insignificant.

------

## Constant Complexity

- `O(1)` is called **constant time** or **constant space**.
- The algorithm always uses the **same amount of resources**, regardless of input size.

```text
O(5000000) = O(1)
```

Note ➡️

- `O(1)` does not necessarily mean that an algorithm is fast.
- It means that its resource usage is **independent of the input size**.

------

## Best, Average & Worst Case

- There are three common cases:
  - **Best Case**
  - **Average Case**
  - **Worst Case**
- Some algorithms have the same complexity in all three cases.
- Some algorithms have different complexities for different cases.
- If only one case is used to represent an algorithm's complexity, **use the worst case**.

---

## Analyzing Time Complexity

### Case 1: Single Loop — `O(n)`

```js
Given an integer array arr with length n
for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

- `console.log(arr[i])` → **`O(1)`**

- The loop runs **`n` times**.

- Therefore:

  ```
  Time Complexity = O(1 × n) = O(n)
  ```

------

### Case 2: Nested Loop with Constant Inner Loop — `O(n)`

```
Given an integer array arr with length n:
for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < 500000; j++) {
        console.log(arr[i]);
    }
}
```

- `console.log(arr[i])` → **`O(1)`**

- Inner loop runs **500,000 times**.

- `500,000` is a constant → **`O(500000) = O(1)`**

- Therefore, each outer loop iteration costs **`O(1)`**.

- Outer loop runs **`n` times**.

- Therefore:

  ```bash
  Time Complexity = O(1 × n) = O(n)
  ```

------

### Case 3: Nested Loops — `O(n²)`

```
//Given an integer array arr with length n
for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length; j++) {
        console.log(arr[i] * arr[j]);
    }
}
```

- Multiplication and `console.log()` → **`O(1)`**

- Inner loop runs **`n` times** → each outer iteration costs **`O(n)`**.

- Outer loop runs **`n` times**.

- Therefore:

  ```bash
  Time Complexity = O(n × n) = O(n²)
  ```

------

### Case 4: Multiple Independent Loops — `O(n + m)`

```
// Given integer arrays arr with length n and arr2 with length m:

for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}

for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}

for (let i = 0; i < arr2.length; i++) {
    console.log(arr2[i]);
}
```

- First two `for` loops → **`O(n)`** each.

- Third `for` loop → **`O(m)`**.

- Therefore:

  ```bash
  Time Complexity = O(n + n + m)
  = O(2n + m)
  = O(n + m)
  ```

------

### Case 5: Dependent Nested Loops — `O(n²)`

```
// Given an integer array arr with length n:
for (let i = 0; i < arr.length; i++) {
    for (let j = i; j < arr.length; j++) {
        console.log(arr[i] + arr[j]);
    }
}
```

- The inner loop depends on the current iteration of the outer loop.

- Number of inner loop iterations:

  ```bash
  n + (n - 1) + (n - 2) + ... + 1
  ```

- This is the sum:

  ```bash
  1 + 2 + 3 + ... + n
  = n(n + 1) / 2
  = (n² + n) / 2
  ```

- Ignore the constant and lower-order term:

  ```bash
  O((n² + n) / 2) = O(n²)
  ```

---

## Logarithmic Complexity 

- `O(log n)` is called **logarithmic time** and is **extremely fast**.
- `O(n · log n)` is also reasonably fast and is the time complexity of efficient sorting algorithms.
- `O(log n)` usually means the input/search space is **reduced by a percentage at every step**.

---

## Analyzing Space complexity 

- Initializing variables such as **arrays or strings** requires allocating memory.
- We **do not count the space used by the input**.
- We usually **do not count the space used by the output**, unless the interviewer asks us to.

### Case 1 : No Extra Data Structure — `O(1)`

```js
// Given an integer array "arr" with length n
for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

- The only extra space used is the loop variable `i`.
- `i` is a single integer, so its space is **constant** relative to `n`.
- Therefore : `Space Complexity = O(1)`

### Case 2 : Extra Array of Size `n` — `O(n)`

```js
// Given an integer array "arr" with length n

let doubledNums = [];

for (let i = 0; i < arr.length; i++) {
    doubledNums.push(arr[i] * 2);
}
```

- `doubledNums` stores **`n` integers** at the end of the algorithm.
- Therefore: `Space Complexity = O(n)`

### Case 3 : Constant Fraction of Input — `O(n)`

```js
// Given an integer array "arr" with length n

let nums = [];
let oneHundredth = Math.floor(arr.length / 100);

for (let i = 0; i < oneHundredth; i++) {
    nums.push(arr[i]);
}
```

- `nums` stores the **first 1% of the numbers** in `arr`.
- 1% of n = n / 100
- Therefore : `Space Complexity = O(n / 100) = O(n)`

### Case 4 : 2D Array of Size `n × m` — `O(n · m)`

```js
// Given integer arrays "arr" with length n and "arr2" with length m

let grid = Array.from({ length: arr.length }, () => 
    new Array(arr2.length)
);

for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr2.length; j++) {
        grid[i][j] = arr[i] * arr2[j];
    }
}
```

- `grid` has dimensions **`n × m`**.
- Therefore, it stores **`n · m`** elements.
- Hence : `Space Complexity = O(n · m)`





