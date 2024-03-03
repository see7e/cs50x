---
title: CS50 - Week 5
tags: programação, cs50
use: Documentation
languages: C
dependences: CS50
---

> This material is distribured by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my undersantding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Lecture 5](#lecture-5)
  - [Welcome! #](#welcome-)
  - [Data Structures](#data-structures)
  - [Stacks and Queues](#stacks-and-queues)
  - [Resizing Arrays](#resizing-arrays)
  - [Linked Lists](#linked-lists)
    - [Operation](#operation)
    - [Difference between Dot(`.`) and Arrow(`->`) operator ](#difference-between-dot-and-arrow--operator)
    - [Struct Definition](#struct-definition)
    - [Main Function](#main-function)
    - [Adding Numbers to the Linked List](#adding-numbers-to-the-linked-list)
    - [Traversing the Linked List](#traversing-the-linked-list)
    - [Freeing Memory](#freeing-memory)
  - [Trees](#trees)
    - [Data Structure Definition](#data-structure-definition)
    - [Function Declarations](#function-declarations)
    - [Main Function](#main-function-1)
    - [Tree Traversal Functions](#tree-traversal-functions)
  - [Dictionaries](#dictionaries)
  - [Hashing and Hash Tables](#hashing-and-hash-tables)
  - [Trie](#trie)
  - [Summing Up](#summing-up)
- [Section](#section)
- [Shorts](#shorts)
  - [Data Structures](#data-structures-1)
  - [Structs](#structs)
  - [Singly-Linked Lists](#singly-linked-lists)
  - [Doubly-Linked Lists](#doubly-linked-lists)
  - [Hash Tables](#hash-tables)
  - [Tries](#tries)
  - [Queues](#queues)
  - [Stacks](#stacks)
- [Exercises](#exercises)
  - [Practice Problems #](#practice-problems-)
  - [Lab 5: Inheritance](#lab-5-inheritance)
  - [Problem Set 5](#problem-set-5)
  - [What to Do](#what-to-do)
  - [Advice](#advice)

</details>

# Lecture 5

<details>
<summary>Keywords, lookup in <a href="./src/transcripts/lecture5.md">transcript</a></summary>

- abstract data types
- enqueue, dequeue
- stack
- `realloc()`
- struct operator (`->`)
- linked list
- node
- self referential
- traversing, search
- branches
- trees
- root
- balance
- hashing, domain
- collisions, linear probing, clustering
- memory, amount of space

</details>

## Welcome! [#](https://cs50.harvard.edu/x/2023/notes/5//#welcome)

-   All the prior weeks have presented you with the fundamental building blocks of programming.
-   All you have learned in C will enable you to implement these building blocks in higher-level programming languages such as Python.
-   Today, we are going to talk about organizing data in memory.

## Data Structures

_Data structures_ essentially are forms of organization in memory and there are many ways to organize data in memory.

_Abstract data structures_ are those that we can conceptually imagine. When learning about computer science, it’s often useful to begin with these conceptual data structures. Learning these will make it easier later to understand how to implement more concrete data structures.

## Stacks and Queues

_Queues_ are one form of abstract data structure. They have specific properties. Namely, they are FIFO or “first in first out.”
> E.g. you can imagine yourself in a line for a ride at an amusement park. The first person in the line gets to go on the ride first. The last person gets to go on the ride last.

Queues have specific actions associated with them. For example, 
- an item can be _enqueued_; that is, the item can join the line or queue. 
- an item can be _dequeued_ or leave the queue once it reaches the front of the line.

Queues contrast is a _Stack_. Fundamentally, the properties of a stack are different than a queue. Specifically, it is _LIFO_ or “last in first out.”
> E.g. like stacking trays in a cafeteria, a tray that is placed in a stack last is the first that may be picked up.

Stacks have specific actions associated with them. For example, _push_ places something on top of a stack. _Pop_ is removing something from the top of the stack.
-   In code, you might imagine a stack as follows:
    
    ```c
    const int CAPACITY = 50;
    
    typedef struct
    {
        person people[CAPACITY];
        int size;
    }
    stack;
    ```
    
    Notice that an array called people is of type `person`. The `CAPACITY` is how high the stack could be. The integer `size` is how full the stack actually is, regardless of how much it _could_ hold.

The above code has a limitation that resides in the static size of the `CAPACITY`, it can be modified to a dynamic memory allocation using `malloc()` or even `realloc()`. This will be demonstrated below.

## Resizing Arrays
-   Rewinding to Week 2, we introduced you to your first data structure.
-   An array is a block of contiguous memory.
-   You might imagine an array as follows:
    
    ![three boxes with 1 2 3](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide019.png "array")

-   In memory, there are other values being stored by other programs, functions, and variables. Many of these may be unused garbage values that were utilized at one point but are available now for use.
    
    ![three boxes with 1 2 3 among lots of other memory elements](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide022.png "array inside memory")

-   Imagine you wanted to store a fourth value `4` in our array? What would be needed is to allocate a new area of memory and move the old array to a new one.
    ![Three boxes with 1 2 3 above four boxes with 1 2 and two garbage values](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide025.png "two arrays with garbage values")

-   Old garbage values would be overwritten with our new data.
    ![Three boxes with 1 2 3 above four boxes with 1 2 3 and a garbage value](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide026.png "two arrays with garbage value")
-   One of the drawbacks of this approach is that it’s bad design: Every time we add a number, we have to copy the array item by item.
-   Wouldn’t it be nice if we were able to put the `4` somewhere else in memory? By definition, this would no longer be an array because `4` would no longer be in contiguous memory.
-   In your terminal, type `code list.c` and write code as follows:
    
    ```c
    // Implements a list of numbers with an array of fixed size
    
    #include <stdio.h>
    
    int main(void)
    {
        // List of size 3
        int list[3];
    
        // Initialize list with numbers
        list[0] = 1;
        list[1] = 2;
        list[2] = 3;
    
        // Print list
        for (int i = 0; i < 3; i++)
        {
            printf("%i\n", list[i]);
        }
    }
    ```
    
    Notice that the above is very much like what we learned earlier in this course. We have memory being preallocated for three items.

-   Building upon our knowledge obtained more recently, we can leverage our understanding of pointers to create a better design in this code. Modify your code as follows:
    
    ```c
    // Implements a list of numbers with an array of dynamic size
    
    #include <stdio.h>
    #include <stdlib.h>
    
    int main(void)
    {
        // List of size 3
        int *list = malloc(3 * sizeof(int));
        if (list == NULL)
        {
            return 1;
        }
        
        // Initialize list of size 3 with numbers
        list[0] = 1;
        list[1] = 2;
        list[2] = 3;
        
        // List of size 4
        int *tmp = malloc(4 * sizeof(int));
        if (tmp == NULL)
        {
            free(list);
            return 1;
        }
        
        // Copy list of size 3 into list of size 4
        for (int i = 0; i < 3; i++)
        {
            tmp[i] = list[i];
        }
        
        // Add number to list of size 4
        tmp[3] = 4;
        
        // Free list of size 3
        free(list);
        
        // Remember list of size 4
        list = tmp;
        
        // Print list
        for (int i = 0; i < 4; i++)
        {
            printf("%i\n", list[i]);
        }
        
        // Free list
        free(list);
        return 0;
    ```
    
    Notice that a list of size three integers is created. Then, three memory addresses can be assigned the values `1`, `2`, and `3`. Then, a list of size four is created. Next, the list is copied from the first to the second. The value for the `4` is added to the `tmp` list. Since the block of memory that `list` points to is no longer used, it is freed using the command `free(list)`. Finally, the compiler is told to point `list` pointer now to the block of memory that `tmp` points to. The contents of `list` are printed and then freed.

-   It’s useful to think about `list` and `tmp` as both signs that point at a chunk of memory. As in the example above, `list` at one point _pointed_ to an array of size 3. By the end, `list` was told to point to a chunk of memory of size 4. Technically, by the end of the above code, `tmp` and `list` both pointed to the same block of memory.
-   C comes with a very useful function called `realloc` that will reallocate the memory for you. `realloc` takes two arguments. First, it asks you to specify the array you are attempting to copy. Second, it asks you to specify the size to which you would like the final array to be. Modify your code as follows:
    
    ```c
    // Implements a list of numbers with an array of dynamic size using realloc
    
    #include <stdio.h>
    #include <stdlib.h>
    
    int main(void)
    {
        // List of size 3
        int *list = malloc(3 * sizeof(int));
        if (list == NULL)
        {
            return 1;
        }
        
        // Initialize list of size 3 with numbers
        list[0] = 1;
        list[1] = 2;
        list[2] = 3;
        
        // Resize list to be of size 4
        int *tmp = realloc(list, 4 * sizeof(int));
        if (tmp == NULL)
        {
            free(list);
            return 1;
        }
        list = tmp;
        
        // Add number to list
        list[3] = 4;
        
        // Print list
        for (int i = 0; i < 4; i++)
        {
            printf("%i\n", list[i]);
        }
        
        // Free list
        free(list);
        return 0;
    }
    ```
    
    Notice that `int *tmp = realloc(list, 4 * sizeof(int))` creates a list of size four integers. Then, it copies the values of `list` to this new array. Finally, a pointer called `tmp` points to the location of memory of this new array. The copying is handled by `realloc`. Once that copy is made, the memory at the location of `list` is freed. Then, the pointer called `list` is pointed at the location of `tmp`, where the new array is located.

-   You can imagine how using `realloc()` for a queue or stack could be useful. As the amount of data grows, `realloc` could be used to grow or shrink the stack or queue. The process time will grow as the amount of data increases.

## Linked Lists

> In recent weeks, you have learned about three useful primitives. A `struct` is a data type that you can define yourself. A `.` in _dot notation_ allows you to access variables inside that structure. The `*` operator is used to declare a pointer or dereference a variable.

Today, you are introduced to the Arrow (`->`) operator. It goes to an address and looks inside of a structure, i.e. allows to access elements in [Structures](https://www.geeksforgeeks.org/structures-in-cpp/) and [Unions](https://www.geeksforgeeks.org/union-c/). It is used with a [pointer variable pointing to a structure or union](https://www.geeksforgeeks.org/self-referential-structures/). The arrow operator is formed by using a minus sign, followed by the greater than symbol as shown below.   
**Syntax:**  

```c
pointer_name -> variable_name
```

### Operation 
The `->`  gives the value held by `variable_name` to structure or union variable `pointer_name`.

### Difference between Dot(`.`) and Arrow(`->`) operator 
-   The Dot(`.`) operator is used to normally access members of a structure or union.
-   The Arrow(`->`) operator exists to access the members of the structure or the unions using pointers.

A _Linked list_ is one of the most powerful data structures within C. A linked list allows you to include values that are located at varying areas of memory. Further, they allow you to dynamically grow and shrink the list as you desire.

You might imagine three values stored at three different areas of memory as follows:

![Three boxes with 1 2 3 in separate areas of memory](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide036.png "three values in memory")
-   How could one stitch together these values in a list?
-   We could imagine this data pictured above as follows:
    ![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide037.png "three values in memory")
    
-   We could utilize more memory to keep track of where the next item is.
    
    ![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached where memory addresses are in those attached boxes](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide041.png "three values in memory")
    
    Notice that NULL is utilized to indicate that nothing else is _next_ in the list.
-   By convention, we would keep one more element in memory, a pointer, that keeps track of the first item in the list.c 
    ![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached where memory addresses are in those attached boxes now with a final box with the memory address of the first box](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide042.png "three values in memory with pointer")
    
-   Abstracting away the memory addresses, the list would appear as follows:
    ![Three boxes with in separate areas of memory with smaller boxes with a final box where the one box points to another and another until the end of the boxes](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide043.png "three values in memory with pointer")

The elements (boxes) are called _nodes_. A _node_ contains both an _item_ and a pointer called _next_. In code, you can imagine a node as follows:

 ```c
 typedef struct node
 {
     int number;
     struct node *next;
 }
 node;
 ```
> Notice that the item contained within this node is an integer called `number`. Second, a pointer to a node called `next` is included, which will point to another node somewhere in memory.

**Linked lists are not stored in a contiguous block of memory.** They can grow as large as you wish, provided that enough system resources exist. 

The downside, however, is that **more memory is required to keep track of the list instead of an array**. This is because for each element, you must store not just the value of the element, but also a pointer to the next node. Further, linked lists **cannot be indexed** into like is possible in an array because we need to pass through the first `n−1` elements to find the location of the `nth` element.

Because of this, the list pictured above must be linearly searched. Binary search, therefore, is not possible in a list constructed as above.

-   Conceptually, we can imagine the process of creating a linked list. First, `node *list` is declared, but it is of a garbage value.
    ![One garbage value](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide055.png "linked list")
-   Next, a node called `n` is allocated in memory.
    ![One garbage value called n with another pointer called list](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide059.png "linked list")
-   Next, the `number` of node is assigned the value `1`.
    ![n pointing to a node with 1 as the number and garbage value as the next](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide064.png "linked list")
-   Next, the node’s `next` field is assigned `NULL`.
    ![n pointing to a node with 1 as the number and null as the value of next](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide066.png "linked list")
-   Next, `list` is pointed at the memory location to where `n` points. `n` and `list` now point to the same place.
    ![n and list both pointing to a node with 1 as the number and null as the value of next](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide068.png "linked list")
    
-   A new node is then created. Both the `number` and `next` field are both filled with garbage values.
    ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with garbage values](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide073.png "linked list")
-   The `number` value of `n`’s node (the new node) is updated to `2`.
    
    ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and garbage as the next](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide075.png "linked list")
    
-   Also, the `next` field is updated as well.
    ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and null as the next](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide077.png "linked list")
-   Most important, we do not want to lose our connection to any of these nodes lest they be lost forever. Accordingly, `n`’s `next` field is pointed to the same memory location as `list`.
    
    ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and null as the next](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide084.png "linked list")
    
-   Finally, `list` is updated to point at `n`. We now have a linked list of two items.
    ![list pointing to a node with 1 as the number and next pointing to a node with an n pointing the same place the node with one points to a node with 2 as the number and null as the next](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide086.png "linked list")

To implement this in code, modify your code as follows:

```c
// Prepends numbers to a linked list, using while loop to print

#include <cs50.h>
#include <stdio.h>
#include <stdlib.h>

typedef struct node
{
	int number;
	struct node* next;
}
node;

int main(int argc, char *argv[])
{
	// Memory for numbers
	node *list = NULL;
	
	// For each command-line argument
	for (int i = 1; i < argc; i++)
	{
		// Convert argument to int
		int number = atoi(argv[i]);
		
		// Allocate node for number
		node *n = malloc(sizeof(node));
		if (n == NULL)
		{
			return 1;
		}
		n->number = number;
		n->next = NULL;
		
		// Prepend node to list
		n->next = list;
		list = n;
	}
	
	// Print numbers
	node *ptr = list;
	while (ptr != NULL)
	{
		printf("%i\n", ptr->number);
		ptr = ptr->next;
	}
	
	// Free memory
	ptr = list;
	while (ptr != NULL)
	{
		node *next = ptr->next;
		free(ptr);
		ptr = next;
	}
}
```


### Struct Definition

```c
typedef struct node
{
    int number;
    struct node* next;
}
node;
```

The `node` is defined as a `struct`, which represents a single node in the linked list. Each node contains an `int` variable called `number` to store the value and a pointer `next` that points to the next node in the list.

**Is important to know that as the struct refers to itself, a temporary name must be given in order to the next (struct) pointer utilize the same attributes.** So it could be written in this way, and it still works. 

```c
typedef struct temp
{
	int number;
	struct temp* next
}
node;
```

### Main Function

```c
int main(int argc, char *argv[])
{
    node *list = NULL;
```

The `main` function is the entry point of the program. It declares a pointer `list` of type `node` and initializes it to `NULL`. This pointer will serve as the head of the linked list. There's a possibility of the Head to have a value different than `NULL`, depends on the need for the solution.

### Adding Numbers to the Linked List

```c
for (int i = 1; i < argc; i++)
{
    int number = atoi(argv[i]);
	
    node *n = malloc(sizeof(node));
    if (n == NULL)
    {
        return 1;
    }
    n->number = number;
    n->next = NULL;
	
    n->next = list;
    list = n;
}
```

This `for` loop starts from `i = 1` because `argv[0]` is the name of the program itself, and the command-line arguments start from index 1. For each argument, it performs the following steps:

1.  It converts the `i`th command-line argument (`argv[i]`) to an integer using the `atoi` function and stores it in the `number` variable, because numbers received as arguments are but `char`'s
2.  It allocates memory for a new node using `malloc(sizeof(node))`. If the allocation fails (i.e., `malloc` returns `NULL`), the program returns `1` to indicate an error
3.  It sets the `number` value of the new node to the converted value and sets the `next` pointer to `NULL`
4.  It updates the `next` pointer of the new node to point to the current head of the linked list (`list`) and updates `list` to point to the new node. This way, the new node becomes the new head of the list, and the existing list is linked after it

### Traversing the Linked List

```c
node *ptr = list;
while (ptr != NULL)
{
    printf("%i\n", ptr -> number);
    ptr = ptr -> next;
}
```

This code initializes a pointer `ptr` to the head of the linked list (`list`). It then enters a `while` loop that iterates as long as `ptr` is not `NULL`. Inside the loop, it prints the `number` value of the current node and updates `ptr` to point to the next node in the list. This way, *it traverses the entire linked list and prints all the numbers*.

An alternative way to build the traversing loop is:
```c
for (node = *ptr = list; ptr != NULL; ptr -> next)
{...}
```

### Freeing Memory

```c
ptr = list;
while (ptr != NULL)
{
    node *next = ptr->next;
    free(ptr);
    ptr = next;
}
```

This snippet initializes the `ptr` pointer to the head of the linked list (`list`). It then enters a `while` loop that iterates as long as `ptr` is not `NULL`. Inside the loop, it performs the following steps:

1.  It stores the `next` pointer of the current node in a temporary variable called `next`
2.  It frees the memory allocated for the current node using the `free` function
3.  It updates `ptr` to point to the next node (`next`), thereby moving to the next node in the list

This process continues until all nodes in the list have been freed, ensuring that the allocated memory is properly released.

But **if there's some problem allocating the memory** for the next node and the code `returns 1`, then all the previously nodes will leak out of the program, in this case **a [Garbage Collector]() will be needed**.

Considering the amount of time required to search this list, it is in the order of $O(n)$, as in the worst case the entire list must always be searched to find an item. The time complexity for adding a new element to the list will depend on where that element is added. This is illustrated in the examples below.

Notice how numbers are placed at the start of the list. This insertion will run in the order of $O(1)$, as the number of steps it takes to do this does not depend on the size of the list.

-   Further, you could place numbers at the end of the list as illustrated in this code:
    
    ```c
    // Implements a list of numbers using a linked list
    
    #include <cs50.h>
    #include <stdio.h>
    #include <stdlib.h>
    
    typedef struct node
    {
        int number;
        struct node *next;
    }
    node;
    
    int main(int argc, char *argv[])
    {
        // Memory for numbers
        node *list = NULL;
        
        // For each command-line argument
        for (int i = 1; i < argc; i++)
        {
            // Convert argument to int
            int number = atoi(argv[i]);
            
            // Allocate node for number
            node *n = malloc(sizeof(node));
            if (n == NULL)
            {
                return 1;
            }
            n->number = number;
            n->next = NULL;
            
            // If list is empty
            if (list == NULL)
            {
                // This node is the whole list
                list = n;
            }
            
            // If list has numbers already
            else
            {
                // Iterate over nodes in list
                for (node *ptr = list; ptr != NULL; ptr = ptr->next)
                {
                    // If at end of list
                    if (ptr->next == NULL)
                    {
                        // Append node
                        ptr->next = n;
                        break;
                    }
                }
            }
        }
        
        // Print numbers
        for (node *ptr = list; ptr != NULL; ptr = ptr->next)
        {
            printf("%i\n", ptr->number);
        }
        
        // Free memory
        node *ptr = list;
        while (ptr != NULL)
        {
            node *next = ptr->next;
            free(ptr);
            ptr = next;
        }
    }
    ```
    
    Notice how this code _walks down_ this list to find the end. When appending an element, (adding to the end of the list) our code will run in O(n), as we have to go through our entire list before we can add the final element.

-   Further, you could sort your list as items are added:
    
    ```c
    // Implements a sorted list of numbers using a linked list
    
    #include <cs50.h>
    #include <stdio.h>
    #include <stdlib.h>
    
    typedef struct node
    {
        int number;
        struct node *next;
    }
    node;
    
    int main(int argc, char *argv[])
    {
        // Memory for numbers
        node *list = NULL;
        
        // For each command-line argument
        for (int i = 1; i < argc; i++)
        {
            // Convert argument to int
            int number = atoi(argv[i]);
            
            // Allocate node for number
            node *n = malloc(sizeof(node));
            if (n == NULL)
            {
                return 1;
            }
            n->number = number;
            n->next = NULL;
            
            // If list is empty
            if (list == NULL)
            {
                list = n;
            }
            
            // If number belongs at beginning of list
            else if (n->number < list->number)
            {
                n->next = list;
                list = n;
            }
            
            // If number belongs later in list
            else
            {
                // Iterate over nodes in list
                for (node *ptr = list; ptr != NULL; ptr = ptr->next)
                {
                    // If at end of list
                    if (ptr->next == NULL)
                    {
                        // Append node
                        ptr->next = n;
                        break;
                    }
                    
                    // If in middle of list
                    if (n->number < ptr->next->number)
                    {
                        n->next = ptr->next;
                        ptr->next = n;
                    }
                }
            }
        }
        
        // Print numbers
        for (node *ptr = list; ptr != NULL; ptr = ptr->next)
        {
            printf("%i\n", ptr->number);
        }
        
        // Free memory
        node *ptr = list;
        while (ptr != NULL)
        {
            node *next = ptr->next;
            free(ptr);
            ptr = next;
        }
    }
    ```
    
    Notice how this list is sorted as it is built. To insert an element in this specific order, our code will still run in O(n) for each insertion, as in the worst case we will have to look through all current elements.
    

## Trees

-   _Binary search trees_ are another data structure that can be used to store data more efficiently such that it can be searched and retrieved.
-   You can imagine a sorted sequence of numbers.
    
    ![1 2 3 4 5 6 7 in boxes next to each other](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide086.png "tree")
    
-   Imagine then that the center value becomes the top of a tree. Those that are less than this value are placed to the left. Those values that are more than this value are to the right.
    
    ![1 2 3 4 5 6 7 in boxes arranged in a heirarchy 4 is at the top 3 and 5 are below that and 1 2 6 7 are below those](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide119.png "tree")
    
-   Pointers can then be used to point to the correct location of each area of memory such that each of these nodes can be connected.
    
    ![1 2 3 4 5 6 7 in boxes arranged in a heirarchy 4 is at the top 3 and 5 are below that and 1 2 6 7 are below those arrows connect them in a tree formation](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide120.png "tree")
    
-   In code, this can be implemented as follows.
    
    ```c
    // Implements a list of numbers as a binary search tree
    
    #include <stdio.h>
    #include <stdlib.h>
    
    // Represents a node
    typedef struct node
    {
        int number;
        struct node *left;
        struct node *right;
    }
    node;
    
    void free_tree(node *root);
    void print_tree(node *root);
    
    int main(void)
    {
        // Tree of size 0
        node *tree = NULL;
    
        // Add number to list
        node *n = malloc(sizeof(node));
        if (n == NULL)
        {
            return 1;
        }
        n->number = 2;
        n->left = NULL;
        n->right = NULL;
        tree = n;
    
        // Add number to list
        n = malloc(sizeof(node));
        if (n == NULL)
        {
            free_tree(tree);
            return 1;
        }
        n->number = 1;
        n->left = NULL;
        n->right = NULL;
        tree->left = n;
    
        // Add number to list
        n = malloc(sizeof(node));
        if (n == NULL)
        {
            free_tree(tree);
            return 1;
        }
        n->number = 3;
        n->left = NULL;
        n->right = NULL;
        tree->right = n;
    
        // Print tree
        print_tree(tree);
    
        // Free tree
        free_tree(tree);
        return 0;
    }
    
    void free_tree(node *root)
    {
        if (root == NULL)
        {
            return;
        }
        free_tree(root->left);
        free_tree(root->right);
        free(root);
    }
    
    void print_tree(node *root)
    {
        if (root == NULL)
        {
            return;
        }
        print_tree(root->left);
        printf("%i\n", root->number);
        print_tree(root->right);
    }
    ```

### Data Structure Definition

This structure is indeed a Binary Tree, where each node can have up to two other nodes after/below connected. By convention the sides after a node are named child and have sides, `left` and `right`. In this case, every node represents a `int number`.

```c
typedef struct node
{
    int number;
    struct node *left;
    struct node *right;
}
node;
```

### Function Declarations

The code declares two functions: `free_tree` and `print_tree` as prototypes.

```c
void free_tree(node *root);
void print_tree(node *root);
```

### Main Function

The `main` function is the entry point of the program.

1.  It starts by initializing the `tree` variable, which represents the root of the binary search tree, to `NULL`.

```c
node *tree = NULL;
```

2.  Three nodes are created using `malloc` to dynamically allocate memory for each node. The `number` field of each node is set to a specific value, and the `left` and `right` pointers are initially set to `NULL`.

```c
node *n = malloc(sizeof(node));
if (n == NULL)
{
    return 1;
}
n -> number = 2;
n -> left = NULL;
n -> right = NULL;
tree = n;
```

```c
// Similar steps for the second node (1)
// Similar steps for the third node (3)
```

By doing this, a binary search tree is constructed with the values 2, 1, and 3.

3.  The `print_tree` function is called, passing the root of the tree. This function recursively traverses the tree in an in-order manner (left subtree, current node, right subtree) and prints the values of each node.

```c
print_tree(tree);
```

4.  Finally, the `free_tree` function is called to release the memory allocated for the entire tree, starting from the root node.

```c
free_tree(tree);
```

### Tree Traversal Functions

The code provides two functions for working with the binary search tree: `free_tree` and `print_tree`.

1.  `free_tree` is a recursive function that frees the memory of each node in the tree. It traverses the tree in a post-order manner (left subtree, right subtree, current node). It checks if the current node is `NULL` and, if not, recursively calls `free_tree` for its left and right subtrees. Finally, it frees the memory of the current node.

```c
void free_tree(node *root)
{
    if (root == NULL)
    {
        return;
    }
    free_tree(root->left);
    free_tree(root->right);
    free(root);
}
```

2.  `print_tree` is also a recursive function that prints the values of the tree nodes in ascending order. It traverses the tree in an in-order manner (left subtree, current node, right subtree). It checks if the current node is `NULL` and, if not, recursively calls `print_tree` for its left subtree, prints the value of the current node, and then recursively calls `print_tree` for its right subtree.

```c
void print_tree(node *root)
{
    if (root == NULL)
    {
        return;
    }
    print_tree(root->left);
    printf("%i\n", root->number);
    print_tree(root->right);
}
```

By using these two functions, the code can print the values of the tree nodes and release the allocated memory after use.

That's a summary of each process in the provided code!

Searching this tree could be implemented as follows:

```c
bool search(node *tree, int number)
{
	if (tree == NULL)
	{
		return false;
	}
	else if (number < tree->number)
	{
		return search(tree->left, number); // recusrion
	}
	else if (number > tree->number)
	{
		return search(tree->right, number); // recusrion
	}
	else if (number == tree->number)
	{
		return true;
	}
}
```

Notice this search function begins by going to the location of `tree` (i.e. the first node, the root). Then, it uses recursion to search function for `number` on the half of the tree.

A tree like the above offers dynamism that an array does not offer. It can grow and shrink as we wish.

## Dictionaries

_Dictionaries_ are another data structure. They have a _key_ and a  _value_.
The _holy grail_ of time complexity is O(1) or _constant time_. That is, the ultimate is for access to be instantaneous.

![a graph of various time comlexities where O of log n is second best and O of 1 is best](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide151.png "time complexity")

-   Dictionaries can offer this speed of access.

## Hashing and Hash Tables

_Hashing_ is the idea of taking a value and being able to output a value that becomes a shortcut to it later.

> For example, hashing _apple_ may hash as a value of `1`, and _berry_ may be hashed as `2`. Therefore, finding _apple_ is as easy as asking the _hash_ algorithm where _apple_ is stored. 

While not ideal in terms of design, ultimately, putting all _a_’s in one bucket and _b_’s in another in the given example.

The concept of _bucketizing_ hashed values illustrates how you can use this concept: a hashed value can be used to shortcut finding such a value.

**A _hash function_ is an algorithm that reduces a larger value to something small and predictable. Generally, this function takes in an item you wish to add to your hash table, and returns an integer representing the array index in which the item should be placed**.

A _hash table_ is a fantastic combination of both arrays and linked lists. When implemented in code, a hash table is an _array_ of _pointers_ to _node_s. 

- A hash table could be imagined as follows:

![a verticle column of 26 boxes one for each letter of the alphabet](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide157.png "alphabet")

Notice that this is an array that is assigned each value of the alphabet.

-   Then, at each location of the array, a linked list is used to track each value being stored there:
    ![a verticle column of 26 boxes one for each letter of the alphabet with various names from the harry potter unverise emergint to the right albus is with a and harry is with h](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide169.png "alphabet")

_Collisions_ are when you add values to the hash table, and something already exists at the hashed location. In the above, collisions are simply appended to the end of the list.

Collisions can be reduced by better programming your hash table and hash algorithm. You can imagine an improvement upon the above as follows:

![a verticle column of various boxeds arranged by H A G and H A R with hagrid emerging from H A G and harry emerging from H A R](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide184.png "alphabet")

-   You, as the programmer, have to make a decision about the advantages of using more memory to have a large hash table and potentially reducing search time or using less memory and potentially increasing search time.

## Trie

-   _Tries_ are another form of data structure.
-   _Tries_ are always searchable in constant time.
-   One downside to _Tries_ is that they tend to take up a large amount of memory. Notice that we need $26×5=130$ `node`s just to store _Hagrid_!
-   _Hagrid_ would be stored as follows:
    ![hagrid being spelled with one letter at a time where one letter is associated with one list H from one list A from another and so on ](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide207.png "tries")

-   _Harry_ would then be stored as follows:
    ![hagrid being spelled with one letter at a time where one letter is associated with one list H from one list A from another and so on and harry being spelled similarly where hagrid and harry share a two common letters H and A](https://cs50.harvard.edu/x/2023/notes/5//cs50Week5Slide209.png "tries")

## Summing Up
In this lesson, you learned about using pointers to build new data structures. Specifically, we delved into…

-   Data structures
-   Stacks and queues
-   Resizing arrays
-   Linked lists
-   Dictionaries
-   Tries

See you next time!

---
# Section 
> [Transcript](./src/transcripts/section5.md)

- What are the key trade-offs between data structures we should consider in decisions about which to use?
- What are some of the primary operations we should know how to do and what should we prioritize
	- Insertion
	- Search
	- Deletion
- How can we build our very own hash table?

A good Hash function always gives you the same value for the same input, produces an even distribution across, and use all the slots of memory.

---

# Shorts

## Data Structures 
> [Transc](./src/transcripts/shorts5_data_struct.md)

- Arrays 
- Structs
- Linked-Lists
- Hash Tables 
- Tries 
- Queues
- Stacks

## Structs
> [Transc](./src/transcripts/shorts5_struct.md)


## Singly-Linked Lists
> [Transc](./src/transcripts/shorts5_lists1.md)

- In order to work with s-linked lists effectively, there are a number of operations that we need to understand:

1. Create a linked list when it doesn't already exist.
2. Search through a linked list to find an element.
3. Insert a new node into the linked list.
4. Delete a single element from a linked list.
5. Delete an entire linked list.

## Doubly-Linked Lists
> [Transc](./src/transcripts/shorts5_lists2.md)

- In order to work with d-linked lists effectively, there are a number of operations that we need to understand:

1. Create a linked list when it doesn't already exist.
2. Search through a linked list to find an element.
3. Insert a new node into the linked list.
4. Delete a single element from a linked list.
5. Delete an entire linked list.

## Hash Tables
> [Transc](./src/transcripts/shorts5_hash_tabs.md)

The combination of an Array and a Linked-List.  A good hash function should:

- Use only the data being hashed
- Use all of the data being hashed
- Be deterministic
- Uniformly distribute data
- Generate very different hash codes for very similar data

## Tries
> [Transc](./src/transcripts/shorts5_tries.md)


## Queues
> [Transc](./src/transcripts/shorts5_queues.md)


## Stacks
> [Transc](./src/transcripts/shorts5_stacks.md)

> So a queue and a stack depends on how you actually use them, and not so much what you build kind of underneath the hood.
---

# Exercises

## Practice Problems [#](https://cs50.harvard.edu/x/2023/problems/5/)

In addition to this week’s lab and problem set, you’re welcome to try any of these (optional!) practice problems:

- [Trie](./trie.md) [#](https://cs50.harvard.edu/x/2023/problems/5/trie/), for introducing more complex data structures and working with tries

## [Lab 5: Inheritance](./lab5.md)
> Full code [here](./src/lab5.c)

## Problem Set 5

> Collaboration on problem sets is not permitted except to the extent that you may ask classmates and others for help so long as that help does not reduce to another doing your work for you, per the course’s policy on [academic honesty](https://cs50.harvard.edu/x/2023/psets/5/../../syllabus/#academic-honesty).
>
> The staff conducts random audits of submissions to CS50x. Students found to be in violation of this policy will be removed from the course. Students who have already completed CS50x, if found to be in violation, will have their CS50 Certificate permanently revoked.

## What to Do

Be sure you have completed [Lab 5](./lab5.md) before beginning this problem set.

1.  Log into [code.cs50.io](https://code.cs50.io) using your GitHub account
2.  Run `update50` in your codespace’s terminal window to ensure your codespace is up-to-date and, when prompted, click **Rebuild now**
3.  Submit [Speller](./speller.md) [#](https://cs50.harvard.edu/x/2023/psets/5/speller/)

## Advice

-   Try out any of David’s programs from [Week 5](https://cs50.harvard.edu/x/2023/psets/5/../../weeks/5/).
-   If you see any errors when compiling your code with `make`, focus first on fixing the very first error you see, scrolling up as needed. If unsure what it means, try asking `help50` for help. For instance, if trying to compile `speller`, and
    
	```bash
    make speller
    ```
	
	is yielding errors, try running
	
	```bash
    help50 make speller
    ```
    instead!