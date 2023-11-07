---
sticker: lucide//git-compare
---
Related to [[Basic Operations]] and [[Data Types]]

Elixir has Operators for comparing 
different values like , `<=, >=,==, ===, !==, <, >` in order to compare values. 
this is the order for the values and their comparisons. 
```elixir
number < atom < reference < function < port < pid < tuple < map < list < bitstring
```
Many times there will be strange comparisons between types because of how this works. Perhaps javascript is similar but atleast this has rhyme and reason. 