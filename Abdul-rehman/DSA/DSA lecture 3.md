# Memory Management

## Stack and Heap
- Stack starts at bottom of memory or the memory location of `0xFFFF`(16 bits  pointer size)
	- While the OS occupies the top portion or the memory location starting from `0x0000` .
	- Between the os at top and stack at bottom the memory is divided into pages and in those pages HEAP is stored at any point there
		- We cant really say where exactly it is stored.
	- Everything declared with the keyword `new` is stored in *heap* with its reference being stored in *stack*.
#### Diagram
|O.S
|-Pages
|-Pages
|-Pages
|-Pages
|Stack

## Static memory allocation
- Memory allocated run time
- New
- Delete
- Can exist only in scope.
- 
## Dynamic memory allocation

- Memory allocated compile time
- Work of new and delete done automatically.
- Can exist beyond scope (until deleted)
