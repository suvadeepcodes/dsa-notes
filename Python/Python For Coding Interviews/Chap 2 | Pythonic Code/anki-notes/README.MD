# Pythonic Code (Anki Notes)

Anki Tag ➡️ 02-pythonic-code

**Q1**: What is unpacking in Python ? 

**Solution**:

- Assigning the elements of a collection to multiple variables using the same syntax.

  ```python
  point1 = [0, 0]
  x1, y1 = point1  # x1 = 0, y1 = 0
  ```

  

**Q2**: What happens if the number of variables doesn't match the number of values during unpacking?

**Solution**:

- A `ValueError` is raised.

```python
x, y = [0, 0, 0]
# ValueError: too many values to unpack (expected 2)
```

**Note:** Unpacking also works with tuples and sets.

**Q**: How can unpacking be used in loops with a list of lists?

**Solution**:

We can unpack each inner list directly into variables while iterating.

```python
points = [[0, 0], [2, 4], [3, 6], [5, 10]]

for x, y in points:
    print(f"x: {x}, y: {y}")
```

Output: 

```bash
x: 0, y: 0
x: 2, y: 4
x: 3, y: 6
x: 5, y: 10
```

**Q**: Loop over the array and print both the index and the element at that index using the pythonic way 

```python
nums = [2, 7, 9, 2]
```



**Solution**:

```python
nums = [2, 7, 9, 2]

for i, n in enumerate(nums):
    print(i, n)
```

- The `enumerate()` function returns a tuple of the index and the element at that index. We can unpack this tuple into two variables in the for loop.

**Q**: Loop over both the lists (names and scores) and print each element at each index in both the lists

```python
names = ['Alice', 'Bob', 'Charlie', 'David']
scores = [90, 85, 88, 92]

```

**Solution**:

```python
names = ['Alice', 'Bob', 'Charlie', 'David']
scores = [90, 85, 88, 92]

for name, score in zip(names, scores):
    print(f"{name} scored {score}")
```

- Python provides an easy way to iterate over multiple lists at the same time using the `zip()` function. The `zip()` function takes multiple lists as arguments and returns an iterator of tuples. Each tuple contains an element from each list.
- This is useful when we have multiple lists of the same length and want to iterate over them together.

**Q**: What is the Time and Space Complexity of `zip()` function ? 

**Solution**:

- Time and Space Complexity : 
  - Time ➡️ O(1)
  - Space ➡️O(1)

**Q**: Convert the following code to pythonic code ?

```python
x = 5

if 0 < x and x < 10:
    print('x is between 0 and 10')
```

**Solution**:

The pythonic equivalent is ➡️

```python 
x = 5

if 0 < x < 10:
    print('x is between 0 and 10')
```

**Q**: How can `max()` and `min()` be used as a shortcut to enforce minimum and maximum values?

**Solution**:

```python
x = max(0, x)      # x >= 0
x = min(100, x)    # x <= 100
```

- `max()` → enforces a **minimum value**

- `min()` → enforces a **maximum value**

