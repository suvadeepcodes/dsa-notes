# Tuples 

Anki: 10-tuples

**Q**: Tuples are mutable or immutable ? 

**Solution**: 

- Tuples are immutable , once we create it we cant modify it 

**Q**: How are tuples created ? 

**Solution**:

tuples are created by using parenthesis 

```python
my_tuple =(4,5,6)
print(my_tuple) # Output: (4,5,6)
```

**Q**: Can we index a tuple like a list ? 

**Solution**: 

We can index tuples like a list

```python
my_tuple =(4,5,6)
print(my_tuple[0]) #Output: 4
```

**Q**: Does slicing a tuple create a new tuple with the specified slice ? 

**Solution**:

slicing a tuple doesn't modify it instead it creates a new tuple with the specified slice 

**Q**: Why will the following code raise an error ? 

```python
my_tuple =(4,5,6)
my_tuple[0] = 7 
```

**Solution**:

We cant modify an tuple hence the above code will raise an error 

**Q**: Can we call the following functions on a tuple ? 

- append()
- pop()
- sum()
- max()
- min()

**Solution**:

| Function   | Can we call it ?              |
| ---------- | ----------------------------- |
| `append()` | No as it would modify it      |
| `pop()`    | No as it would modify it      |
| `sum()`    | yes as it would not modify it |
| `max()`    | yes as it would not modify it |
| `min()`    | Yes as it would not modify it |

