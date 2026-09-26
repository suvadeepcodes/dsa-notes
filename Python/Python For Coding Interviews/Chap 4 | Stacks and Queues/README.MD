# Stacks and Queues

## Stack

- Python does not have a built-in stack data structure, but we can use a list for the same purposes.

  - `append()` is used to push an element onto the stack.

    ```python
    stack = []
    stack.append(1)
    stack.append(2)
    ```

    - Time Complexity :O(1)

  - `pop()` is used to remove and return the top element from the stack.

    ```python
    stack = [1, 2]
    
    top_element = stack.pop() # 2
    ```

    - Time Complexity :O(1)

  - `[-1]` can be used to access the top element of the stack without removing it. This assumes that the stack is not empty.

    ```python
    stack = [1, 2]
    
    top_element = stack[-1] # 2
    ```

    - Time Complexity :O(1)

  - `len()` can be used to check if the stack is empty.

    ```python
    stack = [1, 2]
    
    while len(stack) > 0:
        print(stack.pop())
    ```

    - Time Complexity :O(1)

## Queue 

- Python provides a `deque` class from the `collections` module that can be used to implement a queue.

- The `deque` provided in Python is actually a double-ended queue. It allows us to push or pop from either end of the queue efficiently.

  - `append()` is used to enqueue an element to the right side of the queue.

    ```python
    from collections import deque
    
    queue = deque()
    
    queue.append(1) # [1]
    queue.append(2) # [1, 2]
    ```

    - Time Complexity : O(1)

  - `popleft()` is used to remove and return the leftmost element from the queue.

    ```python
    queue = deque([1, 2]) # pass a list to initialize the queue
    
    queue.popleft() # Returns 1, queue is now [2]
    queue.popleft() # Returns 2, queue is now []
    ```

    - Time Complexity : O(1)

  - `[0]` and `[-1]` can be used to access the leftmost and rightmost elements of the queue respectively. This assumes that the queue is not empty.

    ```python
    queue = deque([1, 2, 3, 4])
    
    leftmost_element = queue[0] # 1
    rightmost_element = queue[-1] # 4
    ```

    - **Tip:** In Python, we can also index any element in the queue using the square brackets `[]` similar to a list. This is technically not a queue operation but can be useful in some cases.
    - Time Complexity 
      - Getting the first or last element with `[0]`, `[-1]`: O(1)
      - Getting an arbitrary element with `[i]`: O(n)

  - `len()` can be used to check if the queue is empty.

    ```python
    queue = deque([1, 2])
    
    while len(queue) > 0:
        print(queue.popleft())
    ```

    - Time Complexity : O(1)

  - `appendleft()` is used to enqueue an element to the left side of the queue.

    ```python
    from collections import deque
    
    queue = deque()
    
    queue.appendleft(1) # [1]
    queue.appendleft(2) # [2, 1]
    ```

    - Time Complexity : O(1)

  - `pop()` is used to remove and return the rightmost element from the queue.

    ```python
    queue = deque([1, 2]) # pass a list to initialize the queue
    
    queue.pop() # [1]
    queue.pop() # []
    ```

    - Time Complexity : O(1)

