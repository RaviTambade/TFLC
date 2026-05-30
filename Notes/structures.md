# Transflower Mentor Session: Structures (`struct`) in C

## Dear Students,

So far we have learned:

```text
Variables
   ↓
Pointers
   ↓
Arrays
   ↓
Strings
```

Now let me ask you a question.

Can a student's information be stored in a single variable?

```c
int student;
```

No.

Can it be stored in a single array?

```c
int student[10];
```

No.

Because a student has different types of information:

```text
Roll Number → Integer
Name        → String
Age         → Integer
Percentage  → Float
```

Different data types must be grouped together.

This is why C provides:

# Structure (`struct`)

---

# Step 1: Why Structures Were Invented?

Imagine you are developing a College Management System.

Student Information:

```text
Roll No : 101
Name    : Ravi
Age     : 22
Marks   : 85.5
```

Without structure:

```c
int rollNo;
char name[50];
int age;
float marks;
```

This works for one student.

But for 1000 students?

You will have hundreds of separate variables.

Software engineers needed a mechanism to combine related information into one unit.

Hence:

```c
struct
```

---

# Step 2: Defining a Structure

```c
struct Student
{
    int rollNo;
    char name[50];
    int age;
    float marks;
};
```

Think of this as a blueprint.

Like an architect's building design.

No memory is allocated yet.

---

# Step 3: Creating Structure Variable

```c
struct Student s1;
```

Now memory is allocated.

Memory Layout:

```text
s1

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

---

# Step 4: Assigning Values

```c
s1.rollNo = 101;

strcpy(s1.name,"Ravi");

s1.age = 22;

s1.marks = 85.5;
```

Notice:

```c
.
```

called the **dot operator**.

Used to access structure members.

---

# Step 5: Display Structure Data

```c
printf("%d\n",s1.rollNo);
printf("%s\n",s1.name);
printf("%d\n",s1.age);
printf("%.2f\n",s1.marks);
```

Output:

```text
101
Ravi
22
85.50
```

---

# Step 6: Complete Program

```c
#include<stdio.h>
#include<string.h>

struct Student
{
    int rollNo;
    char name[50];
    int age;
    float marks;
};

int main()
{
    struct Student s1;

    s1.rollNo=101;
    strcpy(s1.name,"Ravi");
    s1.age=22;
    s1.marks=85.5;

    printf("%d\n",s1.rollNo);
    printf("%s\n",s1.name);
    printf("%d\n",s1.age);
    printf("%.2f\n",s1.marks);

    return 0;
}
```

---

# Step 7: Multiple Students

Real applications manage many students.

```c
struct Student students[3];
```

Now memory contains:

```text
Student 1
Student 2
Student 3
```

Just like an array of integers:

```c
int marks[10];
```

But each element is a complete student object.

---

# Step 8: Taking Input

```c
printf("Enter Roll No:");
scanf("%d",&s1.rollNo);

printf("Enter Name:");
scanf("%s",s1.name);

printf("Enter Age:");
scanf("%d",&s1.age);

printf("Enter Marks:");
scanf("%f",&s1.marks);
```

---

# Step 9: Array of Structures

Most important concept.

```c
struct Student students[5];
```

Memory:

```text
Student[0]
Student[1]
Student[2]
Student[3]
Student[4]
```

Access:

```c
students[0].rollNo
students[0].name

students[1].rollNo
students[1].name
```

---

# Step 10: Loop Through Students

```c
for(int i=0;i<3;i++)
{
    printf("%d\n",students[i].rollNo);
    printf("%s\n",students[i].name);
}
```

This is how ERP, CRM, School Management and HR applications manage records.

---

# Step 11: Structures and Functions

Suppose we want to display student details.

```c
void display(struct Student s)
{
    printf("%d\n",s.rollNo);
    printf("%s\n",s.name);
}
```

Calling:

```c
display(s1);
```

Structure is passed as argument.

---

# Step 12: Structure Pointer

Now connect structures with pointers.

```c
struct Student s1;

struct Student *ptr=&s1;
```

Memory:

```text
ptr
 |
 v
+----------------+
| Student Object |
+----------------+
```

---

# Step 13: Arrow Operator

Without pointer:

```c
s1.rollNo
```

With pointer:

```c
ptr->rollNo
```

Equivalent to:

```c
(*ptr).rollNo
```

Example:

```c
printf("%d",ptr->rollNo);
```

This is heavily used in professional software development.

---

# Step 14: Typedef

Writing:

```c
struct Student s1;
```

again and again becomes tedious.

Engineers use:

```c
typedef struct
{
    int rollNo;
    char name[50];
    int age;
    float marks;
} Student;
```

Now:

```c
Student s1;
Student s2;
```

Cleaner and easier.

---

# Step 15: Real Industry Examples

## CRM Application

```c
struct Customer
{
    int customerId;
    char customerName[50];
    char city[50];
};
```

---

## E-Commerce

```c
struct Product
{
    int productId;
    char productName[50];
    float price;
};
```

---

## HR System

```c
struct Employee
{
    int employeeId;
    char employeeName[50];
    float salary;
};
```

---

## Banking

```c
struct Account
{
    int accountNumber;
    char holderName[50];
    double balance;
};
```

---

# Step 16: Mentor Insight

Many students learn structures only as:

```text
Exam Topic
```

A software engineer sees structures as:

```text
Real World Entity
```

Examples:

```text
Student
Customer
Product
Employee
Order
Invoice
Department
Hospital
Doctor
Patient
```

Every business application starts by identifying entities.

Then we create structures to represent them.

---

# Transflower Thinking Process

Before coding ask:

```text
What entity exists in the business?
```

Example:

Hospital

Entities:

```text
Doctor
Patient
Appointment
Medicine
Bill
```

Then create structures.

This is the first step toward software design.

---

# Mini Project

## Student Management System

Structure:

```c
Student
{
   RollNo
   Name
   Age
   Marks
}
```

Features:

```text
Add Student
Display Students
Search Student
Find Topper
Calculate Average Marks
```

---

# Learning Journey So Far

```text
Variables
   ↓
Operators
   ↓
Control Statements
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
```

Notice something interesting:

```text
Structure = Data
Function  = Behaviour
```

This idea will later evolve into:

```text
Class = Data + Behaviour
```

which is the foundation of Object-Oriented Programming.

---

# Next Transflower Mentor Session

After Structures, we will learn:

# File Handling in C

Because currently:

```text
Program Ends
     ↓
Data Lost
```

Real applications must store data permanently.

We will learn:

* fopen()
* fclose()
* fprintf()
* fscanf()
* fread()
* fwrite()

and build a simple persistent Student Management System that saves data to files, just like real business software.
