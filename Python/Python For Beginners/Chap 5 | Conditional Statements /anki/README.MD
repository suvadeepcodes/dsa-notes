# Conditional Statements 

Anki : 05-conditional-statements

**Q**: Are variables defined inside an if statement block  accessible outside of the if statement block ? 

**Solution**: 

variables defined inside an if statement block are accessible outside of the if statement block

```python
if True:
  message ="Hello"
print(message) # This will print Hello
```

**Q**: When is a value falsy ? 

**Solution**

 mnemonic ➡️ **F N Z E C**

| Letter | Meaning          | Examples                  |
| ------ | ---------------- | ------------------------- |
| **F**  | False            | `False`                   |
| **N**  | None             | `None`                    |
| **Z**  | Zero             | `0`, `0.0`                |
| **E**  | Empty string     | `""`                      |
| **C**  | Empty collection | `[]`, `()`, `{}`, `set()` |



