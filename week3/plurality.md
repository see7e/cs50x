---
title: Problem Set 3 - Plurality
tags: programming, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Plurality](#plurality)
  - [Background](#background)
  - [Getting Started](#getting-started)
  - [Understanding](#understanding)
  - [Specification](#specification)
  - [Usage](#usage)
  - [Testing](#testing)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Check Style](#check-style)
  - [Submited](#submited)

</details>

---

# Plurality
> *Full code in [here](./src/plurality.c)*

For this program, you’ll implement a program that runs a plurality election, per the below.

```bash
$ ./plurality Alice Bob Charlie
Number of voters: 4
Vote: Alice
Vote: Bob
Vote: Charlie
Vote: Alice
Alice
```

## Background

Elections come in all shapes and sizes. In the UK, the [Prime Minister](https://www.parliament.uk/education/about-your-parliament/general-elections/) is officially appointed by the monarch, who generally chooses the leader of the political party that wins the most seats in the House of Commons. The United States uses a multi-step [Electoral College](https://www.archives.gov/federal-register/electoral-college/about.html) process where citizens vote on how each state should allocate Electors who then elect the President.

Perhaps the simplest way to hold an election, though, is via a method commonly known as the “plurality vote” (also known as “first-past-the-post” or “winner take all”). In the plurality vote, every voter gets to vote for one candidate. At the end of the election, whichever candidate has the greatest number of votes is declared the winner of the election.

## Getting Started

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/3/plurality.zip
```

in order to download a ZIP called `plurality.zip` into your codespace.

Then execute

```bash
unzip plurality.zip
```

to create a folder called `plurality`. You no longer need the ZIP file, so you can execute

```bash
rm plurality.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd plurality
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
plurality/ $
```

If all was successful, you should execute

```bash
ls
```

and see a file named `plurality.c`. Executing `code plurality.c` should open the file where you will type your code for this problem set. If not, retrace your steps and see if you can determine where you went wrong!

## Understanding

Let’s take a look at `plurality.c` and read through the distribution code that’s been provided to you.

The line `#define MAX 9` is some syntax used here to mean that `MAX` is a constant (equal to `9`) that can be used throughout the program. Here, it represents the maximum number of candidates an election can have.

The file then defines a `struct` called a `candidate`. Each `candidate` has two fields: a `string` called `name` representing the candidate’s name, and an `int` called `votes` representing the number of votes the candidate has. Next, the file defines a global array of `candidates`, where each element is itself a `candidate`.

Now, take a look at the `main` function itself. See if you can find where the program sets a global variable `candidate_count` representing the number of candidates in the election, copies command-line arguments into the array `candidates`, and asks the user to type in the number of voters. Then, the program lets every voter type in a vote (see how?), calling the `vote` function on each candidate voted for. Finally, `main` makes a call to the `print_winner` function to print out the winner (or winners) of the election.

If you look further down in the file, though, you’ll notice that the `vote` and `print_winner` functions have been left blank. This part is up to you to complete!

## Specification

Complete the implementation of `plurality.c` in such a way that the program simulates a plurality vote election.

-   Complete the `vote` function.
    -   `vote` takes a single argument, a `string` called `name`, representing the name of the candidate who was voted for.
    -   If `name` matches one of the names of the candidates in the election, then update that candidate’s vote total to account for the new vote. The `vote` function in this case should return `true` to indicate a successful ballot.
    -   If `name` does not match the name of any of the candidates in the election, no vote totals should change, and the `vote` function should return `false` to indicate an invalid ballot.
    -   You may assume that no two candidates will have the same name.
-   Complete the `print_winner` function.
    -   The function should print out the name of the candidate who received the most votes in the election, and then print a newline.
    -   It is possible that the election could end in a tie if multiple candidates each have the maximum number of votes. In that case, you should output the names of each of the winning candidates, each on a separate line.

You should not modify anything else in `plurality.c` other than the implementations of the `vote` and `print_winner` functions (and the inclusion of additional header files, if you’d like).

## Usage
Your program should behave per the examples below.

```bash
$ ./plurality Alice Bob
Number of voters: 3
Vote: Alice
Vote: Bob
Vote: Alice
Alice
```

```bash
$ ./plurality Alice Bob
Number of voters: 3
Vote: Alice
Vote: Charlie
Invalid vote.
Vote: Alice
Alice
```

```bash
$ ./plurality Alice Bob Charlie
Number of voters: 5
Vote: Alice
Vote: Charlie
Vote: Bob
Vote: Bob
Vote: Alice
Alice
Bob
```

## Testing

Be sure to test your code to make sure it handles…

-   An election with any number of candidate (up to the `MAX` of `9`)
-   Voting for a candidate by name
-   Invalid votes for candidates who are not on the ballot
-   Printing the winner of the election if there is only one
-   Printing the winner of the election if there are multiple winners

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/plurality
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 plurality.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/plurality
```

---

# Walkthrough 

As soon we unzip the file, the already built code is:

```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>
 
// Max number of candidates
#define MAX 9
  
// Candidates have name and vote count
typedef struct
{
    string name;
    int votes;
}
candidate;
  
// Array of candidates
candidate candidates[MAX];
  
// Number of candidates
int candidate_count;
  
// Function prototypes
bool vote(string name);
void print_winner(void);
  
int main(int argc, string argv[])
{
    // Check for invalid usage
    if (argc < 2)
    {
        printf("Usage: plurality [candidate ...]\n");
        return 1;
    }
  
    // Populate array of candidates
    candidate_count = argc - 1;
    if (candidate_count > MAX)
    {
        printf("Maximum number of candidates is %i\n", MAX);
        return 2;
    }
    for (int i = 0; i < candidate_count; i++)
    {
        candidates[i].name = argv[i + 1];
        candidates[i].votes = 0;
    }
  
    int voter_count = get_int("Number of voters: ");
  
    // Loop over all voters
    for (int i = 0; i < voter_count; i++)
    {
        string name = get_string("Vote: ");
  
        // Check for invalid vote
        if (!vote(name))
        {
            printf("Invalid vote.\n");
        }
    }
  
    // Display winner of election
    print_winner();
}
  
// Update vote totals given a new vote
bool vote(string name)
{
    // TODO
    return false;
}
  
// Print the winner (or winners) of the election
void print_winner(void)
{
    // TODO
    return;
}
```

For the `vote()`  as it's has `bool` return, for the triage at `// Check for invalid vote` we need to set a validation that will iterate over the candidates, check the information and compute the vote for the available candidate. As follows:

```c
for (int i = 0; i < candidate_count; i++) // number of candidates
{
	if (strcmp(candidates[i].name, name) == 0)   // validate candidates vs vote
	{
		candidates[i].votes += 1;
		return true;
	}
}
return false; // no need for else statement
```

To return the winner firstly the code was tilting to sort the list by `.vote` numbers but saw in [here](https://gist.github.com/deeunix/d9523f86b7499ba880055f836b48ba6d) an even better way, tried to optimize it but even Chat (😂) agrees that it's already efficient. *Just changed the variable name (makes more sense to me in this way).*
> The provided code is already efficient for its purpose.

```c
int winner = 0; // initialize winner's number of votes

for (int i = 0; i < candidate_count; i++) //iterate over list of candidates
{
	if (candidates[i].votes > winner)
	{
		winner = candidates[i].votes;
	}
}

// look for winners number of votes
for (int i = 0; i < candidate_count; i++)
{
	if (candidates[i].votes == winner)
	{
		printf("%s\n", candidates[i].name);
	}
}
return;
```

## Result

```bash
plurality/ $ make plurality 
plurality/ $ ./plurality 
Usage: plurality [candidate ...]
plurality/ $ ./plurality João
Number of voters: 2
Vote: Maria
Invalid vote.
Vote: João
João
plurality/ $ ./plurality João Maria
Number of voters: 3
Vote: João
Vote: Maria
Vote: Maria
Maria
```

## Log Trace 

```bash
plurality/ $ check50 cs50/problems/2023/x/plurality
Connecting......
Authenticating...
Verifying......
Preparing.....
Uploading......
Waiting for results............................
Results for cs50/problems/2023/x/plurality generated by check50 v3.3.7
:) plurality.c exists
:) plurality compiles
:) vote returns true when given name of first candidate
:) vote returns true when given name of middle candidate
:) vote returns true when given name of last candidate
:) vote returns false when given name of invalid candidate
:) vote produces correct counts when all votes are zero
:) vote produces correct counts after some have already voted
:) vote leaves vote counts unchanged when voting for invalid candidate
:) print_winner identifies Alice as winner of election
:) print_winner identifies Bob as winner of election
:) print_winner identifies Charlie as winner of election
:) print_winner prints multiple winners in case of tie
:) print_winner prints all names when all candidates are tied
To see the results in your browser go to https://submit.cs50.io/check50/########################################
```

## Check Style 

```bash
plurality/ $ style50 plurality.c
Results generated by style50 v2.7.5
Looks good!
```

## Submited

```bash
plurality/ $ submit50 cs50/problems/2023/x/plurality
Connecting......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
./plurality.c
Files that won't be submitted:
./plurality
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/plurality to see your results.
```