---
sticker: vault//SVG Icons/Nerd Fonts/function-variant-985201.svg
---
3### Anonymous Functions 
There functions do not have names, they're meant to be passed around to functions, as seen in the [[Enum Module]] section. In order to define one you will need to define it using either the `{elixir}fn ... end` syntax or the [[Capture Operator]]. 

### Pattern Matching
[[Pattern Matching]] isn't limited to variables in elixir, because functions are first class objects it can be applied to them as well. 
```elixir
handle_result = fn
  {:ok, result} -> IO.puts "Handling result..."
  {:ok, _} -> IO.puts "This would be never run as previous will be matched beforehand."
  {:error} -> IO.puts "An error has occurred!"
end

some_result = 1

handle_result.({:ok, some_result})
Handling result...
:ok
# ^ The IO.puts function returns :ok once it finishes the print
handle_result.({:error})
An error has occurred!
:ok
# ^ The IO.puts function returns :ok once it finishes the print
```

## Named Functions 
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

#### Function Naming and Arguments. 
Functions are named by the name combined with the arity (number of arguments). So a function like `hello` with no arguments would be referred to as `hello/0`, that same function with one or two arguments would be referred to as `hello/1` and `hello/2` respectively. 

#### Functions and [[Pattern Matching]] 
Functions use Pattern Matching behind the scenes with the arguments they're called with. If you set the function up in order to accept a 

![](https://media.tenor.com/uJOLBspTDLoAAAAd/cat-dance.gif)
Yayyyyyy!!!!!!!!!!!! Functions!!!!!!!!!!!!!!!!!!