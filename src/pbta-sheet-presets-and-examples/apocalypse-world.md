# Apocalypse World

This preset is based on the [_Apocalypse World_](http://apocalypse-world.com/) rules written by D. Vincent Baker and Meguey Baker, published by Lumpley Games.

![](<../.gitbook/assets/image (7).png>)

```toml
# Configure Rolls
rollFormula = "2d6"
statToggle = "Highlight"

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
    cool = "Cool"
    hard = "Hard"
    hot = "Hot"
    sharp = "Sharp"
    weird = "Weird"

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
      label = "Harm Conditions"
      options = [
        "Stabilized",
        "Shattered (-1COOL)",
        "Crippled (-1HARD)",
        "Disfigured (-1HOT)",
        "Broken (-1SHARP)"
      ]
    [character.attributesLeft.improvement]
      type = "LongText"
      label = "Improvement"
    [character.attributesLeft.hx]
      type = "LongText"
      label = "HX"
    [character.attributesLeft.look]
      type = "LongText"
      label = "Look"
    [character.attributesLeft.special]
      type = "LongText"
      label = "Playbook Special"

  # Define groups for moves.
  [character.moveTypes]
    basic = "Basic Moves"
    peripheral = "Peripheral Moves"
    class = "Class Moves"

  # Define groups for equipment.
  [character.equipmentTypes]
    gear = "Gear"
    barter = "Barter"

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
    [npc.attributesTop.gender]
      type = "Text"
      label = "Gender"
    [npc.attributesTop.age]
      type = "Text"
      label = "Age"

  [npc.attributesLeft]
    [npc.attributesLeft.look]
      type = "LongText"
      label = "Look"
    [npc.attributesLeft.drive]
      type = "LongText"
      label = "Drive"

  # Define logical groups for moves.
  [npc.moveTypes]
    mc = "MC Moves"
  [npc.equipmentTypes]
    loot = "Loot"
```
