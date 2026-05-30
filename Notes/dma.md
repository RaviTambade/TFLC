# Dynamic Memory Allocation (DMA) in C

So far your journey has been:

```text
Variables
   ↓
Functions
   ↓
Pointers
   ↓
Arrays
   ↓
Strings
   ↓
Structures
   ↓
Files
   ↓
Multidimensional Arrays
```

Now we are entering a topic that separates a beginner C programmer from a serious systems programmer.

# Dynamic Memory Allocation (DMA)

# Step 1: The Problem with Arrays

Suppose you are creating a Student Management System.

You decide to store student marks:

```c
int marks[100];
```

Question:

What if there are only 10 students?

```text
Memory Reserved = 100 Integers
Memory Used     = 10 Integers
Memory Wasted   = 90 Integers
```

Another scenario:

```c
int marks[100];
```

What if tomorrow there are 1000 students?

```text
Memory Reserved = 100 Integers
Memory Needed   = 1000 Integers
```

Now memory is insufficient.

This is the biggest limitation of traditional arrays:

```text
Size must be known at compile time.
```

Real-world applications rarely know this.

Examples:

```text
How many customers?
How many products?
How many employees?
How many orders?
```

The answer is usually:

```text
Unknown until runtime.
```

# Step 2: Memory Regions of a Program

When a C program runs, memory is divided into regions.

```text
+--------------------+
| Code Segment       |
+--------------------+
| Global Variables   |
+--------------------+
| Stack              |
+--------------------+
| Heap               |
+--------------------+
```

You already use:

```text
Stack Memory
```

Example:

```c
int age = 25;
```

Stored on stack.

Dynamic memory comes from:

# Heap Memory

The Heap is a large pool of memory managed at runtime.


# Step 3: What is Dynamic Memory Allocation?

Instead of:

```c
int marks[100];
```

we ask the Operating System:

> Give me memory when I need it.

This process is called:

```text
Dynamic Memory Allocation
```

# Step 4: malloc()

The most important DMA function.

Syntax:

```c
malloc(size);
```

Example:

```c
int *ptr;

ptr=(int *)malloc(5*sizeof(int));
```

Meaning:

```text
Allocate memory for 5 integers
Return starting address
Store address in ptr
```

Memory:

```text
Heap

+----+----+----+----+----+
|    |    |    |    |    |
+----+----+----+----+----+

ptr
 |
 v
```

# Step 5: First DMA Program

```c
#include<stdio.h>
#include<stdlib.h>

int main()
{
    int *ptr;

    ptr=(int *)malloc(5*sizeof(int));

    for(int i=0;i<5;i++)
    {
        ptr[i]=(i+1)*10;
    }

    for(int i=0;i<5;i++)
    {
        printf("%d\n",ptr[i]);
    }

    free(ptr);

    return 0;
}
```

Output:

```text
10
20
30
40
50
```

# Step 6: Why Pointers are Required

Students often ask:

Why did we learn pointers before DMA?

Because:

```c
malloc()
```

returns an address.

Addresses must be stored in pointers.

```c
int *ptr;
```

Without pointers:

```text
DMA is impossible.
```

This is why Transflower teaches:

```text
Pointers
   ↓
Arrays
   ↓
DMA
```

in that order.

# Step 7: calloc()

Another memory allocation function.

Syntax:

```c
calloc(numberOfElements,sizeOfElement);
```

Example:

```c
int *ptr;

ptr=(int *)calloc(5,sizeof(int));
```

Difference:

### malloc()

```text
Memory contains garbage values.
```

### calloc()

```text
Memory initialized to zero.
```

Example:

```text
0
0
0
0
0
```

# Step 8: malloc vs calloc

| Feature        | malloc          | calloc          |
| -------------- | --------------- | --------------- |
| Parameters     | Total bytes     | Elements + Size |
| Initialization | Garbage         | Zero            |
| Speed          | Slightly Faster | Slightly Slower |


# Step 9: realloc()

Suppose:

```c
ptr=(int *)malloc(5*sizeof(int));
```

Later user adds more students.

Need:

```text
10 Integers
```

Instead of creating a new array:

```c
ptr=(int *)realloc(ptr,10*sizeof(int));
```

Meaning:

```text
Resize memory block
```

This is one of the most powerful features of C.

# Step 10: Real Example

Initial customers:

```text
5
```

Allocate:

```c
malloc(5*sizeof(Customer))
```

Later customers become:

```text
50
```

Resize:

```c
realloc(...)
```

No need to restart application.

# Step 11: free()

Very important.

Suppose:

```c
ptr=(int *)malloc(100*sizeof(int));
```

When finished:

```c
free(ptr);
```

Meaning:

```text
Return memory back to Operating System
```

# Step 12: Memory Leak

Common beginner mistake.

```c
int *ptr;

ptr=(int *)malloc(100*sizeof(int));

return 0;
```

No:

```c
free(ptr);
```

Memory remains occupied.

This is called:

# Memory Leak

In long-running applications:

```text
Web Servers
ERP Systems
CRM Applications
Games
```

memory leaks can crash systems.


# Step 13: Real Industry Analogy

Imagine:

```text
malloc()
```

Renting a warehouse.

```text
realloc()
```

Expanding warehouse.

```text
free()
```

Returning warehouse when no longer needed.

Good software engineers always return rented resources.

# Step 14: Dynamic Array

Take size from user.

```c
int n;

printf("Enter Size:");
scanf("%d",&n);

int *arr;

arr=(int *)malloc(n*sizeof(int));
```

Now array size is determined at runtime.

Example:

```text
User enters 5
```

Memory:

```text
5 Integers
```

```text
User enters 5000
```

Memory:

```text
5000 Integers
```

Same program.

# Step 15: Dynamic Structure Allocation

Suppose:

```c
typedef struct
{
    int id;
    char name[50];
} Student;
```

Allocate:

```c
Student *s;

s=(Student *)malloc(sizeof(Student));
```

Access:

```c
s->id=101;
```

This is heavily used in enterprise applications.


# Step 16: Dynamic Array of Structures

Example:

```c
Student *students;

students=(Student *)
malloc(100*sizeof(Student));
```

Now:

```text
100 Student Objects
```

created dynamically.

This is how early database-style systems were built.

# Step 17: Why DMA Was Invented?

Without DMA:

```text
Fixed Size
Memory Waste
Memory Shortage
```

With DMA:

```text
Flexible Size
Efficient Usage
Runtime Allocation
```

# Mentor Insight

Most students learn:

```text
malloc()
calloc()
realloc()
free()
```

as functions.

A software engineer sees them as:

```text
Memory Management Tools
```

Understanding DMA means understanding how software actually uses RAM.

# Mini Project

## Dynamic Student Management System

Ask:

```c
How many students?
```

Allocate:

```c
Student *students;
```

using:

```c
malloc()
```

Features:

```text
Add Students
Display Students
Search Student
Update Student
Delete Student
```

Later:

```text
More Students Added
```

Use:

```c
realloc()
```

# Knowledge Journey

```text
Variables
   ↓
Pointers
   ↓
Arrays
   ↓
Strings
   ↓
Structures
   ↓
Files
   ↓
Multidimensional Arrays
   ↓
Dynamic Memory Allocation
```

Notice something important:

```text
Pointers + Structures + DMA
```

together unlock:

```text
Linked Lists
Stacks
Queues
Trees
Graphs
Databases
Operating Systems
```

---

# Next Transflower Mentor Session

Now we arrive at one of the most important milestones in computer science:

# Linked Lists

Because arrays have limitations:

```text
Fixed Size
Costly Insertions
Costly Deletions
```

Linked Lists solve these problems using:

```text
Structure
+
Pointer
+
Dynamic Memory Allocation
```

This is the first true Data Structure that transforms a programmer into a software engineer capable of building complex systems.
