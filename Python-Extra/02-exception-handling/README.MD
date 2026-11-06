# Exception Handling

## Try Except

When an error occurs in a program, it usually causes the program to crash. And Python is no exception.

```python
result = 10 / 0 # ZeroDivisionError: division by zero

print("This will not be printed.")
```

But there is a way we can handle these errors and prevent the program from crashing. This is done using the `try` and `except` blocks.

```python
try:
    # code that might cause an error
    result = 10 / 0
except:
    print("An error occurred!")

print("This will be printed regardless.")
```

A `try` block is reminiscent to an `if-else` statement. The code inside a `try` block is always executed, but if any line of code raises an error, the program will immediately jump to the `except` block. If no error occurs, the `except` block is skipped.

This is called **exception handling**.

## Error Catching

When an error occurs in a `try` block, it may be useful for us to know exactly what error occurred. This can allow us to better debug our code.

```python
try:
    result = 10 / 0
except Exception as error:
    print("Error:", error)
```

The above code will *catch* the error and place it inside a variable called `error` using the `as` keyword. We can then print this variable to see the error message, which would be:

```bash
Error: division by zero
```

## Multiple Except Blocks

Instead of having a single `except` block to handle all exceptions,

```bash
try:
    n = 10 / 0
except Exception as error:
    print("An error occurred:", error)
```

you can have multiple `except` blocks to handle different types of exceptions.

```python
try:
    num1 = int(a)
    num2 = int(b)
    result = num1 / num2
except ValueError:
    print("Error: Invalid value!")
except ZeroDivisionError:
    print("Error: Division by zero!")
except Exception as error:
    print("An error occurred:", error)
```

In the first example we catch all exceptions with `Exception`. In the second example, we have different blocks to handle different exceptions. The first `except` will catch a `ValueError`, the second will catch a `ZeroDivisionError`, and the third will catch any other exceptions. That means, if neither a `ValueError` nor a `ZeroDivisionError` occurs, the third block will still catch all other exceptions.