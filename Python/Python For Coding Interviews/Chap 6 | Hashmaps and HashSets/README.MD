# Hashmaps and Hashsets

## Hash Map Basics

- A hash map is a collection of key-value pairs. Each key is unique, and it maps to a specific value. Keys may be of any immutable type, such as integers, strings, or  tuples.

- In Python, hash maps are implemented using the `dict` class. The common operations on a hash map include:

- Insertions ➡️ insert a key-value pair into the hash map

  ```python
  my_dict = {}
  
  my_dict['a'] = 1 # {'a': 1}
  ```

  - Time Complexity ➡️ O(1)

- Access ➡️ Access the value associated with a key 

  ```python
  my_dict = {'a': 1}
  
  print(my_dict['a']) # 1
  ```

  - Time Complexity ➡️ O(1)

- Deletion ➡️ Delete a key-value pair from the hash map

  ```python
  my_dict = {'a': 1, 'b': 2}
  
  del my_dict['a'] # {'b': 2}
  
  my_dict.pop('b') # {}
  
  my_dict.pop('c') # KeyError: 'c'
  
  my_dict.pop('c', 'default') # No error, returns 'default'
  ```

  - Note ➡️
    - There are two ways to delete a key-value pair from a hash map: using the `del` keyword or the `pop()` method. The only difference is that the `pop()` method returns the value associated with the key.
    - If the key does not exist, both `pop()` and `del` will raise a `KeyError`. To avoid this, you can pass a default value to the `pop()` method, which will be returned if the key does not exist.
  - Time Complexity ➡️ O(1)

- Lookup ➡️ Check if a key exists in the hash map.

  ```python
  my_dict = {'a': 1}
  
  does_a_exist = 'a' in my_dict # True
  does_b_exist = 'b' in my_dict # False
  ```

  - Time Complexity ➡️ O(1)

Note  ➡️ The above time complexities are technically for the average case, but in most cases it's safe to assume that these hash map operations are O(1)

## Default Dict

- In algorithms, it's very common to count the frequency of elements in a list or a string. The straight forward way to do this is with the following code:

  ```python
  nums = [1, 2, 4, 3, 2, 1]
  freq = {}
  
  for num in nums:
      if num in freq:
          freq[num] += 1
      else:
          freq[num] = 1
  
  print(freq)  # {1: 2, 2: 2, 4: 1, 3: 1}
  ```

  - The above code iterates through `nums`, if a number is not in the dictionary, it adds it with a value of `1`. If the number is already in the dictionary, it increments the value by `1`. This is perfectly fine, but Python provides a more elegant way to do this using the `collections` module

- The `collections` module provides a class called `defaultdict` that is a subclass of the built-in `dict` class. It allows you to set a default value for a key that doesn't exist in the dictionary. This can be very useful when counting the frequency of elements in a list. Consider the following code:

  ```pyt
  from collections import defaultdict
  
  nums = [1, 2, 4, 3, 2, 1]
  freq = defaultdict(int)
  
  for num in nums:
      freq[num] += 1
  
  print(freq)  # {1: 2, 2: 2, 4: 1, 3: 1}
  ```

  - We removed the need for conditional statements within the loop, but how? Well we created a `defaultdict`, and passed in `int` as the default value. This means that if a key doesn't exist in the dictionary, it will be created with a default value of the integer `0`. This allows us to increment the value without checking if the key exists.

  - This pattern is also used with other data types, such as lists and sets. For example, if you wanted to create a dictionary where the default value is an empty list, you would use:

    ```python
    nums = [1, 2, 4, 3, 2, 1]
    d = defaultdict(list)
    
    for num in nums:
        d[num].append(num)
    
    print(d)  # {1: [1, 1], 2: [2, 2], 4: [4], 3: [3]}
    ```

    - This will create a dictionary where each key is a number in the list, and the value is a list of all the occurrences of that number. Even if the number doesn't exist in the dictionary, it will first create an empty list as the default value, and then append the given value `num` to the list.

## Counter

- If all we want to do is count the occurrences of elements in a list, an even better solution exists than the `defaultdict`. We can use the `collections.Counter` class:

  ```
  from collections import Counter
  
  nums = [1, 2, 4, 3, 2, 1]
  
  counter = Counter(nums)
  
  print(counter)  # Counter({1: 2, 2: 2, 4: 1, 3: 1})
  
  counter[100] += 1 # No error, even though 100 is not a key
  
  print(counter)  # Counter({1: 2, 2: 2, 4: 1, 3: 1, 100: 1})
  ```

  - The `Counter` class is a subclass of the `dict` class, and it provides a more concise way to count the occurrences of elements in a list. It returns a dictionary where the keys are the elements in the list and the values are the number of times each element appears. It behaves similarly to a `defaultdict` with an integer default value, meaning if a key doesn't exist, it will return `0`.

## Dict Comprehension 

- Similar to list comprehension, Python also supports dictionary comprehension. We can use dictionary comprehensions to initialize dictionaries in a more concise way.

  ```python
  nums = [1, 2, 3, 4, 5]
  
  squared = {num: num * num for num in nums}
  
  print(squared)  # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
  ```

  - In the above code, we created a dictionary where the keys are the numbers from the list `nums` and the values are the square of each number. Notice that the syntax is similar to list comprehension, but we use curly braces instead of square brackets. Inside the curly braces, we have a key-value pair separated by a colon before the loop.

## Dict items

- If we wanted all the keys from a dictionary, we could loop over the dictionary and append the keys to a list. But Python provides a more concise way to get all the keys from a dictionary using the `keys()` method.

  ```py
  my_dict = {"a": 1, "b": 2, "c": 3}
  
  keys = my_dict.keys()
  
  print(keys)  # dict_keys(['a', 'b', 'c'])
  
  keys_list = list(keys)
  
  print(keys_list)  # ['a', 'b', 'c']
  ```

  - The `keys()` method returns a view object that displays a list of all the keys in the dictionary. We can convert this view object to a list using the `list()` method.Similarly, we can get all the values from a dictionary using the `values()` method.

    ```python
    my_dict = {"a": 1, "b": 2, "c": 3}
    
    values = my_dict.values()
    
    print(values)  # dict_values([1, 2, 3])
    
    values_list = list(values)
    
    print(values_list)  # [1, 2, 3]
    ```

  - Lastly, we can get all the key-value pairs from a dictionary using the `items()` method. This is most commonly used when we want to loop over both the keys and values in a dictionary.

    ```python
    my_dict = {"a": 1, "b": 2, "c": 3}
    
    for key, value in my_dict.items():
        print(key, value)
    ```

## Hash Set Basics

- Hash sets are very similar to hash maps, but they only store keys without any associated values. Hash sets also cannot contain duplicates, just like hash maps. In Python, hash sets are implemented using the `set` class. The common operations on a hash set include:

  - Insertion : Insert a key into the hash set.

    ```python
    my_set = set()
    
    my_set.add('a') # {'a'}
    ```

    - Time Complexity : O(1)

  - **Deletion**: Delete a key from the hash set.

    ```python
    my_set = {'a'}
    
    my_set.remove('a') # {}
    my_set.remove('a') # KeyError
    
    my_set.add('b') # {'b'}
    my_set.discard('b') # {}
    my_set.discard('b') # {} (no error)
    ```

    - As shown above, you can use the `remove()` method to delete an element from a hash set. If the element does not exist, the method will raise a `KeyError`. Alternatively, you can use the `discard()` method, which will not raise an error if the element does not exist.
    - Time Complexity : O(1)

  - Lookup : Check if a key exists in the hash set.

    ```python
    my_set = {'a'}
    
    'a' in my_set # True
    'b' in my_set # False
    ```

    - For lookup operations, you can also use the `in` operator, similar to how you would check if an element is in a list.
    - Time Complexity :O(1)

  Note ➡️ The above time complexities are technically for the average case, but in most cases it's safe to assume that these hash set operations are O(1)

## Set Comprehension

- Just like with lists and dictionaries, Python also supports set comprehension. We can use set comprehension to initialize sets in a more concise way.

  ```python
  nums = [1, 3, 5]
  
  squared = {num * num for num in nums}
  
  print(squared)  # {1, 9, 25}
  ```

  - In the above code, we created a set where the elements are the square of each number in the list `nums`. Notice that the syntax is similar to list comprehension, but we use curly braces instead of square brackets. Inside the curly braces, we have the expression we want to add to the set.Both dictionaries and sets use curly braces. The difference between them is that dictionaries have key-value pairs separated by a colon, while sets only have the elements themselves.

## Tuple Keys

- It's common to store pairs of values in a dictionary or set. For example, we might store the `row, column` pair of a cell in a grid. While we cannot store a list as a key in a dictionary, we can use a tuple instead.

  ```python
  dict_of_pairs = {}
  
  dict_of_pairs[(0, 0)] = 1
  dict_of_pairs[(0, 1)] = 2
  
  print(dict_of_pairs)  # {(0, 0): 1, (0, 1): 2}
  
  set_of_pairs = set()
  
  set_of_pairs.add((0, 0))
  set_of_pairs.add((0, 1))
  
  print(set_of_pairs)  # {(0, 0), (0, 1)}
  ```

  - In the above code, we created a dictionary and a set where the keys and elements are tuples. We can use tuples to store pairs of values in a single object. This is useful when we want to store multiple values together, but we don't want to create a new class or structure.