
# Function Pointers Gaming Application

🧓 *“Years ago, I mentored a group of students building a simple 2D arcade game. It worked great… until they added ‘Pause’ and ‘Game Over’. Suddenly, the `main()` became an if-else jungle. I told them — ‘Games aren’t just graphics. They’re intelligent systems, and at the heart of every game is a **state machine**.’”*

So, let me show you how to build a **game loop** that flows like a real game:
**Start → Playing → Paused → Game Over** — all handled cleanly using **function pointers**.


## 🎮 Game State Machine in C Using Function Pointers

### 🧠 **States We'll Implement:**

1. `Start`
2. `Playing`
3. `Paused`
4. `GameOver`

Each state will:

* Display a message.
* Read user input.
* Transition to the next state using a function pointer.


### 🧱 Step-by-Step Implementation

```c
#include <stdio.h>
#include <string.h>

// Define a function pointer type for states
typedef void (*GameState)();

// Forward declarations
void stateStart();
void statePlaying();
void statePaused();
void stateGameOver();

// The current game state pointer
GameState currentState = stateStart;

// Shared game status
int lives = 3;

void stateStart() {
    printf("\n🎮 [START] Press 'p' to play: ");
    char input;
    scanf(" %c", &input);
    if (input == 'p' || input == 'P') {
        currentState = statePlaying;
    } else {
        printf("Invalid input. Staying at start screen.\n");
    }
}

void statePlaying() {
    printf("\n▶️ [PLAYING] Press 'a' to attack, 'x' to pause, or 'q' to quit: ");
    char input;
    scanf(" %c", &input);

    if (input == 'a') {
        lives--;
        printf("⚔️ You attacked! Lives left: %d\n", lives);
        if (lives <= 0) {
            currentState = stateGameOver;
        }
    } else if (input == 'x') {
        currentState = statePaused;
    } else if (input == 'q') {
        currentState = stateGameOver;
    } else {
        printf("Unknown command.\n");
    }
}

void statePaused() {
    printf("\n⏸️ [PAUSED] Press 'r' to resume or 'q' to quit: ");
    char input;
    scanf(" %c", &input);
    if (input == 'r') {
        currentState = statePlaying;
    } else if (input == 'q') {
        currentState = stateGameOver;
    } else {
        printf("Still paused... Invalid input.\n");
    }
}

void stateGameOver() {
    printf("\n💀 [GAME OVER] Press 's' to start new game or 'e' to exit: ");
    char input;
    scanf(" %c", &input);
    if (input == 's') {
        lives = 3;
        currentState = stateStart;
    } else if (input == 'e') {
        printf("👋 Exiting game. Thanks for playing!\n");
        currentState = NULL;
    } else {
        printf("Invalid option.\n");
    }
}

int main() {
    printf("🎉 Welcome to the Function Pointer Game Machine!\n");

    while (currentState != NULL) {
        currentState();  // Call the current state function
    }

    return 0;
}
```

---

## 🔍 How It Works

* Each state function handles:

  * User input
  * Behavior
  * Transition to the next state
* `main()` doesn't care what state it’s in — it just calls `currentState()`!

---

🧓 *“This is not just a game. It’s a model for **state-based thinking** — something every software engineer needs. From game loops to vending machines, elevators to ATM systems — state machines make your logic clean, modular, and future-ready.”*

---

## 🧑‍🎓 Practice Challenge

Ready to go a step further?

Try adding:

* 🥇 **Score counter**
* ⏳ **Timer simulation**
* 🎵 **Sound effects (just printf for now!)**
* 📜 **Save game logic (use file I/O)**

Let me know — I’ll guide you through each upgrade, mentor-style.
Because in the world of C, when you master **states + function pointers**, you build systems that *think*.

🎮 *Game on, engineer.*
