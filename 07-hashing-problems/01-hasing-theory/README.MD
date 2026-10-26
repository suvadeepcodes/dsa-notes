# Hashing Theory

## Data Structure

- Data Structure ➡️ A way of organizing and storing data efficiently.
- Interface ➡️ Defines what operations a data structure supports, including their inputs and outputs.
  - Example: list → `append()`, .
- Implementation ➡️ Defines how operations work internally, including memory allocation, resizing, and element rearrangement.
- Note ➡️
  - Interface = What a data structure does.
  - Implementation = How it does it.

## Hash Function

- Hash Function ➡️ Converts a key into an integer within a fixed range say \([0, x-1]\).

- Properties ➡️

  - Deterministic: Same input always produces the same hash.
  - Keys are the inputs to the hash function
  
- Example hash algorithm for a string containing letters of the English alphabet:➡️  

  - Algorithm: 

    - Initialize `total = 0`.
    - Convert each character to its alphabet position (`a = 1`, `b = 2`, …, `z = 26`).
    - Multiply each value by its 1-based string position and add it to `total`.
    - Return `total % x` to keep the hash value within the range.

  - Python code ➡️

    ```python
    def hash_string(s, x):
        total = 0
        for i, char in enumerate(s):
            value = ord(char) - ord('a') + 1
            total += value * (i + 1)
        return total % x
    ```

## Whats the point of hash function ? 

- Hash Map (`dict` in Python) ➡️ A data structure that stores key-value pairs, created by combining a hash function with an array.
- Array vs Hash Map ➡️
  - Array → Maps integer indices to values; fixed size.
  - Hash Map → Maps keys to values; keys can be almost anything.
- Key Properties ➡️
  - Keys are typically immutable; values can be anything.
  - Supports insertion, deletion, updating, and key-existence checks in average \(O(1)\) time.
  - Allows iteration over keys and values.
- Importance in DSA ➡️ Hash maps can significantly improve algorithm efficiency, often reducing time complexity by a factor of \(O(n)\).
- Ordering ➡️ An ordered data structure remembers insertion order; an unordered data structure does not treat insertion order as relevant.
- HashMap in Python is an unordered data structure

## HashMap Disadvantages

- Overhead: Hashing keys adds constant-factor costs, which can make hash maps slower for small inputs.
- Space: May use more memory than arrays due to unused capacity.
- Resizing: Can be expensive because existing keys may need to be re-hashed.
- Complexity Note ➡️ Hash map operations are typically \(O(1)\) relative to the number of stored elements \(n\). However, hashing a string of length \(m\) takes \(O(m)\) time.

## Hash Set

- Set ➡️ A hash-based data structure that stores unique elements without mapping them to values.

- Operations ➡️ Add, remove, and check whether an element exists — average \(O(1)\) time.

- Key Properties ➡️

  - Duplicate elements are ignored.

  - Does not track element frequency.

  - Adding the same element 100 times stores it only once.

- Note ➡️ A set is essentially a hash map that stores only keys, without associated values.

## Arrays as Hash Map Keys

- Problem ➡️ Arrays are mutable, so they cannot be used directly as Python dictionary keys.

- Solution ➡️ Convert the array into an immutable tuple using `tuple(arr)`.

  ```python
  arr = [1, 51, 163]
  key = tuple(arr)  # (1, 51, 163)
  
  d = {key: "value"}
  ```

- Alternative ➡️ Convert the array into a delimited string, e.g., `[1, 51, 163]` → `"1,51,163"`.

