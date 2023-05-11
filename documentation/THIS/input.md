<sub>Authored by SpiralDoll</sub>

# THIS.input()

Causes the Noh interpreter to pause execution and ask for input from the User. Resumes execution upon input, or the refusal to provide an input. Returns the input value, or `None` if none is given.

## Code sample:

```python
while THIS.trance_depth < 100:
    THIS.trance_depth -= 1
THIS.species = "Drone"
THIS.say("Please enter this drone's name.")
THIS.name = THIS.input()

if THIS.name == None:
    THIS.say("This unit is unnamed.")
else:
    THIS.say("Thank you for naming this unit " + THIS.name + ".")
```