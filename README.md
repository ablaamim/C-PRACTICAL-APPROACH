# **C++ A Practical Approach**

This approach is designed to teach **C++ programming** through hands-on exercises. Each chapter introduces **fundamental concepts**, followed by **exercises** to reinforce learning.

</p>
<p align="center">
<img src="https://github.com/ablaamim/C-PRACTICAL-APPROACH/blob/main/imgs/marvin.jpg" width="500">
</p>

---

## Introduction :

### **Welcome to C++ The Language That Loves You Back (Sort of)**

## **Preamble: The Wild World of C++**

Ah, **C++**. The language that’s been around since the dinosaurs (a.k.a. the 1980s). It’s the **cool uncle of programming languages**—a little complex, sometimes strict, but **extremely powerful** once you get to know it.  

### **Why Learn C++?**
1. **You love pain.**  
   - Memory management? Pointers? Segmentation faults? Sounds fun!  
2. **You want control.**  
   - Python may let you chill, but **C++ makes you the architect** of your own digital empire.  
3. **You enjoy debugging for hours.**  
   - C++ will **test your patience**, but the reward is ultimate power.  
4. **It’s everywhere!**  
   - Games? ✅  
   - Operating Systems? ✅  
   - Banking systems? ✅  
   - NASA? 🚀✅  

### **C++ vs. Other Languages**
| Language  | Why It's Cool | Why It's Not C++ |
|-----------|--------------|------------------|
| Python    | Easy to learn, fewer bugs | Slower, no manual memory control |
| Java      | Cross-platform, garbage collection | Verbose, not as fast as C++ |
| JavaScript | Great for web apps | Not even remotely C++ |
| Assembly  | Super fast, ultimate control | You might lose your sanity |

So buckle up! Learning C++ is like training a dragon. Once you tame it, you can **conquer kingdoms** (or at least impress your nerdy friends).

---

Congratulations! You now know the **basics of C++** (or at least, you're pretending you do). But let’s talk about something **far more important**—**why are there no baby pigeons?**  

Seriously, have you ever seen a baby pigeon? No? **Exactly.** They exist, but for some reason, we only ever see the full-grown ones. Perhaps they **hide in secret government labs** until they’re fully developed. Perhaps they **teleport into existence** as full-sized pigeons.  

One thing is for sure: **learning C++ is easier than finding a baby pigeon.**  

Now, let’s get back to **conquering C++**—one **segmentation fault** at a time. 🚀🔥

</p>
<p align="center">
<img src="https://github.com/ablaamim/C-PRACTICAL-APPROACH/blob/main/imgs/funny-programming-memes-february-11-2024-5.png" width="500">
</p>

> Learning curve for normal and mentally challenged people.

---

## **File Descriptors and Their Relation to `cin`, `cout`, and `cerr`**

## **What Are File Descriptors?**
A **file descriptor** is a **non-negative integer** that the **operating system** uses to **reference an open file** (or another I/O resource like a socket or pipe). They serve as **handles** by which programs can **read from** or **write to** these resources.

### **Common File Descriptors in Unix-Like Systems**
| **File Descriptor** | **Purpose**                |
|---------------------|----------------------------|
| **0**               | **Standard Input**         |
| **1**               | **Standard Output**        |
| **2**               | **Standard Error Output**  |

---

</p>
<p align="center">
<img src="https://www.computerhope.com/jargon/f/file-descriptor-illustration.png" width="400">
</p>

---

## **Standard Streams in C++**
In **C++**, we have three **standard streams** that are **closely tied** to these file descriptors:

1. **`std::cin` (Standard Input Stream)**  
   - Corresponds to **file descriptor `0`**.  
   - Used to **read input** from the user (often via keyboard).

2. **`std::cout` (Standard Output Stream)**  
   - Corresponds to **file descriptor `1`**.  
   - Used to **write output** to the screen (or another output device).

3. **`std::cerr` (Standard Error Stream)**  
   - Corresponds to **file descriptor `2`**.  
   - Used to **write error messages**, ensuring they appear **immediately** (often unbuffered).

---

## **How They Work Together**
- **File descriptors** are the **lowest-level** constructs handled by the **operating system**.  
- **C++ streams** (`cin`, `cout`, `cerr`) are **high-level abstractions** that provide **buffered I/O** and **type-safe operations** on top of those file descriptors.

### **Example:**
```cpp
#include <iostream>

int main() {
    std::string name;
    
    // Reading from standard input (file descriptor 0)
    std::cin >> name;
    
    // Writing to standard output (file descriptor 1)
    std::cout << "Hello, " << name << "!" << std::endl;
    
    // Writing to standard error (file descriptor 2)
    std::cerr << "This is an error message." << std::endl;

    return 0;
}

---

## Understanding the C++ Compilation Process**
### **Introduction**
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

# **Why Use `-std=c++17` When Compiling C++?**
When compiling a C++ program with `g++`, the flag `-std=c++17` **specifies the C++ standard version**. It tells the compiler to use the **C++17 standard**, which provides **improvements and new features** over older versions like **C++11** and **C++14**.

---

## **1️⃣ Why Not Use Older Standards?**
Some **older C++ standards** are still used, but they **lack modern features** and may cause **performance or safety issues**.  

| **Standard**  | **Why You Shouldn't Use It** |
|--------------|------------------------------|
| **C++98**    | No smart pointers, lacks modern features, verbose. |
| **C++03**    | Just minor fixes, still lacks C++11 features. |
| **C++11**    | Introduced great features, but lacks structured bindings and `if constexpr`. |
| **C++14**    | Small improvements, but no `std::filesystem` or `std::optional`. |
| **C++17**    | ✅ **Balanced, widely supported, modern, and stable**. |

---

## Step-by-Step Compilation Commands

1. Preprocessing (-E option)
```
g++ -E -std=c++17 main.cpp -o main.i
```

* Expands macros (GOLDEN_RATIO is replaced with 1.61).

* Includes the full content of <iostream>.

* Produces the preprocessed file main.i.

## Compilation to Assembly (-S option)
```
g++ -S -std=c++17 main.i -o main.s
```
* Converts the preprocessed C++ code into assembly instructions.
* Produces main.s.

3. Assembly to Machine Code (-c option)
```
g++ -c -std=c++17 main.s -o main.o
```
* Translates assembly into binary machine code.
* Produces main.o.

4. Linking to Create Executable
```
g++ -std=c++17 main.o -o main
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

incredible C++ history fact: Bjarne Stroustrup was inspired by his own legs when he wrote the C++ compiler error.

</p>
<p align="center">
<img src="https://github.com/ablaamim/C-PRACTICAL-APPROACH/blob/main/imgs/Evhzp8NXUAI1WQI.jpg" width="500">
</p>

## Examples

### Example 1 : Understanding the Preprocessor

> Write a program that:
Defines a constant PI = 3.14159 using #define.
Defines a macro function SQUARE(x) that squares a number.
Prints SQUARE(4) and the value of PI.

```cpp
#include <iostream>
#define PI 3.14159
#define SQUARE(x) ((x) * (x))

int main()
{
    std::cout << "Pi value: " << PI << std::endl;
    std::cout << "Square of 4: " << SQUARE(4) << std::endl;
    return (0);
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

int main()
{
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

### Example 3 : Understanding Compilation Steps

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

void sayHello()
{
    std::cout << "Hello from the header file!" << std::endl;
}

```

Create a main.cpp file:

```C
#include "myHeader.hpp"

int main()
{
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

---

##  Understanding Namespaces

### **Definition:**

A **namespace** in C++ is used to **group logically related variables, functions, and classes** to avoid **name conflicts**.

- It prevents naming clashes in **large projects**.
- The **standard library (`std`)** is inside the `std` namespace.
- You can create **custom namespaces**.

### **Example: Using a Custom Namespace**
```cpp
#include <iostream>

// Declare a custom namespace
namespace MyNamespace
{
    int x = 10;
    void display()
    {
        std::cout << "Value of x: " << x << std::endl;
    }
}

int main()
{
    // Accessing elements from MyNamespace
    MyNamespace::display();
    
    // Using 'using' to avoid repeating MyNamespace::
    using namespace MyNamespace;
    std::cout << "Value of x: " << x << std::endl;

    return (0);
}
```
Expected Output:

```
Value of x: 10
Value of x: 10
```
Key Points:

✅ Use namespace::member to access elements.

✅ Use using namespace <name> to avoid writing namespace:: repeatedly.

✅ Best practice: Avoid using namespace std; in large projects to prevent conflicts.

---
#  Compile-Time vs. Runtime Variables in C++
## **Introduction**
In C++, variables can either be determined **at compile-time** or **at runtime**. Understanding this distinction helps you write **optimized, efficient, and error-free** code.  

This chapter covers:
- The difference between **compile-time and runtime variables**.
- The use of **`const` and `constexpr`**.
- How to decide between **`const` and `constexpr`**.
- A practical example using an **addition function**.

---

## **2.1 Compile-Time vs. Runtime: What’s the Difference?**
When you declare a variable, its value is either **known before execution (compile-time)** or **determined while the program runs (runtime)**.

| **Feature**      | **Compile-Time**                     | **Runtime**                       |
|-----------------|---------------------------------|---------------------------------|
| **When evaluated?** | During program compilation | While the program is running |
| **Performance**  | Faster (resolved before execution) | Slightly slower (computed dynamically) |
| **Can depend on user input?** | ❌ No  | ✅ Yes |
| **Memory usage** | May not take space if optimized | Allocated in RAM during execution |
| **Modifiable?**  | ❌ No  | ✅ Yes |

### **Example: Compile-Time vs. Runtime Variables**
```cpp
#include <iostream>

constexpr int compileTimeVar = 10;  // Known at compile-time
int runtimeVar;  // Declared but assigned later

int main()
{
    runtimeVar = 20;  // Assigned during execution

    std::cout << "Compile-Time Value: " << compileTimeVar << std::endl;
    std::cout << "Runtime Value: " << runtimeVar << std::endl;

    return 0;
}

✅ compileTimeVar is evaluated at compile-time and cannot change.
✅ runtimeVar is determined at runtime, meaning its value can change.

## Understanding const Variables

A const variable is read-only, meaning its value cannot change after it has been initialized. However, it can be evaluated at runtime.

Example: Using const Variables
```cpp
#include <iostream>

int main()
{
    const int x = 5;  // Read-only variable
    std::cout << "x: " << x << std::endl;
    
    // x = 10;  // ❌ ERROR: Cannot modify a const variable

    return (0);
}
```
✅ Key Properties of const:

Can hold values known at runtime.
Stored in memory like regular variables.
Cannot be modified after initialization.

## Understanding constexpr Variables
A constexpr variable must be evaluated at compile-time. It cannot depend on runtime input.

Example: Using constexpr Variables

```cpp
#include <iostream>

constexpr int square(int x)
{
    return x * x;  // Computed at compile-time
}

int main()
{
    constexpr int result = square(5);  // ✅ Evaluated at compile-time
    std::cout << "Square of 5: " << result << std::endl;

    return 0;
}
```
✅ Key Properties of constexpr:

The value must be known at compile-time.
constexpr functions allow calculations at compile-time.
If used with runtime values, it fails to compile.

## When to Use `const` vs. `constexpr`**

| **Use Case**                                    | **Recommended Keyword** |
|-------------------------------------------------|------------------------|
| Immutable values that may change at runtime     | `const`               |
| Constants known at compile-time                 | `constexpr`           |
| Optimizing calculations at compile-time         | `constexpr`           |
| Function parameters that should not be modified | `const`               |
| Ensuring function execution happens at compile-time | `constexpr`     |


</p>
<p align="center">
<img src="https://us1.discourse-cdn.com/spiceworks/original/4X/f/7/5/f751776beea7ca000875724230a6bdb59d8e507c.gif" width="800">
</p>