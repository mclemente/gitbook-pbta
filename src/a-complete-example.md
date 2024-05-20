# A Complete Example

Based on the previous sections, here's a complete example of a sheet configuration for the PbtA system.

```
# Configure Rolls
rollFormula = "2d6"
statToggle = "Toggle"

# Define roll result ranges.
[rollResults]
  [rollResults.failure]
    range = "6-"
    label = "Complications..."
  [rollResults.partial]
    range = "7-9"
    label = "Partial success"
  [rollResults.success]
    range = "10+"
    label = "Success!"

########################################
## CHARACTERS ##########################
########################################
# Define the character group.
[character]

  # Define stats.
  [character.stats]
    foo = "Foo"
    bar = "Bar"
    bas = "Bas"

  # Define attributes.
  [character.attributesTop]
    [character.attributesTop.harm]
      type = "Clock"
      label = "Harm"
      max = 6
    [character.attributesTop.armor]
      type = "Number"
      label = "Armor"
    [character.attributesTop.hold]
      type = "Resource"
      label = "Hold"
    [character.attributesTop.xp]
      type = "Xp"
      label = "Xp"
      max = 5

  # Define sidebar details.
  [character.attributesLeft]
    [character.attributesLeft.harmConditions]
      type = "ListMany"
      label = "Conditions"
      options = [
        "Unconscious",
        "Blinded",
        "Deafened",
        "Paralyzed",
        "Stunned",
        "Weakened",
        "Dying",
      ]
    [character.attributesLeft.look]
      type = "LongText"
      label = "Look"

  # Define groups for moves.
  [character.moveTypes]
    basic = "Basic Moves"
    peripheral = "Advanced Moves"
    class = "Class Moves"

  # Define groups for equipment.
  [character.equipmentTypes]
    gear = "Gear"
    loot = "Loot"

########################################
## NPCS ################################
########################################
# Define stats.
[npc]
  # Define attributes.
  [npc.attributesTop]
    [npc.attributesTop.harm]
      type = "Resource"
      label = "Harm"
    [npc.attributesTop.damage]
      type = "Roll"
      label = "Damage"
      default = "d6"
    [npc.attributesTop.loot]
      type = "Text"
      label = "Loot"
  [npc.attributesLeft]
    [npc.attributesLeft.look]
      type = "LongText"
      label = "Look"
    [npc.attributesLeft.drive]
      type = "LongText"
      label = "Drive"

  # Define logical groups for moves.
  [npc.moveTypes]
    gm = "GM Moves"
```
