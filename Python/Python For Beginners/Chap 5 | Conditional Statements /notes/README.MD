# Conditional Statements 

## Comparision Operators 

- Comparision operators evaluate to `True` or `False` depending on the values we compare 

  | Comparision Operator | What it Does ?           |
  | -------------------- | ------------------------ |
  | `==`                 | Equal to                 |
  | `!=`                 | Not Equal to             |
  | `<`                  | Less than                |
  | `>`                  | Greater than             |
  | `<=`                 | Less than or Equal to    |
  | `>=`                 | Greater than or Equal to |

  

## If statement scope 

- if statements do not create a new scope .This means that varibles defined inside an if statement are accessible outside of the if statement 

  ```python
  if True:
    message ="Hello"
  print(message) # This will print "Hello"
  ```

## Truthy or Falsy 

- A value is considered truthy if it evaluates to `True` in a boolean context .A value is considered falsy if it evaluates to `False` in a boolean context 
- A value is Falsy if it is 
  - False
  - None
  - 0
  - 0.0
  - "" (empty string)
  - [] (empty list)
  - Empty collection (empty tuple , empty set , empty dictionary)
- A value is truthy if it is not false