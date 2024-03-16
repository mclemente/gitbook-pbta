---
description: Learn how to write the TOML configuration used for character sheets.
---

# Configuring Your System

The PbtA system is built so that you can configure your character sheets to have custom stats, attributes, details, moves, and equipment. All characters share the same basic character sheet structure, which needs to be created by the GM using the system's settings.

## Configuring your sheet

You can configure character sheets by going to the gear tab in Foundry's right sidebar, clicking the **Configure Settings** button, and then going to the **System Settings** tab. From there, click the **PbtA Sheet Configuration** button to open up the character sheet editor.

![](<.gitbook/assets/image (5).png>)

## Working with TOML

In a future release, the sheet configuration dialog will be a graphical user interface (GUI) to let you see the sheet as you build it, but in this pre-release version of the system, the editor is text-based using the TOML syntax.

{% hint style="info" %}
### What is TOML?

TOML is [Tom's Obvious, Minimal Language](https://github.com/toml-lang/toml) and is very similar to working with an INI file. This system uses it due to how much easier it is to read than JSON while not having strict indentation or spacing rules. Eventually, the TOML format will only be used for exporting and importing character sheet structures and the system will instead use a graphical user interface (GUI) to build out character sheets, but for now TOML is the only way to configure them.

This article will show an example sheet configuration written with TOML, and then we'll break down each part of it shortly below that.
{% endhint %}

### Basic Syntax

The basic syntax of TOML for the sheet configuration uses the following structure:

* `# Comment` - Turn any line into a comment that gets ignored by prefixing it with #
* `variable = "value"` - Any variable can be assigned a value by setting it equal to some value. Numbers  or true/false can be written directly, while text/strings should be in " quotation marks. Variable names should be machine-safe (letters, numbers, and hyphens only). The following types of values are supported:
  * **String:** `"value"` - Any text value enclosed in `"` marks. This is the most common type used in sheet configuration, and will also work for numbers. When in doubt, enter your value as a string surrounded by quotation marks.
  * **Number:** `0` - Numeric values can be entered without `"` marks.
  * **Boolean:** `true` - Boolean values can be entered as either `true` or `false`. Most commonly used for default values on checkbox attributes.
  * **Array:** `["Apple", "Orange", "Banana"]` - Arrays of values, such as options for checkboxes. Arrays are a bit more advanced and will be covered later in the **Character Sheets** section.
  * **Subgroup:** Rather than having a value assigned directly, an option can be set as a subgroup, following the rules for writing groups listed below. More details and examples of groups and subgroups will be shown in the **Character Sheets** section.
* `[group]` - Groups can be defined with `[` and `]` around the group name. Groups can also be nested. Indentation of group children is not required, but is recommended for legibility. Nested groups need to include the parent group's prefix and a period, such as `[group.subgroup]`. Sub groups should be machine-safe similar to variable names.

