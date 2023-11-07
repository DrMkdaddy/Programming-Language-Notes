The Information from [[Data Types]] will be mentioned here. 

- Integers and Floats
	- They both support basic arithmetic operators like 
		- `* and /` for multiplication and division
			- CAUTION: The `/` Operator will always return a float, in order to avoid that it is required to use the `div(dividend, divisor)` function in order to return a proper integer. Additionally the `rem(dividend, divisor)` function does the same work but for the remainder. 
		- `+ and -` for addition and subtraction
- Booleans
	- Booleans have basic operators that are very close to logic gates.
		- `and` and `or` are short-circuiting boolean operators. 
			- These are very close to regular and and or binary logic but with one major difference, as soon as they find a result they stop evaluating the expression. 
			- `||` (pipes) and `&&` (ampersands) are very close to their siblings, however they accept types other than booleans.  
		- `!` will reverse a boolean. `!42` will return `false`, while `!false` or `!nil` will return `true`. Fun fact: This is a non-strict version of just typing out `not`! 
```elixir
-20 || true
# ^ Returns -20 because remember how everything but nil and false return true? 
# It even short circuits and returns true. 
false || 42
# ^ returns 42


```
```elixir
false or true
# ^ returns true. if there were more booleans (which there won't be) it'll short circuit and stop evaluating the moment it completes. 
true and 42
# ^ returns true. 
not false 
#^ returns true
not 42
#

```
