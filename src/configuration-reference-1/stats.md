# Stats

Stats are entered for the `[character]` group as key/value pairs, as in the following example:

```
[character.stats]
  cool = "Cool"
  hard = "Hard"
  hot = "Hot"
  sharp = "Sharp"
  weird = "Weird"
```

## Stat Toggle

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
