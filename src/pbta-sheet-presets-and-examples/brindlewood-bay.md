# Brindlewood Bay

This character sheet preset is based on the [Brindlewood Bay](https://www.gauntlet-rpg.com/brindlewood-bay.html) RPG by Jason Cordova.

```toml
# Configure Rolls
rollFormula = "2d6"

# Define roll result ranges.
[rollResults]
  [rollResults.crit]
    range = "12+"
    label = "Critical Success!"
  [rollResults.success]
    range = "10-11"
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
    vitality = "Vitality"
    composure = "Composure"
    reason = "Reason"
    presence = "Presence"
    sensitivity = "Sensitivity"

  # Define attributes.
  [character.attributesTop]
    [character.attributesTop.style]
        type = "LongText"
        label = "Style"
        description = "Pick one or make up your own."
    [character.attributesTop.cozyactivity]
        type = "LongText"
        label = "Cozy Activity"
        description = "No two Mavens can have the same activity."
    [character.attributesTop.xp]
        type = "Xp"
        label = "XP Track"
        description = "When you roll a miss, or when a move says to, mark Xp."
        max = 5
        default = 0

  # Define sidebar details.
  [character.attributesLeft]
    [character.attributesTop.conditions]
        type = "LongText"
        label = "Conditions"
    [character.attributesLeft.endofsession]
        type = "ListMany"
        label = "End of Session"
        description = "The first is always marked. At the beginning of a session, mark two more (three total marked)."
        options = [
            "Did the Murder Mavens solve a mystery?",
            "Did you secretly undermine the authority of a local official?",
            "Did you share your wisdom with a young person?",
            "Did you share a memory of a late family member?",
            "Did you behave like a woman half your age?",
            "Did you dote on someone?",
            "Did you show someone that you’ve “still got it?”"
        ]
    [character.attributesLeft.crownqueen]
        type = "ListMany"
        label = "Crown of the Queen"
        description = "When you put on this Crown, mark and narrate any you wish."
        options = [
            "A flashback of your fondest memory of your late partner.",
            "A flashback showing how you were an imperfect sister or daughter.",
            "A flashback showing how you were an imperfect mother.",
            "A flashback of your fondest memory with one of your children.",
            "A scene in the present day showing a private side of you very few get to see.",
            "A scene in the present day showing a burgeoning romance.",
            "A scene in the present day showing how you satisfy your physical desires."
        ]
    [character.attributesLeft.crownvoid]
        type = "ListMany"
        label = "Crown of the Void"
        description = "When you put on this Crown, mark the first empty box."
        options = [
            "A Shadow in the Garden. Hereafter, during cozy vignettes focused on you or Cozy Move scenes involving you, you must also narrate how dark entities subtly reveal themselves in the scene.",
            "The Chariot. Your Reason modifier is reduced by 1 and your Sensitivity modifier is increased by 1.",
            "The Pallid Mask. Hereafter, during any intimate conversation with another character, you must make a casual reference to death, dying, the afterlife, or the End of All Things—no matter the subject at-hand.",
            "The Pomegranate Kernel. You gain the condition “Obsessed with the Void.” It can never be removed.",
            "The Void. Retire your character in a way that shows how they are lost to the Void. "
        ]
    
  # Define groups for moves.
  [character.moveTypes]
    basic = "Basic Moves"
    class = "Maven Moves"

  # Define groups for equipment.
  [character.equipmentTypes]
    cozyplace = "A Cozy Little Place"
    

########################################
## NPCS ################################
########################################
# Define stats.
[npc]      
  [npc.attributesLeft]
    [npc.attributesLeft.details]
      type = "LongText"
      label = "Descriptive Details"
    [npc.attributesLeft.personality]
      type = "LongText"
      label = "Personality or Role"
    [npc.attributesLeft.quote]
      type = "LongText"
      label = "Inspiring Quote"

  # Define logical groups for moves.
  [npc.moveTypes]
    custom = "Moves"
```
