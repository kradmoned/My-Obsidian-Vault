# What is calling ocnvention?
How are arguments pass tp the fucntion is the calling convention such as `stdcall`
# Coding Standards
# Process of creating an executable
This is for a compiled language like c
- Prepossessing
- Compiling
- Assembling
- Link

For Assembly
- Source File 
- Assembled  To Object File
	- A lisitng File is also generated. Research a bit about it. A way of knowing how our assemble work, what kinda machine code it generate.
- Linker
	- Map File
- . 
# Defining Data
# Intrinsic Data Types

The intrinsic data types are those defined when using data definition statements to set aside storage in memory for a variable.

These types include various integer and real number formats:

|Data Type|Size / Description|Details and Usage|Sources|
|:--|:--|:--|:--|
|**BYTE**|8-bit unsigned integer.|Represents the smallest unsigned byte, capable of storing values from 0 up to 255.||
|**SBYTE**|8-bit signed integer.|Represents the smallest signed byte (–128) up to the largest signed byte (+127). When using the Microsoft debugger, the `SBYTE` value is automatically displayed in decimal with a leading sign.||
|**WORD**|16-bit unsigned integer.|Used to define storage for 16-bit integers or double characters. The largest unsigned value is 65535.||
|**SWORD**|16-bit signed integer.|Used to define storage for 16-bit signed integers. The smallest signed value is –32768.||
|**DWORD**|32-bit unsigned integer.|Used for storage definitions of unsigned 32-bit integers.||
|**SDWORD**|32-bit signed integer.|Used for storage definitions of signed 32-bit integers. The smallest signed value is –2147483648.||
|**QWORD**|64-bit integer.|Also referred to as quadwords (8 bytes).||
|**TBYTE**|80-bit integer.|Also referred to as tenbyte values.||
|**REAL4**|4-byte IEEE short real.|Used in storage definitions for real numbers.||
|**REAL8**|8-byte IEEE long real.|Used in storage definitions for real numbers.||
|**REAL10**|10-byte IEEE extended real.|Used in storage definitions for real numbers.||

### Data Storage Order

All data types larger than a single byte store their individual bytes in **Little Endian Order**. In this arrangement, the **least significant byte** occurs at the first (lowest) memory address. For example, a `DWORD` initialized as `12345678h` will have its bytes stored in reverse order in memory.


# Data Definition Statement

A **data definition statement** is used to set aside storage in memory for a variable.

### Key Characteristics:

- **Purpose:** It reserves space for a variable in memory.
- **Naming:** It may optionally assign a name (label) to the data being defined.
- **Syntax:** The general structure is:
    
    ```
    [name] directive initializer [,initializer] . . .
    ```
    
    (e.g., `value1 BYTE 10`).
- **Initializers:** All initializers provided in the statement become **binary data** in memory.
- **Directives Used:** The directive used corresponds to the intrinsic data type being defined, such as `BYTE`, `SBYTE`, `WORD`, `SWORD`, `DWORD`, `SDWORD`, `QWORD`, `TBYTE`, `REAL4`, `REAL8`, or `REAL10`.
- **Uninitialized Data:** Storage can be declared uninitialized using the initializer `?` (e.g., `value6 BYTE ?`). Declaring uninitialized data can reduce the program's executable (EXE) file size.



Variable declaration in Assembly Language is performed using a **Data Definition Statement**. This process sets aside storage in memory for a variable, typically within the **`.data`** segment of the program.

## The Data Definition Statement

A data definition statement is a command recognized by the assembler that reserves space for a variable in memory.

The general syntax is:

```
[name] directive initializer [,initializer] . . .
```

1. **`[name]` (Optional Label):** This is the identifier used to reference the variable's address (offset).
2. **`directive`:** This specifies the intrinsic data type, determining the size of the memory allocated (e.g., `BYTE`, `DWORD`, `REAL4`).
3. **`initializer`:** This defines the initial value(s) stored in the allocated memory. All initializers become **binary data** in memory.

### Intrinsic Data Type Directives

The intrinsic directives are used as part of the data definition statement to define storage for various integer and real number formats:

|Directive|Size / Description|Example Declaration|Source(s)|
|:--|:--|:--|:--|
|**BYTE**|8-bit unsigned integer|`value1 BYTE 'A'` or `list1 BYTE 10,20,30,40`|
|**SBYTE**|8-bit signed integer|`value4 SBYTE -128`|
|**WORD**|16-bit unsigned integer|`word1 WORD 65535`|
|**SWORD**|16-bit signed integer|`word2 SWORD –32768`|
|**DWORD**|32-bit unsigned integer|`val1 DWORD 12345678h`|
|**SDWORD**|32-bit signed integer|`val2 SDWORD –2147483648`|
|**QWORD**|64-bit integer (quadword)|`quad1 QWORD 1234567812345678h`|
|**TBYTE**|80-bit integer (tenbyte)|`val1 TBYTE 1000000000123456789Ah`|
|**REAL4**|4-byte IEEE short real|`rVal1 REAL4 -2.1`|
|**REAL8**|8-byte IEEE long real|`rVal2 REAL8 3.2E-260`|
|**REAL10**|10-byte IEEE extended real|`rVal3 REAL10 4.6E+4096`|

## Declaring Arrays and Strings

Variables can be defined as arrays or strings using multiple initializers separated by commas:

1. **Arrays:** Multiple values of the specified type are stored consecutively.
    
    ```
    myList WORD 1,2,3,4,5 ; array of words
    ```
    Multiple arrays are stored contiguosly
	`lis11 WORD 1,2,3,4;
	    WORD 5,6,7,8;
	    ;Here the other list is stored after first one  so can be accessed without an `
	    
    
2. **Strings:** A string is implemented as an array of characters, often enclosed in quotation marks and typically null-terminated (followed by a null byte, `0`).
    
    ```
    str1 BYTE "Enter your name",0
    ```
    
3. **The DUP Operator:** This operator is used to allocate space for an array or string efficiently. The syntax is `counter DUP ( argument )`.
    
    ```
    var1 BYTE 20 DUP(0)    ; 20 bytes, all equal to zero
    ShortArray REAL4 20 DUP(0.0) ; array of real numbers
    ```
    

## Declaring Uninitialized Data

Storage can be declared without an initial value using the question mark initializer (`?`).

- **Using the `?` Initializer:**
    ```
    value6 BYTE ?       ; uninitialized byte storage
    word3 WORD ?        ; uninitialized word storage
    ```
    
- **Using the `.data?` Directive:** Variables declared with the `?` initializer within the separate **`.data?`** segment are stored as uninitialized data. This method has the advantage of reducing the program's executable (EXE) file size.
    
    ```
    .data?
    smallArray DWORD 10 DUP(?)
    ```


## Strings in Assembly Language

A string in Assembly Language is fundamentally defined as an **array of characters**. Since ASCII characters are defined as occupying **1 byte**, strings are typically declared using the `BYTE` directive.

### 1. Implementation and Storage

|Concept|Description|Source(s)|
|:--|:--|:--|
|**Basic Structure**|A string is implemented as an array where **each character occupies a single byte** of storage.||
|**Character Constants**|Character and string constants can be enclosed in either **single or double quotes**. Examples include `'A'`, `"x"`, `"ABC"`, and `'xyz'`.||
|**Embedded Quotes**|It is possible to embed one type of quotation mark inside a string enclosed by the other type, such as `'Say "Goodnight," Gracie'`.||
|**Character Sets**|Character storage typically utilizes standard ASCII (0 – 127), extended ASCII (0 – 255), or ANSI (0 – 255). Unicode is also supported and can theoretically encode over a million code points.||

### 2. Null-Termination

Strings are often **null-terminated**. A null-terminated string is an array of characters immediately followed by a **null byte**.

The null byte, which has a value of `0`, signifies the end of the string.

**Example of Null-Terminated Declaration:**

```
str1 BYTE "Enter your name",0
```

### 3. Declaration and Formatting

Strings are declared using the Data Definition Statement format: `[name] directive initializer [,initializer] . . .`. Since characters are 1 byte, the `BYTE` directive is used.

#### Defining Strings Across Multiple Lines

- A single string enclosed in one set of quotation marks **cannot be broken down in multiple lines** without using single or double quotation marks for each part.
- To continue defining a single string across several source code lines, the previous line must end with a **comma**.

**Example of Multi-line Definition:**

```
greeting BYTE "Welcome to the Encryption Demo program "
BYTE "created by Kip Irvine.",0
```

#### End-of-Line Characters

To include platform-specific line breaks within a string (such as in a menu or prompt), special hexadecimal character sequences are used:

- `0Dh` = carriage return
- `0Ah` = line feed

**Example using control characters:**

```
newLine BYTE 0Dh,0Ah,0
```

### 4. Allocating Space with DUP Operator

The **`DUP` operator** can be used to allocate storage for a string or array of bytes efficiently.

- **Syntax:** `counter DUP ( argument )`
- **Purpose:** The operator repeats the `argument` a number of times equal to the `counter`.

**Example using DUP for repeated characters:**

```
var3 BYTE 4 DUP("STACK") ; Generates 20 bytes: "STACKSTACKSTACKSTACK"
```