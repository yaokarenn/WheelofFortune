# Wheel of Fortune (Text-Based C++)

A command-line, single-player adaptation of the classic game show *Wheel of Fortune*, written in C++. The game challenges players to solve hidden word puzzles across various categories by spinning a wheel for cash values, buying vowels, and avoiding penalties like Bankrupt or Lose a Turn.

---

## Gameplay Overview

The game runs for 3 complete rounds, with a new puzzle selected randomly for each round. 

* **Puzzle Presentation:** Puzzles are displayed as a series of underscores. Non-alphabetic characters (spaces, exclamation points, punctuation) are preserved and visible from the start
* **Clues/Categories:** The system automatically determines and displays the category based on the active puzzle. Categories include **Holidays**, **States**, and **World Events**
* **Player Stats:** The player starts with 10 misses and a bank of $0. The current score and remaining misses are displayed at the beginning of every turn
* **Win/Loss Conditions:** A round ends successfully when the puzzle is solved. If the miss counter drops to 0, the game ends

---

## Game Actions

During each turn, the player selects one of three options:

### 1. Spin the Wheel
* The wheel lands on a random value from a predefined distribution of cash amounts, Bankrupt, or Lose a Turn
* Landing on **Lose a Turn** costs the player 1 miss
* Landing on **Bankrupt** resets the player's current bank to $0 and costs 1 miss
* Landing on a dollar amount allows the player to guess a consonant. A correct guess reveals the letters and adds the spin value to the bank. An incorrect guess or guessing a vowel during a spin results in a penalty and a lost miss

### 2. Buy a Vowel
* If the player has at least $250 in their bank, they can purchase a vowel (A, E, I, O, U)
* A successful vowel guess reveals its placements in the puzzle. An incorrect vowel guess costs the player 1 miss

### 3. Solve the Puzzle
* The player can attempt to type out the entire solution
* The system evaluates the guess while accounting for case-insensitivity
* A correct solution wins the round and secures the banked amount. An incorrect guess penalizes the player by 1 miss

---

## Technical Concepts Covered

This project serves as a practical application of foundational computer science and C++ concepts:

* **String Manipulation:** Features custom functions to dynamically mask words into hidden characters while preserving punctuation, alongside case-insensitive string parsing
* **Input Buffer Management:** Solves the classic C++ conflict between standard extraction (`cin >>`) and line-reading (`getline`) streams by managing trailing newline characters in the input buffer
* **Randomization:** Uses time-seeded pseudo-random number generation (`srand` and `rand`) to ensure unique puzzle selection and wheel spins every playthrough
* **Control Flow Architecture:** Implements nested loops (`do-while` loops) to cleanly separate the lifecycle of a single turn, an entire round, and the overall 3-round game structure

---

### Core Functions
* `string convert2U(string p)`: Takes the secret puzzle string and returns a version where all alphabetic characters are masked with underscores
* `void display(string p)`: Iterates through strings to format and display characters separated by clean spacing for maximum readability
* `int main()`: Contains the primary game engine, state trackers (misses, rounds, bank accounts), and the conditional logic managing player choices
