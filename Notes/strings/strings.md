# Strings

## Dear Students,

Yesterday we learned Arrays.

Today we will learn one of the most widely used concepts in software development:

# Strings in C

Before learning strings, answer this question:

### How do we store a person's age?

```c
int age = 25;
```

### How do we store salary?

```c
float salary = 45000.50;
```

### How do we store a person's name?

Can we write?

```c
char name = 'Ravi';
```

No.

Because a single `char` can store only one character.

```c
char ch = 'R';
```

stores only one letter.

But a name contains multiple characters.

```text
R
a
v
i
```

We need a collection of characters.

This is where Strings come into the picture.

---

# Step 1: What is a String?

A String is an array of characters terminated by a special character called the NULL character.

```c
char name[5] = {'R','a','v','i','\0'};
```

Memory:

```text
+----+----+----+----+----+
| R  | a  | v  | i  |\0  |
+----+----+----+----+----+
```

The last character:

```c
'\0'
```

is extremely important.

Without it, C cannot determine where the string ends.

---

# Step 2: Easier String Initialization

Instead of writing:

```c
char name[5]={'R','a','v','i','\0'};
```

we normally write:

```c
char name[]="Ravi";
```

Compiler automatically adds:

```c
'\0'
```

Memory becomes:

```text
+----+----+----+----+----+
| R  | a  | v  | i  |\0  |
+----+----+----+----+----+
```

---

# Step 3: Printing Strings

For integers:

```c
printf("%d",age);
```

For strings:

```c
printf("%s",name);
```

Example:

```c
#include<stdio.h>

int main()
{
    char name[]="Transflower";

    printf("%s",name);

    return 0;
}
```

Output:

```text
Transflower
```

---

# Step 4: How printf() Reads a String

Suppose:

```c
char name[]="Ravi";
```

Memory:

```text
R a v i \0
```

When printf executes:

```c
printf("%s",name);
```

Internally:

```text
Read R
Read a
Read v
Read i
Stop at \0
```

This is why NULL character is mandatory.

---

# Step 5: String is Actually a Character Array

Remember:

```c
char name[]="Ravi";
```

is actually:

```c
char name[5];
```

Array elements:

```text
name[0]='R'
name[1]='a'
name[2]='v'
name[3]='i'
name[4]='\0'
```

String = Character Array

---

# Step 6: Traversing a String

Just like arrays.

```c
#include<stdio.h>

int main()
{
    char name[]="Ravi";

    for(int i=0;name[i]!='\0';i++)
    {
        printf("%c\n",name[i]);
    }

    return 0;
}
```

Output:

```text
R
a
v
i
```

---

# Step 7: Relationship Between Strings and Pointers

You already know:

```c
int arr[5];
```

Array name stores base address.

Same applies to strings.

```c
char name[]="Ravi";
```

Memory:

```text
1000 1001 1002 1003 1004

 R    a    v    i   \0
```

Array name:

```c
name
```

contains:

```text
1000
```

which is address of first character.

---

# Step 8: Access String Using Pointer

```c
char name[]="Ravi";

char *ptr=name;
```

Printing first character:

```c
printf("%c",*ptr);
```

Output:

```text
R
```

Move pointer:

```c
ptr++;
```

Now:

```c
printf("%c",*ptr);
```

Output:

```text
a
```

---

# Step 9: Printing String Using Pointer

```c
#include<stdio.h>

int main()
{
    char name[]="Transflower";

    char *ptr=name;

    while(*ptr!='\0')
    {
        printf("%c",*ptr);
        ptr++;
    }

    return 0;
}
```

Output:

```text
Transflower
```

---

# Step 10: Taking Input

Single word:

```c
char name[20];

scanf("%s",name);
```

Input:

```text
Ravi
```

Output:

```text
Ravi
```

---

# Step 11: Problem with scanf()

Suppose user enters:

```text
Ravi Tambade
```

scanf reads only:

```text
Ravi
```

because it stops at space.

Therefore:

```c
fgets(name,sizeof(name),stdin);
```

is preferred.

---

# Step 12: Important String Functions

Include:

```c
#include<string.h>
```

---

## strlen()

Find length.

```c
char name[]="Transflower";

printf("%lu",strlen(name));
```

Output:

```text
11
```

NULL character is not counted.

---

## strcpy()

Copy string.

```c
char source[]="Transflower";
char destination[20];

strcpy(destination,source);
```

Result:

```text
destination = Transflower
```

---

## strcat()

Concatenate strings.

```c
char first[30]="Hello ";
char second[]="Students";

strcat(first,second);
```

Output:

```text
Hello Students
```

---

## strcmp()

Compare strings.

```c
strcmp("Ravi","Ravi")
```

Returns:

```text
0
```

Meaning both strings are equal.

---

# Step 13: Real Industry Example

## Login System

User enters:

```text
admin
```

Stored username:

```c
char storedUser[]="admin";
```

Validation:

```c
if(strcmp(inputUser,storedUser)==0)
{
    printf("Valid User");
}
```

This is how login systems compare usernames and passwords.

---

# Step 14: Mini Project

## Student Information System

Store:

```c
Student Name
City
Course
```

Example:

```c
char studentName[50];
char city[30];
char course[30];
```

Operations:

* Accept Details
* Display Details
* Calculate Name Length
* Compare Two Names

---

# Step 15: Mentor Insight

Many students think:

```text
Arrays Completed
Strings Completed
```

No.

Think deeper.

```text
Pointers
   ↓
Arrays
   ↓
Character Arrays
   ↓
Strings
   ↓
Structures
   ↓
Files
   ↓
Dynamic Memory
   ↓
Data Structures
```

Everything is connected.

When you type a URL:

```text
www.transflower.in
```

it is a string.

When you enter a password:

```text
Secret123
```

it is a string.

When you send a WhatsApp message:

```text
Hello Friend
```

it is a string.

When a browser sends JSON data:

```json
{
   "name":"Ravi"
}
```

all text data is handled using strings.

---

# Transflower Practice Roadmap

### Exercise 1

Print each character of a string.

### Exercise 2

Find string length without using `strlen()`.

### Exercise 3

Copy one string into another without using `strcpy()`.

### Exercise 4

Reverse a string.

Input:

```text
Ravi
```

Output:

```text
ivaR
```

### Exercise 5

Check palindrome.

Input:

```text
MADAM
```

Output:

```text
Palindrome
```

### Exercise 6

Build Login Application

Features:

* Username
* Password
* Validation using `strcmp()`

---

## Next Transflower Mentor Session

After **Strings**, we move to:

### Structures (`struct`)

Because real-world entities such as:

* Student
* Customer
* Product
* Employee
* Order

cannot be represented using only arrays and strings.

Structures are the first step toward designing real business applications and object-oriented thinking.
