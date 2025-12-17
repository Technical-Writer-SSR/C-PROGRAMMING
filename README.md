# C Programming 

![C Language](https://img.shields.io/badge/Language-C-blue)
![Standard](https://img.shields.io/badge/C11/C17-Standard-yellow)
![Compilers](https://img.shields.io/badge/GCC%7CClang%7CMinGW-Compilers-green)
![Level](https://img.shields.io/badge/System%20Programming-Mid--Level-red)
[![C Programming](https://img.shields.io/badge/Language-C-blue.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Standard](https://img.shields.io/badge/Standard-ANSI%20C-orange.svg)](https://en.wikipedia.org/wiki/ANSI_C)
[![Level](https://img.shields.io/badge/Level-Foundational-green.svg)](https://en.wikipedia.org/wiki/C_(programming_language))

##  Table of Contents
- [Introduction](#introduction)
- [File Operations in C](#file-operations-in-c)
- [Common Mistakes to Avoid](#common-mistakes-to-avoid)
- [Best Practices](#best-practices)
- [Quick Reference](#quick-reference)
- [Resources](#resources)
- [Author](#author)

##  Introduction
This guide explains the fundamental role of `#include <stdio.h>` in C programming, particularly for file operations. Understanding header files and function declarations is essential for writing error-free C code.


### Hello World Program
```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

**Compile & Run:**
```bash
gcc hello.c -o hello
./hello
```

##  Core Topics Overview

### 1. **Basic Syntax & Structure**
```c
#include <stdio.h>  // Header file

int main() {        // Entry point
    // Variables
    int age = 25;
    float salary = 50000.50;
    char grade = 'A';
    
    // Output
    printf("Age: %d\nSalary: %.2f\nGrade: %c\n", age, salary, grade);
    
    return 0;  // Exit code
}
```

### 2. **Data Types**
| Type | Size | Range | Example |
|------|------|-------|---------|
| `char` | 1 byte | -128 to 127 | `char c = 'A';` |
| `int` | 4 bytes | -2³¹ to 2³¹-1 | `int num = 100;` |
| `float` | 4 bytes | 1.2E-38 to 3.4E+38 | `float pi = 3.14;` |
| `double` | 8 bytes | 2.3E-308 to 1.7E+308 | `double val = 3.14159;` |

### 3. **Control Flow**
```c
// If-else
if (age >= 18) {
    printf("Adult\n");
} else {
    printf("Minor\n");
}

// Switch
switch(grade) {
    case 'A': printf("Excellent\n"); break;
    case 'B': printf("Good\n"); break;
    default: printf("Try again\n");
}

// Loops
for(int i=0; i<5; i++) printf("%d ", i);  // 0 1 2 3 4

while(count > 0) {
    count--;
}

do {
    // runs at least once
} while(condition);
```

### 4. **Functions**
```c
// Function prototype
int add(int a, int b);

// Function definition
int add(int a, int b) {
    return a + b;
}

// Function call
int result = add(10, 20);
```

### 5. **Arrays & Strings**
```c
// Arrays
int numbers[5] = {1, 2, 3, 4, 5};
numbers[0] = 10;  // Access/modify

// 2D Arrays
int matrix[3][3] = {{1,2,3}, {4,5,6}, {7,8,9}};

// Strings
char name[20] = "John";
char name2[] = "Doe";  // Auto size
strcpy(name, "Jane");  // Copy string
strlen(name);          // Get length
```

### 6. **Pointers (Most Important!)**
```c
int var = 10;
int *ptr = &var;  // ptr points to var

printf("Value: %d\n", var);      // 10
printf("Address: %p\n", &var);   // Memory address
printf("Pointer: %d\n", *ptr);   // 10 (dereference)

// Pointer arithmetic
int arr[] = {10, 20, 30};
int *p = arr;
printf("%d\n", *(p+1));  // 20

// Pointers in functions
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
```

### 7. **Structures**
```c
struct Student {
    char name[50];
    int age;
    float marks;
};

// Create variable
struct Student s1;
strcpy(s1.name, "Alice");
s1.age = 20;
s1.marks = 85.5;

// Pointer to structure
struct Student *ptr = &s1;
printf("Name: %s\n", ptr->name);  // Arrow operator
```

### 8. **Memory Management**
```c
#include <stdlib.h>

// Dynamic allocation
int *arr = (int*)malloc(5 * sizeof(int));
if(arr == NULL) {
    printf("Memory error!\n");
    return 1;
}

// Initialize array
for(int i=0; i<5; i++) arr[i] = i*10;

// Reallocate
arr = realloc(arr, 10 * sizeof(int));

// FREE MEMORY (IMPORTANT!)
free(arr);
arr = NULL;
```

### 9. **File Handling**
```c
#include <stdio.h>

// Write to file
FILE *f = fopen("data.txt", "w");
fprintf(f, "Hello File!\n");
fclose(f);

// Read from file
f = fopen("data.txt", "r");
char buffer[100];
while(fgets(buffer, sizeof(buffer), f) != NULL) {
    printf("%s", buffer);
}
fclose(f);
```

##  File Operations in C

### Key Function Declarations
```c
// These prototypes are defined in stdio.h
FILE *fopen(const char *filename, const char *mode);
int fclose(FILE *stream);
```

### What is `FILE`?
- Structure type defined in `stdio.h`
- Represents a file stream
- `FILE *` is a pointer to this structure

##  Common Mistakes to Avoid

| Mistake | Example | Correction |
|---------|---------|------------|
| Wrong Case | `#include <Stdio.h>` | `#include <stdio.h>` |
| Missing Hash | `include <stdio.h>` | `#include <stdio.h>` |
| Extra Semicolon | `#include <stdio.h>;` | `#include <stdio.h>` |

##  Best Practices
1. Always include necessary headers before function calls
2. Use angle brackets for system headers: `#include <header.h>`
3. Use quotes for local headers: `#include "myheader.h"`
4. Organize includes logically (system headers first)

##  Quick Reference

### Essential Headers for Beginners
| Header | Purpose | Key Functions |
|--------|---------|--------------|
| `stdio.h` | Input/Output | `printf`, `scanf`, `fopen`, `fclose` |
| `math.h` | Math operations | `sqrt`, `sin`, `cos`, `pow` |
| `string.h` | String manipulation | `strlen`, `strcpy`, `strcmp` |

### Basic File Operations Pattern
```c
#include <stdio.h>

int main() {
    FILE *file = fopen("example.txt", "r");
    if (file) {
        // File operations here
        fclose(file);
    }
    return 0;
}
```

##  Resources
- **Books:**
  - *The C Programming Language* by Kernighan & Ritchie
  - *C Primer Plus* by Stephen Prata
- **Online:**
  - [cppreference.com - C documentation](https://en.cppreference.com/w/c)
  - [GCC Documentation](https://gcc.gnu.org/onlinedocs/)
- **Tools:**
  - GCC Compiler
  - GDB Debugger
  - Make Build System

##  Author
**Embedded Systems Developer**  
*Specializing in C Programming and Embedded Systems*  
📧 Contact: Your learning journey starts here!

---

> **Note**: This guide focuses on foundational concepts. Master these basics before moving to advanced topics like memory management, pointers, and embedded systems programming.

[![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)](LICENSE)
[![Last Updated](https://img.shields.io/badge/Updated-January%202025-brightgreen.svg)](README.md)
