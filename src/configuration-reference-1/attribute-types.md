# Attribute Types

The PbtA system support several attribute types. Each attribute type has a required **type** property

{% hint style="info" %}
#### **Common Properties**

All attribute types support the following common properties, which are optional:

* **label** - The label placed above the input on the character sheet.
* **description** - Descriptive text below the label and above the input.
* **default** - The default value of the attribute.
* **customLabel** - If set to `true`, this will turn the label for the attribute into a text field that can be overridden on each character sheet.
{% endhint %}

{% hint style="info" %}
#### Short Syntax

Some attributes can alternatively be written using a short syntax format by only specifying the type and allowing the label to be inferred from the option name. If attributes have required properties, such as the `max` property on `Clock` attributes, they cannot be entered using the short syntax.

```
armor = "Number"
harm = "Clock"
```
{% endhint %}

## Number

Basic number input.

```toml
[character.attributesTop.armor]
  type = "Number"
  default = 0
```

## Text

Basic text input.

```toml
[character.attributesLeft.nickname]
  type = "Text"
```

## LongText

Text area field, used for larger text descriptions.

```toml
[character.attributesLeft.look]
  type = "LongText
```

## Resource

Numeric resource with both current and max values.

```toml
[character.attributesTop.mana]
  type = "Resource"
  label = "Mana"
  max = 4
  default = 4
```

## Clock

Numeric resource that uses checkboxes to determine the current amount (like **Harm** in _Apocalypse World_). Clocks also support an optional "inputStyle" that lets you specify if the inputs should be checkboxes or radios (circles).

### Example of clocks with checkboxes:

```toml
[character.attributesTop.harm]
  type = "Clock"
  label = "Harm"
  max = 6
  default = 0
```

### Example of clocks with circles:

```toml
[character.attributesTop.improvement]
  type = "Xp"
  label = "Improvement"
  max = 7
  default = 0
```

## Checkbox

Single checkbox with label. If using the "default" property on checkboxes, it should be entered as either "true" or "false" (no quote marks).

```toml
[character.attributesLeft.wounded]
  type = "Checkbox"
  label = "Wounded"
  checkboxLabel = "Untreated wounds"
  default = false
```

## ListMany&#x20;

Multiple checkboxes with labels. ListMany does not support the "default" property at this time.

{% hint style="info" %}
ListMany attributes can also be used as conditons. If you set `condition = true` in your attribute, any numeric modifiers in the condition labels will be available as modifiers during move rolls.
{% endhint %}

{% hint style="info" %}
To enable multiple checkboxes for an option, add `|n` onto the end of the option, such as `Afraid (-2 to engage)|3` to create an option named "Afraid (-2 to engage)" with 3 checkboxes.
{% endhint %}

{% hint style="info" %}
To enable a custom textbox for an option, set its value to `[Text]`

This can be combined with the multiple checkboxes option, such as `[Text]|2` for a custom textbox with 2 checkboxes.
{% endhint %}

```toml
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
    "Insecure (-2 to defend)|3",
    "[Text]",
    "[Text]|4"
  ]
```

## ListOne

{% hint style="info" %}
ListOne is only available in PbtA 0.8.0+
{% endhint %}

Similar to ListMany, but uses a single-select Radio input rather than multi-select Checkboxes. Configuration is similar to ListMany with two caveats:

* Conditions are not supported
* default values can be assigned

```toml
[character.attributesLeft.status]
  type = "ListOne"
  label = "Status"
  description = "Character's current status"
  default = 2 # values are numeric, starting with 0 as the first option
  options = [
    "Healthy",
    "Wounded",
    "Near Death",
    "Unconscious",
    "Dying"
  ]
```

## Roll

A single text field and a roll button to make a dice roll based on its value.

```toml
[character.attributesLeft.damage]
  type = "Roll"
  label = "Damage"
  default = "d10"
```

## Track

{% hint style="info" %}
Track attributes are only available in PbtA 0.8.0+
{% endhint %}

Tracks are an advanced field used for use cases like the Root RPG's reptuation tracks. It tracks 3 values: `value` (the actual bonus that would be applied to rolls) and `negative.value` / `positive.value` (how close you are from changing the bonus).

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption><p>Screenshot of a Reputation track from n1xx1's original merge request</p></figcaption></figure>

```toml
[character.attributesTop.reputation]
  type = "Track"
  label = "Reputation"
  default = 0
  [character.attributesTop.reputation.negative]    
    label = "Notoriety"
    steps = 3
    max = 3
    default = 0
  [character.attributesTop.reputation.positive]
    label = "Prestige"
    steps = 5
    max = 3
    default = 0
```
