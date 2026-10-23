# Tuples 

- Tuples are immutable (once a tuple is created it cannot be changed)

- we can create tuples using parenthesis 

  ```python
  my_tuple = (4,5,6)
  print(my_tuple) # Output : (4,5,6)
  ```

- We can index tuples like a list 

  ```python
  my_tuple = (4,5,6)
  print(my_tuple[0]) # Output : 4 
  ```

- slicing 

  - slicing a tuple doesnt modify it , instead it creates a new tuple with the specified slice

    ```python
    my_tuple = (4,5,6)
    print(my_tuple[1:]) # Output : (5,6)
    ```

- since we can't modify a tuple the following code will raise an error 

  ```python
  my_tuple = (4,5,6)
  my_tuple[0] = 7 # Raises an error 
  ```

- append ,pop , sum(), max(), min()

  - we cant call `append` , `pop` on a tuple since these functions would modify it 
  - we can hawever still call `sum()`, `max()` and `min()` on a tuple since these functions doesn't modify the tuple  