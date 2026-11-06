# Reading Stdin

## Reading Input

So far we have only printed output to the console, but what if we want to take input from the console?

In Python, the `input()` function is used to read input to the program while the program is running. This input comes from a stream of data called *standard input* or *stdin*. This can either mean the data a user types in manually into the terminal (console) or input that is supplied to the program before it is run.

```python
user_input = input("Enter some text: ")

print(user_input) # This will print the input to the console
```

In the above code, `input()` will print the *string* `"Enter some text: "` to the console and read one line of input from stdin. The input will be in the form of a *string* and will be stored in the variable `user_input`.

When `input()` prints text, the following print statement will be on the same line as the prompt. So if the input was `"some text"` in the above example, the output would be:

```bash
Enter some text: some text
```

## Type Conversion with Input

We are not required to provide a prompt to the user when calling the `input()` function:

```python
user_input = input() # This will read one line of input from stdin

print(user_input) # This will print the input to the console
```

By default, `input()` returns the user input as a *string*. If you're expecting a different type of input like an *integer* or a *float*, you need to explicitly convert it using `int()` or `float()`.

```python
 age = int(input("Enter your age: "))

temperature = float(input("Enter the temperature: "))
```

The example above converts the user input, which is expected to be an *integer* representing age, to an *integer* using `int()`. It also converts the user input, which is expected to be a *float* representing temperature, to a *float* using `float()`. It's important to note that if the user enters a value that can't be converted to the expected type, a `ValueError` will be raised, so be careful when converting user input.

## Parse Input

Sometimes we have to do more than just convert the input to a single type. We might need to restructure the input in some way. This is called **parsing** the input.

Suppose you read a list of integers separated by commas into a string, but you want to store them as a list. You can use the `split()` method to split the string by commas. This will convert "1,2,3" into a list of strings `["1", "2", "3"]`.

```python
number_string = "1,2,3"

string_list = number_string.split(",")

print(string_list) # Output: ['1', '2', '3']
```

The above code will split the numbers by the `","` substring, and store each number as a string in the list `string_list`, which is a list of strings. In this case, the `","` is considered the **delimiter**.

## 

