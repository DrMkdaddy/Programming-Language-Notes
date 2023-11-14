---
sticker: vault//SVG Icons/Nerd Fonts/format-text-wrapping-overflow-986383.svg
---
### `{elixir} if and unless` Statements
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

### `{elixir}case` Statements
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
The `case` statement uses [[Spaces/Home/Elixir/Basics/Pattern Matching]] so in order to match against existing variables you will need to use the pin operator. 

### `{elixir} cond` Statements 
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

### `{elixir}with` Statements
This is used in situations where you may use a nested `{elixir}case` statement or situations where you can't cleanly pipe things together, the expression is made up of the keywords, generators, and finally an expression. 
Generators will be elaborated more in [[List Comprehensions]] but for now they use [[Spaces/Home/Elixir/Basics/Pattern Matching]] to compare the right side (<-) to the left. 
```elixir
user = %{first: "Sean", last: "Callan"}
%{first: "Sean", last: "Callan"}
with {:ok, first} <- Map.fetch(user, :first),
     {:ok, last} <- Map.fetch(user, :last),
     do: last <> ", " <> first
# ^ Returns"Callan, Sean"
```
If the expression fails to match the non-matching keyword will be value will be returned. 
```elixir 
user = %{first: "doomspork"}
%{first: "doomspork"}
with {:ok, first} <- Map.fetch(user, :first),
     {:ok, last} <- Map.fetch(user, :last),
     do: last <> ", " <> first
# ^ Returns :error
```
A larger example where `{elixir} with` can refactor and make a nested case statement more readable. 
Before Refactor: 
```elixir
case Repo.insert(changeset) do
  {:ok, user} ->
    case Guardian.encode_and_sign(user, :token, claims) do
      {:ok, token, full_claims} ->
        important_stuff(token, full_claims)
      error ->
        error
    end
  error ->
    error
end
```
After Refactor: 
```elixir
with {:ok, user} <- Repo.insert(changeset),
     {:ok, token, full_claims} <- Guardian.encode_and_sign(user, :token, claims) do
  important_stuff(token, full_claims)
end
```
Also, with statements now support else! 
```elixir
import Integer
Integer
m = %{a: 1, c: 3}
%{a: 1, c: 3}
a =
  with {:ok, number} <- Map.fetch(m, :a),
    true <- is_even(number) do
      IO.puts "#{number} divided by 2 is #{div(number, 2)}"
      :even
  else
    :error ->
      IO.puts("We don't have this item in map")
      :error
    _ ->
      IO.puts("It is odd")
      :odd
  end
It is odd
:odd
```