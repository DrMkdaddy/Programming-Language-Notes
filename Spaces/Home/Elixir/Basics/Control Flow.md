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
