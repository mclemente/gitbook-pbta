# Rovers

This preset is based on the _Rovers_ rules written by Catherine Ramen and published by Aviatrix Games. It uses the [Creative Commons 3.0 license](https://creativecommons.org/licenses/by/4.0/).

![](<../.gitbook/assets/image (9).png>)

```
# Configure Rolls
rollFormula = "2d6"

# Configure stat toggle label and formula modifier.
[statToggle]
  label = "Scar"
  modifier = "-2"

# Define roll result ranges.
[rollResults]
  [rollResults.failure]
    range = "6-"
    label = "Miss"
  [rollResults.partial]
    range = "7-9"
    label = "Partial Success"
  [rollResults.success]
    range = "10-11"
    label = "Success"
      [rollResults.critical]
    range = "12+"
    label = "Critical Success!"

########################################
## CHARACTERS ##########################
########################################
# Define the character group.
[character]

  # Define stats.
  [character.stats]
    wit = "Wit"
    might = "Might"
    grit = "Grit"

  # Define attributes.
  [character.attributesTop]
    [character.attributesTop.terms]
    	type = "Clock"
      label = "Terms"
      max = 4
    [character.attributesTop.hp]
      type = "Resource"
      label = "HP"
    [character.attributesTop.armor]
      type = "Number"
      label = "Armor"
    [character.attributesTop.strain]
      type = "Clock"
      label = "Strain"
      max = 5
    [character.attributesTop.xp]
      type = "Xp"
      label = "Experience"
      max = 10
      
      # Define sidebar details.
  [character.attributesLeft]
    [character.attributesLeft.creds]
      type = "Number"
      label = "Creds"
      
    [character.attributesLeft.load]
       type = "ListMany"
      label = "Load"
      options = [
        "Light (1-3)",
        "Normal (4-5)",
        "Heavy (6)",
        "Encumbered (7-9)"
      ]
 
    [character.attributesLeft.look]
      type = "LongText"
      label = "Background Skills"

  # Define groups for moves.
  [character.moveTypes]
    service = "Service Skills"
    skills = "General Skills"
    muster = "Mustering Out"

  # Define groups for equipment.
  [character.equipmentTypes]
    gear = "Equipment"
    load = "No Load"

########################################
## NPCS ################################
########################################
# Define stats.
[npc]
  # Define attributes.
  [npc.attributesTop]
    [npc.attributesTop.hp]
      type = "Resource"
      label = "HP"
    [npc.attributesTop.armor]
      type = "Number"
      label = "Armor"
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
