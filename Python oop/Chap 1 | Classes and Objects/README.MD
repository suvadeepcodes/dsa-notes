# Chap 1 | Classes and Objects

## Intro to Classes

- A [class](https://docs.python.org/3/tutorial/classes.html) is a blueprint for creating objects

  ```python
  class SuperHero:
      def __init__(self, name: str, power: str, health: int, speed: int):
          self.name = name
          self.power = power
          self.health = health
          self.speed = speed
  ```

  - In Python, a class is defined with the keyword `class`, followed by the class name and a colon. The `__init__` method is a special method that runs automatically when you create an object. It sets the object's starting attributes.
  - Notice that the `__init__` method has an argument `self`. This is required. The `self` variable allows us to add attributes to our object. It also prevents name conflicts, since `name` and `self.name` are different variables.

## What are Objects ? 

- An **object** is an instance of a class. It's a specific item created using the blueprint defined by the class.

  ```python
  # Creating superhero objects
  iron_man = SuperHero("Iron Man", "repulsor beams", 100, 80)
  spider_man = SuperHero("Spider Man", "web slinging", 90, 95)
  ```

  