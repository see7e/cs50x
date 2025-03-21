---
title: SHORST1 - CONDITIONALS - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

All right. So now let's talk about something really useful in programming-- conditional statements. So conditional expressions allow your programs to make decisions and take different forks in the road, something I alluded to little earlier, depending on the values of variables, or based on what the user inputs at the programmer, at the command line, or if you have a prompt or something like that. C has a couple of different ways to express conditional expressions, which we also sometimes will call a conditional branch in your programs. And some of these are going to look pretty familiar to you from scratch, so we'll even pull them up side by side, just you can make that analogy in your head. So, if-- if is a pretty simple conditional. If you recall from scratch on the right here you could fill in that is hexagon with a blue expression if mouse down or if x is less than 10, or something like that. And then, if x was less than 10, or if the mouse was in fact, down, all of the code inside of the puzzle piece would execute. All the things that fit inside that C shape. 

Similarly, do we have if on the left there. If Boolean expression, which I'm just using as a substitute for one of the Boolean expressions we previously discussed, open curly brace, close curly brace. So think of open curly brace and closed curly brace as sort of analogous to the sandwich effect of the if block on the right from scratch. 

If the Boolean expression in the if statement is true, then all the lines of code between the curly braces will execute in order from top to bottom. If the Boolean expression is false, we'll skip over everything in between the curly braces, because we only want to go down that fork in the road if the Boolean expression is true. 

We can take this one step further with if else. So this Scratch block is pretty similar to the one we saw just a second ago, except it takes two different paths based on what happens. So if the mouse was down, or if x was less than 10, we'll do everything that's in between that first fork, that first C. , 

Otherwise, if the mouse is up, or x is not less than 10, we will do everything in the second set. And that's analogous to what you see here for C. If Boolean expression, do the stuff between the first set of curly braces. Else, do the stuff between the second set of curly braces. So if the Boolean expression is true, we'll do whatever's between the first set. If the Boolean expression is false, that would trigger the else, and we would do whatever's in the second set of curly braces. Again, top to bottom, all lines in between the braces. 

In C, it's possible to create an if-else if-else chain. In fact you can have if-else if-else if-else, if, and so on and so on and so on. In Scratch, this required nesting the blocks. You add an if-else, and you had to put another one inside of the else, and so on, and it got kind of nested and complicated. But C, we don't have to do that. We can actually just have it be a chain like this. Again, as you might expect, all of these branches are mutually exclusive. You can only ever go down one of the branch. If this is true. Otherwise, if this is true. Otherwise, if this is true. Otherwise, do this. So all four of the branches in this example are mutually exclusive. It's an if-else if-else chain. 

It is possible though, and sometimes very useful, to create a chain of not mutually exclusive branches. In this example, only the third and fourth branches are mutually exclusive. It could be that you could satisfy the first condition, and you could satisfy the second condition, and you could satisfy the third condition-- in which case you would go down the first branch, then you go down a second branch, then you would go down the third branch. Or perhaps you satisfy the first condition, and the second condition, but you don't satisfy the third condition. In this case you go down the first branch and the second branch, and then the fourth branch, 

The reason for this is that the else will only bind to the nearest if. So even though there's an else here, that doesn't necessarily create a mutually exclusive chain of everything. It's only the expression there with Boolean expression 3-- that's the mutually exclusive with the else. So it is possible, and sometimes quite useful, as I said, to create a chain of not mutually exclusive branches. Let's take a look at a different kind of conditional, which you have not seen before in Scratch. There's something called the switch statement. The switch statement is kind of neat because it's a conditional statement that allows you to specify distinct cases, instead of relying on Boolean expressions to make decisions for you. So for example, let's say that I have this program, and I'm asking the user to provide input to me. So I say, int x = Get Int(), and if you're not familiar yet, get int is a function that is also included in the CS50 library, so if you `#include` CS50.H you'll have access to Get Int() and all of its cousins-- GetFloat, GetString, and so on. Basically one Get function for every data type that we've already discussed. 

So Int x equals GetInt. Basically what's happening is I'm at the terminal. I'm asking the user to type in a number. 

And here I'm switching what I'm doing, depending on what the user typed at the prompt. So if they typed one, I print out one. And then I break. If they type two, I print out two. And then I break. It's important to break between each case because otherwise you will fall through. So if I didn't have any breaks there, and the user typed one, what would happen is it would print one, two, three, sorry. That's kind of strange behavior, right? You might think so. But there are actually some cases where this could be a pretty useful thing. So here's another example of a switch statement where I omit the breaks. But I do it on purpose. 

So what happens here? Think for a second. You may even want to pause the video. 

What happens here if the user types four? So I've asked the user for input. And they provide the value 4. What gets printed when I do that? On the previous slide, there were breaks between all the cases. And so it would just print four and then stop. But in this case, it won't. What will happen is you will fall through each case. 

So in this case I've organized my cases in such a way that if the user types 4, I will print four, three, two, one, blast off. And if they typed 5, I would start at five and do the same thing. If they typed 1, I would just do one, blast off. 

So in this case, I'm using a switch kind of cleverly so that I do intend to fall through all the cases. But generally you're probably gonna want to break between all of them, unless you have a situation like this one where you're kind of leveraging the fact that you'll fall through the cases without a break. So that's the second of the major types of conditional statements. The last of which is ?: So I have two snippets of C code here. One on the left and one on the right. The one on the left should probably be pretty familiar to you. 

I have Int x. And I probably should have asked the user for-- this should probably be Int x equals GetInt, or something like that. And then I'm making a decision. If some Boolean expression is true, assign x the value 5. Otherwise, assign x the value 6. 

That on the left should probably be pretty familiar from our discussion of If Else just a moment ago. Would you be surprised to know that the line on the right does the exact same thing? 

So this is called ?: or sometimes called the ternary operator. And it's pretty cool. It's usually used as a cute trick. 

But what it allows you to do is to simulate an If Else with really small, really trivially short conditional branches. You generally wouldn't use ?: if you had six lines of code between each set of curly braces. But if you're just making a quick decision, if you're going to do one thing or the other and it's very simple, this might be an example of how to do it with ?: the ternary operator. So Int x equals expression ? The thing after the question mark is what x's value will be if expression is true. 

The thing after the colon is what x's value would be if the expression was false. So I'm asking myself, is the expression true? If it is, assign x the value 5. If it's not, assign x the value 6. Again, like I said. This is usually just a cute trick. And sometimes if you become really comfortable with it, you'll do this because it looks kind of cool in your programs. Generally I'm presenting it to you now so you're familiar with it if you see it. But certainly know you don't have to write it in any of your code. But it is something to be familiar with, because you'll definitely encounter snippets of code here and there where this ?: syntax, AKA the ternary operator, is used. 

So quick summary on what conditionals are, and what the options are available to you in C. You have If and if-else, and if else if, et cetera. You can use Boolean expressions for those to make decisions. 

With switch statements you use discrete cases to make decisions. You would specifically say, if it's one, or if it's two, or if it's three, I'll do this thing, or this thing, or this thing. And ?: can to be used to replace very simple if-else branches, or if-else chains to make your code look a little fancy. 

I'm Doug Lloyd. And this is CS50. 