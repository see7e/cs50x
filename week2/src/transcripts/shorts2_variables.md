---
title: SHORST2 - VARIABLES - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

DOUG LLOYD: As you start working with functions, another thing is going to become really important to understand, which is the concept of variable scope. So scope is a characteristic of a variable that defines from which functions that variable can be accessed. There are two primary scopes in C, local variables and global variables. Now, local variables can only be accessed within the functions in which they're created. They can't be accessed by every other function that exists in your program, only the function in which it was created. Global variables, on the other hand, can be accessed by any function in the program. And the reason for that is because they're not created inside of any particular function. We declare them outside of all of the functions, which means that every function knows where it is and can access and manipulate it. 

So far in the course you've pretty much been working exclusively with local variables. Here's an example of a very, very simple main function and a very simple additional function that we've written. In this case, x, which I've colored green just to highlight the locality or the scope of that variable, is local to the function triple. main cannot refer to x at all. It doesn't know what it is. No other function, in fact, if we had additional functions in here, could refer to x. 

Similarly, results which I've colored blue, is local only to main. Only main knows what the variable result is. triple cannot use it. 

Now as I mentioned, global variables do exist. If you declare that variable outside of any function, all of the functions in the program can refer to it. So in this case I've highlighted in green a global variable declaration. In this case, the variable being declared is called global, just to be extremely clear about it. It is of type float. And I assign it the value 0.5050. 

You'll notice that in main and in triple, I am able to refer to global. And in fact, if I go through the program as indicated, main first calls triple, triple multiplies global by 3, which sets its value to 1.5-something, 1.51 or something like that, and then main also prints out the value of global. So main will not print out 0.5050, it will print out global times 3, 1.51. So you've got to be careful when you're working with global variables. While they're very flexible in being able to pass information around so that every function can use it, it also can have some dangerous consequences if one function changes the value of a variable before you expect it to be changed. 

Why does this distinction matter? Why do we care whether some variables are local and others are global? Well, for the most part, local variables in C are what's called passed by value when we make a function call. What does that mean? 

Well, when a variable is passed by value, the callee, which is another way of saying the function that is receiving the variable that gets passed in as an input, it actually doesn't receive that variable itself. It receives its own copy of it to work with. This is a really important distinction. We just saw a second ago that with global variables, if we manipulate the global variable in one function, the effect in that one function carries through to every other function. 

But with local variables, that's not true. Each function when it receives variables as input receive copies of those variables, not the variables themselves. So what is the side effect of that? That means that the variable in the caller, the function that is making the function call, is unchanged unless you override it. 

For example, in this code foo is not changed at all. Int foo equals 4, call triple of foo, inside of triple, we would expect that foo would be multiplied by 3 and returned, but there's actually no effect. 

Here though, a very subtle difference. This does have the effect we want. Do you see why? We're overriding foo in main this time. 

So int foo equals 4, foo equals triple foo, when we make that call, triple gets its own copy of foo, its own copy of 4. It says return 4 times 3, or whatever variable gets passed in times 3. And then we assign the return value of triple to foo again. So this actually would overwrite foo. This is the only way to do this with local variable. So now if we add another line of code here at the end of main to print out the value of foo, it would in fact print out 12. 

Variable scope is generally not too much of a problem if you name all of your variables different things. But it can get kind of nasty if the same variable name appears in multiple functions, which will happen a lot. If you ever do work in the real world where you are working on collaborative programs and people in different teams are working together to write the same program or the same set of programs, they'll frequently reuse variable names, particularly common ones like x, y, i, j, and so on. 

But when variables have the same name, scope issues can get a little trickier to parse. For example, do you know what would be printed out at the end of this particular program? Take a minute. Pause the video and read through this program. You can see at the top we have a function declaration for a function called increment. That function takes a single parameter, an integer which we call x. And it outputs an integer. That's the return type at the beginning. 

Then we have main, a couple of lines of code in main, the last of which is a print statement. And remember, that's the question here. What is actually going to be printed at the end of this function? And then we actually have the definition of increment below. 

So take a minute, step through the code, trace things out. Do you know what will be printed at the end of this particular program? 

All right. Hopefully, you've taken a few seconds to try and parse this one out. Let's do it together. 

So I've crossed out increment's declaration at the top there. It was kind of a distraction. It's not its own variable. It doesn't have its own scope. It's just a function declaration, so for purposes of trying to parse out what's happening in this program, we might as well just avoid it. 

Now we have in this case, the reason this problem is tricky is because we have local variables in both main and increment, each of which is called x. And of course the crux of this issue is trying to suss out which x gets changed and how does it get changed. So I've colored every instance of x that's local to main red. And I've colored every instance of x that's local to increment blue. 

Notice in that third line of main, y equals increment x, that increment is not being passed main's x, or the red x. It's getting passed a copy of it. And it's only going to work with that copy of it, the blue x. If you're mathematically inclined, you might have instead thought of this as x sub m for main and x sub i for increment. But it's the same idea. x sub m, or the red x's in the previous slide, are the variables that are local-- is the instance of x rather that is local to main, and x sub i, or the blue variables in the previous slide, are the instances of x that are local to increment. 

So, were you able to figure out what this function printed at the end? I'm Doug Lloyd, and this is CS50. 