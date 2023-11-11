---
sticker: vault//SVG Icons/Nerd Fonts/function-variant-985201.svg
---
3### Anonymous Functions 
There functions do not have names, they're meant to be passed around to functions, as seen in the [[Enum Module]] section. In order to define one you will need to define it using either the `{elixir}fn ... end` syntax or the [[Capture Operator]]. 

### Pattern Matching
[[Pattern Matching]] isn't limited to variables in elixir, because functions are first class objects it can be applied to them as well. 
Elixir uses Pattern Matching in order to
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
```

## Named Functions 


![](https://media.tenor.com/uJOLBspTDLoAAAAd/cat-dance.gif)
Yayyyyyy!!!!!!!!!!!! Functions!!!!!!!!!!!!!!!!!!