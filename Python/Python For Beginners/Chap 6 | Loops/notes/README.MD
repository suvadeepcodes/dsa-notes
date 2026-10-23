# Loops

## while loops

```python
i=0
while i<5:
  print("I love Python!")
  i+=1
```

## For Loops

- print 0-9

  ```python
  for i in range(10):
    print(i)
  ```

- print 2-4

  ```python
  for i in range(2,5):
    print(i)
  ```

- print 0,2,4,6 and 8

  ```python
  for i in range(0,10,2):
    print(i)
  ```

## Control Flow

| Control Flow | What it does ?                                                                                      |
| ------------ | --------------------------------------------------------------------------------------------------- |
| `break`      | Exits the loop immediately                                                                          |
| `continue`   | Skips the remaining code inside the loop for the current iteration and moves to the next iteration  |
| `pass`       | Acts as a placeholder and does nothing. We cannot have empty loops so we use `pass` to avoid errors |
