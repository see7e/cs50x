---
title: Lab 2 - Scrabble
tags: studies, programação, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Lab 2: Scrabble #](#lab-2-scrabble-)
  - [Getting Started](#getting-started)
  - [Background](#background)
  - [Implementation Details](#implementation-details)
    - [Hints](#hints)
    - [How to Test Your Code](#how-to-test-your-code)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Check Style](#check-style)
  - [Submited](#submited)

</details>

---
# Lab 2: Scrabble [#](https://cs50.harvard.edu/x/2023/labs/2/#lab-2-scrabble)
> Full code [here](./src/lab2.c)

You are welcome to collaborate with one or two classmates on this lab, though it is expected that every student in any such group contribute equally to the lab.

Determine which of two Scrabble words is worth more.

```bash
$ ./scrabble
Player 1: COMPUTER
Player 2: science
Player 1 wins!
```

## Getting Started

Open [VS Code](https://code.cs50.io/).

Start by clicking inside your terminal window, then execute `cd` by itself. You should find that its “prompt” resembles the below.

```bash
$
```

Click inside of that terminal window and then execute

```bash
wget https://cdn.cs50.net/2022/fall/labs/2/scrabble.zip
```

followed by Enter in order to download a ZIP called `scrabble.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!

Now execute

```bash
unzip scrabble.zip
```

to create a folder called `scrabble`. You no longer need the ZIP file, so you can execute

```bash
rm scrabble.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd scrabble
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
scrabble/ $
```

If all was successful, you should execute

```bash
ls
```

and you should see a file called `scrabble.c`. Open that file by executing the below:

```bash
code scrabble.c
```

If you run into any trouble, follow these same steps steps again and see if you can determine where you went wrong!

## Background

In the game of [Scrabble](https://scrabble.hasbro.com/en-us/rules), players create words to score points, and the number of points is the sum of the point values of each letter in the word.

| A   | B   | C   | D   | E   | F   | G   | H   | I   | J   | K   | L   | M   | N   | O   | P   | Q   | R   | S   | T   | U   | V   | W   | X   | Y   | Z   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 3   | 3   | 2   | 1   | 4   | 2   | 4   | 1   | 8   | 5   | 1   | 3   | 1   | 1   | 3   | 10  | 1   | 1   | 1   | 1   | 4   | 4   | 8   | 4   | 10  |


For example, if we wanted to score the word `Code`, we would note that in general Scrabble rules, the `C` is worth `3` points, the `o` is worth `1` point, the `d` is worth `2` points, and the `e` is worth `1` point. Summing these, we get that `Code` is worth `3 + 1 + 2 + 1 = 7` points.

## Implementation Details

Complete the implementation of `scrabble.c`, such that it determines the winner of a short scrabble-like game, where two players each enter their word, and the higher scoring player wins.

-   Notice that we’ve stored the point values of each letter of the alphabet in an integer array named `POINTS`.
    -   For example, `A` or `a` is worth 1 point (represented by `POINTS[0]`), `B` or `b` is worth 3 points (represented by `POINTS[1]`), etc.

-   Notice that we’ve created a prototype for a helper function called `compute_score()` that takes a string as input and returns an `int`. Whenever we would like to assign point values to a particular word, we can call this function. Note that this prototype is required for C to know that `compute_score()` exists later in the program.

-   In `main()`, the program prompts the two players for their words using the `get_string()` function. These values are stored inside variables named `word1` and `word2`.

-   In `compute_score()`, your program should compute, using the `POINTS` array, and return the score for the string argument. Characters that are not letters should be given zero points, and uppercase and lowercase letters should be given the same point values.
    -   For example, `!` is worth `0` points while `A` and `a` are both worth `1` point.
    -   Though Scrabble rules normally require that a word be in the dictionary, no need to check for that in this problem!

-   In `main()`, your program should print, depending on the players’ scores, `Player 1 wins!`, `Player 2 wins!`, or `Tie!`.

### Hints

-   You may find the functions `isupper()` and `islower()` to be helpful to you. These functions take in a character as the argument and return a boolean.

-   To find the value at the `n`th index of an array called `arr`, we can write `arr[n]`. We can apply this to strings as well, as strings are arrays of characters.

-   Recall that computers represent characters using [ASCII](https://asciitable.com/), a standard that represents each character as a number.

### How to Test Your Code

Your program should behave per the examples below.

```bash
$ ./scrabble
Player 1: Question?
Player 2: Question!
Tie!
```

```bash
$ ./scrabble
Player 1: Oh,
Player 2: hai!
Player 2 wins!
```

```bash
$ ./scrabble
Player 1: COMPUTER
Player 2: science
Player 1 wins!
```

```bash
$ ./scrabble
Player 1: Scrabble
Player 2: wiNNeR
Player 1 wins!
```

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/labs/2023/x/scrabble
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 scrabble.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/labs/2023/x/scrabble
```

---

# Walkthrough

As you unzip the folder, this is the already done code.

```c
#include <ctype.h>
#include <cs50.h>
#include <stdio.h>
#include <string.h>

// Points assigned to each letter of the alphabet
int POINTS[] = {1, 3, 3, 2, 1, 4, 2, 4, 1, 8, 5, 1, 3, 1, 1, 3, 10, 1, 1, 1, 1, 4, 4, 8, 4, 10};

int compute_score(string word);

int main(void)
{
    // Get input words from both players
    string word1 = get_string("Player 1: ");
    string word2 = get_string("Player 2: ");

    // Score both words
    int score1 = compute_score(word1);
    int score2 = compute_score(word2);

    // TODO: Print the winner
}

int compute_score(string word)
{
    // TODO: Compute and return score for string
}
```

As all the scores follows the alphabetical order in the `POINTS[]` array, all we need to do is convert the letter in the string to a relative positional index, where `a` is the number `97` and `A` is `65`, from **ASCII** table.

```c
// uppercase lettrs
if (word[i] >= 65 && word[i] <= 90)
{
  score += POINTS[word[i] - 65];
  //printf("%i\n", score);
}
//lowercase lettrs
else if (word[i] >= 97 && word[i] <= 122)
{
  score += POINTS[word[i] - 97];
  //printf("%i\n", score);
}
```


This code, inside a loop ( `while (word[i] != '\0')`) that verifies if we've reached the end of the word. 

## Result

```bash
scrabble/ $ make scrabble 
scrabble/ $ ./scrabble 
Player 1: Question?
Player 2: Question!
Tie!
scrabble/ $ ./scrabble 
Player 1: Oh,
Player 2: hai!
Player 2 wins!
scrabble/ $ ./scrabble 
Player 1: COMPUTER
Player 2: science
Player 1 wins!
scrabble/ $ ./scrabble 
Player 1: Scrabble
Player 2: wiNNeR
Player 1 wins!
```

## Log Trace 

```bash
scrabble/ $ check50 cs50/labs/2023/x/scrabble
Connecting.......
Authenticating...
Verifying.........
Preparing.............
Uploading..........
Waiting for results...............................................
Results for cs50/labs/2023/x/scrabble generated by check50 v3.3.7
:) scrabble.c exists
:) scrabble.c compiles
:) handles letter cases correctly
:) handles punctuation correctly
:) correctly identifies 'Question?' and 'Question!' as a tie
:) correctly identifies 'drawing' and 'illustration' as a tie
:) correctly identifies 'hai!' as winner over 'Oh,'
:) correctly identifies 'COMPUTER' as winner over 'science'
:) correctly identifies 'Scrabble' as winner over 'wiNNeR'
:) correctly identifies 'pig' as winner over 'dog'
:) correctly identifies 'Skating!' as winner over 'figure?'
To see the results in your browser go to https://submit.cs50.io/check50/####################################
```

## Check Style 

```bash
scrabble/ $ style50 scrabble.c
Results generated by style50 v2.7.5
Looks good!
```

## Submited

```bash
scrabble/ $ submit50 cs50/labs/2023/x/scrabble
Connecting.......
Authenticating...
Verifying.......
Preparing............
Files that will be submitted:
./scrabble.c
Files that won't be submitted:
./scrabble
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading..........
Go to https://submit.cs50.io/users/see7e/cs50/labs/2023/x/scrabble to see your results.
```