# Variables 

## Variable Declaration 

- To declare a variable we use the following syntax 

  ```py
  message ="Hello , world!"
  ```

## Naming Convention

- In python we use snake casing to declare variables 

  ```python
  my_name = "Suvadeep"
  ```

## Multiple Assignments 

- Python allows you to assign multiple variables in a single line. Just separate the variables with a comma, and the right-hand side values with a comma as well.
  ```python
  msg1, msg2 = "Hello", "World"
  ```

## How can we print the type of a variable or value in Python ? 

- We can print the type of a variable or value using the `type()` function 

  ```python
  print(type(10))
  ```

- This will output: `<class 'int'>`

## Type Casting 

- A variable in Python can be converted to a different type using **type casting**

  ```python
  variable = 10.9
  print(int(variable))
  ```

- This code will output : 10

## Type Errors 

- We can't convert a string to an integer unless the string is a number 

## Empty Variable 

- If we want to declare a variable without a value, we can use the `None` keyword

  ```python
  my_name = None
  ```

