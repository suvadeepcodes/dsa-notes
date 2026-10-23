# Sorted Dicts and Sorted Sets

## Sorted Dict Basics 

- Python does not have a built-in sorted dictionary data structure. However, we can use the [sorted containers](https://grantjenks.com/docs/sortedcontainers/) library to create a sorted dictionary in Python. It supports the same operations as a regular dictionary, but the keys are always sorted. A sorted dictionary may *not* contain duplicate keys.

- Insertion 

  - Insert a key-value pair into the sorted dict.

    ```python
    from sortedcontainers import SortedDict
    
    sorted_dict = SortedDict()
    
    sorted_dict['C'] = 90
    
    sorted_dict['B'] = 80
    
    sorted_dict['A'] = 70
    
    print(sorted_dict)  # SortedDict({'A': 70, 'B': 80, 'C': 90})
    ```

- Access 

  - Access the value associated with a key.

    ```python
    sorted_dict = SortedDict({'a': 1})
    
    print(sorted_dict['a']) # 1
    ```

- Deletion

  - Delete a key-value pair from the sorted dict.

    ```python
    sorted_dict = SortedDict({'a': 1, 'b': 2, 'c': 3, 'd': 4})
    
    # removes & return the last key-value pair in sorted order
    sorted_dict.popitem() # ('d', 4)
    
    # removes & return the first key-value pair in sorted order
    sorted_dict.popitem(0) # ('a', 1)
    
    # remove & return the value associated with the key
    sorted_dict.pop('b') # 2
    
    del sorted_dict['c'] # {}
    ```

    - As shown above, there are several ways to delete a key-value pair from a sorted dictionary. You can use the `popitem()` method to remove and return the first or last key-value pair in sorted order. You can also use the `pop()` method to remove and return the value associated with a specific key, or the `del` keyword to delete a key-value pair.
    - The `popitem()` method will raise a `KeyError` if the dictionary is empty.
    - The `pop()` method will raise a `KeyError` if the key does not exist.
    - The `del` keyword will also raise a `KeyError` if the key does not exist.

- Lookup

  - Check if a key exists in the sorted dict.

    ```python
    sorted_dict = SortedDict({'a': 1})
    
    does_a_exist = 'a' in sorted_dict # True
    does_b_exist = 'b' in sorted_dict # False
    ```

    - For lookup operations, you can also use the `in` operator, similar to how you would check if an element is in a list.

- Iterating 

  - Loop through the sorted dict

    ```python
    sorted_dict = SortedDict({'a': 1, 'b': 2, 'c': 3})
    
    for key, value in sorted_dict.items():
        print(key, value)
    ```

    - Notice that we loop through the sorted dictionary using the `items()` method, which returns a list of key-value pairs. We will iterate over the key-value pairs in sorted order based on the keys. If we only iterated over the keys, but we needed the values as well, we would have to do a lookup for each key, which would be less efficient. 

- Time and Space Complexity 

  - Insertion : O(logn)
  - Access : O(logn)
  - Deletion : O(logn)
  - **Lookup**: O(logn)

## Sorted Set Basics

- Sorted sets are very similar to hash sets, but they store keys in sorted order. Sorted sets may not contain duplicate elements. The common operations on a sorted set include:

  - **Insertion**: Insert a key into the sorted set.

    ```python
    from sortedcontainers import SortedSet
    
    my_set = SortedSet()
    
    my_set.add(90)
    my_set.add(80)
    my_set.add(85)
    
    print(my_set) # SortedSet([80, 85, 90])
    ```

  - **Deletion**: Delete a key from the sorted set.

    ```python
    my_set = SortedSet([90, 80, 85, 95])
    
    my_set.remove(90) # SortedSet([80, 85, 95])
    
    my_set.discard(100) # SortedSet([80, 85, 95])
    
    my_set.pop() # 95
    
    my_set.pop(0) # 80
    
    print(my_set) # SortedSet([85])
    
    my_set.clear() # SortedSet([])
    ```

    - The `remove()` method will raise a `KeyError` if the element does not exist, while the `discard()` method will not.
    - The `pop()` method will remove and return the largest element in the sorted set.
    - The `pop(0)` method will remove and return the smallest element in the sorted set.
    - The `clear()` method will remove all elements from the sorted set.

- Lookup : 

  - Check if a key exists in the sorted set.

    ```python
    my_set = SortedSet([80, 85, 90])
    
    does_80_exist = 80 in my_set # True
    does_100_exist = 100 in my_set # False
    ```

    - For lookup operations, you can also use the `in` operator, similar to how you would check if an element is in a list.

- Iterating:

  - Loop through the sorted set.

    ```python
    sorted_set = SortedSet([4, 3, 5, 2, 1])
    
    for num in sorted_set:
        print(num)  # 1, 2, 3, 4, 5
    ```

    - The elements in a sorted set are always sorted in ascending order.

- Time Complexity 

  - **Insertion**: O(logn)
  - **Deletion**: O(logn)
    - Note: `clear()` is O(n)
  - **Lookup**: O(logn)