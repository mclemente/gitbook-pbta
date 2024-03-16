# Monster of the Week

This character sheet preset is based on the [Monster of the Week](https://www.evilhat.com/home/monster-of-the-week/) rules written by Michael Sands and published by Evil Hat Productions.

![](<../.gitbook/assets/image (10).png>)

```toml
# Configure Rolls
rollFormula = "2d6"

# Define roll result ranges.
[rollResults]
  [rollResults.success]
    range = "10+"
    label = "Success!"
  [rollResults.partial]
    range = "7-9"
    label = "Partial success"
  [rollResults.failure]
    range = "6-"
    label = "Miss..."

########################################
## CHARACTERS ##########################
########################################
# Define the character group.
[character]

  # Define stats.
  [character.stats]
    cool = "Cool"
    tough = "Tough"
    charm = "Charm"
    sharp = "Sharp"
    weird = "Weird"

  # Define attributes.
  [character.attributesTop]
    [character.attributesTop.harm]
      type = "Clock"
      label = "Harm"
      description = "When you reach 4 or more, mark unstable."
      max = 7
    [character.attributesTop.unstable]
        type = "Checkbox"
        label = "Unstable"
        checkboxLabel = "Unstable Injuries"
        description = "(Unstable injuries will worsen as time passes)"
        default = false
    [character.attributesTop.luck]
      type = "Clock"
      label = "Luck"
      description = "Mark luck to change a roll to 12 or avoid all harm."
      max = 7
      default = 0
    [character.attributesTop.xp]
      type = "Xp"
      label = "Experience"
      description = "When you roll a miss, or when a move says to, mark Xp."
      max = 5
      default = 0

  # Define sidebar details.
  [character.attributesLeft]
    [character.attributesLeft.armour]
        type = "Number"
        label = "Armour"
        default = 0
        description = "Armour reduces harm suffered by the armour rating."
    [character.attributesLeft.luckspecial]
        type = "LongText"
        label = "Luck Special"
    [character.attributesLeft.look]
        type = "LongText"
        label = "Look"
    [character.attributesLeft.improvements]
        type = "LongText"
        label = "Improvements"
    [character.attributesLeft.advancedimprovements]
        type = "LongText"
        label = "Advanced Improvements"
    
  # Define groups for moves.
  [character.moveTypes]
    basic = "Basic Moves"
    class = "Playbook Moves"

  # Define groups for equipment.
  [character.equipmentTypes]
    gear = "Gear"
    weapon = "Weapons"
    transport = "Transport"
    armour = "Armour"

########################################
## NPCS ################################
########################################
# Define stats.
[npc]
  # Define attributes.
  [npc.attributesTop]
    [npc.attributesTop.harm]
        type = "Resource"
        label = "Harm Capacity"
    [npc.attributesTop.armour]
        type = "Number"
        label = "Armour"
        default = 0
    [npc.attributesTop.type]
        type = "ListMany"
        label = "NPC Type"
        options = [
            "Monster",
            "Minion",
            "Bystander",
            "Location"
        ]
      
  [npc.attributesLeft]
    [npc.attributesLeft.powers]
      type = "LongText"
      label = "Drive"
    [npc.attributesLeft.attacks]
      type = "LongText"
      label = "Attacks"
    [npc.attributesLeft.weakness]
      type = "LongText"
      label = "Weakness"
    [npc.attributesLeft.desc]
      type = "LongText"
      label = "Description"
    [npc.attributesLeft.motivation]
      type = "LongText"
      label = "Motivation"

  # Define logical groups for moves.
  [npc.moveTypes]
    custom = "Custom Moves"
```
