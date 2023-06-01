---
title: SHORST2 - DEBUGGIN2 - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

SPEAKER 1: Welcome, everyone. My name is Carter, and today I'll show you my secret program. You can run the program by typing ./secret into your terminal, and if you type in the right password, you should be able to see come on in. So let's try it out. 

I'll do ./secret, and maybe I don't know the secret phrase, so I'll just say, let me in. And at which point, I don't get any response. So let me try it again and do ./secret. Maybe password is the password here. But it's not. And I'll just reveal to you that the password is please. So if I type ./secret, and I type in please, I should see come on in. But I don't. And so what's the problem here? 

Well, maybe I should look into my code, and maybe step through it bit by bit. So I'll do code secret.c, and I can see the very top of my code, starting with this int main(void) function. To step through my code, remember we can use debug50 to set a breakpoint, or a place to pause in our code. So I can go to this left side here, find a pale red circle, and turn it into a bright red circle as I click it, and set that pause point, or that breakpoint. 

Now I can do debug50 of secret, and then my code should boot up, and I should be able to pause right at that moment I'm asking the user for their secret phrase. Of course, I have to actually step over that line for it to actually run my program, so I'll then step over, and I can type in my secret phrase of please. 

OK, so that seems pretty good. I see that phrase becomes please, and correct is currently false, but it should change to true after I do this check phrase function. So I'll step over check phrase, and I see it's actually still false. And so of course, if I run past line 13, nothing will happen. I actually won't print "come on in." 

So at this point, debug50 seems to be not really helping me here. I've walked through my entire program, but I haven't seen what went wrong in my code. Well, debug50 has this option to step into a function, actually dive in and see what's happening underneath that hood of that function. So what I can do is go to debug50 again, and run debug50 with secret, wait for my code to go to that breakpoint again, and I'll walk through that first piece where I type in my phrase, please. 

But now, instead of stepping over this check phrase function, I actually want to dive into it and see what's going on underneath there. So I'll do step into in debug50, and then see, I'm setting my password to be please. So if I step over line 22, I should see that password becomes please, as it does on this left hand side. 

And now, when I check for if phrase is password, I should actually be able to return true, because it seems that phrase is the same as password. So I'll step over that, and see-- well actually, I get to line 29. And this is kind of subtle, but in C, you can't compare two strings using two equal signs. You actually could use a different function called string compare, or strcmp for short. 

So to use strcompare, I can use strcmp, and give it two arguments, phrase and password. And with these two inputs, strcompare will tell me are they exactly equivalent or not. If they are equivalent, strcmp-- or strcompare-- will give me 0 as a value back. So now my code is saying, if these strings are equivalent-- and I know they are because strcompare is giving me zero-- I can go ahead and return true and say this is the correct password. 

So with this new code here, I should be able to exit debug50 and go back to the terminal. And now I can make secret again, run secret, type in my password of please, and now there it is. It says, come on in. 

And with that, we've seen how debug50 can help us not only step over our code, but dive into functions and see the bugs inside of them. 