# Hashing 

**Q**: What is a Data Structure ?

**Solution**:

A data structure is a format for organizing data in an efficient way. In practical terms, we can split data structures into two things: the interface and the implementation.

The **interface** is like a contract that specifies how we can interact with the data structure - what operations we can perform on it, what inputs it expects, and what outputs we can expect. Basically, it's how we use the data structure.

The **implementation** is the code that actually makes the data structure work

---

**Q**: What is a hash function ? 

**Solution**:

A hash function is a function that takes an input and deterministically converts it to an integer that is less than a fixed size set by the programmer. Inputs are called **keys** and the same input will always be converted to the same integer.

Example of a hashing function ➡️

```js  
function hash(key, x) {
    let total = 0;

    for (let i = 0; i < key.length; i++) {
        // Convert character to alphabet position
        // a -> 1, b -> 2, ..., z -> 26
        let value = key.charCodeAt(i) - 'a'.charCodeAt(0) + 1;

        // Multiply by position (index + 1)
        total += value * (i + 1);
    }

    // Keep the result between 0 and x - 1
    return total % x;
}
```

---

**Q**: Why do we need a hash function , and how does it help create a hash map  ?

**Solution**:

 Arrays provide **O(1) random access**, but they have an important limitation: their indices must be **integers**.

A **hash function** solves this by taking a key (such as a string) and **deterministically converting it into an integer**.

When we combine a **hash function with an array**, we get a **hash map**.

```bash
Key → Hash Function → Integer Index → Array → Value
```

This allows us to use **keys instead of integer indices** to access values efficiently.

**Q**: What is an ordered data structure and what is an unordered data structure ? 

**Solution**:

| ordered data structure        | unordered data structure        |
| ----------------------------- | ------------------------------- |
| insertion order is remembered | insertion order is not relevant |

**Q**: Time Complexity of various hash-maps operations 

**Solution**:

| Operations                             | Time Complexity | JS implantation |
| -------------------------------------- | --------------- | --------------- |
| add a key-value pair                   | O(1) avg        |                 |
| remove a key-value pair                | O(1) avg        |                 |
| update the value associated with a key | O(1) avg        |                 |
| check if a key exists                  | O(1) avg        |                 |
| access the value associated with a key | O(1) avg        |                 |
| Find length /Number of elements        | O(1)            |                 |
| Iterate over elements                  | O(1)            |                 |

Note ➡️ 

- In general hash maps is an unordered data structure and whether iteration preserves insertion order depends on the language and implementation .But Javascripts `Map` does preserve insertion order
- Hash Map operations are generally O(1) on avergae , not guranteed O(1) .In the worst case operation can become O(n) due to collisions

**Q**: Why can hash tables use more memory than arrays?

**Solution**:

- Hash tables use an **underlying array** with a certain capacity.
- The capacity can be **much larger than the number of elements**, causing **unused space**.
- When a hash table resizes, existing keys must be **re-hashed**, making resizing more expensive than a dynamic array.
- Therefore, hash tables trade **extra memory** for **fast average O(1) operations**.

**Q**: Is a hash map operation always `O(1)`?

**Solution**: 

When we say a hash map operation is **`O(1)`**, we are talking about the **number of elements in the hash map**.

For example : 

```js
map.get("apple");
```

There are two things happening:

1. **Hash the key** `"apple"` to determine where it should be stored.
2. **Access that location** in the hash table to get the value.

The second step is **`O(1)` on average** because we can directly access the calculated location.

However, the **hashing itself depends on the size of the key**.

For a string with `m` characters:

```bash
Hashing the key → O(m)
Accessing the hash table → O(1) average
```

**Q**: What is a Set , and how is it different from a Hash Map ? 

**Solution**::

- A Set is a data structure used to store **unique elements**.

- It uses a similar hashing mechanism to a hash map, but there is one major difference:

  ```bash
  Hash Map:
  Key → Value
  
  Set:
  Key
  ```

- A Set is useful when you **only care whether an element exists**, not about storing a value associated with it.

**Q**: Set Operations and there time complexity 

**Solution**:

| Set Operations                | Time Complexity |
| ----------------------------- | --------------- |
| Adding                        | O(1)            |
| Removing                      | O(1)            |
| Checking if an element exists | O(1)            |

**Q**: Hashmaps js implementation 

```js
// Declaration: use the Map object
let hashMap = new Map();

// If you want to initialize it with some key value pairs, use the following syntax:
let hashMap = new Map([
    [1, 2],
    [5, 3],
    [7, 2]
]);

// Checking if a key exists: use .has()
hashMap.has(1); // true
hashMap.has(9); // false

// Accessing a value given a key: use .get()
hashMap.get(5); // 3

// Adding or updating a key: use .set()
// If the key already exists, the value will be updated
hashMap.set(5, 6);

// If the key doesn't exist yet, the key value pair will be inserted
hashMap.set(9, 15);

// Deleting a key: use .delete()
hashMap.delete(9);

// Get size
hashMap.size; // 3

// Iterate over the key value pairs: use the following code
for (const [key, value] of hashMap) {
    console.log(key + " " + value);
}
```



