# Chap 1 | Classes and Objects

## Intro to Classes

- A class is a blueprint for creating objects

- Below we create a class called SuperHero

  ```python
  class SuperHero:
      def __init__(self, name: str, power: str, health: int, speed: int):
          self.name = name
          self.power = power
          self.health = health
          self.speed = speed
  ```

  - A class is defined with the keyword `class`, followed by the class name and a colon. The `__init__` method is a special method that runs automatically when you create an object. It sets the object's starting attributes.
  - Notice that the `__init__` method has an argument `self`. This is required. The `self` variable allows us to add attributes to our object. 

## What are Objects ? 

- An **object** is an instance of a class. It's a specific item created using the blueprint defined by the class.

  ```python
  # Creating superhero objects
  iron_man = SuperHero("Iron Man", "repulsor beams", 100, 80)
  spider_man = SuperHero("Spider Man", "web slinging", 90, 95)
  ```


## Object Attributes 

- **Attributes** are the properties that define or belong to an object. In our superhero example, we have the following attributes for a superhero: `name`, `power`, `health`, and `speed`.

- Accessing Attributes : 

  - To access an object's attributes, we use dot notation: `object_name.attribute_name`

    ```python
    class SuperHero:
        def __init__(self, name: str, power: str, health: int, speed: int):
            self.name = name
            self.power = power
            self.health = health
            self.speed = speed
    
    iron_man = SuperHero("Iron Man", "repulsor beams", 100, 80)
    
    print(iron_man.name)    # Iron Man
    print(iron_man.power)   # repulsor beams
    ```

- Modifying Attributes 

  - We can also *modify* an attribute's value using the same dot notation:

    ```python
    iron_man.health = 90
    iron_man.power = "advanced repulsor technology"
    
    print(iron_man.health)  # 90
    print(iron_man.power)   # advanced repulsor technology
    ```

- Attribute Types 

  - While Python won't give us any errors when changing the data type of an attribute, we should avoid doing so to avoid unexpected behavior.

    ```python
    iron_man.name = 42       # Allowed but bad practice
    iron_man.health = "full" # Allowed but bad practice
    ```

## Object Methods

- **Methods** are functions that belong to a class or object. They define the behavior of the class or object.

- #### Defining methods in a class

  - Let's update our `SuperHero` class to include two methods, `use_power()` and `take_damage(amount)`:

    ```python
    class SuperHero:
        def __init__(self, name, power, health, speed):
            self.name = name
            self.power = power
            self.health = health
            self.speed = speed
    
        def use_power(self):
            print(f"{self.name} uses {self.power}!")
    
        def take_damage(self, amount):
            self.health -= amount
            print(f"{self.name} takes {amount} damage. Health is now {self.health}.")
    ```

  - We can create an object of the `SuperHero` class and call the methods on it:

    ```python
    iron_man = SuperHero("Iron Man", "super strength", 100, 90)
    
    iron_man.use_power()     # Output: Iron Man uses super strength!
    iron_man.take_damage(20) # Output: Iron Man takes 20 damage. Health is now 80.
    ```


## Self Parameter

- `self` is how Python refers to the specific object being created or acted upon. It allows each superhero to have their own set of attributes and use their own powers.

- `self` is the first parameter in all our methods , including `__init__`

  ```python
  class SuperHero:
      def __init__(self, name, power, health, speed):
          self.name = name
          self.power = power
          self.health = health
          self.speed = speed
  
      def use_power(self):
          print(f"{self.name} uses {self.power}!")
  ```

- #### How `self` works in method calls

  - To better understand how `self` works, it can be helpful to think of it this way:

  - `self` inside `use_power()` refers to `spider_man`

    ```python
    spider_man = SuperHero("Spider-Man", "web-slinging", 100, 90)
    
    spider_man.use_power() # SuperHero.use_power(spider_man)
    ```

## Init Method

- The `__init__` method we've been using is a special method in Python classes, also known as a constructor. Its job is to initialize the attributes of a new object when it's created.

- The `__init__` method is technically *not* a constructor in Python, but it's often referred to as one. The `__new__` method is the actual constructor in Python.

  ```python
  class SuperHero:
      def __init__(self, name, power):
          self.name = name
          self.power = power
  ```

  - The `__init__` method is automatically called when we create a new object from our class. It sets up the initial state of the object.

  - n the above code, `__init__` is responsible for setting the initial values for `name` and `power` for each new superhero we create

    ```python
    # Creating a superhero
    iron_man = SuperHero("Iron Man", "repulsor beams")
    ```

    - Above we created a `SuperHero` object called `iron_man` which calls the `__init__` method. Logically, this is equivalent to `SuperHero.__init__(iron_man, "Iron Man", "repulsor beams")`
      - We don't need to explicitly pass anything for the `self` parameter because Python handles this automatically.
      - `self` inside `__init__` refers to the new `iron_man` object
      - The other parameters are passed to the `__init__` method to initialize the attributes of the object
      - After this process, `iron_man` is a fully initialized `SuperHero` object with all its attributes set.

  ## Docstrings

  - Docstrings are string literals that describe functions, methods, classes, or modules. They serve as documentation for our code.

    ```python
    class SuperHero:
        """
        A class to represent a superhero.
    
        Attributes:
            name (str): The superhero's name
            health (int): The superhero's health points
        """
    
        def __init__(self, name: str, health: int) -> None:
            """Initialize a new SuperHero instance."""
            self.name = name
            self.health = health
    
        def take_damage(self, amount: int) -> None:
            """
            Reduce the superhero's health by the given amount.
    
            Args:
                amount (int): The amount of damage to inflict
            """
            self.health -= amount
            print(f"{self.name} takes {amount} damage.")
    ```

    We have three docstrings in this class:

    1. The class docstring describes the class and its attributes.
    2. The `__init__` method docstring describes the method and its parameters.
    3. The `take_damage` method docstring describes the method and its parameters.

