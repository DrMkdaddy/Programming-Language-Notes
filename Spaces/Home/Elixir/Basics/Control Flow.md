### If and Unless Statements
Control Structures, like `{elixir}if and unless (?)`, `{elixir}cond` and `{elixir} with`
Example of if statements. 
```elixir
if String.valid?("Hello") do
  "Valid string!"
else
  "Invalid string."
end
# ^ Returns"Valid string!"
```
Unless statements are a lot like if statements, except that they work if the statement evaluates to `{elixir}false` and not `{elixir} true`. 
```elixir
unless is_integer("hello") do
  "Not an Int"
end
# ^ "Not an Int"
```

### Case Statements
Case statements allow you to match against multiple patterns. 
```elixir
case {:ok, "Hello World"} do
  {:ok, result} -> result
  {:error} -> "Uh oh!"
  _ -> "Catch all"
end
# ^ Returns "Hello World"
```
Without the `__` variable the match will fail, raising an error. Additionally it serves as an else statement that "everything else" will be funneled into. 
The `case` statement uses [[Pattern Matching]] so in order to match against existing variables you will need to use the pin operator. 

