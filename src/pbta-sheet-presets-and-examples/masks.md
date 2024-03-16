# Masks

This preset is based on the [_Masks_](https://www.magpiegames.com/masks/) rules written by Brendan Conway and published by Magpie Games. It uses the [Creative Commons 4.0 license](https://creativecommons.org/licenses/by/4.0/).

![](<../.gitbook/assets/image (1).png>)

```
# Configure Rolls
rollFormula = "2d6"
statToggle = "Locked"

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
    danger = "Danger"
    freak = "Freak"
    savior = "Savior"
    superior = "Superior"
    mundane = "Mundane"

  # Define attributes.
  [character.attributesTop]
    [character.attributesTop.heroName]
      type = "Text"
      label = "Hero Name"
    [character.attributesTop.xp]
      type = "Xp"
      label = "Potential"
      max = 5
    [character.attributesTop.momentUnlocked]
      type = "Checkbox"
      label = "Moment of Truth"
      checkboxLabel = "Unlocked"
      default = false

  # Define sidebar details.
  [character.attributesLeft]
    [character.attributesLeft.conditions]
      type = "ListMany"
      label = "Conditions"
      description = "Choose all that apply:"
      condition = true
      options = [
        "Afraid (-2 to engage)",
        "Angry (-2 to comfort)",
        "Guilty (-2 to provoke)",
        "Hopeless (-2 to unleash)",
        "Insecure (-2 to defend)"
      ]
    [character.attributesLeft.look]
      type = "LongText"
      label = "Look"
    [character.attributesLeft.abilities]
      type = "LongText"
      label = "Abilities"
    [character.attributesLeft.influence]
      type = "LongText"
      label = "Influence"
    [character.attributesLeft.moment]
      type = "LongText"
      label = "Moment of Truth"

  # Define groups for moves.
  [character.moveTypes]
    basic = "Basic Moves"
    playbook = "Playbook Moves"
    team = "Team Moves"
    adult = "Adult Moves"

  # Define groups for equipment.

########################################
## NPCS ################################
########################################
# Define stats.
[npc]
  # Define attributes.
  [npc.attributesTop]
    [npc.attributesTop.realName]
      type = "Text"
      label = "Real Name"
    [npc.attributesTop.generation]
      type = "Text"
      label = "Generation"
    [npc.attributesTop.conditions]
      type = "Text"
      label = "Conditions"

  [npc.attributesLeft]
    [npc.attributesLeft.drive]
      type = "LongText"
      label = "Drive"
    [npc.attributesLeft.abilities]
      type = "LongText"
      label = "Abilities"
    [npc.attributesLeft.conditions]
      type = "ListMany"
      label = "Conditions"
      description = "Choose all that apply:"
      options = [
        "Afraid",
        "Angry",
        "Guilty",
        "Hopeless",
        "Insecure"
      ]

  # Define logical groups for moves.
  [npc.moveTypes]
    villain = "Villain Moves"
```
