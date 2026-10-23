# Lists

## Introduction to Lists

- Collection of items that are stored in a specific order 

  ```python
  my_list = [1,2,3]
  print(len(my_list)) # Output: 3 
  print(my_list[0]) # Output : 1 

- lists are mutable (meaning we can change the values of the elements  in the list)

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

## List Append 

- adds new elements to the end of a list using the `append()` function 

  ```python
  my_list = [1,2,3]
  my_list.append(4)
  
  print(my_list) #Output : [1,2,3,4]
  ```

## List pop 

- remove elements from a list using the `pop()` function 

  ```python
  my_list = [1,2,3]
  my_list.pop()
  print(my_list) # Output : [1,2]
  ```

- we can also specify an index to remove a specific element as shown below 

  ```python
  my_list = [1,2,3]
  my_list.pop(0)
  print(my_list) # Output : [2,3]
  ```

## List Find 

- We can find the index of an element in a list using the `index()` function (first element) 

  ```python
  my_list = [1,2,3,4,5,3]
  print(my_list.index(3)) # Output : 2 
  ```

## List slicing 

- List slicing syntax is similar to string slicing 

  ```python 
  my_list = [1,2,3,4,5]
  print(my_list[1:3]) # Output : [2,3]
  print(my_list[:3]) # Output : [1,2,3]
  print(my_list[2:]) # Output : [3,4,5]
  print(my_list[::-1]) # Output : [5,4,3,2,1]
  ```

  