# User Defined Types

In C programming, user-defined types allow you to create complex data structures that better represent the problem domain of your application. This is achieved using several mechanisms, including `struct`, `union`, `enum`, and `typedef`. Here’s a detailed guide on how to use these user-defined types in C.
 

- **Structs**: Group related variables of different types together.
- **Unions**: Store different data types in the same memory location, but only one type can be used at a time.
- **Enums**: Define a set of named integer constants for better code readability.
- **Typedef**: Create aliases for existing types to simplify complex type definitions.

These user-defined types are fundamental for creating more organized, readable, and maintainable C programs. They help model real-world entities more effectively and make code easier to understand and work with.# User Defined Types in C – Transflower Mentor Style

So far in our C learning journey, we have worked with:

```c
int age;
float salary;
char grade;
```

These are called:

```text
Built-in Data Types
```

provided by the C language.

But now think like a software engineer.


# Step 1: The Real Problem

Suppose you are developing a:

```text
School Management System
```

For every student you need:

```text
Roll Number
Name
Age
Marks
```

Using primitive variables:

```c
int rollNo;
char name[50];
int age;
float marks;
```

Works for one student.

What about:

```text
100 Students ?
1000 Students ?
10000 Students ?
```

The code becomes difficult to manage.

We need a way to create our own data type.

This is where:

```text
User Defined Types
```

enter the picture.


# What Are User Defined Types?

User Defined Types allow programmers to create their own data models.

Think:

```text
int
float
char
```

are provided by C.

Similarly:

```text
Student
Employee
Product
Customer
Order
```

can be created by us.


# Four Major User Defined Types

C provides four mechanisms:

```text
struct
union
enum
typedef
```

Let's understand them one by one.


# Part 1: Structure (struct)

## Real World Thinking

A student is not a single value.

A student contains:

```text
Roll Number
Name
Age
Marks
```

These belong together.


## Structure Definition

```c
struct Student
{
    int rollNo;
    char name[50];
    int age;
    float marks;
};
```

Here we have created a new blueprint:

```text
Student
```

# Visual Representation

```text
Student

+----------------+
| rollNo         |
+----------------+
| name           |
+----------------+
| age            |
+----------------+
| marks          |
+----------------+
```

# Creating an Object

```c
struct Student s1;
```

Memory:

```text
s1

rollNo
name
age
marks
```

# Assigning Values

```c
s1.rollNo = 101;
s1.age = 20;
s1.marks = 85.5;
```


# Accessing Members

```c
printf("%d", s1.rollNo);
printf("%f", s1.marks);
```

using:

```text
Dot Operator (.)
```


# Why Structures Exist

Without structure:

```c
int rollNo;
char name[50];
float marks;
```

With structure:

```c
struct Student student;
```

Cleaner.

Organized.

Real-world modeling.


# Industry Examples

## Employee

```c
struct Employee
{
    int empId;
    char name[50];
    float salary;
};
```

## Product

```c
struct Product
{
    int productId;
    char title[50];
    float price;
};
```

## Bank Account

```c
struct Account
{
    int accountNo;
    char holderName[50];
    double balance;
};
```


# Part 2: Union

Now let's understand something interesting.


# Structure Memory

Consider:

```c
struct Sample
{
    int x;
    float y;
    char z;
};
```

Memory:

```text
x
y
z
```

Every member gets separate storage.

# Union

```c
union Sample
{
    int x;
    float y;
    char z;
};
```

Memory:

```text
+-----------+
| Shared    |
| Memory    |
+-----------+
```

All members share the same location.


# Visualization

Structure:

```text
+----+----+----+
| x  | y  | z  |
+----+----+----+
```

Union:

```text
+------------+
| x/y/z      |
+------------+
```

One memory block.

# Example

```c
union Data
{
    int i;
    float f;
};
```

```c
union Data d;

d.i = 10;
```

Memory contains:

```text
10
```

Now:

```c
d.f = 5.5;
```

The previous value is overwritten.

Because:

```text
Same Memory
```

# Why Use Union?

Useful when:

```text
Only one value is needed at a time
```

Examples:

```text
Device Drivers
Embedded Systems
Network Protocols
Memory Optimization
```

# Part 3: Enumeration (enum)

Consider:

```text
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
```

We can store:

```c
int day;
```

But:

```text
1 means Monday?
2 means Tuesday?
```

Not clear.


# Enum Solution

```c
enum Day
{
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
};
```

Internally:

```text
MONDAY     = 0
TUESDAY    = 1
WEDNESDAY  = 2
...
```


# Usage

```c
enum Day today;

today = MONDAY;
```

More readable than:

```c
today = 0;
```

# Real Industry Examples

## Order Status

```c
enum OrderStatus
{
    PENDING,
    PROCESSING,
    SHIPPED,
    DELIVERED
};
```

## Traffic Signal

```c
enum Signal
{
    RED,
    YELLOW,
    GREEN
};
```

## User Roles

```c
enum UserRole
{
    ADMIN,
    MANAGER,
    EMPLOYEE
};
```

# Why Engineers Love Enum

Compare:

```c
status = 2;
```

vs

```c
status = SHIPPED;
```

Which is easier to understand?

Obviously:

```text
SHIPPED
```

# Part 4: Typedef

Many students complain:

```c
struct Student s1;
struct Student s2;
struct Student s3;
```

Too much typing.

# Typedef Solution

```c
typedef struct Student
{
    int rollNo;
    char name[50];
} Student;
```

Now:

```c
Student s1;
Student s2;
```

Cleaner.

# Typedef with Primitive Types

```c
typedef unsigned int UINT;
```

Now:

```c
UINT age;
```

instead of:

```c
unsigned int age;
```

# Industry Usage

Operating systems and frameworks use typedef heavily.

Example:

```c
typedef unsigned long DWORD;
```

Common in Windows APIs.

# Combining Struct + Typedef

Professional C programmers often write:

```c
typedef struct
{
    int id;
    char name[50];
    float salary;
} Employee;
```

Usage:

```c
Employee emp1;
Employee emp2;
```

Looks almost like a built-in type.

# Real Business Example

## Student Result System

```c
typedef struct
{
    int rollNo;
    char name[50];
    float marks;
} Student;
```

Array:

```c
Student students[100];
```

Now we can manage:

```text
100 Students
```

easily.

# Mentor Insight

When beginners see:

```c
struct
union
enum
typedef
```

they think:

```text
Language Features
```

Software engineers see:

```text
Modeling Real World Entities
```

# Evolution of Thinking

Initially:

```c
int age;
```

One value.

Then:

```c
int marks[5];
```

Collection of values.

Then:

```c
struct Student
{
   ...
};
```

Entity.

Then:

```c
Student students[100];
```

Collection of entities.

This is how business software is built.

# Industry Mapping

```text
Student
Employee
Customer
Order
Product
Invoice
Hospital Patient
Bank Account
```

All are typically represented using:

```text
Structures
```


# Mentor Challenge

Create the following user-defined types:

### Student

```text
Roll Number
Name
Marks
```

### Employee

```text
Employee Id
Name
Salary
```

### Product

```text
Product Id
Title
Price
```

### Enum

```text
Order Status
```

Values:

```text
Pending
Processing
Shipped
Delivered
```

# Knowledge Journey

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
Iteration
    ↓
Recursion
    ↓
User Defined Types
        ↓
    Structure
    Union
    Enum
    Typedef
        ↓
Dynamic Memory Allocation
        ↓
Linked Lists
        ↓
Data Structures
```

The biggest lesson from User Defined Types is:

> **Programming is not about storing data. It is about modeling the real world inside memory.**

That transformation—from primitive values to meaningful business entities—is what turns a C programmer into a software engineer.
