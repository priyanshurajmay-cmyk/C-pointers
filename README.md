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

---

## Operations on Pointers in C++

Pointers support **arithmetic operations** such as increment, decrement, and addition. These operations move the pointer to the next or previous memory location based on the data type size.

```cpp
int a[10], b;
int* c;

c = &a[0];   // c points to a[0]
c += 2;      // c points to a[2]
             // value of c increases by 2 * sizeof(int)
c++;         // c points to a[3]

b = *c++;    // value of a[3] copied to b, c points to a[4]
*c = 3;      // a[4] becomes 3
(*c)++;      // a[4] is incremented
```

### Explanation:

* Pointer arithmetic moves the pointer by multiples of the data type size.
* `*c++` accesses the value first, then increments the pointer.
* `(*c)++` increments the value stored at the location pointed to by `c`.

**Key Point:**
Pointer operations are commonly used while working with arrays.

---


## Q 1 Write a C++ program that:

Declares one global variable

Declares one local variable inside main()

Dynamically allocates one integer using new
Print the addresses of all three and identify which memory region each belongs to.
```cpp
#include <iostream>
using namespace std;

// Global variable
int g = 10;

int main()
{
    // Local variable
    int l = 20;

    // Dynamic variable
    int* d = new int;
    *d = 30;

    cout << "Global variable address: " << &g << endl;
    cout << "Local variable address: " << &l << endl;
    cout << "Dynamic variable address: " << d << endl;

    delete d;   // free memory
    return 0;
}
```

output:

<img width="427" height="218" alt="image" src="https://github.com/user-attachments/assets/4a500d22-e889-4b57-bf03-b8a927f1bb46" />

## Q2
Write a function square(int) and call it:

Normally

Using a function pointer

```cpp
#include <iostream>
using namespace std;

// Function to find square
int square(int x)
{
    return x * x;
}

int main()
{
    int n = 5;

    // Normal function call
    cout << "Square (normal call): " << square(n) << endl;

    // Function pointer call
    int (*fp)(int);
    fp = square;

    cout << "Square (function pointer): " << fp(n) << endl;

    return 0;
}
```

Output:

<img width="614" height="179" alt="image" src="https://github.com/user-attachments/assets/ce08d72d-4b81-4e96-9416-92bd038ee507" />


# C + +
1. write a c ++ program to read and display elements of an array.

```c++
#include <iostream>
using namespace std;

int main() {
    int n;

    // Read number of elements
    cout << "Enter the number of elements: ";
    cin >> n;

    int arr[n];

    // Read array elements
    cout << "Enter " << n << " elements:\n";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    // Display array elements
    cout << "The elements of the array are:\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

2. write a c ++ program to find the sum of all elements in an array.

```c++
#include <iostream>
using namespace std;

int main() {
    int n, sum = 0;

    // Read number of elements
    cout << "Enter the number of elements: ";
    cin >> n;

    int arr[n];

    // Read array elements
    cout << "Enter " << n << " elements:\n";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        sum += arr[i];   // Add each element to sum
    }

    // Display sum
    cout << "Sum of all elements in the array = " << sum;

    return 0;
}
```
3. write a c ++ program to copy one array into another

```c++
#include <iostream>
using namespace std;

int main() {
    int n;

    // Read number of elements
    cout << "Enter the number of elements: ";
    cin >> n;

    int arr1[n], arr2[n];

    // Read elements of first array
    cout << "Enter elements of the first array:\n";
    for (int i = 0; i < n; i++) {
        cin >> arr1[i];
    }

    // Copy elements from arr1 to arr2
    for (int i = 0; i < n; i++) {
        arr2[i] = arr1[i];
    }

    // Display copied array
    cout << "Elements of the second array are:\n";
    for (int i = 0; i < n; i++) {
        cout << arr2[i] << " ";
    }

    return 0;
}
```

4. write a c ++ program to print array elements at even index positions

```
#include <iostream>
using namespace std;

int main() {
    int n;

    // Read number of elements
    cout << "Enter the number of elements: ";
    cin >> n;

    int arr[n];

    // Read array elements
    cout << "Enter " << n << " elements:\n";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    // Print elements at even index positions
    cout << "Elements at even index positions:\n";
    for (int i = 0; i < n; i++) {
        if (i % 2 == 0) {
            cout << arr[i] << " ";
        }
    }

    return 0;
}
```

5. write a c ++ program to read and display a 2D array (matrix)

```
#include <iostream>
using namespace std;

int main() {
    int rows, cols;

    // Read number of rows and columns
    cout << "Enter number of rows: ";
    cin >> rows;
    cout << "Enter number of columns: ";
    cin >> cols;

    int matrix[rows][cols];

    // Read matrix elements
    cout << "Enter the elements of the matrix:\n";
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cin >> matrix[i][j];
        }
    }

    // Display matrix elements
    cout << "The matrix is:\n";
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
