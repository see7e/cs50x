---
title: Problem Set 6 - Readability
tags: programação, cs50
use: Exercise
languages: Python
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Readability](#readability)
  - [Getting Started #](#getting-started-)
  - [Specification](#specification)
  - [Usage](#usage)
  - [Testing](#testing)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Submitted](#submitted)

</details>

---

# Readability

Implement a program that computes the approximate grade level needed to comprehend some text, per the below.

```bash
$ python readability.py
Text: Congratulations! Today is your day. You're off to Great Places! You're off and away!
Grade 3
```

## Getting Started [#](https://cs50.harvard.edu/x/2023/psets/6/readability//#getting-started)

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/6/sentimental-readability.zip
```

in order to download a ZIP called `sentimental-readability.zip` into your codespace.

Then execute

```bash
unzip sentimental-readability.zip
```

to create a folder called `sentimental-readability`. You no longer need the ZIP file, so you can execute

```bash
rm sentimental-readability.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd sentimental-readability
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
sentimental-readability/ $
```

Execute `ls` by itself, and you should see `readability.py`. If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Specification

-   Write, in a file called `readability.py`, a program that first asks the user to type in some text, and then outputs the grade level for the text, according to the Coleman-Liau formula, exactly as you did in [Problem Set 2](https://cs50.harvard.edu/x/2023/psets/6/readability/../../2/), except that your program this time should be written in Python.
    -   Recall that the Coleman-Liau index is computed as `0.0588 * L - 0.296 * S - 15.8`, where `L` is the average number of letters per 100 words in the text, and `S` is the average number of sentences per 100 words in the text.
-   Use `get_string` from the CS50 Library to get the user’s input, and `print` to output your answer.
-   Your program should count the number of letters, words, and sentences in the text. You may assume that a letter is any lowercase character from `a` to `z` or any uppercase character from `A` to `Z`, any sequence of characters separated by spaces should count as a word, and that any occurrence of a period, exclamation point, or question mark indicates the end of a sentence.
-   Your program should print as output `"Grade X"` where `X` is the grade level computed by the Coleman-Liau formula, rounded to the nearest integer.
-   If the resulting index number is 16 or higher (equivalent to or greater than a senior undergraduate reading level), your program should output `"Grade 16+"` instead of giving the exact index number. If the index number is less than 1, your program should output `"Before Grade 1"`.

## Usage

Your program should behave per the example below.

```bash
$ python readability.py
Text: Congratulations! Today is your day. You're off to Great Places! You're off and away!
Grade 3
```

## Testing

While `check50` is available for this problem, you’re encouraged to first test your code on your own for each of the following.

-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `One fish. Two fish. Red fish. Blue fish.` and press enter. Your program should output `Before Grade 1`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `Would you like them here or there? I would not like them here or there. I would not like them anywhere.` and press enter. Your program should output `Grade 2`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `Congratulations! Today is your day. You're off to Great Places! You're off and away!` and press enter. Your program should output `Grade 3`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `Harry Potter was a highly unusual boy in many ways. For one thing, he hated the summer holidays more than any other time of year. For another, he really wanted to do his homework, but was forced to do it in secret, in the dead of the night. And he also happened to be a wizard.` and press enter. Your program should output `Grade 5`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `In my younger and more vulnerable years my father gave me some advice that I've been turning over in my mind ever since.` and press enter. Your program should output `Grade 7`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `Alice was beginning to get very tired of sitting by her sister on the bank, and of having nothing to do: once or twice she had peeped into the book her sister was reading, but it had no pictures or conversations in it, "and what is the use of a book," thought Alice "without pictures or conversation?"` and press enter. Your program should output `Grade 8`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `When he was nearly thirteen, my brother Jem got his arm badly broken at the elbow. When it healed, and Jem's fears of never being able to play football were assuaged, he was seldom self-conscious about his injury. His left arm was somewhat shorter than his right; when he stood or walked, the back of his hand was at right angles to his body, his thumb parallel to his thigh.` and press enter. Your program should output `Grade 8`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `There are more things in Heaven and Earth, Horatio, than are dreamt of in your philosophy.` and press enter. Your program should output `Grade 9`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `It was a bright cold day in April, and the clocks were striking thirteen. Winston Smith, his chin nuzzled into his breast in an effort to escape the vile wind, slipped quickly through the glass doors of Victory Mansions, though not quickly enough to prevent a swirl of gritty dust from entering along with him.` and press enter. Your program should output `Grade 10`.
-   Run your program as `python readability.py`, and wait for a prompt for input. Type in `A large class of computational problems involve the determination of properties of graphs, digraphs, integers, arrays of integers, finite families of finite sets, boolean formulas and elements of other countable domains.` and press enter. Your program should output `Grade 16+`.

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/sentimental/readability
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 readability.py
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/sentimental/readability
```

---

# Walkthrough
> Full code [here](./src/readability.py)

The code could be divided in two blocs:
1. Counting the number of elements
  ```c
  while (text[i] != '\0')
  {
    // uppercase or lowercase lettrs
    if ((text[i] >= 65 && text[i] <= 90) || (text[i] >= 97 && text[i] <= 122))
    {
      letters++;
    }
    // spaces between words
    else if (text[i] == 32)
    {
      words++;
    }
    // sentences (. ! ?)
    else if (text[i] == 46 || text[i] == 33 || text[i] == 63)
    {
      sentences++;
    }
    i++;
  }
  ```

  Converts to:

  1. Counting the number of letters:
  ```python
  letters = sum(1 for char in text if char.isalpha())
  ```
  
  This uses a generator expression to iterate over each character (`char`) in the `text` variable. The `char.isalpha()` condition checks if the character is an alphabet letter. If it is, the generator expression yields a value of 1, indicating that it is a letter. Finally, the `sum` function adds up all the 1's, giving us the total count of letters.

  2. Counting the number of words:
  ```python
  words = len(text.split())
  ```
  
  This splits the `text` variable into a list of words using the `split` method. By default, the `split` method splits the text at whitespace characters. The `len` function then returns the number of elements in the resulting list, which corresponds to the number of words in the text.

  3. Counting the number of sentences:
  ```python
  sentences = sum(1 for char in text if char in ['.', '!', '?'])
  ```
  
  Similar to the first point, this line uses a generator expression to iterate over each character in the `text` variable. The condition `char in ['.', '!', '?']` checks if the character is a period, exclamation mark, or question mark. If it is, the generator expression yields a value of 1. Finally, the `sum` function adds up all the 1's, giving us the total count of sentences.

2. Calculating the floating points:

  ```c
  // Caulculate the floating points
  float L = ((float)letters / (float)words) * 100;
  float S = ((float)sentences / (float)words) * 100;
  float subindex = 0.0588 * L - 0.296 * S - 15.8;

  int index = round(subindex);
  ```

  To:

  ```python
  # Calculate the floating points
  L = (letters / words) * 100.00
  S = (sentences / words) * 100.00
  subindex = 0.0588 * L - 0.296 * S - 15.8

  index = round(subindex)
  ```

  This is nothing but the same, only with the change of the syntax.


## Result

```bash
sentimental-readability/ $ python readability.py 
Text: Congratulations! Today is your day. You're off to Great Places! You're off and away!
Grade 3
```

## Log Trace 

```bash
sentimental-readability/ $ check50 cs50/problems/2023/x/sentimental/readability
Connecting......
Authenticating...
Verifying........
Preparing.....
Uploading.......
Waiting for results............................
Results for cs50/problems/2023/x/sentimental/readability generated by check50 v3.3.7
:) readability.py exists.
:) handles single sentence with multiple words
:) handles punctuation within a single sentence
:) handles more complex single sentence
:) handles multiple sentences
:) handles multiple more complex sentences
:) handles longer passages
:) handles questions in passage
:) handles reading level before Grade 1
:) handles reading level at Grade 16+
To see the results in your browser go to https://submit.cs50.io/check50/
```

## Submitted

```bash
sentimental-readability/ $ submit50 cs50/problems/2023/x/sentimental/readability
Connecting.......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
./readability.py
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading........
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/sentimental/readability to see your results.
```