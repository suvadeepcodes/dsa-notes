# Chap 3 | Class Attributes

## Class Attributes

- When assembling the Avengers to fight Thanos, certain information needs to be shared across all heroes. For instance, Nick Fury needs to track how many heroes we have ready for battle. This is where **class attributes** come in.

  ```python
  class Superhero:
      hero_count = 0      # Class attribute
  
      def __init__(self, name: str, power: str):
          self.name = name      # Instance attribute
          self.power = power    # Instance attribute
          Superhero.hero_count += 1
  ```

- In the above code, `hero_count` is a class attribute, where as `name` and `power` are instance attributes.

- In this case, `hero_count` belongs to the entire superhero class - not to individual heroes. This attribute is shared by all instances of the class. Unlike instance attributes, we don't use the `self` keyword to access class attributes.

- Class attributes must be declared *outside* the `__init__` method and without the `self` keyword.

  ```python
  iron_man = Superhero("Iron Man", "repulsor beams")
  thor = Superhero("Thor", "lightning")
  
  print(f"Heroes ready to face Thanos: {Superhero.hero_count}")  # This should print 2
  ```

- In the above code, we created two instances of the `Superhero` class, `iron_man` and `thor`. We then accessed the class attribute `hero_count` using the class name `Superhero.hero_count`.

- Notice that we access class attributes using the class name, not the instance name. This is because class attributes are shared by all instances of the class. Class attributes can be updated outside the class as well.

- Note ➡️ We can also access the class attribute using the instance of the class `iron_man.hero_count` but it's not recommended. That's because the class attribute belongs to the class, not to the instance.

## Class vs Instance Attributes

- The below example shows a `BankAccount` class with class and instance attributes.

  ```python
  class BankAccount:
      total_accounts = 0    # Class attribute: Shared by ALL accounts
      total_balance = 0     # Class attribute: Tracks bank's total money
  
      def __init__(self, name: str, balance: float):
          self.name = name        # Instance: Each account has unique owner
          self.balance = balance  # Instance: Each account has unique balance
          BankAccount.total_accounts += 1
          BankAccount.total_balance += balance
  ```

  - We use class attributes to track bank-wide information that is shared by all accounts, such as the total number of accounts and the total balance of all accounts.
  - We use instance attributes to track information that is unique to each account, such as the account number and the balance of the account.

## Class Methods

- So far the methods we have used were all related to the instance of the class. For example, we used `use_power` method which was used by a single superhero.

- Sometimes we need special methods that work with the entire class rather than individual instances. For example, we may want to upgrade the training level of all heroes at once. Let's see how we can do that using class methods.

  ```python
  class Superhero:
      training_level = 1  # Class attribute
  
      def __init__(self, name: str, power: str):
          self.name = name         # Instance attribute
          self.power = power       # Instance attribute
  
      @classmethod
      def upgrade_training(cls) -> None:
          cls.training_level += 1
          print(f"All heroes now at training level {cls.training_level}")
  ```

- In the above `Superhero` class, the `upgrade_training` method is a class method.

  - It uses `@classmethod` decorator to define the class method
  - It uses `cls` as the first parameter instead of `self`
  - It upgrades the `training_level` (a class attribute) by `1`
  - `cls` is used to access the class attribute instead of the class name `Superhero`

- The below code shows how the recommended way to call the class method:

  ```python
  Superhero.upgrade_training()     # Recommend way to use class method
  print(Superhero.training_level)  # 2
  ```

- The below code shows how the class method can be called using an instance of the class, which is *not* recommended:

  ```python
  iron_man = Superhero("Iron Man", "Flying")
  iron_man.upgrade_training()     # Works but not recommended
  print(iron_man.training_level)  # 2
  ```

- **Important**: Class methods are similar to class attributes. They are shared by all instances of the class. This also means that they do *not* have access to instance attributes, which is why we don't use `self` in class methods. Class methods can be defined with additional parameters, after the `cls` parameter.

## Static Methods

- So far we've seen instance methods (using `self`) and class methods (using `cls`).

- There are also **static methods** which are similar to class methods but they don't have access to `self` or `cls`. They do not have access to instance attributes, but they *can* still access class attributes using the class name.

- They are just regular functions that live inside a class for organizational purposes.

  ```python
  class Superhero:
      def __init__(self, name: str, power: str):
          if not self.is_valid_power(power):
              raise ValueError(f"Invalid power: {power}")
          self.name = name        # Instance attribute
          self.power = power      # Instance attribute
  
      @staticmethod
      def is_valid_power(power: str) -> bool:
          valid_powers = ['Flying', 'Strength', 'Speed', 'Intelligence']
          for valid_power in valid_powers: # Iterate over each valid power and check if the power matches
              if power == valid_power:
                  return True
          return False
  ```

- In the above code, we defined a class `Superhero` with a static method `is_valid_power`. We call this method using the `self` parameter within the `__init__` method for validation before creating the hero.

- Alternatively, we could have defined this method outside the class, but this method would never be needed outside the class. Thus, it's best to define it inside the class for organizational purposes.

- Below is an example of how this class can be used. Notice that we can also call the static method using the class name.

  ```python
  print(Superhero.is_valid_power('Flying'))         # True
  print(Superhero.is_valid_power('Mind Reading'))   # False
  
  iron_man = Superhero("Iron Man", "Flying")        # Works
  
  mind_reader = Superhero("Hero", "Mind Reading")
  ```

  