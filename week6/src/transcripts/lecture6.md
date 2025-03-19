---
title: LECTURE6 - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DAVID MALAN: All right. This is CS50, and this is week six, wherein we finally transition from Scratch to C to, now, Python. And, indeed, this is going to be somewhat of a unique experience in that, just like a few weeks past-- perhaps, for the first time-- and now, today, you're going to learn a new language. But the goal isn't just to throw another fire hose of content and syntax and whatnot at you, but rather, to really equip you all to actually teach yourself new languages in the future. 

And so, indeed, what we'll do today, what we'll do this coming week is prepare you to stand on your own. And once Python is passe and the world has moved on to some other language in some number of years, you'll be well equipped to figure out how to wrap your mind around some new syntax, some new language and solve problems, as well. Now, you recall, in week zero, this is where we started-- just saying hello to the world. 

And that quickly escalated just a week later in C to be something much, much more cryptic. And if you've still struggled with some of the syntax, find yourself checking your notes or your previous code, that's totally normal. And that's one of the reasons why there are languages besides C out there-- among them, this language called Python. Humans over the decades have realized, gee, that wasn't necessarily the best design decision, or humans have realized, wow, you know what? Now that computers have gotten faster with more memory and faster CPUs, we can actually do more with our programming languages. 

So just as human languages evolve, so do actual programming languages. And even within a programming language, there's typically different versions. We, for instance, have been using version C11 of C, which was updated in 2011. But Python itself continues to evolve, and it's now up to version 3-plus. And so there, too, these things will evolve in the coming days. 

Thankfully, what you're about to see is "Hello, World!" for the third time, but it's going to be literally this. None of the crazy syntax above or below, fewer semicolons, if any, fewer currently braces. And, really, a lot of the distractions get out of the way. So to get there, let's consider exactly how we've been programming up until now. So you write a program in C and you've got, hopefully, no syntax error, so you're ready to build it-- that is, compile it. 

And so, you've run make, and then, you've run the program, like ./hello. Or if you think back to week two, where we took a peek underneath the hood of what make is doing, it's really running the actual compiler-- something called clang-- maybe with some command-line arguments creating a program called hello. And then, you could do ./hello. So, today, you're going to start doing something similar in spirit, but fewer steps. 

No longer will you have to compile your code and then run it, and then, maybe, fix or change it, and then compile your code and run it, and then repeat, repeat. The process of running your code is going to be distilled into just a single step. And the way to think of this, for now, is that, whereas C is frequently used as, indeed, a compiled language whereby you convert it first to 0s and 1s, Python's going to let you speed things up whereby you, the human programmer, don't have to compile it. 

You're just going to run what's called an interpreter-- which, by design, is named the exact same thing as the language itself-- and by running this program installed in VS Code or, eventually, on your own Macs or PCs. This is just going to tell your computer to interpret this code and figure out how to get down to that lower level of 0s and 1s. But you don't have to compile the code yourself anymore. 

So with that said, let's consider what the code is going to look like, side by side. In fact, let's look back at some Scratch blocks, just like we did with C in week one, and do some side by sides. Because even though some of the syntax this week and beyond is going to be different, the ideas are truly going to be the same. There's not all that much intellectually new just yet. 

So whereas, in week zero, we might have said hello to the world with this purple puzzle piece, today, of course-- or, rather, in week one, it looked like this in C. But today, moving forward, it's going to, quite simply, look like this instead. And if we go back and forth for just a moment, here, again, is the version in C, noticing the very C-like characteristics. And just at a glance here, in Python, I claim it's now this. What do you apparently need not worry about anymore? What's gone? 

So semi-colon is gone. And, indeed, you don't need those to finish most of your thoughts anymore. Anything else? 

AUDIENCE: Backslash n. 

DAVID MALAN: So the backslash n is absent. And that's curious because we're still going to get a new line, but we'll see that it's become the default. And this one's a little more subtle, but now, the function is called print instead of printf. So it's a little more familiar in that sense. 

All right. So when it comes to using libraries-- that is, code that other people have written-- in the past, we've done things like `#include` cs50.h to use CS50's own header file or standard I/O or standard lib or string or any number of other header files you have all used. Moving forward, we're going to give you, for this first week, a similar CS50 library-- just very short-term training wheels that we'll quickly take off because, in reality, it's a lot easier to do things in Python, as we'll see. But the syntax for this, now, is going to be to import the CS50 library in this way. 

And when we have, now, this ability, we can actually start writing some code right away. In fact, let me switch over to VS Code here. And just as in the past, I'll create a new file. But instead of creating something called .c, I'm going to go ahead and create my first program called hello.py, using code space hello dot py. That, of course, gives me this new tab. 

And let me actually, quite simply, do what I proposed-- print, quote unquote, "Hello, world" without the /n, without the semicolon, without the f in print. And now, let me go down to my terminal window. And I don't have to compile it. I don't have to do dot slash. I, instead, run a program called python, whose purpose in life is, now, to interpret my code top to bottom, left to right. 

And if I run python of hello.py, crossing my fingers, as always-- voila. Now I have printed out "hello, world." So we seem to have gotten the new line for free, in the sense where it's automatically happening. The dollar sign isn't weirdly on the same line, like it once was in week one. But that's just a minor detail here. If we switch back to, now, some other capabilities-- well, indeed, with the CS50 library, you can also not just import the library itself, but specific functions. 

And you'll see that, temporarily, we're going to give you a helper function called get_string, just like in C, that just makes it work exactly the same way as in C. And we'll see a couple of other functions that will just make life easier, initially. But, quickly, will we take those training wheels off so that nothing is, indeed, CS50-specific. All right. Well, how about functions, more generally, in Python? Let's do a whirlwind tour, if you will, much like we did in that first week of C, comparing one to the other. 

So back in our world of Scratch, one of the first programs we wrote was this one here, whereby we ask the human their name. We then used the return value that was automatically stored in this answer variable as an second argument to join so that we could say "Hello, David" or "Hello, Carter." So this was back in week zero. In week one, we converted it to this. 

And here is a perfect example of things like escalating quickly. And, again, this is why we start in Scratch. There's just so much distraction here to achieve the same idea. But even today, we're going to chip away at some of that syntax. So, in C, we had to declare the variable as a string, here. We of course, had the semicolon and more. Well, in Python, the comparable code, now, is going to look, more simply, like this. So semicolon is, again, gone on both lines, for that matter. So that's good. 

What else appears to have changed or disappeared? Yeah. 

AUDIENCE: [? Do you have ?] the same type of variable? 

DAVID MALAN: Yeah. So I didn't have to specifically say that answer is now a string. And, indeed, Python is dynamically typed. And, in fact, it will infer from context exactly what it is you are storing in that variable. Other details that seem a little bit different? A little bit different. What else jumps out at you here? I'll go back. This was the C version. And maybe focus, now, on the second line because we've rather exhausted the first. 

Here's, now, the Python version. What's different here? Yeah? 

AUDIENCE: You don't need to worry about %s or percent anything. You just have the variable after [? them. ?] 

DAVID MALAN: Yeah. There's no %s anymore. There's no second argument, at the moment, per se, to print. Now, it is still a little weird. It's as though I've deployed some addition here, arithmetically. But that's not the case. Some of you have program before. And plus, some of you might know, means what in this context? So to combine or, more technically-- anyone know the buzzword? Yeah. 

AUDIENCE: Concatenate. 

DAVID MALAN: To concatenate. So to concatenate is the fancy way of what Scratch calls joining, which is to take one string on the left, one string on the right and to join them together. To glue them together, if you will. So this is not addition. It would be if it were numbers involved instead. But because we've got a string-- Hello comma-- and another string implicitly in this variable based on what the human typed in in response to this get_string function. 

That's going to concatenate Hello comma space, and then, David or Carter or whatever the human has typed in. But it turns out, there's going to be different ways to do this in Python. And we'll show you a few different ones. And here, too, try not to get too hung up on or frustrated by all of the different ways you can solve problems. Odds are, you're going to be picking up tips and techniques for years to come if you continue programming. So let's just give you a few of the possible ways. 

So here's a second way you could print out hello comma David or hello comma Carter. But what has changed? In the previous version, I used concatenation explicitly. And the space here is important, grammatically, just so we get that in the final phrase. Now, I'm proposing to get rid of that space to add a comma outside of the double quotes, as well. 

But if you think back to C, this probably just means that print, similar in spirit to printf, can take not just one argument, but even two. And in fact, because of this comma in the middle that's outside of the double quotes, it's hello comma, and then, it will be automatically concatenated with-- even without using the plus, to whatever the value of answer is. And by default, just for grammatical prettiness, the print function always gives you a space for free in between each of the multiple arguments you pass in. 

We'll see how you can override that down the line. But, for now, that's just another way to do it. Now, perhaps the better, if slightly cryptic way to do this-- or just the increasingly common way-- is, probably, the third version, which looks a little weird, too. And, probably, the weirdness jumps out. We've suddenly introduced these curly braces, which I promised were mostly gone. And they are. 

But inside of this string here, I've done a curly brace, which might mean what? Just intuitively. And here is an example of how you learn a new language. Just infer, from context, how Python probably works. What might this mean? Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah. So this is an indication, because the curly braces-- because this was the way Python was designed-- that we want to plug in the value of answer, not literally A-N-S-W-E-R. And the fancy word here is that the answer variable will be interpolated-- that is, substituted with its actual value. But, but, but-- and this is actually weird-looking; this was introduced a few years ago to Python. What else did I have to change to make these curly braces work, apparently? 

Yeah? 

AUDIENCE: Drop the f before the-- 

DAVID MALAN: Yeah. There's this weird f. And so, it's like part of printf. But now, it's inside the parentheses there. This is just the way Python designed this. So a few years ago, when they introduced what are called format strings or fstrings, you literally prefix your quoted string with the letter f. And then, you can use trickery like this, like putting curly braces so that the value will be substituted automatically. 

If you forget the f, you're going to literally see hello comma curly brace answer closed curly brace. If you add the f, it's, indeed, interpolated. The value is plugged in. All right. Questions on how we can just say hello to the world via Python, in this case. Yeah? 

AUDIENCE: If you do this without the f, what would happen? 

DAVID MALAN: If you do this without the-- 

AUDIENCE: [? The f. ?] 

DAVID MALAN: Without the f? If you omit the f, you will literally see H-E-L-L-O comma curly brace A-N-S-W-E-R closed curly brace. So, in fact, let's do this. Let me go back to VS Code here, quickly. I've still got my file called hello.py open. And let me go ahead and change this ever so slightly. So I'm going to go ahead and-- let's say from cs50 import get_string. And that's just the new syntax I propose using to import a function from someone else's library. 

I'm going to now go ahead and ask the question-- let's go ahead and use get_string, storing the result in answer. So get_string, quote unquote, "What's your name?" And then, on this line, I'm going to deliberately make a mistake here, exactly to your question. Let me just say hello comma answer, and just this. Now, even though answer is a variable, Python's not going to be so presumptuous as to just plug in the value of a variable called answer. 

What it's going to do, of course, is-- if I type in my name-- whoops. I typed too fast. Let me go ahead and rerun that again. If I run python with hello.py, type in my name and hit Enter, I get hello comma answer. Well, let me do one better. Let me apply these curly braces as before. Let me rerun python of hello.py. What's your name? D-A-V-I-D. 

And here's, again, the answer to your question. Now, we get, literally, the curly braces. So the fix here, ultimately, is just going to be to add the f there, rerun my program again with David. And now, hello comma David. So this is, admittedly, a little more cryptic than the ones with the plus or the comma, but this is just increasingly common. Why? because you can read it left to right. It's nice and convenient. It's less cryptic than the %s's. 

So it's a new and improved version, if you will, of printf in C, based on decades of experience of programmers doing things like this. Questions on printing in this way? We're now on our way to programming in Python. Anything? All right. Well, what more can we do with this language, here? Well, let me propose that we consider that we have, for instance, a few other features that we can add to the mix, as well-- namely, let's say some data types, as well. 

So let me flip over here, to back to the slides. And there's different data types in Python, as we'll soon see. But they're not as explicit. As we already saw, by using a string from get_string, you don't have to explicitly state what it is. But you saw-- recall, in C-- all of these various data types. And then, in Python, nicely enough, this list is about to get shorter. 

And so, here is our list in C. Here is an abbreviated list in Python. So we're still going to have strings, but they're going to be more succinctly called strs now, S-T-R. We're still going to have ints for integers. We're still going to have floats for floating point values. We're even going to have bools for true and false. But what's missing, now, from the list is long and floats. And why is that? Or rather, long and double. 

We'll recall that, in C, those used more bits. Well, in Python, the smaller data types, previously-- int and float, themselves-- just used more bits for you. And so, you don't need to distinguish between small and large. You just use one data type, and the language gives you a bigger range than before. It turns out, though, there's going to be some other features, as well, of Python, and these data types-- one of which will be called range, another of which will be list. 

So gone will be arrays. We'll actually use something literally called a list. Tuples-- sort of x, y pairs for coordinates and things like that. Dicts for dictionaries-- so we'll have built-in capabilities for storing keys and values we'll see, and even a set. Mathematically, a set is a collection of values, but it automatically gets rid of duplicates for you. 

So all of these things, we could absolutely implement in C if we wanted. And, indeed, in problem set five, you've been implementing your very own spell checker using some form of hash table. Well, it turns out that, in Python, you can solve those same problems, but perhaps a little more readily. In fact, let me go back over here to VS Code, and let me propose that I do the following. 

Let me go ahead and create a file called dictionary.py. Let me propose that I try to implement, say-- problem set five-- our spell checker in Python instead of C and achieve, ultimately, the same kind of behavior whereby I'll be able to spell check a whole bunch of words. So this is jumping the gun a little bit because you're about to see syntax will revisit over the course of today. But, for now, I've got a new file called dictionary.py. 

And let me begin to create some placeholders for functions. We'll see in just a bit that, in Python, you can define a function called check, and that check function can take a word as its input. And I'll come back to this in just a moment. In Python, I can define a second function like load, which itself will take a whole dictionary, just like in problem set five. And I'll go ahead and come back to the implementation of this. 

Meanwhile, we might similarly implement a function called size, which takes no arguments but, ultimately, is going to return the size of my dictionary of words. And then, lastly, for consistency with problem set five, we might define an unload function, whose purpose in life is to free any memory that you've been using, just to give it back to the computer. Now, odds are, whether you're still working on speller or have finished speller, you wrote a decent amount of lines of code. And indeed, it's been, by design, a challenge. 

But one of the reasons for these higher-level languages like Python is that you can stand on the shoulders of programmers before you and solve very common problems much more quickly. So that you can focus on building your new app or your web application or your own project to solve problems of interest to you. So at the risk of crushing some spirits, let me propose that, in Python if you want a dictionary for something like a spell checker, well, that's fine. 

Go ahead and give yourself a variable, like words, to store all of those words and just assign it equal to a dictionary-- or dict, for short, in Python. That will give you a hash table. Now, it turns out, in speller recall, you don't need to worry about words and definitions. It's just about spell-checking the words. So strictly speaking, we don't need keys and values. We just need keys. 

So I'm going to save myself a few more keystrokes by just saying that, technically, in Python, using a set suffices. Again, a set is just a collection of values with no duplicates. But they don't necessarily have keys and values. It's just one or the other. But now that I have-- on line one, I claim the equivalent, in Python, of a hash table, I can actually do something like this. Here's how I might implement the check function in Python. 

If the word passed into this function is in my variable called words, well, return True. Else, go ahead and return False. Done. No, wait. You're thinking, if anything at all, maybe we want to handle lowercase instead of just uppercase and lowercase. Well, you know what? In Python, if you want to force a whole word to lowercase, you don't have to iterate over it with a loop. You don't have to use any of that C-type functions or anything. Just say word.lower, and that will convert the whole thing to lowercase for parity with the dictionary. 

All right. How about something like the load function in Python? Well, in Python, you can open files just like in C. For instance, in Python, I might do open, the dictionary argument in read mode, just like fopen in Python. I might do something like this. For each line in that file, let me go ahead and add, to my words variable, that line. And then, let me go ahead and close that file. And I think I'm done. 

I'm just going to go ahead and return True, just because I think I'm already done. Now, here, too, I could nitpick a little bit. Technically, if I'm reading in every line from the file, every line in the dictionary ends with, technically, a backslash n. But there's an easy way to get rid of that, just like you might see with an alternative syntax. What I'm actually going to do is this. Let me grab from the current line, the current word, by stripping off with reverse strip-- rstrip; a function we'll, again, see-- that just gets rid of the trailing new line-- the backslash n at the end of that line. 

And what I really want to do, then, is add this word to that dictionary. Meanwhile, if I want to figure out what the size is of my dictionary, well-- and, see, you're probably writing code to iterate over all of those lines, and you're just going to count them up using a variable. Not so in Python. You can just return the length of those words. And better still, in Python, you don't have to manage your own memory. No more malloc. No more free. No more manual thinking about memory. The language just deals with all of that for you. 

So you know what? It suffices for me to just return True and claim that unloading is done for me. And that's it. Again, whether, you're in the middle of or already finished, this might, perhaps, adjust some frustration, but also, enlightenment in that this is why higher-level languages exist. You can build on top of the same principles, the same ideas, with which you've been dealing, struggling even this past week. 

But you can now express yourself all the more succinctly. This one line implements a hash table for you, and all of this, now, just uses that hash table in a simpler way. Any questions, now, on this, keeping in mind that the point, nonetheless, of speller in p-set 5 is to understand what's really going on underneath the hood and, better still, to notice this. 

This might seem all rather amazing, but let me go ahead and do this. I've actually got a couple of versions of speller written here, and I've got a version written in C that I won't show the source code for. But I'm going to go ahead and make that version of speller in C. And I'm going to go ahead here and, let's say, split my window here for just a moment. And I'm going to go into a Python version of speller, really, that I just wrote. 

And on the left-hand side here, let me go ahead and run speller-- the version I compiled in C-- using a big text like the Sherlock Holmes text, which has a whole lot of words in it. And on the right-hand side, let me run python of speller.py, which is a separate file I wrote in advance, just like we give you speller.c. And I'll, similarly, run this on the Sherlock Holmes text. 

And I'm going to do my best to hit Enter on the left and the right of my screen at the same time. But we should see, hopefully, the same list of misspelled words and the timings thereof. So here we go on the right. Here we go on the left. All right. A race to see which one wins here. C is on the left. Python is on the right. OK. Interesting. Hopefully, Python's close behind. 

Note that some of this is internet delay. And so, it might not necessarily be a crazy number of seconds. But the system is, indeed, using, if we measure it, a low level. How much time the CPU spent executing my code? C took a total of 1.64 seconds. That was pretty fast, even though it took a moment more for all of the bytes to come over the internet. The Python version, though, took what? 2.44 seconds. 

So what might the inference be? One, maybe I'm just better at programming in C than I am in Python, which is probably not true. But what else might you infer from this example? Should we, maybe, give up on Python, stick with C? No? So what might be going on here? Why is the Python version, that I claim is correct-- and I think the numbers all line up, just not the times. Where is the trade-off here? 

Well, here, again, is this design trade-off. Yeah? 

AUDIENCE: In order to save the programmer time, [INAUDIBLE]. 

DAVID MALAN: Yeah, exactly. In order to save the human programmer time, there's a lot more features built into Python-- more functions, more automatic management of memory and so forth-- and you have to pay a price. Someone else's code is doing all of that work for you. But if they've written some number of lines of code, those are just more lines of code that need to be executed for you, whereas here, the computer is at the risk of oversimplifying only running my lines of code. So there's just less overhead. And so, this is a perpetual trade-off. 

Typically, when using a more user-friendly and more modern language, one of the prices you might pay is performance. Now, there's a lot of smart computer scientists in the world, though, trying to push back on those same trade-offs. And so, these interpreters, like the command I wrote, Python technically can-- especially if you run a program again and again-- actually, secretly, behind the scenes, compile your code for you, down to 0s and 1s. And then, the second, the third, the fourth time you run that program, it might very well be faster. 

So this is a bit of a head fake here, in that I'm running them once and only once. But we could get benefit over time if we kept running the Python version again and again and, perhaps, fine-tune the performance. But, in general, there's going to be this trade-off. Now, would you rather spend the 60 seconds I wrote implementing a spell checker or this 6 hours, 16 hours you might be or have spent implementing the same in C? Probably not. For productivity's sake, this is why we have these additional languages. 

Just for fun, let me flip over to another screen here and open up a version of Python that's actually-- in just a second-- on my own Mac instead of the cloud so that I can actually do something with graphics. So, here, I just have a black and white terminal window on my very own Mac. And I've pre-installed Python, just like we've done so for VS Code in the cloud for you. 

Notice that I've got this photo of, perhaps, one of your favorite TV shows here, with the cast of The Office. Notice all of the faces in this image here. And let me propose that we try to find one face in the crowd, CSI-style, whereby we want to find, perhaps, the Scranton Strangler, so to speak. And so, here is an example of this guy's face. Now, how do we go about finding this specific face in the crowd? 

Well, our human eyes, obviously, can pluck him out, especially if you're familiar with the show. But let me go ahead and do this instead. Let me go ahead and propose that we run code that I already wrote in advance here. This is a Python program with more lines of code that we won't dwell on for today. But it's meant to motivate what we can do. From a pillow library, implying a Python image library, I want to import some type of information, some feature called image so that I can manipulate images, not unlike our own problem set four. 

And this is powerful. in? Python. You can just [MIMICS EXPLOSION] import face recognition as a library that someone else wrote. From there, I'm going to create a variable called image. I'm going to use this face recognition libraries. load_image_file function. It's a little verbose, but it's similar in spirit to fopen. And I'm going to open office.jpeg. I'm going to, then, declare a second variable called face_locations, plural, because what I'm expecting to get back, per the documentation for this library, is a list of all of the faces' locations that are detected. 

All right. Then, I'm going to iterate over each of those faces using a for loop, that we'll see in more detail. I'm going to, then, infer what the top, right, bottom, and left corners are of that face. And then, what I'm going to do here is show that face alone, if I've detected the face in question. So let me go ahead, here, and run detect.py. And we'll see not just the one face we're looking for. 

But if I run Python of detect.py, it's going to do all of the analysis. I'll see a big opening here, now, of all of the faces that were detected in this here program. [CHUCKLES] OK, some better than others, I guess, if you zoom in on catching someone. Typical Angela. If you want to, now, find that one face, I think we need to train the software a bit more. So let me actually open up a second program called recognize that's got more going on. 

But let me, with a wave of a hand, point out that I'm now loading not only the office.jpeg, but also toby.jpeg to train the algorithm to find that specific face. And so, now, if I run this second version-- recognize.py-- with Python of recognize.py-- hold my breath for just a moment; it's analyzing, presumably, all of the faces-- you see the same, original photo. 

But do you see one such face highlighted here? This version of the code found Toby, highlighted him with the screen and, voila, we have face recognition. So for better or for worse, this is what's happening, increasingly societally, nowadays. And honestly, even though I didn't write the code live-- because it's a good dozen or more lines of code-- it's not terribly many. And literally, all the authorities-- all we have to do is import face recognition and, voila, you have access. These technologies are here already. 

But let's consider, for just a moment-- how did we find Toby? How might that library-- even though we're not going to look at its implementation details, how does it find Toby and distinguish him from all of these other faces in the crowd? What might it be doing, intuitively. Think back even to p-set four, what you, yourselves, have access to, data-wise. Yeah? 

AUDIENCE: [? Since ?] we gave it an image of Toby's face before, it probably looks at are the pixels in one area the same as in another area and allots it to the same-- from that reference image to this image. And then, it's going to say, hey, a lot of the similar consult ranges are here and here, so we can safely guess that this is the same [? person. ?] 

DAVID MALAN: Yeah, exactly. And to summarize for the camera here, we have trained the software, if you will, by giving it a photo of Toby's face. So, by looking for the same or, really, similar pixels-- especially if it's a slightly different image of Toby-- we can, perhaps, identify him in the crowd. And what really is a human face? Well, at the end of the day, the computer only knows it as a pattern of bits or, really, at a higher level, a pattern of pixels. 

So maybe a human face is, perhaps, best defined, in general, as two eyes and a nose and a mouth that, even though all of us look similar, structurally, odds are, the measurement between the eyes and the nose and the width of the mouth, the skin tone and all of these other physical characteristics are patterns that software could, perhaps, detect and then look, statistically, through the image, looking for the closest possible match to these various measurement shapes, colors and sizes and the like. 

And, indeed, that might be the intuition. But what's powerful here, again, is just how easy and readily available this technology now is. All right. So with that said, let's propose to consider what more we can do with Python itself, get back to the fundamentals, so that you, yourselves can start to implement something along those same lines. So besides having access to things like a get_string function, the CS50 library provides a few other things, as well-- namely, in C, we had these. 

But in Python, we're going to have fewer. In Python, our library, short-term, is going to give you not only get_string, but also get_int and get_float. Why? It's actually just annoying, as we'll soon see, to get back an integer or a float from a user and just make sure that it's an int and a float and not a word like cat or dog, or some string that's not actually a number. 

Well, we can import not just the specific function, get_string, but we can actually import all of these functions one at a time, like this, as we'll soon see. Or you can even, in Python, import specific functions from a file. One of you asked a while back, when you include something like CS50.h or standard I/O .h, you're actually getting all of the code in that file, which, potentially, can add bulk to your own program or time. 

In this case, when you import specific functions from Python, you can be a little more narrowly precise as to what it is you want to have access to. All right. So, with that said, let's go ahead and see what conditionals look like in Python. So in the left-hand side again, here, we'll see Scratch. So it's just a contrived example asking if x is less than y, then, say, x is less than y. 

In C, it looked like this. In Python, now, it's going to look like this instead. And here's before in C, and here's after. And just to call out a few of the obvious differences, what has changed, in Python, for conditionals, it would seem? What's the difference? Yeah. 

AUDIENCE: There's a lack of curly braces. 

DAVID MALAN: Yeah. So there's no more curly braces. And, indeed, you don't use those. What appears to be taking their place, if you might infer? What seems to have taken their place? What do you think? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: So the colon at the start of this line, here. But also even more important, now, is this indentation below it. So some of you, and we know this from office hours, have a habit of indenting everything on the left, right? And it's just this crazy mess to look at. Frustrating for you, surely. But C and Clang is pretty tolerant when it comes to things like white space in a program. 

Python, uh-uh. They realized, years ago, that-- let's help humans help themselves and just require standard indentation. So four spaces would be the norm here. But because it's indented below that colon, that, indeed, indicates that this, now, is part of that condition. Something else has gone missing, versus C, in this conditional. What else is a little simplified? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah. So no more parentheses. You can still use them, especially when you need to, logically, to do order of operations, like in math. But in this case, if you just want to ask a simple question, like if x less than y, you can just do it like that. How about when you have an if else? Well, this is almost the same, here, with these same changes. In C, this looked like this. And it's starting to get a bit bulky-- at least, if we use our curly braces in this way. 

In Python, we can tighten things up further, even though, strictly speaking, in C, you don't always need the curly braces. But here, gone are the parentheses, again. Gone are the curly braces. Indentation is consistent, and we've just added another keyword, else, with the colon. But no more semicolons, as well. How about something larger, like this, in if, else, if else? This one's a little curious. 

But in C, it looked like this-- if, else, if else. In Python, it now looks like this. And there's, perhaps, one curiosity here that, honestly, all these years later, I still can't remember how to spell it half the time. What's weird about this? What do you spot as different? Yeah, over here. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah. Instead of else if, it's elif. Why? [SIGHS] Apparently, else space if was just too many keystrokes for humans to type, so they condensed it into this way. Probably means it's a little more distinguishable, too, for the computer between the if and the else, too. But just something to remember, now. It's, indeed, elif and not else if. All right. So what about variables in Python? I've used a couple of them already, but let's distill exactly how you define and declare these things, as well. 

So, in Scratch, if we wanted to create a variable called counter and set it equal, initially, to 0, we would do something like this-- specify that it's an int, use the assignment operator, end the thought with a semicolon. In Python, it's just simpler. You name the variable, use the assignment operator, as before, you set it equal to some value, and that's it. You don't mention the type. You don't mention the semicolon or anything more. 

What if you want to change a variable, like counter, by 1-- that is, incremented by 1? You have a few different ways here. In C, we saw syntax like this, where you can say counter equals counter plus 1, which, again, feels illogical. How can counter equal counter plus 1? But, again, we read this code, really, right to left, updating its value by 1. In Python, it's almost the same. You just get rid of the semicolon. So that logic is there. 

But recall, in C, we could do something slightly different that we can also do in Python. In Python, you can also, more succinctly, do this-- plus equals, and then, whatever number you want to add. Or you can even change it to subtract, if you prefer. Sadly, gone is something you've probably typed a whole lot. What was the other way you can add 1? 

AUDIENCE: Plus plus? 

DAVID MALAN: Plus plus is no more, sadly, in Python. Just too many ways to do the same thing, so they got rid of it in favor of just this syntax, here. So keep that in mind, as well. 

What about loops, when you want to do something in Python again and again. Well, in Scratch, in week zero, here's how we meowed three times, specifically. In C, we had a couple of ways of doing this. This was the more mechanical approach, where you create a variable called i. You set it equal to 0. You then do while i is less than 3, the following. And then, you, yourself increment i again and again. Mechanical in the sense that you have to implement all of these gears and make them turn yourself, but this was a correct way to do that. 

In Python, we can still achieve the same idea, but we don't need the int keyword. We don't need any of the semicolons. We don't need the parentheses. We don't need the curly braces. We can't use the plus plus, so maybe that's a minor step backwards if you're a fan. But otherwise, the code, the logic is exactly the same. But there's other ways to achieve this same idea. 

Recall that, in C, we could also do this. You could use a for loop, which does exactly the same thing. Both are correct. Both are, arguably, well-designed. It's to each their own when it comes to choosing between these. In Python, though, we're going to have to think through how to do this. So you don't do the same for loop as in C. The closest I could come up with is this, where you say for i-- or whatever variable you want to do the counting-- in-- literally the preposition-- and then, you use square brackets here. 

And we've used square brackets before, in the context of arrays and things like that. And the 0, 1, 2 looks like an array, in some sense, even though we've also seen arrays with curly braces. But these square brackets, for now, denote a list. Python does not have arrays. An array is that contiguous chunk of memory, back to back to back, that you have to resize somehow by moving things around in memory, as per two weeks ago. 

In Python, though, you can just create a list like this using square brackets. And better still, as we'll see, you can add or even remove things from that list down the road. This, though, is not going to be very well-designed. This will work. This will iterate in Python three times. But what might rub you the wrong way about this design, even if you've never seen Python before? How does this example not end well? Yeah? 

AUDIENCE: Making a large list [INAUDIBLE]. 

DAVID MALAN: Yeah. If you're making a large list, you have to type out each one of these numbers, like comma 3, comma 4, comma 5, comma, dot, dot, dot, 50 comma, dot, dot, dot, 500. Like, surely, that's not the best solution, to have all of these numbers on the screen, wrapping endlessly on the screen. So, in Python, another way to do this would be to use a function called range, which, technically, is a data type onto itself. 

And this returns to you as many values as you ask for it. range takes some other arguments, as well. But the simplest use case here is, if you want back the numbers 0, 1, and 2-- a total of three values-- you say, hey, Python, please give me a range of three values. And by default, they start at 0 on up. But this is more efficient than it would be to hard code the entire list at once. 

And the best metaphor I could come up with is something like this. Here, for instance, is a deck of cards. This is normal, human size, and there's presumably 52 cards here. So writing out 0 through 51 on code would be a little ridiculous for the reasons you know. And it would just be very unwieldy and ugly and wrapping in all of that. It would be the virtual equivalent of me handing you all of these cards at once to just deal with. 

And, right, they're not that big, but it's a lot of cards to hold on to. It requires a lot of memory or physical storage, if you will. What range does, metaphorically, is, if you ask me for three cards, I hand you them one at a time, like this, so that, at any point in time, you only have one number in the computer's memory until you're handed the next. The alternative-- the previous version would be to hand me all three cards at once, or all 52 cards at once. But in this case, range is just way more efficient. 

You can do range of 1,000. That's not going to give you a list of 1,000 values all at once. It's going to give you 1,000 values one at a time, reducing memory significantly in the computer itself. All right. So, besides this, what about doing something forever in Scratch? Well, we could do this, literally, with a forever block, which didn't quite exist in C. In C, we had to hack it together by saying while True-- because True is, by definition, T-R-U-E, always true. So this just deliberately induces an infinite loop for us. 

In Python, the logic's going to be almost the same. And infinite loops in Python tend to actually be even more common because you can always break out of them, as you could in C. In Python, it looks like this. And this is slightly more subtle, but gone are the curly braces. Gone are the parentheses. But ever so slight difference, too? A capital T for True and it's going to be a capital F for False. Stupid little differences. Eventually, you're going to mistype one or the other. But these are the kinds of things to keep an eye out and to start recognizing in your mind's eye when you read code. 

Questions, now, on any of these building blocks? Yeah? 

AUDIENCE: In the for loop, was i set to 0 once for [? every loop? ?] 

DAVID MALAN: In the for loop, was i-- it was set to 0 on the first iteration, then 1 on the next, then 2 on the third. And the same thing for range. It just doesn't use up as much memory all at once. Other questions, now, on any of these building blocks of Python? All right. Well, let's go ahead and build something a little more than hello. Let me propose that, over here, we implement, maybe, the simplest of calculators here. 

So let me go back to VS Code here, open my terminal window and open up, say, a file called calculator.py. And in calculator.py, we'll have an opportunity to explore some of these building blocks, but we'll allow things to escalate pretty quickly to more interesting examples so that we can do the same thing, ultimately, as well. And, in fact, let me go ahead and do this. Moreover, I've brought some code with me in advance. 

For instance, something called calculator0.c, from the first week of C. And let me go ahead and split my window here, in fact, so that I can now do something like this. Let me move this over here, here. Calculator.py. So now, I have, on the left of my screen, calculator.c-- or calculator0.c because that's the first version I made-- and calculator.py on the right. 

Let me go ahead and implement, really, the same idea here. So on the right-hand side, the analog of including cs50.h would be from cs50 import get_int if I want to, indeed, use this function. Now, I'm going to go ahead and give myself a variable x without defining its type. I'm going to use this get_int function and I'm going to prompt the user for x, just like in C. 

I'm, then, going to go ahead and prompt the user for another int, like y, here, just like in C. And at the very end, I'm going to go ahead and do print x plus y. And that's it. Now, granted, I have some comments in my C version of the code, just to remind you of what each line is doing. But I've still distilled this into six lines-- or, really, four if I get rid of the blank line. 

So it's already, perhaps, a bit tighter here. It's tighter because something really important, historically, is missing. What did I seem to omit altogether that we haven't really highlighted yet? Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah. The main function is gone. And in fact, maybe you took for granted that it just worked a moment ago when I wrote hello, but I didn't have a main function in hello, either. And this, too, is a feature of Python and a lot of other languages, as well. Instead of having to adhere to these long-standing traditions, if you just want to write code and get something done, fine. Just write code and get something done without, necessarily, all of this same boilerplate. 

So whatever is in your Python file-- left indented, if you will, by default-- is just going to be the code that the interpreter runs, top to bottom, left to right. Well, let me go ahead, now, and run code like this. Let me go ahead and open back up my terminal window, run python of calculator.py. And I'll do x is 1, y is 2. And as you might expect, it gives me 3. 

Slight aesthetic bug. I put my space in the wrong place here. So that's a newbie mistake. Let me fix that, aesthetically. Let me rerun python of calculator.py. Type in 1. Type in 2. And, voila, there is now my same version again. But let me propose, now, that we get rid of this training wheel. We don't want to keep taking one step forward and then two steps back by adding these training wheels, so let me instead do this. 

In my version of calculator.py, suppose that we take away, already, the training wheel that is the CS50 library here and let me, instead, then, use just Python's built-in function called input, which literally does just that. It gets input from the user and it stores it, as before, in x and y. So this is not CS50-specific. This is real-world Python programming. Well, let me go ahead and run, again, python of calculator.py. 

And, of course, if x is 1 and y is 2, x plus y should, of course, still be 3. It's apparently 12, according to Python, until CS50's library gets involved. But does anyone want to infer what just went wrong? Yeah? 

AUDIENCE: We're always [INAUDIBLE]. 

DAVID MALAN: Exactly. The input function, by design, always returns a string of text. After all, that's what the human typed in. And even though, yes, I typed the number keys on the keyboard, it's still coming back as all text. Now, maybe we should use like a get_int function. Well, that doesn't exist in Python. All you can do is get textual input-- a string from the user. But we can convert one to the other. 

And so, a fix for this so that we don't accidentally concatenate-- that is, join x plus y together-- would be to do something like this. Let me go back to my Python code, here. And whereas, in C, we could previously do typecasting-- we can convert one type to another-- that generally wasn't the case when you were doing something complex, like a string to an int. 

You could do a char to an int and vise versa. But for a string, recall, there was a special function in the C-type library called a to I, like Ascii to integer. That's the closest analog, here. And, in fact, the way to do this in Python would be to use a function called int, which, indeed, is the name of the data type, too, even though I have not yet had to type it. And I can convert the output of the input function automatically from a string immediately to an int. 

And now, if I go back to my terminal window, rerun python of calculator.py with 1 and 2 for x and y, now, I'm back in business. So that, then, is, for instance, what the CS50 library does, if temporarily this week, is it just deals with the conversion for you. And, in fact, bad things could happen if I type the wrong thing, like dog or cat instead of a number. But we'll cross that bridge in just a moment, as well. 

All right. What if we do something slightly different, now, with our calculator. Instead of addition, let's do division instead. So z equals x divided by y, thereby giving me a third variable z. Let me go ahead and run python of calculator.py again. I'll type in 1. I'll type in 3 this time. And what problem do you think we're about to see? Or is it gone? What happened when I did this in C, albeit with some slightly more cryptic syntax, when I divided one number, like 1 divided by 3? 

Anyone recall? Yeah? 

AUDIENCE: You would round to the nearest integer. 

DAVID MALAN: Yeah. So it would round down to the nearest integer, whereby you experience truncation. So if you take an integer like 1, you divide it by another integer like 3, that technically should be 0.33333, infinitely long. But in C, recall, you truncate the value. If you divide an int by an int, you get back an int, which means you get only the integer part, which was the 0. 

Now, Python actually handles this for us and avoids the truncation. But it leaves us, still, with one other problem here, which is going to be, for instance, not necessarily visible at a glance. This looks correct. This has solved the problem in C. So truncation does not happen. The integers are automatically converted to a float-- a floating point value. But what other problem did we trip over, back in week one? 

What else got a little dicey when dealing with simple arithmetic? Anyone recall? Well, the syntax in Python is a little different, but let me go ahead and do this. It turns out, in Python, if you want to see more significant digits than what I'm seeing here by default, which is a dozen or so, let me go ahead and print out z as follows. Let me first print out a format string because I want to format z in an interesting way. And notice, this would have no effect on the difference. This is just a format string that, for no compelling reason at the moment, is interpolating z in those curly braces using an fstring or format string. 

If I run this again with 1 and 3, we'll see, indeed, the exact same thing. But when you use an fstring, you, indeed, have the ability to format that string more precisely. Just like with %f in Python, you could start to fine-tune how many significant digits you see-- in C, rather. In Python, you can do the same, but the syntax is a little different. If you want the computer to interpolate z and show you 50 significant digits-- that is, 50 numbers after the decimal point-- syntax is similar to C, but it's a little different. 

You literally put a colon after the variable's name. dot 50 means show me the decimal point and, then, 50 digits to the right, and the f just indicates please treat this as a floating point value. So now, if I rerun python of calculator.py, divide 1 by 3, unfortunately, Python has not solved all of the world's problems for us. This, again, was an example of floating point imprecision. So that problem is still latent. 

So just because the world has advanced, doesn't necessarily mean that all of our problems from C have gone away. There are solutions using third-party libraries for scientific calculations and the like. But out of the box, floating point imprecision is still an issue. Meanwhile, there was one other problem in C that we ran into involving numbers, and that was this-- integer overflow. Recall that an integer in C only took up, what, 32 bits typically, which meant you could count as high as 4 billion or, maybe, if you're doing positive and negatives, as high as 2 billion, after which, weird things would happen. 

The number would go to 0 or negative or it would overflow or wrap back around. Well, wonderfully, in Python, they did, at least, address this, whereby you can count as high as you want. And Python will just use more and more and more and more bits and bytes to store really big numbers so integer overflow is not a thing. With that said, Python is limited to how many digits it will show you on the screen at once as a string. But, mathematically, your math will be correct now. 

So we've taken a couple of steps forward, one step sideways. But, indeed, we have solved some of our problems here. All right. Questions, now, on any of these examples thus far? Question? All right. Well, how about another problem that we encountered in C. Let's revisit it here in Python, as well. So let me go ahead and, on the left-hand side here, let me open up a file called, say, compare3.c on the left, and let me go ahead and create a new file on the right called compare.py. 

Because recall that bad things happened when we needed to compare two values in C. So on the left, here, is a reminder of what we once did in C, whereby, if we want to compare values, we can get an int in C, store it in x. A get_int in C, store it in y. We then have our familiar, conditional logic here, just printing out if x x less than y or not. Well, we can certainly do the same thing, ultimately, in Python by using some fairly familiar syntax. And let's just demonstrate this one quickly. 

Let me go over here, too. I'll do from cs50 import get_int, even though I could do this, instead, with the input function itself. x equals get_int, and I'll prompt the user for that. y equals get_int, and I'll prompt the user for that. After that, recall that I can say, without parentheses, if x is less than y, then print out, without the f, "x is less than y." Then, I can go ahead and say else if x is greater than y, I can print out, quote unquote, "x is greater than y." 

If you'd like to interject now, what did I screw up? Anyone? Yeah? 

AUDIENCE: Elif. 

DAVID MALAN: Elif, right? So elif x is greater than y, else-- this part's the same-- print "x is equal to y." There's no new logic going on here. But, at least syntactically, it's a little cleaner. Indeed, this program is only 11 lines long, albeit without any comments. Let me go ahead and run python of compare.py. Let's see. Is 1 less than 2? Indeed. Let's run it again. 

Is 2 less than 1? No, it's greater than. And let's, lastly, type in 1 and 1 twice. x is equal to y. So we've got a pretty side-by-side, one-to-one conversion here. Let's do something a little more interesting, then. In C, how about I open, instead, something where we actually compared for a purpose? So if I open up, from earlier in the course-- how about agree.c, which prompt the user to agree to something or not? 

And let me code up a new version here, called agree.py. And I'll do this on the right-hand side, with agree.py. But on agree.c on the left-- notice that this is how we did this yes-no thing in C-- we compared c, a character, equal to single quotes 'Y' or equal to single quotes little 'y.' And then, the same thing for n. Now, in Python, this one is actually going to be a little bit different, here. 

Let me go ahead and, in the Python version of this, let me do something like this. We'll use get_string. Actually, no. We'll just use input in this case. So let's do s equals input. And we'll ask the user the same thing-- Do you agree, question mark. Then, let's go ahead and say, if s equals equals-- how about Y? Huh. How do I do this? Well, a few things. 

Turns out, I'm going to do this-- s equals equals little y. Then, I'm going to go ahead and print out "Agreed." And elif s equals equals capital N or s equals equals lowercase n, I'm going to go ahead and print out "Not agreed." And I claim, for the moment, that this is identical, now, to the program on the left in C. But what's different? So we're still doing the same kind of logic, these equal equals for comparing for equality. 

But notice that, nicely enough, Python got rid of the two vertical bars, and it's just literally the word "or." If you recall seeing ampersand ampersand to express a logical and in C, [GRUNTS] you can just write, literally, the word "and." And so, here's a hint of why Python tends to be pretty popular. People just like that it's a little closer to English. There's a little less of the cryptic syntax here. 

Now, this is correct, as this code will now work. But I've also used double quotes instead of single quotes, and I also omitted, a few minutes ago, from my list of data types in Python the word "char." In Python, there are no chars. There are no individual characters. If you want to manipulate an individual character, you use a string-- that is to say, a str-- of size 1. 

Now, in Python, you can use single quotes or double quotes. I'm deliberately using double quotes everywhere, just for consistency with how we treat strings in C. It's pretty common, though, to use single quotes instead, if only because, on most keyboards, you don't have to hold the Shift key anymore. Humans have really started to optimize just how quickly they want to be able to code. 

So using a single quote tends to be pretty popular in Python and other languages, as well. They are fundamentally the same, single or double, unlike in C, where they have meaning. So this is correct, I claim. And, in fact, let me run this real quick. I'll open up my terminal window here. Let me get rid of the version in C and run python of agree.py. And I'll type in Y. OK. I'll run it again and type in little y. And I'll stipulate it's going to work for no, as well. 

But this isn't necessarily the only way we can do this. There are other ways to implement the same idea. And in fact, I can go about doing this instead. Let me go back up to my code here. And we saw a hint of this earlier. We know that lists exist in Python, and you can create them just by using square brackets. So what if I simplify the code a little bit and just say if s is in the following list of values-- capital Y or lowercase y. It's not all that different, logically, but it's a little tighter. It's a little more compact. 

So elif s is in capital N or lowercase n, I can express that same idea, too. So here, again, it's just getting a little more pleasant to write code. There's less hitting of the keyboard. You can express yourself a little more succinctly. And using the keyword in, Python will figure out how to search the entire list for whatever the value of s is. And if it finds it, it will return True automatically. Else, it will return False. 

So if I run agree.py again and type in capital Y or lowercase y, that still, now, works. Well, I can tighten this up further if I want to add more features. Well, what if I want to support not just big Y and little y, but how about "Yes" or "yes" or, in case the user is yelling or someone who isn't good with CapsLock types in "YES?" Wait a minute. But it could be weird. Do we want to support this or this? 

This just gets really tedious, quickly, combinatorially, if you consider all of these possible permutations. What would be smarter than doing something like this, if you want to just be able to tolerate "yes" in any form of capitalization? Logically, what would be nice? 

AUDIENCE: Maybe, whatever the input is, you just transfer it over to all lowercase while uppercase, and then redo it? 

DAVID MALAN: Exactly. Super common paradigm. Why don't we just force the user's input to all lowercase or all uppercase-- doesn't matter, so long as we're self-consistent-- and just compare against all uppercase or all lowercase. And that will get rid of all of the possible permutations, otherwise. Now, in C, we might have done something like this. We might have simplified this whole list and just said-- let's say we'll do-- how about lowercase? So y or yes, and we'll just leave it at that. 

But we need to force, now, s to lowercase. Well, in C, we would have used the C-type library. We would have done to.lower and call that function, passing it in. Although, not really because, in C-type, those operate on individual characters or chars, not whole strings. We actually didn't see a function that could convert a whole string in C to lowercase. 

But in Python, we're going to benefit from some other feature, as well. It turns out that Python supports what's called object-oriented programming. And we're only going to scratch the surface of this in CS50. But if you take a higher-level C course in programming or CS, you explore this as a different paradigm. Up until now, in C, we've been focusing on what's called, really, procedural programming. You write procedures. You write functions, top to bottom, left to right. 

And when you want to change some value, we were in the habit of using a procedure-- that is, a function. You would pass something, like a variable, into a function, like toupper or tolower, and it would do its thing and hand you back a value. Well, it turns out that it would be nicer, programming-wise, if some data types just had built-in functionality. Why do we have our variables over here and all of our helper functions, like toupper and tolower over here, such that we constantly have to pass one into the other. 

It would be nice to bake into our data type some built-in functionality so that you can change variables using their own, default built-in functionality. And so, Object-Oriented Programming, otherwise known as OOP, is a technique whereby certain types of values, like a string-- AKA str-- not only have properties inside of them-- attributes, just like a struct in C-- your data can also have functions built into them, as well. 

So, whereas in C, which is not object-oriented, you have structs. And structs can only store data, like a name and a number when implementing a person. In Python, you can, for instance, have not just a structure-- otherwise known as a class-- storing a name and a number. You can have a function call that person or email that person or actual verbs or actions associated with that piece of data. 

Now, in the context of strings, it turns out that strings come with a lot of useful functionality. And in fact, at this URL here, which is in docs.python.org, which is the official documentation for Python, you'll see a whole list of methods-- that is, functions-- that come with strings that you can actually use to modify their values. And what I mean by this is the following. If we go through the documentation, poke around, it turns out that strings come with a function called lower. 

And if you want to use that function, you just have to use slightly different syntax than in C. You do not do tolower, and you do not say, as I just did, lower because this function is built into s itself. And just like in C, when you want to go inside of a variable, like a structure, and access a piece of data inside of it, like name or number, when you also have functions built into data types-- AKA methods; a method is just a function that is built into a piece of data-- you can do s dot lower open paren, closed paren in this case. 

And I can do this down here, as well. If s.lower in, quote unquote, "n" or "no", the whole thing, I can force this whole thing to lowercase. So the only difference here, now, as an object-oriented programming, instead of constantly passing a value into a function, you just access a function that's inside of the value. It just works because of how the language itself is defined. And the only way you know whether these functions exist is the documentation-- a class, a book, a website or the like. 

Questions, now, on this technique? All right. I claim this is correct. Now, even though you've never programmed, most of you, in Python before, not super well-designed. There's an subtle inefficiency, now, on lines 3 and 5 together. What's dumb about how I've used lower, might you think? Yeah? 

AUDIENCE: I feel like, using it twice, you'd just want another [? variable. ?] 

DAVID MALAN: Yeah. If you're going to use the same function twice and ask the same question, expecting the same answer, why are you calling the function itself twice? Maybe we should just store the result in a variable. So we could do this in a couple of different ways. We, for instance, could go up here and create another variable called t and set that equal to s.lower. And then, we could just change this to be t, here. 

But honestly, I don't think we technically need another variable altogether, here. I could just do something like this. Let's change the value of s to be the lowercase version thereof. And so, now, I can quite simply refer to s again and again like this, reusing that same value. Now, to be sure, I have now just lost the user's original input. And if I care about that-- if they typed in all caps, I have no idea anymore. So maybe I do want to use a separate variable, altogether. 

But a takeaway here, too, is that strings in Python are technically what we'll call immutable-- that is, they cannot be changed. This was not true in C. Once we gave you arrays in week two or memory in week four, you could go to town on a string and change any of the characters you want-- uppercasing, lowercasing, changing it, shortening it and so forth. But in this case, this returns a copy of s, forced to lowercase. It doesn't change the original string-- that is, the bytes in the computer's memory. 

When you assign it back to s, you're essentially forgetting about the old version of s. But because Python does memory management for you-- there's no malloc, there's no free-- Python automatically frees up the original bytes, like Y-E-S, and hands them back to the operating system for you. All right. Questions, now, on this technique? Questions on this? 

In general, I'll call out-- the Python documentation will start to be your friend because, in class, we'll only scratch the surface with some of these things. But in docs.python.org, for instance, there's a whole reference of all of the built-in functions that come with the language, as well as, for instance, those with a string. All right. Before we take a break, let's go ahead and create something a little familiar too based on our weeks here, in C. Let me propose that we revisit those examples involving some meows. 

So, for instance, when we had our cat meow back in the first week and, then, second in C, we did something that was a little stupid at first whereby we created a file, as I'll do here-- this time, called meow.py. And if I want a cat to meow three times, I could run it once, like this, a little copy-paste. And now, python of meow.py, and I'm done. Now, we've visited this example two times, at least, now in Scratch and in C. 

It's correct, I'll stipulate, but what's, obviously, poorly designed? What's the fault here? Yeah? 

AUDIENCE: It should just be a loop. 

DAVID MALAN: It should just be a loop, right? Why type it three times? Literally, copying and pasting is almost always a bad thing-- except in C, when you have the function prototypes that you need to borrow. But in this case, this is just inefficient. So what could we do better here, in Python? Well, in Python, we could probably change this in a few different ways. We could borrow some of the syntax we proposed in slide form earlier, like give me a variable called i. Set it to 0, no semicolon. While i is less than 3-- if I want to do this three times-- I can go ahead and print out "meow." 

And then, I can do i plus equals 1. And I think this would do the trick. Python of meow.py, and we're back in business already. Well, if I wanted to change this to a for loop, well, in Python, it would be a little tighter, but this would not be the best approach. So for i in 0, 1, 2, I could just do print "meow", like this. And that, too, would get the job done. But, to our discussion earlier, this would get stupid pretty quickly if you had to keep enumerating all of these values. What did we introduce instead? 

The range function. Exactly. So that hands me back, way more efficiently, just the values I want, indeed, one at a time. So even this, if I run it a third or fourth time, we've got the same result. But now, let's transition to where we went with this back in the day. How can we start to modularize this? It would be nice, I claimed, if MIT had given us a meow function. Wouldn't it be nice if Python had given us a meow function? Maybe less compelling in Python, but how can I build my own function? 

Well, I did this briefly with the spell checker earlier, but let me go ahead and propose that we could implement, now, our own version of this in Python as follows. Let me go ahead and start fresh here and use the keyword def. So this did not exist in C. You had the return value, the function name, the arguments. In Python, you literally say def to define a function. You give it a name, like meow. 

And now, I'm going to go ahead and, in this function, just print out meow. And this lets me change it to anything else I want in the future. But for now, it's an abstraction. And in fact, I can move it out of sight, out of mind-- just going to hit Enter a bunch of times to pretend, now, it exists, but I don't care how it is implemented. And up here, now, I can do something like this. For i in range of 3, let me go ahead and not print "meow" anymore. Let me just call meow and tightening up my code further. 

Let's see. Python of meow.py. This is, I think, going to be the first time it does not work correctly. OK. So here, we have, sadly, our first Python error. And let's see. The syntax is going to be different from C or Clangs output. Traceback is the term of art here. This is like a trace back of all of the lines of code that were just executed or, really, functions you've called. The file name is uninteresting. This is my codespace, specifically, but the file name is important here-- meow.py. 

Our line 2 is the issue-- OK, I didn't get very far before I screwed up-- and then, there's a name error. And you'll see, in Python, there's typically these capitalized keywords that hint at what the issue is. It's something related to names of variables. "meow" is not defined. All right. You're programming Python for the first time. You've screwed up. You're following some online tutorial. You're seeing this. Reason through it. Why might "meow" not be defined? 

What can we infer about Python? How to troubleshoot, logically? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Maybe. Is it because "meow" is defined after? As smart as Python seems to be, vis-a-vis C, they have some similar design characteristics. So let's try that. So let me scroll all the way back down to where I moved this earlier. Let me get rid of it-- way down there. I'll copy it to my clipboard. And let me just hack something together. Let me just put it up here. And let's see if this works. So now, let me clear my terminal, run python of meow.py. 

OK. We're back in business. So that was actually really good intuition. Good debugging technique, just reason through it. Now, this is contradicting what I claimed back in week one, which was that the main part of your program, ideally, should just be at the top of the file. Don't make me look for it. It's not a huge deal with a four-line program, but if you've got 40 lines or 400 lines, you don't want the juicy part of your program to be way down here, and all of these functions way up here. 

So it would be nice, maybe, if we actually have a main function. And so, it actually turns out to be a convention in Python to define a main function. It's not a special function that's automatically called, like in C. But humans realized, you know what? That was a pretty useful feature. Let me define a function called main. Let me indent these lines underneath it. Let me practice what I'm preaching, which is put the main code at the top of the file. And, wonderfully, in Python, now, you do not need prototypes. 

There's none of that hackish copying and pasting of the return type, the name and the arguments to a function, like we needed in C. This is now OK instead, except for one, minor detail. Let me go ahead and run python of meow.py. Hopefully, now, I've solved this problem by having [GROANS] a main function. 

But now, nothing has happened. All right. Even if you've never programmed in Python before, what might explain this behavior, and how do I fix? Again, when you're off in the real world, learning some new language, all you have is deductive logic to debug. Yeah? 

AUDIENCE: I remember in C, even though we [INAUDIBLE]. 

DAVID MALAN: Right. So the solution, to be clear, in C was that we had to put the prototype up here. Otherwise, we'd get an error message. In this case, I'm actually not getting an error message. And, indeed, I'll claim that you don't need the prototypes in Python. Just not necessary because that was annoying, if nothing else. But what else might explain? Yeah, in the back? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah. Maybe you have to call main itself. If main is not some special status in Python, maybe just because it exists isn't enough. And, indeed, if you want to call main, the new convention is actually going to be-- as the very last line of your program, typically-- to literally call main. It's a little stupid-looking, but they made a design decision. And this is how, now, we work around it. Python of meow.py. Now we're back in business. 

But now, logically, why does this work the way it does? Well, in this case-- top to bottom-- line 1 is telling Python to define a function called main and, then, define it as follows, lines 2 and 3. But it's not calling main yet. Line 6 is telling Python how to define a function called meow, but it's not calling these lines yet. Now, on line 10, you're telling Python, call main. And at that point, Python has been trained, if you will, to know what main is on line 1, to know what meow is on line 6. 

And so, it's now perfectly OK for main to be above meow because you never called them yet. You defined, defined, and then, you called. And that's the logic behind this. Any questions, now, on the structure of this technique, here? Now, let's do one more, then. Recall that the last thing we did in Scratch and in C was to, actually, parameterize these same functions. 

So suppose that you don't want main to be responsible for the loop here. You instead want to, very simply, do something like "meow" three times and be done with it. Well, in Python, it's going to be similar in spirit to C. But, again, we don't need to keep mentioning data types. If you want "meow" to take some argument-- like a number n-- you can just specify n as the name of that argument. Or you can call it anything else, of course, that you want. You don't have to specify int or anything else. 

In your code, now, inside of meow, you can do something like for i in, let's say-- I definitely, now, can't do this because that would be weird, to start the list and end it with n. So, if I can come back over here, what's the solution? How can I do something n times? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah. Using range. So range is nice because I can pass in, now, this variable n. And now, I can meow-- whoops. Now i can print out, quote unquote, "meow." So it's almost the same as in Scratch, almost the same as in C. But it's a little simpler. And if, now, I run meow.py, I'll have the ability, now, to do this here, as well. All right. Questions on any of this? Right now, we're taking this stroll through week one. We're going to, momentarily, escalate things to look not only at some of these basics, but also, other features, like we saw with face recognition with the speller or the like. 

Because of how many of us are here, we have a huge amount of candy out in the lobby. So why don't we go ahead and take a 10-minute break? And when we come back, we'll do even fancier, more powerful things with Python in 10. 

All right. So we are back. Among our goals, now, are to introduce a few more building blocks so that we can solve more interesting problems at the end, much like those that we began with. You'll recall, from a few weeks ago, we played with this two-dimensional Super Mario world. And we tried to print a vertical column of three or more bricks. Well, let me propose that we use this as an opportunity to, now, tinker with some of Python's more useful, more user-friendly functionality, as well. 

So let me code a file called mario.py, and let's just print out the equivalent of that vertical column. So it's of height 3. Each one is a hash, so let's do for i in range of 3 initially, and let's just print out a single hash. And I think, now, python of mario.py-- voila. We're in business, printing out just that same column there. What if, though, we want to print a column of some variable height where the user tells us how tall they want it to be? 

Well, let me go up here, for instance and, instead, how about-- let's do this. How about from cs50 import? How about the get_int function, as before? So it will deal with making sure the user gives us an integer. And now, in the past, whenever we wanted to get a number from a user, we've actually followed a certain paradigm. In fact, if I open up here, for instance, how about mario1.c from a while back, you might recall that we had code like this. And we specifically use the do while loop in C whenever we want to get something from the user, maybe, again and again and again, until they cooperate. At which point, we finally break out of the loop. 

So it turns out, Python does have while loops, does have for loops, does not have do while loops. And yet, pretty much any time you've gotten user input, you've probably used this paradigm. So it turns out that the Python equivalent of this is to do, similar in spirit, but using only a while loop. And a common paradigm in Python, as I alluded earlier, is to actually deliberately induce an infinite loop while True-- capital T-- and then, do what you want to do, like get an int from the user and prompt them for the height, for instance, in question. 

And then, if you're sure that the user has given you what you want-- like n is greater than 0, which is what I want, in this case, because I want a positive integer; otherwise, there's nothing to print-- you literally just break out of the loop. And so, we could actually use this technique in C. It's just not really done in C. You could absolutely, in C, have done a while True loop with the parentheses, lowercase true. You could break out of it, and so forth. 

But in Python, this is the Python way. And this is actually a term of art. This way in Python is pythonic This is "the way everyone does it," quote unquote. Doesn't mean you have to, but that's the way the cool Python programmers would implement an idea like this-- trying to do something again and again and again until the user actually cooperates. But all we've done is take away the do while loop. But still, logically, we can implement the same idea. 

Now, below this, let me go ahead and just print out, for i in range of n this time-- because I want it to be variable and not 3. I can go ahead and print out the hash-- let me go ahead and get rid of the C version here-- open my terminal window and I'll run, again, Python of mario.py. I'll type in 3 and I get back those three hashes. But if I, instead, type in 4, I now get four hashes instead. 

So the takeaway here is, quite simply, that this would be the way, for instance, to actually get back a value in Python that is consistent with some parameter, like greater than 0. How about this? Let's actually practice what we preached a moment ago with our meowing examples and factoring all this out. Let me go ahead and define a main function, as before. Let me go ahead and assume, for the moment, that a get_height function exists, which is not a thing in Python. I'm going to invent it in just a moment. 

And now, I'm going to go ahead and do something like this. for i in the range of that height, well, let's go ahead and print out those hashes. So I'm assuming that get_height exists. Let me go ahead and implement that abstraction, so define a function, now, called get_height. It's not going to take any arguments in this design. While True, I can go ahead and do the same thing as before-- assign a variable n, the return value of get_int prompting the user for that height. 

And then, if n is greater than 0, I can go ahead and break. But if I break here, I, logically-- just like in C-- end up executing below the loop in question. But there's nothing there. But if I want get_height to return the height, what should I type here on line 14, logically? What do I want to return, to be clear? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah. So I actually want to return n. And here's another curiosity of Python, vis-a-vis C. There doesn't seem to be an issue of scope anymore, right? In C, it was super important to not only declare your variables with the data types, you also had to be mindful of where they exist-- inside of those curly braces. In Python, it turns out you can be a little looser with things, for better or for worse. 

And so, on line 11, if I create a variable called n, it exists on line 11, 12 and even 13, outside of the while loop. So to be clear, in C, with a while loop, we would have ordinarily had not a colon. We would have had the curly brace, like here and over here. And a week ago, I would have claimed that, in C, n does not exist outside of the while loop, by nature of those curly braces. 

Even though the curly braces are gone, Python actually allows you to use a variable any time after you have assigned it a value. So slightly more powerful, as such. However, I can tighten this up a little bit, logically. And this is true in C. I don't really need to break out of the loop by using break. Recall that or know that I can actually-- once I'm ready to go, I can just return the value I care about, even inside of the loop. And that will have the side effect of breaking me out of the loop and, also, breaking me out of and returning from the entire function. 

So nothing too new here, in terms of C versus Python, except for this issue with scope. And I, indeed, returned n at the bottom there, just to make clear that n would still exist. So either of those are correct. Now, I just have a Python program that I think is going to allow me to implement this same Mario idea. So let's run python of mario.py. And-- OK, so nothing happened. Python of mario.py. What did I do wrong? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, I have to call main. So, at the bottom of my code, I have to call main here. And this is a stylistic detail that's been subtle. Generally speaking, when you are writing in Python, there's not a CS50 style guide, per se. There's actually a Python style guide that most people adhere to. And in this case, double blank lines between functions is the norm. I'm doing that deliberately, although it might, otherwise, not be obvious. 

But now that I've called main on line 16, let's run mario.py once more. Aha. Now we see it. Type in 3, and I'm back in business, printing out the values there. Yeah? 

AUDIENCE: Why do you [INAUDIBLE]? Why can't [INAUDIBLE]? 

DAVID MALAN: Sure. Why do I need the if condition at all? Why can't I just return n here as by doing return n. Or if I really want to be succinct, I could technically just do this. The only reason I added the if condition is because, if the user types in negative 1, negative 2, I wanted to prompt them again and again. That's all. But that would be totally acceptable, too, if you were OK with that result instead. 

Well, let me do one other thing here to point out why we are using get_int so frequently. This new training wheel, albeit temporarily. So let me go back to the way it was a moment ago and let me propose, now, to take away get_int. I claimed earlier that, if you're not using get_int, you can just use the input function itself from Python. But that always returns a string, or a str. And so, recall that you have to pass the output of the input function to an int, either on the same line or, if you prefer, on another line, instead. 

But it turns out what I didn't do was show you what happens if you don't cooperate with the program. So if I run python of mario.py now, works great, even without the get_int function. And I can do it with 4. Still works great. But let me clear my terminal and be difficult, now, as the user and type in "cat" for the height instead. Enter. Now, we see one of those trace backs again. 

This one is different. This isn't a name error, but, apparently, a value error. And if I ignore the stuff I don't understand, I can see "invalid literal for int with base 10-- "cat."" That's a super cryptic way of saying that C-A-T is not a number in decimal notation. And so, I would seem to have to, somehow, handle this case. And if you want to be more curious, you'll see that this is, indeed, a traceback. 

And C tends to do this, too, or the debugger would do this for you, too. You can see all of the functions that have been called to get you to this point. So apparently, my problem is, initially, in line 14. But line 14, if I keep scrolling, is uninteresting. It's main. But line 14 leads me to execute line 2, which is, indeed, in main. That leads me to execute line 9, which is in get_height. 

And so, OK, here is the issue. So the closest line number to the error message is the one that probably reveals the most. Line 9 is where my issue is. So I can't just blindly ask the user for input and, then, convert it to an int if they're not going to give me an int. Now, how do we deal with this? Well, back in problem set two, you might recall validating that the user typed in a number and using a for loop and the like. 

Well, it turns out, there's a better way to do this in Python, and the semantics are there. If you want to try to convert something to a number that might not actually be a number, turns out, Python and certain other languages literally have a keyword called try. And if only this existed for the past few weeks, I know. But you can try to do the following with your code. What do I want to try to do? 

Well, I want to try to execute those few lines, except if there's an error. So I can say except if there's a value error-- specifically, the one I screwed up and created a moment ago. And if there is a value error, I can print out an informative message to the user, like "not an integer" or anything else. And what's happening here, now, is literally this operative word, try. 

Python is going to try to get input and try to convert it to an int, and it's going to try to check if it's greater than 0 and then try to return it. Why? Three of those lines are inside of, indented underneath the try block, except if something goes wrong-- specifically, a value error happens. Then, it prints this. But it doesn't return anything. And because I'm in a loop, that means it's going to do it again and again and again until the human actually cooperates and gives me an actual number. 

And so, this, too, is what the world would call pythonic. In Python, you don't, necessarily, rigorously try to validate the user's input, make sure they haven't screwed up. You honestly take a more lackadaisical approach and just try to do something, but catch an error if it happens. So catch is also a term of art, even though it's not a keyword here. Except if something happens, you handle it. 

So you try and you handle it. You best-effort programming, if you will. But this is baked into the mindset of the Python programming community. So now, if I do python of mario.py and I cooperate, works great as before. Try and succeed. 3 works. 4 works. If, though, I try and fail by typing in "cat," it doesn't crash, per se. It doesn't show me an error. It shows me something more user-friendly, like "not an integer." And then, I can try again with "dog." "Not an integer." I can try again with 5. And now, it works. 

So we won't, generally, have you write much in the way of these try-except blocks, only because they get a little sophisticated quickly. But that is to reveal what the get_int function is doing. This is why we give you the training wheels, so that, when you want to get an int, you don't have to jump through all these annoying hoops to do so. But that's all the library's really doing for you, is just try and except. 

You won't be left with any training wheels, ultimately. Questions, now, on getting input and trying in this way? Anything at all? Yeah? 

AUDIENCE: I'm still [INAUDIBLE] try block. 

DAVID MALAN: Oh, could you put the condition outside of the try block? Short answer, yes. And, in fact, I struggled with this last night when tweaking this example to show the simplest version. I will disclaim that, really, I should only be trying, literally, to do the fragile part. And then, down here, I should be really doing what you're proposing, which is do the condition out here. 

The problem is, though, that, logically, this gets messy quickly, right? Because except if there's a value error, I want to print out "not an integer." I can't compare n against 0, then, because n doesn't exist because there was an error. So it turns out-- and I'll show you this; this is now the advanced version of Python-- there's actually an else keyword you can use in Python that does not accompany if or elif. It accompanies try and except, which I think is weirdly confusing. A different word would have been better. 

But if you'd really prefer, I could have done this, instead. And this is one of these design things where reasonable people will disagree. Generally speaking, you should only try to do the one line that might very well fail. But honestly, this looks stupid. No, it's just unnecessarily complicated. And so, my own preference was actually the original, which was-- yeah, I'm trying a few extra lines that, really, aren't going to fail, mathematically. But it's just tighter. It's cleaner this way. 

And here's, again, the sort of arguments you'll start to make yourself as you get more comfortable with programming. You'll have an opinion. You'll disagree with someone. And so long as you can back you argument up, it's pretty reasonable, probably. All right. So how about we, now, take away some piece of magic that's been here for a while. Let me go ahead and delete all of this here. And let me propose that we revisit not that vertical column and the exceptions that might result from getting input, but these horizontal question marks that we saw a while ago. 

So I want all of those question marks on the same line. And yet, I worry we're about to see a challenge here because print, up until now, has been putting new lines everywhere automatically, even without those backslash n's. Well, let me propose that we do this. for i in the range of 4. If I want four question marks, let me just print four question marks. Unfortunately, I don't think this is correct yet. Let me run python of mario.py. And, of course, this gives me a column instead of the row of question marks that I want. 

So how do we do this? Well, it turns out, if you read the documentation for the print function, it turns out that print, not surprisingly, perhaps, takes a lot of different arguments, as well. And in fact, if you go to the documentation for it, you'll see that it takes not just positional arguments-- that is, from left to right, separated by commas. It turns out, Python has supports a fancier feature with arguments where you can pass the names of arguments to functions, too. 

So what do I mean by this? If I go back to VS Code here and I've read the documentation, it turns out that, yes, as before, you can pass multiple arguments to Python, like this. Hello comma David comma Nalan, that will just automatically concatenate all three of those positional arguments together. They're positional in the sense that they literally flow from left to right, separated by commas. 

But if you don't want to just pass in values like that, you want to actually print out, as I did before, a question mark. But you want to override the default behavior of print by changing the line ending, you can actually do this. You can use the name of an argument that you know exists from the documentation and set it equal to some alternative value. And in fact, even though this looks cryptic, this is how I would override the end of each line, to be quote, unquote. 

That is nothing because, if you read the documentation, the default value for this end argument-- does someone want to guess-- is-- is backslash n. So if you read the documentation, you'll se that backslash n is the implied default for this end argument. And so, if you want to change it, you just say end equals something else. And so, here, I can change it to nothing and, now, rerun python of mario.py. And now, they're all in the same line. 

Now, it looks a little stupid because I made that week one mistake where I still need to move the cursor to the next line. That's just a different problem. I'm just going to go over here and print nothing. I don't even need to print backslash n because, if print automatically gives you a backslash n, just call print with nothing, and you'll get that for free. So let me rerun python of mario.py. And now, it looks a little prettier at the prompt. 

And to be super clear as to what's going on-- suppose I want to make an exclamation here. I could change the backslash n default to an exclamation point, just for kicks. And if I run python of mario.py Again, now, I get this exclamation with question marks and exclamation points, as well. So that's all that's going on here. And this is what's called a named argument. It literally has a name that you can specify when calling it in. And it's different from positional in that you're literally using the name. 

Let me propose something else, though. And this is why people like Python. There's just cool ways to do things. That's a three-line, verbose way of printing out four question marks. I could certainly take the shortcut and just do this. But that's not really that interesting for anyone, especially if I want to do it a variable number of times. But Python does let you do this. 

If you want to multiply a character some number of times, not only can you use plus for concatenation, you can use star or an asterisk for multiplication, if you will-- that is, concatenation again and again and again. So if I just print out, quote unquote, "?" times 4, that's actually going to be the tightest way, the most distinct way I can print four question marks instead. And if I don't use 4, I use n, where I get n from the user. Bang. 

Now, I've gotten rid of the for loop entirely, and I'm using the star operator to manipulate it instead. And, to be super clear here, insofar as Python does not have malloc or free or memory management that you have to do, guess what Python also doesn't have. Anything on your minds in the past couple of week? Doesn't have-- 

AUDIENCE: Pointers. 

DAVID MALAN: Pointers, yeah. So Python does not have pointers, which just means that all of that happens for you automatically, underneath the hood, again, by way of code that someone else wrote. 

How about one more throwback with Mario? We've talked about, in week one, this two-dimensional structure where it's like I claim 3 by 3-- a grid of bricks, if you will. Well, how can we do this in Python? We can do this in a couple of ways, now. Let me go back to my mario.py, and let me do something like for i in range of-- we'll just do 3, even though I know, now, I could use get_int or I could use input and int. 

And if I want to do something two-dimensionally, just like in C, you can nest your for loops. So maybe I could do for j in range of 3. And then, in here, I could print out a hash symbol. And then, let's see if that gives me 9 total. So if I've got a nested loop like this, python of mario.py hopefully gives me a grid. No, it gave me a column of 9. Why, logically, even though I've got my row and my columns? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, the line ending. So in my row, I can't let print just keep adding new line, adding new line. So I just have to override this here and let me not screw up like before. Let me print one at the end of the whole row, just to move the cursor down. And I think, now, together, we've got our 3 by 3. Of course, we could tighten this up further. If I don't like the nested loop, I probably could go in here and just print out, for instance, a brick times 3. Or I could change the 3 to a variable if I've gotten it from the user. 

So I can tighten this up further. So, again, just different ways to solve the same problem and, again, evidence of why a lot of people like Python. There's just some more pleasant ways to solve problems without getting into the weeds, constantly, of doing things, like with for loops and while loops endlessly. All right. Well, how about some other building blocks? 

Lists are going to be so incredibly useful in Python, just as arrays were in C. But arrays are annoying because you have to manage the memory yourself. You have to in advance how big they are or you have to use pointers and malloc or realloc to resize them. Oh my god. The past two weeks have been painful, in that sense. But Python does this all for free for you. In fact, there's a whole bunch of functions that come with Python that involve lists, and they'll allow us, ultimately, to do things again and again and again within the same data structure. 

And, for instance, we'll be able to get the length of a list. You don't have to remember it yourself in a variable. You can just ask Python how many elements are in this list. And with this, I think we can solve some old problems, too. So let me go back here, to VS Code. Let me close mario and give us a new program called scores.py. And rather than show the C and the Python now, let's just focus on Python. 

And in scores.c way back when, we just averaged three test scores or something like that-- 72, 73, and 33-- a few weeks ago. So if I want to create a list in this Python version of 72, 73, 33, I just use my square bracket notation. C let you use curly braces if you know the values in advance, but Python's just this. And now, if I want to compute the average-- in C, recall, I did something with a loop. I added all the values together. I, then, divide it by the total number of values just like you would in grade school, and that gave me the average. 

Well, Python comes with a lot of super handy functions-- not just length, but others, as well. And so, in fact, if you want to compute the average, you can take the sum of all of those scores and divide it by the length of all of those scores. So Python comes with length, comes with sum. You can just pass in a whole list of any size and let it deal with that problem for you. So if I want to, now, print out this average, I can print out Average colon-- and then, I'll plug in my average variable for interpolation. Let me make this an fstring so that it gets formatted, and let me just run python of scores.py. 

And there is my average. It's rounding weird because we're still vulnerable to some floating point imprecision, but at least I didn't need loops and I didn't have to write all this darn code just to do something that Excel and Google Spreadsheets can just do like that. Well, Python is closer to those kinds of tools, but more powerful in that you can manipulate the data yourself. How about, though, if I want to get a bunch of scores manually from the user and, then, sum them together. Well, let's combine a few ideas here. How about this? 

First, let me go ahead and import the get_int function from the CS50 library, just so we don't have to deal with try and except or all of that. And let me go ahead and give myself an empty list. And this is powerful. In C, [SIGHS] there's no point to an empty array because, if you create an empty array with square bracket notation, it's not useful for anything. But in Python, you can create it empty because Python will grow and shrink the list for you automatically, as you add things to it. 

So if I want to get three scores from the user, I could do something like this-- for i in range of 3. And then, I can grab a variable called "score" or anything. I could call get_int, prompt the human for the score that they want to type in. And then, once they do, I can do this. Thinking back to our object-oriented programming capability now, I could do scores.append, and I can append that score to it. 

And you would only know this from having read the documentation, heard it in class, in a book or whatnot, but it turns out that, just like strings have functions like lower built into them, lists have functions like append built into them that just literally appends to the end of the list for you, and Python will grow or shrink it as needed. No more malloc or realloc or the like. 

So this just appends to the scores list. That score, and then again and again and again. So the array starts at-- sorry, the list starts at size 0, then grows to 1 then 2 then 3 without you having to do anything else. And so, now, down here, I can compute an average with the sum of those scores divided by the length of the total number of scores. And to be clear, length is the total number of elements in the list. Doesn't matter how big the values themselves are. 

Now I can go ahead and print out an fstring with something like Average colon average in curly braces. And if I run python of scores.py-- I'll type in, just for the sake of discussion, the three values, I still get the same answer. But that would have been painful to do in C unless you committed, in advance, to a fixed size array-- which we already decided, weeks ago, was annoying-- or you grew it dynamically using malloc or realloc or the like. 

All right. What else can I do? Well, there's some nice things you might as well know exist. Instead of scores.append, you can do slight fanciness like this. If you want to append something to a list, you can actually do plus equals, and then put that thing in a temporary list of its own and just use what is essentially concatenation-- but not concatenation of strings, but concatenation of lists. So this new line 6 appends to the score's list-- this tiny, little list I'm temporarily creating with just the current new score. 

So just another piece of syntax that's worth seeing that allows you to do something like that, as well. All right. Well, how about we go back to strings for a moment? And all of these examples, as always, are on the course's website afterward. Suppose we want to do something like converting characters to uppercase. Well, to be clear, I could do something like this. Let me create a program called uppercase.py. 

Let me prompt the user for a before string as by using the input function or get_string, which is almost the same. And I'll prompt the user for a string beforehand. Then, let me go ahead and print out, how about, the keyword "After," and then end the new line with nothing, just so that I can see "Before" on one line and "After" on the next line. And then, let me do this-- and here's where Python gets pleasant, too, with loops-- for c in before-- print c.upper end equals quote, unquote. And then, I'll print this here. 

All right. That was fast, but let's try to infer what's going on. So line 1 just gets input from the user, stores it in a variable called before. Line two literally just prints "After" but doesn't move the cursor to the next line. What it, then, does is this. And, in C, this was a little more annoying. You needed a for loop with i. You needed array notation with the square brackets. But, Python, if you say for variable in string-- so for c, for character, in string, Python is going to automatically assign c to the first letter that the user types in. 

Then, on the next iteration, the second letter, the third letter, and the fourth. So you don't need any square bracket notation, you just use c, and Python will do it for you and just hand you back, one at a time, each of the letters that the user has typed in. So if I go back over here and I run, for instance, python of uppercase.py and I'll type in, how about, "david" in all lowercase and hit Enter, you'll now see that it's all uppercase instead by iterating over it, indeed, one character at a time. 

But we already know, thanks to object-oriented programming, strings themselves have the functionality built in to not just uppercase single characters, but the whole string. So, honestly, this was a bit of a silly exercise. I don't need to use a loop anymore, like in C. And so, some of the habits you've only just developed in recent weeks, it's time to start breaking them when they're not necessary. 

I can create a variable called after, set it equal to before.upper-- which, indeed, exists, just like dot lower exists. And then, what I can go ahead and print out is, for instance-- let's get rid of this print line here and do it at the end-- "After" and print the value of that variable. So now, if I rerun uppercase.py, type in "david" in all lowercase, I can just uppercase the whole thing all at once because, again, in Python, you don't have to operate on characters individually. 

Questions on any of these tricks up until now? No? All right. How about a few other techniques that we saw in C that we'll bring back, now, in Python. So it turns out, in Python, there are other libraries you can use, too, that unlock even more functionality. So, in C, if you wanted command line arguments, you just change the signature for main to be, instead of void, int argc comma string argv, open brackets for an array or char star, eventually. 

Well, it turns out, in Python, that, if you want to access command line arguments, it's a little simpler, but they're tucked away in a library-- otherwise known as a module-- called sys, the system module. Now, this is similar, in spirit, to the CS50 library, and that's got a bunch of functionality built in. But this one comes with Python itself. So if I want tot create a program like greet.py, in VS Code, here, let me go ahead and do this. 

From the sys library, let's import argv. And that's just a thing that exists. It's not built into main because there is no main, per se, anymore. So it's tucked away in that library. And now, I can do something like this. If the length of argv equals equals 2, well, let's go ahead and print out something friendly, like hello comma argv bracket 1, and then, close quotes. Else, if the length of argv is not equal to 2, Let's just go ahead and print out hello, world. 

Now, at a glance, this might look a little cryptic, but it's identical to what we did a few weeks ago. When I run this, python of greet.py, with no arguments, it just says "hello, world." But if I, instead, add a command line argument, like my first name and hit Enter, now, the length of argv is no longer 1. It's going to be 2. And so, it prints out "Hello, David" instead. 

So the takeaway here is that, whereas in C, argv technically contained the name of your program, like ./hello or ./greet, and then everything the human typed. Python's a little different in that, because we're using the interpreter in this way-- technically, when you run python of greet.py, the length of argv is only 1. It contains only greet.py, so the name of the file. It does not unnecessarily contain Python itself because what's the point of that being there, omnipresently? 

It does contain the number of words that the human typed after Python itself. So argv is length 1 here. argv is length 2 here. And that's why, when it did equal 2, I saw "Hello, David" instead of the default "Hello, world." So same ability to access command line arguments, add these kinds of inputs to your functions, but you have to unlock it by way of using argv instead, in this way. 

If you want to see all of the words, you could do something like this. Just as-- if we combine ideas, here-- for i in range of, how about, length of argv. Then, I can do this-- print argv bracket i. All right. A little cryptic, but line 3 is just a for loop iterating over the range of length of argv. So if the human types in two words, the length of argv will be 2. So this is just a way of saying iterate over all of the words in argv, printing them one at a time. 

So python of greet.py, Enter just prints out the name of the program. python of greet.py with David prints out greet.py and, then, David. I can keep running it though with more words, and they'll each get printed one at a time. But what's nice, too, about Python-- and this is the point of this exercise-- honestly, this looks pretty cryptic. This is not very pleasant to look at. If you just want to iterate over every word in a list, which argv is, watch what I can do. 

I can do for arg or any variable name in argv. Let me just, now, print out that argument. I could keep calling it i, but i seems weird when it's not a number. So I'm changing to arg as a word, instead. If I now do python of greet.py, it does this. If I do python of greet.py, David, it does that again. David Malan, it does that again. So this is, again, why Python is just very appealing. You want to do something this many times, iterate over a list? Just say it, and it reads a little more like English. And there's even other fanciness, too, if I may. 

It's a little stupid that I keep seeing the name of the program, greet.py, so it'd be nice if I could remove that. Python also supports what are called slices of arrays-- sorry, slices of lists. Even I get the terminology confused. If argv is a list, then it's going to print out everything in it. But if I want a slice of it that starts at location 1 all the way to the end, you can use this funky syntax in between the square brackets, which we've not seen yet, that's going to start at item 1 and go all the way to the end. 

And so, this is a nice, clever way of slicing off, if you will, the very first element because now, when I run greet.py, David Malan, I should only see David and Malan. If I only want one element, I could do 1 to 2. If I want all of them, I could do 0 onward. I could give myself just one of them in this way. So you can play with the start value and the end value in this way, to slice and dice these lists in different ways. 

That would have been a pain in C, just because we didn't really have the built-in support for manipulating arrays as cleanly as this. All right. Just so you've seen it, too-- though, this one is less exciting to see live-- if I go ahead and create a quick program here, it turns out, there's something else in the sys library, the ability to exit programs-- either exiting with status code 1 or 0, as we've been doing any time something goes right or wrong. 

So, for instance, let me whip up a quick program that just says, if the length of sys.argv does not equal 2, then let's yell at the user and say you're missing a command line argument. Otherwise, command-line argument. And let's, then, return sys.exit(1). Else, let's go ahead and, logically, just say print a formatted string that says hello-- as before-- sys.argv 1. Now, things look different all of a sudden, but I'm doing something deliberately. 

First, let's see what this does. So, on line 1, I'm importing not argv, specifically. I'm importing the whole sys library, and we'll see why in a second. Well, it turns out that the sys library has not only the argv list, it also has a function called exit, which I'd like to be able to use, as well. So it turns out that, if you import a whole library in this way, that's fine. But you have to refer to the things inside of it by using that same library's name and a dot to namespace it, so to speak. 

So here, I'm just saying, if the user does not type in two words, yell at them with missing command line argument, and then, exit with 1. Just like in C, when you do exit 1, just means something went wrong. Otherwise, print out hello to this. And this is starting to look cryptic, but it's just a combination of ideas. The curly braces means interpolate this value, plug it in here. sys.argv is just the verbose way of saying go into the sys library and get the argv variable therein. And bracket 1, of course, just like arrays in C, is just the second element at the prompt. 

So when I run this version, now-- python of exit.py-- with no arguments, I get yelled at in this way. If, however, I type in two arguments total-- the name of the file and my own name-- now, I get greeted with hello, David. And it's the same idea before. This was a very low-level technique, but same thing here. If you do echo dollar sign question mark Enter, you'll see the exit code of your program. 

So if I do this incorrectly again-- let me rerun it without my name, Enter-- I get yelled at. But if I do echo dollar sign question mark, there's the secret one that's returned. Again, just to show you parity with C, in this case. Questions, now, on any of these techniques, here? No. All right. How about something that's a little more powerful, too? We spend so much time in week 0 and 1 doing searching and, then, eventually, sorting in week 3. Well, it turns out, Python can help with some of this, too. 

Let me go ahead and create a program called names.py that's just going to be an opportunity to, maybe, search over a whole bunch of names. Let me go ahead and import sys, just so I have access to exit. And let me go ahead and create a variable called names that's going to be a list with a whole bunch of names. How about here? Charlie and Fred and George and Ginny and Percy and, lastly, Ron. So a whole bunch of names here. 

And it'd be a little annoying to implement code that iterates over that, from left to right, in C, searching for one of those names. In fact, what name? Well, let's go ahead and ask the user to input the name that they want to search for so that we can tell them if the name is there or not. And we could do this, similar to C, in Python, doing something like this. So for n in names, where n is just a variable to iterate over each name-- if the name I'm looking for equals the current name in the list-- AKA n-- well, let's print out something friendly, like "Found." And then, let's do sys.exit 0 to indicate that we found whoever that is. 

Otherwise, if we get all the way to the bottom here, outside of this loop, let's just print "Not found" because if we haven't exited yet. And then, let's just exit with 1. Just to be clear, I can continue importing all of sys, or I could do from sys import exit, and then, I could get rid of sys dot everywhere else. But sometimes, it's helpful to know exactly where functions came from. So this, too, is just a matter of style, in this case. All right. So let's go ahead and run this. 

python of names.py, and let's look for Ron, all the way at the end. All right. He's found. And let's search for someone outside of the family here, like Hermione. Not found. OK. So it seems to be working in this way. But I've essentially implemented what algorithm? What algorithm would this seem to be, per line 7 and 8 to 9 and 10? 

AUDIENCE: Linear. 

DAVID MALAN: Yeah. So it's just linear search. It's a loop, even thought he syntax is a little more succinct today, and it's just iterating over the whole thing. Well, honestly, we've seen an even more terse way to do this in Python. And this, again, is what makes it a more pleasant language, sometimes. Why don't I just do this? Instead of iterating one at a time, why don't I just say this? Let me go ahead and change my condition to just be-- how about if the name we're looking for is in the names list, we're done. We found it. 

Use the end preposition that we've seen a couple of times, now, that itself asks the question, is something in something else? And Python will take care of linear search for us. And it's going to work exactly the same if I do python of names.py, search for Ron. It's still going to find him and it's still going to do it linearly, in this case. But I don't have to write all of the lower-level code myself, in this case. Questions, now, on any of this? The code's just getting shorter and shorter. No? What about-- let's see. What else might we have here? 

How about this? Let's go ahead and implement that phonebook that we started, metaphorically, with in the beginning of the course. Let's code up a program called phonebook.py. And in this case, let's go ahead and let's create a dictionary this time. Recall that a dictionary is a little something that implements something like this-- a two-column table that's got keys and values, words and definitions, names and numbers. And let's focus on the last of those, names and numbers, in this case. 

Well, I claimed earlier that Python has built-in support for dictionaries-- dict objects-- that you can create with one line. I didn't need it for speller because a set is sufficient when you only want one of the keys or the values, not both. But now, I want some names and numbers. So it turns out, in Python, you can create an empty dictionary by saying dict open parenthesis, closed. And that just gives you, essentially, a chart that looks like this, with nothing in it. 

Or there's more succinct syntax. You can, alternatively, do this, with two curly braces, instead. And, in fact, I've been using a shortcut all this time. When I had a list, earlier, where my variable was called scores, and I did this, that was actually the shorthand version of this-- hey, Python, give me an empty list. So there's different syntax for achieving the same goal. In this case, if I want a dictionary for people, I can either do this or, more commonly, just two curly braces, like that. 

All right. Well, what do I want to put in this? Well, let me actually put some things in this. And I'm going to just move my closed curly brace to a new line. If I want to implement this idea of keys and values, the way you do this in Python is key colon value comma. Key colon value. So you'd implement it more in code. So, for instance, if I want Carter to be the first key in my phone book and I want his number to be +1-617-495-1000, I can put that as the corresponding value. 

The colon is in between. Both are strings, or strs, so I've quoted both deliberately. If I want to add myself, I can put a comma. And then, just to keep things pretty, I'm moving the cursor to the next line. But that's not strictly required, aesthetically. It's just good style. And here, I might do +1-949-468-2750. And now, I have a dictionary that, essentially, has two rows, here-- Carter and his number and David and his number, as well. And if I kept adding to this, this chart would just get longer and longer. 

Suppose I want to search for one of our numbers. Well, let's prompt the user for the name, for whose number you want to search by getting string. Or you know what? We don't need this CS50 library. Let's just use input and prompt the user for a name. And now, we can use this super terse syntax and just say if name in people, print the formatted string number colon and-- here, we can do this-- people bracket name. 

OK. So this is getting cool quickly, confusingly. So let me run this. python of phonebook.py Let's type in Carter. And, indeed, I see his number. Let's run it again with David, and I see my number here. So what's going on? Well, it turns out that a dictionary is very similar, in spirit, to a list. It's actually very similar, in spirit, to an array in C. But instead of being limited to keys that are numbers, like bracket 0, bracket 1, bracket 2, you can actually use words. And that's all I'm doing here on line 8. 

If I want to check for the name Carter, which is currently in this variable called name, I can index into my people dictionary using not a number, but using, literally, a string-- the name Carter or David or anything else. To make this clearer, too, notice that I'm, at the moment, using this format string, which is adding some undue complexity. But I could clarify this, perhaps, further as this. 

I could give myself another variable called number, set it equal to the people dictionary, indexing into it using the current name. And now, I can shorten this to make it clearer that all I'm doing is printing the value of that. And, in fact, I can do this even more cryptically. This would be weird to do, but if I only ever want to show David's phone number and never Carter's, I can literally, quote unquote, "index into" the people dictionary because, now, when I run this, even if I type Carter, I'm going to get back my number instead. 

But that's all that's happening if I undo that, because that's now a bug. But I index into it using the value of name. Dictionaries are just so wonderfully convenient because, now, you can associate anything with anything else but not using numbers, but entire key words, instead. So here's how, if, in speller, we gave you not just words, but hundreds of thousands of definitions, as well, you could essentially store them as this. And then, when the human wants to look up a definition in a proper dictionary, not just for spell checking, you could index into the dictionary using square brackets and get back the definition in English, as well. 

Questions on this? Yeah? 

AUDIENCE: Is the way this code does, as presented, saying that Python has [INAUDIBLE]? 

DAVID MALAN: A really good question. So, to summarize, how is Python finding that name within that dictionary? This is where, honestly, speller in p-set 5 is what Python's all about. So you have struggled, are struggling with implementing your own spell checker and implementing your own hash table. And recall that, per last week, the goal of a hash table is to, ideally, get constant time access. Not something linear, which is slow and even better than something logarithmic, like log base 2 of n. 

So Python and the really smart people who invented it, they have written the code that does its best to give you constant time searches of dictionaries. And they're not always going to succeed, just as you and your own problem set are probably going to have some collisions once in a while and start to have chains of length lists of words. But this is where, again, you defer to someone else, someone smarter than you, someone with more time than you to solve these problems for you. 

And if you read Python's documentation, you'll see that it doesn't guarantee constant time, but it's going to, ideally, optimize the data structure for you to get as fast as possible. And of all of the data structures like a dictionary, a hash table is, really, like the Swiss army knife of computing because it just lets you associate something with something else. And even though we keep focusing on names and numbers, that's a really powerful thing because it's more powerful than lists and arrays, which are only numbers and something else. Now, you can have any sorts of relationships, instead. 

All right. Let me show a few other examples before we culminate with some more powerful techniques in Python, thanks to libraries. How about this problem we encountered in week 4, which was this. Let me code up a program called, again, compare.py here but, this time, compare to strings and not numbers. So let me, for instance, get one string from the user called s. 

Just for the sake of discussion, let me get another string from the user called t so that we can actually do some comparison here. And if s equals equals t, let's go ahead and print out that they're the same. Else, let's go ahead and print out that they're different. So this is very similar to what we did in week 4. But in week 4, recall we did this specifically because we had encountered a problem. 

For instance, if I run-- whoops. If I run-- what's going on? [INAUDIBLE] Come on. Oh. OK. Wow, OK. Long day. All right. If I run the proper command, python of compare.py, then let's go ahead and type in something like "cat" in all lowercase, "cat" in all lowercase. And they're the same. If, though, I do this again with "dog" and "dog," they're the same. And, of course, "cat" and "dog," they're different. But does anyone recall, from two weeks ago, when I typed in my name twice, both identically capitalized. 

What did it say? That they were, in fact, different. And why was that? Why were two strings in C different, even though I typed literally the same thing? Two different places in memory. So each string might look the same, aesthetically, but, of course, was stored elsewhere in memory. And yet, Python appears to be using the equality operator-- equals equals-- like you and I would expect, as humans-- actually comparing for us char by char in each of those strings for actual [? quality. ?] 

So this is a feature of Python, in that it's just easier to do. And why? Well, this derives from the reality that, in Python, there are no pointers anymore. There's no underlying memory management. It's not up to you, now, to worry about those lower-level details. The language itself takes care of that for you. And so, similarly, if I do this and don't ask the user for two strings, but just one, and then, I do something like this. How about give myself a second variable t, set it equal to s.capitalize, which, note, is not the same as upper; capitalize, by design, per Python's documentation, will only capitalize the first letter for you-- I can now print out, say, two fstrings here-- what the value of s is and, then, let me print out, with another fstring, what the value of t is. 

And recall that, in C, this was a problem because if you capitalize s and store it in t, we accidentally capitalized both s and t. But in this case, in Python, when I actually run this and type in "cat" In all lowercase, the original s is unchanged because, when I use capitalize on line 3, this is, indeed, capitalizing s. But it's returning a copy of the result. It cannot change s itself because, again, for that technical term, s is immutable. Strings, once they exist, cannot be changed themselves. But you can return copies and modify mutated copies of those same strings. 

So, in short, all of those headaches we encountered in week 4 are now solved, really, in the way you might expect. And here's another one that we dwelled on in week 4, with the colored liquid in glasses. Let me code up a program called swap.py. And in swap.py, let me set x equal to 1, y equal to 2. And then, let me just print out an fstring here. So how about x is this comma y is that. And then, let me do that twice, just for the sake of demonstration. 

And in here, recall that we had to create a swap function. But then, we had to pass it in by reference with the ampersand. And oh my god, that was peak complexity in C. Well, if you want to swap x and y in Python, you could do x comma y equals y comma x. And now, python of swap.py. And there we go. All of that's handled for you. It's like a shell game without even a temporary variable in mind. 

So what more can we do here? How about a few final building blocks? And these related, now, to files from that week 4. Suppose that I want to save some names and numbers in a CSV file-- Comma Separated Values, which is like a very lightweight spreadsheet. Well, first, let me create a phonebook.csv file that just has name comma number as the first row there. 

But after that, I'm going to go ahead, now, and code up a phonebook.py program that actually allows me to add things to this phonebook. So let me split my screen here so that we can see the old and the new. And down here, in my code for phonebook.py, in this new and improved version, I'm going to actually import a whole other library, this one called CSV. And here, too, especially for people in data science and the like, really like being able to manipulate files and data that might very well be stored in spreadsheets or CSVs-- Comma Separated Values, which we saw briefly in week 4. 

In phonebook.py, then, it suffices to just import CSV after reading the documentation therefore because this is going to give me functionality in code related to CSV files. So here's how I might open a file in Python. I literally call open-- it's not fopen now; it's just open-- and I open this file called phonebook.csv. And just as in C, I'm going to open it in append mode-- not right, where it would change the whole thing. I want to append new line at a time. 

After this, I want to get, maybe, a name from the user. So let's prompt the user for some input for their name. And then, let's prompt the user for a number, as well, using input prompting for number. All right. And now, this is a little cryptic, and you'd only know this from the documentation. But if you want to write rows to a CSV file that you can, then, view in Excel or the like, you can do this-- give me a variable called writer-- but I could call it anything I want. 

Let me use a csv.writer function that comes with this CSV library, passing in the file. This is like saying, hey, Python, treat this open file as a CSV file so that things are separated with commas and nicely formatted in rows and columns. Now, I'm going to do this-- use that writer to write a row. Well, what do I want to write? I want to write a short list-- namely, the current name and the current number-- to that file, but I don't want to use fprintf and %s and all of that stuff that we might have had in the past. And now, I just want to close the file. 

Let me reopen my terminal. Let me run python of phonebook.py, and let me type in David and then +1-949-468-2750 and, crossing my fingers, watching the actual CSV at top-left. My code has just added me to the file. And if I were to run it again, for instance, with Carter and +1-617-495-1000, crossing my fingers again-- we've updated the file. And it turns out, there's code now, via which I can even read that file. But I can, first, tighten this up, just so you've seen it. 

It turns out, in Python, it's so common to open files and close them. Humans make mistakes, and they often forget to close files, which might, then, end up using more memory than you intend. So you can, alternatively, do this in Python so that you don't have to worry about closing files. You can use this keyword instead. You can say with the opening of this file as a variable called file do all of the following underneath. 

So I'm indenting most of my code. I'm using this new, Python-specific keyword called width. And this is just a matter of saying, with the following opening of the file, do those next four lines of code, and then, automatically close it for me at the end of the indentation. It's a minor optimization, but this, again, is the pythonic way to do things, instead. How else might I do this, too? 

Well, it turns out that the code I've written here-- on line 9, especially-- is a little fragile. If any human opens this spreadsheet-- the CSV file in Excel, Google Spreadsheets, Apple Numbers-- and maybe moves the columns around just because, maybe, they're fussing. They saved it, and they don't realize they've, now, changed my assumptions. I don't want to, necessarily, write name and number always in that order because what if someone screws up and flips those two columns by literally dragging and dropping? 

So it turns out that, instead of using a list here, we can use another feature of this library, as follows. Instead of using a writer, there's something called a dictionary writer or dict writer that takes the same argument as input-- the file that's opened. But now, the one difference here is that you need to tell this dictionary writer that your field names are name and number. And let me close the CSV here. 

Name and number are the names of the fields, the columns in this CSV file. And when it comes time to write a new row, the syntax here is going to be a little uglier, but it's just a dictionary. The name I want to write to the dictionary is going to be whatever name the human typed in. The number that I want to write to the CSV file is going to be whatever the number the human typed in. But what's different, now, about this code is, by simply using a dictionary writer here instead of the generic writer, now, the columns can be in this order or this order or any order. 

And the dictionary writer is going to figure out, based on the first line of text in that CSV, where to put name, where to put number. So if you flip them, no big deal. It's going to notice, oh, wait, the columns changed. And it's going to insert the columns correctly. So just, again, another more powerful feature that lets you focus on real work, as opposed to actually getting tied up in the weeds of writing code like this, otherwise. 

Questions on this one, as well? But what we will do, now, is come full circle to some of the more sophisticated examples with which we began, and I'm going to go back over to my own Mac laptop here, where I've got my own terminal window up and running, and I was just going to introduce a couple of final libraries that really speak to just how powerful Python can be and how quickly you can get up and running. 

To be fair, can't necessarily do all of these things in the cloud, like in code spaces, because you need access to your own speakers or microphone or the like. So that's why I'm doing it on my own Mac, here. But let me go ahead and open up a program called speech.py. And I'm not using VS Code here. I'm using a program called VI that's entirely terminal window based. But it's going to allow me, for instance, to import the Python text to speech version 3 library. 

I'm going to give myself a variable called engine that's going to be set equal to the Python text to speech 3 libraries init method, which is just going to initialize this library that relates to text to speech. I'm going to, then, use the engine's say function to say something like, how about, hello comma world. And then, as my last line, I'm going to say engine.runAndWait, capitalized as such, to tell my program, now, to run that speech and wait until it's done. 

All right. I'm going to save this file. I'm going to run python of speech.py. And I'm going to cross my fingers, as always, and-- 

INTERPRETER: Hello, world. 

DAVID MALAN: All right. So now, I have a program that's actually synthesizing speech using a library like this. How can I, now, modify this to be a little more interesting? Well, how about this? Let me go ahead and prompt the user for their name, like we've done several times here, using Python's built-in name function. And now, let me go ahead and use a format string in conjunction with this library, interpolating the value of name there. 

And-- at least, if my name is somewhat phonetically pronounceable-- let's go ahead and run python of speech.py, type in my name, and-- 

INTERPRETER: Hello, David. 

DAVID MALAN: OK. It's a weird choice of inflection, but we're starting to synthesize voice, not unlike Siri or Google Assistant or Alexa or the like. Now, we can, maybe, do something a little more advanced, too. In addition to synthesizing speech in this way, we could synthesize, for instance, an actual graphic. Let me go ahead, now, and do something like this. Let me create a program called qr.py. 

I'm going to go ahead and import a library called OS, which gives you access to operating system related functionality in Python. I'm going to import a library I've pre-installed called qrcode, which is a two-dimensional barcode that you might have seen in the real world. I'm going to go ahead and create an image variable using this qrcode library's make function, which, per its documentation, takes a URL, like one of CS50's own videos. 

So we'll do this with youtu.be/xvF2joSPgG0. So, hopefully, that's the right lecture. And now, we've got img.save, which is going to allow me to create a file called qr.ping. Think back, now, on problem set 4 and how painful it was to save files. We'll just use the save function, now, in Python and save this as a PNG file-- Portable Network Graphic. 

And then, lastly, let's just go ahead and open with the command open qr.png on my Mac so that, hopefully, this just automatically opens. All right. I'm going to go ahead and just double-check my syntax here so that I haven't made any mistakes. I'm going to go ahead and run python of qr.py. Enter. That opens up this. Let me go ahead and zoom in. If you've got a phone handy and you'd like to scan this code here, whether in person or online-- I apologize. You won't appreciate it. 

Amazing! OK. And, lastly, let me go back into our speech example here, create a final ending here in our final moments. And how about we just say something like "This was CS50," like this. Let's go ahead, here. Fix my capitalization, just for tidiness. Let's get rid of the name. And now, with our final flourish and your introduction to Python equipped-- here we go-- 

INTERPRETER: This was CS50. 

DAVID MALAN: All right. We'll see you next time. 

[APPLAUSE] 

[MUSIC PLAYING] 
