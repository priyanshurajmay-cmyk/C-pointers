# C-pointers

---

## What is a Pointer in C++?

A **pointer** is a variable that **stores the memory address** of another variable instead of storing the actual value.

```cpp
int x = 10;
int* p = &x;
```

* `x` → normal integer variable
* `&x` → address of `x`
* `p` → pointer that stores the address of `x`

---

## Declaring a Pointer

```cpp
data_type* pointer_name;
```

Example:

```cpp
int* ptr;
float* fptr;
```

The `*` tells the compiler that the variable is a pointer.

---

## Address-of (`&`) Operator

Used to **get the address** of a variable.

```cpp
int a = 5;
int* p = &a;
```

---

## Dereference (`*`) Operator

Used to **access or modify the value** stored at the address a pointer is pointing to.

```cpp
cout << *p;   // prints 5
*p = 10;      // changes value of a to 10
```

---

## Pointer and Function (Basic Idea)

Pointers allow functions to modify original variables.

```cpp
void update(int* p) {
    *p = 20;
}
```

---

## Null Pointer

A pointer that points to nothing.

```cpp
int* p = NULL;   // or nullptr (preferred in modern C++)
```

Prevents accidental access to invalid memory.


---

## Array of Pointers in C++

An **array of pointers** is an array in which each element stores the **address of a variable**.

```cpp
int* a[3];
int b = 5, c = 99, d = 17;

a[0] = &b;
a[1] = &c;
a[2] = &d;
```

Here, `a` is an array of three integer pointers. Each element of `a` points to a different integer variable. The values can be accessed using dereferencing: `*a[0]`, `*a[1]`, and `*a[2]`.

**Key Point:**
`int* a[3]` means an array of pointers to integers.


---

## Pointer to a Function in C++

A **function pointer** stores the **address of a function** and is used to call the function indirectly.

```cpp
void func(float)
{
    ...
}

void (*a)(float);
a = func;

(*a)(1.2);  // causes function call
a(1.2);     // causes function call
```

Here, `a` is a pointer to a function that takes a `float` argument and returns `void`. The function can be called using either `(*a)(1.2)` or `a(1.2)`.

**Key Point:**
Function pointers allow functions to be passed as arguments and used for callbacks.







