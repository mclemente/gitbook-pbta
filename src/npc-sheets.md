# NPC Sheets



NPC sheets are defined under the `[npc]` group in your sheet configuration and have 3 required options/groups. They each function identically to their counterparts in [character sheet](character-sheets.md).

* **attributesTop** - Attributes in the attributesTop group are displayed directly below the stats in character sheets.&#x20;
* **attributesLeft** - Attributes in the attributesLeft group are displayed directly below the stats in character sheets.&#x20;
* **moveTypes** - This group defines the groups/separators that will appear in the moves tab of character sheets. Examples include "Basic", "Advanced", "Spells", and "Class Moves"

![](<.gitbook/assets/image (2).png>)

{% hint style="warning" %}
#### A Note About Group Prefixing

Each of the options listed on this page are subgroups in the npc group, which means they need to be entered using a format such as `[npc.attributesTop]` rather than just `[attributesTop]`

On options that have direct value assignment (such as `type = "Checkbox"`), you won't include the prefix, as that's inferred from the group above the option. The complete example at the end of this page should help with understanding everything in context.
{% endhint %}

## attributesTop and attributesLeft

NPC sheets have two customizable areas where custom attributes can be placed.

As with characters, this system supports two sets of attributes: **attributesLeft** and **attributesTop**. The two different groups of attributes behave identically; the only difference is that attributesTop is displayed as a row at the top of the sheet directly below the NPC's avatar and name, while attributesLeft is displayed in a column to the left side of the Moves section of the sheet. Some attribute types may work better in one group or the other, for instance, a `ListMany` attribute type would work better in the attributesLeft group if it has more than 5 or so options due to the extra height created by the list options.

{% hint style="info" %}
#### Referencing attributes in rolls and macros

If you're trying to reference an attribute in something like an inline roll, then the attribute groups will need to be accessed using the shorthand `attrLeft` or `attrTop`. For instance, the following could work:

```
[[2d6+@attrTop.armor.value]]
```

If you're instead trying to reference an attribute in a macro, you can find them on the actor using a similar format:

```javascript
let actor = game.actors.getName('My NPC');
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
* **ListMany** - Multiple checkboxes with labels that can support any number of them being checked at a given time. In a future version of the system, there will be a "limit" option to specify how many options can be chosen by characters at once.
* **Roll** - A text field along with a button to trigger dice rolls based on its current value. Works best with a supplied `default` value, such as `default = "d10"`

### Example attribute

Assigning an attribute to a NPC should look similar to the following:

```
[npc.attributesTop]
  [npc.attributesTop.armor]
    type = "Number"
    label = "Armor"
  [npc.attributesTop.harm]
    type = "Clock"
    max = 6
    default = 0
  [npc.attributesTop.damage]
    type = "Roll"
    label = "Damage"
    default = "1d10"

[npc.attributesLeft]
  [npc.attributesLeft.look]
    type = "LongText"
    label = "Look"
  [npc.attributesLeft.weight]
    type = "Resource"
    label = "Weight"
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
      
```

## moveTypes

The `moveTypes` option will allow you to define the various move types that can be used to organize moves in your players' characters. For example, "Hard Moves" or "Soft Moves".

Each move type should be entered as a single string value.

```
[npc.moveTypes]
  hard = "Hard Moves"
  soft = "Soft Moves"
```
