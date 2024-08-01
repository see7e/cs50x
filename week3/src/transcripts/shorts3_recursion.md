---
title: SHORST3 - RECURSION - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] 

DOUG LLOYD: You probably think that code is just used to accomplish a task. You write it out. It does something. That's pretty much it. 

You compile it. You run the program. You're good to go. 

But believe it or not, if you code for a long time, you actually might come to see code as something that's beautiful. It solves a problem in a very interesting way, or there's just something really neat about the way it looks. You might be laughing at me, but it's true. And recursion is one way to sort of get this idea of beautiful, elegant-looking code. It solves problems in ways that are interesting, easy to visualize, and surprisingly short. 

The way recursion works is, a recursive function is defined as a function that calls itself as part of its execution. That might seem a little strange, and we'll see a little bit about how this works in a moment. But again, these recursive procedures are going to be so elegant because they're going to solve this problem without having all these other functions or these long loops. You'll see that these recursive procedures are going to look so short. And they really are going to make your code look a lot more beautiful. 

I'll give you an example of this to see how a recursive procedure might be defined. So if you're familiar with this from math class many years ago, there's something called the factorial function, which is usually denoted as an exclamation point, which is defined over all positive integers. And the way that n factorial is calculated is you multiply all of the numbers less than or equal to n together-- all the integers less than or equal to n together. 

So 5 factorial is 5 times 4 times 3 times 2 times 1. And 4 factorial is 4 times 3 times 2 times 1 and so on. You get the idea. 

As programmers, we don't use n, exclamation point. So we'll define the factorial function as fact of n. And we'll use factorial to create a recursive solution to a problem. And I think you might find that it's a lot more visually appealing than the iterative version of this, which we'll also take a look at in a moment. 

So here are a couple of facts-- pun intended-- about factorial-- the factorial function. The factorial of 1, as I said, is 1. The factorial of 2 is 2 times 1. The factorial of 3 is 3 times 2 times 1, and so on. We talked about 4 and 5 already. 

But looking at this, isn't this true? Isn't factorial of 2 just 2 times the factorial of 1? I mean, the factorial of 1 is 1. So why can't we just say that, since factorial of 2 is 2 times 1, it's really just 2 times the factorial of 1? 

And then extending that idea, isn't the factorial of 3 just 3 times the factorial of 2? And the factorial of 4 is 4 times the factorial of 3, and so on? In fact, the factorial of any number can just be expressed if we kind of carry this out forever. We can kind of generalize the factorial problem as it's n times the factorial of n minus 1. It's n times the product of all the numbers less than me. 

This idea, this generalization of the problem, allows us to recursively define the factorial function. When you define a function recursively, there's two things that need to be a part of it. You need to have something called a base case, which, when you trigger it, will stop the recursive process. 

Otherwise, a function that calls itself-- as you might imagine-- could go on forever. Function calls the function calls the function calls the function calls the function. If you don't have a way to stop it, your program will be effectively stuck at an infinite loop. It will crash eventually, because it'll run out of memory. But that's beside the point. 

We need to have some other way to stop things besides our program crashing, because a program that crashes is probably not beautiful or elegant. And so we call this the base case. This is a simple solution to a problem which stops the recursive process from occurring. So that's one part of a recursive function. 

The second part is the recursive case. And this is where the recursion will actually take place. This is where the function will call itself. 

It won't call itself in exactly the same way it was called. It'll be a slight variation that makes the problem it's trying to solve a teeny bit smaller. But it generally passes the buck of solving the bulk of the solution to a different call down the line. 

Which of these looks like the base case here? Which one of these looks like the simplest solution to a problem? We have a bunch of factorials, and we could continue going on-- 6, 7, 8, 9, 10, and so on. 

But one of these looks like a good case to be the base case. It's a very simple solution. We don't have to do anything special. 

The factorial of 1 is just 1. We don't have to do any multiplication at all. It seems like if we're going to try and solve this problem, and we need to stop the recursion somewhere, we probably want to stop it when we get to 1. We don't want to stop before that. 

So if we're defining our factorial function, here's a skeleton for how we might do that. We need to plug in those two things-- the base case and the recursive case. What's the base case? If n is equal to 1, return 1-- that's a really simple problem to solve. 

The factorial of 1 is 1. It's not 1 times anything. It's just 1. It's a very easy fact. And so that can be our base case. If we get passed 1 into this function, we'll just return 1. 

What's the recursive case probably look like? For every other number besides 1, what's the pattern? Well, if we're taking the factorial of n, it's n times the factorial of n minus 1. 

If we're taking the factorial of 3, it's 3 times the factorial of 3 minus 1, or 2. And so if we're not looking at 1, otherwise return n times the factorial of n minus 1. It's pretty straightforward. 

And for the sake of having slightly cleaner and more elegant code, know that if we have single-line loops or single-line conditional branches, we can get rid of all of the curly braces around them. So we can consolidate this to this. This has exactly the same functionality as this. 

I'm just taking away the curly braces, because there's only one line inside of those conditional branches. So these behave identically. If n is equal to 1, return 1. Otherwise return n times the factorial of n minus 1. So we're making the problem smaller. If n starts out as 5, we're going to return 5 times the factorial of 4. And we'll see in a minute when we talk about the call stack-- in another video where we talk about the call stack-- we'll learn about why exactly this process works. 

But while factorial of 5 says return 5 times factorial of 4, and 4 is going to say, OK, well, return 4 times the factorial of 3. And as you can see, we're sort of approaching 1. We're getting closer and closer to that base case. 

And once we hit the base case, all of the previous functions have the answer they were looking for. Factorial of 2 was saying return 2 times the factorial of 1. Well, factorial of 1 returns 1. So the call for factorial of 2 can return 2 times 1, and give that back to factorial of 3, which is waiting for that result. 

And then it can calculate its result, 3 times 2 is 6, and give it back to factorial of 4. And again, we have a video on the call stack where this is illustrated a little more than what I'm saying right now. But this is it. This alone is the solution to calculating the factorial of a number. 

It's only four lines of code. That's pretty cool, right? It's kind of sexy. 

So in general, but not always, a recursive function can replace a loop in a non-recursive function. So here, side by side, is the iterative version of the factorial function. Both of these calculate exactly the same thing. 

They both calculate the factorial of n. The version on the left uses recursion to do it. The version on the right uses iteration to do it. 

And notice, we have to declare a variable an integer product. And then we loop. So long as n is greater than 0, we keep multiplying that product by n and decrementing n until we calculate the product. So these two functions, again, do exactly the same thing. But they don't do it in exactly the same way. 

Now, it is possible to have more than one base case or more than one recursive case, depending on what your function is trying to do. You aren't necessarily just limited to a single base case or a single recursive case. So an example of something with multiple base cases might be this-- the Fibonacci number sequence. 

You may recall from elementary school days that the Fibonacci sequence is defined like this-- the first element is 0. The second element is 1. Both of those are just by definition. 

Then every other element is defined as the sum of n minus 1 and n minus 2. So the third element would be 0 plus 1 is 1. And then the fourth element would be the second element, 1, plus the third element, 1. And that would be 2. And so on and so on. 

So in this case, we have two base cases. If n is equal to 1, return 0. If n is equal to 2, return 1. Otherwise, return Fibonacci of n minus 1 plus Fibonacci of n minus 2. 

So that's multiple base cases. What about multiple recursive cases? Well, there's something called the Collatz conjecture. I'm not going to say, you know what that is, because it's actually our final problem for this particular video. And it's our exercise to work on together. 

So here's what the Collatz conjecture is-- it applies to every positive integer. And it speculates that it's always possible to get back to 1 if you follow these steps. If n is 1, stop. We've got back to 1 if n is 1. 

Otherwise, go through this process again on n divided by 2. And see if you can get back to 1. Otherwise, if n is odd, go through this process again on 3n plus 1, or 3 times n plus 1. So here we have a single base case. If n is equal to 1, stop. We're not doing any more recursion. 

But we have two recursive cases. If n is even, we do one recursive case, calling n divided by 2. If n is odd, we do a different recursive case on 3 times n plus 1. 

And so the goal for this video is to take a second, pause the video, and try and write this recursive function Collatz where you pass in a value n, and it calculates how many steps it takes to get to 1 if you start from n and you follow those steps up above. If n is 1, it takes 0 steps. Otherwise, it's going to take one step plus however many steps it takes on either n divided by 2 if n is even, or 3n plus 1 if n is odd. 

Now, I've put up on the screen here a couple of test things for you, a couple of tests cases for you, to see what these various Collatz numbers are, and also an illustration of the steps that need to be gone through so you can sort of see this process in action. So if n is equal to 1, Collatz of n is 0. You don't have to do anything to get back to 1. You're already there. 

If n is 2, it takes one step to get to 1. You start with 2. Well, 2 is not equal to 1. So it's going to be one step plus however many steps it takes on n divided by 2. 

2 divided by 2 is 1. So it takes one step plus however many steps it takes for 1. 1 takes zero steps. 

For 3, as you can see, there's quite a few steps involved. You go from 3. And then you go to 10, 5, 16, 8, 4, 2, 1. It takes seven steps to get back to 1. And as you can see, there's a couple other test cases here to test out your program. So again, pause the video. And I'll go jump back now to what the actual process is here, what this conjecture is. 

See if you can figure out how to define Collatz of n so that it calculates how many steps it takes to get to 1. So hopefully, you have paused the video and you aren't just waiting for me to give you the answer here. But if you are, well, here's the answer anyway. 

So here's a possible definition of the Collatz function. Our base case-- if n is equal to 1, we return 0. It doesn't take any steps to get back to 1. 

Otherwise, we have two recursive cases-- one for even numbers and one for odd. The way I test for even numbers is to check if n mod 2 equals 0. This is basically, again, asking the question, if you recall what mod is-- if I divide n by 2 is there no remainder? That would be an even number. 

And so if n mod 2 equals 0 is testing is this an even number. If so, I want to return 1, because this is definitely taking one step plus Collatz of whatever number is half of me. Otherwise, I want to return 1 plus Collatz of 3 times n plus 1. That was the other recursive step that we could take to calculate the Collatz-- the number of steps it takes to get back to 1 given a number. So hopefully, this example gave you a little bit of a taste of recursive procedures. Hopefully, you think code is a little more beautiful if implemented in an elegant, recursive way. But even if not, recursion is a really powerful tool nonetheless. And so it's definitely something to get your head around, because you'll be able to create pretty cool programs using recursion that might otherwise be complex to write if you're using loops and iteration. I'm Doug Lloyd. This is CS50. 