# Object-Oriented-Python
#### SOLID Principles of Object Oriented Programming
* Single Responsibility Principle: every class should have a single responsibility. There should never be more than one reason for a class to change.
* Open/Closed Principle: open for extension, but closed for modification.
* Liskov Substitution Principle: objects in a program should be replaceable with instances of their subtypes without altering the correctness of the program.
* Interface Segregation Principle: many client-specific interfaces are better than one general-purpose interface (low coupling, and high cohesion)
* Dependency Inversion Principle.
  - Abstractions should not depend upon details;
  - Details should depend upon abstractions.
  - ather than working with classes that are tight coupled, use interfaces.

#### Design Patterns
* **Wrap** simplified interface (aka facade pattern)
* **Extend** an existing collection to add features
* **invent** from scratch
* **Flywheel** design pattern: use stateless pack to implement strategy
  - no __init__ methhod
  - data must be passed in
  - can pass one strategy instance to multiple object

#### Decorator
* `@abstractmethod`: class cannot be instantiated
* `@overload`: different method with the same names but different arguments
* `@staticmethod`: bound to class
* `@classmethod`: require receiving class as first positional param

```python
class Position:
  @classmethod
  def getPositions(self, account, assets, db, archive=False):
    pass

Position.getPositions(account, assets, db)
```

#### Argument Parsing
* `*` packs arguments into a tuple
* `**` packs into dictionary (variable name must be provided)

#### Privacy
* Most names are public
* Use leading `_` in method for implementation details subject to change
* Dunder method `__` are internal to Python. Do not mess with dunder.

___
### Chapter III
#### String
* `__repr__`: intended for program read
  * in formatted string: `f"{obj!r}"`
* `__str__`: intended for human read
  * in formatted string: `f"{obj!s}"`

#### Mutability
* `==` calls `__eq__`
* `is` compares **ID** always
* Mutable
  * mutable object must not be hashed
  * only define `__eq__` but not `__hash__` (must override both)
* Immutable
  - define neither `__hash__` nor `__eq__`: both method compare `id`
  - define both methods to customize behavior
  - can be placed in map, set
* `__hash__` method: return `int`
  - must modulo `sys.hash_info.modulus`

#### Other method
* `__bool__`: can return `False` for empty collection
* `__byte__`L for serialization, but better to use `pickle` or `json` module

#### Comparator
Reflection rules, implement one from each of the four pair
```
(x < y, y > x)
(x <= y, y >= x)
(x == y, y == x)
(x != y, y != x)
```

#### Polymorphism
* Two classes are polymorphic when they share common attributes and methods
* One symptom of Pretty Poor Polymorphism is the reliance on `isinstance()` to determine subclass membership
  - violate encapsulation and class design
  - should provide a variant attribute or method implementation that varies based on the class
