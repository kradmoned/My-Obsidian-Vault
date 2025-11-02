*Using Slide 5 or lEcture 5*
# Operand Types
-  Immediate 
	- It is the constant integer
-  Register
-  Memory
# Instruction Operand Notation 
*Just see it from slides*

# Direct Memory Operand
- A direct memory operand is named reference to storage in memory
- Square bracket means any value in it is an address
## MOV Instruction
- Left Operand ins destination
- `MOV destination,source`
- No more than one memory operand permitted(What does it mean).
	- Means both the operand cant be memory reference itself
		- `MOV a,b` *not allowed*.
- CS , EIP and IP cannot be destination
	- Entry point of program is written to one of the instruction pointer.
- No immediate to segment moves(What does it mean? seriously)
- *See the example in the slide*
- Additional Question Can we mov an 8bit value to 16 bit register or vice versa. What will happen?
- Operands Of the mov Instruction must be the same size.
- *see slide again the next one*
### MOVZS Or Zero Extension
- This is used for copying a smaller value into a larger destinationn.
- The upper portion becomes all zeroes
- *It requires the destination to be a register*
- Used for Unsigned Numbers
### MoVSX or sign extension
- Used for copying a smaller signed value into a larger destination
- It fills the upper half with all ones
	- Why is that
- *The destination Must also be a register*
### XCHG instruction
- Used for swapping the values
- One of the operands must be a register.
- No immediate operands are permitted.
- I think the size should also be the same meaning same bit areas. Need to confirm.
	- Yeah should be same , most instruction require the same size. Only some allow size mismatch.
