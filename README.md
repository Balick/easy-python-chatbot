# Simple Chatbot — JetBrains Academy (Hyperskill) Project

A small console-based chatbot written in Python. This project walks you through building an interactive assistant that greets the user, asks for their name, guesses their age using remainders, counts, quizzes the user on a short question, and finishes with a friendly goodbye.

This implementation follows the JetBrains Academy (Hyperskill) "Simple Chatty Bot" tutorial and is intended for learning basic Python concepts: functions, input/output, loops, and simple algorithms.

## Contents

- bot.py (suggested name) — the main script containing:
  - `greet(bot_name, birth_year)`
  - `remind_name()`
  - `guess_age()`
  - `count()`
  - `test()`
  - `end()`
- README.md — this file

## Requirements

- Python 3.x

No external libraries are required.

## How to run

1. Save the provided code in a file, e.g. `bot.py`.
2. Run the script from a terminal:

   ```bash
   python3 bot.py
   ```

3. Interact with the assistant by following on-screen prompts.

## Example session

```text
Hello! My name is Aid.
I was created in 2025.
Please, remind me your name.
> Alice
What a great name you have, Alice!
Let me guess your age.
Enter remainders of dividing your age by 3, 5 and 7.
> 1
> 2
> 1
Your age is 22; that's a good time to start programming!
Now I will prove to you that I can count to any number you want.
> 3
0 !
1 !
2 !
3 !
Let's test your programming knowledge.
Why do we use methods?
1. To repeat a statement multiple times.
2. To decompose a program into several small subroutines.
3. To determine the execution time of a program.
4. To interrupt the execution of a program.
> 1
Please, try again.
> 2
Congratulations, have a nice day!
```

## What the program does (function summary)

- `greet(bot_name, birth_year)`  
  Prints a greeting with the bot's name and creation year.

- `remind_name()`  
  Asks the user for their name and responds with a compliment.

- `guess_age()`  
  Prompts the user for the remainders of their age when divided by 3, 5, and 7.  
  It computes the age using a simple remainder-based formula:

  ```
  age = (rem3 * 70 + rem5 * 21 + rem7 * 15) % 105
  ```

  (This works because 70 ≡ 1 (mod 3), 21 ≡ 1 (mod 5), 15 ≡ 1 (mod 7) and 105 = 3*5*7.)

- `count()`  
  Reads a non-negative integer and counts from 0 up to that number, printing each value.

- `test()`  
  Prints a quiz question (loaded from a small `questions` dictionary) and displays the answer choices.  
  The function loops until the user selects the correct option (currently the correct option is `2` in the provided data). After each wrong answer it prints "Please, try again." The function returns control when the correct option is chosen.

- `end()`  
  Prints a closing message.

## Data

The script includes a minimal questions dictionary:

```python
questions = {
    "Why do we use methods?": [
        "To repeat a statement multiple times.",
        "To decompose a program into several small subroutines.",
        "To determine the execution time of a program.",
        "To interrupt the execution of a program."
    ]
}
```

The current correct answer (in the provided code) is option 2.

## Notes, quirks, and suggestions for improvement

- Input validation is minimal. If the user enters non-integer input where integers are expected, the script will raise a ValueError. Consider adding try/except blocks to handle invalid input gracefully.
- The quiz loop currently prints "Please, try again." immediately after the user enters an answer, even if it is correct. You may want to print that only when the answer is incorrect, and print a confirmation or next step when the answer is correct.
- `guess_age()` relies on the user providing valid remainders (0..2 for mod 3, 0..4 for mod 5, 0..6 for mod 7). Consider validating these ranges.
- Extend the `questions` structure to include multiple questions or a correct-answer index explicitly (e.g., store tuples of `(choices, correct_index)`).
- Add unit tests that cover input validation, the age-guessing algorithm, and the quiz logic (mocking input/output).
- Add command-line options to customize bot name, birth year, or to load questions from a file.
- Optionally persist user progress or preferences (e.g., to a JSON file).

## Where this comes from

This project follows the JetBrains Academy / Hyperskill "Simple Chatty Bot" learning track. It is intended as an educational exercise to practice basic Python features.
<https://hyperskill.org/projects/97>
