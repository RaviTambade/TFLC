# Erros

*“Come, young coders,”* the mentor began, walking to the center of the classroom with chalk in one hand and wisdom in the other.

*"Let me tell you a story... the story of Aryan — a passionate young programmer — and the three ghosts he met on his coding quest."*


### 🛑 **Chapter 1: The Guardian of the Gate – Compile-Time Errors**

Once upon a time, Aryan wrote his first C++ program. It was full of excitement, logic, and... well... quite a few mistakes.

He hit **Compile**, dreaming of seeing his output. But alas!

❗️“`error: expected ';' before 'return'`”
❗️“`error: ‘x’ was not declared in this scope`”

The *compiler* appeared like a strict school teacher with a red pen.

> 🧙‍♂️ “Aryan,” the Compiler scolded,
> “You forgot the grammar of our language. Fix your syntax!”

Aryan learned that **Compile-Time Errors** are like entrance exam failures — they stop you before you even enter the battlefield.

🔍 **What he did**:

* He added missing semicolons.
* Corrected variable names.
* Matched brackets properly.

🧠 **Moral**: If your code can’t even compile, it’s like writing a letter with the wrong address — it’ll never reach the reader.


### 🔗 **Chapter 2: The Silent Disconnector – Linking Errors**

After Aryan fixed all his typos, his code compiled. He smiled.

But now\... a new message appeared:

❗️“`undefined reference to 'calculateArea'`”

> “But I declared that function!” Aryan shouted.

And then... the *Linker* emerged — silent, stern, and logical.

> 🧙 “You declared the function, young coder… but where is the definition?”

Aryan realized that he had written:

```c
float calculateArea(float radius);
```

...but forgot to *define* it.

Or, sometimes, he defined it in another file but forgot to compile both files together.

🛠️ **Linking Errors**, the mentor explained, are like building a machine with missing parts — everything’s connected, but one screw is gone, and the engine won’t start.

🧠 **Moral**: Declarations and definitions must both exist. All modules must be included before the final build.


### ⚠️ **Chapter 3: The Trickster in the Shadows – Runtime Errors**

Finally, Aryan managed to compile and link successfully.

He ran the program...

💥 Boom! It crashed.

❗️“`Segmentation fault`”
❗️“`Floating point exception`”

He had just divided by zero without realizing it. Another time, he accessed memory beyond the size of his array.

That’s when the final ghost appeared — **The Runtime Error** — mischievous and often hard to find.

> 🧙 “I live in the hidden corners of logic,” the ghost laughed,
> “Only careful thought and testing can catch me!”

Aryan learned the hard way:

* To check if a file exists before reading.
* To validate user input.
* To test boundary conditions.

🧠 **Moral**: Even a perfect build can fall apart if logic isn’t tight and input isn’t checked.


### 🔁 Mentor’s Summary: The Code Quest Map

```plaintext
┌────────────┐        ┌─────────────┐        ┌─────────────┐
│ Compilation│ ───▶  │   Linking   │ ───▶   │  Execution  │
└────────────┘        └─────────────┘        └─────────────┘
     ⬇                     ⬇                       ⬇
 Compile-Time Errors   Linking Errors         Runtime Errors
```

> 🔧 **Fix Compile-Time**: Review syntax, structure, language rules.
> 🔧 **Fix Linking Errors**: Check all function definitions and object files.
> 🔧 **Fix Runtime Errors**: Think logically, test deeply, handle all possible inputs.


### 🧠 Mentor’s Final Words:

*"In your programming journey, expect to meet all three ghosts. But don’t fear them. Each error is a lesson wrapped in frustration. Unwrap it patiently."*

> “Great coders aren’t those who never err — they are those who know how to debug with grace and learn with every mistake.”
