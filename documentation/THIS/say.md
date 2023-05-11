<sub>Authored by SpiralDoll</sub>

# THIS.say(*objects, sep=' ', stream='text')

Causes the Noh interpreter to say the non-named arguments.

* `*objects`: Any number of variables. They will be separated by `sep` (spaces by default).

* `sep`: The separater between the variables.

* `stream`: Where the interpreter says the variables.
  * `'text'`: Text chat.
  * `'voice'`: Voice chat.
  * Other values may be valid if the Noh interpreter recognizes them.

## Code sample:

```python
while THIS.trance_depth < 100:
    THIS.trance_depth -= 1
THIS.species = "Drone"
THIS.say("Trance entered.")

THIS.say(2 + 3, 2 - 3, 2 ** 3) # Interpreter says "5 -1 8"
THIS.say(USER.name, "commands", THIS.species) # example of mixing variable types
```