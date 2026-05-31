### 3. **Enums (Enumerations)**

An `enum` is a user-defined type that consists of a set of named integer constants. Enums make code more readable by using descriptive names instead of numeric values.

**Defining and Using Enums:**

```c
#include <stdio.h>

// Define an enum
enum Weekday {
    SUNDAY,    // Default is 0
    MONDAY,    // 1
    TUESDAY,   // 2
    WEDNESDAY, // 3
    THURSDAY,  // 4
    FRIDAY,    // 5
    SATURDAY   // 6
};

int main() {
    enum Weekday today = WEDNESDAY;

    // Use the enum in a switch statement
    switch (today) {
        case MONDAY:
            printf("Today is Monday.\n");
            break;
        case WEDNESDAY:
            printf("Today is Wednesday.\n");
            break;
        case FRIDAY:
            printf("Today is Friday.\n");
            break;
        default:
            printf("It's a different day.\n");
            break;
    }

    return 0;
}
```