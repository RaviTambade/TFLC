### 2. **Unions**

A `union` is a data structure that can store different data types in the same memory location. A union allows you to use the same memory location for multiple types, but only one type can be used at a time.

**Defining and Using Unions:**

```c
#include <stdio.h>

// Define a union
union Data {
    int i;
    float f;
    char str[20];
};

int main() {
    union Data data;

    // Store an integer
    data.i = 10;
    printf("data.i = %d\n", data.i);

    // Store a float (overwrites the previous value)
    data.f = 220.5;
    printf("data.f = %f\n", data.f);

    // Store a string (overwrites the previous value)
    sprintf(data.str, "Hello, world!");
    printf("data.str = %s\n", data.str);

    // Note that accessing other members after storing the string will be incorrect
    printf("data.i after storing string = %d\n", data.i); // Undefined behavior
    printf("data.f after storing string = %f\n", data.f); // Undefined behavior

    return 0;
}
```