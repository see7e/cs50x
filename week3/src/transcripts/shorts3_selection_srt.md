---
title: SHORST3 - SELECTION SORT - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DOUG LLOYD: Selection sort is an algorithm that, as you might expect, sorts a set of elements. And algorithm recall is a step-by-step set of instructions for completing a task. 

In selection sort the basic idea is this, find the smallest unsorted element and add it to the end of the sorted list. Effectively what this does is build a sorted list, one element at a time. Breaking it down to pseudocode we could state this algorithm as follows, repeat this until no unsorted elements remain. Search through the unsorted data to find the smallest value, then swap the smallest value with the first element of the unsorted part. 

It may help to visualize this, so let's take a look at this. So this, I contend, is an unsorted array and I've indicated it by indicating that all of the elements are colored red, they are not yet sorted. This is the entire unsorted part of the array. 

So let's go through the steps of selection sort to sort this array. So again, we're gonna repeat until no unsorted elements remain. We're gonna search through the data to find the smallest value, and then swap that value with the first element of the unsorted part. 

Right now, again, the entire array is the unsorted part. All of the red elements are unsorted. So we search through and we find the smallest value. We start at the beginning, we go to the end, we find the smallest value is, one. So that's part one. And then part two, swap that value with the first element of the unsorted part, or the first red element. 

In this case that would be five, so we swap one and five. When we do this, we can visually see that we've moved the smallest valued element of the array, to the very beginning. Effectively sorting that element. 

And so we can indeed confirm and state that one, is sorted. And so we'll indicate the sorted portion of our array, by coloring it blue. 

Now we just repeat the process again. We search through the unsorted part of the array to find the smallest element. In this case, it's two. 

We swap that with the first element of the unsorted part. In this case two also happens to be the first element of the unsorted part. So we swap two with itself, which really just leaves two where it is, and it's sorted. Continuing on, we search through to find the smallest element. It's three. We swap it with the first element, which is five. And now three is sorted. 

We search through again, and we find the smallest element is four. We swap it with the first element of the unsorted part, and now four is sorted. 

We find that five is the smallest element. We swap it with the first element of the unsorted part. And now five is sorted. 

And then lastly, our unsorted part consists of just a single element, so we search through and we find that six is the smallest, and in fact, only element. And then we can state that it is sorted. And now we've switched our array from being completely unsorted in red, to completely sorted in blue, using selection sort. 

So what's the worst case scenario here? Well in the absolute worst case, we have to look over all of the elements of the array to find the smallest unsorted element, and we have to repeat this process n times. Once for each element of the array because we only, in this algorithm, sort one element at time. 

What's the best case scenario? Well it's exactly the same, right? We actually have to still step through every single element of the array in order to confirm that it is, in fact, the smallest element. 

So the worst case runtime, we have to repeat a process n times, once for each of n elements. And in the best case scenario, we have to do the same. 

So thinking back to our computational complexity toolbox, what do you think is the worst case runtime for selection sort? What do you think is the best case runtime for selection sort? 

Did you guess Big O of n squared, and Big Omega of n squared? You'd be right. Those are, in fact, the worst case and best case run times, for selection sort. 

I'm Doug Lloyd. This is CS50. 