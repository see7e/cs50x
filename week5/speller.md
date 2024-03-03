---
title: Problem Set 5 - Speller
tags: programação, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Speller](#speller)
  - [Getting Started #](#getting-started-)
  - [Distribution](#distribution)
    - [Understanding](#understanding)
      - [`dictionary.h`](#dictionaryh)
      - [`dictionary.c`](#dictionaryc)
      - [`speller.c`](#spellerc)
      - [`texts/`](#texts)
      - [`Makefile`](#makefile)
  - [Specification](#specification)
  - [Hints](#hints)
  - [Testing](#testing)
    - [`check50`](#check50)
    - [style50](#style50)
  - [Staff’s Solution](#staffs-solution)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Submitted](#submitted)

</details>

# Speller
> Full code [here](./src/speller/dictionary.c)

**Be sure to read this specification in its entirety before starting so you know what to do and how to do it!**

For this problem, you’ll implement a program that spell-checks a file, a la the below, using a hash table.

```bash
$ ./speller texts/lalaland.txt
MISSPELLED WORDS

[...]
AHHHHHHHHHHHHHHHHHHHHHHHHHHHT
[...]
Shangri
[...]
fianc
[...]
Sebastian\'s
[...]

WORDS MISSPELLED:
WORDS IN DICTIONARY:
WORDS IN TEXT:
TIME IN load:
TIME IN check:
TIME IN size:
TIME IN unload:
TIME IN TOTAL:
```

## Getting Started [#](https://cs50.harvard.edu/x/2023/psets/5/speller//#getting-started)

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/5/speller.zip
```

in order to download a ZIP called `speller.zip` into your codespace.

Then execute

```bash
unzip speller.zip
```

to create a folder called `speller`. You no longer need the ZIP file, so you can execute

```bash
rm speller.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd speller
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
speller/ $
```

Execute `ls` by itself, and you should see a few files and folders:

```bash
dictionaries/  dictionary.c  dictionary.h  keys/  Makefile  speller.c  speller50  texts/
```

If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Distribution

### Understanding

Theoretically, on input of size _n_, an algorithm with a running time of _n_ is “asymptotically equivalent,” in terms of _O_, to an algorithm with a running time of _2n_. Indeed, when describing the running time of an algorithm, we typically focus on the dominant (i.e., most impactful) term (i.e., _n_ in this case, since _n_ could be much larger than 2). In the real world, though, the fact of the matter is that _2n_ feels twice as slow as _n_.

The challenge ahead of you is to implement the fastest spell checker you can! By “fastest,” though, we’re talking actual “wall-clock,” not asymptotic, time.

In `speller.c`, we’ve put together a program that’s designed to spell-check a file after loading a dictionary of words from disk into memory. That dictionary, meanwhile, is implemented in a file called `dictionary.c`. (It could just be implemented in `speller.c`, but as programs get more complex, it’s often convenient to break them into multiple files.) The prototypes for the functions therein, meanwhile, are defined not in `dictionary.c` itself but in `dictionary.h` instead. That way, both `speller.c` and `dictionary.c` can `#include` the file. Unfortunately, we didn’t quite get around to implementing the loading part. Or the checking part. Both (and a bit more) we leave to you! But first, a tour.

#### `dictionary.h`

Open up `dictionary.h`, and you’ll see some new syntax, including a few lines that mention `DICTIONARY_H`. No need to worry about those, but, if curious, those lines just ensure that, even though `dictionary.c` and `speller.c` (which you’ll see in a moment) `#include` this file, `clang` will only compile it once.

Next notice how we `#include` a file called `stdbool.h`. That’s the file in which `bool` itself is defined. You’ve not needed it before, since the CS50 Library used to `#include` that for you.

Also notice our use of `#define`, a “preprocessor directive” that defines a “constant” called `LENGTH` that has a value of `45`. It’s a constant in the sense that you can’t (accidentally) change it in your own code. In fact, `clang` will replace any mentions of `LENGTH` in your own code with, literally, `45`. In other words, it’s not a variable, just a find-and-replace trick.

Finally, notice the prototypes for five functions: `check`, `hash`, `load`, `size`, and `unload`. Notice how three of those take a pointer as an argument, per the `*`:

```c
bool check(const char *word);
unsigned int hash(const char *word);
bool load(const char *dictionary);
```

Recall that `char *` is what we used to call `string`. So those three prototypes are essentially just:

```c
bool check(const string word);
unsigned int hash(const string word);
bool load(const string dictionary);
```

And `const`, meanwhile, just says that those strings, when passed in as arguments, must remain constant; you won’t be able to change them, accidentally or otherwise!

#### `dictionary.c`

Now open up `dictionary.c`. Notice how, atop the file, we’ve defined a `struct` called `node` that represents a node in a hash table. And we’ve declared a global pointer array, `table`, which will (soon) represent the hash table you will use to keep track of words in the dictionary. The array contains `N` node pointers, and we’ve set `N` equal to `26` for now, to match with the default `hash` function as described below. You will likely want to increase this depending on your own implementation of `hash`.

Next, notice that we’ve implemented `load`, `check`, `size`, and `unload`, but only barely, just enough for the code to compile. Notice too that we’ve implemented `hash` with a sample algorithm based on the first letter of the word. Your job, ultimately, is to re-implement those functions as cleverly as possible so that this spell checker works as advertised. And fast!

#### `speller.c`

Okay, next open up `speller.c` and spend some time looking over the code and comments therein. You won’t need to change anything in this file, and you don’t need to understand its entirety, but do try to get a sense of its functionality nonetheless. Notice how, by way of a function called `getrusage`, we’ll be “benchmarking” (i.e., timing the execution of) your implementations of `check`, `load`, `size`, and `unload`. Also notice how we go about passing `check`, word by word, the contents of some file to be spell-checked. Ultimately, we report each misspelling in that file along with a bunch of statistics.

Notice, incidentally, that we have defined the usage of `speller` to be

```bash
Usage: speller [dictionary] text
```

where `dictionary` is assumed to be a file containing a list of lowercase words, one per line, and `text` is a file to be spell-checked. As the brackets suggest, provision of `dictionary` is optional; if this argument is omitted, `speller` will use `dictionaries/large` by default. In other words, running

```bash
./speller text
```

will be equivalent to running

```bash
./speller dictionaries/large text
```

where `text` is the file you wish to spell-check. Suffice it to say, the former is easier to type! (Of course, `speller` will not be able to load any dictionaries until you implement `load` in `dictionary.c`! Until then, you’ll see `Could not load`.)

Within the default dictionary, mind you, are 143,091 words, all of which must be loaded into memory! In fact, take a peek at that file to get a sense of its structure and size. Notice that every word in that file appears in lowercase (even, for simplicity, proper nouns and acronyms). From top to bottom, the file is sorted lexicographically, with only one word per line (each of which ends with `\n`). No word is longer than 45 characters, and no word appears more than once. During development, you may find it helpful to provide `speller` with a `dictionary` of your own that contains far fewer words, lest you struggle to debug an otherwise enormous structure in memory. In `dictionaries/small` is one such dictionary. To use it, execute

```bash
./speller dictionaries/small text
```

where `text` is the file you wish to spell-check. Don’t move on until you’re sure you understand how `speller` itself works!

Odds are, you didn’t spend enough time looking over `speller.c`. Go back one square and walk yourself through it again!

#### `texts/`

So that you can test your implementation of `speller`, we’ve also provided you with a whole bunch of texts, among them the script from _La La Land_, the text of the Affordable Care Act, three million bytes from Tolstoy, some excerpts from _The Federalist Papers_ and Shakespeare, and more. So that you know what to expect, open and skim each of those files, all of which are in a directory called `texts` within your `pset5` directory.

Now, as you should know from having read over `speller.c` carefully, the output of `speller`, if executed with, say,

```bash
./speller texts/lalaland.txt
```

will eventually resemble the below.

Below’s some of the output you’ll see. For information’s sake, we’ve excerpted some examples of “misspellings.” And lest we spoil the fun, we’ve omitted our own statistics for now.

```bash
MISSPELLED WORDS

[...]
AHHHHHHHHHHHHHHHHHHHHHHHHHHHT
[...]
Shangri
[...]
fianc
[...]
Sebastian's
[...]

WORDS MISSPELLED:
WORDS IN DICTIONARY:
WORDS IN TEXT:
TIME IN load:
TIME IN check:
TIME IN size:
TIME IN unload:
TIME IN TOTAL:
```

`TIME IN load` represents the number of seconds that `speller` spends executing your implementation of `load`. `TIME IN check` represents the number of seconds that `speller` spends, in total, executing your implementation of `check`. `TIME IN size` represents the number of seconds that `speller` spends executing your implementation of `size`. `TIME IN unload` represents the number of seconds that `speller` spends executing your implementation of `unload`. `TIME IN TOTAL` is the sum of those four measurements.

**Note that these times may vary somewhat across executions of `speller`, depending on what else your codespace is doing, even if you don’t change your code.**

Incidentally, to be clear, by “misspelled” we simply mean that some word is not in the `dictionary` provided.

#### `Makefile`

And, lastly, recall that `make` automates compilation of your code so that you don’t have to execute `clang` manually along with a whole bunch of switches. However, as your programs grow in size, `make` won’t be able to infer from context anymore how to compile your code; you’ll need to start telling `make` how to compile your program, particularly when they involve multiple source (i.e., `.c`) files, as in the case of this problem. And so we’ll utilize a `Makefile`, a configuration file that tells `make` exactly what to do. Open up `Makefile`, and you should see four lines:

1.  The first line tells `make` to execute the subsequent lines whenever you yourself execute `make speller` (or just `make`).
2.  The second line tells `make` how to compile `speller.c` into machine code (i.e., `speller.o`).
3.  The third line tells `make` how to compile `dictionary.c` into machine code (i.e., `dictionary.o`).
4.  The fourth line tells `make` to link `speller.o` and `dictionary.o` in a file called `speller`.

**Be sure to compile `speller` by executing `make speller` (or just `make`). Executing `make dictionary` won’t work!**

## Specification

Alright, the challenge now before you is to implement, in order, `load`, `hash`, `size`, `check`, and `unload` as efficiently as possible using a hash table in such a way that `TIME IN load`, `TIME IN check`, `TIME IN size`, and `TIME IN unload` are all minimized. To be sure, it’s not obvious what it even means to be minimized, inasmuch as these benchmarks will certainly vary as you feed `speller` different values for `dictionary` and for `text`. But therein lies the challenge, if not the fun, of this problem. This problem is your chance to design. Although we invite you to minimize space, your ultimate enemy is time. But before you dive in, some specifications from us.

-   You may not alter `speller.c` or `Makefile`.
-   You may alter `dictionary.c` (and, in fact, must in order to complete the implementations of `load`, `hash`, `size`, `check`, and `unload`), but you may not alter the declarations (i.e., prototypes) of `load`, `hash`, `size`, `check`, or `unload`. You may, though, add new functions and (local or global) variables to `dictionary.c`.
-   You may change the value of `N` in `dictionary.c`, so that your hash table can have more buckets.
-   You may alter `dictionary.h`, but you may not alter the declarations of `load`, `hash`, `size`, `check`, or `unload`.
-   Your implementation of `check` must be case-insensitive. In other words, if `foo` is in dictionary, then `check` should return true given any capitalization thereof; none of `foo`, `foO`, `fOo`, `fOO`, `fOO`, `Foo`, `FoO`, `FOo`, and `FOO` should be considered misspelled.
-   Capitalization aside, your implementation of `check` should only return `true` for words actually in `dictionary`. Beware hard-coding common words (e.g., `the`), lest we pass your implementation a `dictionary` without those same words. Moreover, the only possessives allowed are those actually in `dictionary`. In other words, even if `foo` is in `dictionary`, `check` should return `false` given `foo's` if `foo's` is not also in `dictionary`.
-   You may assume that any `dictionary` passed to your program will be structured exactly like ours, alphabetically sorted from top to bottom with one word per line, each of which ends with `\n`. You may also assume that `dictionary` will contain at least one word, that no word will be longer than `LENGTH` (a constant defined in `dictionary.h`) characters, that no word will appear more than once, that each word will contain only lowercase alphabetical characters and possibly apostrophes, and that no word will start with an apostrophe.
-   You may assume that `check` will only be passed words that contain (uppercase or lowercase) alphabetical characters and possibly apostrophes.
-   Your spell checker may only take `text` and, optionally, `dictionary` as input. Although you might be inclined (particularly if among those more comfortable) to “pre-process” our default dictionary in order to derive an “ideal hash function” for it, you may not save the output of any such pre-processing to disk in order to load it back into memory on subsequent runs of your spell checker in order to gain an advantage.
-   Your spell checker must not leak any memory. Be sure to check for leaks with `valgrind`.
-   **The hash function you write should ultimately be your own, not one you search for online.** There are many ways to implement a hash function beyond using the first character (or characters) of a word. Consider a hash function that uses a sum of ASCII values or the length of a word. A good hash function tends to reduce “collisions” and has a fairly even distribution across hash table “buckets”.

Alright, ready to go?

-   Implement `load`.
-   Implement `hash`.
-   Implement `size`.
-   Implement `check`.
-   Implement `unload`.


## Hints

To compare two strings case-insensitively, you may find [`strcasecmp`](https://man.cs50.io/3/strcasecmp) (declared in `strings.h`) useful! You’ll likely also want to ensure that your hash function is case-insensitive, such that `foo` and `FOO` have the same hash value.

Ultimately, be sure to `free` in `unload` any memory that you allocated in `load`! Recall that `valgrind` is your newest best friend. Know that `valgrind` watches for leaks while your program is actually running, so be sure to provide command-line arguments if you want `valgrind` to analyze `speller` while you use a particular `dictionary` and/or text, as in the below. Best to use a small text, though, else `valgrind` could take quite a while to run.

```bash
valgrind ./speller texts/cat.txt
```

If you run `valgrind` without specifying a `text` for `speller`, your implementations of `load` and `unload` won’t actually get called (and thus analyzed).

If unsure how to interpret the output of `valgrind`, do just ask `help50` for help:

```bash
help50 valgrind ./speller texts/cat.txt
```

## Testing

How to check whether your program is outting the right misspelled words? Well, you’re welcome to consult the “answer keys” that are inside of the `keys` directory that’s inside of your `speller` directory. For instance, inside of `keys/lalaland.txt` are all of the words that your program _should_ think are misspelled.

You could therefore run your program on some text in one window, as with the below.

```bash
./speller texts/lalaland.txt
```

And you could then run the staff’s solution on the same text in another window, as with the below.

```bash
./speller50 texts/lalaland.txt
```

And you could then compare the windows visually side by side. That could get tedious quickly, though. So you might instead want to “redirect” your program’s output to a file, as with the below.

```bash
./speller texts/lalaland.txt > student.txt
./speller50 texts/lalaland.txt > staff.txt
```

You can then compare both files side by side in the same window with a program like `diff`, as with the below.

```bash
diff -y student.txt staff.txt
```

Alternatively, to save time, you could just compare your program’s output (assuming you redirected it to, e.g., `student.txt`) against one of the answer keys without running the staff’s solution, as with the below.

```bash
diff -y student.txt keys/lalaland.txt
```

If your program’s output matches the staff’s, `diff` will output two columns that should be identical except for, perhaps, the running times at the bottom. If the columns differ, though, you’ll see a `>` or `|` where they differ. For instance, if you see

```bash
MISSPELLED WORDS                                                MISSPELLED WORDS

TECHNO                                                          TECHNO
L                                                               L
                                                              > Thelonious
Prius                                                           Prius
                                                              > MIA
L                                                               L
```

that means your program (whose output is on the left) does not think that `Thelonious` or `MIA` is misspelled, even though the staff’s output (on the right) does, as is implied by the absence of, say, `Thelonious` in the lefthand column and the presence of `Thelonious` in the righthand column.

### `check50`

To test your code less manually (though still not exhaustively), you may also execute the below.

```
check50 cs50/problems/2023/x/speller
```

Note that `check50` will also check for memory leaks, so be sure you’ve run `valgrind` as well.

### style50

Execute the below to evaluate the style of your code using `style50`.

```
style50 dictionary.c
```

## Staff’s Solution

How to assess just how fast (and correct) your code is? Well, as always, feel free to play with the staff’s solution, as with the below, and compare its numbers against yours.

```bash
./speller50 texts/lalaland.txt
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/speller
```

---

# Walkthrough
> Full code [here](./src/speller/dictionary.c)

1.  **`bool check(const char *word)`** 
   The `check` function should search for the given `word` in the dictionary. You'll need to implement the logic to traverse the linked list at the corresponding hash index and check if the word exists. If found, return `true`; otherwise, return `false`.

Here's a modified version of the `check` function:

```c
{
    // Get the hash value for the word
    unsigned int index = hash(word);
    
    // Traverse the linked list at the hash index
    node *cursor = table[index];
    while (cursor != NULL)
    {
        // Compare the word with the current node's word
        if (strcasecmp(word, cursor->word) == 0)
        {
            // Word found in the dictionary
            return true;
        }
        
        // Move to the next node
        cursor = cursor->next;
    }
    
    // Word not found in the dictionary
    return false;
}
```

2.  **`unsigned int hash(const char *word)`** 
   The `hash` function is responsible for converting a word into a (hash) value. Like in the previous example in the Lecture, there's a possibility to lookup the first character of the word.
   
   The first implementation (below) only considers the first character of the word,

   ```c
	unsigned int hash(const char *word)
	{
	    return toupper(word[0]) - 'A';
	}
	```

   which is not an ideal hash function. Here's an example of a few words and their corresponding hash values using the original `hash` function implementation:
   
   |Word|Hash value|
   |:-:|:-:|
   |"apple"|$65 - 65 = 0$|
   |"Banana"|$66 - 65 = 1$|
   |"cat"|$67 - 65 = 2$|
   |"Dog"|$68 - 65 = 3$|
   |"elephant"|$69 - 65 = 4$|
   |"Frog"|$70 - 65 = 5$|
   |"grape"|$71 - 65 = 6$|
   |"Horse"|$72 - 65 = 7$|

   You can improve it by considering multiple characters of the word:

```c
{
    // Initialize the hash value
    unsigned int hash_value = 0;
    
    // Calculate the hash value by considering the first three characters
    for (int i = 0; i < 3 && word[i] != '\0'; i++)
    {
        hash_value = (hash_value * 26) + (toupper(word[i]) - 'A');
    }
    
    // Return the hash value within the range of the hash table size
    return hash_value % N;
}
```

> Is important to divide the value calculated in the function by the size of the array to avoid segmentation faults.

For "*apple*"
-   For the first character 'a', we calculate $(0 * 26) + (0) = 0 + 0 = 0$.
-   For the second character 'p', we calculate $(0 * 26) + (15) = 0 + 15 = 15$.
-   For the third character 'p', we calculate $(15 * 26) + (15) = 390 + 15 = 405$.
-   At least $405 \%N = 13$ 

3.  **`bool load(const char *dictionary)`** 
   The `load` function should read the dictionary file and insert each word into the hash table. You'll need to open the file, read each word, create a new node for each word, calculate the hash value, and insert the node at the corresponding index in the hash table.
   
   Here's a modified version of the `load` function:

```c
{
    // Open the dictionary file
    FILE *file = fopen(dictionary, "r");
    if (file == NULL)
    {
        return false;
    }
    
    // Clear the hash table
    for (int i = 0; i < N; i++)
    {
        table[i] = NULL;
    }
    
    // Buffer to store each word read from the file
    char buffer[LENGTH + 1];
    
    // Read words from the file until the end is reached
    while (fscanf(file, "%s", buffer) != EOF)
    {
        // Create a new node for the word
        node *new_node = malloc(sizeof(node));
        if (new_node == NULL)
        {
            fclose(file);
            return false;
        }
        
        // Copy the word into the node
        strcpy(new_node->word, buffer);
        
        // Calculate the hash value
        unsigned int index = hash(new_node->word);
        
        // Insert the node at the beginning of the linked list at the hash index
        new_node->next = table[index];
        table[index] = new_node;
    }
    
    // Close the dictionary file
    fclose(file);
    
    // Dictionary loaded successfully
    return true;
}
```

4.  **`unsigned int size(void)`**
   The `size` function should return the number of words in the dictionary. You'll need to traverse the hash table and count the number of nodes in each linked list.
   
   Here's a modified version of the `size` function:

```c
{
    // Initialize the word count
    unsigned int count = 0;
    
    // Traverse the hash table
    for (int i = 0; i < N; i++)
    {
        // Traverse the linked list at the current index
        node *cursor = table[i];
        while (cursor != NULL)
        {
            // Move to the next node
            cursor = cursor->next;
            
            // Increment the word count
            count++;
        }
    }
    
    // Return the word count
    return count;
}
```

5.  **`bool unload(void)`** 
   The `unload` function should free the memory allocated for the hash table. You'll need to traverse the hash table and free each node in each linked list.
   
   Here's a modified version of the `unload` function:

```c
{
    // Traverse the hash table
    for (int i = 0; i < N; i++)
    {
        // Traverse the linked list at the current index
        node *cursor = table[i];
        while (cursor != NULL)
        {
            // Keep track of the next node
            node *temp = cursor->next;
            
            // Free the current node
            free(cursor);
            
            // Move to the next node
            cursor = temp;
        }
    }
    
    // Dictionary unloaded successfully
    return true;
}
```

With these modifications, you should have a functional dictionary implementation using a hash table. Make sure to include the necessary headers and define the constant `LENGTH` appropriately in your code.

Note: The given code does not handle collisions (i.e., multiple words hashing to the same index). You may want to consider implementing a collision resolution method, such as separate chaining or open addressing, to handle collisions in the hash table.

## Result

```bash
diff -y student.txt staff.txt
WORDS MISSPELLED:     955                WORDS MISSPELLED:     955
WORDS IN DICTIONARY:  143091             WORDS IN DICTIONARY:  143091
WORDS IN TEXT:        17756              WORDS IN TEXT:        17756
TIME IN load:         0.02               | TIME IN load:         0.04
TIME IN check:        0.58               | TIME IN check:        0.02
TIME IN size:         0.00               | TIME IN size:         0.00
TIME IN unload:       0.00               | TIME IN unload:       0.02
TIME IN TOTAL:        0.60               | TIME IN TOTAL:        0.08
```

I know that there's another way to implement `check()` but can't visualize.

## Log Trace 

```bash
$ cd speller/
speller/ $ check50 cs50/problems/2023/x/speller
Connecting......
Authenticating...
Verifying.......
Preparing.....
Uploading.......
Waiting for results.......................
Results for cs50/problems/2023/x/speller generated by check50 v3.3.7'
:) dictionary.c exists
:) speller compiles
:) handles most basic words properly
:) handles min length (1-char) words
:) handles max length (45-char) words
:) handles words with apostrophes properly
:) spell-checking is case-insensitive
:) handles substrings properly
:) program is free of memory errors'
To see the results in your browser go to https://submit.cs50.io/check50/#######################################
```

## Submitted

I didn't knew that `.h` file was going to be submitted, so I've placed all the `#include` at the start of `.c` file.

```bash
speller/ $ submit50 cs50/problems/2023/x/speller
Connecting.......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:'
./dictionary.h
./dictionary.c'
Files that won\'t be submitted:
./texts/wells.txt
./keys/wells.txt
./keys/burnett.txt
./texts/stoker.txt
./keys/xueqin1.txt
./keys/carroll.txt
./keys/xueqin2.txt
./speller
./texts/xueqin2.txt
./texts/constitution.txt
./texts/stein.txt
./texts/holmes.txt
./keys/cat.txt
./keys/her.txt
./keys/stoker.txt
./keys/wordsworth.txt
./dictionaries/large
./texts/whittier.txt
./keys/birdman.txt
./dictionary.o
./texts/aca.txt
./texts/federalist.txt
./texts/her.txt
./texts/xueqin1.txt
./keys/grimm.txt
./texts/wordsworth.txt
./texts/surgery.txt
./texts/rinehart.txt
./speller50
./keys/frankenstein.txt
./keys/whittier.txt
./speller.c
./texts/shakespeare.txt
./texts/pneumonoultramicroscopicsilicovolcanoconiosis.txt
./texts/homer.txt
./texts/tolstoy.txt
./texts/burnett.txt
./texts/carroll.txt
./keys/holmes.txt
./Makefile
./keys/stein.txt
./keys/federalist.txt
./staff.txt
./student.txt
./texts/birdman.txt
./speller.o
./keys/aca.txt
./keys/shakespeare.txt
./texts/revenant.txt
./texts/grimm.txt
./keys/rinehart.txt
./keys/mansfield.txt
./keys/revenant.txt
./dictionaries/small
./keys/surgery.txt
./keys/pneumonoultramicroscopicsilicovolcanoconiosis.txt
./keys/tolstoy.txt
./texts/cat.txt
./texts/lalaland.txt
./keys/austen.txt
./texts/mansfield.txt
./keys/homer.txt
./keys/lalaland.txt
./texts/frankenstein.txt
./texts/austen.txt
./keys/constitution.txt
Keeping in mind the course\'s policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading.......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/speller to see your results.
speller/ $ submit50 cs50/problems/2023/x/speller
```