---
title: SHORST3 - BINARY SEARCH - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] 

DOUG LLOYD: All right. So binary search is an algorithm we can use to find an element inside of an array. Unlike linear search, it requires a special condition be met beforehand, but it's so much more efficient if that condition is, in fact, met. 

So what's the idea here? it's divide and conquer. We want to reduce the size of the search area by half each time in order to find a target number. This is where that condition comes into play, though. We can only leverage the power of eliminating half of the elements without even looking at them if the array is sorted. 

If it's a complete mix up, we can't just out of hand discard half of the elements, because we don't know what we're discarding. But if the array is sorted, we can do that, because we know that everything to the left of where we currently are must be lower than the value we're currently at. And everything to the right of where we are must be greater than the value we're currently looking at. 

So what's the pseudocode steps for binary search? We repeat this process until the array or, as we proceed through, sub arrays, smaller pieces of the original array, is of size 0. Calculate the midpoint of the current sub array. 

If the value you're looking for is in that element of the array, stop. You found it. That's great. Otherwise, if the target is less than what's at the middle, so if the value we're looking for is lower than what we see, repeat this process again, but change the end point, instead of being the original complete full array, to be just to the left of where we just looked. 

We knew that the middle was too high, or the target was less than the middle, and so it must exist, if it exists at all in the array, somewhere to the left of the midpoint. And so we'll set the array location just to the left of the midpoint as the new end point. Conversely, if the target is greater than what's at the middle, we do the exact same process, but instead we change the start point to be just to the right of the midpoint we just calculated. And then, we begin the process again. 

Let's visualize this, OK? So there's a lot going and on here, but here's an array of the 15 elements. And we're going to be keeping track of a lot more stuff this time. So in linear search, we were just caring about a target. But this time we want to care about where are we starting to look, where are we stopping looking, and what's the midpoint of the current array. So here we go with binary search. We're pretty much good to go, right? I'm just going to put down below here a set of indices. This is basically just what element of the array we're talking about. With linear search, we care, inasmuch as we need to know how many elements we're iterating over, but we don't actually care what element we're currently looking at. In binary search, we do. And so those are just there as a little guide. 

So we can start, right? Well, not quite. Remember what I said about binary search? We can't do it on an unsorted array or else, we are not guaranteeing that the certain elements or values aren't being accidentally discarded when we just decide to ignore half of the array. 

So step one with binary search is you must have a sorted array. And you can use any of the sorting algorithms we've talked about to get you to that position. So now, we're in a position where we can perform binary search. 

So let's repeat the process step by step and keep track of what's happening as we go. So the first we need to do is calculate the midpoint of the current array. Well, we'll say we're, first of all, looking for the value 19. We're trying to find the number 19. The first element of this array is located at index zero, and the last element of this array is located at index 14. And so we'll call those start and end. 

So we calculate the midpoint by adding 0 plus 14 divided by 2; pretty straightforward midpoint. And we can say that the midpoint is now 7. So is 15 what we're looking for? No, it's not. We're looking for 19. But we know that 19 is greater than what we found at the middle. 

So what we can do is change the start point to be just to the right of the midpoint, and repeat the process again. And when we do that, we now say the new start point is array location 8. What we've effectively done is ignored everything to the left of 15. We've eliminated half of the problem, and now, instead of having to search over 15 elements in our array, we only have to search over 7. So 8 is the new start point. 14 is still the end point. 

And now, we go over this again. We calculate the new midpoint. 8 plus 14 is 22, divided by 2 is 11. Is this what we're looking for? No, it's not. We're looking for a value that's less than what we just found. So we're going to repeat the process again. We're going to change the end point to be just to the left of the midpoint. So the new end point becomes 10. And now, that's the only part of the array we have to sort through. So we have now eliminated 12 of the 15 elements. We know that if 19 exists in the array, it must exist somewhere between element number 8 and element number 10. 

So we calculate the new midpoint again. 8 plus 10 is 18, divided by 2 is 9. And in this case, look, the target is at the middle. We found exactly what we're looking for. We can stop. We successfully completed a binary search. All right. So we know this algorithm works if the target is somewhere inside of the array. Does this algorithm work if the target is not in the array? Well, let's start it again, and this time, let's look for the element 16, which visually we can see does not exist anywhere in the array. 

The start point is again 0. The end point is again 14. Those are the indices of the first and last elements of the complete array. And we'll go through the process we just went through again, trying to find 16, even though visually, we can already tell that it's not going to be there. We just want to make sure this algorithm will, in fact, still work in some way and not just leave us stuck in an infinite loop. 

So what's the step first? Calculate the midpoint of the current array. What's the midpoint of the current array? Well, it's 7, right? 14 plus 0 divided by 2 is 7. Is 15 what we're looking for? No. It's pretty close, but we're looking for a value slightly bigger than that. 

So we know that it's going to be nowhere to the left of 15. The target is greater than what's in the midpoint. And so we set the new start point to be just to the right of the middle. The midpoint is currently 7, so let's say the new start point is 8. And what we've effectively done again is ignored the entire left half of the array. 

Now, we repeat the process one more time. Calculate the new midpoint. 8 plus 14 is 22, divided by 2 is 11. Is 23 what we're looking for? Unfortunately, no. We're looking for a value that is less than 23. And so in this case, we're going to change the end point to be just to the left of the current midpoint. The current midpoint is 11, and so we'll set the new end point for the next time we go through this process to 10. 

Again, we go through the process again. Calculate the midpoint. 8 plus 10 divided by 2 is 9. Is 19 what we're looking for? Unfortunately, no. We're still looking for a number less than that. So we'll change the end point this time to be just to the left of the midpoint. The midpoint is currently 9, so the end point will be 8. And now, we're just looking at a single element array. 

What's the midpoint of this array? Well, it starts at 8, it ends at 8, the midpoint is 8. Is that what we're looking for? Are we looking for 17? No, we're looking for 16. So if it exists in the array, it must exist somewhere to the left of where we currently are. So what are we going to do? Well, we'll set the end point to be just to the left of the current midpoint. So we'll change the end point to 7. Do you see what just happened here, though? Look up here now. 

Start is now greater than end. Effectively, the two ends of our array have crossed, and the start point is now after the end point. Well, that doesn't make any sense, right? So now, what we can say is we have a sub array of size 0. And once we're gotten to this point, we can now guarantee that element 16 does not exist in the array, because the start point and end point have crossed. And so it's not there. Now, notice that this is slightly different than the start point and end point being the same. If we had been looking for 17, it would have been in the array, and the start point and end point of that last iteration before those points crossed, we would have found 17 there. It's only when they cross that we can guarantee that the element does not exist in the array. 

So let's take a lot fewer steps than linear search. In the worst case scenario, we had to split up a list of n elements repeatedly in half to find the target, either because the target element will be somewhere in the last division, or it doesn't exist at all. So in the worst case, we have to split up the array-- do you know? Log of n times; we have to cut the problem in half a certain number of times. That number of times is log n. 

What's the best case scenario? Well, the first time we calculate the midpoint, we find what we're looking for. In all the previous examples on binary search we've just gone over, if we had been looking for the element 15, we would have found that immediately. That was at the very beginning. That was the midpoint of the first attempt at a split of a division in binary search. 

And so in the worst case, binary search runs in log n, which is substantially better than linear search, in the worst case. In the best case, binary search runs in omega of 1. So binary search is a lot better than linear search, but you have to deal with the process of sorting your array first before you can leverage the power of binary search. 

I'm Doug Lloyd. This is CS 50. 