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
	- In situations where you may need to iterate over a enumerable without having to create a new value. It allows you to iterate over a group using an anonymous function or similar. 
	- `Enum.each(["one", "two", "three"], fn(s) -> IO.puts(s) end)` 
		- Returns "one" \\n "two" \\n "three" \\n :ok
		- Note this does return the :ok atom in order to indicate that the process what completed successfully. 
- `map`
	- Map does the same thing as `each` but creates a new enumerable instead as a return. 
	- `Enum.map([0, 1, 2, 3], fn(x) -> x - 1 end)` 
		- Returns `[-1, 0, 1, 2]`
- `min`
	- Returns the minimal value in the enumerable. 
		- `Enum.min([5, 3, 0, -1])`
			- Returns `-1`
		- Can return the value of an anonymous function if the list is empty
			- `Enum.max([], fn -> :foo end)`
				- Returns `:foo` 
- `max`
	- Returns the maximal value in the enumerable. 
		- `Enum.min([5, 3, 0, -1])`
			- Returns `5`
	- Can return the value of an anonymous function if the list is empty
		- `Enum.min([], fn -> :foo end)`
			- Returns `:foo` 
- `filter`
	- This function allows you to filter values in a list in order to only return the values that evaluate to true in the provided anonymous function. 
		- `Enum.filter([1, 2, 3, 4], fn(x) -> rem(x, 2) == 0 end)`
			- Returns `[2, 4]`
- `reduce`
	- This function allows you to reduce the enumerable into a single value. 
	- You can additionally supply an optional accumulator as well. It seems this value is just added at the end. 
	- `Enum.reduce([1, 2, 3], 10, fn(x, acc) -> x + acc end)`
		- Returns `16`
	- `Enum.reduce(["a","b","c"], "1", fn(x,acc)-> x <> acc end)`
		- Returns `cba1`
		- The function works in a stacking order, it starts with `1`, then stacks `a` on top, then stacks `b`, then finally `c`
- `sort`
	- Allows you to sort an enumerable. 
	- It uses the term ordering as defined in 
		- `Enum.sort([5, 6, 1, 3, -1, 4])`
			- Returns `[-1, 1, 3, 4, 5, 6]`
	- It follows the same term ordering as mentioned in [[Comparisons]], so there may be some strange behavior when values of different types are in the same enumerable. 
		- `Enum.sort([:foo, "bar", Enum, -1, 4])`
			- Returns `[-1, 4, Enum, :foo, "bar"]`
	- You may also define a custom sorting function. 
		- `Enum.sort([%{:val => 4}, %{:val => 1}], fn(x, y) -> x[:val] > y[:val] end)`
		- Returns `[%{val: 4}, %{val: 1}]
	- Whole 
- `uniq`
	- 