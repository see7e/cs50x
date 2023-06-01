---
title: CS50 - Week 2
tags: programação, cs50
use: Documentation
languages: C
dependences: CS50
---

> This material is distributed by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my understanding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Lecture 2](#lecture-2)
  - [Welcome!](#welcome)
  - [Compiling](#compiling)
  - [Debugging](#debugging)
    - [Figuring Out](#figuring-out)
  - [Arrays](#arrays)
  - [Strings](#strings)
  - [Command Line Arguments](#command-line-arguments)
  - [Exit Status](#exit-status)
  - [Cryptography](#cryptography)
  - [Summing Up](#summing-up)
- [Section](#section)
- [Shorts](#shorts)
  - [Functions](#functions)
  - [Variables and Scope](#variables-and-scope)
  - [Debugging](#debugging-1)
  - [Arrays](#arrays-1)
  - [Command  Line Arguments](#command--line-arguments)
- [Exercises](#exercises)
  - [Practice Problems 2 #](#practice-problems-2-)
  - [Lab 2: Scrabble](#lab-2-scrabble)
  - [Problem Set 2](#problem-set-2)
    - [What to Do](#what-to-do)
    - [Advice](#advice)

</details>

# Lecture 2

<details>
<summary>Keywords, lookup in <a href="./src/transcripts/lecture2.md">transcript</a></summary>

- lower level
- cyphertext
- encription
- compilers (`clang` x `gcc`)
- command line arguments
- function prototype
- blob ([*Binary large object*](https://www.gartner.com/en/information-technology/glossary/blob-binary-large-object))
- debugger
- breakpoint
- scope
- bits and bites
- floating point
- arguments
- cowsay
- exit status
- encryption X decryption

</details>

## Welcome!

-   In our previous session, we learned about C, a text-based programming language.

-   This week, we are going to take a deeper look at additional building-blocks that will support our goals of learning more about programming from the bottom up.

-   Fundamentally, in addition to the essentials of programming, this course is about problem-solving. Accordingly, we will also focus further on how to approach computer science problems.

## Compiling

-   _Encryption_ is the act of hiding plain text from prying eyes. _decrypting_, then, is the act of taking an encrypted piece of text and returning it to a human-readable form.

-   An encrypted piece of text may look like the following:
    
    ![encryption](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide008.png "encryption")
    
-   Recall that last week you learned about a _compiler_, a specialized computer program that converts _source code_ into _machine code_ that can be understood by a computer.

-   For example, you might have a computer program that looks like this:
    
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        printf("hello, world\n");
    }
    ```

> *Note that in the header (*`cs50.h`*) file there's only the function prototypes (function definitions), wich grabs from the function (*`cs50.c`*) file the full code.* 

-   A compiler will take the above code and turn it into the following machine code:
    
    ![machine code](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide012.png "machine code")
    
-   _VS Code_, the programming environment provided to you as a CS50 student, utilizes a compiler called **[`clang`](https://en.wikipedia.org/wiki/Clang)** or _c language_.

-   If you were to type `make hello`, it runs a command that executes clang to create an output file that you can run as a user.

-   VS Code has been pre-programmed such that `make` will run numerous command line arguments along with clang for your convenience as a user.

-   Consider the following code:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string name = get_string("What's your name? ");
        printf("hello, %s\n", name);
    }
    ```

-   You can attempt to enter into the terminal window: `clang -o hello hello.c`. You will be met by an error that indicates that clang does not know where to find the `cs50.h` library.

-   Attempting again to compile this code, run the following command in the terminal window:
	```bash
	clang -o hello hello.c -lcs50
	```
	 This will enable the compiler to access the `cs50.h` library.

- `-o` means *output*, this will set the name of the `.out` file.

-   Running in the terminal window `./hello`, your program will run as intended.

-   While the above is offered as an illustration, such that you can understand more deeply the process and concept of compiling code, using `make` in CS50 is perfectly fine and the expectation!

-   Compiling involves major steps, including the following:
    
    1. **PREPOCESSING** is where the header files in your code, designated by a `#` (such as `#include \<cs50.h\>`) are effectively copied and pasted into your file. During this step, the code from `cs50.h` is copied into your program. Similarly, just as your code contains `#include \<stdio.h\>`, code contained within `stdio.h` somewhere on your computer is copied to your program. This step can be visualized as follows:
    ```c
    // [...]
    string get_string(string prompt);
    int printf(string format, ...);
    // [...]
    
    int main(void)
    {
        string name = get_string("What's your name? ");
        printf("hello, %s\n", name);
    }
    ```
    
    2. **COMPILING** is where your program is converted into assembly code. This step can be visualized as follows:
        ![compiling](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide033.png "compiling")
        
    3. **ASSEMBLING** involves the compiler converting your assembly code into machine code. This step can be visualized as follows:
        ![assembling](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide038.png "assembling")
        
    4. **LINKING** step, code from your included libraries are converted also into machine code and combined with your code. The final executable file is then outputted.
        ![linking](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide049.png "linking")
        

## [Debugging](./bugs_and_debugging.md)

-   Everyone will make mistakes while coding.

-   Consider the following image from last week:
    ![mario](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide061.png "mario")
    
-   Further, consider the following code that has a bug purposely inserted within it:
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        for (int i = 0; i <= 3; i++)
        {
            printf("#\n");
        }
    }
    ```

-   Type `code buggy0.c` into the terminal window and write the above code.

-   Running this code, four bricks appear instead of the intended three.

### Figuring Out 

There's at least two good ways to figure out what the problem is

-   `printf` is a very useful way of debugging your code. You could modify your code as follows: 
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        for (int i = 0; i <= 3; i++)
        {
            printf("i is %i\n", i);
            printf("#\n");
        }
    }
    ```

-   Running this code, you will see numerous statements, including `i is 0`, `i is 1`, `i is 2`, and `i is 3`. Seeing this, you might realize that Further code needs to be corrected as follows:
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        for (int i = 0; i < 3; i++)
        {
            printf("#\n");
        }
    }
    ```
    
    *Notice the `<=` has been replaced with `<`.*

-   A second tool in debugging is called a _debugger_, a software tool created by programmers to help track down bugs in code. **In VS Code, a preconfigured debugger has been provided to you.** To utilize this debugger:

	1. Set a _breakpoint_ by clicking to the left of a line of your code, just to the left of the line number. When you click there, you will see a red dot appearing. Imagine this as a stop sign, asking the compiler to pause such that you can consider what’s happening in this part of your code.
	
    ![break point](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Debugging.png "break point")
    
    2. Run `debug50 ./buggy0`. You will notice that after the debugger comes to life that a line of your code will illuminate in a gold-like color. Quite literally, the code has _paused_ at this line of code. Notice in the top left corner how all local variables are being displayed, including `i`, which has a current value of `0`. At the top of your window, you can click the `step over` button and it will keep moving through your code. Notice how the value of `i` increases.
        While **this tool will not show you where your bug is, it will help you slow down and see how your code is running step by step**.
        To illustrate a third means of debugging, please start a new file by running `code buggy1.c` in your terminal window. Write your code as follows:
        ```c
        #include <cs50.h>
        #include <stdio.h>
        
        int get_negative_int(void);
        
        int main(void)
        {
            int i = get_negative_int();
            printf("%i\n", i);
        }
        
        // Prompt user for positive integer
        int get_negative_int(void)
        {
            int n;
            do
            {
                n = get_int("Negative Integer: ");
            }
            while (n < 0);
            return n;
        }
        ```
        Notice `get_negative_int` is designed to get a negative integer from the user.
        -   Running `make buggy1`, you’ll notice that it does not do as intended. It accepts positive integers and seems to ignore negative ones.
        -   As before, set a breakpoint at a line of your code. Best to set a breakpoint at `int i = get_negative_int`. Now, run `debug50 buggy1`.
        -   Unlike before, where you utilized the `step over` button at the top of the window, use the `step into` button. This will take the debugger into your `get_negative_int` function. Notice how doing this will show you that you are, indeed, stuck in the `do while` loop.
        -   With this knowledge, you might consider why you are stuck in this loop, leading you to edit your code as follows:
        ```c
        #include <cs50.h>
        #include <stdio.h>
        
        int get_negative_int(void);
        
        int main(void)
        {
            int i = get_negative_int();
            printf("%i\n", i);
        }
        
        // Prompt user for positive integer
        int get_negative_int(void)
        {
            int n;
            do
            {
                n = get_int("Negative Integer: ");
            }
            while (n >= 0);
            return n;
        }
        ```
        Notice `n < 0` has been changed.
	3.   A final form of debugging is called _rubber duck debugging_. When you are having challenges with your code, consider how speaking out loud to, quite literally, a rubber duck about the code problem. If you’d rather not talk to a small plastic duck, you are welcome to speak to a human near you! They need not understand how to program: Speaking with them is an opportunity for you to speak about your code.

## Arrays

-   In Week 0, we talked about *data types* such as `bool`, `int`, `char`, `string`, etc.
-   Each data type requires a certain amount of system resources:
    -   `bool` 1 byte
    -   `int` 4 bytes
    -   `long` 8 bytes
    -   `float` 4 bytes
    -   `double` 8 bytes
    -   `char` 1 byte
    -   `string` (`n*char`) bytes
-   Inside of your computer, you have a finite amount of memory available.
    ![memory](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide084.png "memory")
    
-   Physically, on the memory of your computer, you can imagine how specific types of data are stored on your computer. You might imagine that a `char`, which only requires 1 byte of memory, may look as follows:
    ![1 byte](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide087.png "1 byte")
    
-   Similarly, an `int`, which requires 4 bytes might look as follows:
    
    ![4 bytes](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide088.png "4 bytes")
    
-   We can create a program that explores these concepts. Inside your terminal, type `code scores.c` and write code as follows:
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        // Scores
        int score1 = 72;
        int score2 = 73;
        int score3 = 33;
    
        // Print average
        printf("Average: %f\n", (score1 + score2 + score3) / 3.0);
    }
    ```
    
    Notice that the number on the right is a floating point value of `3.0`, such that the calculation is rendered as a floating point value in the end.

-   Running `make scores`, the program runs.
-   You can imagine how these variables are stored in memory:
    
    ![scores in memory](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide098.png "scores in memory")
    
-   _Arrays_ are a way of storing data back-to-back in memory such that this data is easily accessible.
-   `int scores[3]` is a way of telling the compiler to provide you three back-to-back places in memory of size `int` to store three `scores`. Considering our program, you can revise your code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Scores
        int scores[3];
        scores[0] = 72;
        scores[1] = 73;
        scores[2] = 33;
    
        // Print average
        printf("Average: %f\n", (scores[0] + scores[1] + scores[2]) / 3.0);
    }
    ```
    
    Notice that `score[0]` examines the value at this location of memory by `indexing into` the array called `scores` at location `0` to see what value is stored there.

-   You can see how while the above code works, there is still an opportunity for improving our code. Revise your code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Get scores
        int scores[3];
        for (int i = 0; i < 3; i++)
        {
            scores[i] = get_int("Score: ");
        }
    
        // Print average
        printf("Average: %f\n", (scores[0] + scores[1] + scores[2]) / 3.0);
    }
    ```
    
    Notice how we index into `scores` by using `scores[i]` where `i` is supplied by the `for` loop.

-   We can simplify or _abstract away_ the calculation of the average. Modify your code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    // Constant
    const int N = 3;
    
    // Prototype
    float average(int length, int array[]);
    
    int main(void)
    {
        // Get scores
        int scores[N];
        for (int i = 0; i < N; i++)
        {
            scores[i] = get_int("Score: ");
        }
    
        // Print average
        printf("Average: %f\n", average(N, scores));
    }
    
    float average(int length, int array[])
    {
        // Calculate average
        int sum = 0;
        for (int i = 0; i < length; i++)
        {
            sum += array[i];
        }
        return sum / (float) length;
    }
    ```
    
    Notice that a new function called `average` is declared. Further, notice that a `const` or constant value of `N` is declared. Most importantly, notice how the `average` function takes `int array[]`, which means that the compiler passes an array to this function. 
    An improvement could be to create a loop that runs inside of the array and calculate de variabe `length`.

-   Not only can arrays be containers: They can be passed between functions.

## Strings

-   A `string` is simply an array of variables of type `char`: an array of characters. Defined in the header file of `cs50.h`.
	```c
	/**
	 * Our own type for (pointers to) strings.
	 */
	typedef char *string;
	```
-   Considering the following image, you can see how a string is an array of characters that begins with the first character and ends with a special character called a `NULL character`:
    ![hi with terminator](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide116.png "hi with terminator")
    
-   Imagining this in decimal, your array would look like the following:
    ![hi with decimal](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide117.png "hi with decimal")
    
-   Implementing this in your own code, type `code hi.c` in the terminal window and write code as follows:
    ```c
    #include <stdio.h>
    
    int main(void)
    {
        char c1 = 'H';
        char c2 = 'I';
        char c3 = '!';
    
        printf("%i %i %i\n", c1, c2, c3);
    }
    ```
    
    Notice that this will output the decimal values of each character.

-   To further understand how a `string` works, revise your code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string s = "HI!";
        printf("%i %i %i\n", s[0], s[1], s[2]);
    }
    ```
    
    Notice how the `printf` statement presents three values from our array called `s`.

-   Let’s imagine we want to say both `HI!` and `BYE!`. Modify your code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string s = "HI!";
        string t = "BYE!";
        
        printf("%s\n", s);
        printf("%s\n", t);
    }
    ```
    
    Notice that two strings are declared and used in this example.

-   You can visualize this as follow:
    ![hi and bye](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide126.png "hi and bye")
    
-   We can further improve this code. Modify your code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string words[2];
    
        words[0] = "HI!";
        words[1] = "BYE!";
    
        printf("%s\n", words[0]);
        printf("%s\n", words[1]);
    }
    ```
    
    Notice that both strings are stored within a single array of type `string`. So this is properly an a Matrix structure.

-   A common problem within programming, and perhaps C more specifically, is to discover the length of an array. How could we implement this in code? Type `code length.c` in the terminal window and code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        // Prompt for user's name
        string name = get_string("Name: ");
    
        // Count number of characters up until '\0' (aka NUL)
        int n = 0;
        while (name[n] != '\0')
        {
            n++;
        }
        printf("%i\n", n);
    }
    ```
    
    Notice that this code loops until the `NULL` character is found.

-   Since this is such a common problem within programming, other programmers have created code in the **[`string.h`](https://manual.cs50.io/#string.h)** library to find the length of a string. You can find the length of a string by modifying your code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        // Prompt for user's name
        string name = get_string("Name: ");
        int length = strlen(name);
        printf("%i\n", length);
    }
    ```
    
    Notice that this code uses the `string.h` library, declared at the top of the file. Further, it uses a function from that library called `strlen`, which calculates the length of the string passed to it.

-   **[`ctype.h`](https://manual.cs50.io/#ctype.h)** is another library that is quite useful. Imagine we wanted to create a program that converted all lowercase characters to uppercase ones. In the terminal window type `code uppercase.c` and write code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        string s = get_string("Before: ");
        printf("After:  ");
        for (int i = 0, n = strlen(s); i < n; i++)
        {
            if (s[i] >= 'a' && s[i] <= 'z')
            {
                printf("%c", s[i] - 32);
            }
            else
            {
                printf("%c", s[i]);
            }
        }
        printf("\n");
    }
    ```
    
    Notice that this code _iterates_ through each value in the string. The program looks at each character. If the character is lowercase, it subtracts the value 32 from it to convert it to uppercase.

-   Recalling our previous work from last week, you might remember this ASCII values chart:
    ![ascii](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide120.png "ascii")
    
-   **When a lowercase character has `32` subtracted from it, it results in an uppercase version of that same character.**

-   While the program does what we want, there is an easier way using the `ctype.h` library. Modify your program as follows:
    ```c
    #include <cs50.h>
    #include <ctype.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        string s = get_string("Before: ");
        printf("After:  ");
        for (int i = 0, n = strlen(s); i < n; i++)
        {
            if (islower(s[i]))
            {
                printf("%c", toupper(s[i]));
            }
            else
            {
                printf("%c", s[i]);
            }
        }
        printf("\n");
    }
    ```
    
    Notice that the program uses `islower` to detect if each character is uppercase or lowercase. Then, the `toupper` function is passed `s[i]`. Each character (if lowercase) is converted to uppercase.

-   Again, while this program does what is desired, there is an opportunity for improvement. As the documentation for `ctype.h` states, `toupper` is smart enough to know that if it is passed what is already an uppercase letter, it will simply ignore it. Therefore, we no longer need our `if` statement. You can simplify this code as follows:
    ```c
    #include <cs50.h>
    #include <ctype.h>
    #include <stdio.h>
    #include <string.h>
    
    int main(void)
    {
        string s = get_string("Before: ");
        printf("After:  ");
        for (int i = 0, n = strlen(s); i < n; i++)
        {
            printf("%c", toupper(s[i]));
        }
        printf("\n");
    }
    ```
    
    Notice that this code is quite simplified, removing the unnecessary `if` statement.

## Command Line Arguments

-   `Command-line arguments` are those arguments that are passed to your program at the command line. For example, all those statements you typed after `clang` are considered command line arguments. You can use these arguments in your own programs!
-   In your terminal window, type `code greet.c` and write code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string name = get_string("What's your name? ");
        printf("hello, %s\n", name);
    }
    ```
    
    Notice that this says `hello` to the user.

-   Replacing the `void` sentence in `int main()` to `int argc` and `char argv[]`. Modify your code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(int argc, string argv[])
    {
        if (argc == 2)
        {
            printf("hello, %s\n", argv[1]);
        }
        else
        {
            printf("hello, world\n");
        }
    }
    ```
    
    -  **`int argc`, stands for "argument count", is the number of command line arguments** passed along the call (`./file`) of the program, and, 
    - **`char argv[]` stands for "argument vector", which is an array of the characters** passed as arguments at the command line.

- **`char argv[i]` index starts in 0 wich is the program file (`./file`) itself  and then the arguments passed on the CLI.**

-   Therefore, using the syntax of this program, executing `./greet David` would result in the program saying `hello, David`.

## Exit Status

-   When a program ends, a special exit code is provided to the computer.
-   When a program exits without error, a status code of `0` is provided the computer. Often, when an error occurs that results in the program ending, a status of `1` is provided by the computer.
-   You could write a program as follows that illustrates this by typing `code status.c` and writing code as follows:
    ```c
    #include <cs50.h>
    #include <stdio.h>
    
    int main(int argc, string argv[])
    {
        if (argc != 2)
        {
            printf("Missing command-line argument\n");
            return 1;
        }
        printf("hello, %s\n", argv[1]);
        return 0;
    }
    ```
    
    Notice that if you fail to provide `./status David`, you will get an exit status of `1`. However, if you do provide `./status David`, you will get an exit status of `0`.
    **This value can be retrieved using `echo $?`.**

-   You can imagine how you might use portions of the above program to check if a user provided the correct number of command-line arguments.

## Cryptography

-   Cryptography is the art of ciphering and deciphering a message.
-   `plaintext` and a `key` are provided to a `cipher`, resulting in ciphered text.
    ![cryptography](https://cs50.harvard.edu/x/2023/notes/2//cs50Week2Slide153.png "cryptography")

-   The key is a special argument passed to the cipher along with the plaintext. The cipher uses the key to make decisions about how to implement its cipher algorithm.

## Summing Up

In this lesson, you learned more details about compiling and how data is stored within a computer. Specifically, you learned…

-   Generally, how a compiler works.
-   How to debug your code using four methods.
-   How to utilize arrays within your code.
-   How arrays store data in back to back portions of memory.
-   How strings are simply arrays of characters.
-   How to interact with arrays in your code.
-   How command-line arguments can be passed to your programs.
-   The basic building-blocks of cryptography.

See you next time!

---
# Section 
> [Transcript](./src/transcripts/section2.md)

- What are the steps involved in compilation?
- What are arrays?
- What are strings?
- What's the point of command-line arguments?
- What makes for good design?

---

# Shorts

## Functions 
> [Transc](./src/transcripts/shorts2_functions.md)

## Variables and Scope 
> [Transc](./src/transcripts/shorts2_variables.md)

Scope is a characteristic of a variable that defines from which functions that variable may be accessed.
- Local variables can only be accessed within the functions in which they are created.
- Global variables can be accessed by any function in the program.

Why does this distinction matter? For the most part, local variables in C are passed by value in function calls.

When a variable is passed by value, the callee receives a copy of the passed variable, not the
variable itself. That means that the variable in the caller is unchanged unless overwritten.

## Debugging

- Step througthrough ([Transc](./src/transcripts/shorts2_debug1.md))
- Step into ([Transc](./src/transcripts/shorts2_debug2.md))

`debug50` is a tool configured and used along the VSCode to verify the steps of the code, verify what is happening with the variables and their memory address.

## Arrays 
> [Transc](./src/transcripts/shorts2_arrays.md)

## Command  Line Arguments
> [Transc](./src/transcripts/shorts2_cla.md)

- `int argc`, stores the count of elements passed in the CLI.
- `char **argv`, stores always arrays of `char`'s i.e. `strings`.


---

# Exercises

## Practice Problems 2 [#](https://cs50.harvard.edu/x/2023/problems/2/#week-2-practice-problems)

In addition to this week’s lab and problem set, you’re welcome to try any of these (optional!) practice problems:

-   Hours [#](https://cs50.harvard.edu/x/2023/problems/2/hours/), for practice with arrays, passing arrays as parameters to a function, integer division and type casting
-   N0 V0w3ls [#](https://cs50.harvard.edu/x/2023/problems/2/no-vowels/), for practice with strings, command-line arguments, and writing an entire program from scratch
-   Password [#](https://cs50.harvard.edu/x/2023/problems/2/password/), for practice iterating through a string, using the `ctype` library, and using Boolean variables

## [Lab 2: Scrabble](./lab2.md)
> Full code [here](./src/lab2.c)

## Problem Set 2

Collaboration on problem sets is not permitted except to the extent that you may ask classmates and others for help so long as that help does not reduce to another doing your work for you, per the course’s policy on [academic honesty](https://cs50.harvard.edu/x/2023/psets/2//../../syllabus/#academic-honesty).

The staff conducts random audits of submissions to CS50x. Students found to be in violation of this policy will be removed from the course. Students who have already completed CS50x, if found to be in violation, will have their CS50 Certificate permanently revoked.

### What to Do
Be sure you have completed [Lab 2](#lab-2-scrabble) [#](https://cs50.harvard.edu/x/2023/labs/2/) before beginning this problem set.

1.  Log into [code.cs50.io](https://code.cs50.io) using your GitHub account
2.  Run `update50` in your codespace’s terminal window to ensure your codespace is up-to-date and, when prompted, click **Rebuild now**
3.  Submit [Readability](./readability.md) [#](https://cs50.harvard.edu/x/2023/psets/2/readability/)
4.  Submit one of:
    -   [Bulbs](./bulbs.md) [#](https://cs50.harvard.edu/x/2023/psets/2/bulbs/), if feeling less comfortable
    -   [Caesar](./caesar.md) [#](https://cs50.harvard.edu/x/2023/psets/2/caesar/), if feeling less comfortable
    -   [Substitution](./substitution.md) [#](https://cs50.harvard.edu/x/2023/psets/2/substitution/), if feeling more comfortable
    -   [Wordle50](./wordle50.md) [#](https://cs50.harvard.edu/x/2023/psets/2/wordle50/), if feeling more comfortable

If you submit more than one of Bulbs, Caesar, Substitution, or Wordle50, we’ll record the single highest of your scores among those problems.

### Advice

-   Try out any of David’s programs from class via Week 2’s examples.
-   To see the manual pages for C functions, visit [manual.cs50.io](https://manual.cs50.io/).
-   If you see any errors when compiling your code with `make`, focus first on fixing the very first error you see, scrolling up as needed. If unsure what it means, try asking `help50` for help. For instance, if trying to compile `readability`, and
	
    ```bash
    make readability
    ```
    
    is yielding errors, try running
    
    ```bash
    help50 make readability
    ```
    
    instead!