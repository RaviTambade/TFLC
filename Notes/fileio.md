# File Handling in C

Until now we have learned:

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
```

Let me ask a practical question.

Suppose you create a Student Management System.

```text
Student:
Ravi
Roll No: 101
Marks: 85
```

You store the data in variables.

Program runs perfectly.

Then:

```text
Program Ends
```

What happens?

All data disappears.

Why?

Because variables are stored in RAM.

RAM is temporary memory.

```text
Power OFF
Program Ends
Computer Restart
```

Data is lost.
# Why File Handling Was Invented?

Businesses need permanent storage.

Examples:

```text
Bank Account Details
Customer Records
Employee Data
Product Catalog
Hospital Records
```

must survive even after:

```text
Program Closed
System Restarted
Power Failure
```

Therefore programs need to store information on:

```text
Hard Disk
SSD
USB Drive
```

This is called:

# File Handling


# Step 1: What is a File?

A file is a collection of data stored permanently on secondary storage.

Examples:

```text
students.txt
employees.txt
products.dat
orders.csv
```

# Step 2: File Pointer

Just as arrays use pointers.

Files also use pointers.

C provides:

```c
FILE *fp;
```

Think of it as:

```text
Program
   |
   v
File Pointer
   |
   v
students.txt
```

The file pointer helps the program communicate with a file.

---

# Step 3: Opening a File

Syntax:

```c
fp = fopen("students.txt","w");
```

Meaning:

```text
Open students.txt
Mode = Write
```

---

# File Opening Modes

## Write Mode

```c
"w"
```

Creates new file.

If file exists:

```text
Old Data Deleted
```

---

## Read Mode

```c
"r"
```

Read existing file.

File must already exist.

---

## Append Mode

```c
"a"
```

Adds data at end of file.

Existing data remains safe.

---

# Step 4: Writing Data

Example:

```c
#include<stdio.h>

int main()
{
    FILE *fp;

    fp=fopen("students.txt","w");

    fprintf(fp,"Welcome To Transflower");

    fclose(fp);

    return 0;
}
```

After execution:

```text
students.txt

Welcome To Transflower
```

---

# Step 5: Closing File

Always close file.

```c
fclose(fp);
```

Reason:

```text
Flush Data
Release Resources
Prevent Corruption
```

---

# Step 6: Reading Data

Suppose file contains:

```text
Welcome To Transflower
```

Program:

```c
#include<stdio.h>

int main()
{
    FILE *fp;

    char text[100];

    fp=fopen("students.txt","r");

    fscanf(fp,"%s",text);

    printf("%s",text);

    fclose(fp);

    return 0;
}
```

Output:

```text
Welcome
```

Notice:

```text
Only first word
```

because `%s` stops at space.


# Step 7: Reading Character by Character

```c
char ch;

while((ch=fgetc(fp))!=EOF)
{
    printf("%c",ch);
}
```

Output:

```text
Welcome To Transflower
```

EOF means:

```text
End Of File
```

# Step 8: Writing Character by Character

```c
fputc('A',fp);
fputc('B',fp);
fputc('C',fp);
```

File becomes:

```text
ABC
```


# Step 9: Writing Strings

```c
fputs("Learning C Programming",fp);
```

File:

```text
Learning C Programming
```


# Step 10: Reading Strings

```c
fgets(buffer,100,fp);
```

Reads complete line.

Better than:

```c
fscanf()
```

for text data.


# Step 11: Storing Student Records

Structure:

```c
typedef struct
{
    int rollNo;
    char name[50];
    float marks;
} Student;
```

Student:

```c
Student s1;

s1.rollNo=101;
strcpy(s1.name,"Ravi");
s1.marks=85;
```

Save:

```c
fprintf(fp,"%d %s %.2f",
        s1.rollNo,
        s1.name,
        s1.marks);
```

File:

```text
101 Ravi 85.00
```


# Step 12: Reading Student Records

```c
Student s;

fscanf(fp,"%d %s %f",
       &s.rollNo,
       s.name,
       &s.marks);
```

Output:

```text
101 Ravi 85.00
```


# Step 13: Binary Files

Text files are human-readable.

Example:

```text
101 Ravi 85
```

But business systems often use binary files.

Why?

```text
Faster
Compact
Efficient
```

# Step 14: Writing Structure Directly

```c
fwrite(&s1,
       sizeof(Student),
       1,
       fp);
```

Meaning:

```text
Write entire student object
```

directly into file.


# Step 15: Reading Structure Directly

```c
fread(&s1,
      sizeof(Student),
      1,
      fp);
```

Entire structure comes back.

This is very powerful.


# Step 16: Complete Student Save Program

```c
#include<stdio.h>
#include<string.h>

typedef struct
{
    int rollNo;
    char name[50];
    float marks;
} Student;

int main()
{
    FILE *fp;

    Student s1;

    s1.rollNo=101;
    strcpy(s1.name,"Ravi");
    s1.marks=85.5;

    fp=fopen("students.dat","wb");

    fwrite(&s1,sizeof(Student),1,fp);

    fclose(fp);

    printf("Student Saved");

    return 0;
}
```

# Step 17: Real Industry Analogy

Imagine:

## Hospital System

```text
Doctor
Patient
Appointment
Bill
```

represented using structures.

When user clicks:

```text
Save
```

Application writes those structures into:

```text
Database
Files
Cloud Storage
```

File Handling is the first step toward understanding databases.

# Step 18: Mentor Insight

Most students think:

```text
File Handling = Exam Topic
```

Software Engineers think:

```text
Persistence
```

Important concept:

```text
RAM  = Temporary Memory
Disk = Permanent Memory
```

Applications become useful only when data survives program termination.


# Mini Project

## Student Record Management System

Structure:

```c
Student
{
   RollNo
   Name
   Marks
}
```

Menu:

```text
1 Add Student
2 Display Students
3 Search Student
4 Exit
```

Use:

```c
fwrite()
fread()
```

Store data in:

```text
students.dat
```

# Knowledge Connection

Observe how everything is connecting:

```text
Variables
    ↓
Arrays
    ↓
Strings
    ↓
Structures
    ↓
Files
```

A Student Record is:

```text
Structure
```

Many Student Records:

```text
Array of Structures
```

Permanent Storage:

```text
File
```

This is exactly how early business software was built.


# What Comes Next?

After File Handling, a Transflower student is ready for:

# Dynamic Memory Allocation (DMA)

Because until now:

```c
int marks[100];
```

size is fixed.

But real applications don't know in advance:

```text
How many customers?
How many products?
How many employees?
```

Therefore programs must allocate memory at runtime using:

* `malloc()`
* `calloc()`
* `realloc()`
* `free()`

This is the gateway to:

```text
Linked Lists
Stacks
Queues
Trees
Databases
Operating Systems
```

and marks the transition from basic C programming to serious systems and software engineering.

