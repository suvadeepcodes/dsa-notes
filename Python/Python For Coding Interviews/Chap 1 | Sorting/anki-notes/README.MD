# Sorting (Anki Notes)

Anki Tag ➡️ 01-sorting

**Q**: Complete the print statements

```pyt
elements = [5, 3, 6, 2, 1]

elements.sort()

print(elements) # [1, 2, 3, 5, 6]

strings = ["grape", "apple", "banana", "orange"]

strings.sort()

print(strings) # ['apple', 'banana', 'grape', 'orange']
```

**Solution**:

- print(elements) ➡️  [1, 2, 3, 5, 6] 
  - sorts the elements (if numbers) in ascending order in-place 
- print(strings) ➡️ ['apple', 'banana', 'grape', 'orange']
  - sorts the elements (if strings) in lexicographical order

**Q**: What is the Time and Space Complexity of `.sort()` ? 

**Solution**:

- Time ➡️ O(nlogn)
- Space ➡️ O(n)

Where n ➡️ Number of elements in the list

**Q**: Write the function signature of `.sort()` ? 

**Solution**:

```python
def sort(key=None, reverse=False) -> None:
```

- `key` parameter allows us to customize the sorting order
- `reverse` parameter is a boolean value that determines whether the list should be sorted in *descending order*. By default, it is set to `False`

**Q**: Sort the elements list in descending order 

```python
elements = [5, 3, 6, 2, 1]

print(elements) # [6, 5, 3, 2, 1]
```

**Solution**:

- We can sort a list in descending order by setting the reverse parameter to `True`

  ```python
  elements = [5, 3, 6, 2, 1]
  
  elements.sort(key=None, reverse=True)
  
  print(elements) # [6, 5, 3, 2, 1]
  ```

- We can actually omit the `key` parameter and only pass the `reverse` parameter, by using a feature of Python called *keyword arguments*.

  ```python
  elements.sort(reverse=True)
  ```

**Q**: Sort the `words` list in ascending order by the length of each string without using lambda function 

```python
words = ["apple", "banana", "kiwi", "pear", "watermelon", "blueberry", "cherry"]

# Should be final output 
print(words) # ['kiwi', 'pear', 'apple', 'banana', 'cherry', 'blueberry', 'watermelon']
```



**Solution**:

```python
def get_word_length(word: str) -> int:
    return len(word)

words = ["apple", "banana", "kiwi", "pear", "watermelon", "blueberry", "cherry"]

words.sort(key=get_word_length)

print(words) # ['kiwi', 'pear', 'apple', 'banana', 'cherry', 'blueberry', 'watermelon']
```

- key parameter allows to customize the sorting order , the key parameter returns a value to be used for sorting

**Q**: Sort the `words` list in ascending order by the length of each string using lambda function 

```python
words = ["apple", "banana", "kiwi", "pear", "watermelon", "blueberry", "cherry"]

# Should be final output 
print(words) # ['kiwi', 'pear', 'apple', 'banana', 'cherry', 'blueberry', 'watermelon']
```

**Solution**:

```python
words = ["apple", "banana", "kiwi", "pear", "watermelon", "blueberry", "cherry"]

words.sort(key=lambda word: len(word))

print(words) # ['kiwi', 'pear', 'apple', 'banana', 'cherry', 'blueberry', 'watermelon']
```

Syntax 

- The keyword `lambda`.
- The input variable `word`. We can use any variable name here.
- The colon `:`, after which we define the function body.
- The expression `len(word)`, which is the return value of the function.

**Q**: Explain the difference between `.sort`() and `.sorted()` ? 

**Solution**:

| `.sort()`                  | `.sorted()`                     |
| -------------------------- | ------------------------------- |
| Modifies the original list | Returns a new list              |
| Original list is changed   | Original list remains unchanged |
| Everything else is similar | Everything else is similar      |