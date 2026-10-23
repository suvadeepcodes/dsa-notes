# Strings

## Length function

- The function `len()` returns the number of characters in the string

  ```python
  my_str ="Leetcode"
  print(len(my_str)) # Output ➡️ 8
  ```

## String indexing 

- We can access individual characters from a string using String indexing 

  ```python
  my_str = "Hello"
  print(my_str[0]) # Output ➡️ H
  ```

## Looping over a string 

```python
my_string = "Hello ,World!"
for i in range(len(my_string)):
  print(my_string[i])
```

## String Looping Shorthand

```python
my_string = "Hello"
for char in my_string:
  print(char)
```

- The code will output: 

  ```bash
  H
  e
  l
  l
  o
  ```

## String Concatenation

- When we use the `+` operator with two strings Python joins them together to create a new string 

  ```python
  str ="Hello"
  str2 = "World!"
  print(str + str2) # Output : Hello , world
  ```

## String slicing 

- In this example we are extracting the substring from index 1 to index 5 (not excluding 5) from the string "Hello , World!"

  ```python
  my_string = "Hello , World!"
  print(my_string[1:5]) # Output : ello
  ```

- If we dont specify the start its equivalent to starting from the beginning of the string 

  ```python
  my_string ="Leetcode"
  print(my_string[:3]) # Output :Lee
  ```

- If we dont specify the end its equivalent to ending at the end of the string 

  ```python
  my_string = "Leetcode"
  print(my_string[4:]) #Output : Code
  ```

- If we dont specify either we get the entire string 

  ```python
  my_string = "Leetcode"
  print(my_string[:]) #Output : Leetcode
  ```

- By not specifying the starting index or the ending index and setting the step to -1 the string will be reversed 

  ```python 
  my_string = "Hello"
  print(my_string[::-1]) #Output : olleH
  ```

- if we dont specify either we get the entire string 

  ```python
  my_string = "Leetcode"
  print(my_string[:]) #Output : Leetcode
  ```

## Reversing a string 

- By not specifying the starting index or the ending index and setting the step to -1 the string will be reversed 

  ```python
  my_string = "Hello"
  print(my_string[::-1]) # Output : olleH
  ```

- The value before the first colon is the starting index , the value after the first colon is the ending index and the value after the colon is the step .If the step is negative the string will be reversed 

  ```bash
  starting index ➡️ inclusive 
  ending index ➡️ exclusive 
  ```

## Strings are Immutable 

- Strings are immutable in Python which means they cannot be changed after they are created

- Whenever we slice a string we are not modifying the underlying string instead we are creating a new string with the sliced characters 

  ```python
  message = "I will never change"
  message[0] = "X" # This will cause an error 
  ```

- In the above code we try to reassign just the first character of the string .This will cause a  `TypeError` because strings are immutable. We cannot change individual characters we can only reassign the entire string