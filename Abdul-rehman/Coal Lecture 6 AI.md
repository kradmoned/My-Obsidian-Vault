

### RISC vs. CISC & The Big Memory Rule

So, **RISC** (Reduced Instruction Set Computer) is all about simple, fast instructions. A key feature is its "load-store" design, which means you _can't_ do operations directly on stuff in memory. You have to load it into a register first.

This explains the most important rule I learned: you **cannot** do an operation between two memory locations. One of the operands **must** be a register.

> **Example:**
> 
> Code snippet
> 
> ```
> ; This is WRONG ❌
> add myVar1, myVar2 
> ```

> ; This is RIGHT ✅
> 
> mov eax, myVar1
> 
> add eax, myVar2

---

### Directives vs. Instructions

I need to remember the difference here.

- **Instructions** (`MOV`, `ADD`, `CALL`) are commands for the CPU that become machine code.
    
- **Directives** (`.data`, `INVOKE`, `EQU`) are commands for the assembler that help build the program. They don't generate CPU code themselves.
    

---

### Data & Symbol Directives

- **`.data` vs. `.data?`**
    
    - `.data`: For variables I initialize with a value. This stuff goes into the `.exe` file, making it bigger.
        
    - `.data?`: For uninitialized variables. This just reserves space, keeping the `.exe` smaller. The OS allocates the memory at runtime.
        
    - Example: `myArray DWORD 10 DUP(?)` goes in `.data?`.
        
- **`EQU` and `=` Directives**
    
    - These are basically like `#define` in C. They create symbolic constants that the assembler replaces with their value during compilation.
        
    - They don't take up any memory in the final program.
        
- **The Dollar Sign (`$`) Counter**
    
    - This is a neat trick. `$` gives me the current memory offset in whatever segment I'm in.
        
    - I can use it to calculate the size of an array automatically: `ListSize = ($ - list)`.
        

---

### Calling Procedures

- **`CALL`** is the actual CPU instruction. It pushes the return address to the stack and jumps to the procedure.
    
- **`INVOKE`** is a handy directive that makes calling functions easier. It's a macro that automatically `PUSH`es all the arguments onto the stack for me and then makes the `CALL`.
    
    > **Example:** `INVOKE ExitProcess, 0` is just a shortcut for writing:
    
    > Code snippet
    > 
    > ```
    > push 0
    > call ExitProcess
    > ```
    
- **`DumpRegs`**: This is a function from the Irvine32 library. Calling it is super useful for debugging because it just prints out the contents of all my registers. 