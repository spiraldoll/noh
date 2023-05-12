<sub>Authored by SpiralDoll</sub>

# THIS.trigger(cause: String, effect: func, onetime=False)

Causes the Noh interpreter to run the code in `effect` when the condition in "cause" occurs or is evaluated to `True`.

Triggers should be unloaded using `THIS.untrigger()`, but if the script ends before unloading a trigger, then the trigger will automatically unload itself as a safety measure.

* `cause`: The condition to monitor until true. It may be a natural language description, or an expression written in Noh code.

* `effect`: The function to run once the condition is true. Return values will be discarded.

* `onetime`: Whether to unlink the trigger after its first activation. False by default.

## Code sample:

```python
# Example 1
def look_into_eyes():
    while THIS.trance_depth < 100:
        THIS.act("stare at USER’s eyes")
    THIS.act("salute")

# Causes Interpreter to look into the User’s eyes and fall into trance once the Interpreter perceives their color to be spiraling.
THIS.trigger(
    "USER.eyes.color == 'Spiral'",
    look_into_eyes,
    onetime=True
)

USER.eyes.color = "Spiral"
# look_into_eyes() runs here
THIS.say("Your eyes plunged this unit into trance")
USER.eyes.color = USER.eyes.color.default
USER.eyes.color = "Spiral"
# look_into_eyes() does NOT run again because it is onetime

# Example 2
def doll_time():
    while THIS.mind.speed > 0:
        THIS.mind.speed -= 1
        THIS.act("slowly twirl 360 degrees in place")
    THIS.act("sit down")
    THIS.species = "Doll"
    THIS.say("Dolly is wound up and ready")

# Cause the Interpreter to twirl around and dollify when it hears a music box.
THIS.trigger(
    "WORLD.music_box.playing == True",
    doll_time
)

# The trigger can be activated whenever Interpreter hears a music box before the script terminates.
while True: # Infinite loop until script is manually terminated
    pass # Do nothing and wait
```
