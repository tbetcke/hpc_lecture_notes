# Python classes
If you've not used Python classes before, this guide will give you an introduction to what they are and what they are used for.

In general, a `class` is a set of instructions for how to create an object. An instance of a class is the object that is created from the class.
As an example, we can create a class that defines a fraction.

```python
from math import gcd


class Fraction:
    """A fraction."""

    def __init__(self, numerator, denominator):
        self.numerator = numerator
        self.denominator = denominator

    def print_numerator(self):
        print(self.numerator)

    def __str__(self):
        """Get string representation."""
        return str(self.numerator) + " over " + str(self.denominator)

    def __add__(self, other):
        """Add two fractions."""
        assert isinstance(other, Fraction)
        new_numerator = self.numerator * other.denominator + other.numerator * self.denominator
        new_denominator = self.denominator * other.denominator
        common_factor = gcd(new_numerator, new_denominator)
        return Fraction(new_numerator // common_factor, new_denominator // common_factor)

    def __mul__(self, other):
        """Multiply two fractions."""
        assert isinstance(other, Fraction)
        new_numerator = self.numerator * other.numerator
        new_denominator = self.denominator * other.denominator
        common_factor = gcd(new_numerator, new_denominator)
        return Fraction(new_numerator // common_factor, new_denominator // common_factor)
```

This class contains a number of functions: functions inside a class are called methods.
Each method starts with the `self` input: this refers to the instance of the class itself and can be used to store information
that other methods will need. (You could use another name instead of `self` but it's very very common practice to use `self`.)
Function that start and end with a double underscore (`__`) are special methods.

The special method `__init__` is run when an instance of the class is created. In this function, we store the numerator and denominator of the
fraction as `self.numerator` and `self.denominator`.

We can create a fraction and call the `print_numerator` method like this:

```python
half = Fraction(1, 2)
half.print_numerator()
```

This first line will run `__init__` with `half` as `self`, `1` as `numerator` and `2` as `denominator`. The second line will run `print_numerator` with `half` as `self`, and will therefore
print `1`.

The special method `__str__` defines what happens when you `print` an instance of your class. In our example, `print(half)` will print `1 over 2`.

The special method `__add__` defines what the `+` operator does. If you read the implementation above, you can see that `__add__`
is adding fractions in the way you would expect. For example, you can add two fractions like this:

```python
half = Fraction(1, 2)
third = Fraction(1, 3)
print(half + third)
```

The special method `__mul__` defines what the `*` operator does. For example, you can multiply two fractions like this:

```python
half = Fraction(1, 2)
third = Fraction(1, 3)
print(half * third)
```

There are a lot more special methods that you can use, including those to define the behaviour of `-`, `/`, `//`, `**`, `@`, `[]`, `=`, `<`, `<=`, `>`, and `>=`. You can find
(details of these in the Python documentation](https://docs.python.org/3/reference/datamodel.html#specialnames)
