<sub>Authored by SpiralDoll</sub>

# THIS.link(cause, *effects, bidi=False)

Causes the Noh interpreter to propagate changes made to `cause` to every one of the variables in `effect`.

Linked variables should be unlinked using `THIS.unlink()`, but if the script ends before unlinking a link, then the link will automatically unlink itself as a safety measure.

* `cause`: The variable to monitor changes to.

* `*effects`: The variable(s) to apply the same changes to.

* `bidi`: Whether changes to `*effects` *also* change `cause` and other variables in `*effects`. False by default.

## Code sample:

```python
# Links Interpreter's breast size to libido (but not the other way around).
THIS.link(THIS.breasts.size, THIS.libido)
# Increases Interpreter's breast size to max allowable.
while THIS.breasts.size < 100:
    THIS.breasts.size += 1
THIS.say(THIS.breasts.size, THIS.libido)
# Interpreter should say "100 100" because THIS.breasts.size is linked to THIS.libido

# Decreases Interpreter's libido to min allowable.
while THIS.libido > 0:
    THIS.libido -= 1
THIS.say(THIS.breasts.size, THIS.libido)
# Interpreter should say "100 0" because THIS.libido is not linked to THIS.breasts.size
```