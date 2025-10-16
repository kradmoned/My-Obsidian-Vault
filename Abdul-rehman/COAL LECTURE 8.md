
---

# Direct-Offset Operands in MASM32

## 1. What Are They? 🤔

A **Direct-Offset operand** is a way of accessing memory by combining a **direct memory address** with a **numeric offset**. This lets you access data at a specific location relative to a known starting point.

Think of it like a street address (`direct`) and an apartment number (`offset`).

Formula:

Effective Address = Base Address of Variable + Offset

---

## 2. Why Use Them?

- **Arrays:** Essential for accessing specific elements in an array.
    
- **Structs:** Used to access individual fields within a structure.
    
- **Data Manipulation:** Allows for flexible and dynamic memory access.
    

---

## 3. Syntax and Examples

### Accessing Array Elements

The most common use case. Remember, arrays are zero-indexed.

**Example:**

Code snippet

```
.data
myArray  BYTE  10h, 20h, 30h, 40h
```

To get the 3rd element (`30h`):

Code snippet

```
mov al, [myArray + 2]  ; Moves 30h into the AL register
```

- **`myArray`** is the direct base address.
    
- **`+ 2`** is the offset in bytes.
    

You can also use a register for the offset:

Code snippet

```
mov esi, 2
mov al, [myArray + esi]  ; Same result, more flexible
```

---

## 4. `OFFSET` Operator vs. Direct-Offset

Don't get these confused!

- **Direct-Offset:** `[variable + number]` - Accesses the _value_ at a calculated address.
    
- **`OFFSET` operator:** `OFFSET variable` - Gets the _address_ of the variable itself.
    

**Example:**

Code snippet

```
mov esi, OFFSET myArray  ; ESI now holds the memory address of myArray
mov al, [esi + 2]        ; Now you can use the address in ESI for indirect access
```


```array DWORD 1,2,3
	MOV EAX,array
	XCHNG EAX,[array+4]
	MOV array,EAX; 2,1,3
	MOV EAX,[array+8]; EAX = 3
	XCHNG EAX,[array] , 3,1,3, EAX =2
	MOV [array+8], EAX ; 3,1,2 
```

# INC and DEC instruction
- Single operand Instruction
- Can use different types of operand
	- Such as ax, al
# WHat is overflow flag used for and carry flag used for?

# NEG Instruction and flags

# Implementing Arithmetic Expressions.
- HLL compilers translate mathematical expression into assemblylanguage , for example
- See example from slides
# Flags affected by arithmatic
- In intel ISA the recent result of instruction sett flags
- The MOV instruction never affects the flags
- Most of instruction do change the flag bits
- See the concept flag on slide
## Zero FLag(ZF)
- The zero flag is set when result is zero
```
mov cx,1
sub cx,1; zf = 1


```

## Sign Flag(SF)
- It depends on msb , if it is zero then  SF is also zero and if its one then SF is also one
## Carry Flag(CF)
- The carry flag is set when the result of an operation generates an unsigned value that is out of range for the destination operand.
```
mov al. 0ffh 
add all,1   CF = 1. AL = 00
```
- If carry out of MSB or borrow in then it is set to one.
## OverFlow Flag
- It is used in signed calculation
- If you perform some signed computation and add two positive numbers than it should be positive but in case of overflow it will be negative
```asm
mov al. +127
add a,1  ; OF =1 . AL =???

; Example 2
mov al , 7Fh ; OF = 1, AL  = 80h
add al, 1
```
Both Examples are exactly the same
### A rule of thumb
- Overflow is only sey when two positive operands are added and their sum is negative and similarly the reverse


