---
sticker: lucide//git-compare
---
Related to [[Basic Operations]] and [[Data Types]]

Elixir has Operators for comparing 
different values like , `<=, >=,==, ===, !==, <, >` in order to compare values. 
this is the order for the values and their comparisons. 
=== and its brother !== are strict operators, they will return false when comparing floats and integers. 
```elixir
number < atom < reference < function < port < pid < tuple < map < list < bitstring
```
Many times there will be strange comparisons between types because of how this works. Perhaps javascript is similar but atleast this has rhyme and reason. 

Elixir has both string interpolation (very similar to Python's F Strings) and String Concatenation. 
```elixir
	String Interpolation
		name = "Sean"
		"Hello, #{name}"
		# ^ Returns Hello, Sean
	String Concatenation 
		name = "Alex"
		"Hello, " <> name
		# ^ Returns Hello, Alex
	
```

