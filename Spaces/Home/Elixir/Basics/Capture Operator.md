---
sticker: vault//SVG Icons/Nerd Fonts/ampersand-985741.svg
---
Capture Operatorss are a shorthand method in order to create anonymous functions like the ones mentioned in [[Enum Module]]. Like a [[Basic Operations]] operator this is a single character (an ampersand &)

Typically you'd pass an anonymous function like this: `elixir Enum.map([1,2,3], fn number -> number + 3 end)`, with `[4, 5, 6]` as a return. However