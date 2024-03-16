# TOML Syntax

[TOML](https://github.com/toml-lang/toml) shares traits with other file formats used for application configuration and data serialization, such as YAML and JSON. TOML and JSON both are simple and use ubiquitous data types, making them easy to code for or parse with machines. TOML and YAML both emphasize human readability features, like comments that make it easier to understand the purpose of a given line. TOML differs in combining these, allowing comments (unlike JSON) but preserving simplicity (unlike YAML).

INI files are frequently compared to TOML for their similarities in syntax and use as configuration files. However, there is no standardized format for INI and they do not gracefully handle more than one or two levels of nesting.

## Example

```
# This is a comment in a TOML document.

# Properties are set with the key on the left and the value on the right.
title = "TOML Example"

# Groups should be wrapped in []
[owner]
  name = "Tom Preston-Werner"
  dob = 1979-05-27T07:32:00-08:00 # First class dates

# Value type examples:
[database]
  # String
  server = "192.168.1.1"
  # Array
  ports = [ 8001, 8001, 8002 ]
  # Number
  connection_max = 5000
  # Boolean
  enabled = true

# Groups can also have nested groups.
[servers]

  # Indentation (tabs and/or spaces) is recommended but not required
  [servers.alpha]
    ip = "10.0.0.1"
    dc = "eqdc10"

  # Nested groups must include the parent name as a prefix.
  [servers.beta]
    ip = "10.0.0.2"
    dc = "eqdc10"

[clients]
  data = [ ["gamma", "delta"], [1, 2] ]

# Line breaks are OK when inside arrays
hosts = [
  "alpha",
  "omega"
]
```
