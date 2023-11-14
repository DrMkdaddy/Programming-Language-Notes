---
sticker: vault//SVG Icons/Nerd Fonts/function-983701.svg
---
Named functions have to be defined in a module using the `{elixir} def` keyword. Functions defined in a module are available for other modules to use. 
```elixir
defmodule Greeter do
  def hello(name) do
    "Hello, " <> name
  end
end

Greeter.hello("Sean")
# ^ Returns "Hello, Sean"
# If the function's body spans only one line you can just use a do: shortcut.

defmodule Greeter do
  def hello(name), do: "Hello, " <> name
end

defmodule Length do
  def of([]), do: 0
  def of([_ | tail]), do: 1 + of(tail)
end
Length.of []
0
Length.of [1, 2, 3]
3
# ^ The result differ. One returns zero when given an empty array and the other returns the length of the array. 
# The function is also overloaded. 
defmodule Greeter2 do
  def hello(), do: "Hello, anonymous person!"
  def hello(name), do: "Hello, " <> name
  def hello(name1, name2), do: "Hello, #{name1} and #{name2}"
end
Greeter2.hello()
"Hello, anonymous person!"
Greeter2.hello("Fred")
"Hello, Fred"
Greeter2.hello("Fred", "Jane")
"Hello, Fred and Jane"
# Has overloaded functions. The behaviour will differ pertaining to the inputs and whether that match the pattern or not. 
```

### Function Naming and Arguments. 
Functions are named by the name combined with the arity (number of arguments). So a function like `hello` with no arguments would be referred to as `hello/0`, that same function with one or two arguments would be referred to as `hello/1` and `hello/2` respectively. 

### Functions and [[Pattern Matching]] 
Functions use Pattern Matching behind the scenes with the arguments they're called with. If you set the function up in order to accept a [[Collections#Maps|Map]] but only care about a particular key, you can pattern match the argument on the presence of that key.
```elixir
defmodule Greeter1 do
  def hello(%{name: person_name}) do
    IO.puts "Hello, " <> person_name
  end
end
```
```elixir
fred = %{
name: "Fred",
age: "95",
favorite_color: "Taupe"
}

Greeter1.hello(fred)
"Hello, Fred"
# ^ When the function is called with the fred map it'll only pattern match the key provided. 
```
The function will fail if you do not provide the key the function expects, if the function does not find the matching map it will fail. However, because the function only will look for the :name key in the map it will result in function not knowing anything about the rest of the collection. In order to retain that information the map will need to be assigned to its own variable in the function in order to be used.  