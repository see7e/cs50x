---
title: SHORST3 - BUBBLE SORT - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DOUG LLOYD: All right, so bubble sort is an algorithm you can use to sort a set of elements. Let's take a look at how it works. 

So the basic idea behind bubble sort is this. We generally want to move higher valued elements generally to the right, and lower valued elements generally to the left, as we would expect. We want the lower things to be at the beginning, and the higher things to be at the end. 

How do we do this? Well in pseudocode code, we could say, let's set a swap counter to a non-zero value. We'll see why we do that in a second. And then we repeat the following process until the swap counter is 0, or until we make no swaps at all. 

Reset the swap counter to 0 if it's not already 0. Then look at every adjacent pair of elements. If those two elements are not in order, swap them, and add 1 to the swap counter. If you're thinking about this before you visualize it, notice that this will move lower valued elements to the left and higher valued elements to the right, effectively doing what we want to do, which is move those groups of elements in that way. Let's visualize how this might look using our array that we used to test out these algorithms. We have an unsorted array here again, indicated by all of the elements being in red. And I set my swap counter to a nonzero value. I arbitrarily chose negative 1-- it's not 0. We want to repeat this process until the swap counter is 0. This is why I set my swap counter to some non-zero value, because otherwise the swap counter would be 0. We wouldn't even begin the process of the algorithm. So again, the steps are-- reset the swap counter to 0, then look at every adjacent pair, and if they're out of order, swap them, and add 1 to the swap counter. So let's begin this process. So the first thing we do is we set the swap counter to 0, and then we start looking at each adjacent pair. 

So we first start looking at 5 and 2. We see that they are out of order and so we swap them. And we add 1 to the swap counter. So now our swap counter is 1, and 2 and 5 have been switched. Now we repeat the process again. 

We look at the next adjacent pair, 5 and 1-- they're also out of order, so we swap them and add 1 to the swap counter. Then we look at 5 and 3. They are out of order, so we swap them and we add 1 to the swap counter. Then we look at 5 and 6. They're in order, so we don't actually need to swap anything this time. Then we look at 6 and 4. They're also out of order, so we swap them and we add 1 to the swap counter. 

Now notice what's happened. We've moved 6 all the way to the end. So in selection sort, if you've seen that video, what we did was we ended up moving the smallest elements in building the sorted array essentially from left to right, smallest to largest. In the case of bubble sort, if we're following this particular algorithm, we're actually going to be building the sorted array from right to left, largest to smallest. We have effectively bubbled 6, the largest value, all the way to the end. 

And so we can now declare that that is sorted, and in future iterations-- going through the array again-- we don't have to consider 6 anymore. We only have to consider the unsorted elements when we're looking at adjacent pairs. So we have finished one pass through bubble sort. So now we go back to the question, repeat until the swap counter is 0. Well the swap counter is 4, so we're going to keep repeating this process again. 

We're going to reset the swap counter to 0, and look at each adjacent pair. So we start with 2 and 1-- they're out of order, so we swap them and we add 1 to the swap counter. 2 and 3, they're in order. We don't need to do anything. 3 and 5 are in order. We don't need to do anything there. 

5 and 4, they are out of order, and so we need to swap them and add 1 to the swap counter. And now we've moved 5, the next largest element, to the end of the unsorted portion. So we can now call that part of the sorted portion. 

Now you're looking at the screen and probably can tell, as can I, that the array is sorted right now. But we can't prove that yet. We don't have a guarantee that it's sorted. But this is where the swap counter's going to come into play. 

So we've completed a pass. The swap counter is 2. So we're going to repeat this process again, repeat until the swap counter is 0. Reset the swap counter to 0. So we'll reset it. 

Now look at each adjacent pair. That's in order, 1 and 2. 2 and 3 are in order. 3 and 4 are in order. So at this point, notice we've completed looking at every adjacent pair, but the swap counter is still 0. 

If we don't have to switch any elements, then they must be in order, by virtue of this process. And so an efficiency of sorts, that we computer scientists love, is we can now declare the entire array must be sorted, because we didn't have to swap any elements. That's pretty nice. 

So what's the worst case scenario with bubble sort? In the worst case the array is in completely reverse order, and so we have to bubble each of the large elements all the way across the array. And we effectively also have to bubble all of the small elements back all the way across the array, too. So each of the n elements has to move across all of the other n elements. So that's the worst case scenario. In the best case scenario though, this is slightly different from selection sort. The array is already sorted when we go in. We don't have to make any swaps on the first pass. So we might have to look at fewer elements, right? We don't have to repeat this process a number of times over. 

So what does that mean? So what's the worst case scenario for bubble sort, and what's the best case scenario for bubble sort? Did you guess this? In the worst case you have to iterate across all the n elements n times. So the worst case is n squared. 

If the array is perfectly sorted though, you only have to look at each of the elements once. And if the swap counter is still 0, you can say this array is sorted. And so in the best case, this is actually better than selection sort-- it's omega of n. 

I'm Doug Lloyd. This is CS50. 