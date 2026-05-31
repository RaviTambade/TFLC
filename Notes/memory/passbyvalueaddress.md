# Pass By Value vs Pass By Address

Before understanding pointers deeply, every software engineer must answer one important question:

> When a function receives data, does it receive the **actual data** or does it receive the **address of the data**?

The answer leads us to:

```text
Pass By Value
Pass By Address
```

# Think Like a Manager

Suppose you are a project manager.

You have a document:

```text
Project Budget
--------------
100000
```

Now you ask an employee:

> "Please update this budget."

There are two ways.

# Scenario 1: Pass By Value

You create a photocopy.

```text
Original Document
-----------------
100000

Photocopy
---------
100000
```

Employee modifies:

```text
Photocopy
---------
200000
```

What happened to original?

```text
Original
---------
100000
```

Nothing changed.

Because employee worked on a copy.

This is:

```text
Pass By Value
```

# C Example

```c
#include<stdio.h>

void update(int amount)
{
    amount = 200000;
}

int main()
{
    int budget = 100000;

    update(budget);

    printf("%d",budget);
}
```

Output:

```text
100000
```

Students are surprised.

They expected:

```text
200000
```

But function received:

```text
Copy of budget
```

not the actual budget.

# Memory Visualization

Before function call:

```text
main()

budget
+-------+
|100000 |
+-------+
```

Call:

```c
update(budget);
```

Compiler creates:

```text
update()

amount
+-------+
|100000 |
+-------+
```

Now there are two separate variables.

```text
budget
amount
```

Changing one does not affect the other.

# Scenario 2: Pass By Address

Instead of giving photocopy:

You give office location.

```text
Budget Document
Room Number 101
```

Employee goes directly to room 101.

Makes changes there.

Now original changes.

This is:

```text
Pass By Address
```

# C Example

```c
#include<stdio.h>

void update(int *amount)
{
    *amount = 200000;
}

int main()
{
    int budget = 100000;

    update(&budget);

    printf("%d",budget);
}
```

Output:

```text
200000
```


# What Happened?

Function receives:

```c
&budget
```

Meaning:

```text
Address of budget
```

Suppose:

```text
budget
Address = 1000
Value   = 100000
```

Function receives:

```text
1000
```

not

```text
100000
```

Inside function:

```c
*amount = 200000;
```

means:

```text
Go to address 1000
Change value there
```

# Visualizing Pass By Address

Main Function:

```text
Address  Value

1000     100000
budget
```

Call:

```c
update(&budget);
```

Function:

```text
amount
   |
   |
   v

1000
```

Pointer points to budget.

```text
amount
   |
   v

budget
```

Modification:

```c
*amount = 200000;
```

Result:

```text
Address  Value

1000     200000
```

Original data changes.

# Why Engineers Prefer Pass By Address

Consider:

```c
struct Employee
{
    char name[1000];
    double salary;
    char address[2000];
};
```

Size:

```text
3000+ bytes
```

Now imagine:

```c
processEmployee(employee);
```

using Pass By Value.

Every function call copies:

```text
3000 bytes
```

If function is called:

```text
10000 times
```

Huge memory waste.

# Better Approach

```c
processEmployee(&employee);
```

Now only address is copied.

Suppose machine is:

```text
64-bit
```

Address size:

```text
8 bytes
```

Instead of copying:

```text
3000 bytes
```

we copy:

```text
8 bytes
```

Massive improvement.

# Industry Example: Student Records

```c
struct Student
{
    int rollNo;
    char name[100];
    float marks[6];
};
```

Suppose:

```c
void displayStudent(Student student)
```

Every call copies entire structure.

Better:

```c
void displayStudent(Student *student)
```

Pass only address.

Most enterprise applications work this way.

# Why C Uses Pass By Value Only

Many students ask:

> "Sir, does C support Pass By Address?"

Interesting answer:

```text
No
```

C supports only:

```text
Pass By Value
```

Even here:

```c
update(&budget);
```

what is passed?

```text
A copy of address
```

The address itself is passed by value.

That copied address happens to point to original memory.

Hence we call it:

```text
Pass By Address
```

conceptually.

# Memory Comparison

Suppose:

```c
struct BigData
{
    int values[10000];
};
```

Size:

```text
40000 bytes
```

### Pass By Value

```c
process(data);
```

Stack:

```text
Main Stack
    ↓

40000 bytes copied
```

### Pass By Address

```c
process(&data);
```

Stack:

```text
Address only

8 bytes
```

Huge savings.

# Mentor Insight

Freshers often think:

```text
Pointer = Confusing Syntax
```

Experienced engineers think:

```text
Pointer = Memory Efficiency
```

Pointers are not merely symbols like:

```c
*
&
```

Pointers are mechanisms that allow:

```text
Shared Access
Memory Optimization
Dynamic Memory Allocation
Linked Lists
Trees
Operating Systems
Database Engines
Game Engines
```

# Real Software Examples

### Banking System

```c
Customer customers[10000];
```

Functions receive:

```c
Customer *
```

not

```c
Customer
```

### Game Development

```c
Player *
Enemy *
Weapon *
```

Objects are large.

Passing copies would be expensive.


### Operating Systems

Processes are represented through structures.

Kernel functions typically manipulate:

```c
Process *
```

rather than copying entire process information.

# Interview Question

What will be output?

```c
void change(int x)
{
    x = 50;
}

int main()
{
    int num = 10;

    change(num);

    printf("%d",num);
}
```

Answer:

```text
10
```

Because:

```text
Pass By Value
```


What will be output?

```c
void change(int *x)
{
    *x = 50;
}

int main()
{
    int num = 10;

    change(&num);

    printf("%d",num);
}
```

Answer:

```text
50
```

Because:

```text
Pass By Address
```

# Knowledge Connection

```text
Variables
    ↓
Functions
    ↓
Arrays
    ↓
Pointers
    ↓
Pass By Value
    ↓
Pass By Address
    ↓
Dynamic Memory Allocation
    ↓
Linked Lists
```

Notice how pointers suddenly become useful.

Without understanding Pass By Address, students often ask:

> "Why do we even need pointers?"

Now the answer is clear:

```text
To allow functions to work with original data
without creating unnecessary copies.
```

That idea becomes the foundation of efficient software engineering and systems programming. 🚀
