<sub>Authored by SpiralDoll</sub>

Welcome to Noh! This document should be the first thing you read in order to get started with becoming a Noh programmer. (Or Noh interpreter, if you so desire~)

Noh syntax is modeled after Python, so if you are familiar with that, you will find this simple.

---

# Variables

Variables are automatically created as soon as it is referred to.
For example, to define a variable called `counter`, then add 1 to it, you write:

```python
counter = 0
counter += 1
```

To make sure that a variable is a specific data type (see "Types" below), you may also add an annotation.

```python
counter = 0
counter = "bacon" # succeeds
```
vs.
```python
strict_counter: int = 0
strict_counter = "bacon" #error, because "bacon" is not an int
```

Variable names may contain lowercase letters, underscores (`_`), and digits;
digits may **not** be the first letter of a variable name.

---

# Comments

Comments are lines that only provide a supplementary note to the programmer, and in some cases the Noh interpreter.

Any line beginning with `#` is a comment.

If a line contains `#` (outside of an expression), then the rest of the line after the `#` is a comment.

```python
counter = 0 # Implicitly declares the variable 'counter'
# Add 1 to the counter
counter += 1
# Now the counter should store the value 1
```

---

# Singletons

Noh has several singletons, which are all-caps variables that represent something.

* `THIS` refers to the Noh interpreter.
* `USER` refers to the user using the Noh interpreter.
  * If there are multiple users, a specific user may be disambiguated with a name (e.g. `USER["Mistress Foo"]`) or with a numerical index (e.g. `USER[0]` for the first person to interact with the Noh script).
* `WORLD` refers to the world around the Noh interpreter, or its perception of it.

Singletons may contain parameters, such as `THIS.trance_depth` and `USER.voice`.
There is no exhaustive list of parameters, as every Noh interpreter is different.
A Noh programmer may define arbitrary variables, which the Noh interpreter will automatically interpret and map based on the name of the variable.

Parameters may be nested using `.`. For example, the color of the user's eyes may be equally validly be written as `USER.eye_color` or `USER.eyes.color`.

---

# Types

Noh has several data types:

* `null`: The lack of a value.
* `bool`: A boolean only has two values: `True` or `False`. This can also be thought of as "yes or no", "on or off", and "activated or deactivated".
* `int`: A whole number. Unless otherwise stated, an `int` variable will be on a scale of 0 to 100.
* `float`: A number that may have a fractional part.
  * Because Noh interpreters do not actually use the IEEE 754 standard, or any floating-point binary representation of any sort, this is actually kind of a misnomer.
* `string`: A string of characters.
  * To declare a string, enclose the text in `'single quotes'` or `"double quotes"`; you will need to escape quotes that appear in the string itself, e.g. `'That\'s "Mistress Foo" to you.'` or `"That's \"Mistress Foo\" to you."`
* `list`: An array of data.
  * For example, to declare a list of the Powerpuff Girls' names, write `powerpuff = ["Blossom", "Bubbles", "Buttercup"]`.
  * Individual items of a list can be referred to with a number inside `[square brackets]`.
    * Lists are 0-indexed; this means that `"Blossom"` is `powerpuff[0]`, not `powerpuff[1]`.
    * Lists may have a negative index, in which case it is counted from the back. `powerpuff[-1]` is `"Buttercup"`.
* `dict`: A dictionary of key-value pairs.
  * For example, to declare a dictionary of the NATO spelling alphabet, write `alphabet = {'A': 'Alfa', 'B': 'Bravo', 'C': 'Charlie'}`.
  * Dictionaries can be indexed by key, but not by value. In this example, `alphabet['A']` quickly gets you `'Alfa'`, but `alphabet['Alfa']` either gets you `null` or causes an error depending on the Noh interpreter.

---

# Arithmetic

Noh has the following arithmetic operations:

* `+ - * / > <`: As expected.
* `%`: Not percentage, but the remainder to a division (modulo).
  * e.g. `7 % 3` is `1`, because 7 divided by 3 is 2 remainder 1.
* `**`: Exponentiation.
  * e.g. `3 ** 3` is `27`, because 3 cubed is 27.
* `== !=`: Equals / not equals.
* `>= <=`: Greater than or equal to / less than or equal to.
* `!` or `not`: "Not"; Turns `True` into `False` and `False` into `True`.
  * It also turns 0 into `False` and all other numerical values into `True`.
* Noh interpreters familiar with Boolean logic may also implement `& | ^ ~` or `and or xor not`, but this has few use cases.

---

# Functions

Functions may have names containing lowercase letters, underscore, or digits (again, except as the first character).
Some functions may take arguments, which are values passed to be worked on by the function.

For example, to declare a function that salutes the user, write:

```python
def salute_user(name: string):
    THIS.act("Salute")
    THIS.say("Hello, " + name + ".")
    return
```

**The indentation is NOT optional!** Python, and by extension Noh, determines scope using indentation.

Functions may be called using the name followed by `()`, optionally enclosing any arguments.

```python
salute_user("Mistress Foo") # Interpreter salutes and says "Hello, Mistress Foo."
salute_user("Master Bar") # Interpreter salutes again and says "Hello, Master Bar."
```

Optionally, functions may `return` a value, which may be assigned to a variable or used immediately in an expression.

```python
def silly_math_example(x: int, y: int):
    return x * (y + 1) + 3

THIS.say(silly_math_example(3, 4))
# The Noh interpreter says "18".
```

