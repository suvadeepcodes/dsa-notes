# Anki Notes ➡️ Chap 5 | Conditional Statements

**Q**: Explain the following conditional statements 

- `==`
- `!=`
- `<`
- `>`
- `<=`
- `>=`

**Solution**:

Comparision operators evaluate to `True` or `False` depending on the values we compare

| Comparision Operator | What it Does ?           |
| -------------------- | ------------------------ |
| `==`                 | Equal to                 |
| `!=`                 | Not Equal to             |
| `<`                  | Less than                |
| `>`                  | Greater than             |
| `<=`                 | Less than or Equal to    |
| `>=`                 | Greater than or Equal to |

**Q**: What is the scope of if statement ? 

**Solution**:

if statements do not create a new scope .This means that varibles defined inside an if statement are accessible outside of the if statement

```python
if True:
  message ="Hello"
print(message) # This will print "Hello"
```

**Q**: When is a value considered falsy ? 

**Solution**:

A value is Falsy if it is

- False
- None
- 0
- 0.0
- "" (empty string)
- [] (empty list)
- Empty collection (empty tuple , empty set , empty dictionary)

