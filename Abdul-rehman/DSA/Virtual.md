Of course, here is a concise markdown note on the C++ `virtual` keyword.

# C++ `virtual` Keyword: A Concise Guide

The `virtual` keyword in C++ enables **runtime polymorphism** (also called dynamic binding or late binding). It allows a program to decide at runtime which function to call based on the actual type of an object, rather than the type of the pointer or reference used to access it.

---

### 1. `virtual` Functions

Declaring a member function `virtual` in a base class allows it to be overridden by derived classes. When called through a base class pointer, the overridden version in the derived object is executed.

-   **Without `virtual` (Static Binding):** The call is resolved at compile-time based on the pointer's type.
-   **With `virtual` (Dynamic Binding):** The call is resolved at runtime based on the object's actual type.

**Example:**
```cpp
class Base {
public:
    virtual void show() { std::cout << "Base\n"; }
};

class Derived : public Base {
public:
    void show() override { std::cout << "Derived\n"; } // 'override' is a safety check
};

Base* ptr = new Derived();
ptr->show(); // Prints "Derived" because show() is virtual
```

---

### 2. `virtual` Destructors

This is the most critical use of `virtual`. If you `delete` a derived object through a base class pointer, you **must** have a `virtual` destructor in the base class.

-   **Problem:** Without it, only the base destructor is called, leaking all resources from the derived class.
-   **Solution:** A `virtual` destructor ensures both derived and base destructors are called in the correct order.

**Rule of Thumb:** If a class is intended to be a base class, give it a `virtual` destructor.

```cpp
class Base {
public:
    virtual ~Base() {} // Correct!
};
```

---

### 3. Pure `virtual` Functions & Abstract Classes

A **pure `virtual` function** creates an interface, forcing derived classes to implement it. It is declared by adding `= 0`.

-   A class with at least one pure virtual function is an **abstract class**.
-   You cannot create an instance of an abstract class.

This is the C++ equivalent of Java's `abstract` methods and classes.

**Example:**
```cpp
// Abstract base class
class Shape {
public:
    virtual void draw() const = 0; // Pure virtual function
    virtual ~Shape() = default;
};

// Concrete class MUST implement draw()
class Circle : public Shape {
public:
    void draw() const override { /* ... */ }
};
```

---

### Quick Java Comparison

| C++ Feature            | Java Equivalent              |
| :--------------------- | :--------------------------- |
| `virtual` function     | Default method behavior      |
| `virtual` destructor   | Handled by Garbage Collector |
| Pure `virtual` (`= 0`) | `abstract` method            |
| Abstract Class         | `abstract` class             |
| `override` specifier   | `@Override` annotation       |
| Non-`virtual` method   | `final` method (roughly)     |

