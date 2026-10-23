## Functions

## How to define a function ? 

```python
def add(x:int,y:int)-> int:
	return x + y 

print(add(x,y)) => 7
```

- Local scope 
  - variables defined inside the function are only accessible within the function 
- Parameters
  - inputs to the function defination are called parameters 
- Arguments
  - inputs passed to the function call are called arguments 
- Type hints 
  - indicates what type of data the function expects to receive and return .This is optional 
- Global scope
  - variables declared outside of any function have a global scope and they can be accessed from the program including inside functions 

## Default Arguments

```python
def greet(name ="world"): 
  print("Hello "+ name + "!")
  
  
greet() #Hello World
greet("Bob") #Hello Bob
```

