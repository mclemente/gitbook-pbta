# Custom Actor Types/Sheets

As of the 0.2.0 version of the PbtA system, you can now make custom actor types in addition to characters and NPCs.

To define a custom actor type, you use the same structure as either characters or npcs, but you use your custom actor type name instead of character or npc in all of your properties. In addition, there's an optional baseType property on custom actor types to choose whether it should use the character sheet as its base (meaning a wider layout and with support for stats) or the npc sheet.

## Example Custom Actor Type

The following example would be added to the end of your sheetConfig TOML after all of your other settings.

In it, we've defined two custom actor types:

1. `foobar` - Custom actor type using the `npc` sheet as its `baseType`.
2. `ipsum` - Custom actor type using the `character` sheet as its `baseType`, which also allows for including rollable stats.

```
########################################
## Custom Actor Types ##################
########################################
[foobar]
  baseType = 'npc'

  # Define attributes.
  [foobar.attributesTop]
    [foobar.attributesTop.harm]
      type = "Resource"
      label = "Harm"
    [foobar.attributesTop.gender]
      type = "Text"
      label = "Gender"
    [foobar.attributesTop.age]
      type = "Text"
      label = "Age"

  [foobar.attributesLeft]
    [foobar.attributesLeft.look]
      type = "LongText"
      label = "Look"
    [foobar.attributesLeft.drive]
      type = "LongText"
      label = "Drive"

  # Define logical groups for moves.
  [foobar.moveTypes]
    mc = "MC Moves"

[ipsum]
  baseType = 'character'
  [ipsum.stats]
    lorem = "Lorem"
    ipsum = "Ipsum"
    dolor = "Dolor"
    sit = "Sit"
    amet = "Amet"

  # Define attributes.
  [ipsum.attributesTop]
    [ipsum.attributesTop.power]
      type = "Number"
      label = "Power"

  [ipsum.attributesLeft]
    [ipsum.attributesLeft.look]
      type = "LongText"
      label = "Look"
    [ipsum.attributesLeft.drive]
      type = "LongText"
      label = "Drive"

  # Define logical groups for moves.
  [ipsum.moveTypes]
    lorem = "Lorem Moves"
    ipsum = "Ipsum Moves"
```
