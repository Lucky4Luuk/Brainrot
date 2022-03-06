# Brainrot specification

## Commands
The basic commands are similar to the original brainfuck commands.
The cell pointer points to an 8 bit memory address allocated as consecutive virtual memory when needed.
The virtual memory should be unbounded to the right, but bounded on the left.

|Command|Description
|-------|-----------
|+|Increment value at current 8 bit memory cell [wrapping]
|-|Decrement value at current 8 bit memory cell [wrapping]
|>|Move cell pointer 1 cell to the right
|<|Move cell pointer 1 cell to the left
|[|Jump past the matching ] if the cell at the pointer is 0
|]|Jump back to the matching [ if the cell at the pointer is nonzero
| |
|:FUNC{code}|Function declaration
|@FUNC|Function call

## Function declaration
Basic declaration:
```bf
:foo{
	+++>---<
}
```

## Function calls
```bf
:foo{
	+++>---<
}

:main{
	>+++<		Make sure there's something to subtract in cell 2
	@foo		Call function foo
	--->+++<	Set cell 1 and cell 2 back to 0
}
```
