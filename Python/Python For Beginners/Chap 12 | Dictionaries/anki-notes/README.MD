# Dictionaries 

Anki : 12-dictionaries

 **Q**: What is a dictionary ? 

**Solution**:

- used to store *key-value* pairs 

**Q**: What are the 2 ways of creating a dictionary ?

**Solution**:

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

**Q**: What must be unique in a dictionary , the keys or the values ? 

**Solution**:

- The keys must be unique the values can be duplicated

**Q**:How can we check if a dictionary contains a key ?

**Solution**:

To check if a dictionary contains a key we can use the *in* operator

```python
my_dict ={"a":1,"b":2,"c":3}
print("a" in my_dict) # Output : True
print("d" in my_dict) # Output : False
```

**Q**:How to loop over a dictionary ?

**Solution**:

to loop over a dictionary we can use the following technique

```python
my_dict ={"a":1,"b":2,"c":3}
for key,value in my_dict.items():
  print(key,value)
```

**Q**: How to remove a key-value pair from a dict ? 

**Solution**:

- `del` keyword

```python
my_dict ={"a":1,"b":2,"c":3}
del my_dict["a"]
```

