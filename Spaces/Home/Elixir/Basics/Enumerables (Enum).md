---
sticker: vault//SVG Icons/Nerd Fonts/select-group-987010.svg
---
Related to [[Lists]] as this is a module in order to manipulate these objects, except for tuples. 

Common Functions: 
- `all?`
	- This function allows you to check a list, if any of them evaluate to `false` the function will return `false`.
- `any?`
	- This function is much like `all?` except when a single value in the enumerable evaluates to `true` it will evaluate to true. 
- Chunking
	- `chunk_every`
		- This function will split an enumerable into several, equally sized chunks. 
		- the `:discard` argument will remove all of the values that remain after the chunking. 
	- `chunk_by`
		- This allows you to group each enumerable based off something other than size. 
```elixir
Enum.chunk_by(["one", "two", "three", "four", "five"], fn(x) -> String.length(x) end)
# ^ Returns [["one", "two"], ["three"], ["four", "five"]]
Enum.chunk_by(["one", "two", "three", "four", "five", "six"], fn(x) -> String.length(x) end)
# ^ Returns [["one", "two"], ["three"], ["four", "five"], ["six"]]. 
# Because of how the grouping is right to left, despite that the length of "six" is like like "one" and "two" that means it will be in its own group. It's like a slider on a tape, putting a cut where it finds a difference. 
```
- `each`
	- In situations where you may need to iterate over a enumerable without having to create a new value. It allows you to
- `map`
	- 
- `min`
	- 
- `max`
	- 
- `filter`
	- 
- `reduce`
	- 
- `sort`
	- 
- `uniq`
	- 