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
			- `["foo", :bar, 42] -- [42, "bar"]` returns `["foo", :bar]` because while an atom's value is its own name it is not its name. 
			- `[1,2,2,3,2,3] -- [1,2,3,2]` returns `[2, 3]` because values will kill themselves from right to left. 
		- There are helper functions to help you grab a head (the first-most value on a list) and the tail (the rest of the list). 
			- `hd [3.14, :pie, "Apple"]` returns `3.14` as it is the head. 
			- `tl [3.14, :pie, "Apple"]` returns `[:pie, "Apple"]`
- Tuples
	- Tuples are like lists but with one major difference, they are stored contiguously in memory. It's quick to access their data but expensive to prepend or append more values. 
	- Closest to traditional arrays. More or less the inverse of a List. 
		- While looking up a value is O(1) unlike the list's O(N) look up time. 
		- Adding a new value is O(N) while with a list it is O(1).
		- This is because an entirely new copy of the tuple must be put into memory, instead of being appended or prepended to. 
		- Tuples are a common way for functions to return information. 
	- `{3.14, :pie, "Apple"}` returns `{3.14, :pie, "Apple"}`
	- `File.read("path/to/existing/file")` would return `{:ok, "... contents ..."}`
- Keyword Lists
	- Keyword lists are a special list of tuple where the first value is an atom. 
	- These have similar performance to lists and are also used as ways to pass optional arguments to functions. 
		- `[foo: "bar", hello: "world"]` returns `[foo: "bar", hello: "world"]`
		- `[{:foo, "bar"}, {:hello, "world"}]` returns `[foo: "bar", hello: "world"]`
			- As I can see these have the same returns. I will likely use the second method of writing it as it is much more explicit to me. 
- Maps
	- Equivalent to dictionaries. The traditional Key-Value Store. 
	- Defined using %{}. 
	- With maps there is a special syntax for maps that only use atoms as their keys. 
		- `{foo: "bar", hello: "world"}` returns `%{foo: "bar", hello: "world"}`
		- `%{foo: "bar", hello: "world"} == %{:foo => "bar", :hello => "world"}` returns `true`
			- This is good to know as this helps to bridge my learning gap between elixir and python! 
	- Something else about maps is that they provide their own syntax for updating a key. 
		- `map = %{foo: "bar", hello: "world"}` returns `%{foo: "bar", hello: "world"}`
		- `%{map | foo: "baz"}` returns `%{foo: "baz", hello: "world"}`
			- There is a problem with this approach. It does require 
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