# Lists 

Anki: 09-lists

**Q**: Are lists mutable ? 

**Solution**:

- lists are mutable (meaning we can change the values in the list)

**Q**: How can we check whether an element *is in* or *not in* a list ? 

**Solution**:

We can use the *in* and *not in* operator to check whether an element is in or not in the list 

```python
my_list = [1,2,3]
if 2 in my_list:
  print("2 present")
  
if 4 not in my_list:
  print("4 not present")
```

**Q**: What are the 2 ways of  looping  over a list ? 

**Solution**:

Method 1 ➡️

```python
my_list =[1,2,3,4,5]
for i in range(len(my_list)):
  print(my_list[i])
```

Method 2 ➡️

```python
my_list = [1,2,3,4,5]
for element in my_list:
  print(element)
```

**Q**: Explain the following list functions ? 

- `sum()`
- `min()`
- `max()`
- `append()`
- `pop()`
- `index()`

**Solution**:

| list functions | What it does ?                                   |
| -------------- | ------------------------------------------------ |
| `sum()`        | returns the sum of all the elements in the list  |
| `min()`        | returns the smallest element in the list         |
| `max()`        | returns the largest element in the list          |
| `append()`     | adds an element to the end of the list           |
| `pop()`        | removes the last element from the list           |
| `index()`      | finds the first index of the element in the list |

**Q**: Can we use the slice operator on a list ? 

**Solution**:

- list slicing is similar to string slicing 
- slicing a list creates a new list

