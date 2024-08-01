---
title: Lab 5 - Inheritance
tags: programming, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Inheritance #](#inheritance-)
  - [Background](#background)
  - [Getting Started](#getting-started)
  - [Understanding](#understanding)
  - [Implementation Details](#implementation-details)
    - [Hints](#hints)
    - [How to Test Your Code](#how-to-test-your-code)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Submited](#submited)

</details>

# Inheritance [#](https://cs50.harvard.edu/x/2023/labs/5//#lab-5-inheritance)

You are welcome to collaborate with one or two classmates on this lab, though it is expected that every student in any such group contribute equally to the lab.

Simulate the inheritance of blood types for each member of a family.

```bash
$ ./inheritance
Child (Generation 0): blood type OO
    Parent (Generation 1): blood type AO
        Grandparent (Generation 2): blood type OA
        Grandparent (Generation 2): blood type BO
    Parent (Generation 1): blood type OB
        Grandparent (Generation 2): blood type AO
        Grandparent (Generation 2): blood type BO

```

## Background

A person’s blood type is determined by two alleles (i.e., different forms of a gene). The three possible alleles are A, B, and O, of which each person has two (possibly the same, possibly different). Each of a child’s parents randomly passes one of their two blood type alleles to their child. The possible blood type combinations, then, are: OO, OA, OB, AO, AA, AB, BO, BA, and BB.

For example, if one parent has blood type AO and the other parent has blood type BB, then the child’s possible blood types would be AB and OB, depending on which allele is received from each parent. Similarly, if one parent has blood type AO and the other OB, then the child’s possible blood types would be AO, OB, AB, and OO.

## Getting Started

Open [VS Code](https://code.cs50.io/).

Start by clicking inside your terminal window, then execute `cd` by itself. You should find that its “prompt” resembles the below.

```bash
$
```

Click inside of that terminal window and then execute

```bash
wget https://cdn.cs50.net/2022/fall/labs/5/inheritance.zip
```

followed by Enter in order to download a ZIP called `inheritance.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!

Now execute

```bash
unzip inheritance.zip
```

to create a folder called `inheritance`. You no longer need the ZIP file, so you can execute

```bash
rm inheritance.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd inheritance
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
inheritance/ $
```

If all was successful, you should execute

```bash
ls
```

and you should see `inheritance.c`.

If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Understanding

Take a look at the distribution code in `inheritance.c`.

Notice the definition of a type called `person`. Each person has an array of two `parents`, each of which is a pointer to another `person` struct. Each person also has an array of two `alleles`, each of which is a `char` (either `'A'`, `'B'`, or `'O'`).

Now, take a look at the `main` function. The function begins by “seeding” (i.e., providing some initial input to) a random number generator, which we’ll use later to generate random alleles. The `main` function then calls the `create_family` function to simulate the creation of `person` structs for a family of 3 generations (i.e. a person, their parents, and their grandparents). We then call `print_family` to print out each of those family members and their blood types. Finally, the function calls `free_family` to `free` any memory that was previously allocated with `malloc`.

The `create_family` and `free_family` functions are left to you to write!

## Implementation Details

Complete the implementation of `inheritance.c`, such that it creates a family of a specified generation size and assigns blood type alleles to each family member. The oldest generation will have alleles assigned randomly to them.

The `create_family` function takes an integer (`generations`) as input and should allocate (as via `malloc`) one `person` for each member of the family of that number of generations, returning a pointer to the `person` in the youngest generation.
-   For example, `create_family(3)` should return a pointer to a person with two parents, where each parent also has two parents.
-   Each `person` should have `alleles` assigned to them. The oldest generation should have alleles randomly chosen (as by calling the `random_allele` function), and younger generations should inherit one allele (chosen at random) from each parent.
-   Each `person` should have `parents` assigned to them. The oldest generation should have both `parents` set to `NULL`, and younger generations should have `parents` be an array of two pointers, each pointing to a different parent.

We’ve divided the `create_family` function into a few `TODO`s for you to complete.

1. You should allocate memory for a new person. Recall that you can use `malloc` to allocate memory, and `sizeof(person)` to get the number of bytes to allocate.
2. We’ve included a condition to check if `generations > 1`.
    -   If `generations > 1`, then there are more generations that still need to be allocated. We’ve already created two new `parents`, `parent0` and `parent1`, by recursively calling `create_family`. Your `create_family` function should then set the parent pointers of the new person you created. Finally, assign both `alleles` for the new person by randomly choosing one allele from each parent.
    -   Otherwise (if `generations == 1`), then there will be no parent data for this person. Both `parents` of your new person should be set to `NULL`, and each `allele` should be generated randomly.
3. Finally, your function should return a pointer for the `person` that was allocated.

The `free_family` function should accept as input a pointer to a `person`, free memory for that person, and then recursively free memory for all of their ancestors.

> Since this is a recursive function, you should first handle the base case. If the input to the function is `NULL`, then there’s nothing to free, so your function can return immediately.
> Otherwise, you should recursively `free` both of the person’s parents before `free`ing the child.


### Hints

-   You might find the `rand()` function useful for randomly assigning alleles. This function returns an integer between `0` and `RAND_MAX`, or `2147483647`.
    -   In particular, to generate a pseudorandom number that is either `0` or `1`, you can use the expression `rand() % 2`.
-   Remember, to allocate memory for a particular person, we can use `malloc(n)`, which takes a size as argument and will allocate `n` bytes of memory.
-   Remember, to access a variable via a pointer, we can use arrow notation.
    -   For example, if `p` is a pointer to a person, then a pointer to this person’s first parent can be accessed by `p->parents[0]`.


### How to Test Your Code

Upon running `./inheritance`, your program should adhere to the rules described in the background. The child should have two alleles, one from each parent. The parents should each have two alleles, one from each of their parents.

For example, in the example below, the child in Generation 0 received an O allele from both Generation 1 parents. The first parent received an A from the first grandparent and a O from the second grandparent. Similarly, the second parent received an O and a B from their grandparents.

```bash
$ ./inheritance
Child (Generation 0): blood type OO
    Parent (Generation 1): blood type AO
        Grandparent (Generation 2): blood type OA
        Grandparent (Generation 2): blood type BO
    Parent (Generation 1): blood type OB
        Grandparent (Generation 2): blood type AO
        Grandparent (Generation 2): blood type BO

```

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/labs/2023/x/inheritance
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 inheritance.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/labs/2023/x/inheritance
```

---

# Walkthrough

Using the steps in the [Implementation Details](#implementation-details):
- In case of more than one generation and enters in the `if` condition:
	```c
	{
		p->parents[0] = create_family(generations - 1);
		p->parents[1] = create_family(generations - 1);
		
		p->alleles[0] = p->parents[0]->alleles[rand() % 2];
		p->alleles[1] = p->parents[1]->alleles[rand() % 2];
	}
	```
	
	 I don't know why the already built code, starts with:
	 
	```c
	{
	// Create two new parents for current person by recursively calling create_family
	person *parent0 = create_family(generations - 1);
	person *parent1 = create_family(generations - 1);
	
	// TODO: Set parent pointers for current person
	
	// TODO: Randomly assign current person's alleles based on the alleles of their parents
	}
	```

 - In case of the last generation (**base case**) or if it's only one
   
	```c
	{
		p->parents[0] = NULL;
		p->parents[1] = NULL;
		
		p->alleles[0] = random_allele();
		p->alleles[1] = random_allele();
	}
	```

- And don't forget to `return` the node for the `person *create_family(int generations)` function
  ```c
  return p;
  ```

## Log Trace 

```bash
inheritance/ $ check50 cs50/labs/2023/x/inheritance
Connecting......
Authenticating...
Verifying........
Preparing.....
Uploading.......
Waiting for results...................
Results for cs50/labs/2023/x/inheritance generated by check50 v3.3.7'
:) inheritance.c exists
:) inheritance compiles
:) create_family creates correct size of family
:) create_family follows inheritance rules 1
:) create_family follows inheritance rules 2
:) create_family follows inheritance rules 3
:) free_family results in no memory leakages'
To see the results in your browser go to https://submit.cs50.io/check50/########################################
```

## Style

```bash
inheritance/ $ style50 inheritance.c
Results generated by style50 v2.7.5'
Looks good!'
```

## Submitted

```bash
inheritance/ $ submit50 cs50/labs/2023/x/inheritance
Connecting.....
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
./inheritance.c
Files that won\'t be submitted:
./inheritance
Keeping in mind the course\'s policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading..........
Go to https://submit.cs50.io/users/see7e/cs50/labs/2023/x/inheritance to see your results.
```

Just for better programming, looking for any possible improvement, there are a few areas where you can make improvements:

1.  Error handling: When allocating memory using `malloc`, like the other previous programs, it's a good practice to check if the allocation was successful. You can add error handling to ensure that memory allocation succeeds. If `malloc` returns `NULL`, it means the allocation failed. You can update the `create_family` function to handle this case:

```c
person *create_family(int generations)
{
    person *p = malloc(sizeof(person));
    if (p == NULL) {
        fprintf(stderr, "Memory allocation failed.\n");
        exit(1);
    }
	
    // Rest of the code ...
}
```

2.  Function prototypes (*this one is just to remember*): It's a good practice to declare function prototypes before they are used. This helps improve code readability and eliminates the need for rearranging function definitions. You can add function prototypes at the beginning of the code.

```c
// Function prototypes
person *create_family(int generations);
void print_family(person *p, int generation);
void free_family(person *p);
char random_allele();

// Rest of the code ...
```

3.  Avoiding magic numbers: We all know that the `GENERATIONS` value is fixed for this exercise, but you can pass it as a parameter to the `create_family` function or even as an `argv`. This allows for greater flexibility and easier modification in the future.