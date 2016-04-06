# Formatting character strings in Python

You are asked below to add calculated values to your plots using the `plt.text()` function. It can display character strings, integers and floating point values, but there are a few challenges to using the `plt.text()` function. The `print()` function behaves very similar to the `plt.text()` function, displaying text in the interpreter window rather than on a plot, so we can explore a few examples using the `print()` function rather than `plt.text()`. You can later apply these same ideas to your plots with the `plt.text()` function.

First, numerical values must be converted to character strings before they can be displayed as part of some text. For example, typing the text below will produce an type error.
```python
>>> print("I have "+4+" tacos")
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-1-13c2c5bb89fe> in <module>()
----> 1 print("I have "+4+" tacos")

TypeError: Can't convert 'int' object to str implicitly
```
The message states that we cannot concatenate (add together) character and numerical values in a single print statement. We can fix this by converting the integer value to a character string using the `str()` function.
```python
>>> print("I have "+str(4)+" tacos")
I have 4 tacos
```
Obviously, this is useful though there are some limitations to using `str()` for formatting numbers as we'll see below.

Use of the `str()` function can be applied to floating point numbers as well.
```python
>>> print("The value of pi is approximately "+str(355.0/113.0))
The value of pi is approximately 3.1415929203539825
```
Cool, but this example raises another issue. The approximation of pi above is only accurate to 7 decimal places, so it would be best to only display that number of decimal values. We can do this using a `format` string.
```python
>>> print("The value of pi is approximately {0:.7f}".format(355.0/113.0))
The value of pi is approximately 3.1415929
```
So, what happened? Previously, we had our text in quotation marks (`"The value of pi..."`) and then concatenated a numerical value that was converted to a character string using the `str()` function. With the `format` string, we put `{0:.7f}` in the location where we would like the number to be displayed and followed the text in quotation marks with `.format(355.0/113.0)`. With the `format` method we can specify how we would like text displayed, in our case the number of decimal places in our floating point value. The general syntax for the format method is
```python
{<key>:<format options>}.format(<value>)
```
where `<key>` refers to the position of an item in the list of values to be formatted (`0` if there is only one value), `<format options>` are the specifications for how to display the text, and `<value>` is the value you want to display. In our case, we specify we want the first floating point value (`0`) to be displayed with seven decimal places `{0:.7f}`. In this case, the number after the period is the number of decimal places to show and the "`f`" will display the text as a typical floating point number. Perhaps this is easier to understand with a second example for two numbers.
```python
>>> print("The value of pi is approximately {0:.7f}, which is a good approximation of {1:.36f}".format(355.0/113.0, np.pi))
The value of pi is approximately 3.1415929, which is a good approximation of 3.141592653589793115997963468544185162
```
Now we have our approximation (value `0`) displayed with 7 digits after the decimal point and the value of pi from the NumPy library (value `1`) displayed with 36 digits after the decimal place. In the format string we simply use commas to list the values in the order they are given in the text to be displayed. In cases where you have only one value to format, you can even omit the `0`. In this way we could alternatively display the approximate value of pi in scientific notation by deleting the `0` key and replacing the "`f`" with an "`e`".
```python
>>> print("The value of pi is approximately {:.7e}".format(355.0/113.0))
The value of pi is approximately 3.1415929e+00 
```
As you might imagine, there is a great deal of formatting that can be done with the `format` method, but you're likely to only need to change the number of decimal places for floating point values in the exercises today. More information about the format method is available on the [Python documentation page](https://docs.python.org/3.5/library/string.html#formatstrings).
