---
sticker: vault//SVG Icons/Nerd Fonts/distribute-vertical-center-987596.svg
---
Related to [[Data Types]]. 
- Lists
	- Lists are simple unordered collections of values, they don't have to be unique nor of the same type. 
		- The way that this structure is implemented is via a linked list, where a pointed points to the next object in the array and so on. 
			- This means that appending (putting the object at the end) a item to the list has a complexity of O(n) while prepending (placing a value at the front of the list) has a complexity of O(1)
			- This lends itself to a First-In First Out approach to handling these lists. 
		- You can subtract and concatenate from lists. 
			- NOTE: Lists use strict comparisons for ints and floats. 
			- `["foo", :bar, 42] -- [42, "bar"]` returns `["foo", :bar]` because while an atom's value is its own name it is not its name. 
- Tuples
	- 
- Keyword Lists
	- 
- Maps
	- 