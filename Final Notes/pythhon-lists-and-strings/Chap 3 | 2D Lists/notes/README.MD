# Chap 14 | 2D Lists

## Multi-Dimensional List

- A nested list is a list that contains other lists. This allows us to create multi-dimensional lists, which are lists of lists.

  ```python
  nested_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
  ```

- This is a 2D list, where each element is a list of integers. Thus, `nested_list[0]` and `nested_list[1]` are lists themselves, and *not* integers. Perhaps it's better visualized like this:

  ```python
  nested_list = [
      [1, 2, 3],
      [4, 5, 6],
      [7, 8, 9]
  ]
  
  print(nested_list[0])  # [1, 2, 3]
  print(nested_list[1])  # [4, 5, 6]
  print(nested_list[2])  # [7, 8, 9]
  ```

- If we want to access elements in a list, we can do so by chaining the indices:

  ```python
  print(nested_list[0][0])  # 1
  
  print(nested_list[2][2])  # 9
  
  print(nested_list[1][2])  # 6
  ```

- Iterating over a nested_list

  ```python
  nested_list = [[1], [2, 3], [4, 5, 6]]
  
  for sublist in nested_list:
      for element in sublist:
          print(element)
  ```

## 2D Grid

- It's common to represent a 2D grid as a list of lists in Python. For example, a 2x3 grid can be represented as:

  ```python
   grid = [
      [0, 0, 0],
      [0, 0, 0]
  ]
  
  rows = len(grid)    # 2
  cols = len(grid[0]) # 3
  ```

- In this example, the variable `grid` is a list of lists. The variable `rows` is the number of rows in the grid, and the variable `cols` is the number of columns in the grid. We assume that each sub-list in the grid has the same length, which is usually the case for a 2D grid in algorithm problems.

## Nested List Comprehension

- It's common to need to initialize a 2-D list of a given size, especially a 2-D grid. Suppose we wanted to declare a 2x3 grid of zeros. You might be tempted to try this:

  ```python
  grid = [[0] * 3] * 2
  
  print(grid) # [[0, 0, 0], [0, 0, 0]]
  ```

- At first it seems correct. We create a list of size 3 with `[0] * 3`. We add it to a list, and multiply the result by 2. However, this code will not work as expected. The issue is that the inner list is a reference to the same list object. This means that if we change one of the inner lists, all the inner lists will change as shown below.

  ```python
  grid = [[0] * 3] * 2
  
  grid[0][0] = 1
  
  print(grid) # [[1, 0, 0], [1, 0, 0]]
  ```

- A better way to initialize a 2-D list is to use a **nested list comprehension**:

  ```python
  grid = [[0 for i in range(3)] for j in range(2)]
  
  grid[0][0] = 1
  
  print(grid) # [[1, 0, 0], [0, 0, 0]]
  ```

- We create the inner list of zeroes with list comprehension. Then we use that list for the outer list with list comprehension again. This works as expected because each inner list is a separate object.But there's a more concise solution you may prefer:

  ```python
  grid = [[0] * 3 for _ in range(2)]
  ```

- This code is equivalent to the previous code but uses less characters. We create a list of zeroes with `[0] * 3` and use it for the outer list with list comprehension. Since the variable in the for loop is not used, we use an underscore `_` to indicate that it is a throwaway variable. This is a common convention in Python.

- Time Complexity :

  - To initialze a 2-D grid of size `n x m` with a given value, the time complexity is `O(n∗m)`.