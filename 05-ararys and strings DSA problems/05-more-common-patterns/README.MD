# More Common Patterns

---

## String Building in js 

When a string is modified, the original string cannot be changed directly. A new string needs to be created and creating a new string is O(n)

Suppose you're doing:

```js
let result = "";

for (let char of s) {
    result += char;
}
```

Conceptually, you're doing:

```bash
""       → copy 0 chars
"a"      → copy 1 char
"ab"     → copy 2 chars
"abc"    → copy 3 chars
"abcd"   → copy 4 chars
...
```

So for `n` characters:

```bash
1 + 2 + 3 + ... + n
```

which is: O(n²)

**Array Approach** :

instead : 

```js 
let arr = [];

for (let i = 0; i < s.length; i++) {
    arr.push(s[i]);
}

return arr.join("");
```

We do : 

```bash
arr.push() → O(1)
arr.push() → O(1)
arr.push() → O(1)
...
```

for n charcters : n × O(1) = O(n)

Then `arr.join("")` takes O(n) because it has to create the final string 

Therefore: 

```bash
O(n) + O(n)
= O(2n)
= O(n)
```

So Remember this pattern : 

```js 
// Potentially O(n²)
let result = "";
result += char;

// Potentially O(n²)
let result = "";
result += char;
```

---

### Subarrays/substrings, subsequences, and subsets

- **Subarray / Substring**:
  - A **contiguous** part of an array or string.
- Subsequence
  - Elements that **maintain their original order**, but **don't need to be contiguous**.
- Subset
  - A collection of elements where **order doesn't matter** and elements **don't need to be contiguous**.