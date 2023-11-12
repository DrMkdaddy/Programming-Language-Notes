---
sticker: vault//SVG Icons/Nerd Fonts/select-group-987010.svg
---
Related to [[Collections]] as this is a module in order to manipulate these objects, except for tuples. 

### Common Functions: 
#### `{elixir}all?`
- This function allows you to check a list, if any of them evaluate to `false` the function will return `false`.
#### `{elixir}any?`
- This function is much like `all?` except when a single value in the enumerable evaluates to `true` it will evaluate to true. 
#### Chunking
- `{elixir}chunk_every`
	- This function will split an enumerable into several, equally sized chunks. 
	- the `:discard` argument will remove all of the values that remain after the chunking. 
- `{elixir}chunk_by`
	- This allows you to group each enumerable based off something other than size. 
```elixir
Enum.chunk_by(["one", "two", "three", "four", "five"], fn(x) -> String.length(x) end)
# ^ Returns [["one", "two"], ["three"], ["four", "five"]]
Enum.chunk_by(["one", "two", "three", "four", "five", "six"], fn(x) -> String.length(x) end)
# ^ Returns [["one", "two"], ["three"], ["four", "five"], ["six"]]. 
# Because of how the grouping is right to left, despite that the length of "six" is like like "one" and "two" that means it will be in its own group. It's like a slider on a tape, putting a cut where it finds a difference. 
```
#### `{elixir}each`
- In situations where you may need to iterate over a enumerable without having to create a new value. It allows you to iterate over a group using an anonymous function or similar. 
- `{elixir icon} Enum.each(["one", "two", "three"], fn(s) -> IO.puts(s) end)` 
	- Returns "one" \\n "two" \\n "three" \\n :ok
	- Note this does return the :ok atom in order to indicate that the process what completed successfully. 
#### `{elixir} map`
- Map does the same thing as `each` but creates a new enumerable instead as a return. 
- `{elixir icon} Enum.map([0, 1, 2, 3], fn(x) -> x - 1 end)` 
	- Returns `{elixir icon} [-1, 0, 1, 2]`
- `{elixir}map_every`
	- Allows you to hit every nth value in the list with a function. 
		- `{elixir icon} Enum.map_every([1, 2, 3, 4, 5, 6, 7, 8], 3, fn x -> x + 1000 end)`
			- Returns `{elixir icon} [1001, 2, 3, 1004, 5, 6, 1007, 8]`
#### `{elixir}min`
- Returns the minimal value in the enumerable. 
	- `{elixir icon} Enum.min([5, 3, 0, -1])`
		- Returns `-1`
	- Can return the value of an anonymous function if the list is empty
		- `{elixir icon} Enum.max([], fn -> :foo end)`
			- Returns `:foo` 
#### `{elixir}max`
- Returns the maximal value in the enumerable. 
	- `{elixir icon} Enum.min([5, 3, 0, -1])`
		- Returns `5`
- Can return the value of an anonymous function if the list is empty
	- `{elixir icon} Enum.min([], fn -> :foo end)`
		- Returns `:foo` 
### `{elixir}filter`
- This function allows you to filter values in a list in order to only return the values that evaluate to true in the provided anonymous function. 
	- `{elixir icon} Enum.filter([1, 2, 3, 4], fn(x) -> rem(x, 2) == 0 end)`
		- Returns `[2, 4]`
#### `{elixir}reduce`
- This function allows you to reduce the enumerable into a single value. 
- You can additionally supply an optional accumulator as well. It seems this value is just added at the end. 
- `{elixir icon} Enum.reduce([1, 2, 3], 10, fn(x, acc) -> x + acc end)`
	- Returns `16`
- `{elixir icon} Enum.reduce(["a","b","c"], "1", fn(x,acc)-> x <> acc end)`
	- Returns `cba1`
	- The function works in a stacking order, it starts with `1`, then stacks `a` on top, then stacks `b`, then finally `c`
### `{elixir}sort`
- Allows you to sort an enumerable. 
- It uses the term ordering as defined in 
	- `{elixir icon} Enum.sort([5, 6, 1, 3, -1, 4])`
		- Returns `{elixir icon} [-1, 1, 3, 4, 5, 6]`
- It follows the same term ordering as mentioned in [[Comparisons]], so there may be some strange behavior when values of different types are in the same enumerable. 
	- `{elixir icon} Enum.sort([:foo, "bar", Enum, -1, 4])`
		- Returns `{elixir icon} [-1, 4, Enum, :foo, "bar"]`
- You may also define a custom sorting function. 
	- `{elixir icon} Enum.sort([%{:val => 4}, %{:val => 1}], fn(x, y) -> x[:val] > y[:val] end)`
		- Returns `{elixir icon} [%{val: 4}, %{val: 1}]
- Without the custom sorting function: 
	- `{elixir icon} Enum.sort([%{:count => 4}, %{:count => 1}])`
		- Returns `{elixir icon} [%{count: 1}, %{count: 4}]`
#### `{elixir}uniq`
- Returns the list without duplicates. 
	- `{elixir icon} Enum.uniq([1, 2, 3, 2, 1, 1, 1, 1, 1])`
		- Returns `{elixir icon} [1, 2, 3]`
- `{elixir}uniq_by`
	- This will also allow you to remove duplicates but you may provide a function in order to perform the comparisons. 
		- `{elixir icon} Enum.uniq_by([%{x: 1, y: 1}, %{x: 2, y: 1}, %{x: 3, y: 3}], fn coord -> coord.y end)`
			- Returns `{elixir icon} [%{x: 1, y: 1}, %{x: 3, y: 3}]`