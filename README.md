# **C++ - A Practical Approach**

This approach is designed to teach **C++ programming** through hands-on exercises. Each chapter introduces **fundamental concepts**, followed by **exercises** to reinforce learning.

</p>
<p align="center">
<img src="" width="500">
</p>

---

# **Chapter 1: Understanding the C++ Compilation Process**
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

### **Step 1: Preprocessing (`.cpp → .i`)**
- The **preprocessor** expands macros, includes header files, and removes comments.
- Directives like `#include`, `#define`, and `#ifdef` are processed.
- The output is a preprocessed file (`.i`).

### **Step 2: Compilation (`.i → .s`)**
- The compiler converts the **preprocessed code** into **assembly language**.
- It also checks for **syntax errors**.

### **Step 3: Assembly (`.s → .o/.obj`)**
- The assembler translates **assembly code** into **machine code**.
- Produces an **object file** (`.o` on Linux/macOS, `.obj` on Windows).

### **Step 4: Linking (`.o → Executable`)**
- Combines object files and **external libraries** to create an **executable program**.
- Resolves function references from libraries (like the **C++ Standard Library**).

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