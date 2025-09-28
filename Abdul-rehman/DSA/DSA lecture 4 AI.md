
---
creation_date: 2025-09-17
course: C++ Programming
lecture: 1
tags: [cpp, pointers, arrays, templates, generics, stl, recursion]
---

# Lecture Notes: Pointers, Generic Programming, and STL

This lecture covers fundamental but powerful C++ features: the deep relationship between pointers and arrays, the concept of generic programming using templates, and an introduction to the Standard Template Library (STL).

---

## 1. [[Pointers]] And [[Arrays]]

In C++, pointers and arrays are intimately related. Understanding this relationship is key to mastering many common C++ idioms.

- **Array Name as a Pointer**: The name of an array acts as a ==constant pointer== to the first element of that array.
- **Equivalence**: For an array `a`, the expression to access the first element, `a[0]`, is completely equivalent to dereferencing the pointer, `*a`.
    - `*a` is shorthand for `*(&a[0])`.

### Pointer Arithmetic

Pointer arithmetic is different from normal integer arithmetic. The compiler automatically scales the arithmetic by the size of the data type the pointer points to.

- **Incrementing a Pointer**: If you have a pointer `int* p = a;` and you execute `p++`, the address stored in `p` does not increase by 1 byte. Instead, it increases by `sizeof(int)` (usually 4 bytes), effectively making it point to the next element, `a[1]`.

> [!EXAMPLE] Pointer Arithmetic Visualization
> ```cpp
> int a[] = {10, 20, 30};
> int* ptr = a; // ptr points to a, address e.g., 0x1000
> 
> std::cout << *ptr; // Outputs 10
> 
> ptr++; // ptr now points to a, address is 0x1004 (not 0x1001)
> 
> std::cout << *ptr; // Outputs 20
> ```

### Dynamic Arrays

Dynamic arrays allow you to specify the number of elements at runtime, not just at compile time. They are allocated on the [[Heap Memory]].

- **Allocation**: Use the `new` keyword. `int* myArray = new int[count];`
- **Deallocation**: Use the `delete[]` keyword. `delete[] myArray;`

> [!WARNING] Critical Syntax: `delete[]`
> You **must** use the square brackets `[]` when deleting an array allocated with `new[]`.
> - `delete[] myArray;` ✅ Correctly deallocates the entire array.
> - `delete myArray;` ❌ **Incorrect.** This leads to a [[Memory Leak]] as it only deallocates the first element.

### Stack vs. Heap Array Allocation

> [!QUESTION] How does an array declared on the stack differ from an array declared on the heap?

This is a fundamental concept in C++ memory management.

| Feature | Stack-Allocated Array | Heap-Allocated (Dynamic) Array |
| :--- | :--- | :--- |
| **Allocation** | `int arr[10];` | `int* arr = new int[10];` |
| **Lifetime** | Memory is ==automatically== deallocated when the variable goes out of scope. | Memory persists until it is ==manually== deallocated with `delete[]`. |
| **Size** | Size must be a constant known at compile time. | Size can be determined at runtime. |
| **Memory Region**| Stored in [[Stack Memory]]. | Stored in [[Heap Memory]]. |
| **Speed** | Very fast allocation and deallocation. | Slower due to system calls for memory management. |
| **Risk** | Risk of "Stack Overflow" if the array is too large. | Risk of "Memory Leaks" if you forget to `delete[]`. |

> [!SUMMARY] Stack vs. Heap
> Use the **stack** for fixed-size, short-lived arrays where performance is critical. Use the **heap** for large arrays or when the size is not known until runtime, and remember to manage the memory yourself.

---

## 2. Generic Programming

Generic programming allows you to write flexible, reusable functions and classes that can work with any data type. This avoids code duplication.

> [!INFO] Connection to Java
> Your intuition is correct! C++ Templates are the direct counterpart to ==Java Generics==. They are both mechanisms for writing type-agnostic code.

### Function Templates

Instead of writing multiple overloaded functions for different types, you can write a single "template" for the function.

- **The Problem (Overloading)**: Code duplication for different data types.
    ```cpp
    // Function to find the maximum of two integers
    int max(const int& a, const int& b) {
        return (a > b) ? a : b;
    }

    // Overloaded function for doubles
    double max(const double& a, const double& b) {
        return (a > b) ? a : b;
    }
    ```

- **The Solution (Templates)**: A single, generic blueprint. The compiler generates the specific versions needed at compile time.
    ```cpp
    template <typename T>
    T max(const T& a, const T& b) {
        return (a > b) ? a : b;
    }
    ```
    - `template <typename T>` declares a template with a placeholder type `T`.
    - You can now call `max(5, 10);` or `max(3.14, 2.71);` using the same function.

### Class Templates

Just like with functions, you can create generic classes that can manage any data type.

- **Declaration (`.h` file)**: The blueprint of the class is declared in a header file.
    ```cpp
    // In Array.h
    template <typename T>
    class Array {
    private:
        T* data;
        int size;
    public:
        Array(int s);
        ~Array();
        // ... other member functions
    };
    ```
- **Definition (`.cpp` or `.tpp` file)**: The implementation of the member functions.

> [!QUESTION] Umm, why do we need another `.cpp` file in our project like `A_impl.cpp`?

This is a common and important point of confusion with templates.

The compiler needs to see the **full definition (the implementation) of a template** wherever it is used in order to generate the code for a specific type (e.g., to create an `Array<int>` or `Array<double>`).

- **The Problem**: If you put the template implementation in a separate `.cpp` file, the compiler won't see it when you `#include "A.h"` in another file (`main.cpp`). It only sees the declaration, which isn't enough to create the class. This will cause linker errors.
- **The Solution**: Template definitions are almost always placed in the header file (`.h`) itself, or in a file that is included by the header (often named `.tpp` or `_impl.cpp`). This ensures the full code is available wherever the template is needed.

---

## 3. Standard Template Library ([[STL]])

The [[STL]] is a powerful library in C++ that provides a collection of ready-to-use template classes and functions. It's a prime example of generic programming.

- **Containers**: Data structures that store collections of objects.
- Some of the most common sequence containers are:
    - `[[vector]]`: A dynamic array that can grow and shrink. Think of it like Java's `ArrayList`. Provides fast random access.
    - `[[deque]]`: "Double-ended queue". Similar to a vector but allows for efficient insertions and deletions at both the beginning and the end.
    - `[[list]]`: A doubly-linked list. Efficient for insertions and deletions anywhere in the list, but does not provide fast random access.

---

## 4. [[Recursion]]

Recursion is a problem-solving technique where a function calls itself to solve smaller instances of the same problem.

- **Core Concept**: A function calls itself, breaking a problem down until it reaches a simple **base case** that can be solved directly without further recursion.
- **Future Applications**: Recursion is the natural way to think about and implement many data structures and algorithms you will learn, including:
    - Tree and graph traversals
    - Sorting algorithms like Merge Sort and Quick Sort
    - Searching algorithms like Binary Search

---

## 🧠 Review & Connections

### Glossary
- **[[Memory Leak]]**: A memory management failure where heap-allocated memory is no longer needed but is not released, making it unusable.
- **[[Heap Memory]]**: A region of computer memory used for dynamic allocation.
- **[[Stack Memory]]**: A region of memory where local variables are stored. Memory is managed automatically in a LIFO (Last-In, First-Out) manner.
- **[[STL]]**: Standard Template Library. A core part of the C++ Standard Library containing generic containers, algorithms, and iterators.

### Main Takeaways
1.  An array's name is a pointer to its first element, and pointer arithmetic is scaled by the type's size.
2.  Dynamic arrays on the heap give runtime flexibility but require manual memory management with `new[]` and `delete[]`.
3.  Templates provide a powerful way to write generic, type-safe code, similar to Java Generics.
4.  Template definitions must typically be placed in header files for the compiler to see them.

### Potential Exam Questions
- What is the output of the following code snippet involving pointer arithmetic?
- Write a function template `swap` that takes two arguments of any type and swaps their values.
- What is a memory leak and how can you cause one when using dynamic arrays? How do you prevent it?
- Compare and contrast a `std::vector` and a `std::list` in terms of performance for insertion and random access.```