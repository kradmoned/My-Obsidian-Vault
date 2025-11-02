*Arithmetic instructions dont allow us to do addition on two memory space / variables . one of them must be be a register*
What is risk isa?
# Adding Variables to Add sub
- Funtion called `DumpRegs` included in irvine32 display the value of all register
- `Call` ?
- `Invoke ExitProcess,0` is accessing a windows api turning of the program
- `Invoke` is a directive, it is translated to 2 instruction push 0 and call ExitProcess.
- `.data?` directive to declare an uninitialized data segment
	- Like with this `smallArray DWORD 10 DUP(?)`
	- if we define in `.data`  then our program size will increase by alot.
	- `.data` stores and allocates data at compile time. and thus invlude those reserved space at exe stored in harddisk.
	-  Macro like c such as `name=expression` or `count=50` kinda like `#define Size 2` . These are called equal sign directive
		- Things like this don't take extra memory. as such they are directives.
	- *Current Location Counter*: `$` .  It states the offsett with respect to the current segment u are in. Think of segments like .data ,.data?, .code . For example if we are in the .data segment and we use it it will tell how far in memory space we are in there.
		- Can be used to do things like calculate the size of a list/array. Kinda confusing.
-  *EQU Directive* It defines a symbol as either an integer or text expression. Kinda like the equal directive.
	- HAs two forms with  one allowing redefinition.
	- Using `%` sign we can have it evaluate an expression during assembling.
	- Hmm where can we use it in .data .data? also can we use it in .code?.
