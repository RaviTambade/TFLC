

### 4. **Typedef**

`typedef` is used to create an alias for an existing type, which can make complex type definitions easier to manage and more readable.

**Using Typedef:**

```c
#include <stdio.h>

// Define a new type using typedef
typedef struct {
    char name[50];
    int age;
} Person;

// Function to print person details
void printPerson(Person p) {
    printf("Name: %s\n", p.name);
    printf("Age: %d\n", p.age);
}

int main() {
    // Declare and initialize a Person
    Person john = {"John Doe", 30};

    printPerson(john);

    return 0;
}
```