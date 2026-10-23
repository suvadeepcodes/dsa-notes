# Loops 

Anki: 06-loops

**Q**: Print `I love Python` 5 times using while loops 

**Solution**:

```python
i=0
while i<5:
  print("I love Python!")
  i+=1
```

**Q**: What does the following print ? 

```python
for i in range(10):
  print(i)
```

**Solution**:

- prints 0-9

**Q**: What does the following print ? 

```python
for i in range(2,5):
  print(i)
```

**Solution**:

- prints 2-4

**Q**: What does the following print ? 

```python
for i in range(0,10,2):
  print(i)
```

**Solution**:

prints 0,2,4,6,8

**Q**: Explain `break` , `continue` and `pass` ? 

**Solution**:

| Control Flow | What they do ?                                               |
| ------------ | ------------------------------------------------------------ |
| `break`      | Exits the loop immediately                                   |
| `continue`   | Skips the remaining code inside the loop for the current iteration and moves to the next iteration |
| `pass`       | Acts as a placeholder and does nothing. We cannot have empty loops so we use `pass` to avoid errors |

