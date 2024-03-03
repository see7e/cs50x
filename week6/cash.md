---
title: Problem Set 6 - Cash
tags: programação, cs50
use: Exercise
languages: Python
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Cash](#cash)
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

# Cash

Implement a program that calculates the minimum number of coins required to give a user change.

```bash
$ python cash.py
Change owed: 0.41
4
```

## Getting Started [#](https://cs50.harvard.edu/x/2023/psets/6/cash//#getting-started)

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/6/sentimental-cash.zip
```

in order to download a ZIP called `sentimental-cash.zip` into your codespace.

Then execute

```bash
unzip sentimental-cash.zip
```

to create a folder called `sentimental-cash`. You no longer need the ZIP file, so you can execute

```bash
rm sentimental-cash.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd sentimental-cash
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
sentimental-cash/ $
```

Execute `ls` by itself, and you should see `cash.py`. If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Specification

-   Write, in a file called `cash.py`, a program that first asks the user how much change is owed and then spits out the minimum number of coins with which said change can be made. You can do this exactly as you did in [Problem Set 1](https://cs50.harvard.edu/x/2023/psets/6/cash/../../1/), except that your program this time should be written in Python, and you should assume that the user will input their change in dollars (e.g., 0.50 dollars instead of 50 cents).
-   Use `get_float` from the CS50 Library to get the user’s input and `print` to output your answer. Assume that the only coins available are quarters (25¢), dimes (10¢), nickels (5¢), and pennies (1¢).
    -   We ask that you use `get_float` so that you can handle dollars and cents, albeit sans dollar sign. In other words, if some customer is owed $9.75 (as in the case where a newspaper costs 25¢ but the customer pays with a $10 bill), assume that your program’s input will be `9.75` and not `$9.75` or `975`. However, if some customer is owed $9 exactly, assume that your program’s input will be `9.00` or just `9` but, again, not `$9` or `900`. Of course, by nature of floating-point values, your program will likely work with inputs like `9.0` and `9.000` as well; you need not worry about checking whether the user’s input is “formatted” like money should be.
-   If the user fails to provide a non-negative value, your program should re-prompt the user for a valid amount again and again until the user complies.
-   Incidentally, so that we can automate some tests of your code, we ask that your program’s last line of output be only the minimum number of coins possible: an integer followed by a newline.

## Usage

Your program should behave per the example below.

```bash
$ python cash.py
Change owed: 0.41
4
```

## Testing

While `check50` is available for this problem, you’re encouraged to first test your code on your own for each of the following.

-   Run your program as `python cash.py`, and wait for a prompt for input. Type in `0.41` and press enter. Your program should output `4`.
-   Run your program as `python cash.py`, and wait for a prompt for input. Type in `0.01` and press enter. Your program should output `1`.
-   Run your program as `python cash.py`, and wait for a prompt for input. Type in `0.15` and press enter. Your program should output `2`.
-   Run your program as `python cash.py`, and wait for a prompt for input. Type in `1.60` and press enter. Your program should output `7`.
-   Run your program as `python cash.py`, and wait for a prompt for input. Type in `23` and press enter. Your program should output `92`.
-   Run your program as `python cash.py`, and wait for a prompt for input. Type in `4.2` and press enter. Your program should output `18`.
-   Run your program as `python cash.py`, and wait for a prompt for input. Type in `-1` and press enter. Your program should reject this input as invalid, as by re-prompting the user to type in another number.
-   Run your program as `python cash.py`, and wait for a prompt for input. Type in `foo` and press enter. Your program should reject this input as invalid, as by re-prompting the user to type in another number.
-   Run your program as `python cash.py`, and wait for a prompt for input. Do not type anything, and press enter. Your program should reject this input as invalid, as by re-prompting the user to type in another number.

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/sentimental/cash
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 cash.py
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/sentimental/cash
```

---

# Walkthrough
> Full code [here](./src/cash.py)

The main differences reside in the `get_cents()` function.

Once a non-negative input value is obtained, it is multiplied by 100 to convert it from dollars to cents. This conversion is necessary because the remaining code operates on integer values representing cents.

The resulting value, representing the amount owed in cents, is stored in the `cents` variable.

```python
def get_cents():
    cents = 0
    while True:
        # Prompt the user for the amount of money
        dollars = get_float("Change owed: ")
        try:
            cents = int(dollars * 100)
            if cents >= 0:
                break
        except ValueError:
            continue
    return cents
```

And the use of `//` operator, which is used instead of the `/` operator for division. The reason for using `//` instead of `/` is to perform integer division.
In Python, the `/` operator performs floating-point division, which means it returns the result as a floating-point number with decimal places. On the other hand, the `//` operator performs integer division, which returns the whole number part of the division result, discarding any decimal places.
For example, if the remaining cents is 67 and we want to calculate the number of quarters, `67 // 25` will give us `2`, which represents the maximum number of quarters we can have from 67 cents.

## Result

```bash
sentimental-cash/ $ python cash.py 
Change owed: 0.41
4
```

## Log Trace 

```bash
sentimental-cash/ $ check50 cs50/problems/2023/x/sentimental/cash
Connecting......
Authenticating...
Verifying......
Preparing.....
Uploading......
Waiting for results............................
Results for cs50/problems/2023/x/sentimental/cash generated by check50 v3.3.7
:) cash.py exists
:) input of 0.41 yields output of 4
:) input of 0.01 yields output of 1
:) input of 0.15 yields output of 2
:) input of 1.6 yields output of 7
:) input of 23 yields output of 92
:) input of 4.2 yields output of 18
:) rejects a negative input like -1
:) rejects a non-numeric input of "foo" 
:) rejects a non-numeric input of "" 
To see the results in your browser go to https://submit.cs50.io/check50/#######################################
```

## Submitted

```bash
sentimental-cash/ $ submit50 cs50/problems/2023/x/sentimental/cash
Connecting......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
./cash.py
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/sentimental/cash to see your results.
```