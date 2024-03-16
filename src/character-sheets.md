# Character Sheets

Character sheets are defined under the `[character]` group in your sheet configuration and have 4 required options/groups, and one optional group:

* **stats** - This group defines character stats (such as ability scores in Dungeon World). Rolls will be made using these stats.
* **attributesTop** - Attributes in the attributesTop group are displayed directly below the stats in character sheets.&#x20;
* **attributesLeft** - Attributes in the attributesLeft group are displayed directly to the left of the moves list in character sheets.
* **moveTypes** - This group defines the groups/separators that will appear in the moves tab of character sheets. Examples include "Basic", "Advanced", "Spells", and "Class Moves".
* **equipmentTypes** - (optional) This group defines the groups/separators that will appear in the equipment tab of character sheets. Examples include "Gear" and "Loot".

![](<.gitbook/assets/image (6).png>)

{% hint style="warning" %}
#### A Note About Group Prefixing

Each of the options listed on this page are subgroups in the character group, which means they need to be entered using a format such as `[character.stats]` rather than just `[stats]`

On options that have direct value assignment (such as `type = "Checkbox"`), you won't include the prefix, as that's inferred from the group above the option. The complete example after this page and the NPC page should help with understanding everything in context.
{% endhint %}

## stats

The `[character.stats]` option group is used to define the stats used by your player characters. Each stat is written as direct assignment with the short syntax, such as the following:

```
[character.stats]
  cool = "Cool"
  hard = "Hard"
  hot = "Hot"
  sharp = "Sharp"
  weird = "Weird"
```

These stats will then be available on character sheets and when selecting stats used by moves.

## attributesTop and attributesLeft

Character sheets have two customizable areas where custom attributes can be placed.

Attributes are used in the PbtA system to track things that are not stats or moves. For instance, **Harm** in _Apocalypse World_, **Look** in _Dungeon World_, and **Conditions** in _Masks_ would all be considered attributes when making a sheet in the PbtA system.

This system supports two sets of attributes: **attributesLeft** and **attributesTop**. The two different groups of attributes behave identically; the only difference is that attributesTop is displayed as a row at the top of the sheet directly below the Stats, while attributesLeft is displayed in a column to the left side of the Moves section of the sheet. Some attribute types may work better in one group or the other, for instance, a `ListMany` attribute type would work better in the attributesLeft group if it has more than 5 or so options due to the extra height created by the list options.

{% hint style="info" %}
#### Referencing attributes in rolls and macros

If you're trying to reference an attribute in something like an inline roll, then the attribute groups will need to be accessed using the shorthand `attrLeft` or `attrTop`. For instance, the following could work:

```
[[2d6+@attrTop.armor.value]]
```

If you're instead trying to reference an attribute in a macro, you can find them on the actor using a similar format:

```javascript
let actor = game.actors.getName('My Character');
let armor = actor.data.data.attrTop.armor.value;
```
{% endhint %}

### Attribute Types

For a full list of attribute types and how to use them, see the [Attribute Types](configuration-reference-1/attribute-types.md) page. For reference, the available attribute types in summary are:

* **Number** - Attributes that should be numeric values only.
* **Text** - Plain text values in a single-line text field.
* **LongText** - Plain text values in a text area that spans multiple lines. In a future version of the system, this will support the TinyMCE text editor.
* **Resource** - Numeric value fields that support both a current `value` and `max` value.
* **Clock** - Numeric value fields with current and max values, but the front-end widget will be a series of checkboxes.
* **Xp** - Numeric value fields with current and max values, but the front-end widget will be a series of radio circles. In a future version of the system, this will support additional values to better tie it to character advancement.
* **Checkbox** - A single checkbox with a label.
* **ListMany** - Multiple checkboxes with labels that can support any number of them being checked at a given time. In a future version of the system, there will be a "limit" option to specify how many options can be chosen by characters at once. In addition, ListMany can be used to handle conditions if the labels of your options include a number (such as -2) and the `condition = true` property is included in the attribute.
* **Roll** - A text field along with a button to trigger dice rolls based on its current value. Works best with a supplied `default` value, such as `default = "d10"`

### Example attribute

Assigning an attribute to a character should look similar to the following:

```
[character.attributesTop]
  [character.attributesTop.armor]
    type = "Number"
    label = "Armor"
  [character.attributesTop.harm]
    type = "Clock"
    max = 6
    default = 0
  [character.attributesTop.damage]
    type = "Roll"
    label = "Damage"
    default = "1d10"

[character.attributesLeft]
  [character.attributesLeft.look]
    type = "LongText"
    label = "Look"
  [character.attributesLeft.weight]
    type = "Resource"
    label = "Weight"
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
      
```

## moveTypes

The `moveTypes` option will allow you to define the various move types that can be used to organize moves in your players' characters. For example, "Basic Moves" or "Advanced Moves".

Each move type should be entered as a single string value.

```
[character.moveTypes]
  basic = "Basic Moves"
  advanced = "Advanced Moves"
  class = "Class Moves"
```

## equipmentTypes

As with `moveTypes`, the `equipmentTypes` option will allow you to define the various equipment types that can be used to organize equipment in your players' characters. For example, "Gear" or "Loot".

Equipment types are optional, but each equipment type should be entered as a single string value if you use them.

```
[character.equipmentTypes]
  gear = "Gear"
  loot = "Loot"
```
