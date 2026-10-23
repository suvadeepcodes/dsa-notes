# String Slicing 

Anki : 08-string-slicing

**Q**: What is Python string slicing syntax ? 

**Solution**:

`string[start:end:step]`

**Q**: In slicing which  index is included and which is excluded ?

**Solution**:

`start` is included, `end` is excluded.

**Q**: What does `my_string[:3]` mean?

**Solution**:

From beginning up to, but not including, index `3`.

**Q**: What does `my_string[4:]` mean ?

**Solution**:

From index `4` to the end.

**Q**: What does `my_string[:]` mean?

**Solution**:

Copy  the whole string.

**Q**: What does `my_string[::-1]` do?

**Solution**:

Reverses the string.

**Q**: Are Strings mutable or immutable in Python ? 

**Solution**:

Strings are immutable in python which means they cannot be changed after they are created 

**Q**: Are we creating a new string when we use the slice operator ? 

**Solution**: 

Whenever we slice a string we are not modifying the string instead we are creating a new string with the sliced characters 

**Q**: Why this causes an error ? 

```python
message = "I will never change"
message[0]= "X" # This will cause an error 
```

**Solution**: 

In the above code we try to reassign just the first character .This will cause a `TypeError` because *strings are immutable* .We cannot change individual characters we can only reassign the entire string  