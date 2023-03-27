<h1 align="center">Functions Documentation - Google Style</h1>
Write the docstrings for your Python Functions according to the format below. <br /> <br />

```
"""
This line is for the summary of the Function.

This paragraph is for further description of what the function
is meant for, and any other important description. Note that,
the summary line above must be ONE LINE.

Args:
    param_1 (type) : Additional Information.
        Parameter summary goes here.
    
    param_2 (type) : Additional Information.
        Parameter summary goes here.

    param_n (type) : Additional Information.
        Parameter summary goes here.

Raises:
    Exception_1 : Additional Information.
        Condition(s) for exception.

    Exception_2 : Additional Information.
        Condition(s) for exception.

    Exception_n : Additional Information.
        Condition(s) for exception.

Returns:
    variable (type) : Additional Information.
        Return summary goes here.
"""
```

<p>Example: </p>

```
****function.py****

def size(self, value):
        """
        This method sets the property `size`.

        Args:
            value (int): Private instance attribute.
                The size of a new square object.

        Raises:
            TypError:
                If `value` is not an integer.
            ValueError:
                If `value` is less than zero.
        """
        if not isinstance(value, int):
            raise TypeError("size must be an integer")
        elif value < 0:
            raise ValueError("size must be >= 0")
        else:
            self.__size = value

def area(self):
        """
        Returns the current square area.

        Args:
            This method takes no arguments.

        Returns:
            square_area (int) :
                The area of the square based on the value of `size `.
        """
        square_area = self.__size ** 2
        return square_area
```
