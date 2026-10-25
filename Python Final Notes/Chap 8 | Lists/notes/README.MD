# Chap 8 | Lists

## Introduction to Lists

- Collection of items that are stored in a specific order

  ```python
  my_list = [1,2,3]
  print(len(my_list)) # Output: 3 
  print(my_list[0]) # Output : 1 
  ```

- lists are mutable (meaning we can change the values of the elements in the list)

## List Operations

- List within conditional statements

  ```python
  my_list = [1,2,3]
  if my_list:
    print("The list is not empty")
  else:
    print("The list is empty")
  ```

- We can use the `in` and `not in` operator to check whether an element is in or not in the list

  ```python
  my_list = [1,2,3]
  if 2 in my_list:
    print("2 present")
  
    
    
  if 4 not in my_list:
    print("4 not present")
  ```

## List Looping

- Method 1

  ```python
  my_list = [1,2,3,4,5]
  for i in range(len(my_list)):
    print(my_list[i])
  
  ```

- Method 2

  ```python
  my_list = [1,2,3,4,5]
  for element in my_list:
    print(element)
  ```


## List Functions

| Function | What it does ?                                  |
| -------- | ----------------------------------------------- |
| `sum()`  | returns the sum of all the elements in the list |
| `min()`  | returns the smallest element in the list        |
| `max()`  | returns the largest element in the list         |

## List slicing

- List slicing syntax is similar to string slicing

  ```
  my_list = [1,2,3,4,5]
  print(my_list[1:3]) # Output : [2,3]
  print(my_list[:3]) # Output : [1,2,3]
  print(my_list[2:]) # Output : [3,4,5]
  print(my_list[::-1]) # Output : [5,4,3,2,1]
  ```

## Common List Operations

- `append()` ➡️ adds an element to the end of the list

  - Time Complexity ➡️ O(1)

- `pop()` ➡️ removes and returns the last element of the list

  - If the list is already empty, we will get an `IndexError`.
  - We can also pass an integer to `pop()` to remove an element at a specific index.
  - If we `pop(index)` an index that is out of bounds
  - Time Complexity ➡️ O(1)

- `insert()` ➡️ inserts an element at a specified index in the list

  - If the index is too large, the element will be inserted at the end of the list.
  - If the index is negative, the element will be inserted at the beginning of the list.
  - Time Complexity ➡️ O(n) , where n is the number of elements in the list.

- `index()` ➡️ Returns the index of the first occurrence of a specified element in the list.

  - If the element is not in the list, we will get an `ValueError`.
  - Time complexity: O(n), where nn is the length of the list.

- `remove()`: Removes the first occurrence of a specified element from the list.

  - Time complexity: O(n), where nn is the length of the list.

- `extend()`: Adds the elements of another list to the end of the list.

  ```
  my_list = [1, 3, 2, 3]
  
  my_list.index(3) # 1
  
  my_list.remove(3) # [1, 2, 3]
  
  my_list.extend([4, 5]) # [1, 2, 3, 4, 5]
  ```

  - Time complexity: O(m), where m is the length of the list passed to `extend()`.

- `in` operator

  - used to check if an element is in a list,

    ```
    my_list = [1, 2, 3]
    
    if 3 in my_list:
        print("3 is in the list")
    ```

  - Time complexity: O(n), where n is the length of the list.

### List Concat

- Instead of using the `extend()` method there's an even easier way to concatenate two lists in Python. We can use the `+` operator:

  ```
  list1 = [1, 2, 3]
  list2 = [4, 5, 6]
  
  result = list1 + list2 # [1, 2, 3, 4, 5, 6]
  ```

- The only difference between this and the `extend()` method is that the `+` operator creates a new list, while the `extend()` method modifies the original list.

- Time Complexity : O(n+m) where n is the length of one list and m is the length of the other list.

## List Initialization

- If we want to create an empty list of a specific size, this is the easiest way to do it in Python

  ```
  my_list = [0] * 5
  ```

- Time complexity: O(n) where nn is the size of the resulting list.'

## List Clone

- Python provides multiple ways to clone a list. Here are a few ways to do it:

- Using the `copy()` method:

  ```
  original_list = [1, 2, 3]
  cloned_list = original_list.copy()
  ```

- Using the slicing syntax:

  ```
  original_list = [1, 2, 3]
  cloned_list = original_list[:]
  ```

- Using the `list()` constructor:

  ```
  original_list = [1, 2, 3]
  cloned_list = list(original_list)
  ```

- Keep in mind, that if you have a list of objects, the above methods will not create [deep copies](https://developer.mozilla.org/en-US/docs/Glossary/Deep_copy) of the elements within the list. In this case we have a list of integers, which are primitive types, so we don't need to worry about that. But if you had a list of lists, for example, you would need to use the `copy.deepcopy()` method to create a deep copy.

- Using `copy.deepcopy()` for deep copies:

  ```
  import copy
  
  original_list = [[1, 2], [3, 4]]
  
  cloned_list = copy.deepcopy(original_list)
  ```

- Time complexity: O(n) where n is the length of the list being copied.

## List Comprehension

- List Comprehension allows us to create lists in a concise way

- Example ➡️

  ```
  my_list = [i for i in range(5)]
  
  print(my_list) # [0, 1, 2, 3, 4]
  ```

- This is called **list comprehension**. In the above example, we have a `for` loop inside the square brackets. The loop iterates over the range of numbers from `0` to `4`. Before the loop we place the expression `i` which is the value we want to add to the list. This is a very concise way to create a list.

- Another Example ➡️

  ```
  arr1 = [1, 2, 3]
  arr2 = [4, 5, 6]
  
  result = [i + j for i, j in zip(arr1, arr2)]
  ```

  - Above we have two lists `arr1` and `arr2`. We use the `zip()` function to iterate over both lists at the same time. We then add the elements of both lists together and create a new list. The expression `i + j` is the value we want to add to the list.

- Third Example ➡️

  ```
  arr = [1, 2, 3, 4, 5]
  
  result = [i for i in arr if i % 2 == 0]
  ```

  - In the above example, we have a list `arr`. We iterate over the list and add the element to the new list only if it's even

- Time complexity: O(n) where n is the number of times the loop within the list comprehension runs.