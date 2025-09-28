# Pointers And Arrays
- For an array *a*  `a[0]` is equivalent to `*a` or `*(&a[0])`
- Array name as pointer.
-  Pointer arithmetic
	- if we increment a pointer by 1 it increases value by the size of pointer such as going addition 4 increment to `a[1]`.

## Dynamic Arrays
- Count of array element can be specified at run time
- Uses new 
- Uses delete[]
	- Important is to remember the `[]` with delete
- How array declared in stack differ from array declared in heap?

# Generic Programming
## Function Template
### Overloading
- Creating Different overloaded function for comparing stings, integers and string
~~~
int max(const int&a , const int& b)
{
	return (a>b) ? a: b;
}

double max(const double&a , const double& b)
{
	return (a>b) ? a: b;
}

~~~
### Template
- Kinda reminds me of Java Generics
```
template <typename T>
T Max( const T& a , const T& b ){
	return(a>b)? a:b;
}
```
## Class Template
### Class Declaration
-  `.h ` file
### Member Functions' Definition
- `.cpp` file

### Using Template Class
-  Umm why do we need another cpp file in our project.
	```
	A.cpp
	A_impl.cpp
	```
# Standard Template Library(STL)
Some of the most used are 
These can be used for many other types.
- Vector
- deque
- list
These three can increase their size.

# Recursion
Functions calling themseleves.
- In future the data structures and algorithms we will learn are also recursive like linear search, length of a string
