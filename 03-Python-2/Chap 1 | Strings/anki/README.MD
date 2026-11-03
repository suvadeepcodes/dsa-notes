# Anki Notes ➡️ Chap 1 | Strings

Anki Tag ➡️ 01-strings

**Q**: What is the `len()` function ? 

**Solution**:

- The function `len()` returns the number of characters in a string 

  ```python
  my_str ="Leetcode"
  print(len(my_str)) # Output ➡️ 8
  ```

**Q**: How can we access individual characters from a string ? 

**Solution**:

we can access individual characters from a string using string indexing 

```python
my_str = "Hello"
print(my_str[0]) # Output ➡️ H
```

**Q**: How can we loop over a string ? 

**Solution**:

Method 1 ➡️

```python
my_string = "Hello ,World!"
for i in range(len(my_string)):
  print(my_string[i])
```

Method 2 ➡️

```python
my_string = "Hello"
for char in my_string:
  print(char)
```

**Q**: What is String Concatenation ? 

**Solution**:

When we use the `+` operator with 2 strings Python joins them together to create a new string

```python
str ="Hello"
str2 = "World!"
print(str + str2) # Output : Hello , world

```

**Q**: Strings are mutable or immutable in Python 

**Solution**:

Strings are immutable in Python which means they cannot be changed after they are created 

**Q**: Why this causes an error ? 

```python
message = "I will never change"
message[0] = "X" # This will cause an error 
```

**Solution**:

in the above code we try to reassign just the first character of the string .This will cause a `TypeError` because strings are immutable. We cannot change individual characters we can only reassign the entire string

**Q**: How can we reverse a string in Python ? 

**Solution**:

```python
my_string = "Hello"
print(my_string[::-1]) # Output : olleH
```

