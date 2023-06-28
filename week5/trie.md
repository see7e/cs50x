---
title: Practice Problems 5 - Trie
tags: programação, cs50
use: Exercise
languages: C
dependences: CS50
---

# Trie [#](https://cs50.harvard.edu/x/2023/problems/5/trie//#trie)

## Learning Goals

-   Learn more about data structures
-   Work with a trie

![puppies](https://cs50.harvard.edu/x/2023/problems/5/trie/puppies.jpeg)

## Background

Imagine you just rescued a dog and you’re deciding on a name. You found a file online with a list of about 150 of the most popular dog names! You are curious as to whether or not the names you are considering are on this list. Since trie’s are great for data lookups, we’ve given you some (almost!) complete code in `trie.c`. There is one function, `check`, which is not yet implemented. Your job is to complete this function.

## Demo

<iframe src="https://asciinema.org/a/JukHED1VvaJLFHMJbIvLksgF1/iframe?autoplay=1&amp;loop=1&amp;cols=100&amp;rows=12" id="asciicast-iframe-JukHED1VvaJLFHMJbIvLksgF1" name="asciicast-iframe-JukHED1VvaJLFHMJbIvLksgF1" scrolling="no" allowfullscreen="true" style="overflow: hidden; margin: 0px; border: 0px; display: inline-block; width: 100%; float: none; visibility: visible; height: 285px;"></iframe>

## Getting Started

1.  Log into [code.cs50.io](https://code.cs50.io/) using your GitHub account.
2.  Click inside the terminal window and execute `cd`.
3.  Execute `wget https://cdn.cs50.net/2022/fall/labs/5/trie.zip` followed by Enter in order to download a zip called `trie.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!
4.  Now execute `unzip trie.zip` to create a folder called `trie`.
5.  You no longer need the ZIP file, so you can execute `rm trie.zip` and respond with “y” followed by Enter at the prompt.

## Implementation Details

Notice that the trie itself is implemented through the creative use of several `struct`s called `node`. Each `node` in a trie has an array of (potential) children, with size 26—one potential child for each letter of the alphabet! Adding words to this trie, notice that—for every letter in a word—we create a new `node` child whose parent is either the `root` node (for the first letter) or the previous letter (if not the first letter). On the very last letter, we set the `is_word` attribute of the child `node` to `true`. Now, checking if a word is in our trie is as easy as following each letter of that word through our trie. If we get to the final letter and see that `is_word` is true, well, that name is in our trie!

-   Hints
    
    -   You probably want to start by setting a `node` pointer, `cursor` to the `root` of the trie.
    -   Iterate through every letter in the argument `word` and, as you do, determine the array index that corresponds to that letter.
    -   You can use the index for a letter to check if `children[index]` is a `NULL` pointer, meaning the word does not exist in the trie.
    -   If `children[index]` is in fact a node, you can reset `cursor` to this node and check for the next letter in its `children` nodes.
    -   Remember that the lookup should be case-insensitive. For instance, `A` and `a` should correspond to 0, `B` and `b` corresponds to 1, etc.
    

## Thought Question

-   When might you want to use a trie as a data structure? When might you _not_?

## How to Test Your Code

Your program should behave per the examples below.

```bash
trie/ $ ./trie dog_names.txt
Check word: Molly
Found!
```

```bash
trie/ $ ./trie dog_names.txt
Check word: Lucy
Found!
```

```bash
trie/ $ ./trie dog_names.txt
Check word: Prudence
Not Found.
```

No `check50` for this one!

To evaluate that the style of your code, type in the following at the `$` prompt.

```bash
style50 trie.c
```

## How to Submit

No need to submit! This is a practice problem.