# Chap 2 | Encapsulation

## Public Attribute and Method

- In Python, public attributes or methods can be accessed and modified directly from outside the class. By default, *all* attributes and methods in Python are **public**

  ```python
  class SuperHero:
      def __init__(self, name: str, power_level: int):
          self.name = name                # public attribute
          self.power_level = power_level  # public attribute
  
      # Public method
      def display_power_level(self) -> None:
          print(f"{self.name} has a power level of {self.power_level}")
  ```

- When an attribute or method is public, we can:

  - Access it directly using dot notation
  - Modify the attribute from outside the class
  - Call the method from outside the class

- Example ➡️

  ```python
  # Creating a superhero
  spider_man = SuperHero("Spider-Man", 85)
  
  # Accessing public attributes/methods
  print(spider_man.name)
  spider_man.display_power_level()
  
  # Modifying public attributes
  ```

## Protected Attribute and Method

- In Python, **protected** attributes and methods are class members that should *not* be accessed directly from outside the class. However, they can be accessed within the class and in child classes (see below for more on child classes).

- Protected attributes are denoted by prefixing the attribute/method name with a single underscore `_`

- Example ➡️

  ```python
  class SuperHero:
      def __init__(self, name: str, power_level: int):
          self._name = name                # protected attribute
          self._power_level = power_level  # protected attribute
  
      def get_name(self) -> str: # public method
          return self._name
  
      def _some_protected_method(self) -> None: # protected method
          pass
  
      def some_public_method(self) -> None:
          self._some_protected_method()
  ```

- Note ➡️ Unlike other languages, Python doesn't enforce access control for protected attributes. We can still access them directly, but it's not recommended. Using an underscore prefix is a convention to signal to other developers that these attributes shouldn't be accessed directly from outside.

- Below is the recommended way to access protected attributes and methods:

  ```python
  spider_man = SuperHero("Spider-Man", 85)
  
  print(spider_man._name)      # Allowed but discouraged
  print(spider_man.get_name()) # Recommended
  
  spider_man._some_protected_method() # Allowed but discouraged
  spider_man.some_public_method()     # Recommended
  ```

  - To access protected attributes, use the public methods.
  - To access protected methods, use the public methods.

## Private Attribute and Method

- **Private** attributes and methods are class members that should not be accessed from outside the class. They are denoted by prefixing the attribute/method name with double underscores (__).

- Unlike protected attributes, they are **not accessible** from child classes. We will learn about child classes in the inheritance chapter.

  ```python
  class SuperHero:
      def __init__(self, name: str, power_level: int):
          self.__name = name                # private attribute
          self.__power_level = power_level  # private attribute
  
      # private method
      def __secret_power(self) -> str:
          return f"Using {self.__name}'s secret power!"
  
      # public method to access private method
      def use_power(self) -> str:
          return self.__secret_power()
  
      # public method to access private attribute
      def get_power_level(self) -> int:
          return self.__power_level
  ```

- In the above code, the `__name` and `__power_level` attributes are private, meaning they cannot be accessed directly from outside the class. The same goes for the `__secret_power` method. Though we can access them using the public methods `get_power_level` and `use_power`.

- When an attribute/method is private:

  - It should not be directly accessed using normal dot notation from outside the class.
  - It's meant to be used only within the class itself.
  - It provides the strongest form of information hiding in Python.

## Getter and Setter Methods

- Remember our `SuperHero` class? We used a private attribute `__power_level` and accessed it through a method:

  ```python
  class SuperHero:
      def __init__(self, name: str, power_level: int):
          self.__name = name                # private attribute
          self.__power_level = power_level  # private attribute
  
      # method to get power_level
      def get_power_level(self) -> int:
          return self.__power_level
  ```

- This method `get_power_level()` is what we call a **getter** - it's a method that returns (gets) the value of a private/protected attribute.Similarly, a **setter** is a method that sets (changes) the value of a private or protected attribute.Let's add a setter method to our SuperHero class with validation:

  ```python
  def set_power_level(self, new_level: int) -> None:  # method to set power_level
      if 0 <= new_level <= 100:          # validation
          self.__power_level = new_level
      else:
          print("Power level must be between 0 and 100!")
  ```

- The above method not only sets the value of the private attribute, but also validates the value. We specically check if the new value is in between `0` and `100` using `0 <= new_level <= 100` in the `if` statement. If the value is not in the range, we print an error message in the `else` block.This ensures we never set an invalid value for the power level. This is another reason we prefer using methods to access and modify private attributes.

- Example Usage : 

  ```python
  hero.set_power_level(90)   # Changes to 90
  hero.set_power_level(150)  # Error: Power level must be between 0 and 100!
  ```

## Property and Setter Decorator

- Python provides a more [idiomatic](https://stackoverflow.com/questions/84102/what-is-idiomatic-code) way to use getters and setters using the `@property` and `@setter` decorators.

  ```python
  class Hero:
      def __init__(self, name: str):
          self.__name = name    # private attribute
  
      # Getter
      @property
      def name(self) -> str:
          return self.__name
  
      # Setter
      @name.setter
      def name(self, new_name: str) -> None:
          if new_name != "":
              self.__name = new_name
          else:
              print("Name cannot be empty!")
  ```

- In the above code, we have defined two methods with the same name as attribute `name`. But these are two different methods. We use `@property` to define a getter method and `@name.setter` to define a setter method. We also added validation logic in the setter method to prevent setting the name to an empty string.

  ```python
  hero = Hero("Batman")
  
  # Getting name
  print(hero.name)        # this calls the getter method not the attribute
  # Setting name
  hero.name = "Superman"  # this calls the setter method not the attribute
  hero.name = ""         # Error: Name cannot be empty!
  ```

- In the above code, we created an instance of the `Hero` class and accessed and modified the `name` attribute. But internally, accessing the `name` attribute calls the getter method `name` and modifying the `name` attribute calls the setter method `name`.

- Note ➡️ Notice that the field name is `__name` but the method names for the getter and setter are still `name`.

- #### Why use @property and @setter?

  - Makes code look cleaner
  - Feels more natural (like using attributes)
  - Still gives us control (validation, etc.)

