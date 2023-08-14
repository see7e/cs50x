---
title: Problem Set 3 - Runoff
tags: programação, cs50
use: Exercise
languages: C
dependences: CS50
---

<details> <summary>Table of Contents</summary>

- [Runoff](#runoff)
	- [Background](#background)
	- [Getting Started](#getting-started)
	- [Understanding](#understanding)
	- [Specification](#specification)
		- [`vote`](#vote)
		- [`tabulate`](#tabulate)
		- [`print_winner`](#print_winner)
		- [`find_min`](#find_min)
		- [`is_tie`](#is_tie)
		- [`eliminate`](#eliminate)
	- [Usage](#usage)
	- [Testing](#testing)
	- [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
	- [Log Trace](#log-trace)
	- [Check Style](#check-style)
	- [Submited](#submited)

</details>

---

# Runoff

For this program, you’ll implement a program that runs a runoff election, per the below.

```bash
./runoff Alice Bob Charlie
Number of voters: 5
Rank 1: Alice
Rank 2: Bob
Rank 3: Charlie

Rank 1: Alice
Rank 2: Charlie
Rank 3: Bob

Rank 1: Bob
Rank 2: Charlie
Rank 3: Alice

Rank 1: Bob
Rank 2: Alice
Rank 3: Charlie

Rank 1: Charlie
Rank 2: Alice
Rank 3: Bob

Alice
```

## Background

You already know about plurality elections, which follow a very simple algorithm for determining the winner of an election: every voter gets one vote, and the candidate with the most votes wins.

But the plurality vote does have some disadvantages. What happens, for instance, in an election with three candidates, and the ballots below are cast?

![Five ballots, tie betweeen Alice and Bob](https://cs50.harvard.edu/x/2023/psets/3/runoff/../fptp_ballot_1.png)

A plurality vote would here declare a tie between Alice and Bob, since each has two votes. But is that the right outcome?

There’s another kind of voting system known as a ranked-choice voting system. In a ranked-choice system, voters can vote for more than one candidate. Instead of just voting for their top choice, they can rank the candidates in order of preference. The resulting ballots might therefore look like the below.

![Three ballots, with ranked preferences](https://cs50.harvard.edu/x/2023/psets/3/runoff/../ranked_ballot_1.png)

Here, each voter, in addition to specifying their first preference candidate, has also indicated their second and third choices. And now, what was previously a tied election could now have a winner. The race was originally tied between Alice and Bob, so Charlie was out of the running. But the voter who chose Charlie preferred Alice over Bob, so Alice could here be declared the winner.

Ranked choice voting can also solve yet another potential drawback of plurality voting. Take a look at the following ballots.

![Nine ballots, with ranked preferences](https://cs50.harvard.edu/x/2023/psets/3/runoff/../ranked_ballot_3.png)

Who should win this election? In a plurality vote where each voter chooses their first preference only, Charlie wins this election with four votes compared to only three for Bob and two for Alice. But a majority of the voters (5 out of the 9) would be happier with either Alice or Bob instead of Charlie. By considering ranked preferences, a voting system may be able to choose a winner that better reflects the preferences of the voters.

One such ranked choice voting system is the instant runoff system. In an instant runoff election, voters can rank as many candidates as they wish. If any candidate has a majority (more than 50%) of the first preference votes, that candidate is declared the winner of the election.

If no candidate has more than 50% of the vote, then an “instant runoff” occurrs. The candidate who received the fewest number of votes is eliminated from the election, and anyone who originally chose that candidate as their first preference now has their second preference considered. Why do it this way? Effectively, this simulates what would have happened if the least popular candidate had not been in the election to begin with.

The process repeats: if no candidate has a majority of the votes, the last place candidate is eliminated, and anyone who voted for them will instead vote for their next preference (who hasn’t themselves already been eliminated). Once a candidate has a majority, that candidate is declared the winner.

Let’s consider the nine ballots above and examine how a runoff election would take place.

Alice has two votes, Bob has three votes, and Charlie has four votes. To win an election with nine people, a majority (five votes) is required. Since nobody has a majority, a runoff needs to be held. Alice has the fewest number of votes (with only two), so Alice is eliminated. The voters who originally voted for Alice listed Bob as second preference, so Bob gets the extra two vote. Bob now has five votes, and Charlie still has four votes. Bob now has a majority, and Bob is declared the winner.

What corner cases do we need to consider here?

One possibility is that there’s a tie for who should get eliminated. We can handle that scenario by saying all candidates who are tied for last place will be eliminated. If every remaining candidate has the exact same number of votes, though, eliminating the tied last place candidates means eliminating everyone! So in that case, we’ll have to be careful not to eliminate everyone, and just declare the election a tie between all remaining candidates.

Some instant runoff elections don’t require voters to rank all of their preferences — so there might be five candidates in an election, but a voter might only choose two. For this problem’s purposes, though, we’ll ignore that particular corner case, and assume that all voters will rank all of the candidates in their preferred order.

Sounds a bit more complicated than a plurality vote, doesn’t it? But it arguably has the benefit of being an election system where the winner of the election more accurately represents the preferences of the voters.

## Getting Started

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/3/runoff.zip
```

in order to download a ZIP called `runoff.zip` into your codespace.

Then execute

```bash
unzip runoff.zip
```

to create a folder called `runoff`. You no longer need the ZIP file, so you can execute

```bash
rm runoff.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd runoff
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
runoff/ $
```

If all was successful, you should execute

```bash
ls
```

and see a file named `runoff.c`. Executing `code runoff.c` should open the file where you will type your code for this problem set. If not, retrace your steps and see if you can determine where you went wrong!

```c
#include <cs50.h>
#include <stdio.h>

// Max voters and candidates
#define MAX_VOTERS 100
#define MAX_CANDIDATES 9

// preferences[i][j] is jth preference for voter i
int preferences[MAX_VOTERS][MAX_CANDIDATES];

// Candidates have name, vote count, eliminated status
typedef struct
{
	string name;
	int votes;
	bool eliminated;
}
candidate;

// Array of candidates
candidate candidates[MAX_CANDIDATES];

// Numbers of voters and candidates
int voter_count;
int candidate_count;

// Function prototypes
bool vote(int voter, int rank, string name);
void tabulate(void);
bool print_winner(void);
int find_min(void);
bool is_tie(int min);
void eliminate(int min);

int main(int argc, string argv[])
{
// Check for invalid usage
if (argc < 2)
{
	printf("Usage: runoff [candidate ...]\n");
	return 1;
}

// Populate array of candidates
candidate_count = argc - 1;
if (candidate_count > MAX_CANDIDATES)
{
	printf("Maximum number of candidates is %i\n", MAX_CANDIDATES);
	return 2;
}
for (int i = 0; i < candidate_count; i++)
{
	candidates[i].name = argv[i + 1];
	candidates[i].votes = 0;
	candidates[i].eliminated = false;
}

voter_count = get_int("Number of voters: ");
if (voter_count > MAX_VOTERS)
{
	printf("Maximum number of voters is %i\n", MAX_VOTERS);
	return 3;
}

// Keep querying for votes
for (int i = 0; i < voter_count; i++)
{
	// Query for each rank
	for (int j = 0; j < candidate_count; j++)
	{
		string name = get_string("Rank %i: ", j + 1);
		
		// Record vote, unless it's invalid
		if (!vote(i, j, name))
		{
			printf("Invalid vote.\n");
			return 4;
		}
	}

	printf("\n");
}

// Keep holding runoffs until winner exists
while (true)
{
	// Calculate votes given remaining candidates
	tabulate();
	
	// Check if election has been won
	bool won = print_winner();
	if (won)
	{
		break;
	}
	
	// Eliminate last-place candidates
	int min = find_min();
	bool tie = is_tie(min);
	
	// If tie, everyone wins
	if (tie)
	{
		for (int i = 0; i < candidate_count; i++)
		{
			if (!candidates[i].eliminated)
			{
				printf("%s\n", candidates[i].name);
			}
		}
		break;
	}
	
	// Eliminate anyone with minimum number of votes
	eliminate(min);
	
	// Reset vote counts back to zero
	for (int i = 0; i < candidate_count; i++)
	{
		candidates[i].votes = 0;
	}
}
return 0;
}

// Record preference if vote is valid
bool vote(int voter, int rank, string name)
{
	// TODO
	return false;
}

// Tabulate votes for non-eliminated candidates
void tabulate(void)
{
	// TODO
	return;
}

// Print the winner of the election, if there is one
bool print_winner(void)
{
	// TODO
	return false;
}

// Return the minimum number of votes any remaining candidate has
int find_min(void)
{
	// TODO
	return 0;
}

// Return true if the election is tied between all candidates, false otherwise
bool is_tie(int min)
{
	// TODO
	return false;
}

// Eliminate the candidate (or candidates) in last place
void eliminate(int min)
{
	// TODO
	return;
}
```

## Understanding

<details> <summary>Let's break down the code and simplify the explanation:</summary> 

1.  The code defines the maximum number of voters and candidates allowed in the election using the constants `MAX_VOTERS` and `MAX_CANDIDATES`.

2.  The preferences of voters are stored in a two-dimensional array called `preferences`. Each element `preferences[i][j]` represents the index of the candidate that is the `j`th preference for voter `i`.

3.  The candidates are defined using a struct called `candidate`. Each candidate has a name, vote count, and an eliminated status.

4.  An array `candidates` is used to store all the candidate objects.

5.  Global variables `voter_count` and `candidate_count` keep track of the number of voters and candidates, respectively.

6.  The code defines function prototypes for various functions used in the program.

7.  In the `main` function, the code checks for valid command-line arguments and sets up the candidates' data structure. It also prompts the user for the number of voters and their preferences.

8.  After gathering all the votes, the program enters a loop that continues until a winner is determined. In each iteration, it calculates the votes for the remaining candidates using the `tabulate` function.

9.  The `print_winner` function checks if there is a winner by checking if any candidate has more than 50% of the total votes.

10.  The `find_min` function finds the minimum number of votes among the remaining candidates.

11.  The `is_tie` function checks if there is a tie by comparing the vote count of the remaining candidates with the minimum number of votes.

12.  The `eliminate` function eliminates the candidate(s) with the minimum number of votes.

13.  The loop continues until a winner is found or the election is declared a tie.

14.  Finally, the program returns 0 to indicate successful execution.

To complete the program, you need to implement the functions `vote`, `tabulate`, `print_winner`, `find_min`, `is_tie`, and `eliminate` as per the specifications of the program.

</details>

Let’s take a look at `runoff.c`. We’re defining two constants: `MAX_CANDIDATES` for the maximum number of candidates in the election, and `MAX_VOTERS` for the maximum number of voters in the election.

Next up is a two-dimensional array `preferences`. The array `preferences[i]` will represent all of the preferences for voter number `i`, and the integer `preferences[i][j]` here will store the index of the candidate who is the `j`th preference for voter `i`.

Next up is a `struct` called `candidate`. Every `candidate` has:
- a `string` field for their `name`,
- an `int` representing the number of `votes` they currently have,
- and a `bool` value called `eliminated` that indicates whether the candidate has been eliminated from the election. 
The array `candidates` will keep track of all of the candidates in the election.

The program also has two global variables: `voter_count` and `candidate_count`.

Now onto `main`. Notice that after determining the number of candidates and the number of voters. 

The main voting loop begins, giving every voter a chance to vote. As the voter enters their preferences, the `vote` function is called to keep track of all of the preferences. If at any point, the ballot is deemed to be invalid, the program exits.

Once all of the votes are in, another loop begins: this one’s going to keep looping through the runoff process of checking for a winner and eliminating the last place candidate until there is a winner.

The first call here is to a function called `tabulate`, which should look at all of the voters’ preferences and compute the current vote totals, by looking at each voter’s top choice candidate who hasn’t yet been eliminated. Next, the `print_winner` function should print out the winner if there is one; if there is, the program is over. But otherwise, the program needs to determine the fewest number of votes anyone still in the election received (via a call to `find_min`). If it turns out that everyone in the election is tied with the same number of votes (as determined by the `is_tie` function), the election is declared a tie; otherwise, the last-place candidate (or candidates) is eliminated from the election via a call to the `eliminate` function.

If you look a bit further down in the file, you’ll see that these functions — `vote`, `tabulate`, `print_winner`, `find_min`, `is_tie`, and `eliminate` — are all left to up to you to complete!

## Specification

Complete the implementation of `runoff.c` in such a way that it simulates a runoff election. You should complete the implementations of the `vote`, `tabulate`, `print_winner`, `find_min`, `is_tie`, and `eliminate` functions, and you should not modify anything else in `runoff.c` (and the inclusion of additional header files, if you’d like).

### `vote`

Complete the `vote` function.

-   The function takes arguments `voter`, `rank`, and `name`. If `name` is a match for the name of a valid candidate, then you should update the global preferences array to indicate that the voter `voter` has that candidate as their `rank` preference (where `0` is the first preference, `1` is the second preference, etc.).
-   If the preference is successfully recorded, the function should return `true`; the function should return `false` otherwise (if, for instance, `name` is not the name of one of the candidates).
-   You may assume that no two candidates will have the same name.

Hints

-   Recall that `candidate_count` stores the number of candidates in the election.
-   Recall that you can use [`strcmp`](https://man.cs50.io/3/strcmp) to compare two strings.
-   Recall that `preferences[i][j]` stores the index of the candidate who is the `j`th ranked preference for the `i`th voter.

### `tabulate`

Complete the `tabulate` function.

-   The function should update the number of `votes` each candidate has at this stage in the runoff.
-   Recall that at each stage in the runoff, every voter effectively votes for their top-preferred candidate who has not already been eliminated.

Hints

-   Recall that `voter_count` stores the number of voters in the election and that, for each voter in our election, we want to count one ballot.
-   Recall that for a voter `i`, their top choice candidate is represented by `preferences[i][0]`, their second choice candidate by `preferences[i][1]`, etc.
-   Recall that the `candidate` `struct` has a field called `eliminated`, which will be `true` if the candidate has been eliminated from the election.
-   Recall that the `candidate` `struct` has a field called `votes`, which you’ll likely want to update for each voter’s preferred candidate.
-   Once you’ve cast a vote for a voter’s first non-eliminated candidate, you’ll want to stop there, not continue down their ballot! Recall that you can break out of a loop early using `break` inside of a conditional.

### `print_winner`

Complete the `print_winner` function.

-   If any candidate has more than half of the vote, their name should be printed and the function should return `true`.
-   If nobody has won the election yet, the function should return `false`.

Hints

-   Recall that `voter_count` stores the number of voters in the election. Given that, how would you express the number of votes needed to win the election?

### `find_min`

Complete the `find_min` function.

-   The function should return the minimum vote total for any candidate who is still in the election.

Hints

-   You’ll likely want to loop through the candidates to find the one who is both still in the election and has the fewest number of votes. What information should you keep track of as you loop through the candidates?

### `is_tie`

Complete the `is_tie` function.

-   The function takes an argument `min`, which will be the minimum number of votes that anyone in the election currently has.
-   The function should return `true` if every candidate remaining in the election has the same number of votes, and should return `false` otherwise.

Hints

-   Recall that a tie happens if every candidate still in the election has the same number of votes. Note, too, that the `is_tie` function takes an argument `min`, which is the smallest number of votes any candidate currently has. How might you use that information to determine if the election is a tie (or, conversely, not a tie)?

### `eliminate`

Complete the `eliminate` function.

-   The function takes an argument `min`, which will be the minimum number of votes that anyone in the election currently has.
-   The function should eliminate the candidate (or candidates) who have `min` number of votes.


## Usage

Your program should behave per the example below:

```bash
./runoff Alice Bob Charlie
Number of voters: 5
Rank 1: Alice
Rank 2: Charlie
Rank 3: Bob

Rank 1: Alice
Rank 2: Charlie
Rank 3: Bob

Rank 1: Bob
Rank 2: Charlie
Rank 3: Alice

Rank 1: Bob
Rank 2: Charlie
Rank 3: Alice

Rank 1: Charlie
Rank 2: Alice
Rank 3: Bob

Alice
```

## Testing

Be sure to test your code to make sure it handles…

-   An election with any number of candidate (up to the `MAX` of `9`)
-   Voting for a candidate by name
-   Invalid votes for candidates who are not on the ballot
-   Printing the winner of the election if there is only one
-   Not eliminating anyone in the case of a tie between all remaining candidates

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```bash
check50 cs50/problems/2023/x/runoff
```

Execute the below to evaluate the style of your code using `style50`.

```bash
style50 runoff.c
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/runoff
```

---

# Walkthrough

1. `bool vote(...)` function:
	is responsible for recording the preference of a voter. It takes three parameters:
	- `voter` (the index of the voter),
	- `rank` (the preference rank of the candidate), and
	- `name` (the name of the candidate).
	
	The validation is similar to **Plurality**, we need to check if the given candidate name is valid and matches one of the candidates in the `candidates` array using the `strcmp()` function. If it is valid, we will update the `preferences` array to store the index of the candidate as the preference for the corresponding voter and rank.
	
	```c
	bool vote(int voter, int rank, string name)
	{
	    // Check if the candidate name is valid
	    for (int i = 0; i < candidate_count; i++)
	    {
	        if (strcmp(candidates[i].name, name) == 0)
	        {
	            // Update the preferences array
	            preferences[voter][rank] = i;
	            return true;
	        }
	    }
	    return false; // For an invalid vote
	}
	```
	
	Is called in:
	```c
	// Record vote, unless it's invalid
	if (!vote(i, j, name))
	{
		printf("Invalid vote.\n");
		return 4;
	}
	```

	Where:
	- `i`, iterates over the number of votes,
	- `j`, iterates over the number of candidates
	- `name`, receives the string to compute the vote.

2. `void tabulate()` function:
	is responsible for calculating the vote counts for each non-eliminated candidate.
	
	```c
	void tabulate(void)
	{
	    // Reset vote counts for all candidates
	    for (int i = 0; i < candidate_count; i++)
	    {
	        candidates[i].votes = 0;
	    }
	    // Iterate through each voter's preferences
	    for (int i = 0; i < voter_count; i++)
	    {
	        // Iterate through each preference rank
	        for (int j = 0; j < candidate_count; j++)
	        {
	            // Get the candidate index based on the current preference rank
	            int candidate_index = preferences[i][j];
	            
	            // If the candidate is not eliminated, increment their vote count and break the loop
	            if (!candidates[candidate_index].eliminated)
	            {
	                candidates[candidate_index].votes++;
	                break;
	            }
	        }
	    }
	}
	```
	
	1. Firstly, we reset the vote counts for all candidates to zero (*is necessary to ensure accurate vote counting for the current round of the runoff election*). We iterate through the `candidates` array and set the `votes` field of each candidate to zero.
	
	2. Next, we iterate through each voter's preferences using a nested loop. The outer loop iterates over each voter (using `i` for `voter_count`), and the inner loop iterates over each candidate (using `j` for `candidate_count`) and it's preference rank.
	
	3. Inside the nested loop, we get the candidate index for the current preference rank using `preferences[i][j]` and the loops indexes (`i` and `j`).
	
	4. We check if the candidate at the obtained index is eliminated. If not, we increment their vote count by one and break out of the inner loop since we have found the highest-ranked non-eliminated candidate for that voter.
	
	5. The process continues for all voters and their preference ranks.
	
	After executing the `tabulate` function, the `candidates` array will have updated vote counts for each non-eliminated candidate.

3. `bool print_winner()` function:
	is responsible for determining if there is a clear winner in the election.
	
	```c
    bool print_winner(void)
    {
	    // Calculate the majority threshold
	    int majority_limit = voter_count / 2 + 1;
	    // Iterate through each candidate
	    for (int i = 0; i < candidate_count; i++)
	    {
	        // Check if the candidate has more than half of available votes
	        if (candidates[i].votes >= majority_limit)
	        {
	            printf("%s\n", candidates[i].name);
	            return true;
	        }
	    }
	    return false; // If no winner found
	}
	```
	
	1. We calculate the [majority threshold](https://en.wikipedia.org/wiki/Electoral_threshold) by dividing the total number of voters (`voter_count`) by 2 and adding 1. This threshold represents the minimum number of votes needed to win the election (more than half of the total votes).
	
	2. We iterate through each candidate using a loop.
	
	3. For each candidate, we check if their vote count (`candidates[i].votes`) is greater than the majority threshold. If it is, that means the candidate has received more votes than the threshold required to win.
	
	4. If we find a candidate with more than the majority threshold votes, we print their name using `printf` and return `true` to indicate that a clear winner has been found.
	
	5. If we finish iterating through all the candidates and no candidate has more than the majority threshold votes, we return `false` to indicate that there is no clear winner yet.
    
	The `print_winner` function checks if any candidate has received more votes than the half of the available number of votes, indicating that they have won the election directly. 
	
	If a winner is found, their name is printed, and `true` is returned. Otherwise, it returns `false` to indicate that there is no clear winner yet. This boolean is used to break or not the main loop.

4. `find_min()` function:
	is responsible for finding the minimum number of votes received by any non-eliminated candidate.
	
	```c
	int find_min(void)
	{
    // Set an initial minimum vote count to a large value
    int min_votes = MAX_VOTERS + 1;
	
    // Iterate through each candidate
    for (int i = 0; i < candidate_count; i++)
    {
        // Check if the candidate is not eliminated and their vote count is less than the current minimum
        if (!candidates[i].eliminated && candidates[i].votes < min_votes)
        {
            min_votes = candidates[i].votes;
        }
    }
    return min_votes;
	}
	```
	
	1. We set an initial minimum vote count (`min_votes`) to a value larger than the maximum possible number of voters. **This ensures that any valid vote count will be smaller than the initial minimum value**.
		- Other path is to initialize `min_votes` with a negative integer (e.g. ` = -1`), this will change the `if` conditional: 
		```c
		if (!candidates[i].eliminated && (min_votes == -1 || candidates[i].votes > min_votes)) {...}
		```
    
	2. We iterate through each candidate using a loop.
	
	3. For each candidate, we check if they are not eliminated (`!candidates[i].eliminated`) and if their vote count (`candidates[i].votes`) is less than the current minimum (`min_votes`).
	
	4. If both conditions are true, we update the `min_votes` variable with the current candidate's vote count.
	
	5. After iterating through all the candidates, the `min_votes` variable will contain the minimum vote count among the non-eliminated candidates.
	
	6. We return the `min_votes` value, representing the minimum number of votes received by any non-eliminated candidate.

5. `is_tie()` function:
	determines whether the election is tied between all non-eliminated candidates. 
	
	```c
	bool is_tie(int min)
	{
    // Iterate through each candidate
    for (int i = 0; i < candidate_count; i++)
    {
        // Check if the candidate is not eliminated and their vote count is different from the minimum
        if (!candidates[i].eliminated && candidates[i].votes != min)
        {
            return false;
        }
    }
    // If all non-eliminated candidates have the same vote count as the minimum, it is a tie
    return true;
	}
	```
	
	1. The function takes the `min` parameter, which represents the minimum number of votes received by any non-eliminated candidate.
    
	2. We iterate through each candidate using a loop.
	
	3. For each candidate, we check if they are not eliminated (`!candidates[i].eliminated`) and if their vote count (`candidates[i].votes`) is different from the minimum (`min`).
	
	4. If we find any non-eliminated candidate with a vote count different from the minimum, we immediately return `false`, indicating that the election is not tied.
	
	5. If the loop completes without finding any non-eliminated candidate with a different vote count than the minimum, it means that all non-eliminated candidates have the same vote count as the minimum. In this case, we return `true`, indicating a tie.

6. `eliminate()` function:
	will eliminate the candidate(s) with the minimum votes (parameter) so that they are no longer considered in the subsequent rounds of the election.
	```c
	void eliminate(int min)
	{
	    // Iterate through each candidate
	    for (int i = 0; i < candidate_count; i++)
	    {
	        // Check if the candidate is not eliminated and their vote count is equal to the minimum
	        if (!candidates[i].eliminated && candidates[i].votes == min)
	        {
	            candidates[i].eliminated = true;
	        }
	    }
	}
	```
	
	1. The function takes the `min` parameter, which represents the minimum number of votes received by any non-eliminated candidate.
    
	2. We iterate through each candidate using a loop.
    
	3. For each candidate, we check if they are not already eliminated (`!candidates[i].eliminated`) and if their vote count is equal to the minimum (`candidates[i].votes == min`).
    
	4. If a candidate meets both conditions, it means they have the minimum number of votes and should be eliminated from the election. We update their `eliminated` status to `true` by setting `candidates[i].eliminated = true`.
    
	5. After iterating through all the candidates, the `eliminate` function will have marked all the candidates who received the minimum number of votes as eliminated.

## Log Trace 

```bash
runoff/ $ check50 cs50/problems/2023/x/runoff
Connecting......
Authenticating...
Verifying........
Preparing.....
Uploading.......
Waiting for results.........................
Results for cs50/problems/2023/x/runoff generated by check50 v3.3.7
':) runoff.c exists
:) runoff compiles
:) vote returns true when given name of candidate
:) vote returns false when given name of invalid candidate
:) vote correctly sets first preference for first voter
:) vote correctly sets third preference for second voter
:) vote correctly sets all preferences for voter
:) tabulate counts votes when all candidates remain in election
:) tabulate counts votes when one candidate is eliminated
:) tabulate counts votes when multiple candidates are eliminated
:) tabulate handles multiple rounds of preferences
':( print_winner prints name when someone has a majority
    print_winner did not print winner of election
:( print_winner returns true when someone has a majority
    print_winner did not print winner and then return true
':) print_winner returns false when nobody has a majority
:) print_winner returns false when leader has exactly 50% of vote
:) find_min returns minimum number of votes for candidate
:) find_min returns minimum when all candidates are tied
:) find_min ignores eliminated candidates
:) is_tie returns true when election is tied
:) is_tie returns false when election is not tied
:) is_tie returns false when only some of the candidates are tied
:) is_tie detects tie after some candidates have been eliminated
:) eliminate eliminates candidate in last place
:) eliminate eliminates multiple candidates in tie for last
:) eliminate eliminates candidates after some already eliminated
'To see the results in your browser go to https://submit.cs50.io/check50/######################################
```
> :( print_winner prints name when someone has a majority
>**Cause**  
>print_winner did not print winner of election  
>
>:( print_winner returns true when someone has a majority
>**Cause**  
>print_winner did not print winner and then return true

As noted we had a problem in the `print_winner()` function. The problem was just the ` > ` that didn't count the limited included, the correct conditional is `if (candidates[i].votes >= majority_limit)`

```bash
runoff/ $ check50 cs50/problems/2023/x/runoff
Connecting.......
Authenticating...
Verifying......
Preparing.....
Uploading......
Waiting for results.............................
Results for cs50/problems/2023/x/runoff generated by check50 v3.3.7
':) runoff.c exists
:) runoff compiles
:) vote returns true when given name of candidate
:) vote returns false when given name of invalid candidate
:) vote correctly sets first preference for first voter
:) vote correctly sets third preference for second voter
:) vote correctly sets all preferences for voter
:) tabulate counts votes when all candidates remain in election
:) tabulate counts votes when one candidate is eliminated
:) tabulate counts votes when multiple candidates are eliminated
:) tabulate handles multiple rounds of preferences
:) print_winner prints name when someone has a majority
:) print_winner returns true when someone has a majority
:) print_winner returns false when nobody has a majority
:) print_winner returns false when leader has exactly 50% of vote
:) find_min returns minimum number of votes for candidate
:) find_min returns minimum when all candidates are tied
:) find_min ignores eliminated candidates
:) is_tie returns true when election is tied
:) is_tie returns false when election is not tied
:) is_tie returns false when only some of the candidates are tied
:) is_tie detects tie after some candidates have been eliminated
:) eliminate eliminates candidate in last place
:) eliminate eliminates multiple candidates in tie for last
:) eliminate eliminates candidates after some already eliminated
'To see the results in your browser go to https://submit.cs50.io/check50/######################################
runoff/ $ 
```

## Check Style 

```bash
runoff/ $ style50 runoff.c
Results generated by style50 v2.7.5
Looks good!
```

## Submited

```bash
runoff/ $ submit50 cs50/problems/2023/x/runoff
Connecting......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
./runoff.c
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/runoff to see your results.
runoff/ $ 
```