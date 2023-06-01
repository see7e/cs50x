---
title: Problem Set 2 - Bulbs
tags: programação, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Bulbs #](#bulbs-)
  - [Not-So-Broken Light Bulbs](#not-so-broken-light-bulbs)
  - [Getting Started](#getting-started)
  - [Implementation Details](#implementation-details)
    - [The Basics](#the-basics)
    - [Encoding a Message](#encoding-a-message)
  - [Specification](#specification)
  - [How to Test Your Code](#how-to-test-your-code)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Check Style](#check-style)
  - [Submited](#submited)

</details>

---

# Bulbs [#](https://cs50.harvard.edu/x/2023/psets/2/bulbs//#bulbs)
> Full code [here](./src/bulbs.c)

## Not-So-Broken Light Bulbs

In lecture, you may have noticed what seemed like a “bug” at the front of the stage, whereby some of the bulbs always seem to be off:

![screenshot of Week 2 lecture with strip of bulbs](https://cs50.harvard.edu/x/2023/psets/2/bulbs//binary_bulbs.jpg)

Each sequence of bulbs, though, encodes a message in _binary_, the language computers “speak.” Let’s write a program to make secret messages of your own, perhaps that we could even put on stage!

## Getting Started

Open [VS Code](https://code.cs50.io/).

Start by clicking inside your terminal window, then execute `cd` by itself. You should find that its “prompt” resembles the below.

```bash
$
```

Click inside of that terminal window and then execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/2/bulbs.zip
```

followed by Enter in order to download a ZIP called `bulbs.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!

Now execute

```bash
unzip bulbs.zip
```

to create a folder called `bulbs`. You no longer need the ZIP file, so you can execute

```bash
rm bulbs.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd bulbs
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
bulbs/ $
```

If all was successful, you should execute

```bash
ls
```

and see a file named `bulbs.c`. Executing `code bulbs.c` should open the file where you will type your code for this problem set. If not, retrace your steps and see if you can determine where you went wrong!

## Implementation Details

To write our program, we’ll first need to think about **bases**.

### The Basics

The simplest _base_ is base-1, or _unary_; to write a number, _N_, in base-1, we would simply write _N_ consecutive `1`s. So the number `4` in base-1 would be written as `1111`, and the number `12` as `111111111111`. Think of it like counting on your fingers or tallying up a score with marks on a board.

You might see why base-1 isn’t used much nowadays. (The numbers get rather long!) Instead, a common convention is base-10, or _decimal_. In base-10, each _digit_ is multiplied by some power of 10, in order to represent larger numbers. For instance, 123 is short for 123\=1⋅102+2⋅101+3⋅100.

Changing base is as simple as changing the 10 above to a different number. For instance, if you wrote `123` in base-4, the number you’d really be writing is 123\=1⋅42+2⋅41+3⋅40, which is equal to the decimal number 27.

Computers, though, use base-2, or _binary_. In binary, writing `123` would be a mistake, since binary numbers can only have `0`s and `1`s. But the process of figuring out exactly what decimal number a binary number stands for is exactly the same. For instance, the number `10101` in base-2 represents 1⋅24+0⋅23+1⋅22+0⋅21+1⋅20, which is equal to the decimal number 21.

### Encoding a Message

Light bulbs can only be on or off. In other words, light bulbs represent two possible states; either the bulb is on, or the bulb is off, just as binary numbers are either 1 or 0. We’ll have to find a way to encode text as a sequence of binary numbers.

Let’s write a program called `bulbs` that takes a message and converts it to a set of bulbs that we could show to an unsuspecting audience. We’ll do it in two steps:

-   The first step consists of turning the text into decimal numbers. Let’s say we want to encode the message `HI!`. Luckily, we already have a convention in place for how to do this, [ASCII](https://asciichart.com/). Notice that `H` is represented by the decimal number `72`, `I` is represented by `73`, and `!` is represented by `33`.
-   The next step involves taking our decimal numbers (like `72`, `73`, and `33`) and converting them into equivalent binary numbers, which only use 0s and 1s. For the sake of having a consistent number of bits in each of our binary numbers, assume that each decimal is represented with 8 bits. `72` is `01001000`, `73` is `01001001`, and `33` is `00100001`.

Lastly, we’ll interpret these binary numbers as instructions for the light bulbs on stage; 0 is off, 1 is on. (You’ll find that `bulbs.c` includes a `print_bulb` function that’s been implemented for you, which takes in a `0` or `1` and outputs emoji representing light bulbs.)

Here’s an example of how the completed program might work. Unlike the Sanders stage, we’ll print one byte per line for clarity.

```bash
$ ./bulbs
Message: HI!
⚫🟡⚫⚫🟡⚫⚫⚫
⚫🟡⚫⚫🟡⚫⚫🟡
⚫⚫🟡⚫⚫⚫⚫🟡
```

To check our work, we can read a bulb that’s on (🟡) as a `1` and bulb that’s off (⚫) as a `0`. Then `HI!` became

```
01001000
01001001
00100001
```

which is precisely what we’d expect.

Another example:

```
# ./bulbs
Message: HI MOM
⚫🟡⚫⚫🟡⚫⚫⚫
⚫🟡⚫⚫🟡⚫⚫🟡
⚫⚫🟡⚫⚫⚫⚫⚫
⚫🟡⚫⚫🟡🟡⚫🟡
⚫🟡⚫⚫🟡🟡🟡🟡
⚫🟡⚫⚫🟡🟡⚫🟡
```

Notice that all characters are included in the lightbulb instructions, including nonalphabetical characters like spaces (`00100000`).

## Specification

Design and implement a program, `bulbs`, that converts text into instructions for the strip of bulbs on CS50’s stage as follows:

-   Implement your program in a file called `bulbs.c`.
-   Your program must first ask the user for a message using `get_string`.
-   Your program must then convert the given `string` into a series of 8-bit binary numbers, one for each character of the string.
-   You can use the provided `print_bulb` function to print a series of `0`s and `1`s as a series of yellow and black emoji, which represent on and off light bulbs.
-   Each “byte” of 8 symbols should be printed on its own line when outputted; there should be a `\n` after the last “byte” of 8 symbols as well.

Hints for Decimal-to-Binary

Let’s walk through an example with the number 4. How would you convert 4 to binary? Start by considering the right-most bit, that which—if on—adds 1 to the number we’re representing. Do you need this bit to be on? Divide 4 by 2 to find out:

4/2\=2

2 divides evenly into 4, which tells us there’s no remainder of 1 to worry about. We can safely leave this right-most bit off, then:

```
0
```

What about the preceding bit, now, the one just the left of this bit we discovered? To check, let’s follow a similar process, but pick up where we left off. In the previous step, we divided 4 by 2 and got 2. Now, does 2 divide evenly into 2? It does, so there’s no remainder of 2 to worry about:

```
00
```

Let’s continue further still. After dividing 2 by 2, we’re left with 1. Diving 1 by 2 leaves a remainder of 1. That means we’ll need to turn this bit on:

```
100
```

And now that we’ve divided our number down to 0, we need no further bits to represent it. Notice that we discovered the bits to represent 4 in the opposite order in which we need to print them: we’ll likely need a structure that lets us store these bits, so we can print them forwards later on. And, of course, in your actual code, you’ll be working with `char`s of 8 bits, so you’ll want to prepend any needed 0’s.

When checking for remainders, the modulo (`%`) operator may come in handy! `4 % 2`, for example, returns 0, meaning that 2 divides into 4 with a remainder of 0.

## How to Test Your Code

Your program should behave per the examples above. You can check your code using `check50`, a program that CS50 will use to test your code when you submit, by typing in the following at the `$` prompt. But be sure to test it yourself as well!

```bash
check50 cs50/problems/2023/x/bulbs
```

To evaluate that the style of your code, type in the following at the `$` prompt.

```bash
style50 bulbs.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/bulbs
```

---

# Walkthrough

As soon we open the file from zip this is the already built code:

```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

const int BITS_IN_BYTE = 8;
void print_bulb(int bit);

int main(void)
{
    // TODO
}

void print_bulb(int bit)
{
    if (bit == 0)
    {
        // Dark emoji
        printf("\U000026AB");
    }
    else if (bit == 1)
    {
        // Light emoji
        printf("\U0001F7E1");
    }
}
```

The 1st version of the code was like this (*here is just `main` the rest is above because i'm lazy*):

```c
int main(void)
{
    // user input
    string txt = get_string("Message: ");
    
    // loop through each character
    for (int i = 0; txt[i] != txt[-1]; i++)
    {
        // Def
        int decimal = txt[i];   // used for binary transformation
        char byte[BITS_IN_BYTE];    // array of 8 (byte)
        int pos = BITS_IN_BYTE - 1; // last decimal division
 
        // load the array with 0s
        int j = 0;
        while (j < BITS_IN_BYTE)
        {
            byte[j] = '0';
            j++;
        }
  
        // Transforms decimal in bits following the exercise's principle
        while (decimal > 0)
        {
            if (decimal % 2 == 1)
            {
                byte[pos] = '1';
            }
            pos--;
            decimal = decimal / 2;
        }
  
        // Transforms bit in light
        for (int j = 0; j < BITS_IN_BYTE; j++)
        {
            if (byte[j] == '1')
            {
                print_bulb(1);
            }
            else
            {
                print_bulb(0);
            }
        }
        printf("\n");
    }
}
```

But with some help (you know who) the code changed to this (*from 69 lines down to 40*):

```c
#include <cs50.h>
#include <stdio.h>
  
const int BITS_IN_BYTE = 8;

void print_bulb(int bit);
  
int main(void)
{
    // user input
    string txt = get_string("Message: ");
  
    // loop through each character
    for (int i = 0; txt[i] != '\0'; i++)
    {
        // Transform decimal into bits
        int decimal = txt[i];
        for (int pos = BITS_IN_BYTE - 1; pos >= 0; pos--)
        {
            char bit = (decimal >> pos) & 1;  // extract each bit
            print_bulb(bit);
        }
        printf("\n");
    }
}
  
void print_bulb(int bit)
{
    if (bit == 0)
    {
        // Dark emoji
        printf("\U000026AB");
    }
    else if (bit == 1)
    {
        // Light emoji
        printf("\U0001F7E1");
    }
}
```

**Optimizations made:**

1.  Removed the unnecessary `string.h` header since it wasn't being used.
2.  Replaced the while loop for initializing the `byte` array with a simple for loop.
3.  Simplified the transformation of decimal into bits using [Bitwise Operations](https://www.ibm.com/docs/en/zos/2.3.0?topic=expressions-bitwise-left-right-shift-operators).
4.  Replaced the condition `txt[i] != txt[-1]` with `txt[i] != '\0'` to check for the end of the string.
5.  Removed the redundant variable `j` in the outer for loop.

The transformation of a decimal number into its binary representation using bitwise operations involves a technique called bit shifting and bitwise using `>>` to move the bits the right.

In the optimized code, the transformation of decimal into bits is done using the following lines:

```c
for (int pos = BITS_IN_BYTE - 1; pos >= 0; pos--)
{
    char bit = (decimal >> pos) & 1;  // extract each bit
    print_bulb(bit);
}
```

Let's break down what's happening:

1.  We start with a loop that iterates from `BITS_IN_BYTE - 1` to 0. This loop is used to extract each bit from the decimal number. `BITS_IN_BYTE` is set to 8, representing the number of bits in a byte.
    
2.  Inside the loop, we perform bit shifting and bitwise AND operations to extract each bit. Here's how it works:    
    -   `(decimal >> pos)` shifts the bits of the decimal number to the right by `pos` positions. By doing so, the bit we want to extract becomes the least significant bit (LSB).
    -   `& 1` performs a bitwise AND operation with 1. Since 1 has all bits set to 0 except for the LSB, this operation effectively extracts the LSB from the shifted decimal number.
    -   The result is stored in the variable `bit`.

3.  The extracted bit is then passed to the `print_bulb` function to print the corresponding emoji.
 

By shifting the bits of the decimal number to the right and performing a bitwise AND with 1, we can isolate each bit starting from the most significant bit (MSB) to the least significant bit (LSB) and process them individually.

This technique allows us to transform the decimal number into its binary representation efficiently using bitwise operations, avoiding the need for explicit division and modulus operations.

## Result

```bash
bulbs/ $ make bulbs 
bulbs/ $ check50 cs50/problems/2023/x/bulbs
Connecting........
Authenticating....
Verifying..........
Preparing.............
Uploading..........
Waiting for results.........................................................
Results for cs50/problems/2023/x/bulbs generated by check50 v3.3.7
:) bulbs.c exists
:) bulbs.c compiles
:) bulbifies an empty message correctly
:) bulbifies "I" correctly
:) bulbifies "xyz" correctly
:) bulbifies "?" correctly
:) bulbifies "Hi!" correctly
:) bulbifies "aBcDeFgHiJkLmNoPqRsTuVwXyZ" correctly
:) bulbifies " CS50 :) " correctly
:) bulbifies The Great Gatsby's first sentence correctly
To see the results in your browser go to https://submit.cs50.io/check50/#############################################
```

## Log Trace 

```markdown
# check50
## cs50/problems/2023/x/bulbs
---
### :) bulbs.c exists

**Log**  
checking that bulbs.c exists...  
### :) bulbs.c compiles

**Log**  
running clang bulbs.c -o bulbs -std=c11 -ggdb -lm -lcs50...  
### :) bulbifies an empty message correctly

**Log**  
running ./bulbs...  
sending input ...  
checking for output ""...  
checking that program exited with status 0...  
### :) bulbifies "I" correctly

**Log**  
running ./bulbs...  
sending input I...  
checking for output "⚫🟡⚫⚫🟡⚫⚫🟡\n"...  
checking that program exited with status 0...  

### :) bulbifies "xyz" correctly

**Log**  
running ./bulbs...  
sending input xyz...  
checking for output "⚫🟡🟡🟡🟡⚫⚫⚫\n⚫🟡🟡🟡🟡⚫⚫🟡\n⚫🟡🟡🟡🟡⚫🟡⚫\n"...  
checking that program exited with status 0...  

### :) bulbifies "?" correctly

**Log**  
running ./bulbs...  
sending input ?...  
checking for output "⚫⚫🟡🟡🟡🟡🟡🟡\n"...  
checking that program exited with status 0...  

### :) bulbifies "Hi!" correctly

**Log**  
running ./bulbs...  
sending input Hi!...  
checking for output "⚫🟡⚫⚫🟡⚫⚫⚫\n⚫🟡🟡⚫🟡⚫⚫🟡\n⚫⚫🟡⚫⚫⚫⚫🟡\n"...  
checking that program exited with status 0...  

### :) bulbifies "aBcDeFgHiJkLmNoPqRsTuVwXyZ" correctly

**Log**  
running ./bulbs...  
sending input aBcDeFgHiJkLmNoPqRsTuVwXyZ...  
checking for output "⚫🟡🟡⚫⚫⚫⚫🟡\n⚫🟡⚫⚫⚫⚫🟡⚫\n⚫🟡🟡⚫⚫⚫🟡🟡\n⚫🟡⚫⚫⚫🟡⚫⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡⚫⚫⚫🟡🟡⚫\n⚫🟡🟡⚫⚫🟡🟡🟡\n⚫🟡⚫⚫🟡⚫⚫⚫\n⚫🟡🟡⚫🟡⚫⚫🟡\n⚫🟡⚫⚫🟡⚫🟡⚫\n⚫🟡🟡⚫🟡⚫🟡🟡\n⚫🟡⚫⚫🟡🟡⚫⚫\n⚫🟡🟡⚫🟡🟡⚫🟡\n⚫🟡⚫⚫🟡🟡🟡⚫\n⚫🟡🟡⚫🟡🟡🟡🟡\n⚫🟡⚫🟡⚫⚫⚫⚫\n⚫🟡🟡🟡⚫⚫⚫🟡\n⚫🟡⚫🟡⚫⚫🟡⚫\n⚫🟡🟡🟡⚫⚫🟡🟡\n⚫🟡⚫🟡⚫🟡⚫⚫\n⚫🟡🟡🟡⚫🟡⚫🟡\n⚫🟡⚫🟡⚫🟡🟡⚫\n⚫🟡🟡🟡⚫🟡🟡🟡\n⚫🟡⚫🟡🟡⚫⚫⚫\n⚫🟡🟡🟡🟡⚫⚫🟡\n⚫🟡⚫🟡🟡⚫🟡⚫\n"...  
checking that program exited with status 0...  

### :) bulbifies " CS50 :) " correctly

**Log**  
running ./bulbs...  
sending input CS50 :) ...  
checking for output "⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡⚫⚫⚫⚫🟡🟡\n⚫🟡⚫🟡⚫⚫🟡🟡\n⚫⚫🟡🟡⚫🟡⚫🟡\n⚫⚫🟡🟡⚫⚫⚫⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫⚫🟡🟡🟡⚫🟡⚫\n⚫⚫🟡⚫🟡⚫⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n"...  
checking that program exited with status 0...  

### :) bulbifies The Great Gatsby's first sentence correctly

**Log**  
running ./bulbs...  
sending input In my younger and more vulnerable years my father gave me some advice that I've been turning over in my mind ever since....  
checking for output "⚫🟡⚫⚫🟡⚫⚫🟡\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫🟡🟡⚫🟡\n⚫🟡🟡🟡🟡⚫⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡🟡🟡⚫⚫🟡\n⚫🟡🟡⚫🟡🟡🟡🟡\n⚫🟡🟡🟡⚫🟡⚫🟡\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫🟡🟡⚫⚫🟡🟡🟡\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡🟡⚫⚫🟡⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫⚫⚫⚫🟡\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫🟡🟡⚫⚫🟡⚫⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫🟡🟡⚫🟡\n⚫🟡🟡⚫🟡🟡🟡🟡\n⚫🟡🟡🟡⚫⚫🟡⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡🟡⚫🟡🟡⚫\n⚫🟡🟡🟡⚫🟡⚫🟡\n⚫🟡🟡⚫🟡🟡⚫⚫\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡🟡⚫⚫🟡⚫\n⚫🟡🟡⚫⚫⚫⚫🟡\n⚫🟡🟡⚫⚫⚫🟡⚫\n⚫🟡🟡⚫🟡🟡⚫⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡🟡🟡⚫⚫🟡\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡⚫⚫⚫⚫🟡\n⚫🟡🟡🟡⚫⚫🟡⚫\n⚫🟡🟡🟡⚫⚫🟡🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫🟡🟡⚫🟡\n⚫🟡🟡🟡🟡⚫⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫⚫🟡🟡⚫\n⚫🟡🟡⚫⚫⚫⚫🟡\n⚫🟡🟡🟡⚫🟡⚫⚫\n⚫🟡🟡⚫🟡⚫⚫⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡🟡⚫⚫🟡⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫⚫🟡🟡🟡\n⚫🟡🟡⚫⚫⚫⚫🟡\n⚫🟡🟡🟡⚫🟡🟡⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫🟡🟡⚫🟡\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡🟡⚫⚫🟡🟡\n⚫🟡🟡⚫🟡🟡🟡🟡\n⚫🟡🟡⚫🟡🟡⚫🟡\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫⚫⚫⚫🟡\n⚫🟡🟡⚫⚫🟡⚫⚫\n⚫🟡🟡🟡⚫🟡🟡⚫\n⚫🟡🟡⚫🟡⚫⚫🟡\n⚫🟡🟡⚫⚫⚫🟡🟡\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡🟡⚫🟡⚫⚫\n⚫🟡🟡⚫🟡⚫⚫⚫\n⚫🟡🟡⚫⚫⚫⚫🟡\n⚫🟡🟡🟡⚫🟡⚫⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡⚫⚫🟡⚫⚫🟡\n⚫⚫🟡⚫⚫🟡🟡🟡\n⚫🟡🟡🟡⚫🟡🟡⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫⚫⚫🟡⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡🟡⚫🟡⚫⚫\n⚫🟡🟡🟡⚫🟡⚫🟡\n⚫🟡🟡🟡⚫⚫🟡⚫\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫🟡🟡⚫🟡⚫⚫🟡\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫🟡🟡⚫⚫🟡🟡🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫🟡🟡🟡🟡\n⚫🟡🟡🟡⚫🟡🟡⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡🟡⚫⚫🟡⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫🟡⚫⚫🟡\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫🟡🟡⚫🟡\n⚫🟡🟡🟡🟡⚫⚫🟡\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫🟡🟡⚫🟡\n⚫🟡🟡⚫🟡⚫⚫🟡\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫🟡🟡⚫⚫🟡⚫⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡🟡⚫🟡🟡⚫\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫🟡🟡🟡⚫⚫🟡⚫\n⚫⚫🟡⚫⚫⚫⚫⚫\n⚫🟡🟡🟡⚫⚫🟡🟡\n⚫🟡🟡⚫🟡⚫⚫🟡\n⚫🟡🟡⚫🟡🟡🟡⚫\n⚫🟡🟡⚫⚫⚫🟡🟡\n⚫🟡🟡⚫⚫🟡⚫🟡\n⚫⚫🟡⚫🟡🟡🟡⚫\n"...  
checking that program exited with status 0...
```

## Check Style 

```bash
bulbs/ $ style50 bulbs.c
Results generated by style50 v2.7.5
Looks good!
```

## Submited

```bash
bulbs/ $ submit50 cs50/problems/2023/x/bulbs
Connecting.......
Authenticating...
Verifying.......
Preparing..............
Files that will be submitted:
./bulbs.c
Files that won't be submitted:
./bulbs
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading..........
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/bulbs to see your results.
```