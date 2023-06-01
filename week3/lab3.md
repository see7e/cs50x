---
title: Lab 3 - Sort
tags: studies, programação, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Lab 3: Sort #](#lab-3-sort-)
  - [Background](#background)
  - [Getting Started](#getting-started)
  - [Instructions](#instructions)
    - [Hints](#hints)
    - [How to Check Your Answers](#how-to-check-your-answers)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Submited](#submited)

</details>

---

# Lab 3: Sort [#](https://cs50.harvard.edu/x/2023/labs/3/#lab-3-sort#lab-3-sort)

You are welcome to collaborate with one or two classmates on this lab, though it is expected that every student in any such group contribute equally to the lab.

Analyze three sorting programs to determine which algorithms they use.

## Background

Recall from lecture that we saw a few algorithms for sorting a sequence of numbers: selection sort, bubble sort, and merge sort.

-   Selection sort iterates through the unsorted portions of a list, selecting the smallest element each time and moving it to its correct location.
-   Bubble sort compares pairs of adjacent values one at a time and swaps them if they are in the incorrect order. This continues until the list is sorted.
-   Merge sort recursively divides the list into two repeatedly and then merges the smaller lists back into a larger one in the correct order.

## Getting Started

Open [VS Code](https://code.cs50.io/).

Start by clicking inside your terminal window, then execute `cd` by itself. You should find that its “prompt” resembles the below.

```bash
$
```

Click inside of that terminal window and then execute

```bash
wget https://cdn.cs50.net/2022/fall/labs/3/sort.zip
```

followed by Enter in order to download a ZIP called `sort.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!

Now execute

```bash
unzip sort.zip
```

to create a folder called `sort`. You no longer need the ZIP file, so you can execute

```bash
rm sort.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd sort
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
sort/ $
```

If all was successful, you should execute

```bash
ls
```

and you should see a collection of `.txt` files alongside executable programs `sort1`, `sort2`, and `sort3`.

If you run into any trouble, follow these same steps steps again and see if you can determine where you went wrong!

## Instructions

Provided to you are three already-compiled C programs, `sort1`, `sort2`, and `sort3`. Each of these programs implements a different sorting algorithm: selection sort, bubble sort, or merge sort (though not necessarily in that order!). Your task is to determine which sorting algorithm is used by each file.

-   `sort1`, `sort2`, and `sort3` are binary files, so you won’t be able to view the C source code for each. To assess which sort implements which algorithm, run the sorts on different lists of values.
-   Multiple `.txt` files are provided to you. These files contain `n` lines of values, either reversed, shuffled, or sorted.
    >   For example, `reversed10000.txt` contains 10000 lines of numbers that are reversed from `10000`, while `random10000.txt` contains 10000 lines of numbers that are in random order.
-   To run the sorts on the text files, in the terminal, run `./[program_name] [text_file.txt]`. Make sure you have made use of `cd` to move into the `sort` directory!
    >   For example, to sort `reversed10000.txt` with `sort1`, run `./sort1 reversed10000.txt`.
-   You may find it helpful to time your sorts. To do so, run `time ./[sort_file] [text_file.txt]`.
    >   For example, you could run `time ./sort1 reversed10000.txt` to run `sort1` on 10,000 reversed numbers. At the end of your terminal’s output, you can look at the `real` time to see how much time actually elapsed while running the program.
-   Record your answers in `answers.txt`, along with an explanation for each program, by filling in the blanks marked `TODO`.
    > sort1 uses: `TODO`
    >
    > How do you know?: `TODO`
    >
    > sort2 uses: TODO
    >
    > How do you know?: `TODO`
    >
    > sort3 uses: `TODO`
    >
    > How do you know?: `TODO`


### Hints

-   The different types of `.txt` files may help you determine which sort is which. Consider how each algorithm performs with an already sorted list. How about a reversed list? Or shuffled list? It may help to work through a smaller list of each type and walk through each sorting process.

### How to Check Your Answers

Execute the below to evaluate the correctness of your answers using `check50`. But be sure to fill in your explanations as well, which `check50` won’t check here!

```bash
check50 cs50/labs/2023/x/sort
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/labs/2023/x/sort
```

---

# Walkthrough

## Result

```txt
sort1 uses: Bubble Sort

How do you know?: Has the the best processing time compared to Selection Sort in a sorted list.
time ./sort1 sorted50000.txt
real    0m0,358s
user    0m0,037s
sys     0m0,167s


sort2 uses: Merge Sort

How do you know?: Has the fastest output time.
time ./sort2 random50000.txt
real    0m0,323s
user    0m0,054s
sys     0m0,155s

sort3 uses: Selection Sort

How do you know?: Have the worst processing time in a sorted list.
time ./sort3 sorted50000.txt
real    0m3,290s
user    0m2,601s
sys     0m0,170s
```

## Log Trace 

```bash
sort/ $ check50 cs50/labs/2023/x/sort
Connecting.......
Authenticating...
Verifying.......
Preparing.............
Uploading..........
Waiting for results................................
Results for cs50/labs/2023/x/sort generated by check50 v3.3.7
:) answers.txt exists
:) answers all questions
:) correctly identifies each sort
To see the results in your browser go to https://submit.cs50.io/check50/###############################
```

## Submited

```bash
sort/ $ submit50 cs50/labs/2023/x/sort
Connecting.......
Authenticating...
Verifying.......
Preparing.............
Files that will be submitted:
./answers.txt
Files that won't be submitted:
./sorted50000.txt
./sort1
./reversed10000.txt
./sorted10000.txt
./sorted5000.txt
./reversed50000.txt
./random5000.txt
./random50000.txt
./reversed5000.txt
./sort3
./sort2
./random10000.txt
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading..........
Go to https://submit.cs50.io/users/see7e/cs50/labs/2023/x/sort to see your results.
```