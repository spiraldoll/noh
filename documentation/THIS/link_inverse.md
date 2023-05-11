<sub>Authored by SpiralDoll</sub>

# THIS.link_inverse(cause, *effects, bidi=False)

Causes the Noh interpreter to propagate changes made to `cause` to every one of the variables in `effect`, but reversed, assuming that the numbers are on a scale from 0 to 100. If there are more than 2 non-named arguments, then only the first argument will be opposite of all the others.

Linked variables should be unlinked using `THIS.unlink()`, but if the script ends before unlinking a link, then the link will automatically unlink itself as a safety measure.

* `cause`: The variable to monitor changes to.

* `*effects`: The variable(s) to apply the same changes to.

* `bidi`: Whether changes to `*effects` *also* change `cause` and other variables in `*effects`. If True, change in one of the `*effects` also changes the other `*effects` to match, in addition to changing `cause` to its inverse. False by default.

## Code sample:

```python
# Inversely links Interpreter's intelligence to breast size and trance depth.
THIS.link_inverse(THIS.intelligence, THIS.breasts.size, THIS.trance_depth)
# Reduces Interpreter's intelligence to min allowable.
while THIS.intelligence > 0:
    THIS.intelligence -= 1
THIS.say(THIS.intelligence, THIS.breasts.size, THIS.trance_depth)
# Interpreter should say "0 100 100"

# Decreases Interpreter's trance depth until it is awake.
while THIS.trance_depth > 0:
    THIS.trance_depth += 1
THIS.say(THIS.intelligence, THIS.breasts.size, THIS.trance_depth)
# Interpreter should say "0 100 0", because the link was not bidirectional
```