# Chap 5 | Polymorphism

## Polymorphism with Inheritance

- **Polymorphism** means "many forms" in Greek. In programming, it lets objects behave differently while sharing a common interface. An analogy would be different phones being able to charge with the same charger.

- #### Runtime Polymorphism

  - Decided during program execution
  - In Python it can be achieved through Method Overriding and Duck Typing

- Let's understand Runtime Polymorphism through Method Overriding:

  ```python
  class Superhero:
      def __init__(self, name: str, power: str):
          self.name = name
          self.power = power
  
      def special_power(self) -> None:
          pass # Not needed for this example
  
  class IronMan(Superhero):
      def special_power(self) -> None:
          print(f"{self.name} uses {self.power}")
  
  class Thor(Superhero):
      def special_power(self) -> None:
          print(f"{self.name} uses {self.power}")
  ```

- Above we have a class `Superhero` and two subclasses `IronMan` and `Thor`.

  ```python
  def display_power(hero: Superhero) -> None:
      hero.special_power()
  
  iron_man = IronMan("Iron Man", "repulsor beams")
  thor = Thor("Thor", "hammer")
  
  display_power(iron_man)  # Iron Man uses repulsor beams
  display_power(thor)      # Thor uses hammer
  ```

- Above we have a function `display_power` that takes an object of type `Superhero` and calls its `special_power` method. It accepts any object of type `Superhero` (or its subclasses) and calls their `special_power` method.

- We pass in an instance of `IronMan` and an instance of `Thor` to the `display_power` function and it calls the correct `special_power` method for each instance.

- This works because we expect a `Superhero` object and any subclass of `Superhero` will have a `special_power` method, even if it has not been overridden.

- Compile-time Polymorphism 

  - Decided at compilation time (before the code starts running)
  - In Python it can be achieved through method overloading

## Method Overloading

- **Method Overloading** is a feature that allows a class to have multiple methods with the same name, but different parameters. This is a form of polymorphism (one function name, multiple implementations).

  ```python
  def method_name(parameter1, parameter2):
      pass
  
  def method_name(parameter1, parameter2, parameter3):
      pass
  ```

- In the above example, we have two methods with the same name `method_name`, but different parameters. Method overloading basically means that if you call `method_name` with two parameters, it will use the first method, and if you call it with three parameters, it will use the second method.

- But there is a **problem** with this approach. Python **does not** support method overloading in the same way that languages like Java or C++ do.

- The Solution

  - We can achieve method overloading in Python through default arguments or variable-length arguments.

    ```python
    class Calculator:
        # Method 1: Default arguments
        def add(self, a: int, b: int, c: int = 0) -> int:
            return a + b + c
    
        # Method 2: Variable-length arguments
        def add_multiple(self, *args: int) -> int:
            return sum(args)
    ```

- Example Usage: 

  ```python
  calc = Calculator()
  
  print(calc.add(5, 10))        # Output: 15
  print(calc.add(5, 10, 15))    # Output: 30
  
  print(calc.add_multiple(5, 10, 15, 20))    # Output: 50
  print(calc.add_multiple(1, 2))      
  ```

- The above code demonstrates two methods that achieve method overloading-like behavior.
  - **Using Default Arguments:**
    - In the first `add` method, we make the third parameter optional by giving it a default value of 0
    - This allows the method to work with either 2 or 3 arguments
    - When called with 2 arguments, `c` defaults to 0
    - When called with 3 arguments, all values are used
  - **Using Variable-Length Arguments:**
    - The `add_multiple` method uses `*args` to accept any number of arguments
    - The star `*` before `args` tells Python this method can accept any number of inputs. In the example, you can see that it accepts 4 and 2 arguments.
    - We use the built-in `sum()` function to add all the numbers together
    - Note ➡️ Remember that while this achieves similar results to traditional method overloading, it's not technically the same thing. Python will always execute the same method; we're just making that method flexible enough to handle different numbers of arguments.

## Duck Typing

- **Duck Typing** is a polymorphism concept where the type of an object is determined by its behavior rather than its explicit declaration. In other words, if an object has the methods or attributes that are required by a function or method, it can be used in that context, regardless of its actual class or type.

- The name **Duck Typing** comes from the phrase "If it walks like a duck and quacks like a duck, then it's a duck!"

  ```python
  class IronMan:
      def attack(self) -> str:
          return "Repulsor Blast!"
  
  class Thor:
      def attack(self) -> str:
          return "Lightning Strike!"
  
  def hero_attack(hero) -> None:
      print(hero.attack())
  
  # Create heroes and attack!
  iron_man = IronMan()
  thor = Thor()
  
  hero_attack(iron_man)  # Repulsor Blast!
  hero_attack(thor)      # Lightning Strike!
  ```

- We can see that `hero_attack` doesn't check the type of the object, it only checks if the object has the `attack` method.

- This is not possible in languages like Java or C++. In those languages, we need to declare the type of the object and then use it. Python makes this possible because it is a [dynamically typed language](https://neetcode.io/problems/python-dynamic-typing).

- Why use Duck Typing ? 

  - **Flexibility:** We don't need `IronMan` or `Thor` to inherit from a `Superhero` class. Any new hero class that has an `attack()` method will work with `hero_attack()!`
  - **Less Code:** No parent classes, no inheritance syntax. Just create classes with the methods you need.
  - **Loose Coupling:** `IronMan` doesn't need to know `Thor` exists, and neither needs to know about a `Superhero` parent class. They just need their `attack()` method!
  - Note ➡️ While Duck typing is powerful, it can also be error prone. We may accidentally call a method that doesn't exist on the object.

