# String Slicing 

## Slicing

- In this example we are extracting the substring from index 1 to index 5 (not excluding 5) from the string "Hello , World!"

  ```
  my_string = "Hello , World!"
  print(my_string[1:5]) # Output : ello
  ```

- If we dont specify the start its equivalent to starting from the beginning of the string

  ```
  my_string ="Leetcode"
  print(my_string[:3]) # Output :Lee
  ```

- If we dont specify the end its equivalent to ending at the end of the string

  ```
  my_string = "Leetcode"
  print(my_string[4:]) #Output : Code
  ```

- If we dont specify either we get the entire string

  ```
  my_string = "Leetcode"
  print(my_string[:]) #Output : Leetcode
  ```

- By not specifying the starting index or the ending index and setting the step to -1 the string will be reversed

  ```
  my_string = "Hello"
  print(my_string[::-1]) #Output : olleH
  ```

- if we dont specify either we get the entire string

  ```
  my_string = "Leetcode"
  print(my_string[:]) #Output : Leetcode
  ```

  

## Reversing a string

- By not specifying the starting index or the ending index and setting the step to -1 the string will be reversed

  ```
  my_string = "Hello"
  print(my_string[::-1]) # Output : olleH
  ```

- The value before the first colon is the starting index , the value after the first colon is the ending index and the value after the colon is the step .If the step is negative the string will be reversed

  ```
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

- In the above code we try to reassign just the first character of the string .This will cause a `TypeError` because strings are immutable. We cannot change individual characters we can only reassign the entire string