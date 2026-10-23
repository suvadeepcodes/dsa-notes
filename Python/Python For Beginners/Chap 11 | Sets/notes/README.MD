# Sets

## What is a set ? 

- a set can only contain unique elements 
- a set is unordered meaning the elements are not stored in a specific order 

## How to add elements to a Set ? 

 Method 1 :-

```python 
my_set ={1,2,3}
print(my_set) # Output : {1,2,3}
```

Method 2 :-

```python
my_set =set()
my_set.add(1)
my_set.add(2)
my_set.add(3)
```

## How to remove elements from a set ? 

`remove()` function 

```python
my_set ={1,2,3}
my_set.remove(2)
print(my_set) # Output : {1,3}
```

## How to loop over elements in a set ? 

```python
my_set = {1,2,3}
for element in my_set:
	print(element)
```

## How can we check whether an element exists in a set ? 

```python 
my_set = {"Cat","Dog","Mouse"}
contains_cat = "Cat" in my_set #True
contains_lion = "Lion" in my_set #False
```

## How can we remove duplicates from a list using a set ? 

```python
my_list = [1,2,3,4,5,1,2,5]
my_set = set(my_list)
my_list_no_duplicates = list(my_set)
```

