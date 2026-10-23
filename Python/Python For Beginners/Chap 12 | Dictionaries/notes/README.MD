# Dictionaries

## Intro to dictionaries 

### What is a dictionary ? 

- used to store key-value pairs 
- think of it as a table with 2 columns , first column - key , second column - value 

### What are the 2 ways of creating a dictionary ? 

Method 1 ➡️

```python
my_dict ={"Alice": 25 , "Bob":30 ,"Charlie":35}
```

Method 2 ➡️

```python
my_dict ={}
my_dict["Alice"] = 25
my_dict["Bob"] = 30
my_dict["Charlie"]=35
```

## Dict operations 

### What must be unique in a dictionary , the keys or the values ? 

- The keys must be unique the values can be duplicated 

### How can we check if a dictionary contains a key ? 

- To check if a dictionary contains a key we can use the *in* operator 

```python
my_dict ={"a":1,"b":2,"c":3}
print("a" in my_dict) # Output : True
print("b" in my_dict) # Output : False
```

## Dict Looping 

### How to loop over a dictionary ? 

to loop over a dictionary we can use the following technique

```python
my_dict ={"a":1,"b":2,"c":3}
for key,value in my_dict.items():
  print(key,value)
```

## Count the occurrence 

### Count the occurence of elements in a set 

```python
def count_characters(word:str) -> Dict[str,int]:
  char_count ={}
  for char in word:
    if char in char_count:
      char_count +=1
    else:
      char_count = 1
  return char_count
```

## Dict Remove 

### How to remove a key-value pair from a dict ? 

- `del` keyword 

```python 
my_dict ={"a":1,"b":2,"c":3}
del my_dict["a"]
```

