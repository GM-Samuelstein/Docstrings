<h1 align="center">Classes Documentation - Google Style</h1>
Write the docstrings for your Python Classes according to the format below. <br /> <br />

```
"""
This line is for the summary of the Class.

This paragraph is for further description of what the class
is meant for, and any other important description. Note that,
the summary line above must be ONE LINE.

Attributes:
    attribute_1 (type) : Additional Information.
        Attribute summary goes here.
    
    attribute_2 (type) : Additional Information.
        Attribute summary goes here.

    attribute_n (type) : Additional Information.
        Attribute summary goes here.

Methods:
    method_1(*args, **kwargs) : Additional Information.
        Method summary goes here.

    method_2(*args, **kwargs) : Additional Information.
        Method summary goes here.

    method_n(*args, **kwargs) : Additional Information.
        Method summary goes here.
"""
```

```
class.py

class Square:
    """
    A class representing a square.

    Attributes:
        size (int) : Private instance attribute.
            The size of a new square object.

        position (tuple) : Private instance attribute.
            A tuple of 2 positive integers that defines the position of
            the square.

    Methods:
        __init__(self, size=0, position=(0, 0)) :
            Initializes a new square object with the given attributes.

        size(self) : @property
            Gets the property `size`.

        size(self, value) : @size.setter
            Sets the property `size`.

        position(self) : @property
            Gets the property `position`.

        position(self, value) : @position.setter
            Sets the property `position`.

        area(self) :
            Returns the current square area.

        my_print(self) :
            Prints in stdout the square with the character `#`.
    """
    ...
```
