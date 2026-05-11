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

---

# C++ Structures and Pointer Programs

---

# 1. Structure: Student Records

## Program

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Student {
    int roll;
    string name;
    float marks;
};

int main() {
    Student s[5];

    for (int i = 0; i < 5; i++) {
        cout << "\nEnter details of student " << i + 1 << endl;
        cout << "Roll Number: ";
        cin >> s[i].roll;

        cout << "Name: ";
        cin >> s[i].name;

        cout << "Marks: ";
        cin >> s[i].marks;
    }

    cout << "\nStudents who scored more than 75 marks:\n";
    for (int i = 0; i < 5; i++) {
        if (s[i].marks > 75) {
            cout << "\nRoll Number: " << s[i].roll;
            cout << "\nName: " << s[i].name;
            cout << "\nMarks: " << s[i].marks << endl;
        }
    }

    return 0;
}
```

## Input

```
1 Aman 82
2 Riya 68
3 Karan 90
4 Neha 74
5 Rohit 78
```

## Output

```
Students who scored more than 75 marks:
Aman
Karan
Rohit
```

---

# 2. Structure: Employee Salary Calculation

## Program

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Employee {
    int emp_id;
    string name;
    float basic_salary;
};

int main() {
    Employee e;
    float hra, da, gross_salary;

    cout << "Enter Employee ID: ";
    cin >> e.emp_id;

    cout << "Enter Employee Name: ";
    cin >> e.name;

    cout << "Enter Basic Salary: ";
    cin >> e.basic_salary;

    hra = 0.20 * e.basic_salary;
    da  = 0.10 * e.basic_salary;
    gross_salary = e.basic_salary + hra + da;

    cout << "\nGross Salary: " << gross_salary;
    return 0;
}
```

---

# 3. Pointer Output Questions

## Example 1

```cpp
int arr[] = {10, 20, 30, 40};
int* p = arr;

cout << *p << endl;
cout << *(p + 1) << endl;
cout << *(p + 3) << endl;
```

### Output

```
10
20
40
```

### Explanation

* `p` points to first element
* `p+1` moves to next element
* `p+3` moves to fourth element

---

## Example 2

```cpp
int arr[] = {5, 10, 15, 20};
int* p = arr + 2;

cout << *p << endl;
cout << *(p - 1) << endl;
```

### Output

```
15
10
```

### Explanation

* `arr + 2` points to third element
* `p - 1` moves one step back

---

## Example 3

```cpp
int arr[] = {1, 2, 3};
int* p = arr;

for (int i = 0; i < 3; i++) {
    cout << *(p++) << " ";
}
```

### Output

```
1 2 3
```

### Explanation

Post-increment prints first, then moves pointer.

---

## Example 4

```cpp
char arr[] = {'A','B','C'};
char* p = arr;

cout << p << endl;
```

### Explanation

Printing a `char*` treats it as a string and continues until `'\0'`.

---

## Example 5

```cpp
int arr[] = {3,6,9,12};
int* p = arr;

while (p <= &arr[3]) {
    cout << *p << " ";
    p++;
}
```

### Output

```
3 6 9 12
```

---

## Example 6

```cpp
int arr[] = {7,14,21};

cout << arr[1] << endl;
cout << 1[arr] << endl;
```

### Output

```
14
14
```

### Explanation

`a[b] == b[a]`

---

# 4. Structure Output Questions

## Example 1

```cpp
struct Data {
    int x;
    int y;
};

Data arr[] = {{1,2}, {3,4}, {5,6}};
Data* p = arr;

cout << p->x << endl;
cout << (p + 1)->y << endl;
```

### Output

```
1
4
```

---

## Example 2

```cpp
struct Item {
    int price;
};

Item arr[] = {{1}, {3}, {5}};
Item* p = arr;

cout << p[2].price << endl;
cout << (*(p + 1)).price << endl;
```

### Output

```
5
3
```

---

# How to Compile

```
g++ program.cpp -o program
./program
```

---




# 1. Difference Between Binary Files and Text Files in C++

| Feature         | Text File                          | Binary File                |
| --------------- | ---------------------------------- | -------------------------- |
| Storage Format  | Stores data as readable characters | Stores data in binary form |
| Human Readable  | Yes                                | No                         |
| Size            | Larger                             | Smaller                    |
| Speed           | Slower                             | Faster                     |
| Data Conversion | Automatic conversion to text       | No conversion              |
| Example         | `.txt`                             | `.dat`, `.bin`             |

---

# 2. Polymorphism in C++

Polymorphism means **one function or object behaving in different ways**.

## Types of Polymorphism

### Compile-Time Polymorphism

Achieved using:

* Function Overloading
* Operator Overloading

Example:

```cpp
class Demo {
public:
    void show(int a) {
        cout << a;
    }

    void show(double b) {
        cout << b;
    }
};
```

### Run-Time Polymorphism

Achieved using:

* Virtual Functions
* Function Overriding

Example:

```cpp
class Base {
public:
    virtual void display() {
        cout << "Base";
    }
};

class Derived : public Base {
public:
    void display() override {
        cout << "Derived";
    }
};
```

## Difference

| Compile-Time               | Run-Time                 |
| -------------------------- | ------------------------ |
| Decided during compilation | Decided during execution |
| Faster                     | Slightly slower          |
| Uses overloading           | Uses virtual functions   |

---

# 3. Why Stack is Preferable to Array Sometimes

* Stack follows **LIFO** order.
* Easy insertion/deletion using `push()` and `pop()`.
* Better for:

  * Function calls
  * Undo operations
  * Expression evaluation
* Prevents random access mistakes.

---

# 4. Swap Two Numbers Using Function

```cpp
#include <iostream>
using namespace std;

void swapNumbers(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x = 10, y = 20;

    cout << "Before Swap: " << x << " " << y << endl;

    swapNumbers(x, y);

    cout << "After Swap: " << x << " " << y;

    return 0;
}
```

---

# 5. Write Data into a File

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream file("data.txt");

    file << "Hello File Handling";

    file.close();

    cout << "Data written successfully";

    return 0;
}
```

---

# 6. Read Data from a File

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ifstream file("data.txt");

    string data;

    getline(file, data);

    cout << data;

    file.close();

    return 0;
}
```

---

# 7. Pointer Declaration, Initialization, and Dereferencing

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;

    int *p = &a;

    cout << "Address: " << p << endl;
    cout << "Value: " << *p;

    return 0;
}
```

---

# 8. Access Array Elements Using Pointer Arithmetic

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {10, 20, 30, 40};

    int *p = arr;

    for(int i = 0; i < 4; i++) {
        cout << *(p + i) << endl;
    }

    return 0;
}
```

---

# 9. Difference Between Pointer and Reference

| Pointer                | Reference               |
| ---------------------- | ----------------------- |
| Stores address         | Alias of variable       |
| Can be NULL            | Cannot be NULL          |
| Requires dereferencing | No dereferencing        |
| Can change target      | Cannot change reference |

Example:

```cpp
int a = 10;

int *p = &a;
int &r = a;
```

---

# 10. BankAccount Class

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    double balance;

public:
    BankAccount() {
        balance = 0;
    }

    void deposit(double amount) {
        balance += amount;
    }

    void withdraw(double amount) {
        if(amount <= balance)
            balance -= amount;
        else
            cout << "Insufficient Balance\n";
    }

    void displayBalance() {
        cout << "Balance: " << balance << endl;
    }
};

int main() {
    BankAccount b;

    b.deposit(5000);
    b.withdraw(2000);
    b.displayBalance();

    return 0;
}
```

---

# 11. Difference Between Method Hiding and Overriding

## Method Hiding

Base function hidden due to same function name.

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    void show() {
        cout << "Base";
    }
};

class Derived : public Base {
public:
    void show(int x) {
        cout << "Derived";
    }
};
```

## Method Overriding

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {
        cout << "Base";
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived";
    }
};
```

---

# 12. Count Characters, Words, and Lines in File

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ifstream file("data.txt");

    string line;
    int chars = 0, words = 0, lines = 0;

    while(getline(file, line)) {
        lines++;
        chars += line.length();

        for(char c : line) {
            if(c == ' ')
                words++;
        }

        words++;
    }

    cout << "Lines: " << lines << endl;
    cout << "Words: " << words << endl;
    cout << "Characters: " << chars << endl;

    file.close();

    return 0;
}
```

---

# 13. Copy Contents of One File to Another

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ifstream source("source.txt");
    ofstream dest("dest.txt");

    string line;

    while(getline(source, line)) {
        dest << line << endl;
    }

    source.close();
    dest.close();

    cout << "File copied";

    return 0;
}
```

---

# 14. Append Data into Existing File

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream file("data.txt", ios::app);

    file << "\nNew Data Added";

    file.close();

    return 0;
}
```

---

# 15. Store Student Records in File

```cpp
#include <iostream>
#include <fstream>
using namespace std;

class Student {
public:
    int roll;
    string name;

    void input() {
        cin >> roll >> name;
    }

    void display() {
        cout << roll << " " << name;
    }
};

int main() {
    Student s;

    ofstream file("student.txt");

    s.input();

    file << s.roll << " " << s.name;

    file.close();

    ifstream read("student.txt");

    read >> s.roll >> s.name;

    s.display();

    read.close();

    return 0;
}
```

---

# 16. Stack Using Array

```cpp
#include <iostream>
using namespace std;

class Stack {
    int arr[5];
    int top;

public:
    Stack() {
        top = -1;
    }

    void push(int x) {
        if(top == 4)
            cout << "Overflow\n";
        else
            arr[++top] = x;
    }

    void pop() {
        if(top == -1)
            cout << "Underflow\n";
        else
            top--;
    }

    void display() {
        for(int i = top; i >= 0; i--)
            cout << arr[i] << " ";
    }
};

int main() {
    Stack s;

    s.push(10);
    s.push(20);

    s.display();

    return 0;
}
```

---

# 17. Queue Using Array

```cpp
#include <iostream>
using namespace std;

class Queue {
    int arr[5];
    int front, rear;

public:
    Queue() {
        front = rear = -1;
    }

    void enqueue(int x) {
        if(rear == 4)
            cout << "Overflow\n";
        else {
            if(front == -1)
                front = 0;

            arr[++rear] = x;
        }
    }

    void dequeue() {
        if(front == -1 || front > rear)
            cout << "Underflow\n";
        else
            front++;
    }

    void display() {
        for(int i = front; i <= rear; i++)
            cout << arr[i] << " ";
    }
};

int main() {
    Queue q;

    q.enqueue(10);
    q.enqueue(20);

    q.display();

    return 0;
}
```

---

# 18. Find the Error

```cpp
int *p;
*p = 10;
```

## Error

`p` is uninitialized and points to garbage memory.

## Correct Code

```cpp
int x;
int *p = &x;
*p = 10;
```

---

# 19. Find the Error

```cpp
int *a = new int[10];
delete a;
```

## Error

Array allocated with `new[]` must be deleted using `delete[]`.

## Correct Code

```cpp
delete[] a;
```

---

# 20. Predict Output

```cpp
int a = 5;
int *p = &a;
cout << *p << " " << a;
```

## Output

```cpp
5 5
```

---

# 21. Predict Output

```cpp
int a[5] = {10,20,30,40,50};
int *p = a;
cout << *(p+3);
```

## Output

```cpp
40
```

---

# 22. Predict Output

```cpp
class A {
public:
    A() { cout << "A"; }
    ~A() { cout << "B"; }
};

int main() {
    A x;
}
```

## Output

```cpp
AB
```

Constructor executes first, destructor executes when object goes out of scope.

---

# 23. Why Destructors Are Important

Destructors:

* Release dynamically allocated memory
* Close files
* Prevent memory leaks
* Free system resources automatically

Example:

```cpp
~FileHandler() {
    file.close();
}
```

---

# 24. Why Pointers Are Important for Linked Lists

Pointers:

* Connect nodes dynamically
* Enable dynamic memory allocation
* Allow flexible data structures
* Avoid fixed size limitations

Without pointers, linked lists cannot exist.

---

# 25. Why Virtual Functions Are Needed

Virtual functions:

* Enable runtime polymorphism
* Improve flexibility and extensibility
* Allow base class pointers to call derived class methods

Essential in:

* GUI frameworks
* Game engines
* Plugin systems
* Large enterprise software

---

# Student Record System

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int roll;
    string name;
    float marks[3];

public:
    Student() {
        roll = 0;
        name = "Unknown";
    }

    Student(int r) {
        roll = r;
    }

    Student(int r, string n, float m[]) {
        roll = r;
        name = n;

        for(int i = 0; i < 3; i++)
            marks[i] = m[i];
    }

    ~Student() {
        cout << "Destructor Called\n";
    }

    void addStudent() {
        cout << "Enter Roll and Name: ";
        cin >> roll >> name;

        cout << "Enter 3 Marks: ";

        for(int i = 0; i < 3; i++)
            cin >> marks[i];
    }

    void modifyStudent() {
        cout << "Modify Name: ";
        cin >> name;
    }

    void displayStudent() {
        cout << "Roll: " << roll << endl;
        cout << "Name: " << name << endl;

        for(int i = 0; i < 3; i++)
            cout << marks[i] << " ";
    }

    void calculateAverage() {
        float sum = 0;

        for(int i = 0; i < 3; i++)
            sum += marks[i];

        cout << "\nAverage = " << sum / 3;
    }
};

int main() {
    Student s;

    s.addStudent();
    s.displayStudent();
    s.calculateAverage();

    return 0;
}
```

---

# Employee Salary Management System

```cpp
#include <iostream>
#include <fstream>
using namespace std;

class Employee {
private:
    int id;
    string name;
    float salary;

public:
    void input() {
        cin >> id >> name >> salary;
    }

    void calculateSalary() {
        salary += salary * 0.10;
    }

    void display() {
        cout << id << " " << name << " " << salary << endl;
    }

    void saveToFile(ofstream &file) {
        file << id << " " << name << " " << salary << endl;
    }

    void readFromFile(ifstream &file) {
        file >> id >> name >> salary;
    }
};

int main() {
    Employee e;

    ofstream out("employee.txt");

    e.input();

    e.calculateSalary();

    e.saveToFile(out);

    out.close();

    ifstream in("employee.txt");

    e.readFromFile(in);

    e.display();

    in.close();

    return 0;
}
```

---

# Tic-Tac-Toe Game

```cpp
#include <iostream>
using namespace std;

class Game {
private:
    char board[3][3];
    char turn;

public:
    Game() {
        resetGame();
        turn = 'X';
    }

    void resetGame() {
        for(int i = 0; i < 3; i++) {
            for(int j = 0; j < 3; j++) {
                board[i][j] = '-';
            }
        }
    }

    void printBoard() {
        for(int i = 0; i < 3; i++) {
            for(int j = 0; j < 3; j++) {
                cout << board[i][j] << " ";
            }
            cout << endl;
        }
    }

    void makeMove(int row, int col) {
        if(board[row][col] == '-') {
            board[row][col] = turn;

            turn = (turn == 'X') ? 'O' : 'X';
        }
        else {
            cout << "Invalid Move\n";
        }
    }

    bool checkWinner() {
        for(int i = 0; i < 3; i++) {
            if(board[i][0] == board[i][1] &&
               board[i][1] == board[i][2] &&
               board[i][0] != '-')
                return true;
        }

        return false;
    }
};

int main() {
    Game g;

    g.printBoard();

    g.makeMove(0,0);
    g.makeMove(1,1);

    g.printBoard();

    return 0;
}
```

