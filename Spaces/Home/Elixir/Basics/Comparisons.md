---
sticker: lucide//git-compare
---
Elixir has Operators for comparing different [[Data Types]] against each other like, `{elixir icon} <=, >=,==, ===, !==, <, >` in order to compare values. 

=== and its brother !== are strict operators, they will return false when comparing floats and integers. 
`{elixir icon} number < atom < reference < function < port < pid < tuple < map < list < bitstring`
```
Many times there will be strange comparisons between types because of how the comparisons between types work. 

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

