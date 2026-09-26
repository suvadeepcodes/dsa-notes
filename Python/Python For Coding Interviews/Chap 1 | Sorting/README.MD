# Chap 1 | Sorting

## `.sort()` 

- sorts the elements (if elements) in ascending order in-place
- for list of strings it sorts them in lexicographical order 

  ```python
  elements = [5, 3, 6, 2, 1]
  
  elements.sort()
  
  print(elements) # [1, 2, 3, 5, 6]
  
  strings = ["grape", "apple", "banana", "orange"]
  
  strings.sort()
  
  print(strings) # ['apple', 'banana', 'grape', 'orange']
  ```

  

- Time and Space Complexity 
  - Time : O(nlogn) , n ➡️ number of elements in the list 
  - Space : O(n) , n ➡️ number of elements in the list

- `.sort()` function signature 

  ```python
  def sort(key=None, reverse=False) -> None:
  ```

  - `key` parameter allows us to customize the sorting order 
  - `reverse` parameter is a boolean value that determines whether the list should be sorted in *descending order*. By default, it is set to `False`.

- sort a list in descending order we can set the `reverse` parameter to `True``

  ```python
  elements = [5, 3, 6, 2, 1]
  
  elements.sort(key=None, reverse=True)
  
  print(elements) # [6, 5, 3, 2, 1]
  ```

  - We can actually omit the `key` parameter and only pass the `reverse` parameter, by using a feature of Python called *keyword arguments*. 

    ```python
    elements.sort(reverse=True)
    ```

- `key` parameter 

  - key parameter allows to customize the sorting order , the key parameter returns a value to be used for sorting 

    ```python 
    def get_word_length(word: str) -> int:
        return len(word)
    
    words = ["apple", "banana", "kiwi", "pear", "watermelon", "blueberry", "cherry"]
    
    words.sort(key=get_word_length)
    
    print(words) # ['kiwi', 'pear', 'apple', 'banana', 'cherry', 'blueberry', 'watermelon']
    ```

- Lambda Function

  - We can use a lambda function to customise the sorting of a python list

  - Lambda function to sort a list of words by their length 

    ```python
    words = ["apple", "banana", "kiwi", "pear", "watermelon", "blueberry", "cherry"]
    
    words.sort(key=lambda word: len(word))
    
    print(words) # ['kiwi', 'pear', 'apple', 'banana', 'cherry', 'blueberry', 'watermelon']
    ```

  - Synatax

    - The keyword `lambda`.
    - The input variable `word`. We can use any variable name here.
    - The colon `:`, after which we define the function body.
    - The expression `len(word)`, which is the return value of the function.

## `.sorted()`

- `.sorted()` returns a new list with the elements sorted in the specified order. The original list remains unchanged.

- For the most part, it's similar to the `sort()` method, but it returns a new list instead of modifying the original list.

  ```python
  words = ["kiwi", "pear", "apple", "banana", "cherry", "blueberry"]
  
  sorted_words = sorted(words)
  
  print(sorted_words) # ['apple', 'banana', 'blueberry', 'cherry', 'kiwi', 'pear']
  
  
  numbers = [5, -3, 2, -4, 6, -2, 4]
  
  sorted_numbers = sorted(numbers, reverse=True)
  
  print(sorted_numbers) # [6, 5, 4, 2, -2, -3, -4]
  
  ```

  

