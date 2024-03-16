# The Sprawl

This preset is based on [_The Sprawl_](http://www.ardens.org/games/the-sprawl/) rules by Ardens Ludere.

```
# Configure Rolls
rollFormula = "2d6"
# statToggle = "Highlight"

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
    edge = "Edge"
    meat = "Meat"
    mind = "Mind"
    style = "Style"
    synth = "Synth"

  # Define attributes.
  [character.attributesTop]
    [character.attributesTop.harm]
      type = "Clock"
      label = "Harm"
      max = 6
    [character.attributesTop.cred]
      type = "Number"
      label = "Cred"
    [character.attributesTop.xp]
      type = "Xp"
      label = "Xp"
      max = 10

  # Define sidebar details.
  [character.attributesLeft]
    [character.attributesLeft.links]
      type = "LongText"
      label = "Links"
    [character.attributesLeft.contacts]
      type = "LongText"
      label = "Contacts"
    [character.attributesLeft.look]
      type = "LongText"
      label = "Look"

  # Define groups for moves.
  [character.moveTypes]
    basic = "Basic Moves"
    playbook = "Playbook Moves"

  # Define groups for equipment.
  [character.equipmentTypes]
    gear = "Gear"

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
```
