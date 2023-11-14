---
sticker: vault//SVG Icons/Nerd Fonts/car-shift-pattern-986944.svg
---
[[Spaces/Home/Elixir/Basics/Pattern Matching|Pattern Matching]] isn't limited to variables in elixir, because functions are first class objects it can be applied to them as well. 
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

### Pattern Matching in Action
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