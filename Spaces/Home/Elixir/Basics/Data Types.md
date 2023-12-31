---
sticker: vault//SVG Icons/Nerd Fonts/group-by-ref-type-60311.svg
---
Basic Data Types in Elixir: 
#### Integers
- Whole numbers, no decimals. They can be positive or negative. 
- This value also has support for binary, octal, and hexadecimal numbers as well, so `{elixir icon} 0b110`, `{elixir icon} 0o644`, and `{elixir icon} 0x1F` are all valid declarations. With the value after the 0 defining whether or not it's a binary, octal, or hexadecimal value. 
- Example definition: `{elixir icon} myVar = 2`
#### Floats
- Numbers, with decimals. `2.0` < this is an example of a float despite the decimal being worth nothing. They can be positive or negative. 
- These support `e` for exponential values, like `1.0e-10`! 
- Example definition: `{elixir icon} myVar = 2.0`
#### Booleans
- True / False. Everything is truthy except for `false` and `nil`. 
- Example definition: `{elixir icon} myVar = false (or true)`
#### Atoms
- A variable where the name is also the value. For example, `:true` will return the boolean `{elixir icon} true` and `{elixir icon} :ImHungry` will return `{elixir icon} "I'm Hungry"`. 
- The names of Modules are also Atoms, even if they haven't been declared yet. 
- Atoms are also used to reference modules from Erlang libraries, and even ones that are built in. 
- Example definition: `{elixir icon} :Anything`. This Object is strange as the definition syntax only hinges on this `:` no equals sign or nothing. 
#### Strings
- They're strings! They're UTF-8 by default. Support Line Breaks and escape sequences like `{elixir icon} \r\n` and are wrapped with double quotes like `""`! 