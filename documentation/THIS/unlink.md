<sub>Authored by SpiralDoll</sub>

# THIS.unlink(cause, *effects, bidi=False)

Causes the Noh interpreter to stop propagating changes made to `cause` to every one of the variables in `effect`, linked through the `link()` or `link_inverse()` function.

* `cause`: The variable to stop monitoring changes to.

* `*effects`: The variable(s) to stop applying the same changes to.

* `bidi`: Whether to cancel the inverse link. False by default.

## Code sample:

```python
# Links Interpreter's breast size to trance depth.
THIS.link(THIS.breasts.size, THIS.trance_depth)
# Inversely links Interpreter's breast size to intelligence and levels of shame bidirectionally.
THIS.link(THIS.breasts.size, THIS.intelligence, THIS.emotions.shame, bidi=True)
# Increases Interpreter's breast size to max allowable.
while THIS.breasts.size < 100:
    THIS.breasts.size += 1
THIS.say(THIS.breasts.size, THIS.trance_depth, THIS.intelligence, THIS.emotions.shame)
# Interpreter should say "100 100 0 0"

# Unlink breast size to trance depth, intelligence, and shame
THIS.unlink(THIS.breasts.size, THIS.trance_depth)
THIS.unlink(THIS.breasts.size, THIS.intelligence)
THIS.unlink(THIS.breasts.size, THIS.emotions.shame)
# Since the link to intelligence and shame was bidirectional, but unlinking was not bidirectional, intelligence and shame are still linked to breast size, as well as with each other.
while THIS.intelligence < 100:
    THIS.intelligence += 1
THIS.say(THIS.breasts.size, THIS.trance_depth, THIS.intelligence, THIS.emotions.shame)
# Interpreter should say "0 100 100 100"
```