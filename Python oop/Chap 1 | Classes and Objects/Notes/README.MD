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
- `self` is the first parameter in all our methods , 