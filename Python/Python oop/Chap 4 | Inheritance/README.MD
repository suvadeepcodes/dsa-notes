# Chap 4 | Inheritance

## Inheritance Basics

- **Inheritance** is a fundamental concept in object-oriented programming that allows you to create a new class based on an existing class. The new class, known as the **child class** or **subclass**, inherits properties and methods from the existing class, known as the **parent class** or **superclass**.

- Inheritance allows us to create new classes based on existing ones. Instead of modifying an existing class, inheritance lets us reuse its code while only writing the differences we need in the new class.

- Example ➡️  For example, let's say we have a class `Superhero`.

  ```python
  class Superhero:
      def __init__(self, name: str, power: str):
          self.name = name
          self.power = power
  ```

- Now we want to create a new class `Avenger` that is a modified version of the `Superhero` class. The `Avenger` class will have the same properties and methods as the `Superhero` class, but we can also add a new method `fly` that is specific to the `Avenger` class.

  ```python
  class Avenger(Superhero):
      def fly(self) -> None:
          print(f"{self.name} can fly using {self.power}")
  
  iron_man = Avenger("Iron Man", "repulsor beams")
  iron_man.fly() # Iron Man can fly using repulsor beams
  ```

- In this example, the `Avenger` class inherits from the `Superhero` class. The `Avenger` class has all the properties `name` and `power` from the `Superhero` class, plus the `fly` method, even though we didn't define them in the `Avenger` class.

- The syntax for inheriting from a class is as follows:

  ```python
  class ChildClass(ParentClass):
      # Child class code here
  ```

- When an instance of a child class is created, the constructor of the parent class is called automatically. This is why we can pass the arguments `name` and `power` to the `Avenger` class constructor, even though they are not defined in the `Avenger` class.

## Method Overriding

- So far, we have seen how to inherit properties and methods from a parent class. But what if we want to change the behavior of a method in a child class? This is where method overriding comes in.

- Method overriding allows us to change the behavior of a method in a child class. This is useful when we want to change the behavior of a method that is inherited from a parent class.

- Let's see an example:

  ```python
  class Superhero:
      def __init__(self, name: str):
          self.name = name
  
      def fight(self) -> None:
          print("Superhero fights with advanced weapons!")
  
  class Avenger(Superhero):
      # Override the fight method
      def fight(self) -> None:
          print("Avenger fights with advanced weapons!")
  ```

- In this example, we have a `Superhero` class with a `fight` method. We then have a `Avenger` class that inherits from the `Superhero` class. The `Avenger` class has its own `fight` method that overrides the `fight` method in the `Superhero` class.

  ```python
  avenger = Avenger("Iron Man")
  avenger.fight() # Output: Avenger fights with advanced weapons!
  ```

- Above, we create an instance of the `Avenger` class and call the `fight` method. The `fight` method in the `Avenger` class is called instead of the `fight` method in the `Superhero` class.

- The method from the child class is called instead of the method from the parent class. This is method overriding.

## Super Function

- `super()` is a built-in function in Python that allows you to call methods from a parent class. It's a powerful tool for working with inheritance.

- Why use `super()` ? 

  - When working with inheritance, there are often situations where you want to extend rather than completely replace a parent class's behavior. For example:
    - You might want to add extra initialization steps while keeping the parent's initialization
    - You may need to enhance an existing method while maintaining its core functionality
    - You could need to access parent class properties while adding new ones

- Let's see an example 

  ```python
  class ParentClass:
      def parent_method(self) -> None:
          print("This is the parent class method")
  
  class ChildClass(ParentClass):
      def child_method(self) -> None:
          super().parent_method()
          print("This is the child class method")
  ```

- In this example, the `super()` function is used to call the `parent_method` from the `ParentClass`. The `super()` method can be visualized as an object that points to the parent class. Remember `super()` itself doesn't take any arguments, but it can be used to call the parent class's methods.

- #### Syntax for `super()` function

  ```python
  super().parent_method() # Call parent class's instance method
  
  super().__init__() # Call parent class __init__ method
  
  super().parent_property # Access parent class property
  ```

## Multiple Inheritance 

- Multiple inheritance is a feature in object-oriented programming where a class can inherit attributes and methods from more than one parent class. While powerful, it is generally considered an [anti-pattern](https://stackoverflow.com/questions/406081/why-should-i-avoid-multiple-inheritance).

- Lets see an example : 

  ```python
  class Swimmer:
      def swim(self):
          print("Swimming")
  
  class Flyer:
      def fly(self):
          print("Flying")
  
  # Ducks inherits from both Swimmer and Flyer
  class Duck(Swimmer, Flyer):
      pass
  ```

- In this example, the `Duck` class inherits from both the `Swimmer` and `Flyer` classes. This means that a `Duck` object will have access to both the `swim` and `fly` methods. The names of the parent classes are passed as arguments to the `Duck` class. Currently, we are only using the methods from the parent classes so we just use the `pass` keyword to indicate that we are not adding any new methods or attributes to the `Duck` class.

- Below, we create an instance of the `Duck` class and call the `swim` and `fly` methods.

  ```python
  duck = Duck()
  duck.swim() # Should print "Swimming"
  duck.fly()  # Should print "Flying"
  ```

- Be careful with multiple inheritance. It can be useful in scenarios where a class needs to inherit behavior from multiple sources. However, it can also lead to complex class hierarchies, and it's important to ensure that the inheritance is logical and avoids conflicts.

- In most cases, you should *not* use multiple inheritance. But you may see code like this in the wild.

- Basic Syntax ➡️

  ```python
  class ChildClass(ParentClass1, ParentClass2, ...):
      # Class body
  ```

  