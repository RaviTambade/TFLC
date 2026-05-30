# Multidimensional Arrays

Before we move into Dynamic Memory Allocation and Data Structures, there is one very important concept that every software engineer must understand:

# Multidimensional Arrays

You already know:

```c
int marks[5];
```

This is called a:

```text
One-Dimensional Array (1D Array)
```

Memory:

```text
+----+----+----+----+----+
| 10 | 20 | 30 | 40 | 50 |
+----+----+----+----+----+
```

Used for storing:

* Student marks
* Product prices
* Employee IDs
* Sales figures

But what happens when data has both rows and columns?


# Step 1: Real World Problem

Suppose you are managing marks of students.

| Student | Physics | Chemistry | Maths |
| ------- | ------- | --------- | ----- |
| Ravi    | 85      | 90        | 88    |
| Amit    | 75      | 80        | 78    |
| Neha    | 92      | 89        | 95    |

Can a 1D array represent this table naturally?

```c
int marks[9];
```

Possible, but difficult.

We need something that naturally represents:

```text
Rows
Columns
```

Hence:

# Two-Dimensional Arrays

# Step 2: What is a Two-Dimensional Array?

Syntax:

```c
int marks[3][3];
```

Meaning:

```text
3 Rows
3 Columns
```

Visualization:

```text
      Col0 Col1 Col2

Row0   []   []   []
Row1   []   []   []
Row2   []   []   []
```

Memory contains:

```text
9 integers
```


# Step 3: Initialization

```c
int marks[3][3] =
{
    {85,90,88},
    {75,80,78},
    {92,89,95}
};
```

Table View:

```text
85  90  88
75  80  78
92  89  95
```


# Step 4: Accessing Elements

Access Ravi's Chemistry marks:

```c
marks[0][1]
```

Explanation:

```text
marks[row][column]

marks[0][1]

Row 0
Column 1
```

Output:

```text
90
```

# Step 5: Printing Entire Matrix

Using nested loops:

```c
for(int i=0;i<3;i++)
{
    for(int j=0;j<3;j++)
    {
        printf("%d ",marks[i][j]);
    }

    printf("\n");
}
```

Output:

```text
85 90 88
75 80 78
92 89 95
```

# Step 6: Why Nested Loops?

Think about the table.

Outer loop:

```text
Row Traversal
```

Inner loop:

```text
Column Traversal
```

Visualize:

```text
Row 0
   Col 0
   Col 1
   Col 2

Row 1
   Col 0
   Col 1
   Col 2

Row 2
   Col 0
   Col 1
   Col 2
```

This is why multidimensional arrays and nested loops are inseparable.

# Step 7: Memory Layout

Many students think memory looks like a table.

Actually memory is linear.

For:

```c
int arr[2][3] =
{
    {10,20,30},
    {40,50,60}
};
```

Memory:

```text
1000 → 10
1004 → 20
1008 → 30
1012 → 40
1016 → 50
1020 → 60
```

Internally:

```text
10 20 30 40 50 60
```

stored continuously.

This is called:

```text
Row Major Order
```

used by C.

# Step 8: Relationship with Pointers

Remember:

```c
int arr[5];
```

Array name stores address of first element.

Similarly:

```c
int matrix[3][3];
```

Matrix name stores address of first row.

Example:

```c
matrix
```

is equivalent to:

```c
&matrix[0]
```

# Step 9: Address Calculation

Suppose:

```c
int matrix[3][3];
```

Base address:

```text
1000
```

Memory:

```text
1000 1004 1008
1012 1016 1020
1024 1028 1032
```

Access:

```c
matrix[1][2]
```

Value at:

```text
Row 1
Column 2
```

Address:

```text
1020
```

Understanding this becomes important in advanced C programming.

# Step 10: Taking User Input

```c
for(int i=0;i<3;i++)
{
    for(int j=0;j<3;j++)
    {
        scanf("%d",&marks[i][j]);
    }
}
```

Input:

```text
85 90 88
75 80 78
92 89 95
```

Stored as matrix.

# Step 11: Finding Row Total

Example:

```c
for(int i=0;i<3;i++)
{
    int total=0;

    for(int j=0;j<3;j++)
    {
        total+=marks[i][j];
    }

    printf("Total=%d\n",total);
}
```

Output:

```text
Student1 Total
Student2 Total
Student3 Total
```

# Step 12: Finding Column Total

Useful for subject-wise reports.

```c
for(int j=0;j<3;j++)
{
    int total=0;

    for(int i=0;i<3;i++)
    {
        total+=marks[i][j];
    }

    printf("%d\n",total);
}
```

# Step 13: Matrix Addition

Matrix A:

```text
1 2
3 4
```

Matrix B:

```text
5 6
7 8
```

Result:

```text
6 8
10 12
```

Code:

```c
result[i][j]=a[i][j]+b[i][j];
```

Very common in:

* Graphics
* Scientific Computing
* Machine Learning

# Step 14: Matrix Multiplication

Important for:

* AI
* Computer Vision
* Neural Networks
* Data Science

Example:

```text
A × B
```

requires:

```text
Rows × Columns calculations
```

This is why understanding multidimensional arrays is essential before entering AI and ML.

# Step 15: Three-Dimensional Arrays

Syntax:

```c
int cube[2][3][4];
```

Meaning:

```text
2 Layers
3 Rows
4 Columns
```

Visualize:

```text
Layer 1
   Table

Layer 2
   Table
```

Used in:

* Image Processing
* Simulations
* Scientific Applications

# Step 16: Real Industry Examples

## School Management

```c
marks[students][subjects]
```

Example:

```c
marks[100][6];
```

100 students

6 subjects

## Sales System

```c
sales[12][30];
```

Meaning:

```text
12 Months
30 Days
```

## Hospital

```c
patients[ward][bed]
```

---

## Cinema Booking

```c
seats[10][20]
```

Meaning:

```text
10 Rows
20 Seats
```

## Chess Board

```c
board[8][8];
```

Every chess engine begins with a matrix-like structure.

# Mentor Insight

Students usually see:

```text
2D Array = Exam Question
```

Software Engineers see:

```text
Rows + Columns
```

Any business data that looks like a table can often be represented using a multidimensional array.

Examples:

```text
Excel Sheet
School Marks
Sales Reports
Inventory Tables
Game Boards
Images
```

All are fundamentally matrix structures.

# Mini Project

## Student Result System

Store:

```text
5 Students
3 Subjects
```

Using:

```c
int marks[5][3];
```

Features:

* Enter Marks
* Display Marks
* Calculate Student Total
* Calculate Subject Average
* Find Topper

# Knowledge Journey So Far

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

Notice how your thinking is evolving:

```text
Single Value
   ↓
Collection
   ↓
Table
   ↓
Entity
   ↓
Persistent Storage
```

This is exactly how software systems are designed.



# Next Transflower Mentor Session

After Multidimensional Arrays, we move to:

# Dynamic Memory Allocation (DMA)

Because until now:

```c
int marks[100];
```

size is fixed at compile time.

Real-world systems don't know beforehand:

```text
How many customers?
How many products?
How many orders?
```

So we must learn:

```c
malloc()
calloc()
realloc()
free()
```

which opens the door to:

```text
Linked Lists
Stacks
Queues
Trees
Databases
Operating Systems
```

and transforms you from a C programmer into a systems-thinking software engineer.
