---
title: Problem Set 1 - Cash Credit
tags: programação, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Cash#](#cash)
  - [Getting Started](#getting-started)
  - [Greedy Algorithms](#greedy-algorithms)
  - [Implementation Details](#implementation-details)
    - [How to Test Your Code](#how-to-test-your-code)
  - [How to Submit](#how-to-submit)
- [Credit#](#credit)
  - [Getting Started](#getting-started-1)
  - [Credit Cards](#credit-cards)
  - [Luhn’s Algorithm](#luhns-algorithm)
  - [Implementation Details](#implementation-details-1)
    - [How to Test Your Code](#how-to-test-your-code-1)
  - [How to Submit](#how-to-submit-1)
- [Walkthrough - Cash](#walkthrough---cash)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Check Style](#check-style)
  - [Submited](#submited)
- [Walkthrough - Credit](#walkthrough---credit)
  - [Result](#result-1)
  - [Log Trace](#log-trace-1)
  - [Check Style](#check-style-1)
  - [Submited](#submited-1)

</details>

---

# Cash[#](https://cs50.harvard.edu/x/2023/psets/1/cash//#cash)

## Getting Started

Open [VS Code](https://code.cs50.io/).

Start by clicking inside your terminal window, then execute `cd` by itself. You should find that its “prompt” resembles the below.

```bash
$
```

Click inside of that terminal window and then execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/1/cash.zip
```

followed by Enter in order to download a ZIP called `cash.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!

Now execute

```bash
unzip cash.zip
```

to create a folder called `cash`. You no longer need the ZIP file, so you can execute and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

```bash
rm cash.zip
```

Now type

```bash
cd cash
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
cash/ $
```

If all was successful, you should execute

```bash
ls
```

and see a file named `cash.c`. Executing `code cash.c` should open the file where you will type your code for this problem set. If not, retrace your steps and see if you can determine where you went wrong!

## Greedy Algorithms

![US coins](https://cs50.harvard.edu/x/2023/psets/1/cash//coins.jpg)

<details> <summary>In a simpler way</summary>

When a cashier needs to give change to a customer, they want to use as few coins as possible. This is where greedy algorithms come in. A greedy algorithm is a way to solve a problem by always choosing the best immediate solution. For example, if a customer needs 41 cents in change, the cashier would first give them a quarter because it's the biggest coin and gets them closer to 0 cents faster than any other coin. Then they would give a dime, a nickel, and a penny to make a total of four coins.

</details>

When making change, odds are you want to minimize the number of coins you’re dispensing for each customer, lest you run out (or annoy the customer!). Fortunately, computer science has given cashiers everywhere ways to minimize numbers of coins due: greedy algorithms.

According to the National Institute of Standards and Technology (NIST), a greedy algorithm is one
> “that always takes the best immediate, or local, solution while finding an answer. Greedy algorithms find the overall, or globally, optimal solution for some optimization problems, but may find less-than-optimal solutions for some instances of other problems.”

What’s all that mean? Well, suppose that a cashier owes a customer some change and in that cashier’s drawer are quarters (`25¢`), dimes (`10¢`), nickels (`5¢`), and pennies (`1¢`). The problem to be solved is to decide which coins and how many of each to hand to the customer. Think of a “greedy” cashier as one who wants to take the biggest bite out of this problem as possible with each coin they take out of the drawer. For instance, if some customer is owed `41¢`, the biggest first (i.e., best immediate, or local) bite that can be taken is `25¢`. (That bite is “best” inasmuch as it gets us closer to `0¢` faster than any other coin would.) Note that a bite of this size would whittle what was a `41¢` problem down to a `16¢` problem, since `41 - 25 = 16`. That is, the remainder is a similar but smaller problem. Needless to say, another `25¢` bite would be too big (assuming the cashier prefers not to lose money), and so our greedy cashier would move on to a bite of size `10¢`, leaving him or her with a `6¢` problem. At that point, greed calls for one `5¢` bite followed by one `1¢` bite, at which point the problem is solved. The customer receives one quarter, one dime, one nickel, and one penny: four coins in total.

It turns out that this greedy approach (i.e., algorithm) is not only locally optimal but also globally so for America’s currency (and also the European Union’s). That is, so long as a cashier has enough of each coin, this largest-to-smallest approach will yield the fewest coins possible. How few? Well, you tell us!

## Implementation Details

In `cash.c`, we’ve implemented most (but not all!) of a program that prompts the user for the number of cents that a customer is owed and then prints the smallest number of coins with which that change can be made. 

Indeed, `main` is already implemented for you. But notice how `main` calls several functions that aren’t yet implemented!

One of those functions, `get_cents`, takes no arguments (as indicated by `void`) and returns an `int`. The rest of the functions all take one argument, an `int`, and also return an `int`. All of them currently return `0` so that the code will compile. But you’ll want to replace every `TODO` and `return 0;` with your own code. Specifically, complete the implementation of those functions as follows:

-   Implement `get_cents` in such a way that the function prompts the user for a number of cents using `get_int` and then returns that number as an `int`. If the user inputs a negative `int`, your code should prompt the user again. (But you don’t need to worry about the user inputting, e.g., a `string`, as `get_int` will take care of that for you.) Odds are you’ll find a `do while` loop of help, as in [`mario.c`](https://cdn.cs50.net/2022/fall/lectures/1/src1/mario8.c?highlight)!
-   Implement `calculate_quarters` in such a way that the function calculates (and returns as an `int`) how many quarters a customer should be given if they’re owed some number of cents. For instance, if `cents` is `25`, then `calculate_quarters` should return `1`. If `cents` is `26` or `49` (or anything in between, then `calculate_quarters` should also return `1`. If `cents` is `50` or `74` (or anything in between), then `calculate_quarters` should return `2`. And so forth.
-   Implement `calculate_dimes` in such a way that the function calculates the same for dimes.
-   Implement `calculate_nickels` in such a way that the function calculates the same for nickels.
-   Implement `calculate_pennies` in such a way that the function calculates the same for pennies.

```c
#include <cs50.h>
#include <stdio.h>

int get_cents(void);
int calculate_quarters(int cents);
int calculate_dimes(int cents);
int calculate_nickels(int cents);
int calculate_pennies(int cents);

int main(void)
{
    // Ask how many cents the customer is owed
    int cents = get_cents();

    // Calculate the number of quarters to give the customer
    int quarters = calculate_quarters(cents);
    cents = cents - quarters * 25;

    // Calculate the number of dimes to give the customer
    int dimes = calculate_dimes(cents);
    cents = cents - dimes * 10;

    // Calculate the number of nickels to give the customer
    int nickels = calculate_nickels(cents);
    cents = cents - nickels * 5;

    // Calculate the number of pennies to give the customer
    int pennies = calculate_pennies(cents);
    cents = cents - pennies * 1;

    // Sum coins
    int coins = quarters + dimes + nickels + pennies;

    // Print total number of coins to give the customer
    printf("%i\n", coins);
}

int get_cents(void)
{
    // TODO
    return 0;
}

int calculate_quarters(int cents)
{
    // TODO
    return 0;
}

int calculate_dimes(int cents)
{
    // TODO
    return 0;
}

int calculate_nickels(int cents)
{
    // TODO
    return 0;
}

int calculate_pennies(int cents)
{
    // TODO
    return 0;
}
```

Note that, unlike functions that only have side effects, functions that return a value should do so explicitly with `return`!

Take care not to modify the distribution code itself, only replace the given `TODO`s and the subsequent `return` value! Note too that, recalling the idea of abstraction, each of your calculate functions should accept any value of `cents` , not just those values that the greedy algorithm might suggest. If `cents` is 85, for example, `calculate_dimes` should return 8.

Hint

-   Recall that there are several sample programs in Week 1’s [Source Code](https://cdn.cs50.net/2022/fall/lectures/1/src1/) that illustrate how functions can return a value.

Your program should behave per the examples below.

```bash
$ ./cash
Change owed: 41
4
```

```bash
$ ./cash
Change owed: -41
Change owed: foo
Change owed: 41
4
```

### How to Test Your Code

For this program, try testing your code manually–it’s good practice:

-   If you input `-1`, does your program prompts you again?
-   If you input `0`, does your program output `0`?
-   If you input `1`, does your program output `1` (i.e., one penny)?
-   If you input `4`, does your program output `4` (i.e., four pennies)?
-   If you input `5`, does your program output `1` (i.e., one nickel)?
-   If you input `24`, does your program output `6` (i.e., two dimes and four pennies)?
-   If you input `25`, does your program output `1` (i.e., one quarter)?
-   If you input `26`, does your program output `2` (i.e., one quarter and one penny)?
-   If you input `99`, does your program output `9` (i.e., three quarters, two dimes, and four pennies)?

You can also execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/cash
```

Is `check50` failing to compile your code?

Be sure you have only modified those parts of the program marked as `TODO`. If you modify the `main` function or add any global variables, for example, your code may **fail to compile**. `check50` will test your five functions independently, beyond just checking for the final answer.

And execute the below to evaluate the style of your code using `style50`.

```bash
style50 cash.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/cash
```

---

# Credit[#](https://cs50.harvard.edu/x/2023/psets/1/credit//#credit)

## Getting Started

Open [VS Code](https://code.cs50.io/).

Start by clicking inside your terminal window, then execute `cd` by itself. You should find that its “prompt” resembles the below.

```bash
$
```

Click inside of that terminal window and then execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/1/credit.zip
```

followed by Enter in order to download a ZIP called `credit.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!

Now execute

```bash
unzip credit.zip
```

to create a folder called `credit`. You no longer need the ZIP file, so you can execute

```bash
rm credit.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd credit
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
credit/ $
```

If all was successful, you should execute

```bash
ls
```

and see a file named `credit.c`. Executing `code credit.c` should open the file where you will type your code for this problem set. If not, retrace your steps and see if you can determine where you went wrong!

## Credit Cards

A credit (or debit) card, of course, is a plastic card with which you can pay for goods and services. Printed on that card is a number that’s also stored in a database somewhere, so that when your card is used to buy something, the creditor knows whom to bill. There are a lot of people with credit cards in this world, so those numbers are pretty long:
- American Express uses 15-digit numbers,
- MasterCard uses 16-digit numbers,
- Visa uses 13- and 16-digit numbers. 

And those are decimal numbers (0 through 9), not binary, which means, for instance, that American Express could print as many as 10[^15] = 1,000,000,000,000,000 unique cards! (That’s, um, a quadrillion.)

Actually, that’s a bit of an exaggeration, because credit card numbers actually have some structure to them. 
- **All American Express numbers start with 34 or 37**;

- **most MasterCard numbers start with 51, 52, 53, 54, or 55** (they also have some other potential starting numbers which we won’t concern ourselves with for this problem);

- and **all Visa numbers start with 4**.

But credit card numbers also have a “`checksum`” built into them, a mathematical relationship between at least one number and others. That checksum enables computers (or humans who like math) to detect typos (e.g., transpositions), if not fraudulent numbers, without having to query a database, which can be slow. Of course, a dishonest mathematician could certainly craft a fake number that nonetheless respects the mathematical constraint, so a database lookup is still necessary for more rigorous checks.

## Luhn’s Algorithm

So what’s the secret formula? Well, most cards use an algorithm invented by Hans Peter Luhn of IBM. According to Luhn’s algorithm, you can determine if a credit card number is (syntactically) valid as follows:

1.  Multiply every other digit by 2, starting with the number’s second-to-last digit, and then add those products’ digits together.
2.  Add the sum to the sum of the digits that weren’t multiplied by 2.
3.  If the total’s last digit is 0 (or, put more formally, if the total modulo 10 is congruent to 0), the number is valid!

That’s kind of confusing, so let’s try an example with David’s Visa: 4003600000000014.

1.  For the sake of discussion, let’s first mark every other digit, starting with the number’s second-to-last digit:
    
    `4` 0 `0` 3 `6` 0 `0` 0 `0` 0 `0` 0 `0` 0 `1` 4
    
    Okay, let’s multiply each of the underlined digits by 2:
    
    `(4 \* 2)` + `(0 \* 2)` + `(6 \* 2)` + `(0 \*2)` + `(0 \*2)` + `(0 \*2)` + `(0 \*2)` + `(1 \*2)`
    
    That gives us:
    
    `8` + `0` + `12` + `0` + `0` + `0` + `0` + `2` = **`13`**
    
        
2.  Now let’s add that sum (`13`) to the sum of the digits that weren’t multiplied by 2 (starting from the end):
    
    13 + 4 + 0 + 0 + 0 + 0 + 0 + 3 + 0 = **`20`**
    
3.  Yup, the last digit in that sum (20) is a `0`, so David’s card is legit!
    

So, validating credit card numbers isn’t hard, but it does get a bit tedious by hand. **Let’s write a program**.

## Implementation Details

In the file called `credit.c` in the `credit` directory, write a program that prompts the user for a credit card number and then reports (via `printf`) whether it is a valid American Express, MasterCard, or Visa card number, per the definitions of each’s format herein. 

So that we can automate some tests of your code, we ask that your program’s last line of output be `AMEX\n` or `MASTERCARD\n` or `VISA\n` or `INVALID\n`, nothing more, nothing less. 

For simplicity, you may assume that the user’s input will be entirely numeric (i.e., devoid of hyphens, as might be printed on an actual card) and that it won’t have leading zeroes. 

But do not assume that the user’s input will fit in an `int`! Best to use `get_long` from CS50’s library to get users’ input.

Consider the below representative of how your own program should behave when passed a valid credit card number (sans hyphens).

```bash
$ ./credit
Number: 4003600000000014
VISA
```

Now, `get_long` itself will reject hyphens (and more) anyway:

```bash
$ ./credit
Number: 4003-6000-0000-0014
Number: foo
Number: 4003600000000014
VISA
```

But it’s up to you to catch inputs that are not credit card numbers (e.g., a phone number), even if numeric:

```bash
$ ./credit
Number: 6176292929
INVALID
```

Test out your program with a whole bunch of inputs, both valid and invalid. (*We certainly will!*) Here are a [few card numbers](https://developer.paypal.com/api/nvp-soap/payflow/integration-guide/test-transactions/#standard-test-cards) that PayPal recommends for testing.

If your program behaves incorrectly on some inputs (or doesn’t compile at all), time to debug!

### How to Test Your Code

You can also execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/credit
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 credit.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/credit
```

---

# Walkthrough - Cash

## Result

```bash
cash/ $ make cash 
cash/ $ make cash 
cash/ $ make cash
cash/ $ ./cash
Change owed: -1
Change owed: 0
0
cash/ $ ./cash
Change owed: 4
4
cash/ $ ./cash
Change owed: 5
1
cash/ $ ./cash
Change owed: 24
6
cash/ $ ./cash
Change owed: 25
1
cash/ $ ./cash
Change owed: 26
2
cash/ $ ./cash
Change owed: 99
9
```

## Log Trace 

```bash
cash/ $ check50 cs50/problems/2023/x/cash
Connecting.......
Authenticating...
Verifying.........
Preparing.............
Uploading..........
Waiting for results....................................................
Results for cs50/problems/2023/x/cash generated by check50 v3.3.7
:) cash.c exists
:) cash.c compiles
:) get_cents returns integer number of cents
:) get_cents rejects negative input
:) get_cents rejects a non-numeric input of "foo" 
:) calculate_quarters returns 2 when input is 50
:) calculate_quarters returns 1 when input is 42
:) calculate_dimes returns 1 when input is 10
:) calculate_dimes returns 1 when input is 15
:) calculate_dimes returns 7 when input is 73
:) calculate_nickels returns 1 when input is 5
:) calculate_nickels returns 5 when input is 28
:) calculate_pennies returns 4 when input is 4
:) input of 41 cents yields output of 4 coins
:) input of 160 cents yields output of 7 coins
To see the results in your browser go to https://submit.cs50.io/check50/#######################################
```

## Check Style 

```bash
cash/ $ style50 cash.c
Results generated by style50 v2.7.5
Looks good
```

## Submited

```bash
cash/ $ submit50 cs50/problems/2023/x/cash
Connecting.......
Authenticating...
Verifying.......
Preparing.............
Files that will be submitted:
./cash.c
Files that won't be submitted:
./cash
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading..........
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/cash to see your results.
```


# Walkthrough - Credit

## Result

```bash

```

## Log Trace 

```bash

```

## Check Style 

```bash

```

## Submited

```bash

```