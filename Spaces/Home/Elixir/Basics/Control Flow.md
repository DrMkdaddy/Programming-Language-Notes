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

### Cond Statements 
When you need to match conditions rather than values you can use `cond` statements. 
```elixir 
cond do
  2 + 2 == 5 ->
    "This will not be true"
  2 * 2 == 3 ->
    "Nor this"
  1 + 1 == 2 ->
    "But this will"
end
# ^ Returns "But this will"
```
This like else if or elif.
Like `{elixir}case` you will need to use a "catch all" clause in order to match any extraneous circumstances. 
```elixir
cond do

  7 + 1 == 0 -> "Incorrect"

  true -> "Catch all"

end
"Catch all"
```