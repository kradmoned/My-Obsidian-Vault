# Characters and String Constants
- Both single quote and double quotes can be used for strings
- Reserved words cant be used as identifiers
- Assembly is not case sensitive by default
	- But you have an option to make it case sensitive when compiling


# Directives and identifiers
- Cant start identifiers with digits.
- Directives kinda like `#`  in c such as we use `#include` 
	- These are not language instructions they are used to direct the assembler/compiler
	- No code is generated against directives.
	- They act as a hint for the assembler or the compiler.
	- Different assmeblers have different directives.
	- dIRECTIVES ARE USED IN MASM starting from . such as `.386`
	- See masm directives on internet
	- `.model` tells what memory model does it use. `.model flat`
	- `.stdcall` its a  calling convention , like how function are passed argument such as either through stack heap or comb.
		- it also tells who is responsible for deallocating
		- It is used when when we are using windows API as it is required
	- `.stack 4096` allocate stack memory. 
	-  We will learn about Them later
# Instructions
-  They are assemble into machine code by assebler
- Exectude by cpu att run time
- Syntax: Lable mnemonic operands ; comments
	- Label ,comment are optional whule operands depends
-  Lable act as markers
	- Follow identifer rules
# Labels
1. **Data Label:**
    - These labels are used to assign an optional name to data when defining storage in memory for a variable
 -  They mark the starting address (offset) of a data definition
    - A data label must be unique
    - Labels are **not followed by a colon** (e.g., `myArray`)

# Instruction Mnemonics

Instruction mnemonics are a fundamental component of assembly language, serving as the required verbal command that dictates the operation the Central Processing Unit (CPU) will execute

.

Here is an explanation of instruction mnemonics:

What are Instruction Mnemonics?

• **Required Component**

   - The mnemonic is a **required** element of an assembly language instruction

-   An instruction follows the format: `[label:] mnemonic [operands] [;comment]`

.

• **Examples**

   Mnemonics are typically short, capitalized abbreviations that indicate a specific operation, such as **MOV** (move), **ADD** (add), **SUB** (subtract), **MUL** (multiply), **INC** (increment), and **DEC** (decrement)

.

• **Execution**

   Instructions, which contain the mnemonic, are assembled into machine code by the assembler and are **executed at runtime by the CPU**

.

• **Reserved Words**

   - Instruction mnemonics are classified as **reserved words**

. This means they **cannot be used as identifiers** (names for variables, labels, etc.) within the assembly program


• **Coding Standards**

   - Some suggested coding standards recommend capitalizing all reserved words, including instruction mnemonics
- 

#### Operands
Some have no operands one operand or two operands
# Comments

# 
# Example of assembly code (see slides)
