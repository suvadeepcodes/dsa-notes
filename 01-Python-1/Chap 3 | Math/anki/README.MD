# Anki ➡️ Chap 3 | Math

**Q**: Arithmatic Operators

| Operation | Result | Definition                                                   |
| --------- | ------ | ------------------------------------------------------------ |
| `7 / 2`   | 3.5    | `/` ➡️ division ➡️  divides the first operand by the second .The result is always an float |
| `7 // 2`  | 3      | `//` ➡️ Floor division ➡️ divides the first operand by the second and the result is always an integer (towards negative infinity) |
| `7 % 2`   | `1`    | `%` ➡️ Modulas ➡️ returns the remainder of the division of the first operand by the second |
| `7 **2`   | 49     | `**` ➡️ Exponentiation ➡️ Raises the first operand to the power of the second operand |

**Q**:Shorthand Operators

| shorthand operator | What it does ?   |
| ------------------ | ---------------- |
| `+=`               | count = count +  |
| `-=`               | count = count -  |
| `*=`               | count = count *  |
| `/=`               | count = count /  |
| `//=`              | count = count // |
| `%=`               | count = count %  |
| `**=`              | count = count ** |

**Q**: Boolean operators 

**Solution**:

| Boolean Operators | Definition                                               | Example                                                      |
| ----------------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| `or`              | returns `True` if at least one of the operands is `True` | ``a,b,c = False,False,True`<br/>print(a or b or c)` <br />#Output : True |
| `and`             | returns `True` if all the operands is `True`             | `a,b,c = True,True,True`<br />`print(a and b and c) #Output : True` |
| `not`             | inverts the value of the operand                         | `a,b = True,False`<br />`print(not a)` # Output: False<br />`print(not b)` # Output : True |