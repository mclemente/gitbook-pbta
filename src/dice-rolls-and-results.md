# Dice Rolls and Results

While most sections of the system's sheet configuration are tied to either characters or NPCs, rolls are defined separately and aren't included in either character or NPC groups.

## Required Fields
These fields are required and will halt sheet configuration if not provided.

* `rollFormula` - The dice roll formula that rolls should use when an explicit dice roll formula isn't provided. For example, when a character makes a roll using a stat, it will add that stat bonus to this rollFormula. When an NPC makes a roll, it's typically with a custom formula that's written out fully in the move and ignores this setting.
* `rollResults` - This group contains the various result ranges used for moves and stat rolls. Each range should be a subgroup with `range` and `label` properties.

## Optional Fields
These are optional fields that alter sheet behavior.

* `rollShifting` - (optional) If set to true, buttons will appear on moves in chat to allow their results to be shifted up or down. Defaults to false.
* `statClocks` - (optional) Adds a number of pips to stats. Useful for games such as AW: Burned Over.
* `statShifting` - (optional) Adds a Stat Shift feature to increase/decrease stats. Useful for games such as Masks.
* `statToggle` - (optional) This can be left out, entered as a direct value, or entered as a group with `label` and `modifier` properties inside it. The stat toggle will show up in each stat on character sheets and is useful for some game's such as Highlights in AW or Debilities in DW.
* `minMod` and `maxMod` - (optional) This can be any number, and if included it will prevent rolls from going outside of the bounds you establish. For example, if you set `minMod` to -2 and `maxMod` to 4, a roll with a +5 bonus would instead have a +4 bonus due to the maxMod.

Here's an example of what configuring rolls and result ranges will look like on your character moves and chat messages:

![](<.gitbook/assets/image (8).png>)

Here's an example of what fully configured rolls look like, and we'll go into more detail on each section below.

```
# Configure Rolls
rollFormula = "2d6"

# Enable roll shifting on chat messages
rollShifting = true

# Optionally add pips to stats
statClocks = 4

# Optionally add stat shifting
statShifting = true
# or
[statShifting]
  # Everything is optional. Values shown are the defaults for English localization
  label = "Stat Shift" # String shown on Character Sheet. Otherwise localize "{stat} Shift"
  value = 1 # The value to be shifted up/down
  stat = "Stat" # String used to localize the label
  stats = "Stats" # String used to localize "Character shifts {stats}" on Chat Message

# Optionally enable roll mod caps.
minMod = -4
maxMod = 4

# Configure stat toggle label and formula modifier.
[statToggle]
  label = "Highlight"
  modifier = "-1"

# Define roll result ranges.
[rollResults]
  [rollResults.failure]
    range = "6-"
    label = "Critical Failure"
  [rollResults.partial]
    range = "7-9"
    label = "Partial Success"
  [rollResults.success]
    range = "10-12"
    label = "Success!"
  [rollResults.critical]
    range = "13+"
    label = "Critical Success!"
```

## rollFormula

The `rollFormula` option will let you define the dice roll formula used for all move and stat rolls made by characters. Rolls should be entered with quotes, such as `"2d6"`, `"2d10"`, or `"d8+d6"`. You do not need to include a flat bonus into the roll unless it's expected for every roll, such as `"d6+d4+2"`.

```
rollFormula = "2d6"
```

## rollShifting

The optional `rollShifting` option will add buttons to moves in chat that will allow their results to be shifted up or down. Can be set to either `true` or `false` (defaults to `false`).

```
rollShifting = true
```

## statToggle

The `statToggle` option can be entered as either a single value field or as a group with `label` and `modifier` properties. If a modifier is included, any stats that the player has enabled the toggle for will have its stat rolls and move rolls modified by that value, such as a penalty for Debilities. If the statToggle option is set as a single value, it will be assumed that the modifier is 0.

This setting is optional and can be left out if preferred.

### Method 1: single value (short syntax)

```
statToggle = "Highlight"
```

### Method 2: group (long syntax)

```
# Configure stat toggle label and formula modifier.
[statToggle]
  label = "Debility"
  modifier = "-1"
```

## minMod / maxMod

If either the `minMod` or `maxMod` options are included, roll modifiers will be restricted based on the number you enter. For example, if the minMod is set to -1 and the maxMod is set to +3, a roll that's 2d6-3 would be treated as 2d6-1 and a roll that's 2d6+5 would be treated as 2d6+3.

This setting is optional and can be left out if preferred.

```
minMod = -2
maxMod = 4
```

## rollResults

The `rollResults` option is a group that supports any number of subgroups for various result ranges. This system includes special color-coding for `failure`, `partial`, `success`, and `critical` result ranges, but you can define any number of result ranges that you need. A future version of the system will include an additional setting for custom color-coding.

Each result subgroup follows this format:

```
[rollResults.key]
  range = "6-"
  label = "Label to Display"
```

Here's what the parts in that format do:

* `key` - Each group is defined as `[rollResults.key]`, where `key` is a machine-safe version of your group name. Keys should contain letters, numbers, and hyphens only. For example, if your group was for "Partial Success", you could use the key `partial` or `partial-success`
* `range` - The `range` option lets you specify the dice rolls that should trigger this result. This supports the following notations:
  * `N-` - You can enter a range such as "6-" to handle all results equal or less than the number in the range.
  * `N+` - You can enter a range such as "10+" to handle all results equal or greater than the number in the range.
  * `N1-N2` - You can enter a range such as "7-9" to handle all results within that range, such as 7, 8, and 9.
  * `false` - If you want to temporarily disable a range without deleting it entirely or commenting it out, you can set the range to `false` to disable it.
* `label` - The label that's display in chat messages and on the **Move** form when creating new move items.

### Example rollResults

Here's an example of how to configure roll results for standard ranges in most PbtA games, which includes a 4th range for critical successes. To remove critical success, you could delete the 4th option and change the 3rd range to "10+" instead.

```
[rollResults]
  [rollResults.failure]
    range = "6-"
    label = "Complications..."
  [rollResults.partial]
    range = "7-9"
    label = "Partial success"
  [rollResults.success]
    range = "10-12"
    label = "Success!"
  [rollResults.critical]
    range = "13+"
    label = "Critical Success!"
```
