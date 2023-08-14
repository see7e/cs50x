---
title: SHORST2 - DEBUGGIN1 - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

SPEAKER 1: Welcome, everyone. My name is Carter. And today I'm going to show you my guessing game and how I can use debug50 to help figure out what's wrong with it. So here, I'm trying to write a guessing game that is written in the spirit of the elementary school game where you would guess a number and someone would tell you, it's right or wrong. And I called my program Guess. So I can run it in the terminal with ./guess. 

Here go to ./guess, hit Enter, and I have to guess a number. So here I might guess, maybe 2, and hit Enter. But then I get this flood of messages in the terminal. And I'm wondering, well, what's wrong with this? Why am I getting so many messages here? 

And to try to figure that out, I can go into my code with code guest.c. And then I can see, well, I'm not entirely sure what may be wrong here. So I need to pause my code at some point. And for that, I can use a break point. 

So let me go ahead and go to this left side of my guess.c file, where I see these red circles pop up. I can click on one of them to turn it bright red. And at that point, I've set a pause point in my code. And I can use debug50 to go in and actually step through my code and see what's going on in there. 

So let me go ahead and type debug50 of guess, hit Enter. So now that I have my code opened up in debug50, I can see a few different things. I can see that my number variable is currently set to 0. And my guess is currently set to this odd 32,764. But as I go through my code, I'll actually see those numbers fall into place. 

So if I use this Step Over button to walked to the next line of my code, I can see that number becomes 5, as I expect it to on line 6. And then as I go to line 8 and Step Over that, I get prompted for, what's my guess? And at that point, I might type, well, 3 again. And I'll hit Enter. And then I see guess becomes 3. 

So now I'm wondering, well, if my guess is wrong and my number is 5, my guess is 3, shouldn't I only get wrong guess just once? So I'll actually just keep walking through my code with Step Over. And I'll see, I'm printing "Wrong guess!", which seems right. 

And now I should just exit the program. That should be it. But I really see that my line in that yellow highlight is going back up to 10, line 10 there. And it's actually continuing to go through and print "Wrong guess!" 

And so at this point, I can actually see that maybe the bug in my code is I shouldn't have used a while loop. I should have, maybe, used an if statement, where I'm only checking for this condition once. So now that my while loop has changed to an if statement, I should be able to recompile my code and see what's changed. 

So I can use "make guess". And then I'll run my code, guess. And when I guess 3, I guess I should get "Wrong guess!" So I'll do 3. And then I'll get "Wrong guess!", but also "You're correct!". And at this point, there's probably another bug in my code. And so I'll actually leave this one up to you, to use debug50 and see, well, why am I getting both "Wrong Guess!" and "You're correct!"? 