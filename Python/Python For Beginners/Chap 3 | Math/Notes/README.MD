# Math 

## Arithmatic Operators

| Operator              | What it does ?                                               |
| --------------------- | ------------------------------------------------------------ |
| `+`                   | adds 2 operands                                              |
| `-`                   | Substracts the second operand from the first                 |
| `*`                   | Multiplies 2 operands                                        |
| `/`                   | Divides the first operand by the second .The result is always a float |
| `//` (Floor Division) | Divides the first operand by the second and the result is always an integer |
| `%` (Modulas)         | Returns the remainder of the division of the first operand by the second |
| `**` (Exponentiation) | Raises the first operand to the power of the second operand  |

Examples : 

```python
x,y = 7,2
print(x / y)  # Output : 3.5
print(x // y) # Output : 3 
print(x % y)  # Output : 1
print(x ** y) # Output : 49


```

## Shorthand Operators 

| shorthand operator | What it does ?   |
| ------------------ | ---------------- |
| `+=`               | count = count +  |
| `-=`               | count = count -  |
| `*=`               | count = count *  |
| `/=`               | count = count /  |
| `//=`              | count = count // |
| `%=`               | count = count %  |
| `**=`              | count = count ** |

## Boolean operators 

- Boolean `or` : returns `True` if at least one of the operands is `True`

  ```python
  a,b,c = False,False,True
  print(a or b or c) #Output : True
  ```

- Boolean `and` : returns `True` if all the operands is `True`

  ```python
  a,b,c = True,True,True
  print(a and b and c) #Output : True
  ```

- Boolean negation : inverts the value of the operand 

  ```python
  a,b = True,False
  print(not a) # Output: False
  print(not b) # Output : True
  ```

  