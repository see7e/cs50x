---
title: SHORST3 - LINEAR SEARCH - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DOUG LLOYD: Linear search is an algorithm we can use to find an element in an array. An algorithm recall is a step-by-step set of instructions for completing a task. 

The linear search algorithm works as follows. Iterate across the array from left to right, looking for a specified element. 

In pseudocode, which is a more distilled version of this sentence, if the first element is what you're looking for, you can stop. Otherwise, move to the next element and keep going over and over until you find the element, or you don't. So we can use the linear search algorithm, for example, to find the target value nine in this array. Well we start at the beginning. If it's what we're looking for, we can stop. It's not, we're not looking for 11. So otherwise, move to the next element. 

So we look at 23. Is 23 what we're looking for? Well no, so we move on to the next element, and the next element, and we keep going through this process over and over and over, until we land on a situation like this. 

Nine is what we're looking for, and this element of the array is, it's value is nine. And so we found what we're looking for, and we can stop. The linear search has completed, successfully. 

But what about if we're looking for an element that's not in our array. Does linear search still work? Well sure. So we repeat this process starting at the first element. If it's what we're looking for, we can stop. It's not. Otherwise, we move to the next element. 

But we can keep repeating this process, examining each element in turn, hoping that we find the number 50. But we won't know if we've found the number 50 or if we didn't, until we've stepped over every single element of the array. 

Only once we've done that and come up short, can we conclude that 50 is not in the array. And so the linear search algorithm, well it failed, per se. But not in the sense that it was unsuccessful in doing what we asked it to do. 

It was unsuccessful in as much as it didn't find 50, but 50 wasn't in the array. But we have exhaustively searched through every single element and so, while we didn't find anything, linear search still succeeds even if the element is not in the array. 

So what's the worst case scenario with linear search? Well we have to look through every single element, either because the target element is the last element of the array, or the element we're looking for doesn't actually exist in the array at all. What's the best case scenario? Well we might find the element immediately. And how many elements do we then have to look at in the best case, if we're looking for it and we find it at the very beginning? We can stop immediately. 

What does this say about the complexity of linear search? Well in the worst case, we have to look at every single element. And so it runs in O of n, in the worst case. 

In the best case, we're gonna find the element immediately. And so runs in omega of 1. 

I'm Doug Lloyd. This is CS50. 