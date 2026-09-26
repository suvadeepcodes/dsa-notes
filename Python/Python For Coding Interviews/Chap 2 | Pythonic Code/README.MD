# Pythonic Code

## Unpacking

```python
point1 = [0, 0]
point2 = [2, 4]

x1, y1 = point1 # x1 = 0, y1 = 0
x2, y2 = point2 # x2 = 2, y2 = 4
```

- If we attempt unpacking with not enough variables on the left-side, we will get a `ValueError`.

  ```python
  x, y = [0, 0, 0] # ValueError: too many values to unpack (expected 2)
  ```

- Unpacking also works with tuples and sets with the same syntax.

## Loop Unpacking

- We can also use unpacking in loops to iterate over a list of lists. This is useful when we know the size of the inner lists and want to unpack them into variables.

  ```python
  points = [[0, 0], [2, 4], [3, 6], [5, 10]]
  
  for x, y in points:
      print(f"x: {x}, y: {y}")
  ```

## Enumerate 

- Suppose we wanted to loop over an array and we needed to access both the index and the element at that index. This is simple to accomplish:

  ```python
  nums = [2, 7, 9, 2]
  
  for i in range(len(nums)):
      n = nums[i]
      print(i, n)
  ```

- But the Pythonic way to do this is to use the `enumerate()` function:

  ```python
  nums = [2, 7, 9, 2]
  
  for i, n in enumerate(nums):
      print(i, n)
  ```

- The `enumerate()` function returns a tuple of the index and the element at that index. We can unpack this tuple into two variables in the for loop.

## Zip

- Python provides an easy way to iterate over multiple lists at the same time using the `zip()` function. The `zip()` function takes multiple lists as arguments and returns an iterator of tuples. Each tuple contains an element from each list.

- This is useful when we have multiple lists of the same length and want to iterate over them together.

  ```python
  names = ['Alice', 'Bob', 'Charlie', 'David']
  scores = [90, 85, 88, 92]
  
  for name, score in zip(names, scores):
      print(f"{name} scored {score}")
  ```

- Time and Space Complexity 

  - Time complexity: O(1)

    - The `zip()` function returns an iterator at the beginning of the input lists, so it doesn't traverse the entire lists.

    Space complexity: O(1)

    - The `zip()` function returns an iterator so it doesn't actually create a new list of tuples in memory.

## Inequality

- Python allows us to take a small shortcut when making multiple comparisons.

- The following code:

  ```python
  x = 5
  
  if 0 < x and x < 10:
      print('x is between 0 and 10')
  ```

- is equivalent to:

  ```python
  x = 5
  
  if 0 < x < 10:
      print('x is between 0 and 10')
  ```

## Min Max Shortcut

- Use `max()` to enforce a **minimum value** and `min()` to enforce a **maximum value**.

  ```python
  x = max(0, x)      # x >= 0
  x = min(100, x)    # x <= 100
  ```

