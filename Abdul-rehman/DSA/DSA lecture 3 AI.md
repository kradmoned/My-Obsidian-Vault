---
creation_date: 2025-09-17
course: C++ Programming
lecture: 2
tags: [cpp, memory, stack, heap, static-allocation, dynamic-allocation]
---

# Lecture Notes: Memory Management in C++

This lecture explores how a C++ program organizes and uses memory. Understanding the difference between the [[Stack Memory|Stack]], the [[Heap Memory|Heap]], and the different allocation strategies is fundamental to writing safe and efficient C++ code.

---

## 1. Memory Layout: [[Stack Memory]] and [[Heap Memory]]

A program's memory is typically divided into several segments. For this discussion, we'll focus on the conceptual layout of the Stack and Heap.

- **Operating System (OS)**: Occupies a reserved section of memory (conceptually at the "top," with low memory addresses like `0x0000...`).
- **[[Stack Memory|Stack]]**: A region of memory that grows and shrinks automatically as functions are called and return. It's highly organized and managed by the CPU.
    - Conceptually, the stack starts at a high memory address (e.g., `0xFFFF...` for a 16-bit system) and ==grows downwards== towards lower addresses.
- **[[Heap Memory|Heap]]**: A large pool of memory available for manual, long-term allocation. It is less organized than the stack.
    - The heap occupies the large, unallocated region of memory between the OS and the stack. It's often managed in chunks called "pages."
    - We can't know the exact address where heap memory will be allocated; it's determined by the memory manager at runtime.

### Visual Diagram of Memory Layout

> [!NOTE] Incorporating Visuals
> You can recreate this diagram in Obsidian using tools like Mermaid or Excalidraw for a more interactive note. For now, this text-based representation captures the concept.
> +--------------------------------+ <-- Low Address (e.g., 0x0000)  
| Operating System |  
+--------------------------------+  
| Program Code |  
+--------------------------------+  
| Static/Global Data |  
+--------------------------------+  
| |  
| ^ |  
| | HEAP |  
| | (grows upwards) |  
| |  
+--------------------------------+  
| (free memory) |  
+--------------------------------+  
| |  
| | (grows downwards) |  
| | STACK |  
| v |  
| |  
+--------------------------------+ <-- High Address (e.g., 0xFFFF)

- **Rule of Thumb**: Anything declared with the `new` keyword is allocated on the **heap**. The ==pointer== to that heap memory is itself a local variable and is stored on the **stack**.

> [!EXAMPLE] Stack and Heap Interaction
> ```cpp
> void createObject() {
>     int stackVar = 20; // Stored directly on the stack.
>     int* heapPtr = new int(10); // '10' is on the heap.
>                                // 'heapPtr' (the address) is on the stack.
> } // 'stackVar' is destroyed.
>   // 'heapPtr' is destroyed, but the memory for '10' on the heap is NOT.
>   // This is a memory leak!
> ```

---

## 2. Memory Allocation Strategies

There are two primary ways memory is allocated in C++.

### Static Memory Allocation

*(Note: The definition was corrected from the initial notes.)*

- **When**: Memory is allocated at ==compile time==.
- **How**: The compiler calculates the exact size and location for variables before the program runs. This includes global variables, static variables, and local variables (on the stack).
- **Lifetime**:
    - **Local (Stack) Variables**: Exist only within their **scope** (e.g., inside the function where they are declared). Memory is automatically reclaimed when the scope is exited.
    - **Global/Static Variables**: Exist for the entire duration of the program.
- **Management**: Done ==automatically==. No `new` or `delete` is needed.

```cpp
void myFunction() {
    int stack_array; // Static allocation on the stack.
    // Memory is freed automatically when myFunction() ends.
}

```

### Dynamic Memory Allocation

(Note: The definition was corrected from the initial notes.)

- **When**: Memory is allocated at ==run time==.
    
- **How**: Requested explicitly by the programmer using the new keyword.
    
- **Lifetime**: Can exist **beyond the scope** in which it was created. It persists until it is explicitly deallocated with delete or delete[].
    
- **Management**: Must be done ==manually== by the programmer.
    

````
```cpp
void myFunction() {
    int stack_array; // Static allocation on the stack.
    // Memory is freed automatically when myFunction() ends.
}
````
  

---

## 💡 Review & Connections

> [!SUMMARY] Core Concepts at a Glance  
> | Feature | Static Allocation (Stack) | Dynamic Allocation (Heap) |  
> | :--- | :--- | :--- |  
> | **Timing** | Compile-time | Run-time |  
> | **Control**| Automatic (by the compiler) | Manual (by the programmer) |  
> | **Keywords** | None (new/delete) | new, delete, delete[] |  
> | **Lifetime**| Tied to scope | Persists until manually deleted |  
> | **Speed** | Fast | Slower (OS involvement) |

### Memory Aid (Mnemonic)

- **S**tack -> **S**cope -> **S**peedy -> **S**tatic
    
- **H**eap -> **H**ave to manage it -> **H**efty (for large data)
    

> [!WARNING] Areas Requiring Clarification

What is "stack overflow"? It happens when the stack, which has a fixed size, runs out of space, often due to excessively large local variables or infinite recursion.

> What are smart pointers (std::unique_ptr, std::shared_ptr) and how do they help with dynamic memory management? This is a crucial modern C++ topic.

### Potential Exam Questions

1. Draw a diagram illustrating the state of the stack and heap after a specific function call involving both new and local variables.
    
2. What is the primary difference between delete and delete[]? What happens if you use the wrong one?
    
3. Explain two advantages of using stack allocation over heap allocation.
    
4. Define a "memory leak" and provide a simple code example that causes one.
    

### Additional Resources

- **Video**: "Stack vs Heap Memory" by CodeBreakdown ([Link to a relevant YouTube search](https://www.google.com/url?sa=E&q=https://www.youtube.com/results?search_query=c%2B%2B+stack+vs+heap+memory+for+beginners))
    
- **Article**: "RAII (Resource Acquisition Is Initialization)" - A core C++ principle for managing resources like dynamic memory. Researching this will introduce you to modern C++ best practices.
