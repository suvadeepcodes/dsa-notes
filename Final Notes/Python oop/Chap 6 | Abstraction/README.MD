# Chap 6 | Abstraction

## Abstraction

- **Abstraction** is the concept of hiding complex implementation details and showing only the necessary features to the outside world. Think of it like a TV remote - you just press buttons to change channels, not caring about the electronics inside.

- Data Abstraction

  - Hides complex data details
  - In Python achieved through: private variables

- **Behavioral Abstraction**

  - Hides complex method implementations
  - In Python achieved through: abstract methods

- Let's understand abstraction through a simple example:

  ```python
  class TempConverter:
      def __init__(self, celsius):
          self._celsius = celsius    # Hidden internal state
  
      def get_fahrenheit(self) -> float:
          return (self._celsius * 9/5) + 32
  
  temp = TempConverter(25)
  print(temp.get_fahrenheit())  # 77.0
  ```

- In this code:

  - The `get_fahrenheit` method is the public interface that *abstracts* away the internal implementation details
  - Internal variable `_celsius` is hidden from users
  - Users don't need to understand the conversion formula

## Abstract Method and Class

- So far we have seen the general concept of abstraction. Now let's explore two key concepts which are used to achieve abstraction in Python.

  - An **abstract method** is a method that is declared in a base class, but contains no implementation. The child class must implement the abstract method. Abstract methods are used to enforce a contract on subclasses. Subclasses must implement the abstract method, otherwise they will raise an error.
  - An **abstract class** is a class that contains one or more abstract methods. It serves as a blueprint for other classes and cannot be instantiated on its own.

- Example ➡️

  ```python
  from abc import ABC, abstractmethod
  
  class Superhero(ABC):
      def __init__(self, name):
          self._name = name
  
      def get_name(self) -> str: # public methods
          return self._name
  
      @abstractmethod
      def fly(self) -> str:
          pass
  
  class Superman(Superhero):
      def fly(self) -> str:
          return "Up up and away!"
  ```

  - In the above example:

    - `Superhero` is the base abstract class that inherits from `ABC`. In python, abstract classes are created by inheriting from `ABC`.
    - The `@abstractmethod` decorator marks `fly()` as an abstract method. In python, abstract methods are created by decorating a method with `@abstractmethod` decorator.
    - `Superman`, and any other child class that inherits from `Superhero`, must implement the `fly()` method.
    - Non-abstract methods like `get_name()` are optional to override.

  - Note you can't create an instance of `Superhero` class because it is an abstract class and has an abstract method.

    ```python
    hero = Superhero("Superman")
    ```

    - This will raise a `TypeError` because the `fly()` method is not implemented.

    - #### Why use abstract method?

      - Abstract methods are a powerful tool for achieving abstraction because they:
        - Hide implementation details (abstraction): The base class only declares what methods must exist, without specifying how they work.
        - Enforce consistency: Child classes must implement these methods, ensuring a standard interface across all subclasses, which allows for polymorphism.
        - Prevent incomplete objects: You can't create instances of classes with abstract methods, ensuring only fully-implemented classes can be used.

## Interface

- An **interface** in Python is just like an abstract class, but with one key difference: it contains only abstract methods. While abstract classes can mix both concrete and abstract methods, an interface is a "pure" abstract class. It only defines a contract of what methods must be implemented.

  ```python
  from abc import ABC, abstractmethod
  
  class Database(ABC):
      @abstractmethod
      def connect(self) -> bool:
          pass
  
      @abstractmethod
      def query(self, sql: str) -> list:
          pass
  ```

- This is an interface because it contains only abstract methods `connect` and `query` - it serves as a pure contract that specifies what methods implementing classes must provide. While some programming languages have dedicated `interface` keywords, Python achieves the same functionality using abstract classes (`ABC`).

- #### Interfaces vs Abstract Classes

  - Key differences between interfaces and abstract classes in Python:
    - Interfaces contain only abstract methods (pure contract)
    - Abstract classes can mix both concrete and abstract methods
    - Abstract classes can have constructors (`__init__`), While Python allows `__init__` methods in interfaces, it's considered bad practice as interfaces should focus purely on method contracts

