---
sticker: vault//SVG Icons/Nerd Fonts/distribute-vertical-center-987596.svg
---
Related to [[Data Types]]. 
- Lists
	- Lists are simple unordered collections of values, they don't have to be unique nor of the same type. 
		- The way that this structure is implemented is via a linked list, where a pointer points to the next object in the array and so on. 
			- This means that appending (putting the object at the end) a item to the list has a complexity of O(n) while prepending (placing a value at the front of the list) has a complexity of O(1)
			- This lends itself to a First-In First Out approach to handling these lists. 
		- You can subtract and concatenate from lists. 
			- NOTE: Lists use strict comparisons for ints and floats. 
			- `{elixir icon} ["foo", :bar, 42] -- [42, "bar"]` returns `{elixir icon} ["foo", :bar]` because while an atom's value is its own name it is not its name. 
			- `{elixir icon} [1,2,2,3,2,3] -- [1,2,3,2]` returns `{elixir icon} [2, 3]` because values will kill themselves from right to left. 
		- There are helper functions to help you grab a head (the first-most value on a list) and the tail (the rest of the list). 
			- `{elixir icon} hd [3.14, :pie, "Apple"]` returns `{elixir icon} 3.14` as it is the head. 
			- `{elixir icon} tl [3.14, :pie, "Apple"]` returns `{elixir icon} [:pie, "Apple"]`
- Tuples
	- Tuples are like lists but with one major difference, they are stored contiguously in memory. It's quick to access their data but expensive to prepend or append more values. 
	- Closest to traditional arrays. More or less the inverse of a List. 
		- While looking up a value is O(1) unlike the list's O(N) look up time. 
		- Adding a new value is O(N) while with a list it is O(1).
		- This is because an entirely new copy of the tuple must be put into memory, instead of being appended or prepended to. 
		- Tuples are a common way for functions to return information. 
	- `{elixir icon} {3.14, :pie, "Apple"}` returns `{elixir icon} {3.14, :pie, "Apple"}`
	- `{elixir icon} File.read("path/to/existing/file")` would return `{elixir icon} {:ok, "... contents ..."}`
- Keyword Lists
	- Keyword lists are a special list of tuple where the first value is an atom. 
	- These have similar performance to lists and are also used as ways to pass optional arguments to functions. 
		- `{elixir icon} [foo: "bar", hello: "world"]` returns `{elixir icon} [foo: "bar", hello: "world"]`
		- `{elixir icon} [{:foo, "bar"}, {:hello, "world"}]` returns `{elixir icon} [foo: "bar", hello: "world"]`
			- As I can see these have the same returns. I will likely use the second method of writing it as it is much more explicit to me. 
- Maps
	- Equivalent to dictionaries. The traditional Key-Value Store. 
	- Defined using %{}. 
	- With maps there is a special syntax for maps that only use atoms as their keys. 
		- `{elixir icon} {foo: "bar", hello: "world"}` returns `{elixir icon} %{foo: "bar", hello: "world"}`
		- `{elixir icon} %{foo: "bar", hello: "world"} == %{:foo => "bar", :hello => "world"}` returns `{elixir icon} true`
			- This is good to know as this helps to bridge my learning gap between elixir and python! 
	- Something else about maps is that they provide their own syntax for updating a key. 
		- `{elixir icon} map = %{foo: "bar", hello: "world"}` returns `{elixir icon} %{foo: "bar", hello: "world"}`
		- `{elixir icon} %{map | foo: "baz"}` returns `{elixir icon} %{foo: "baz", hello: "world"}`
			- There is a problem with this approach. It does require creating a new map. As all values in elixir are immutable.
			- Attempting to update a key that doesn't exist will raise a KeyError. z
```elixir
map = %{:foo => "bar", "hello" => :world}
# ^ returns %{:foo => "bar", "hello" => :world}
map[:foo]
# ^ returns "bar"
map["hello"]
# ^ returns :world
# As of Elixir 1.2 variables can also be used as keys
key = "hello"
%{key => "world"}
# ^ returns %{"hello" => "world"}
# Duplicates will also overwrite the former value. 
%{:foo => "bar", :foo => "hello world"}
# ^ Returns %{foo: "hello world"}
```