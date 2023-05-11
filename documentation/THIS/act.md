<sub>Authored by SpiralDoll</sub>

# THIS.act(command: String)

Causes the Noh interpreter to interpret the command given, and act it out.
The command must be either a command (e.g. `"Salute the user."`) or a description of the action (e.g. `"ahegao"`). It is important to use language that is clear, simple, and easy to understand, as well as to use words that the Noh interpreter knows already.

## Code sample:

```python
while THIS.loyalty < 100:
    THIS.act("Zombie-walk to the other end of the room.")
    THIS.act("Turn around 180 degrees.")
    THIS.act("Perform 4 squats.")
    THIS.act("Zombie-walk back where you started.")
    THIS.say("This unit obeys.")
THIS.act("Salute the user.")
THIS.act("Stand at attention.")
```