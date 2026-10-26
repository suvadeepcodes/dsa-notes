# Introduction to Recursion

### What is Recursion?

- **Recursion** is a problem-solving method.
- In code, recursion is implemented using a **function that calls itself**.
- **Iterative algorithms** use loops (`for`, `while`) to repeat logic.
- **Recursive algorithms** use function calls to repeat logic.

### Recursive Function

- A recursive function generally has two parts:

  - **Base Case** → Condition that **stops the recursion**.

  - **Recursive Case** → The part where the function **calls itself** with a changed input.

### Example

```javascript
function fn(i) {
    if (i > 10) {
        return; // Base Case
    }

    console.log(i);
    fn(i + 1); // Recursive Case
}

fn(1);
```

### Base Case

- The **base case** determines when the recursion should stop.
- Without a base case, the function will keep calling itself indefinitely.

```javascript
if (i > 10) {
    return;
}
```

### Recursive Case

- The **recursive case** is where the function calls itself.
- Usually, the input is changed so that eventually the **base case** is reached.

```javascript
fn(i + 1);
```

## Understanding Recursive Call Execution

### How Recursive Calls Execute

- Recursive calls **cascade on top of each other**.
- When a function calls itself, the current function call **waits** until the new call returns.
- Once the **base case** is reached, the calls return in **reverse order**.

### Example

```js
function fn(i) {
    if (i > 3) {
        return;
    }

    console.log(i);
    fn(i + 1);
    console.log("End of call where i =", i);
    return;
}

fn(1);
```

### Output

```
1
2
3
End of call where i = 3
End of call where i = 2
End of call where i = 1
```

### Execution Flow

```
fn(1)
  ↓
fn(2)
  ↓
fn(3)
  ↓
fn(4) → Base Case → return
  ↑
fn(3) continues → print "End of call where i = 3"
  ↑
fn(2) continues → print "End of call where i = 2"
  ↑
fn(1) continues → print "End of call where i = 1"
```

- `fn(1)` calls `fn(2)` and waits.
- `fn(2)` calls `fn(3)` and waits.
- `fn(3)` calls `fn(4)`.
- `fn(4)` reaches the **base case** and returns.
- `fn(3)` continues from the line after the recursive call.
- Then `fn(2)` continues.
- Finally, `fn(1)` continues.

## Recursion example

### Breaking Problems into Subproblems

- Recursion is useful when a problem can be broken into **smaller subproblems**.
- We solve the smaller subproblems recursively and **combine their solutions** to solve the original problem.

### Example: Fibonacci Numbers

- Fibonacci sequence:

  ```bash
  0, 1, 1, 2, 3, 5, 8, ...
  ```

- Each number is the sum of the previous two numbers.

  ```bash
  F(n) = F(n - 1) + F(n - 2)
  ```

- This is called a **recurrence relation**.

- Base Cases

  - `F(0) = 0`

  - `F(1) = 1`

- Recursive Function: 

  ```js
  function F(n) {
      if (n <= 1) {
          return n;
      }
  
      let oneBack = F(n - 1);
      let twoBack = F(n - 2);
  
      return oneBack + twoBack;
  }
  ```

- Breaking the Problem Down

- To calculate `F(3)`:

  ```bash
  F(3)
  ├── F(2)
  │   ├── F(1) → 1
  │   └── F(0) → 0
  │
  └── F(1) → 1
  
  F(2) = 1 + 0 = 1
  F(3) = 1 + 1 = 2
  ```

- Original problem → `F(3)`
- Break it into smaller problems → `F(2)` and `F(1)`.
- `F(2)` is further broken into → `F(1)` and `F(0)`.
- Base cases provide the answers.
- Combine the answers to get the **original answer**.

