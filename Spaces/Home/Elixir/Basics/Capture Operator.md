---
sticker: vault//SVG Icons/Nerd Fonts/ampersand-985741.svg
---
Capture Operators are a shorthand method in order to create anonymous functions like the ones mentioned in [[Enum Module]]. Like a [[Basic Operations]] operator this is a single character (an ampersand &)

Typically you'd pass an anonymous function like this: `{elixir icon}Enum.map([1,2,3], fn number -> number + 3 end)`, with `{elixir icon} [4, 5, 6]` as a return. 

The capture function allows you to rewrite that as `{elixir icon} Enum.map([1,2,3], &(&1 + 3))`. Additionally you can assign the anonymous to a variable(?) 

`{elixir icon} plus_three = &(&1 + 3); Enum.map([1,2,3], plus_three)` Returns `{elixir} [4, 5, 6]`.  

```elixir
sum = &(&1 + &2)
sum.(2, 3)
# ^ Returns 5
```
As seen here, the arguments/inputs are defined using ampersands as well. 