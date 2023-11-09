---
sticker: vault//SVG Icons/Nerd Fonts/lock-pattern-984810.svg
---
### Match Operator
The `{elixir }=` is actually a match operator **CURVE-BALL!!!!** It is almost exactly like the equals sign in algebra, where the right hand side is matched with the left hand side, if it succeeds it returns the value. 

```elixir
list = [1, 2, 3]
# ^ Returns [1, 2, 3]
[1, 2, 3] = list
# ^ Returns [1, 2, 3]
[] = list
# ^ ** (MatchError) no match of right hand side value: [1, 2, 3]
[1 | tail] = list
# ^ [1, 2, 3]
tail
# ^ [2, 3]
[2 | _] = list
# ^ ** (MatchError) no match of right hand side value: [1, 2, 3]
{:ok, value} = {:ok, "Successful!"}
# ^ Returns {:ok, "Successful!"}
value 
# ^ "Successful!"
{:ok, value} = {:error}
# ^ ** (MatchError) no match of right hand side value: {:error}
```

### Pin Operator 
The pin operator `{elixir} ^` will stop variable rebinding, keeping the previous match instead of changing to the new one. 

```elixir
x = 1
# ^ Returns 1
^x = 2
# ^ ** (MatchError) no match of right hand side value: 2 This is the return because of how the previous value was x = 1. Instead of rebinding it was pinned to the previous match 
{x, ^x} = {2, 1}
# ^ {2, 1}
x
# ^ 2 The pinned pattern managed to work and the variable was also repinned
```
In Elixir 1.2 this functionality was extended to support pins in 