# **C++ A Practical Approach**

This approach is designed to teach **C++ programming** through hands-on exercises. Each chapter introduces **fundamental concepts**, followed by **exercises** to reinforce learning.

</p>
<p align="center">
<img src="https://github.com/ablaamim/C-PRACTICAL-APPROACH/blob/main/imgs/marvin.jpg" width="500">
</p>

---

# **Chapter 1  Understanding the C++ Compilation Process**
## **Introduction**
Before writing C++ programs, it's crucial to understand how they are **compiled and executed**. The compilation process transforms **human-readable C++ code** into **machine-executable binary files**.  

In this chapter, we will explore:
- **The compilation steps in C++**.
- **How the preprocessor works**.
- **Using macros to control compilation**.
- **Practical exercises to reinforce these concepts**.

---

## **1.1 The C++ Compilation Process**
When you compile a C++ program, it undergoes **four main stages**:

### **Step 1  Preprocessing (`.cpp → .i`)**
- The **preprocessor** expands macros, includes header files, and removes comments.
- Directives like `#include`, `#define`, and `#ifdef` are processed.
- The output is a preprocessed file (`.i`).

### **Step 2  Compilation (`.i → .s`)**
- The compiler converts the **preprocessed code** into **assembly language**.
- It also checks for **syntax errors**.

### **Step 3  Assembly (`.s → .o/.obj`)**
- The assembler translates **assembly code** into **machine code**.
- Produces an **object file** (`.o` on Linux/macOS, `.obj` on Windows).

### **Step 4  Linking (`.o → Executable`)**
- Combines object files and **external libraries** to create an **executable program**.
- Resolves function references from libraries (like the **C++ Standard Library**).

---

</p>
<p align="center">
<img src="https://github.com/ablaamim/C-PRACTICAL-APPROACH/blob/main/imgs/GCC_CompilationProcess.png" width="500">
</p>

---


## **1.2 Compilation Example Using `g++`**
Let's consider a simple C++ program **(`main.cpp`)**:

```cpp
#include <iostream>
#define GOLDEN_RATIO 1.61

int main()
{
    std::cout << "Golden Ratio value: " << GOLDEN_RATIO << std::endl;
    return (0);
}
```

## Step-by-Step Compilation Commands

1. Preprocessing (-E option)
```
g++ -E main.cpp -o main.i
```

* Expands macros (GOLDEN_RATIO is replaced with 1.61).

* Includes the full content of <iostream>.

* Produces the preprocessed file main.i.

## Compilation to Assembly (-S option)
```
g++ -S main.i -o main.s
```
* Converts the preprocessed C++ code into assembly instructions.
* Produces main.s.

3. Assembly to Machine Code (-c option)
```
g++ -c main.s -o main.o
```
* Translates assembly into binary machine code.
* Produces main.o.

4. Linking to Create Executable
```
g++ main.o -o main
```

* Produces the final executable file: main.

5. Running the Program
```
./main
```
Output:

```
GOLDEN RATIO value: 1.61
```

## Preprocessor Macros and Examples

Preprocessor macros are handled before compilation during the preprocessing stage.

1. Object-like Macro (#define)

```C
#define GOLDEN_RATIO 1.61
std::cout << "Value of Golden Ratio: " << GOLDEN_RATIO << std::endl;
GOLDEN_RATIO is replaced with 1.61 before compilation.
```

2. Function-like Macro

```C
#define SQUARE(x) ((x) * (x))
std::cout << "Square of 5: " << SQUARE(5) << std::endl; // Expands to (5 * 5)
```
3. Conditional Compilation (#ifdef, #ifndef)
```C
#define DEBUG
#ifdef DEBUG
    std::cout << "Debugging mode enabled!" << std::endl;
#endif
```

If DEBUG is defined, the message is printed.

4. Header Guard (#ifndef, #define, #endif)

Used to prevent multiple inclusions of a header file:

```C
#ifndef MY_HEADER_H
#define MY_HEADER_H

void myFunction();

#endif // MY_HEADER_H
```

## Examples

### Example 1 : Understanding the Preprocessor

> Write a program that:
Defines a constant PI = 3.14159 using #define.
Defines a macro function SQUARE(x) that squares a number.
Prints SQUARE(4) and the value of PI.

```C
#include <iostream>
#define PI 3.14159
#define SQUARE(x) ((x) * (x))

int main() {
    std::cout << "Pi value: " << PI << std::endl;
    std::cout << "Square of 4: " << SQUARE(4) << std::endl;
    return 0;
}
```

Expected Output:

```
Pi value: 3.14159
Square of 4: 16
```

### Example 2: Debug Mode with Macros

> Write a program that:
Uses a #define DEBUG macro.
If DEBUG is defined, prints "Debug mode enabled!".
```C
#include <iostream>
#define DEBUG

int main() {
#ifdef DEBUG
    std::cout << "Debug mode enabled!" << std::endl;
#endif
    return 0;
}
```

Compile with and without the DEBUG macro:

```
g++ -DDEBUG main.cpp -o main
./main
```

### Example 3: Understanding Compilation Steps

> Write a simple C++ program.
Compile it step by step:
Preprocess using:

```
g++ -E main.cpp -o main.i
```

Compile to assembly using:

```
g++ -S main.i -o main.s
```

Assemble to object file using:

```
g++ -c main.s -o main.o
```

Link to produce the final executable:

```
g++ main.o -o main
```

Print each generated file to observe the differences.

### Example 4 : using header Guards

Create a header file myHeader.hpp:

```C
#ifndef MYHEADER_HPP
#define MYHEADER_HPP

void sayHello();

#endif
```

Create an implementation file myHeader.cpp:

```C
#include <iostream>
#include "myHeader.hpp"

void sayHello() {
    std::cout << "Hello from the header file!" << std::endl;
}

```

Create a main.cpp file:

```C
#include "myHeader.hpp"

int main() {
    sayHello();
    return 0;
}
```
Compile and run:

```
g++ myHeader.cpp main.cpp -o main
./main
```

Expected Output:

```
Hello from the header file!
```