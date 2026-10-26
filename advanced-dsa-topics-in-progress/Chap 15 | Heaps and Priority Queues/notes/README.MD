# Chap 15 | Heaps and Priority Queues

## Heap Push

- Heaps (or priority queues) are a data structure that allow you to insert (push) and remove (pop) elements based on some *priority* associated with each element. In Python, a heap is a minimum heap by default, meaning that the element with the smallest priority is always at the top of the heap.

  ```python
  import heapq
  
  heap = [] # min heap
  
  heapq.heappush(heap, 3)
  heapq.heappush(heap, 1)
  
  print(heap[0])  # 1
  
  heapq.heappush(heap, 0)
  
  print(heap[0])  # 0
  ```

  - We first imported the `heapq` module, which contains functions for working with heaps.
  - We created an empty list called `heap`. Heaps are implemented as lists in Python.
  - We pushed the elements `3` and `1` onto the heap.
  - We accessed the element with the smallest priority, which is `1`. The element with the smallest priority is always at index 0.
  - We pushed the element `0` onto the heap.
  - We accessed the element with the smallest priority, which is now `0`.
  - Time and Space Complexity
    - The time complexity of `heapq.heappush()` is O(log(n)) where n is the number of elements in the heap.
    - The time complexity of accessing the element with the smallest priority is O(1), since indexing into a list is O(1).
    - The space complexity of a heap is O(n), where n is the number of elements in the heap.

## Heap Pop

- We can also remove elements from a heap using the `heapq.heappop()` function. This function removes the element with the smallest priority from the heap and returns it.

  ```python
  import heapq
  
  heap = []
  
  heapq.heappush(heap, "banana")
  heapq.heappush(heap, "apple")
  heapq.heappush(heap, "kiwi")
  
  print(heapq.heappop(heap))  # apple
  print(heapq.heappop(heap))  # banana
  print(heapq.heappop(heap))  # kiwi
  ```

  - We pushed the strings `"banana"`, `"apple"`, and `"kiwi"` onto the heap.
  - We popped the element with the smallest priority, which is `"apple"`. By default, the priority of strings is determined by their lexicographical order, with smaller lexicographical strings having higher priority.
  - We popped the next element with the smallest priority, which is now `"banana"`.
  - We popped the last element with the smallest priority, which is now `"kiwi"`.
  - The heap is now empty. If we try to pop an element from an empty heap, we will get an `IndexError`.

## Heapify

- If we are given a list of elements up front, we can convert them into a heap using the `heapq.heapify()` function. This function rearranges the elements in the list so that they form a valid heap. The heap is a min heap by default, meaning that the element with the smallest priority is at index 0.

  ```python
  import heapq
  
  heap = [4, 2, 5, 3, 1]
  
  heapq.heapify(heap)
  
  while heap:
      print(heapq.heappop(heap))
  ```

  - The output of this code will be:

    ```bash
    1
    2
    3
    4
    5
    ```

    - We transformed the original list `[4, 2, 5, 3, 1]` into a heap using `heapq.heapify()`. We then popped all the elements from the heap in order of their priority.
    - Time and Space Complexity :
      - The time complexity of `heapq.heapify()` is O(n)where n is the number of elements in the heap. This means it's more efficient than pushing elements onto the heap one by one, which would take O(nlog(n)) time.

## Max Heap

- Unfortunately, Python does not have a built-in max heap implementation. However, we can simulate a max heap by negating the values we insert into the heap. This way, the element with the largest priority (the smallest value) will be at the top of the heap.

- Suppose we had a set of numbers `[4, 2, 3, 5]`. We can insert these numbers into a max heap by negating them and inserting them into a min heap. The negated numbers would be `[-4, -2, -3, -5]`. When we pop elements from the min heap, we would negate them again to get the original numbers.

  ```python
  import heapq
  
  nums = [4, 2, 3, 5]
  max_heap = []
  
  for num in nums:
      heapq.heappush(max_heap, -num) # Negate the number
  
  while max_heap:
      top = -heapq.heappop(max_heap) # Negate the number back
      print(top)
  ```

  - The output of this code will be:

    ```bash
    5
    4
    3
    2
    ```

    - We negated the numbers and pushed them onto the heap, which is technically implemented as a min heap.
    - This way the largest original number, 5, will be at the top of the heap after negation.
    - We popped the elements from the heap and negated them back to get the original numbers.
    - The popped values were `-5, -4, -3, -2` before we negated them back to `5, 4, 3, 2`.

## Custom Heap

- Unfortunately, Python does not have a custom `key` parameter for the `heapq` module. This means that we cannot directly create a heap with custom priorities. However, we can simulate a custom heap by using a **tuple** as the element in the heap.

- With tuples, Python will use the first element of the tuple as the priority. If two tuples have the same first element, Python will compare the second element of the tuples, and so on.

- If we wanted to create a heap of integers by using the absolute value of each integer as the priority, we could use the following code:

  ```python
  import heapq
  
  nums = [4, -2, 3, -5]
  heap = []
  
  for num in nums:
      pair = (abs(num), num)
      heapq.heappush(heap, pair)
  
  while heap:
      pair = heapq.heappop(heap)
      original_num = pair[1]
      print(original_num)
  ```

  - The output of this code will be:

    ```bash
    -2
    3
    4
    -5
    ```

## Heap N Smallest

- Heaps provide a very convenient way to find the smallest elements in a collection. For this we can use `heapq.nsmallest()`:

  ```python
  import heapq
  
  my_array = [1, 6, 3, 5, 7, 9, 8, 10, 2, 12]
  
  heapq.nsmallest(3, my_array)  # returns [1, 2, 3]
  heapq.nsmallest(5, my_array)  # returns [1, 2, 3, 5, 6]
  heapq.nsmallest(1, my_array)  # returns [1]
  ```

  - We initialized an unsorted array `my_array` with some integers.
  - We called `heapq.nsmallest(3, my_array)`. This returns the `3` smallest elements in `my_array`. The elements are returned in sorted order.
  - We also called `heapq.nsmallest(5, my_array)` which returns the `5` smallest elements in `my_array`.
  - We also called `heapq.nsmallest(1, my_array)` which returns the smallest element in `my_array`.
  - Time and Space Complexity
    - The time complexity of `heapq.nsmallest()` is O(mlog(n)) where n is the number of elements to return and m is the size of the input.
    - One way to implement `nsmallest()` is to iterate over the input and push each element onto a heap. We ensure the size of the heap is at most n*n* by popping the largest element if the heap size exceeds n. Thus, we will use a max heap.

## Heap N Largest

- We also have `heapq.nlargest()` to get the `n` largest elements in a collection.

  ```python
  import heapq
  
  my_array = [1, 6, 3, 5, 7, 9, 8, 10, 2, 12]
  
  heapq.nlargest(3, my_array)  # returns [12, 10, 9]
  heapq.nlargest(5, my_array)  # returns [12, 10, 9, 8, 7]
  heapq.nlargest(1, my_array)  # returns [12]
  ```

  - We initialized an unsorted array `my_array` with some integers.
  - We called `heapq.nlargest(3, my_array)`. This returns the `3` largest elements in `my_array`. The elements are returned in *decreasing* order.
  - We also called `heapq.nlargest(5, my_array)` which returns the `5` largest elements in `my_array` in *decreasing* order.
  - We also called `heapq.nlargest(1, my_array)` which returns the largest element in `my_array`
  - Time and Space Complexity
    - The time complexity of `heapq.nlargest()` is O(mlog(n)) where n is the number of elements to return and m is the size of the input.
    - One way to implement `nlargest()` is to iterate over the input and push each element onto a heap. We ensure the size of the heap is at most n by popping the smallest element if the heap size exceeds n. Thus, we will use a min heap.