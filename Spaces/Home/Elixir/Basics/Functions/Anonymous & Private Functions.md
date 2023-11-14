---
sticker: vault//SVG Icons/Nerd Fonts/incognito-984569.svg
---
## Anonymous Functions 
There functions do not have names, they're meant to be passed around to functions, as seen in the [[Enum Module]] section. In order to define one you will need to define it using either the `{elixir}fn ... end` syntax or the [[Capture Operator]]. 

## Private Functions 
Sometimes we don't want a function be able to be accessed outside of the module its defined in. say, for example a library we're writing has helper functions. A private function can be defined using the `{elixir}defp` keyword. 
```elixir
defmodule Greeter do
  def hello(name), do: phrase() <> name
  defp phrase, do: "Hello, "
end

Greeter.hello("Sean")
"Hello, Sean"
# ^ Returns
Greeter.phrase
# ^  ** (UndefinedFunctionError) function Greeter.phrase/0 is undefined or private
#    Greeter.phrase()
```
