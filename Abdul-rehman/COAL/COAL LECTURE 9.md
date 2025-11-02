# Data Related Operators and Directives
As we know directives are instruction for the assembler
## OFFSET Operator
- We can determine the address of any variable through the OFFSETT operator.
- We usually use esi register to store the address \.
```
.data?
bVal BYTE ?

.code
mov esi, OFFSETT bVAl ; ESI = 00404000
```
## PTR Operator
- OVERIDES the default type of a lablel
- See example from slide to understand better and see how it works
- 
### Little Indian Odrder
Due to little endian order the least signinficant bit is accessed first .
Researrch it online.

### Combinining Element
- See slides and make notes bucko 
Of course. Here is the explanation formatted your way.

## TYPE Operator

The **`TYPE`** operator tells you the size, in bytes, of a **single element** of a variable declaration. It's a way to ask the assembler, "How big is the fundamental unit of this data?" This value is determined by the assembler when you build your program, not while it's running. ⚙️

Think of it this way: if you have an array of 4-byte integers, `TYPE` returns `4`, not the total size of the array.

---

### Example

Let's declare several variables using different data type directives:

Code snippet

```
.data
var1 DB 10          ; A single byte (size is 1)
var2 DW 1000        ; A single word (size is 2)
var3 DD 1, 2, 3, 4  ; An array of doublewords (each element's size is 4)
var4 DQ 0           ; A single quadword (size is 8)
```

Now, let's see what the `TYPE` operator returns for each of these when we move the value into a register:

- **`MOV EAX, TYPE var1`**
    
    - **Result:** `EAX` will be **1**, because `var1` was defined with `DB` (Define Byte).
        
- **`MOV EAX, TYPE var2`**
    
    - **Result:** `EAX` will be **2**, because `var2` was defined with `DW` (Define Word).
        
- **`MOV EAX, TYPE var3`**
    
    - **Result:** `EAX` will be **4**. Even though `var3` is an array containing four elements, `TYPE` only returns the size of a single element, which is a `DD` (Define Doubleword).
        
- **`MOV EAX, TYPE var4`**
    
    - **Result:** `EAX` will be **8**, because `var4` was defined with `DQ` (Define Quadword).
        

The `TYPE` operator is very useful for writing flexible code, especially for calculating the memory offsets needed to access elements within an array.
Of course. Here is the explanation formatted in your requested style.

## SIZEOF Operator

The **`SIZEOF`** operator returns the **total size of a variable in bytes**. It calculates this by multiplying the number of elements in the variable (`LENGTHOF`) by the size of a single element (`TYPE`). 📏

Essentially, it answers the question, "How much total memory does this entire variable declaration occupy?" Just like `TYPE`, this value is calculated by the assembler when you build your program, not when it's running.

The formula is: `SIZEOF variable = (LENGTHOF variable) * (TYPE variable)`

---

### Example

Let's use the same set of variables to see how `SIZEOF` works:

Code snippet

```
.data
var1 DB 10          ; 1 element * 1 byte/element = 1 byte total
var2 DW 1000        ; 1 element * 2 bytes/element = 2 bytes total
var3 DD 1, 2, 3, 4  ; 4 elements * 4 bytes/element = 16 bytes total
var4 DQ 0           ; 1 element * 8 bytes/element = 8 bytes total
```

Now, let's see what `SIZEOF` returns for each:

- **`MOV EAX, SIZEOF var1`**
    
    - **Result:** `EAX` will be **1**. (`LENGTHOF` is 1, `TYPE` is 1. `1 * 1 = 1`).
        
- **`MOV EAX, SIZEOF var2`**
    
    - **Result:** `EAX` will be **2**. (`LENGTHOF` is 1, `TYPE` is 2. `1 * 2 = 2`).
        
- **`MOV EAX, SIZEOF var3`**
    
    - **Result:** `EAX` will be **16**. This is where `SIZEOF` is most useful. It knows `var3` has 4 elements (`LENGTHOF`) and each is a `DD` (4 bytes, `TYPE`). The total size is `4 * 4 = 16`.
        
- **`MOV EAX, SIZEOF var4`**
    
    - **Result:** `EAX` will be **8**. (`LENGTHOF` is 1, `TYPE` is 8. `1 * 8 = 8`).


## LENGTHOF Operator

The **`LENGTHOF`** operator returns the **number of elements** in a variable declaration. It's used almost exclusively for arrays to find out how many items are in them. 🔢

It answers the simple question, "How many individual units were defined for this variable?" The value is calculated by the assembler at compile time.

---

### Example

Using the same variables as before, let's see what `LENGTHOF` returns:

Code snippet

```
.data
var1 DB 10          ; A single byte element. Count = 1.
var2 DW 1000        ; A single word element. Count = 1.
var3 DD 1, 2, 3, 4  ; An array with four doubleword elements. Count = 4.
var4 DQ 0           ; A single quadword element. Count = 1.
```

Now, let's see the results of using `LENGTHOF`:

- **`MOV EAX, LENGTHOF var1`**
    
    - **Result:** `EAX` will be **1**. `var1` is a single-element declaration.
        
- **`MOV EAX, LENGTHOF var2`**
    
    - **Result:** `EAX` will be **1**. `var2` is also a single element.
        
- **`MOV EAX, LENGTHOF var3`**
    
    - **Result:** `EAX` will be **4**. This is the most common use case. `LENGTHOF` correctly identifies that there are four distinct doublewords defined for the `var3` array.
        
- **`MOV EAX, LENGTHOF var4`**
    
    - **Result:** `EAX` will be **1**. `var4` is a single element.

## LABLE DIRECTIVE

