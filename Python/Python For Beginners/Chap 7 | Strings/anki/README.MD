# Strings 

Anki : 07-strings 

**Q**: What does the `len()` function do in Python when called on a string ? 

**Solution**:

`len()` ➡️  returns the number of characters in the string 

```python
my_string = "Leetcode"
print(len(my_string)) # Output : 8 
```

**Q**: What are the 2 ways to loop over a string ? 

**Solution**: 

- First Way 

  ```python
  my_str = "Hello , World!"
  for i in range(len(my_str)):
    print(my_str[i])
  ```

- Second way 

  ```python
  my_str = "Hello"
  for char in my_str:
    print(char)
  ```

  