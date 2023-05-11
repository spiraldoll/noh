<sub>Authored by SpiralDoll</sub>

Here are some relatively advanced concepts that a Noh programmer and interpreter may need to know.

# Scope

Variables in Noh are only valid within the scope that it is defined, unless it is derived from a Singleton.

```python
x = 0
if THIS.awareness > 0:
    x = 5
    y = 10
    THIS.say(x) # Interpreter says "5"
    THIS.say(y) # Interpreter says "10"
    THIS.awareness = 0
THIS.say(x) # Interpreter says "5"
THIS.say(y) # Interpreter raises an error because the variable y does not exist here
```

# Declaration shortcuts

Multiple variables may be declared, as in Python.

```python
x, y, z = 1, 2, 3
THIS.say(x) # Interpreter says "1"
THIS.say(y) # Interpreter says "2"
THIS.say(z) # Interpreter says "3"

powerpuff = ["Blossom", "Bubbles", "Buttercup"]
x, y, z = powerpuff
THIS.say(x) # Interpreter says "Blossom"
THIS.say(y) # Interpreter says "Bubbles"
THIS.say(z) # Interpreter says "Buttercup"

x = y = z = 0
THIS.say(x) # Interpreter says "0"
THIS.say(y) # Interpreter says "0"
THIS.say(z) # Interpreter says "0"
```

# Errors/Exceptions

Noh's Exceptions, casually referred to as errors, cause an immediate pause in execution, unless a `try catch` structure is used.

When an error is raised and not caught, the Interpreter states that an exception

```python
x, y = 0, 0
THIS.say(x / y) # Raises an exception due to division by zero
THIS.act("Salute")
```

When running this script called `test.noh`, this is one possible dialogue between the User and the Interpreter.

> **User:** `noh test.noh`

> **Interpreter:** "An exception occurred."

> **User:** "State details."

> **Interpreter:** "An error occurred on Line 2 due to a division by zero."

> **User:** "Understood. Ignore that line and continue."

> **Interpreter:** "Affirmative."

> *The Interpreter salutes and finishes the script.

When an error is raised and caught by an `except` block, a predetermined set of steps may be taken.

```python
x, y = 0, 0
try:
  THIS.say(x / y)
except:
  THIS.say("The mathematical operation caused an error.")
THIS.act("Salute")
```

This can also be useful for dealing with abreactions.

# Optional arguments

Functions may have optional arguments. Optional arguments can be created by adding a `=` after its name (and/or data type).

```python
def salute_user(name=None):
    if name == None:
        name = USER.name
    THIS.say("This unit obeys " + name + ".")

# Assuming that the primary user's name is "Mistress Foo":

salute_user() # Interpreter says "This unit obeys Mistress Foo."
salute_user("Master Bar") # Interpreter says "This unit obeys Master Bar."
salute_user() # Interpreter says "This unit obeys Mistress Foo."
salute_user("Admin Hoge") # Interpreter says "This unit obeys Admin Hoge."
```