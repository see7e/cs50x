---
title: CS50 - Week 4
tags: programming, cs50
use: Documentation
languages: C
dependences: CS50
---

> This material is distributed by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my understanding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Lecture 4](#lecture-4)
  - [Welcome! #](#welcome-)
  - [Memory](#memory)
  - [Hexadecimal](#hexadecimal)
  - [Addresses](#addresses)
  - [Pointers](#pointers)
  - [Strings](#strings)
  - [Pointer Arithmetic](#pointer-arithmetic)
  - [Comparing Strings](#comparing-strings)
  - [Copying](#copying)
  - [Malloc / Free](#malloc--free)
  - [Valgrind #](#valgrind-)
  - [Garbage Values](#garbage-values)
  - [Pointer Fun with Binky](#pointer-fun-with-binky)
  - [Swap](#swap)
    - [Heap-Stack](#heap-stack)
  - [Overflow](#overflow)
  - [`scanf`](#scanf)
  - [Files](#files)
  - [Summing Up](#summing-up)
- [Section](#section)
- [Shorts](#shorts)
  - [Hexadecimal](#hexadecimal-1)
  - [Pointers](#pointers-1)
  - [Defining Custom Types](#defining-custom-types)
  - [Dynamic Memory Allocation](#dynamic-memory-allocation)
  - [Call Stacks](#call-stacks)
  - [File Pointers](#file-pointers)
- [Exercises](#exercises)
  - [Practice Problems #](#practice-problems-)
  - [Lab 4: Smiley or Volume](#lab-4-smiley-or-volume)
    - [What to Do](#what-to-do)
  - [Problem Set 4](#problem-set-4)
  - [What to Do](#what-to-do-1)
  - [Advice](#advice)

</details>

---

# Lecture 4

<details>
<summary>Keywords, lookup in <a href="./src/transcripts/lecture4.md">transcript</a></summary>

- bitmap 
- `rgb` (0-255 = `unsigned __int8`)
- `hexadecimal` (base-16)
- hex convention
- pointers
- linking things together
- string is a pointer to a character
- de-reference
- addition, substraction, on pointers
- touching memory that you shouldn't
- segments of memory
- string compare
- allocate (`malloc`)
- `free`
- reused
- valgring
- heap
- leak
- invalid write
- freed
- garbadge values
- initialise
- swap
- copies of the values
- by value
- by reference
- loaded in the computer memory
- machine code
- globals
- prototype
- overflow
- buffer
- 

</details>

## Welcome! [#](https://cs50.harvard.edu/x/2023/notes/4/#welcome)

-   In previous weeks, we talked about images being made of smaller building blocks called pixels.
-   Today, we will go into further detail about the zeros and ones that make up these images.
-   Further, we will discuss how to access the underlying data stored in computer memory.

## Memory

You can imagine a crime drama where an image is enhanced, enhanced, and enhanced, is not entirely real-life accurate. Indeed, if you keep zooming into an image, you will see pixels.

![A blurry photo](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide012.png "blurry")
> this is a `5`

You can imagine as an image as a map of bits, where zeros represent black and ones represent white.

![Zeros and ones being converted to a black and white smiley](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide015.png "smiley")
> try to look at the bitmap from a distance

_RGB_, or _red, green, blue_, are numbers that represent the amount of each of these colors. In Adobe Photoshop, you can see these settings as follows:

![A photoshop panel with RGB values and hexidecimal input](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide016.png "hex in photoshop")

Notice how the amount of red, blue, and green changes the color selected.

You can see by the image above that color is not just represented in three values. At the bottom of the window, there is a special value made up of numbers and characters. `255` is represented as `FF`. Why might this be?

## Hexadecimal

_Hexadecimal_ is a system of counting that has 16 counting values. They are as follows:

```
0 1 2 3 4 5 6 7 8 9 a b c d e f
```
  
Notice that `F` represents `15`.

-   Hexadecimal is also known as _base-16_.
-   When counting in hexadecimal, each column is a power of 16.
-   The number `0` is represented as `00`.
-   The number `1` is represented as `01`.
-   The number `9` is represented by `09`.
-   The number `10` is represented as `0A`.
-   The number `15` is represented as `0F`.
-   The number `16` is represented as `10`.
-   The number `255` is represented as `FF`, because 16 x 15 (or `F`) is 240. Add 15 more to make 255. This is the highest number you can count using a two-digit hexadecimal system.
-   Hexadecimal is useful because it can be represented using fewer digits. Hexadecimal allows us to represent information more succinctly.

## Addresses

In weeks past, you may recall our artist rendering of concurrent blocks of memory. Applying hexadecimal numbering to each of these blocks of memory, you can visualize these as follows:

![Blocks of memory numbered in hex|500](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide065.png "memory hex")

You can imagine how there may be confusion regarding whether the `10` block above may represent a location in memory or the value `10`. 

Accordingly, by convention, **all hexadecimal numbers are often represented with the `0x` refix as follows:**

> **Short story:** The `0` tells the parser it's dealing with a constant (and not an identifier/reserved word). Something is still needed to specify the number base: the `x` is an arbitrary choice.
>
> **Long story:** In the 60's, the prevalent programming number systems were decimal nd _octal_ — mainframes had 12, 24 or 36 bits per byte, which is nicely divisible by 3 = log28).
>
> The BCPL language used the syntax `8 1234` for octal numbers. When Ken Thompson created B rom BCPL, he used the `0` prefix instead. This is great because
>
> 1. an integer constant now always consists of a single token,
> 2. the parser can still tell right away it's got a constant,
> 3. the parser can immediately tell the base (`0` is the same in    >both bases),
> 4. it's mathematically sane (`00005 == 05`), and
> 5. no precious special characters are needed (as in `#123`).
>
> When C was created from B, the need for hexadecimal numbers arose (the PDP-11 had 16-bit ords) and all of the points above were still valid. Since octals were still needed for other achines, `0x` was arbitrarily chosen (`00` was probably ruled out as awkward).
> *`C#` is a descendant of `C`, so it inherits the syntax.*
> *Found in [here](https://stackoverflow.com/questions/2670639/hy-are-hexadecimal-numbers-prefixed-with-0x)*

![blocks of memory numbered in hex with 0x|500](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide066.png "0x")

-   In your terminal window, type `code addresses.c` and write your code as follows:
    
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        int n = 50;
        printf("%i\n", n);
    }
    ```
    
    Notice how `n` is stored in memory with the value `50`.

-   You can visualize how this program stores this value as follows:
    
    ![the value 50 stored in a memory location with hex|500](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide070.png "hex")

The `C` language has two powerful operators that relate to memory:
- **`&` Provides the address** of something stored in memory.
- **`*`** Instructs the compiler to** go to a location in memory**, i.e. a pointer.

-   We can leverage this knowledge by modifying our code as follows:
    
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        int n = 50;
        printf("%p\n", &n);
    }
    ```
    
    Notice the `%p`, which allows us to view the address of a location in memory. `&n` can be literally translated as “the address of `n`.” Executing this code will return an address of memory beginning with `0x`.

## [Pointers](../../C/Pointers.md)

**A _pointer_ is a variable that contains the address of some element**. Most succinctly, a pointer is an address in your computer’s memory (*this address could be permanent or temporary*).
-   Consider the following code:
    
    ```c
    int n = 50;
    
    int *p = &n;
    ```
    
    Notice that `p` is a pointer that contains a number that is the address of an integer `n`.

-   Modify your code as follows:
    > using `%p` will send to compiler that the `printf` function will deal with with a pointer
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        int n = 50;
        int *p = &n; // p receives the address memory of n
        printf("%p\n", p); // This will print the value of p
    }
    ```
    
    Notice that this code has the same effect as our previous code. We have simply leveraged our new knowledge of the `&` and `*` operators.

-   You can visualize our code as follows:
    
    ![Same value of 50 in a memory location with a pointer value stored elsewhere|500](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide078.png "pointer")
    
    Notice the pointer seems rather large. Indeed, a pointer is usually stored as an 8-byte value.

-   You can more accurately visualize a pointer as one address that points to another:
    
    ![A pointer as an arrow, pointing from one location of memory to another|500](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide079.png "pointer")

-   To illustrate the use of the `*` operator, consider the following:
    
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        int n = 50;
        int *p = &n;
        printf("%i\n", *p);
    }
    ```
    
    Notice that the `printf` line prints the integer at the location of `p`.

## Strings

Now that we have a mental model for pointers, we can peel back a level of simplification that was offered earlier in this course.
Recall that a string is simply an array of characters. For example, `string s = "HI!"` can be represented as follows:
    
![The string HI with an exclaimation point stored in memory|500](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide085.png "hi")

However, what is `s` really? Where is the `s` stored in memory? As you can imagine, `s` needs to be stored somewhere. You can visualize the relationship of `s` to the string as follows:
    
![Same string HI with a pointer pointing to it|500](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide086.png "hi pointer")
    
Notice how a pointer called `s` tells the compiler where the first byte of the string exists in memory.
    
**The value of `*s`** (*that in this case points to a `string`*) **is the memory address of the first element of the pointed object**. Why? Because if the compiler knows the point where it starts, it will pull the "string" until the very end (which is a `'\0'`).

-   Modify your code as follows:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string s = "HI!";
        
        printf("%p\n", s);
        printf("%p\n", &s[0]);
        printf("%p\n", &s[1]);
        printf("%p\n", &s[2]);
        printf("%p\n", &s[3]);
    }
    ```
    
    Notice the above prints the memory locations of each character in the string `s` and they're consecutive slots in memory (*each `char` occupies 1 bite in memory*).

-   Likewise, you can modify your code as follows:
	
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        char *s = "HI!";
        
        printf("%p\n", s);
        printf("%p\n", &s[0]);
        printf("%p\n", &s[1]);
        printf("%p\n", &s[2]);
        printf("%p\n", &s[3]);
    }
    ```
	
    Notice that this code will return the "same" result as the previous one, but the big difference is that now we have a pointer to a char which has the memory location of `s` (*the string*). Just because in `<cs50.h>` there's this `typedef` :
    
    ```c
    typedef char *string;
    ```

## Pointer Arithmetic

You can modify your code to accomplish the same thing in a longer form as follows in order to print the characters:

```c
#include <stdio.h>

int main(void)
{
    char *s = "HI!";
    printf("%c\n", s[0]);
    printf("%c\n", s[1]);
    printf("%c\n", s[2]);
}
```

Notice that we are printing each character at the location of `s`.

-   Further, you can modify your code as follows:
    
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        char *s = "HI!";
        printf("%c\n", *s);
        printf("%c\n", *(s + 1));
        printf("%c\n", *(s + 2));
    }
    ```
    
    Notice that the first character at the location of `s` is printed. Then, the character at the location `s + 1` is printed, and so on. **Remember that memory addresses are indeed numbers, and we can jump on each "slot" of the string (*or i.e. and array*) incrementing the bite size of each element.**

-   Can you imagine what would happen if you attempted to access something at location `s + 50`? 
	If you touch another segment of memory belonged by any other object the compiler will return a `SegmentationFault (core dumped)` error.
	
	Hackers sometimes attempt to gain access to items in memory they should not have access to. If you attempt this, the program will likely quit as a safety precaution.

## Comparing Strings

A string of characters is simply an array of characters identified by its first byte.
Recall that last week we proposed that we could not compare two strings using the ` == ` operator.
Utilizing the ` == ` operator in an attempt to compare strings will attempt to compare the memory locations of the strings instead of the characters therein. Accordingly, we recommended the use of `strcmp`.
-   To illustrate this, type `code compare.c` and write code as follows:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Get two strings
        char *s = get_string("s: ");
        char *t = get_string("t: ");
    
        // Compare strings' addresses
        if (s == t)
        {
            printf("Same\n");
        }
        else
        {
            printf("Different\n");
        }
    }
    ```
    
    Noticing that typing in `HI!` for both strings still results in the output of `Different`.

-   Why are these strings seemingly different? You can use the following to visualize why:
    
    ![two strings stored separately in memory|600](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide115.png "two strings")
    
For clarity, you can see how the following image illustrates pointers pointing to two separate locations in memory:
    
    ![two strings stored separately in memory with separate pointers pointing at them|600](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide116.png "two strings")
    
-   Modify your code as follows:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Get two strings
        char *s = get_string("s: ");
        char *t = get_string("t: ");
    
        // Print strings
        printf("%s\n", s);
        printf("%s\n", t);
    }
    ```
    
    Notice how we now have two separate strings stored likely at two separate locations.

-   You can see the locations of these two stored strings with a small modification:
    
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Get two strings
        char *s = get_string("s: ");
        char *t = get_string("t: ");
    
        // Print strings' addresses
        printf("%p\n", s);
        printf("%p\n", t);
    }
    ```
    
    Notice that the `%s` has been changed to `%p` in the print statement.

## Copying

A common need in programming is to copy one string to another.
> In your terminal window, type `code copy.c` and write code as follows:

```c
#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    // Get a string
    string s = get_string("s: ");

    // Copy string's address
    string t = s;

    // Capitalize first letter in string
    t[0] = toupper(t[0]);

    // Print string twice
    printf("s: %s\n", s);
    printf("t: %s\n", t);
}
```

Notice that `string t = s` copies the address of `s` to `t`. This does not accomplish what we are desiring. **The string is not copied – only the address is**.
    > Remember though that every variable is a pointer to some information located in memory.

-   Before we address this challenge, it’s important to ensure that we don’t experience a _segmentation fault_ through our code, where we attempt to copy `string s` to `string t`, where `string t` does not exist. We can employ the `strlen` function as follows to assist with that:
    
    ```c
    #include <cs50.h>
    #include <ctype.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        // Get a string
        string s = get_string("s: ");
    
        // Copy string's address
        string t = s;
    
        // Capitalize first letter in string
        if (strlen(t) > 0)
        {
            t[0] = toupper(t[0]);
        }
    
        // Print string twice
        printf("s: %s\n", s);
        printf("t: %s\n", t);
    }
    ```
    
    Notice that `strlen` is used to make sure `string t` exists. If it does not, nothing will be copied.
    
-   You can visualize the above code as follows:
    ![two pointers pointing at the same memory location with a string](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide124.png "two strings")
    
    Notice that `s` and `t` are still pointing at the same blocks of memory. This is not an authentic copy of a string. Instead, these are two pointers pointing at the same string.

## Malloc / Free
 
 To be able to make an authentic copy of the string, we will need to introduce two new building blocks.
 - First, **`malloc`** (*memory allocate*) allows you, the programmer, to allocate a block of a specific size of memory.
 - Second, **`free`** allows you to tell the compiler to _free up_ that block of memory you previously allocated.

-   We can modify our code to create an authentic copy of our string as follows:
    
    ```c
    #include <cs50.h>
    #include <ctype.h>
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    int main(void)
    {
        // Get a string
        char *s = get_string("s: ");
    
        // Allocate memory for another valid string + 1 ('\0')
        char *t = malloc(strlen(s) + 1); 
    
        // Copy string into memory, including '\0'
        for (int i = 0; i <= strlen(s); i++)
        {
            t[i] = s[i];
        }
    
        // Capitalize copy
        t[0] = toupper(t[0]);
    
        // Print strings
        printf("s: %s\n", s);
        printf("t: %s\n", t);
    }
    ```
    
Every string to be considered a valid one has to be terminated, i.e. must have the _null_ `\0` character in their final.
So  `malloc(strlen(s) + 1)` creates a block of memory that is the length of the string `s` plus one to efficiently, copy the `s` string. 
Then, the `for` loop walks through the string `s` and assigns each value to that same location on the string `t`.

It turns out that there is an inefficiency in our code: Every iteration in the `for loop` will call the `strlen(s)` taking in consideration that the size of `s` is constant and won't change, we can define as a static value (`n = strlen(s)`) before (in the left-hand side of) the loop execution. Modify your code as follows:

```c
#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void)
{
    // Get a string
    char *s = get_string("s: ");
    
    // Allocate memory for another string with the same size of `s`
    char *t = malloc(strlen(s) + 1);
    
    // Copy string into memory, including '\0'
    for (int i = 0, n = strlen(s); i <= n; i++)
    {
        t[i] = s[i];
    }
    
    // Capitalize copy
    t[0] = toupper(t[0]);
    
    // Print strings
    printf("s: %s\n", s);
    printf("t: %s\n", t);
}
```

The `C` Language has a built-in function to copy strings called `strcpy(char dest, char src)` that does the same work that our `for` loop previously did. It take two arguments:
- **`char dest`**, is the destination and,
- **`char src`**, is the source
> From [`man`](https://man7.org/linux/man-pages/man3/strcpy.3.html)
> The `strcpy()` function copies the string pointed to by `src`, including the terminating null byte (`'\0'`), to the buffer pointed to by `dest`.  **The strings may not overlap, and the destination string `dest` must be large enough to receive the copy**.  _Beware of_ _buffer overruns!_

-   Both `get_string` and `malloc` return `NULL`, a special value in memory, in the event that something goes wrong. 
	You can write code that can check (like a *hand break*) for this `NULL` condition as follows:
    
    ```c
    #include <cs50.h>
    #include <ctype.h>
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    int main(void)
    {
        // Get a string
        char *s = get_string("s: ");
        if (s == NULL) // hand break
        {
            return 1;
        }
    
        // Allocate memory for another string
        char *t = malloc(strlen(s) + 1);
        if (t == NULL) // hand break
        {
            return 1;
        }
    
        // Copy string into memory
        strcpy(t, s);
    
        // Capitalize copy
        if (strlen(t) > 0)
        {
            t[0] = toupper(t[0]);
        }
    
        // Print strings
        printf("s: %s\n", s);
        printf("t: %s\n", t);
    
        // Free memory
        free(t);
        return 0;
    }
    ```
    
    Notice that if the string obtained is of length `0` or `malloc` fails, `NULL` is returned. Further, notice that `free` lets the computer know you are done with this block of memory you created via `malloc`.

Other (high level) programming languages has a "thing" called [Garbage Collector]() and it automatically manage the memory allocated or not in the program execution.
 
## Valgrind [#](https://valgrind.org/docs/manual/quick-start.html)

-   _Valgrind_ is a tool that can check to see if there are memory-related issues with your programs wherein you utilized `malloc`. Specifically, it checks to see if you `free` all the memory you allocated.
-   Consider the following code:
    
    ```c
    1 #include <stdio.h>
    2 #include <stdlib.h>
    3
    4 int main(void)
    5 {
    6     int *x = malloc(3 * sizeof(int));
    7     x[1] = 72;
    8     x[2] = 73;
    9     x[3] = 33;
    10 }
    ```

*Running the above program does not cause any errors*. While `malloc` is used to allocate enough memory for an array, the code fails to `free` that allocated memory. 

`valgrind ./memory`, you will get a report from Valgrind that will report where memory has been lost as a result of your program.

```bash
$ make memory 
$ valgrind ./memory 
==9925== Memcheck, a memory error detector
==9925== Copyright (C) 2002-2017, and GNU GPL\'d, by Julian Seward et al.
==9925== Using Valgrind-3.18.1 and LibVEX; rerun with -h for copyright info
==9925== Command: ./memory
==9925== 
==9925== Invalid write of size 4
==9925==    at 0x109170: main (memory.c:9)
==9925==  Address 0x4bb504c is 0 bytes after a block of size 12 alloc\'d
==9925==    at 0x4848899: malloc (in /usr/libexec/valgrind/vgpreload_memcheck-amd64-linux.so)
==9925==    by 0x109151: main (memory.c:6)
==9925== 
==9925== 
==9925== HEAP SUMMARY:
==9925==     in use at exit: 12 bytes in 1 blocks
==9925==   total heap usage: 1 allocs, 0 frees, 12 bytes allocated
==9925== 
==9925== 12 bytes in 1 blocks are definitely lost in loss record 1 of 1
==9925==    at 0x4848899: malloc (in /usr/libexec/valgrind/vgpreload_memcheck-amd64-linux.so)
==9925==    by 0x109151: main (memory.c:6)
==9925== 
==9925== LEAK SUMMARY:
==9925==    definitely lost: 12 bytes in 1 blocks
==9925==    indirectly lost: 0 bytes in 0 blocks
==9925==      possibly lost: 0 bytes in 0 blocks
==9925==    still reachable: 0 bytes in 0 blocks
==9925==         suppressed: 0 bytes in 0 blocks
==9925== 
==9925== For lists of detected and suppressed errors, rerun with: -s
==9925== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 0 from 0)
```

The review of this trace is:
- `Invalid write of...` means that `malloc` prepares 12 bites of space ($3*4bites$ (int size)) and we are modifying in the index `[2]` which is the 4th element. 
- `12 bytes in 1 blocks are definitely lost in loss record 1 of 1` in `HEAP SUMMARY` denotes that this length of memory was allocated and never freed.
- In `LEAK SUMMARY` we can visualize the same error listed above in `definitely lost` section.
You can modify your code as follows:

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int *x = malloc(3 * sizeof(int));
    x[0] = 72;
    x[1] = 73;
    x[2] = 33;
    free(x);
}
```

 Notice that running Valgrind again now results in now memory leaks:
```bash
[...]
==0000== All heap blocks were freed -- no leaks are possible 
[...]
```

## Garbage Values

When you ask the compiler for a block of memory, there is no guarantee that this memory will be empty.
> That's why in som cases we have to specify a *null* value for each "new element". 

It’s very possible that this memory that you allocated was previously utilized by the computer. Accordingly, you may see _junk_ or _garbage values_. This is a result of you getting a block of memory but not initializing it. For example, consider the following code:
    
```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int scores[1024];
    for (int i = 0; i < 1024; i++)
    {
        printf("%i\n", scores[i]);
    }
}
```

Notice that running this code will allocate `1024` locations in memory for your array, but the `for` loop will likely show that not all values therein are `0`. It’s always best practice to be aware of the potential for garbage values when you do not initialize blocks of memory to some other value like zero or otherwise.

## Pointer Fun with Binky
> [video from Stanford University](https://www.youtube.com/watch?v=5VnDaHBi8dM) that helped us visualize and understand pointers.

So:
- Pointers in order to be dereferenced needs firstly to be initialized
	```c
	int *x;
	x = malloc(...);
	x* = 50;
	```

- The Pointer can be only defined and not initialized
	```c
	int *y; // and that's it
	```

## Swap

In the real world, a common need in programming is to swap two values. Naturally, it’s hard to swap two variables without a temporary holding space. In practice, you can type `code swap.c` and write code as follows to see this in action:
    
```c
#include <stdio.h>

// Function prototype
void swap(int a, int b);

int main(void)
{
    int x = 1;
    int y = 2;

    printf("x is %i, y is %i\n", x, y);
    swap(x, y);
    printf("x is %i, y is %i\n", x, y);
}

void swap(int a, int b)
{
    int tmp = a;
    a = b;
    b = tmp;
}
```

Notice that while this code runs, it does not work. The values, even after being sent to the `swap` function, do not swap. Why?
- when the function receives the (**value of**) arguments, they will be a clone of the originals, so if we don't point to the actual place (**the reference**) where the variables are stored. 

### Heap-Stack

When you pass values to a function, you are only providing copies. In previous weeks, we discussed the concept of _scope_. The values of `x` and `y` created between `{ }` of the `main` function only have the scope of the `main` function. Consider the following image:

![a rectangle with machine code at top followed by globals heap and stack](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide163.png "stack and heap")

Notice that _global_ variables, which we have not used in this course, live in one place in memory. Various functions are stored in the `stack` in another area of memory.

> The Heap-Stack is one chunk of memory, they´re not theoretically separated. The Heap is the "method" of filling this memory space from above to below and, the Stack is the inverse situation.

Now, consider the following image:

![a rectangle with main function at bottom and swap function directly above it](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide167.png "frames")

Notice that `main` and `swap` have two separate _frames_ or areas of memory. Therefore, we cannot simply pass the values from one function to another to change them.

-   Modify your code as follows:
    
    ```c
    #include <stdio.h>
    
    void swap(int *a, int *b);
    
    int main(void)
    {
        int x = 1;
        int y = 2;
    
        printf("x is %i, y is %i\n", x, y);
        swap(&x, &y);
        printf("x is %i, y is %i\n", x, y);
    }
    
    void swap(int *a, int *b)
    {
        int tmp = *a;
        *a = *b;
        *b = tmp;
    }
    ```
    
    Notice that variables are not passed **by _value_** but **by _reference_**. That is, the addresses of `a` and `b` are provided to the function. Therefore, the `swap` function can know where to make changes to the actual `a` and `b` from the main function.

-   You can visualize this as follows:
    ![a and b stored in main function being passed by reference to the swap function](https://cs50.harvard.edu/x/2023/notes/4/cs50Week4Slide173.png "swap by reference")

## Overflow

There's two types of overflows that can be considered as _buffer overflows_
-   A _heap overflow_ is when you overflow the heap, touching areas of memory you are not supposed to.
-   A _stack overflow_ is when too many functions are called, overflowing the amount of memory available.

## `scanf`

In CS50, we have created functions like `get_int()` to simplify the act of getting input from the user.  `scanf()` is a built-in function that can get user input.

We can re-implement `get_int` rather easily using `scanf` as follows:

```c
#include <stdio.h>

int main(void)
{
    int x;
    printf("x: ");
    scanf("%i", &x);
    printf("x: %i\n", x);
}
```

Notice that the value of `x` is stored at the location of `x` in the line `scanf("%i", &x)`.

However, attempting to re-implement `get_string()` is not easy. Consider the following:

```c
#include <stdio.h>

int main(void)
{
    char *s;
    printf("s: ");
    scanf("%s", s);
    printf("s: %s\n", s);
}
```

Notice that no `&` is required because strings are special. Still, this program will not function. Nowhere in this program do we allocate the amount of memory required for our string.

-   We can modify our code as follows:
    
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        char s[4]; // static memory size
        printf("s: ");
        scanf("%s", s);
        printf("s: %s\n", s);
    }
    ```
    
    Notice that if we pre-allocate an array of size `4`, we can type `cat` and the program functions. However, a string larger than this would create an error. That's why in the actual function the memory is allocated based on iterations over the input received. 

## Files

You can read from and manipulate files using the `<stdio.h>` which stands for Standard Input-Output, the file uses the concepts of [Input-Output I/O]().
> While this topic will be discussed further in a future week, consider the following code for `phonebook.c`:

```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    // Open CSV file
    FILE *file = fopen("phonebook.csv", "a");

    // Get name and number
    char *name = get_string("Name: ");
    char *number = get_string("Number: ");

    // Print to file
    fprintf(file, "%s,%s\n", name, number);

    // Close file
    fclose(file);
}
```

Notice that this code uses pointers to access the file.

You can create a file called `phonebook.csv` in advance of running the above code. After running the above program and inputting a name and phone number, you will notice that this data persists in your CSV file.


## Summing Up

In this lesson, you learned about pointers that provide you with the ability to access and manipulate data at specific memory locations. Specifically, we delved into…

-   Memory
-   Hexadecimal
-   Addresses
-   Pointers
-   Strings
-   Pointer Arithmetic
-   Comparing strings
-   Copying
-   Valgrind
-   Garbage values
-   Swap
-   Overflow
-   `scanf`

See you next time!

---

# Section 
> [Transcript](./src/transcripts/section4.md)

- What are pointers, and how can we become familiar with their syntax?
- How can we read and write data from a file?
	-  Using of `<stdio.h>`
	- Using of `unit8_t` of `<stdint.h>`
	- `buffer` is commonly used as a representation of a desired segment 
- What is dynamic memory, and how should we use it?
	- `malloc()` / `free()`

---

# Shorts

## Hexadecimal 
> [Transc](./src/transcripts/shorts4_hexadec.md)

As usual numbers (base-10) have powers ([Exponentiation](https://en.wikipedia.org/wiki/Exponentiation) ), hexadecimals have it but in a different way, e.g. $0x367$ would correspondo to:

|  #   | ... | $16^2$ </br> `256` | $16^1$ </br> `16` | $16^0$ </br> `1` |
|:----:| --- |:------------------:|:-----------------:|:----------------:|
| `0x` | ... |         3          |         6         |        7         |

## Pointers
> [Transc](./src/transcripts/shorts4_ptr.md)

Every file on your computer lives on your disk drive, be it a hard disk drive (HDD) or a solid-state drive (SSD). Disk drives are just storage space; we can't directly work there. Manipulation and use of data can only take place in RAM, so we have to move data there.
Memory is basically a huge array of 8-bit wide bytes (512 MB, 1 GB, 2 GB, 4 GB...)

## Defining Custom Types
> [Transc](./src/transcripts/shorts4_cust_types.md)

- The C keyword typedef provides a way to create a shorthand or rewritten name for data types.
- The basic idea is to first define a type in the normal way, then alias it to something else.

## Dynamic Memory Allocation 
> [Transc](./src/transcripts/shorts4_alocation.md)

- We can use pointers to get access to a block Of dynamically-allocated memory at runtime.
- Dynamically allocated memory comes from a pool of memory known as the heap.
- Prior to this point, all memory we've been working with has been coming from a pool of memory known as the stack.

## Call Stacks
> [Transc](./src/transcripts/shorts4_stacks.md)

- These frames are arranged in a stack. The frame for the most-recently called function is always on the top of the stack.
- When a new function is called, a new frame is pushed onto the top of the stack and becomes the active frame.
- When a function finishes its work, its frame is popped off of the stack, and the frame immediately below it becomes the new, active, function on the top of the stack. This function picks up immediately where it Ieft off.

## File Pointers
> [Transc](./src/transcripts/shorts4_file_ptr.md)

The ability to read data from and write data to files is the primary means of storing **persistent data**, data that does not disappear when your program stops running.

The abstraction of files that C provides is implemented in a data structure known as a `FILE`.
> Almost universally when working with files, we will be using pointers
to them, `FILE*`.

Some of the most common file input/output (I/O) functions that we'll be working with are:
- `fopen()`, opens the file as a pointer. Each file pointer have a specific operation and cannot be changed, only if closed
	```c
	FILE* ptr = fopen(<filename>, <operation>);
	```

- `fclose()`, closes the file pointer
	```c
	fclose(<file pointer>)
	```

- `fread()`, reads the file pointer (if the operation is set as `r`)
	```c
	fread(<buffer>, <size>, <qty>, <file pointer>)
	```

- `fgetc()`, gets a char from the file pointer
	```c
	char ch = fgetc(<file pointer>)
	```

This function mimics the `cat` from Linux :
```c
char ch;
while((ch = fgetc(ptr)) != EOF)
	printf("%c", ch);
```

- `fputc()`
- `fwrite()`, does the same of read, but to write.

---

# Exercises

## Practice Problems [#](https://cs50.harvard.edu/x/2023/problems/4/#week-4-practice-problems)

In addition to this week’s lab and problem set, you’re welcome to try any of these (optional!) practice problems:

-   Bottom Up [#](https://cs50.harvard.edu/x/2023/problems/4/bottomup/), for practice working with images and metadata
-   License [#](https://cs50.harvard.edu/x/2023/problems/4/license/), for practice working with files and file pointers

## Lab 4: Smiley or Volume
> Full code [here](./src/lab4.c)

### What to Do

1.  Log into [code.cs50.io](https://code.cs50.io) using your GitHub account
2.  Run `update50` in your codespace’s terminal window to ensure your codespace is up-to-date and, when prompted, click **Rebuild now**
3.  Submit one of:
    -   [Smiley](./smiley.md) [#](https://cs50.harvard.edu/x/2023/labs/4/smiley/)
    -   [Volume](./volume.md) [#](https://cs50.harvard.edu/x/2023/labs/4/volume/)

If you submit both Smiley and Volume, we’ll record the higher of your two scores.

## Problem Set 4
> Collaboration on problem sets is not permitted except to the extent that you may ask classmates and others for help so long as that help does not reduce to another doing your work for you, per the course’s policy on [academic honesty](https://cs50.harvard.edu/x/2023/psets/4/../../syllabus/#academic-honesty).
>
> The staff conducts random audits of submissions to CS50x. Students found to be in violation of this policy will be removed from the course. Students who have already completed CS50x, if found to be in violation, will have their CS50 Certificate permanently revoked.

## What to Do
> Be sure you have completed [Lab 4](https://cs50.harvard.edu/x/2023/psets/4/../../labs/4/) before beginning this problem set.

1.  Log into [code.cs50.io](https://code.cs50.io) using your GitHub account
2.  Run `update50` in your codespace’s terminal window to ensure your codespace is up-to-date and, when prompted, click **Rebuild now**
3.  Submit one of [Filter](./filter.md):
    -   [this version](https://cs50.harvard.edu/x/2023/psets/4/filter/less/) if feeling less comfortable
    -   [this version](https://cs50.harvard.edu/x/2023/psets/4/filter/more/) if feeling more comfortable
4.  Submit one of:
    -   [Recover](./recover.md) [#](https://cs50.harvard.edu/x/2023/psets/4/recover/)
    -   [Reverse](./reverse.md) [#](https://cs50.harvard.edu/x/2023/psets/4/reverse/)

If you submit both versions of Filter, we’ll record the higher of your two scores.

## Advice

-   Try out any of David’s programs from [Week 4](https://cs50.harvard.edu/x/2023/psets/4/../../weeks/4/).
-   If you see any errors when compiling your code with `make`, focus first on fixing the very first error you see, scrolling up as needed. If unsure what it means, try asking `help50` for help. For instance, if trying to compile `filter`, and
    
    ```
    make filter
    ```
    
    is yielding errors, try running
    
    ```
    help50 make filter
    ```
    
    instead!

