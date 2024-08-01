---
title: LECTURE2 - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DAVID MALAN: All right. This is CS50, and this is week 2 wherein we're going to take a look at a lower level at how things work, and indeed, among the goals of the course is this bottom-up understanding so that in a couple of weeks' time, even a few years' time, when you encounter some new technology, you'll be able to think back hopefully on some of this week's and this is basic building blocks and primitives and really just deduce how tomorrow's technologies work. 

But along the way, it's going to seem-- it's going to be a little hard, perhaps, to see the forest for the trees, so to speak. And so the goal at the end of the day still is going to be problem-solving. And so we thought we'd begin today with a look at some of the problems we'll talk about or solve this coming week, and for that, we have some brave volunteers who have already come up. If we could turn on some dramatic lighting and meet today's volunteers. 

So on my left here, we have-- 

ALEX: Hi. My name is Alex. I'm a first-year at the college and I'm from Chapel Hill, North Carolina. 

DAVID MALAN: Welcome to Alex. And to Alex's right. 

SARAH: I'm Sarah. I'm from Toronto, Canada, and I'm also a first-year student at the college. 

DAVID MALAN: Wonderful. Well, welcome to both Alex and Sarah. So one of the problems you'll perhaps solve this week for problem set 2 is to analyze the reading level of a body of text, whether someone reads at a first grade level, second grade level, third grade level, all the way up to 12 or 13 or beyond. 

What you perhaps never quite thought about, certainly in terms of code, like how you would analyze some text, some book and figure out what reading level is it at. And yet, surely our teachers growing up knew or had an intuitive sense of this. So let's consider some sample text. For instance, Alex, what have you been reading lately? 

ALEX: One fish, two fish, red fish, blue fish. 

DAVID MALAN: Wonderful. So given that, what grade level would you say Alex is currently reading at? Feel free to just shout it out. First, first? So indeed, you'll see this week, if you run your code on Alex's text, it actually turns out he reads below a first grade reading level. But why might that be? What might your intuition be for why we've accused Alex of reading at this level? Feel free to shout out. 

Yeah. So very few syllables, short words, short sentences. And so there's some heuristics, perhaps, we can infer from that short text, that that probably means that it's best for younger children. Now Sarah, by contrast, what have you been reading? 

SARAH: Mr. And Mrs. Dursley of Number. Four Privet Drive were proud to say that they were perfectly normal, thank you very much. They were the last people you'd expect to be involved in anything strange or mysterious because they just didn't hold with much nonsense. 

DAVID MALAN: All right. Now irrespective of what grade you were in when you might have read that text, what grade level to Sarah seemed to be reading at? So eighth grade, second grade. OK. So hearing a bit of everything, so with that, at least according to code, it would actually be seventh grade. And what might the intuition there be? Why is that a higher grade level even though we might disagree exactly which grade it is? 

AUDIENCE: Complicated sentences. 

DAVID MALAN: Yeah. So complicated sentences, longer sentences. So indeed a lot more words were being spoken by Sarah because there was so much more there on the page. So we'll translate these ideas this coming week in problem set 2, if you tackle this one, through code so that you can ultimately infer things of these quantitatively. But to do so, we're going to have to understand text. So let's first thank our volunteers and then we'll dive in to that lower level. 

[APPLAUSE] 

Sorry. You can keep those. 

SARAH: Oh, OK. 

DAVID MALAN: All right. So besides that, let's consider one other body of text perhaps that you might see this week, which is namely a little something like this. What I have here on the screen is what we'll start calling today ciphertext. It's the result of encrypting some piece of information. And encryption, or more generally, the art and science of cryptography is all around us. It's what you're using on the web, on your phones, with your banks. And anything that tries to keep data secure is using encryption. 

But there's going to be different levels of encryption-- strong encryption, weak encryption. And what you see here on the screen isn't all that strong, but we'll see later today how we might decrypt this and actually reveal what the plaintext is that corresponds to that ciphertext. 

But in order to do so, we have to start taking off some training wheels, so to speak. And believe it or not, even though your time would see this past week for the first time, probably, might have been rather in the weeds. And much more complicated seemingly than C, it turns out that along the way, we have been providing and we'll continue to provide certain training wheels. For instance, the CS50 Library is one of them, and even some of the explanations we give of topics for now in these early weeks will be somewhat simplified-- abstracted away, if you will. 

But the goal ultimately is for you to understand each and every one of those details so that after CS50, you really can stand on your own and understand and wrap your mind around any future technologies as well. 

So let's consider first the very first program with which we began last week, which was this one. So "hello, world" in C. At the end of the day, it was really the printf function that was doing the interesting part of the work, but there was a lot of technical stuff above and below it. The curly braces, the parentheses, words like void and include, and then of course, the angled brackets and more. 

But at the end of the day, we needed to convert that source code in C to machine code, the 0's and 1's in binary that the computer understood. And to do that, of course, we ran-- we compiled the code. We ran make and then we were able to actually run that code there. So let me actually go over here to VS Code and really quickly recreate that hello.c pretty much by transcribing the same. 

So I might have here include stdio.h, int main void. And then in here, I had quite simply, hello, comma, world with my backslash, endquotes, and more. Now last time, to compile this, I indeed ran make hello, followed by Enter. Hopefully you see no errors and that's a good thing. And if you do dot, slash, hello, you see, in fact, the results of that program. 

But it turns out that make is not actually a compiler as I alluded to last week. It's a program that clearly makes your program, but it itself just automates the process of using an actual compiler. And there's lots of different compilers out there, and the one that it's actually using underneath the hood is a little something called Clang for C Language. 

And Clang is a pretty popular compiler nowadays. There's another one that's been around for ages called GCC, but these are just specific names for types of compilers that different people, different companies, different groups have actually created. But if you use in week 1 a compiler yourself manually, you have to understand a little more about what's going on because it's even more cryptic than what just make alone. 

So in fact, let me go back to my terminal window here, let me go ahead and clear the screen a little bit and just run really the raw compiler command. So what make is automating for me let me, actually do this manually for just a moment. So if I want to compile hello.c into an executable program I can run, I can do this. clang, space, hello.c, and then Enter. 

And now there's no output, which is a good thing in this case, no errors, but notice this. If I go ahead and type ls, it turns out there's a file that's been created suddenly in my current folder weirdly called a.out. That stands for Assembler Output. And long story short, that's actually the default name of a program that's created when you just run Clang by itself. 

Now that's a pretty bad name for a program because it doesn't describe what it does. So better would be here to perhaps do, well, instead of a.out, which, yes, still prints hello.world, but isn't really a clearly-named program, it'd be nice to name this hello. So what could I do? I could do like we learned last week-- well, I could rename a.out to hello by using Linux's mv command. So I'm going to move a.out to become hello. But that, too, seems kind of tedious. 

Now I have three steps. Like write my code, compile my code, and then rename it before I can even run it. We can do better than that. And so it turns out that certain commands like clang support what we're going to start today calling command line arguments. A command line argument, unlike an argument to a function, is just an additional word or key phrase that you type after a command at your prompt in your terminal window that just modifies the behavior of that command. It configures it a little more specifically. 

So what you're seeing here on the screen is some of a better command with which to run clang so that now I can specify the output of this command per this o. So do what I mean by that? 

Well, let me go ahead and clear my terminal window again and more explicitly type clang -o hello hello.c and then Enter. Nothing, again, appears to happen, but that's a good thing when you see no errors and now the program I just created is indeed called Hello. So it achieves really the same exact effect as make did, but what. I don't have to do with make is type and remember something as long as this command. And this, too, is a bit of a white lie. 

It turns out, we have preconfigured VS Code in the cloud for you to also use some other features of Clang that would be even more tedious for you to write yourselves. And so really, this is why we distill this as ultimately just running make. So let me pause here to see first if there's any questions on what I've done by taking my very first program in C and just now compiling it first with make, but then starting over and now manually compiling it with clang with what we'll call command line arguments. -o, space, hello, and then the name of the file. Yeah? 

AUDIENCE: What is a.out? 

DAVID MALAN: Yeah. So a.out is a historical name. It refers to assembler output-- more on that soon. And it's just the default file name that you get automatically if you just run the compiler on any file so that you have just a standard name for it. But it's not a very well-named program. Instead of running Microsoft Word on your Mac or PC, it would be like double-clicking on a.out. So instead with these command line arguments, you can customize the output of Clang and call it hello or anything you want. Other questions on what I've done here with Clang itself, the compiler? Yeah? 

AUDIENCE: What is -o? 

DAVID MALAN: So -o-- and you would only know this from reading the manual, taking a class, means output. So -o means change Clang's output to be a file called hello instead of the default, which is a.out. And this, too, is, again, a detail you would have to look up on a web page, read the manual, hear someone like me tell you about it. And in fact, there's even more than these options, but we'll just scratch the surface here. 

All right. So if we now know this, what more is actually happening underneath the hood? Well, let's take a closer look at not just this version of my code, but my slightly more complicated version last week, which looked a little something like this, wherein I added in some dynamic input from the user so I could say not hello, world to everyone, but hello, David or hello to whoever actually runs this program. 

So in fact, let me go ahead and change my code here in VS Code just to match that same code from last week. So no new code yet. I'm just going to, in a moment, compile it in a slightly different way. So I did last week's string, I think, answer equals string, quote-unquote, "What's your name?" Just like in Scratch. 

And then down here, instead of doing world, I initially wrote answer, but that didn't go well. What did I ultimately do instead to print out hello, David or hello, so-and-so? Yeah? Sorry, a little louder? 

AUDIENCE: %s? 

DAVID MALAN: Yeah, so %s, the so-called format code that printf just knows how to deal with. And I had to add one other thing. Someone else besides %s-- yeah? 

AUDIENCE: The name of the variable. 

DAVID MALAN: The name of the variable that I want to plug into that placeholder %s. And in this case, it's answer. Now let me make one refinement only because now we're in week 2 and we're going to start writing more lines of code, even though Scratch called the return value of the ask puzzle piece, answer always. 

And see, we have full control over what our variables are called. And now it's probably good not to just generically always call my variable answer if I'm using get_string. Let's call it what it is. So this is now just a matter of style, if you will. Let me change the variable to be name just so that it's a little clearer to me, to you, to a TF or TA exactly what that variable represents instead of more generically answer. 

All right, so that said, let me go down to my terminal window, and last week again, I ran make to compile this exact same program. Now, though, let me go ahead and just use clang. So clang -o-- I'll still call this version hello-- space, hello.c. So exact same command as before. The only thing that's different is I've added a couple of more lines of code to get the user's input. 

Let me hit Enter, and now, darn it, our first error. So output from clang and make is not a good thing, and here, we're seeing something particularly cryptic. So something in function 'main--' undefined reference to 'get_string,' string and then linker command failed with exit code 1. 

So there's actually a lot of jargon in there that will tease apart today, but my hint is that clearly my problem's in main, although that's not surprising because there's nothing else going on here. get_string is an issue, and the issue is that it's an undefined reference. 

And yet, notice, I was pretty good. I added the CS50 header file and I said last week that that's enough to teach the compiler that functions exist, but the problem is that even though this does, in fact, teach Clang that get_string exists, it is not sufficient information for Clang to go find on the hard drive of the computer the 0's and 1's that actually implement get_string itself. 

So in other words, this include line, per last week, is a little bit of a hint. It's a teaser to Clang that you're about to see and use this function somewhere. But if you actually want to use the 0's and 1's that CS50 wrote some time ago and bake those into your program so your program actually knows how to get input from the user, well then, I'm going to have to go ahead and run a slightly different command. 

So let me do this. Let me clear my terminal window just get rid of that distraction and let me propose now that we run this command instead. Almost the same as before, clang -o, space, hello, then hello.c, but with one additional command line argument at the end, and this is a -l-- not a number 1. So -lcs with no space in between those two. 

Now the l is going to result in all of those 0's and 1's that actually were in by CS50 being linked into your code, your few lines of code or mine here. But that's the second step that the compiler requires in order to know how to actually execute and rather compile your code and CS50's. 

And CS50 is not the only one that does this. If you use any third party library in C that doesn't come with the language, you would do -l such and such where whoever-- however they've named their own library. But you don't have to do it for built in things like we've been using thus far. 

All right, so let me go ahead and try this. I'll go back to VS Code here, and let me go ahead now and run clang -o hello, then hello.c. And now instead of just hitting Enter, -lcs50 with no space between the l and the cs50, Enter. Now nothing bad happens, and now I can do ./hello. What's your name? I'll type in David, Enter, and now we see hello, David. 

Now honestly, this is where we're really getting into the weeds, and now this is taking-- this is really just adding nuisance to the process of compiling and running your code. And so the reality is, even though this is indeed what is happening, this is why we used last week and we're going to continue using this week onward make because it just automates that whole process for you. 

But it's ideal to understand what's going wrong because any of the error messages you saw for problem set 1, any of the error messages you see for the next few weeks probably aren't coming from make, they're coming from Clang underneath the hood because make is just automating the process. 

But with make, you literally just write make and then the name of the program, you don't have to worry about any of those command line arguments. Questions, then, on compiling with dash -lcs50 or anything else? Yeah? 

AUDIENCE: What is the benefit of [INAUDIBLE]? 

DAVID MALAN: Sorry, what is the benefit of-- 

AUDIENCE: Using Clang manually. 

DAVID MALAN: What is the benefit of using Clang manually? None, really. In fact, all main is doing is just say-- make is doing is saving us some keystrokes. If you prefer, though, and you just like to be more in control, you can totally run Clang manually if you remember the various command line arguments. Yeah? 

AUDIENCE: So why did you have to explain [INAUDIBLE] 

DAVID MALAN: Exactly. Why did I have to explain-- that is, provide a hint to CS50 with the cs50.h header file, but I didn't have to do that with standardio.h? Just because. standardio.h comes with C, just like a few other libraries come with C that we'll start seeing today. CS50, though, is not built into C everywhere, and so you do have to explicitly add that one there. Yeah? 

AUDIENCE: Can you define what command line argument [INAUDIBLE]? 

DAVID MALAN: A command line argument is a word or phrase that you type at the command line-- a.k.a., your terminal-- in order to influence the behavior of a program. 

AUDIENCE: OK. So it's a term for whatever you're giving it. 

DAVID MALAN: Yeah. It changes the defaults. In our GUI world, Graphical User Interface, you and I would probably click some boxes, we would select some menu options to configure a program to behave in the same way. At a command line interface, you have to just say everything all at once, and that's why we have command line arguments. Yeah? 

AUDIENCE: Is make [INAUDIBLE] 

DAVID MALAN: No. Make is not just for CS50. It's used globally in any project really nowadays using C, C++, even other languages as well. In fact, most every command you see in this class, unless it has 5-0 at the end of it, is globally used. Only those-- a suffix with 50 are, indeed, course-specific. And even those we'll gradually take training wheels off of so that exactly what those commands are doing as well. 

All right, so what is it that we've just done? Everything we've just done, of course, I keep calling compiling, but let's just go down one rabbit hole so that you understand that when you compile code, there's actually a whole bunch of steps, happening and this is going to enable a lot of features, like companies can write code and then convert it to run it on Macs and PCs alike or phones or the like. 

So it's not just a matter of converting source code to machine code, there's actually four steps involved in what you and I, as of last week, know as compiling. 

And these aren't terms that you'll have to keep in mind constantly because again, we're going to abstract a lot of this away. But just so we've gone down the rabbit hole once, let's consider each of these four steps that have been happening for you for a week automatically, the first of which is called preprocessing. So what does this mean? 

Well, let's consider that same program as before. So notice that two of the lines of code start with a hash mark. That is a special symbol in C, and it's a so-called preprocessor directive. You don't need to memorize terms like that, but it just means that it's a little different from every other line. And anything with a hash symbol here should be preprocessed-- that is, analyzed initially before anything else happens. 

So let's consider these two lines up top, what exactly is happening. Well, it turns out with these two lines, you have two header files, of course, cs50.h and stdio.h. Where are those files, because they've never been in VS Code for you, seemingly. If you type LS-- if you open up the File Explorer in the GUI, you have never seen, probably, cs50.h or stdio.h. 

They just work, but that's because there's a folder somewhere on the hard drive that you're using on your Mac or PC or somewhere in the cloud, as in our case. And inside of this folder, traditionally called /usr/include. And user is deliberately misspelled. It's just slightly more succinct, although it's a little weird why we drop that one letter. But usr/include is just a folder on the server that contains cs50.h, stdio.h, and a bunch of other things as well. 

So in fact, if you type in VS Code, in your terminal window, when you're using code spaces in the cloud and type LS space /usr/include, you can see all of the files in that folder. But we've preinstalled all of that stuff for you. So let's consider what's actually in those files here. 

If I highlight these two lines up top that start with hash include, well, I kind of hinted last week that what's in that first file is a hint as to what functions CS50 wrote for you. So you can kind of think of these include lines as being temporary placeholders for what's going to become like a global find and replace. That is the first thing clang is going to do is to preprocess this file. 

It's going to look for any line that starts with hash include. And if it sees that, it's going to essentially go into that file, like cs50.h, and then just copy and paste the contents of that file magically there for you. You don't see it visually on the screen. But it's happening behind the scenes. 

And so really, what's happening with this first line is that somewhere in cs50.h is the declaration of getString like we talked last week, and it probably looks a little something like this. And we didn't spend much time on this yet this past week, but we will in time more. Notice that this is how a function is declared. That is, it is decreed to exist. 

The name of the function, of course, is getString. Inside of the parentheses are its arguments. In this case, there's one argument to getString, I claim today, but you've known this implicitly. And it's a prompt. It's the prompt that the human sees when you use getString. 

What is that prompt? Well, it's a string of text, like quote unquote, "what's your name?" or anything else that I asked last week. Meanwhile, getString, as we know from last week, has a return value. It returns something to you. And that, too, is a string. 

So again, this is also called a functions prototype. It's the thing toward the end of last week that I just copied and pasted from the bottom of my file to the top, just so that it was like this teaser for clang as to what would exist later. So you can think, then, of these include lines as just kind of combining all of those function declarations in some separate file called cs50.h, so that you yourself don't have to type them every time you use the library-- or worse, so that you, yourself, don't have to copy and paste those lines. This is what clang is doing for you in its first step of preprocessing. 

Second, and last in this example, what happens when clang preprocesses this second include line? Well, the only other function we care about in this story is printf, of course, which comes with C. So essentially, you can think of printf's prototype or declaration as just being this. 

Printf is the name of the function. It takes a string that you want to format like, Hello comma world, or Hello comma %s. And then with dot, dot, dot, this actually has technical meaning. It means, of course, that you can plug-in 0 variables, 1 variable, 2 or 10. So dot, dot, dot means some number of variables. 

Now we haven't talked about this yet. And we won't really, in general. printf actually returns a value, a number, that is an integer. But more on that perhaps another time. It's generally not something the programmer tends to look at. 

But that's all we mean by preprocessing, so that at the end of this process, even though there's more lines of code in cs50.h and stdio.h, what's really just happening is that clang, in preprocessing the file, copies and pastes the contents of those files into your code so that now your code knows about everything-- getString, printf, and anything else. Any questions, then, on that first step, preprocessing? Yes? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Good question. When you include a file, does it only include what you need or does it include everything? Think of it as including everything. So if it's a big file, that's a lot of code at the very top. And that's why, if you think back to all of the zeros and ones I showed a little bit ago, as well as last week, there's a lot of zeros and ones that end up on the screen as a result of just writing, Hello, world. A lot of those zeros and ones are perhaps coming from code that you didn't actually, necessarily need. But some of it is perhaps there, but there are ways to optimize that as well. 

All right, so step two of compiling is, confusingly, called compiling. It's just, this is the term that most everyone uses to describe the whole process, instead of just this one step. But once a program has been preprocessed behind the scenes by the compiler for you, it looks now a little something like this. 

And I've put dot, dot, dot just to imply that, yes, to your question, there's more stuff above it. There's more stuff below it. It's just not interesting right now for us. 

So now we have just C code. There's no more preprocessor directives. At this point, all of the hash symbols and those lines of code have been preprocessed and converted to something else. 

And so now-- and this is where things get a little spooky looking. Here now is what happens when clang, or any compiler, literally compiles code like this. It converts it from this in C to this in assembly code. So this is among the scarier languages. I, myself, don't really have fond memories. 

This is not a language that many people program in. If you take a subsequent class in computer science, in systems, a higher level class, you might actually learn this or some variant thereof. But there's at least a few people out there that need to know this stuff because this is closer to what the computers themselves, nowadays, understand. The Intel CPUs or the AMD CPUs, the brains of today's computers and phones understand stuff that looks more like this and less like C. 

Now it's completely esoteric, but let me just highlight a few phrases. There's some stuff that's a little familiar. There is mention of main at the top there in yellow. There is mention of getString toward the bottom. There is mention of printf down below. 

So this is just another programming language called assembly language, that decades ago, humans-- myself included in school-- did write code in. And absolutely, some people still write this code, especially since you can write very, very efficient code. But it's a lot more arcane. It's a lot less user friendly. 

So you'll see in yellow now, these are the so-called instructions that a computer's brain or CPU understands, pushing values around, moving them, subtracting values, calling functions, and move, move, move. So really, the low-level operations that computers understand tend to be arithmetic operations-- subtraction, addition, and the like-- moving things in and out of memory. It's just a lot more tedious for folks like us to write code like this. This is why you and I tend to write stuff like this. 

And ideally, still, people like you and I tend to drag and drop puzzle pieces that sort of abstract all of that away further. But for now, this is, again, called assembly language. It is what happens when the compiler literally compiles your code. But of course, this, still not zeros and ones. So we got two steps to go. 

So when a compiler proceeds to step three, this is where things get converted to machine code. And when a compiler assembles your code for you, it converts what we just saw on the screen here to actual zeros and ones-- the so-called machine code that your phone or your computer understands. But it's worth noting that these are not necessarily all of the zeros and ones of your program. 

Yes, they are the zeros and ones that correspond to your Hello program or printf and getString and the like, but notice that here, we need one final step. In those zeros and ones are only your lines of code. But what about CS50's lines of code that we wrote to implement getString? What about the lines of code that humans wrote decades ago to implement printf? Those are somewhere on this hard drive, like on my Mac, my PC, or somewhere in the cloud, but we need to combine all of those zeros and ones together and link my code with CS50's code with standard I/O's code, all together. 

And so what happens in the last step, ultimately, is that if we have my code here in yellow, and then the code that CS50 wrote, and the code that the authors of C itself wrote, what really is happening is that somewhere, we have not only hello.c, which, obviously, I wrote, and wrote with us live here, there's also, let's assume, somewhere on the computer, a cs50.c file that, coincidentally, I and CS50 staff wrote years ago. And also, somewhere on the computer, there's another file. Let me oversimplify by just calling it stdio.c. In practice, it's probably specifically called printf.c. But they're somewhere, these two other files. 

And so this last step called linking takes my zeros and ones from the code I just wrote, namely this code on the screen here. It then grabs the zeros and ones that CS50 wrote. And it grabs the zeros and ones that the authors of C wrote, in order to implement the standard I/O library. And lastly, voila, links them all together. 

And this is the same blob of zeros and ones that we saw earlier. It's just now the result of preprocessing your code, compiling your code, assembling your code, linking your code, and my God, at this point, like if there were any fun in programming for you yet, we've just taken it all away, we just call this whole process compiling. Why? Because now that we know those steps exist-- and smart people solve that problem for us-- you and I can kind of operate at this level of abstraction and just assume that compiling converts source code to machine code. 

Questions, though, on any of these intermediate steps? Yeah? 

AUDIENCE: For linking, are different parts, like [INAUDIBLE]? 

DAVID MALAN: A good question. So where are all of these zeros and one stored? Because you and I, we've been using a browser, right? code.cs50.io, of course, is this web-based user interface. But again, recall from last week, even though you're using a web browser to access VS Code, that web-based version of VS code is connected to an actual server somewhere in the cloud. 

And on that server, you have your own account and your own files, and really, your own hard drive, virtually in the cloud. Think of it a little like Dropbox or Box or Google Drive or OneDrive or something like that. So you have a hard drive somewhere out there that we've provisioned for you. And it's on that hard drive that you have your code that you just wrote, or I just wrote, cs50.c, stdio.c, and all of the other code that implements the math functions and everything else that C supports. Good question. Yeah? 

AUDIENCE: So, say in the CS50 library, the line [INAUDIBLE] do we do the same exact thing [INAUDIBLE] copy paste them all the way over? 

DAVID MALAN: Good question. That hash includes cs50.h line at the top of my code. If I just replace that with the contents of cs50.c, would that work? Short answer, yes, that would work. You could copy all of the code there. 

However, there's some order of operations that might come into play. And so it's probably not quite as simple as copy, paste. But conceptually, yes, that's what's happening. Now with that said, in cs50.h, are only the prototypes of the functions, the hints as to how the functions look, what their return type is, what their name is, and what their arguments are. 

It's in the dot c file that actual code tends to be written. And this is a little confusing now because you and I have only written code in dot c files. But in the next few weeks, you'll actually start writing some of your own dot h files as well, just like CS50, just like standard I/O. But in essence, that line of code just makes it easier to use and reuse code that's already been written. And that's the whole point of a library. 

AUDIENCE: Does linking them [INAUDIBLE]? 

DAVID MALAN: Say that a little louder. 

AUDIENCE: Does linking happen when you use the compiler? 

DAVID MALAN: Yes. Does linking happen when you compile your code? Yes. When you run make, as we have been doing the past week now, all four of these steps are happening. 

Preprocessing converts the hash include lines to something else. Compiling technically converts it to assembly code, which the Mac, the PC, the server more closely understands. Assembly converts that language to binary machine code that this computer actually understands. And then linking combines everything together. 

And in fact, if you think back a few minutes ago to when I did this -lcs50, the reason I had to add that, and the reason my code did not compile at first, was because I forgot to tell clang to link in CS50's zeros and ones per that last step. I don't need to do -lstdio because it comes with C, so that would just be tedious for everyone in the world. But CS50 does not come with C, so we link that in. 

And to be clear, too, we won't always use CS50's library. That'll be yet another pair of training wheels we take off in the coming weeks. But for now, it makes a few things simpler. Yeah? 

AUDIENCE: What is the [INAUDIBLE]? 

DAVID MALAN: Short answer, yes. So what do the zeros and ones, the machine code, translate to? Yes, there is a one-to-one relationship between the machine code and the assembly code. Assembly code, it's not really English, but at least it's symbols I recognize. It's not zeros and ones. 

Machine code, of course, is just zeros and ones. So back in the day, before C existed, people were programming only in assembly code. Before assembly code existed, people were coding in zeros and ones. And you can imagine just how painful that was, and so each of these languages makes life, for us, sort of easier and easier. In a few weeks, we'll transition to Python, which will, in turn, make C even simpler-- or coding, in general, simpler to do too. 

All right, so with that said, what now can we-- what could go wrong with this? Well, it turns out that besides compiling, technically speaking, there's decompiling. And we've not done this, and we won't do this. But it's worth considering for just a moment. 

If you were to not compile your code, but decompile it-- as the word suggests, this just means reversing the process, converting it, ideally, from machine code-- zeros and ones-- maybe back to C. Now this would be cool, perhaps, if all you have is a program, you can convert it and see the actual source code. What might a downside be, if anyone on the internet is able to decompile code on their machine? Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: OK, so it's easier to find bugs in the code that-- oh, to exploit. So it might be easier to hack into the software by finding mistakes you and I made because, literally, they're staring at you in code, whereas the zeros and ones make it way less obvious. Other downsides of what I called decompiling? Yeah? 

AUDIENCE: If stuff is copyrighted or you don't even know how to get it-- 

DAVID MALAN: Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, if your code, your work, is your intellectual property, copyrighted or otherwise, that's kind of obnoxious that someone can just run a command, and boom, they can see the original code that you wrote. Now, it turns out it's not quite as simple as that. And so even though, yes, you could take a program like Hello, or even Microsoft Word, and convert it from zeros and ones back to some form of source code-- be it in C or Java or Python or something else, whatever it was originally written in-- odds are it's going to be an utter mess to look at. Why? 

Because things variable names are not retained in the zeros and ones, typically. Function names might not be retained in the zeros and ones. The code is, the logic is, but the computer doesn't care what pretty variables you chose and how nicely named your functions were, it just needs to know them as zeros and ones. 

Moreover, if you think about last week, we introduced things like loops in C. And besides for loops, there's what other kind of loop, for instance? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: So, a while loop-- and even though they look different and you have to write different code, they achieve exactly the same functionality, which is to say, when you compile a for loop or you compile a while loop, if they logically do the same thing, they might end up looking identical as zeros and ones. And so, therefore, it's not necessarily predictable that you'll get back the original code, why? Because the zeros and ones might not know, so to speak, whether it was a for loop or a while loop, so maybe compiling will show you one or the other. 

And honestly, decompiling, while possible-- and it's one way of reverse engineering someone's product. Odds are, if you're good enough to start reading code that's been decompiled and reading through the messiness of it, odds are you have the talent probably to just write that same program from scratch yourself. Now, that's an overstatement, perhaps, but it's not quite as easy or threatening as you might first think. 

So in general, once code is compiled, it's pretty challenging, time consuming, costly to reverse engineer it, much like it would be in the real world, right? Like all of us have some kind of phone, probably, nowadays in our pocket. There's nothing stopping you from opening it up somehow, poking around, recreating what's there. That's a huge amount of effort, most likely. 

And at that point, maybe you should just invent the phone, instead of trying to reverse engineer it. So same kind of idea in the physical world. Any questions, then, on compiling, or even decompiling in these forms? 

All right, so odds are, at this point, not only I, but you have made mistakes. And you've written buggy code-- a bug in a code is just a mistake, a logical error or otherwise, where the code just does not behave correctly as you intend. And up until now, odds are, your debugging techniques have been to maybe look back at what I did in class, maybe ask a question online or in-person. But ultimately, it'd be nice if you had some tools of your own with which to debug code. 

And this, honestly, is a lifelong skill. You're not going to emerge from CS50-- and even 20 years from now, you're not going to be writing-- if you're writing code at all-- correct code all of the time. Like, all of us on the staff continue to write bugs. Hopefully, they get a little more sophisticated, and not sort of like, oops, I missed a semicolon. But even those kinds of mistakes, we make too. 

But there's tools out there and techniques that can make your life easier when it comes to solving those problems. Now, the term bug has actually been around for decades. But a fun story to tell is that the first documented actual bug was actually somehow connected to Harvard. In fact, this is the logbook relating to the Harvard Mark II computer from 1947, whereby if you read the notes here-- and I'll Zoom in-- this was an actual moth discovered inside of this big mainframe computer that was causing some kind of problems. And the engineers there at the time actually thought it was funny that, wow, physical bug actually explains the issue. And it's been forever taped to this sheet of paper, which I believe now is on display in the Smithsonian. 

With that said, this is just representative, too, of a logical bug. And that story is actually-- that story was often retold by a famous mathematician, then computer scientist really, Dr. Grace Hopper, who actually worked not only on the Harvard Mark II computer, but its predecessor, the Harvard Mark I. And if you ever spent time, yet, in the engineering building across the river here, you can actually see much of this computer, which is along the wall when you first walk into the Science and Engineering Complex. 

And indeed, as you've probably heard growing up, this is a mainframe computer. This is what Macs and PCs, so to speak, looked like back in the day, with very physical things that essentially implemented the zeros and ones that you and I take for granted now being miniaturized in our laptops and phones. So there's a piece of history there. If you visit that side of campus sometime, do take a look. 

But let's consider, then, how we solve not, of course, physical bugs, but logical bugs. And let's consider something like this from last week, whereby, we were trying very simply to print like this column of three bricks using hashtags of sorts. So let me go over here in just a moment to VS Code. And I'm going to go ahead and open a program I wrote in advance. And I'm bringing it to class because there's a bug in it, and I'd like to figure out how to solve this bug. 

So let me open up a buggy0.c, which is version 0 of my code. And let's just take a quick peek at what's here. It's pretty short. It includes only stdio.h, it uses printf, it uses a for loop, and the goal, quite simply, is to print out that column of three bricks. 

Now, it's short enough that some of you, if you're getting comfy already with C, you might already see the logical bug. It's not a syntax error, like it will compile and run. But there's a bug there. And suppose that I'm very new to C, I'm very uncomfortable with C, it's 2:00 AM and I just can't see the bug, what are my recourses here for actually finding a mistake like this? 

Well, first, let's look at the symptom. Let me go down to my terminal window. I'm going to use make buggy0 because, again, the file is called buggyo.c. 

I'm not going to use clang. In fact, I'm never really going to use clang manually here on out. I'm just going to use make because it makes our lives easier. It does compile. No errors, so it's not syntax. It's not something silly like a missing semicolon. 

But when I run ./buggy0, I, of course, see one, two, three, four-- and this, of course, does not match the one, two, three bricks that I actually intended for that column. And yet, I'm starting counting at 0, as I usually do. I've got three. I'm going up to three. 

So where is my logical error? If it hasn't obviously jumped out at you already, well, how can I solve this? Well, first and foremost, perhaps the best technique for solving bugs, at least early on, is just use printf. Like thus far, we've used sprint say, Hello, and other things on the screen. 

But printf is just a function for printing anything. And there's no reason you can't temporarily use printf to print out the contents of variables, what's going on inside of your program, just to figure out where your mistake is. And then you can delete that line of code later. It doesn't have to stay there forever. 

So let me do this. Instead of just printing out in VS Code the hash symbol, let me do a little safety check here and print out the value of i. So let me go ahead and say something like, i is-- now I want to say i is this. But, of course, this is not how I print out the value of i. 

If I want to print out the value of i, what should I put here? So %i for integer, instead of %s for string. So they're still placeholders. But we use %s for integers. And now if I want to print out i, I just need the comma as the second argument, and then i. 

All right, let me go ahead and back to my terminal window. Let me recompile the program because I've changed it. That still works fine, ./buggy0. 

And now, let me increase the size of my terminal window here. You just see some diagnostic information, if you will. This is not the goal. This is not what you should be submitting for this homework problem, were it one. 

But it is helping us diagnostically know that, OK, when i is zero, here's a hash. When i is 1, here's a hash. When i is two, here's a hash. When i is 3, here's a hash. 

Well, wait a minute. That's one, two, three, four. So clearly, I'm printing it one too many times. So let me look back at the code here by shrinking my terminal window. And let me just ask the group, where is, in fact, the mistake? Or what, equivalently, would be the solution? Yeah, in the middle. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, instead of less than or equal to, use just less than. So you've got to kind of pick a lane here. If you're going to start counting from 0, you generally use less than, and go up to, but not through the value. Or if you prefer, like in the human world, counting from 1 on up, you can use less than or equal to, but you have to be consistent. 

And in general, as a programmer, just always start counting from 0 if you're doing something canonical like this. But the solution is, indeed, just to change this by changing the greater less than or equal to the less than. If I recompile this program with make buggy0, and then do .buggy0 again-- and let me increase the size of my terminal window. Now, you see, OK, almost the same output. But indeed, i starts at 0 and goes up to, but not through, three. 

All right, so printf, in short, can be your first diagnostic tool. Instead of just staring at the screen or raising your hand-- I mean, use printf to see, literally, what's going on inside of your program by just printing out things of interest. And then once you've solved the problem, you can go back into your code, as I'll do here, by shrinking my terminal window. I'll delete the printf line. 

And now I'm ready to share this program with the world or submit it as homework or the like. It's just meant there to be temporary. Any questions on printf as a debugging tool? 

No? All right, well, that only gets us so far. And honestly, as your programs grow and grow and grow, it's going to actually get really annoying to start going in and adding printf's, then removing them, and figuring out, if you've got multiple printf's, well, which one printed what? It just gets messy, eventually, to rely on printf alone. 

So being a computer scientist, computer scientists have written software to make it easier to debug code. That software is what we would generally call a debugger, which would be the second tool of the trade that you can use to actually solve problems in your code. Now, in the world of VS code, there's actually a debugger built in. So the graphical user interface you're about to see in VS Code isn't specific to CS50, it actually comes with VS Code. And it supports C, and C++, and Java, and Python, and lots of other languages too. 

But it's, admittedly, a little complicated to just start using the debugger. You have to create a configuration file and do some annoying steps that just get in the way of solving real problems. So we have automated the process for you of just starting the debugger. And thereafter, it's sort of industry standard how you use it. But we save you the headache of having to create those configuration files. 

So, suppose I want to do this. Suppose I want to try to debug this program step by step using special software. Well, how can I do that? 

Well, let me propose that if I revert this back to the original version where i was less than or equal to 3, I'm pretty sure that I was printing too many hashes. So I'm going to do this-- and you might have done this accidentally or never at all. But notice if you hover over the gutter, so to speak, in VS Code, the part of it all the way to the left of the editor, you see this sort of grayed out red dot. If you click there, it becomes a brighter red dot. And this represents what we're going to call a breakpoint. 

And this is just a visual indicator that you've put like a stop sign equivalent there, and you're telling the debugger in a moment, stop running my code there. Why? Because I prefer to step through my code at sort of a human speed, and not as computer speed where it runs all at once. So I've set my breakpoint, which is step one. 

And then step two is quite simply this. Instead of running the program itself, run the command called debug50, and then ./buggy0. And now this will start your program, but inside of the debugger, which is a special program that smart people wrote that will empower you to now step through your code line by line, and again, at your own comfort pace. I'm going to hit Enter, some stuff's going to happen on the screen-- whoops. 

Notice, this is a common mistake that I made accidentally here. Looks like I've changed my code. I did because I went in and changed the less than or equal to sign. So let me go ahead and rerun make buggy0-- Enter. 

Good, now let me rerun debug50-- Enter. And now some stuff just happened on the screen and it takes a moment to get started but once it's started you'll see this you'll still see your code. But you'll see this yellow highlight, which you've probably not seen before. 

And notice that it's specifically highlighting the same line that I set a breakpoint on. Why? That just means the debugger has executed all of these lines, except for line 7. It has broken at-- not in a bad way. But it has paused execution on line 7, so it hasn't yet printed any hashes. 

And you can see that-- no hashes in the terminal window yet. It's paused execution. But what's interesting with the debugger is the stuff over here on the left-hand side. In the debugger here, you'll see, under variables, all of your so-called local variables. And we haven't really made a distinction between local and something called global. But for now, local variables just means all of the variables that exist in your function. 

So i currently has a value of 0. OK, and that makes sense. So now, how do I step through my code and see what it's doing? Well, at the top of the screen here, you'll see some playback icons, kind of like a video player, but they have special meaning. 

This first one will just play the rest of your program all the way to the end. So you only click that if you've sort of solved the problem and you just want to run it to completion like before. But the next three-- or next two, really, are really the juiciest. 

The second one here, if you hover over it, eventually, you'll see that it's called Step Over. Step Over means that the debugger will run this currently highlighted line of code, but it's not going to dive into it. 

So if it's a function like printf, it's not going to start stepping through printf line by line. Why? Because I can pretty much assume printf, written decades ago, is correct. Problem's probably with me. 

But this next line, if I did really want to step into the printf code to figure out how it works or find some problem in it all these years later, you can step into printf, and then the screen would change, and you'd see each of the lines for printf, line by line-- at least if you have the source code for printf installed. All right, I'm going to use the first one, Step Over. And watch as the yellow highlight moves. And watch as, in the terminal window, there's a hash symbol. 

Here we go. There's one hash. Now, notice line 5 is highlighted. That means it has paused on line 5. Line 5 has not yet been executed. 

So what does that mean? The value of i, per the top left-hand corner, is still 0. But as soon as I click Step Over again, watch what happens at the top left, where i is a variable on the screen. Now i-- and it flashed briefly-- has a value of 1. 

And now if I step over again, watch the terminal window. There's my second hash. Now, let me click Step Over on for loop, watch the variable at top left. Now 1 goes to 2. 

Now let me click it again. Third hash-- and here's where the logical error is perhaps revealed. Let me go ahead and step over the loop. Now i is 3. Wait a minute, I'm still going to print out a hash. 

There it is. There's the fourth hash. And at this point, hopefully, the light bulb, proverbially, has gone off. I realize, oh, I screwed up. I can either stop the program altogether with the red square, or I can just let it run all the way to the end, which just terminates everything. 

At this point, I just want to get back into my code and start fixing things. And you can close, for instance, as I will here, the File Explorer, just to hide the panel that opened. So that's debug50. But it's not a CS50 thing, that just starts the debugger for you, which is something you'd find in most any programming environment nowadays. 

Questions on debugging? Questions? Yeah? 

AUDIENCE: Where does it tell you where it went wrong? 

DAVID MALAN: Good question. Where does it tell you where it went wrong? So, sadly, it does not tell you any of that. The onus is still on you, the human, to use this tool productively to walk through your code at a saner pace. But your brain is the one that still needs to solve it. 

And I don't doubt, down the line, with artificial intelligence and more, programs like this will get all the more helpful, and start answering questions like that for us. And there are other tools we'll introduce you this semester that are even more powerful than this. But for now, it's just a tool, really, to slow things down and not have to change your code. The fact that I had that panel on the left that just showed me i's changing value is just an alternative to printf, and I can step through it a little more slowly. Other questions on debugging? 

No? Let me show you one final example with this debugger here. And this one, too, I wrote in advance. Let me close buggy0.c. And let me open up buggy1.c, my second version thereof. 

Let me close my terminal window for a second and give you a quick tour of this program, which similarly, has a mistake. Now, at the top of this program, some familiar includes, cs50.h and stdio.h. This is not something we've seen before. It's specific to this example-- a function called getNegativeInt. Takes no arguments, and it returns an integer. 

What does it do? It literally gets a negative integer, ideally, from the user. Fun fact, though, it doesn't correctly. That's the bug. getNegativeInt is broken at the moment. 

So what does main do? Well, main just calls this function, passing in nothing in parentheses, no inputs. And it stores the return value in i. And then it just prints out i on the screen. 

So honestly, just by eyeballing this, I feel comfortable enough with programming in C, I think main is correct. Let me just stipulate, main is correct. But there is going to be a bug down here. 

Now, what's the bug down here? Well, let me look at getNegativeInt's implementation. Notice, this first line, 12, is identical to the prototype up here. The prototype is sort of stupidly required up here because C reads things top to bottom, left to right-- the compiler technically does. So if you reference getNegativeInt here, but you don't implement it until down here, and you haven't told C in advance that it will exist, again, you get the error we saw last week. 

All right, so how does getNegativeInt work? We declare a variable called n. We've got to do while loop that does what? It uses getInt, which comes with the cs50 library, per last week. It prompts the user for negative integer, quote unquote, and stores the value in n. 

I then do all of this while n is less than 0, right? Remember, we used to do while loop last week to make sure the human cooperates and doesn't give us the wrong type of value, be it positive or negative or something else. And then we return n. 

And there's some subtleties. Anyone recall-- or have an intuition for why I've declared n on line 14, instead of line 17? This is a C specific thing. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Exactly. There's this notion of scope in C. And we'll continue to see this over time, whereby, a variable only exists inside of the most recent curly braces that you've opened. So if I've declared n here on line 14, I can use it anywhere between lines 13 and 21 because those are the nearest curly braces. 

If by contrast, as you note, if I instead said this, int n equals getInt and so forth, and didn't have the current line 14, well, n would exist inside of these curly braces, but not here, which is too late, and definitely not here. So you just have to declare it first, and then use and reuse it as such. Now, let me just show you how I can debug this. But let me show you the symptoms first. 

Let me open my terminal window. Let me run make buggy1. Compiles OK, so it's not something silly like a semicolon. ./buggy1, and I'm asked for a negative integer. All right, let me give it negative 1-- Enter. 

Well, the main function is supposed to print out what I typed, but it clearly didn't. It's prompting me again. All right, so maybe it'll like negative 2. No? Maybe negative 3. 50? 

OK, so it's definitely broken, right? It kind of seems logically to be doing the opposite. Now, you can perhaps see why this is happening already. These are deliberately simple programs for demonstrations sake. 

But let's do this. Let me go ahead and set a breakpoint in main, even though I'm pretty sure main is correct. But it just helps me start my thought process-- start with main, and then take it from there. Let me run now, debug50 ./buggy1-- Enter. 

And let's see. With that breakpoint now, the GUI is going to reconfigure itself. It's going to pause on line 8 because that's the first interesting line inside of main. So I could have just put the breakpoint on line 8 too. It's smart enough to know that if I set it on 6, you really mean line 8 because that's the first actual line of code. 

And watch, now, what happens. If I step over this line, notice that i, which at the moment seems to have a default value of 0-- more on that another time. But if I click Step Over like before, I'm prompted for a negative integer. Let me type negative 1-- Enter. 

And now, notice, there's no additional yellow highlight. Why? Where am I currently stuck, logically? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, just logically, I must be in that do, while loop. And even if you don't understand it, like that's the only explanation. If you keep getting prompted, surely, there's a loop going on. There's only one loop in my code, so there's probably a problem there. 

So I can't just set a breakpoint in main, and then wait for this to work. So let me just-- let me stop this with the red square. And let me think, all right, instead of-- I can still set my breakpoint in main, but let me rerun the debugger instead. And this time, not step over that line of code, let me step into that line of code. 

So watch what happens now. Instead of clicking the second icon here, let me click the third, whose name is, indeed, Step Into. And watch as the yellow highlight does not move to line 9. It dives into line 8-- the function on line 8, thereby, bringing me down to line 17. It's kind of going down into that next function. 

Now, it didn't bother pausing on line 12 or 13 or 14 because there's nothing intellectually interesting there happening yet. The juicy part really starts, it would seem, in line 17. So, now notice, n is my variable at the top left. If I click-- I don't want to click Step Into now, though. What would go wrong if I click on Step Into-- or what would it do that I don't think I want to do? Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, it would step into getInt. But I'd like to think that the staff's version of getInt is correct, and that's not our problem today, so I want to step over it. And watch now at top left that nothing happens yet to the value of n until I go to the terminal window now, and I type in something like negative 1. 

Now notice, it jumps to line 19, which is the next interesting line. Top left, n, indeed, is negative 1. And here's where I can now pause as a human and think, all right, so while n is less than 0. All right, n, per the top left corner, is negative 1. So all right, while negative 1 is less than 0, well, obviously that's true mathematically. 

So what's going to happen? It's a do while loop. So when I click on Step Over again, it's going to go to this line because it's at the end of the inside of that loop. 

And now here, it's looping through again and again. All right, let me do this once more. I'm going to step over, all right? I'm going to type in negative 2, and it's the exact same thing. 

Now is my chance, on the yellow line-- OK, wait a minute. Negative 2 is obviously less than 0. Let me try this one more time. Click it once here. 

All right, let me give it 50. And now, OK, while 50 is less than 0, that's not true, so the loop is over because it's not going to do it while 50 is less than 0. That's not true. So now watch, when I click Step Over once more, it then finishes the loop, even though there's nothing more to do. 

It's now about to return n. It jumps back up to main, where I left off on line 9. It now prints, in my terminal window, the number 50. And hopefully, at this point, to your question earlier, my human brain has realized, oh, I'm an idiot, like I flipped my sign there. So I probably-- let me stop this. 

I probably want to do something like this. If the goal is to get a negative integer, I probably want to say, while n is, for instance, greater than or equal to 0 would work. So while n is greater than or equal to 0, keep doing this. And that's the logic I wanted to express. 

So the debugger just saves me from staring at the screen, raising a hand, sort of asking someone else. At least in this case, it allows me to go through it at a healthier pace. Questions now on debug50, which should be your new friend, even if it's not your first instinct after printf? 

Any questions on debug50? No? All right, well, there's one last technique we can equip you with here. And that is, in addition to printf and a debugger, no joke, a rubber duck is actually a reasonably recommended solution to finding bugs in your code. 

To your question earlier, the duck two is not going to solve the problem for you. But if you've wondered why this little guy has been here for so long, there's this technique, has its own Wikipedia article of called rubber duck debugging. The idea of which is that if you're home in your dorm room, wrestling with some bug in your code, printf didn't quite reveal the source to you, debugger isn't really helping, honestly, maybe it would help to just sound out what problem you're having. Similar to going to office hours, talking to a TA or a professor, just walking through your problems because in sort of talking to the duck about the fact that you're doing this while n is less than 0, and then if it is-- wait a minute. I'm an idiot, not just for talking to the rubber duck. 

You realize, hopefully, in expressing yourself, literally verbally, you probably will hear with non-zero probability, like some illogic in your statement. And just by sounding things out, you'll realize like, oh, that's my problem. And so, frankly, if you have roommates, you can also use a roommate for this. But the rubber duck is just sort of a go-to when your roommates have no interest in your C problem set, talking something through that as such. 

And this is an invaluable technique. I admittedly tend not to do it so much with a rubber duck, but ideally with colleagues, human colleagues. But just talking through things often will help you just realize, oh, I said something illogical. Now I can go back to the code. 

So don't solve problems by staring at your screen endlessly for minutes, for hours. At that point, it's time for a break, time to walk away, time to talk to the duck, if you've already exhausted some of those other tools. As an aside, on your way out today at the end of class, we have, clearly, plenty of rubber ducks for you. And it's become a thing over the years, at least among some, to bring the duck with them when they travel and send us photos. 

Here, for instance, is CS50's rubber duck debugger, A.K.A. DDB, for Duck Debugger, which is a pun on a geekier program called GDB, the GNU Debugger, which is an actual piece of software for debugging. This is CS50's debugger in the hills of Puerto Rico, also, here on the sea. He made its way to San Francisco here. Also, down by Fisherman's Wharf by the sea lions. Familiar? 

Here at Stanford, where there's a William Gates Computer Science building for computer science, down the road in SF at Google. And this is the Trevi Fountain in Rome. And lastly, the Colosseum. So we'll be curious to see in the coming years where your duck two travels. 

So that, then, was quite a bit. Why don't we go ahead here and take a short 5 minute break? No snacks yet. You're welcome to get up or sit down. We'll return in about five. 

All right, so we are back. And if the goal, ultimately, today is to have a better understanding of things like strings so that we can solve problems with text, let's consider some simpler types of data first, how we might represent those, and then see if that doesn't lead us to a discovery as to how strings, and just today's modern software is using things like that. So when we talked on week zero about representation of data, we had different ways of doing it, in terms of binary and decimal, and unary even. 

When we started talking about the same last week in code, we started talking about data types instead. And these data types were a way of telling the computer, like do you want an integer, do you want a character, do you want a floating point value, like a real number, or even a string, as we've seen? But it turns out that computers, of course, only have finite amounts of resources. Your computer only has a fixed amount of memory or RAM. And that actually has very real world implications. 

So for instance, here are some of the data types we've seen thus far. And it turns out that each of these in C has a specific number of bits allocated to it. Now, admittedly, this can vary by system. 

It's not so much the case nowadays, but for many years, for decades, computers were getting better and better. The earliest computers might have used fewer bits for some of these data types. More modern computers might use more bits. So the numbers you're about to see are pretty much where we are present day. 

So when it comes to these data types, a bool, which is true or false, somewhat curiously, uses a whole byte, even though that's way overkill because for a bool, true or false, you, of course, only need one bit. But it turns out, even though it's wasteful to use eight bits, or one byte, just to represent true or false, it's just easier for computers. So a bool tends to be one byte. 

An int, which we've been using a lot, uses 4 bytes, typically, or 32 bits. And if I do some quick math from week zero, with 32 bits, you have 4 billion possible values, roughly. But if you want to represent positive and negative, that means you can represent roughly negative 2 billion, all the way up to positive 2 billion. So that's the range, typically, with ints. 

If that's too few numbers for you, turns out there's things called longs. And longs use 64 bits, which allow you to have like a quintillion number of possibilities, which is a lot, certainly, a lot more than 4 billion. So sometimes you might use a long. But even that's finite. And so as we discussed at the end of last week, bad things can happen if you make certain assumptions as to the data because of things like integer overflow or the like, where things wrap around. 

Then there's a float, which is a real number, something with a decimal point. By convention, it's 4 bytes or 32 bits, which gives you, in short, only a specific amount of precision. It doesn't necessarily dictate how many numbers to the left or to the right. In the aggregate, ultimately, you have though, 4 billion possible permutations still. 

If you need more precision for scientific, for medical, for financial applications, you might use 8 bytes, A.K.A. a double, which just gives you more digits of precision. They eventually get imprecise per the example we looked at last week, but it at least gets you further down the line. 

As an aside, in really, really important applications, in finance, in medicine, in military operations, and the like where you really can't have rounding errors-- long story short, humans have developed libraries in C and other languages that use more, even, than 8 bytes. So there are solutions to these problems, but they're always finite. You have to pick an upper bound. 

Then there's char, which we saw briefly last week when I asked the user for y or n, for yes or no. And then there's a string, which I'm going to propose as a question mark because a string totally depends. Like, Hi! H-I, exclamation point, would seem to be three bytes. D-A-V-I-D, would seem to be five. 

So the strings, clearly, are variable based on what you or the human type in. So we'll see what this means, though, in just a bit. 

This though, is the thing inside of your Mac, your PC, your phone. It might not look exactly like this, but this is a memory module for a modern computer. And let's go ahead and use this. Really, it's just representative of the finite amount of memory that any computer, indeed, has. 

Let's zoom in on one of these little black chips on the circuit board here. Zoom in, and let me propose that this rectangle really represents some number of bytes, like tucked inside of this little black circuit on the board is maybe, I don't know, a gigabyte, a billion bytes, maybe it's 100 bytes-- some number of bytes. It totally depends on the computer and how much you paid for the stick of memory. 

But if there's a finite number of bytes physically implemented somehow digitally inside of this hardware, well, then it stands to reason that we could number those bytes. We can just arbitrarily decide that the top left corner is byte number one, or really byte number zero. The one next to it is number one, then number two, number 3, dot, dot, dot, number 2 billion or whatever it is, however big this memory is. 

So if you use a variable in a C program, that's only one byte. Like a char, it might literally be stored in that top left-hand corner of the memory. In practice, you don't care where, physically, it is. But really, the artist's rendition would be this-- a char might use one of those single bytes somewhere in the computer's memory. 

If you use an int, which is 4 bytes, it would give you 4 bytes, contiguous-- that is left to right, top to bottom. But all 32 bits would be next to each other so the computer knows that those, indeed, all belong to the same int. If you need a long, or a double for that matter, then you might use a full 8 bytes in this case. And you just keep using and using this memory, kind of like a canvas, almost in Photoshop or a spreadsheet where you can just move pixels or you can move data around, that's really what your computer's memory is, a canvas for storing information in units of bytes or 8 bits. 

Now, we don't need to keep looking at these circuit boards. We can abstract it away, as we often do. And let's go ahead and zoom in on this grid, just to consider some very specific variables. So let me zoom in, and now I see fewer, but larger boxes on the screen, each of which, again, represents a byte. And now let me propose that we play with some actual code. 

So here in C, albeit without a full program, are three ints-- score1, score2, score3. I have, coincidentally, given myself two scores around 72 and 73, and then a pretty low score at 33. Of course, last week or two weeks ago, this would have been high. But now we're dealing with actual integers. So these are three so-so scores on my quizzes or tests or the like. 

So let me go to VS Code here. And let's make a program called scores.c. So I'm going to write, code scores.c. That's going to give me my new file. 

And let me go ahead and implement something like this. Include stdio.h, int main(void), and then inside of here, let me do int score1 will be 72. Int score2 will be 73. And int score3 will be 33. And then let me just do something like write a program to average my three test scores together, something like that. 

So let me do printf, quote unquote, my average is-- and I'm going to go ahead and do, say, %i, /n. And now, let me plug in the results. And this is kind of grade school math now. How do I compute the average of three values? Well, just like on paper, I can do score1 plus score2 plus score3 in parentheses, because of order of operations, divided by 3, since there's three total scores. 

All right, so I think this checks out. And indeed, you can use parentheses and operators like plus in your code like this in C. Let me go ahead now and do make scores. No syntax error. So that's good, nothing missing there. 

And now let me do ./scores and see what my test average is. All right, it's not great, but I think I still passed. And indeed, my average here is 59. Is it precisely 59 though? 

Well, let's see. Let's actually, instead of using an int, how about we go ahead and use something like a floating point value here? And let me go ahead and do this. So let me recompile my code, make scores. 

Huh, all right, I've got an issue. Let me zoom in on my terminal window. We've not seen this one, necessarily, before. But error on line 9. Format specifies type double, which is a lot of precision, but the argument has type int. 

So what does this mean? Well, it's showing me with these green squiggles that something's bad between the %f and this thing over here. Well, on the left, I'm implying a float, or a double for that matter. On the right, though, what data type are score1, score2, score3? 

All right, so they're ints. So clang does not like this. The compiler just doesn't like that I'm using ints on the right, but I want floats on the left. So there's going to be different ways of solving this. 

One way would be to just ignore the problem like I originally did, and just go back to %i. Or as an aside, %d is often an alternative to %i for a decimal number. But we use %i because it sounds like int, so %i is fine here too. 

But I don't want to just avoid the problem. I want to actually display a floating point value. So how can I fix this? Well, it turns out, I can solve this in a few different ways. 

The simplest is just to make sure that at least one number on the right is a floating point value, like 3.0 instead of just 3. Now I think clang will be happier. Let me do make scores-- Enter. 

And indeed, it's OK. Why? As soon as you have at least one more precise data type on the right, it just treats everything, at that point, as floating point value so that the math works out. 

So ./scores, Enter-- and now, there we go, right? Some of us might really want that 1/3 of a point. Our average was not 59. It's 59 1/3, as in this case here. 

All right, so we've solved that there. As an aside, though, there's one other technique to show here. If you didn't want to change it to 3.0 because that's a little weird, because there were literally three scores, it's not like that needs to have a decimal point, you could also explicitly convert the 3 to a float by saying, in parentheses, float. This is what's called typecasting. And this will just convert the thing right after it to that data type, if it's possible. 

So if I do this again, make scores, no errors now. ./scores, and I get, in fact, the same result. There's a bit of a rounding issue here, but we know the rounding relates to the imprecision from last week. For now, let me just be happy with my 59.3 something. I'll take that for now. But this is as close to a good enough correct answer for me now. But how do I-- think about now, what's going on inside of the computer's memory? 

Well, let's consider. Here's that same grid of memory. Each box represents a byte. Where are score1, score2, and score3 in my memory? 

Well, score1, let me just propose, is at the top left. But it's taking up four boxes for 4 bytes. Score2 probably ends up right next to it in memory, though, this isn't always going to be the case, but I've chosen simple examples. 73 is next to it, also taking up 4 bytes. And then lastly, 33 is in score3, down there underneath. 

Now, if we really look at the computer's memory, look at it with some kind of microscope or the like, there's actually 32 bits, 32 bits, 32 bits in each of those four groups of four bytes representing those values. But again, for today's purposes onwards, we don't really need to think again and again in binary. It's just, indeed, these decimal numbers being stored there. 

But I claim now, this isn't the best design. Even if you have never programmed before CS50, what you're looking at here on the screen, as an excerpt, in what sense is this perhaps bad design, even though it's a correct way of storing three test scores? What's kind of bad here? Yeah? 

AUDIENCE: The more scores you have, the more you [INAUDIBLE]. 

DAVID MALAN: Yeah, always do exactly what you did-- extrapolate to 4 scores, 5 scores 50 scores. This can't be that well-designed because now you're going to have 4 lines of code, 5 lines of code, 50 lines of code that are almost identical, except for this like arbitrary number that we're updating at the end of the variable. So indeed, there's probably going to be a better way, even though, at least in C, we haven't yet seen that technique. 

But the solution, today onward, is going to be something called an array. An array is a way of storing your data back to back to back in the computer's memory in such a way that you can access each individual member easily. Put another way, with an array, you can instead do something like this. Instead of saying int score1, int score2, int score3, giving each a value, you can first tell the computer, please give me a variable called scores-- plural, though you can call it anything you want-- of size three, each of which will be an integer. That is to say, this is how you declare an array in C that will have enough room to store three integers. 

Put another way, this is the technical way of telling the computer, please give me 12 bytes in total-- 3 times 4 each for an int, so give me 12 bytes in total. And what the computer will do is guarantee that they're back to back to back in the computer's memory. And that'll be useful in just a moment. 

So let me go ahead and do something useful with this. Let me store three actual scores. Here's how I could now store those same numeric scores in this array. Syntax is a little different, but there's one variable called scores. 

But if you want to go to its first location, starting today, you use square brackets and go to location 0 first, which because things in C are 0 indexed, so to speak, you start counting at 0. The first int is at [0]. Second int is at [1]. Third int is at [2]. 

So it's not one, two, three. It's literally 0, 1, 2. And this is not something you have control over. You must start at 0. So these lines now create an array of size three, and then insert one, two, three values into that array. 

But the upside now is that you only have one name of the variable to remember. It's just called scores. Yes, you need to go into the array to get individual values. You need to index into it using those square brackets. But at least you don't have this hackish approach of declaring a separate variable for each and every one of these values. 

So let me go back to scores.c here. And let me propose that I do this. Let me just use that same idea to do the following. Let me get rid of these three separate integers. Let me give myself an int scores array of size 3. 

And then scores[0] will, as before, be 72. Scores[1] will be 73. And scores[2] will be 33. And let me get rid of the little dot there. 

All right, so now, if I go ahead and run this again with make scores-- Enter. Huh, what did I do wrong here? I think I got a little too ahead of myself. Let me increase my terminal window. 

Let's focus on line 10 here, first. Error, use of undeclared identifier, score1. What did I do here that was dumb? Yeah? 

AUDIENCE: You didn't declare it a variable. 

DAVID MALAN: Right, so I didn't declare score1. I've got old code. So I just kind of, honestly, got ahead of myself here, not even intentionally. So let me go ahead and shrink my terminal window again. 

I need to finish my thought here. So let me clear my terminal. And let me change this now to be scores[0] plus scores[1] plus scores[2]. So it's a little more verbose because I've got these square brackets, so to speak. But I think now my code is consistent. 

So let me make scores now. It now compiles. ./scores gives me, indeed, the same rough average with those same values. 

All right, so let me go ahead and maybe enhance this a little bit. It's a little silly to have to write a special program just to check your average of three test scores like 72, 73, 33. Why don't I actually make the program dynamic and ask the human for those scores? 

So instead, let me do this. How about we get rid of the 72, and change this to getInt. And I'll just prompt the user for a score. Let me get rid of the 73 and get this to be getInt score, quote unquote. And then lastly, get rid of the 33, and replace it with getInt, quote unquote, score. 

getInt is a CS50 thing for now, so I need to include cs50.h, as always. But I think now, it's sort of a better program because now I can compile it once, I can even share it with my friends. And now any of us can average three scores on some classes test. They don't need to know the code or rewrite the code just to type in their scores. 

So make scores worked. ./scores, now I can type anything I want-- maybe it's a 72, 73, 33, still get the same answer. Or maybe I'm having a better semester, 100, 100, maybe 99, and now we get still a pretty high score there. 

But now it's dynamic. Now you don't need the source code. You don't need to recompile the program. It's just going to work again and again. 

But this, too. Let me propose that this code is correct if I want to get three scores from the user. But these highlighted lines now, 6 through 9, are they well-designed, would you say? Yeah? 

AUDIENCE: Can you loop? 

DAVID MALAN: Yeah, right? This is-- we can use a loop, is the spoiler here. Why? I mean, my God, it's like the same code again and again and again. The only thing that's changing is the number. And this should have kind of had some code smell again, because if I keep typing the same thing again and again, that's clearly an opportunity to better design something. 

So let me do this. Let me go ahead and still create my array of size three. But let me use our old friend, the for loop, for int i equals 0, i less than 3, i++. 

And then in here, let me do scores bracket-- we haven't seen this before, but any intuition? Scores bracket-- 

AUDIENCE: i. 

DAVID MALAN: i, because that will use whatever i is, be it 0 or 1 or 2 in iteration. And then I can get an int, asking the user for score, without having to repeat myself again and again. So hopefully, if I didn't make any typos, make scores, all good. 

./scores, 72, 73, 33, and we're back in business. But the code is arguably now better designed, because now, I haven't actually hardcoded the scores, and I haven't actually copied and pasted any of that code. Well, if we consider now what's going on inside of the computer's memory, it's pretty much the same in terms of the values. 

But instead of the variables being, literally, score1, score2, score3, there's just one variable. It's an array called scores. But you can index into its three locations by using scores[0] to get the first, scores[1] to get the second, scores[2] to get the third. 

But this is key. The memory is contiguous. The screen is only so large, so it wraps around. But physically, digitally, the memory is contiguous-- top to bottom, left to right. 

And that's important, why? Because the brackets indicate 0, 1, 2, that each of these integers is just one integer away from the next. It can't be randomly down here all of a sudden. It's got to be back to back to back. 

All right, now equipped with that paradigm, what more could we actually do here? Well, it turns out, it's worth knowing that it's possible in code to even pass arrays around as arguments. And let me just whip this program up somewhat quickly, just so you've seen it before long. But let me go ahead and do this. 

Let me propose that I create a function that does this averaging for me. So I'm going to create a function called average that returns a float. And the arguments this thing is going to take-- let's see, it's going to be the array. So it turns out, if you want to take in an array of numbers-- you can call it anything you want. This is how you tell C that a function takes, not an integer, but an array of integers. 

And you don't have to call it array. I'm doing that just for the sake of discussion. It can be called x. It can be numbers. It can be anything else. 

I'm just calling an array to be super explicit as to what it is there. Now, how do I change my code down here? What I think I'm going to do for the moment is just this. I'm going to get rid of this code here, where I manually computed the average. And let me just call the average function here by passing in the whole array of scores. 

So this is just an example of abstraction, like now I have a function called average. I don't care. I don't have to remember how it works once I implement it. It just kind of tightens up my main code a little bit. But I do still have to implement this. 

So later in my file-- let me repeat myself before, the only time it's OK in C to repeat yourself again and again, by typing out again, average, and then int array open bracket-- but now not a semicolon. Now I have to implement this thing. And I can implement this in a bunch of different ways, but I don't know in advance-- I can't just do this. 

I can't just do array[0] plus array[1] plus array[2], unless this program's only ever going to work on three numbers. So let me go ahead and do this. Let me first propose that there's a poor design here. In my main function, what value have I repeated twice? Among the highlighted lines, what jumps out at you as twice? 

AUDIENCE: The length of the array? 

DAVID MALAN: Yeah, the length of the array, it's just three. Now it's not a huge deal that I typed the number three on line 8 and line 9, but this is exactly the kind of like shortcut that's going to get you in trouble eventually. Why? Because, eventually, you or someone else is going to go in and make the array bigger or smaller, and you're not going to realize that magically, that same number is in two places. 

And indeed, this is what a programmer would often call a magic number. A magic number is one that just kind of appears magically. And you're on the honor system to change it here, if you change it here, and then you change it over here. That's not going to end well if the onus is on the programmer to remember where they hardcoded-- that is, wrote out three explicitly. 

So any time you reuse a value like this, you know what? We should probably do what we did last week, which was to declare a variable, perhaps at the very top of my program, so it's super obvious what it is, called, maybe n, and set that equal to 3. Better yet, what did I do last week to make sure that I can't screw up and accidentally change that value? 

Yeah, constant. And the keyword there was just const for short. And now I have a global variable-- global in the sense that I can access it anywhere-- that is called n. It's an int. And it's always going to be 3. 

And now I can improve my main function a little bit by just changing the 3's to n, so now if I, if a colleague realized, oh, wait a minute, there's four tests this year. You change n to four, recompile the code, and it just works everywhere else, except in my average function. Let me change it back to 3, just for consistency. This is not going to fly now, to just sum up things like this, for instance, and then return this divided by 3. Why will this not work now as I've defined it? Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: OK, I might be returning an integer value when I intend to return a float per this. But I think I'm OK because I used that little trick where I made sure that at least one of the numbers in my arithmetic expression is, in fact, a floating point value. And just by adding the point 0, make sure that everything gets treated as a float. So I think that's OK. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: I'm sorry, a little louder. 

AUDIENCE: It just seems like you're [INAUDIBLE]. 

DAVID MALAN: Exactly. So left hand's not talking to the right hand here, in that my current implementation of average is still assuming that there's only going to be three tests or whatever. But wait a minute, I just went through the trouble of modifying this to be n, generically. And if I change this to 4, I'm not going to be happy, perhaps, with my average because now I'm going to ignore one of my test scores altogether. 

So let me change this back to 3. And unfortunately, if it's a variable now, n, and therefore, I have literally a variable number of scores, how do I take the average of a variable number of things? I mean, what's my building block there? Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah. Why don't I use a loop that goes through the array and adds things up as you go? I mean, kind of like grade school, as you take the average on your calculator or paper and pencil, you just keep adding the numbers together, and then you divide at the end by the total number of things. 

So how can I do this? Well, let me change my implementation of average to first declare a variable called sum, or whatever, set it equal to 0. So this is like me on my piece of paper getting ready to count, or my calculator, of course, when you turn it on, typically defaults to zero. 

And now, let me do for, int i equals 0. i is less than a-- well, no, I didn't do that. i is less than n, i++. And now in here, let me go ahead and add to the current sum, whatever is in the array's location, i. And then down here, I think I can just return some divided by 3.0-- not 3.0, n, perhaps here. And actually, I think I'm going to get-- let's make sure it's a float. Let's use the type casting trick just to make sure I don't accidentally shortchange someone and throw away everything after the decimal point. 

So it just escalated quickly, right? Average just got a lot more involved. It's not just a single one line of code, but now it's dynamic. I initialize a variable called sum to 0. In this loop, I go through and just keep adding to sum, which is initially 0, whatever's in array[i]-- or specifically array[0], array[1], array[2]. That gives me a total sum that I return, divided by the total number of things. 

Now, this I can tighten slightly. Recall that this is syntactic sugar for just adding things. I can't use plus plus because that only literally adds one. But I can use here, plus equals. 

Questions on this implementation here? Really the only takeaway-- or the most important takeaway is that this is the syntax for how you tell a function that it expects a whole array, not a single variable like an int or the like. You literally use square brackets, but you don't specify the length inside there. Yeah? 

AUDIENCE: What variable [INAUDIBLE] at the top? 

DAVID MALAN: What about the variable at the top? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Good question. What do I have it defined as at the top? This variable, N, it must be an integer if you're going to use it inside of an arrays square brackets here. 

So this line 10, notice, no longer says 3, it says N. And so whatever N is 3 or 4 or something else, that's how many integers I will get in that array. And it must be, by definition of an array, an integer that goes in those square brackets. 

And here's a common source of confusion. When you create the array, that is declare it, you use square brackets like this, where you put the total number of elements you want. When you subsequently use the array, like I'm doing here, you don't mention int again-- just like you don't mention int again and again once a variable exists. 

You use the square brackets still, but you don't use N. You use 0 or 1 or 2 or, generically here, i. So when C was designed, they sometimes used the same syntax for two different ideas or contexts. Yeah? 

AUDIENCE: Do you have to include line 6 [INAUDIBLE]? 

DAVID MALAN: Good question. Do I have to include line 6? Short answer, yes, because of the reason we ran into last week. C, or clang really, reads your code top to bottom, left to right. And so if the compiler sees some mention of this function average on line 16, but you haven't told the compiler that average exists, you're going to get an error on the screen. 

So the conventional way to do that is you just copy paste the first line of code from the function, it's so-called prototype or declaration. Yeah? 

AUDIENCE: Is there a library if you don't know the size of the array? 

DAVID MALAN: Really good question, and a perfect segue way. Is there a library you can use if you don't know the size of the array? No. And so if any of you have programmed in Java or Python or other languages, you can actually just ask the array, how big is it? 

In C, you and I, the programmers, have to remember it. And so short answer, no, there's no function that will just automatically do this for us. And in fact, let me make a more subtle claim that it's fine to use global variables like this if they're really for configuration options. 

Why? It's just convenient to put them at the very top of the file because everyone, you, your colleagues, your TAs are going to see them at the top of the code. But you really shouldn't be using them everywhere throughout your code. It'd be better if the average function, itself, were independent of that special variable. 

So by that, I mean this. You know what I should really do, if I really want to be well-designed? I should pass in the length of the array to the average function. I should give the average function a second argument-- I'll call it length, for instance, but I could call it anything I want. And so rather than putting N all the way down here at the bottom of my file, let me just dynamically say length instead. 

And this is a subtlety-- and no need to get too tripped up over this. But this, now, is just an example of how the same function can take not one, but two arguments. But indeed, in C, you must remember, yourself, what the length of an array is. You can't just ask the array via some syntax like you can, those of you who've programmed before in Java or Python. Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Good question. Would it be better designed to write a function that computes the size? Short answer, can't do that in C. As soon as you pass an array into a function in C, you cannot figure out its size if it's a generic array like that of integers. 

There are special cases that you can do that. But in general, no, it's just not possible in C. And if that's some frustration, honestly, this is why more modern languages add that feature. Why? Because it was really annoying, as I'm alluding here to not having that information. 

Now, just to make sure I didn't screw up anywhere, let me compile this final version of scores. Suspense. All good. ./scores, 72, 73, 33, and we're still back in business. 

So this version is more complicated. And as always, we'll have this version on the course's website for reference. But the point, really, is that arrays, not only can be used as containers to store multiple values-- three or more in this case-- you can also even pass them around as arguments, as such. 

All right, now besides that, let's simplify for just a moment, and consider now the world of chars. If we've just got single bytes, where does this lead us? And how does this get us, ultimately, to strings to solve problems like readability and cryptography and the like? 

Well here, for instance, are three lines of code, out of context, that simply store three chars. And you can already see where this is going. Having three variables called c1, c2, c3 is clearly going to end up being bad design because of all the silly redundancy here. But notice, I'm using single quotes like last week because these are single chars. 

What does this look like in the computer's memory? Well, it looks a little something like this. If we clear out the old memory, c1, c2, c3 probably will end up here, maybe not literally in the top left-hand corner. This is just an artist's rendition. But c1, c2, c3 will probably end up like that. 

Now, what's really there? It's really those same three numbers-- 72, 73, 33. But how many bits does a byte have? Just eight. So if we were to look at the binary representation of these characters, it would only be eight bits each. 

That's enough to store small numbers like 72, 73, 33. We're not dealing with Unicode and emoji and the like. But the point is the same. You don't have to use four bytes to store these numbers. You can use a different data type like chars, and underneath the hood, it's, indeed, going to use just single bytes for each. 

But this is sort of like a-- this isn't really how we implement strings, right? When you wanted to say, hi, last week, or this, we used double quotes. And we wrote all of the things together and used one variable, not three, right? When I typed in David, I didn't have a variable for D-A-V-I-D. I had one variable called name that stored the whole thing. 

So in C, we keep talking about these things called strings. We'll see, eventually, that strings are not necessarily what they seem to be. But for now, the key thing about strings is that they're variable length, so to speak, right? 

They might be three characters, Hi, or five characters, David, or anything smaller or larger. So how do we go about implementing strings, if all we have at the end of the day is my memory? Well, here is an example of just creating, declaring, and defining a string called s. s because it's just a simple string, and quote unquote, HI!, in double quotes. 

What does this look like in the computer's memory? Well, let's clear it again. And here, now, because it's technically stored in one variable, s, here is how I might draw it as an artist. It's three bytes in total-- H-I exclamation point. 

But there's no c1, c2, c3, it's just, the whole thing is s. But it turns out that a string, fun fact, is really just what underneath the hood? Kind of leading up to this-- what is a string, if this is how it's laid out in memory? 

AUDIENCE: An array. 

DAVID MALAN: Literally, it's just an array of characters. And we didn't have to know about arrays last week to use strings. This is where, again, the training wheels are starting to come off. But a string is just an array of characters. H-I exclamation point, for instance. 

So technically, an array-- or a string called s is really a variable called s that allows you to get at the first character with s[0], if you want-- s[1], s[2]. You can literally get individual characters just by treating s as though it's an array, which it really is underneath the hood, in this case. 

But there's a catch. How do you know where strings end? In the past, when I drew some integers on the screen, I know, I claim they always take up 4 bytes. If I had drawn a long, it always takes up 8 bytes. If I had drawn a character, it always takes up 1 byte. But how many bytes does a string take up? 

Yeah, I mean, that's kind of the right answer. In this case, three, it would seem. But if it's David, that's a good five characters. But where do we put the number three? Where do you put the number five, right? 

This is literally all that's inside your computer. This is all our building blocks in front of us. So how can we-- where does the three go? Where does the five go? 

Well, it turns out you can solve this in a couple of different ways. But the way humans decided to implement strings years ago is, indeed, an array, but they added one extra byte at the end of every such string array, just to make clear, with a so-called sentinel value, that the string ends here. Why? So that if you have two strings in the computer's memory like, HI! and bye, you know where the barrier is between the exclamation point of one and the letter B in the next, right? You need some kind of delimiter. 

And so what really is underneath the hood is this. When you store a string in memory, when you type in a string-- as the user, if you type in 3 characters, it's going to use 3 plus 1 equals 4 bytes in total. If you type in David, it's going to use 5 plus 1 equals 6 bytes in total. Why? Because C automatically adds this special 0 at the end of the string. 

I've drawn it with backslash 0 because this is how you represent 0 as a char, as a character. But this is literally just 0, as we'll soon see. So any time there's a string in memory, it always takes up one more byte than you, yourself, as the programmer or human typed in. 

In fact, if we convert this again, just for discussion's sake, to those integers, what's literally stored in the computer's memory is going to be 72, 73, 33, and now a 0. And the computer, because of C and how it was invented, it's just smart enough to know that when you print out a string, it prints out every character until it sees a 0, and then it just stops printing. In particular, printf knows how this works. And this is why printf knows when to stop printing. 

Decimal numbers are not that enlightening. We'll generally write the characters like this. And again, backslash 0 is just special symbology. It's what the programmer types to make clear that you're not saying, HI!, 0. You're saying HI!, and then it's a special 0. Specifically, it is eight 0 bits that indicate that it's the end of the string. Technically, that backslash zero, if you want to be fancy, it's called null, N-U-L-L. 

And it turns out, you've seen this before, though we didn't call it out. Here's that same ASCII chart from the past couple of weeks. If I highlight this, what is decimal number 0 mapping to? NUL, which is just programmer speak for the special null character. All 0 bits that means the string ends here. 

This all happens automatically for you. You do not need to create these null characters or these zeros. Any questions then, on this implementation thus far? Any questions here? 

No? Well, let me do this. Let me go back to VS Code in a second. And let's actually corroborate this with some code. Let me go ahead and create a small program called hi.c. 

And how about we do this? Let me include stdio.h. Let me include-- let me type out int main void, as always. 

And now let me do something simple and kind of bad, but char c1 equals quote unquote, h, in single quotes. Char c2 equals quote unquote, I, in single quotes. And lastly, char c3 equals exclamation point, in single quotes. 

And now, let me just print this out. I can't use %s because that is not a string. That's literally three chars, because that's the design decision I made. But I could do this-- %c, %c, %c, which we haven't seen before, but %s is string, %i is int, %c is, indeed, char. So let me put a backslash n at the end for cleanliness, and now do, c1, c2, c3. 

So this is like a char-based version of printing string. So let me make HI! And then let me do ./hi, and it looks like I used printf with %s. But I did things very manually by printing out each individual character. 

What's cool now, though, is that once you know that characters are just numbers and strings are just characters, you can kind of poke around. Let me change all three placeholders to %i instead. And this is totally fine, too. 

Let me rerun this, make hi. Actually, let me make one change, just so we can see this. Let me add spaces, just for aesthetics sake, let me do make hi, ./hi, Enter, and voila, like now, you can actually see the numbers, that I claimed back in week zero, were in fact happening underneath the hood. 

Well, this is not how you would make strings. It'd be incredibly tedious to have three variables for three letter words, five variables for five letter words. We've been using, of course, strings since last week, so let's do that instead. String s equals quote unquote, double quotes "HI!" For this, no, because of these training wheels, I need to include the CS50 library. But we'll come back to that in the coming weeks. 

But for now, I'm going to go ahead and create a string s called quote unquote, "HI!" And now I'm going to change this to be my familiar %s, and now just print out s itself. This, of course, is the same thing as last week, ./hi, gives me the exact same thing, but now, we're dealing, of course, with strings. 

But how can we see a little beyond that? Well, how about this? Let's poke around further with today's primitives. 

Even though s is a string, I could technically print out its first character with %c by doing s[0]. I could technically print out its second character with %c by doing s[1]. I could print out its third character with %c and printing out s[2]. 

So again, this just derives logically from my understanding now that strings are arrays, as you note. Let me do make-- let me do make hi, ./hi. And no visual change, but I'm just kind of now tinkering around. 

And in fact, if you're really curious, let me do this. Let me change these back to i, back to i-- oops, back to i. And let me add a fourth one because if I'm really curious now, let's see what's in s[3]. This is the fourth byte. And even though the string itself is H-I, I think we can corroborate this whole null thing. 

Make hi, ./hi, Enter, and there it is. You could have done this last week, if you really wanted to geek out on strings. But for now, it's just revealing what's going on underneath the hood. Questions then, on what these strings are? Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Why do we need the bracket? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Why do you not need brackets? Good question. Why do I not need brackets on line 6? Because s is a string. 

We'll see in a couple of weeks that s is, essentially, implemented underneath the hood, indeed, as an array, but that happens automatically for you. You can treat s as just a variable name without square brackets. You will use square brackets when you have arrays of ints or you manually create arrays of chars or doubles or floats or anything else. 

But strings are special. Why? I mean, every program you write seems to use strings, text in some form. We're humans we like text, not just numbers and such. So this is just treated a little specially in C and many other languages as well. 

Other questions on this here? No? Let's add then, one other string to the mix. So instead of just saying, HI!, why don't we consider a version of the program that says both, HI! and BYE!. And I claim now that that backslash zero, that null character is going to be ever more important now if we've got two strings in memory, so that C knows how to distinguish one from the other. 

So let me go ahead and just get rid of these two lines for the moment. Let me recreate string s equals, quote unquote double quotes, "HI!" Let me give myself another one. And because I'm just playing around, I'll choose very short variable names. String t equals quote unquote, "BYE!" And then let me just print them both out. 

Let me go ahead and print out %s, backslash n, comma s, and then printf %s backslash n, and then t. So very simple demonstration of just these two variables. Make hi, ./hi, and of course, it prints out two lines, one after the other. 

What's actually going on underneath the hood? Well, let's go back to the computer's memory. HI!, I think, is going to be, I claim, pretty much the same. So s, I'll claim, is in the top left, followed by the backslash zero. And that's important now because BYE! probably is going to end up there. And visually, it wraps just by nature of how I've drawn this grid of bytes, but it's contiguous. B-Y-E-! null, A.K.A. backslash zero, this is now helpful to printf because now printf knows where one begins and ends by way of that special null character. 

But we can poke around now, too. What else can I do here? How about this? How about I go into my code here, back to VS code, and let me go ahead and say something like, well, if I've got two of these strings, you know, let's put them in an array. 

Let's kind of do this sort of arrays in arrays, sort of inception-style here. So string words[2]. So give me an array of two strings is what I'm saying here in code, even though we've not done it with strings yet. We only did it with ints. 

And now let me do this. The first word A.K.A. words[0] will equal, as before, HI! And now words[1] will equal quote unquote, "BYE!" 

And now I've done the exact same thing, but again, I'm just avoiding having s, t, q, r, and all these different variables in my code. I just now am treating them as one single array of strings. How do I change my code down here? Well, if I want to print the first word, I do words[0]. And if I want to print the second word, I do words[1]. 

This is not a useful exercise at the moment because I'm just making my code more complicated. But again, it allows us to poke around and see what's going on because there is that HI! and BYE!. But watch this. If I really want to be cool, I can do this. 

Let's print out %c, %c, %c, backslash n, and then here, %c, %c, %c, %c, so four of those. And now here's where things get interesting. Words is an array of strings. Again, if I may, what's a string? An array of characters. 

So just use the same logic. If words is an array of strings, you get at the first string with words[0]. How do you get at the first character in the first string? Bracket 0, words[0][1], and lastly, words[0][2]. 

And now down here, words[1], but the first character is there. Word[1], the second character is here. Words[1], the third character is here-- whoops-- third character's here. And words[1], the fourth character is here. 

This is not how people program. This is only for demonstrations sake. My God, it's so tedious and verbose already. But if I make hi now, ./hi, now, I'm manually reinventing %s, if I forgot it existed, using %c alone. But you can indeed manipulate arrays in this way. But because strings are arrays of characters, you can manipulate strings in this way too. 

Any question now on this syntax? Any questions here? No? No? 

All right, well, let's go ahead and propose that we solve a couple of other problems we might not have as before. But first, a quick visual of what's been going on underneath the hood here. If here, again, is where we left off on the screen, HI! and BYE! back to back, here is really how I just treated these things. s bracket 0, 1, 2, 3 and then t 0, 1, 2, 3, 4. 

But really, once I put them in an array, the picture becomes this. Words[0] is the whole HI!. Words[1] is the whole BYE!. But if I really get into the weeds and start indexing into individual characters in those strings, all I'm using is new syntax in order to represent these same values here. 

Questions then, on these representations before we forge ahead? No? Yeah? 

AUDIENCE: Does the new line character not [INAUDIBLE]? 

DAVID MALAN: Does the new line character-- say that once more? 

AUDIENCE: Does the new line character take up any space? 

DAVID MALAN: Ah, really good question. Does the new line character take up any space? It does, so far as printf is concerned. But I'm not storing the backslash n in my strings, printf is being manually handed that thing instead. 

All right, so let's go ahead then and consider how we might solve some problems that have arisen now with these strings, as follows here. Suppose I-- let's do this. Let me go back to VS Code here. And let me go ahead and open up a new file called, how about, length.c. 

And let's consider for a moment how I might actually figure out what the length of a string is, which is distinct from the length of an array. I claimed earlier, you cannot figure out dynamically what the length of an array is. But I can figure out the length of a string, specifically, because of this implementation detail of that null character. So let me go ahead and do this. 

Let me include cs50.h in this second program here. Let me include stdio.h, as before. And let me do this, int main void-- and the first thing I'll do is just get a string from the user. I'll ask the user, as always, for their name. 

So I'll call getString, and say, what's your name, question mark, as always. And then down here, if I want to figure out the length of this string and print the length out on the screen, well, I can kind of do this similar in spirit to the average, where I'm accumulating something. 

Let me go ahead and initialize N to 0. Let me give myself-- it's not a for loop because I don't have a-- I don't know in advance how long it is. But what if I do this? 

While the value at name[n] does not equal '/0'-- crazy syntax at the moment, but it's just the culmination of these various building blocks. Let me just finish the thought here, n++. 

And then down here, let's just print out, with printf and %i, that value of N. So I claim this is going to show me the length of any string I type in, whether it's hi or bye or David or anything else. I initialize a variable to zero, and that's good because that's where you start counting in general. 

While name[0] does not equal backslash zero. What is this saying? Well, if name is the string the user typed in-- and name is just an array, as you noted-- the name[0] is going to be the first character. And I'm asking the question, well, does the first character not equal backslash zero? 

And if I type in David, D, it's not, so I keep going and I add 1 to N. Then I'm going to check name[1]. Well, if I typed in David, name[1] is going to be A. A does not equal backslash zero, and so it's going to go again and again and again. 

But five steps in total later, it's going to get to the byte after D-A-V-I-D, realize, wait a minute, that is a backslash n. The loop finishes, and I print out the total length. Arrays, in general, do not have this null character. However, strings do. Again, strings are special versus all of the other data types we've talked about thus far. 

But how could I, for instance, do this differently? Well, let's actually factor this out as a function, as I've commonly done. But rather than implement it myself, you know what? 

It turns out what's nice about strings being so common, there are many other people who have solved these problems before. And in fact, there's a whole string library in C. It is used by way of a header file called string.h. And what string.h is, is a library of string-related functions. 

In fact, you can see in CS50's manual pages for C, the string.h functions, at least those that we recommend as most useful, and in particular, if you poke around there, you'll see that there's a function called strlen. It means string length. It was named very succinctly, just because it's a little easier to type than string length. But strlen tells you the length of a string. 

So how might I use this in my code here? Well, it turns out, I can simplify this quite a bit. Let me get rid of my loop, get rid of my accounting manually, and do something like this-- int n equals strlen of the humans name, name. And now I'll just use printf, as before, with %i backslash n, and output the value of n. 

But there's a bug at the moment. What have I forgotten to do? Yeah, I have to include the header file at the top of the screen, so let me-- at the top of the code. So let me also include string.h at the top of my file, so that C knows that, in fact, strlen exists. 

Let me go ahead and make length, as before. ./length-- or actually, really for the first time, what's your name? D-A-V-I-D. And hopefully, I'm going to see, in fact, 5. 

By contrast, if I run it again and type in HI!, now I see three. So strlen is just one of the functions in that library. And there are so many more. 

In fact, yet another library that might be useful moving forward is this one, ctype, which relates to C data types and lots of functions therein that can be useful. For instance, if you review its documentation in the manual pages online, you'll see that there are functions via which we can solve problems like this. Let me go ahead and propose here-- let me see. 

Let's do an example here involving-- how about checking if something is uppercase or lowercase, and converting it to uppercase only. Let me go back to VS Code, and code a program called uppercase.c. In this, file I'm going to start by including now, as always, cs50.h. I'm going to include stdio.h. And I'm going to add one other to the mix, which is string.h now too, so I can access the length of things as needed. 

Int main void comes next. And then within my main function, I'm going to go ahead and declare a string called s. I'm going to call getString, as before. And I'm going to go ahead and just ask the user for a string called before. 

I want to do a before and after. Whatever the user types in is before. But I want to force everything to uppercase, thereafter. Let me now, in this loop here, do this. Let me printf quote unquote, "After," just so we can see this on the screen. 

And let me do four int i gets 0, i is less than strlen of s, i++. What am I about to do? I'm about to iterate over every character in the string from left to right, from 0 on up to, but not through, the length of s. 

And how do I check if something is lowercase, so that I can actually force it to uppercase? Well, it turns out, I could do this literally. If the character in s at location i is greater than or equal to capital A, ampersand, ampersand, which means and instead of or, which we saw in the past, s[i] is less than or equal to little z, that means, logically in English, that this is indeed lowercase. 

How do I now convert it to uppercase, this character? Well, I could just literally print out the same character. But that would not be the answer here because that's not changing the value. But what could I do instead? 

Well, let me actually pull up here real fast the ASCII chart as before, and let's see if we can't glean some insight. If I pull up the same ASCII chart, and suppose the human has typed in a lowercase a, that's 97. What letter-- I want to convert it to uppercase A, so what number do I want to convert the 97 to, per week zero? So 65, we keep coming back to that one. 

What if the user types in lowercase b? I want to change the 98 value to 66, and so forth. And any quick math, how far apart are those? So it's always 32, like uppercase to lowercase is always, wonderfully, good design, 32 away, one from the other. 

So what does this mean? Well, I think we saw earlier that underneath the hood, a char is just a number. You can certainly do arithmetic on it. And here, again, if you understand these lower level primitives, what if I do this? Whatever s[i] is, if I know on line 13 that it's lowercase, do I want to add or subtract 32? 

AUDIENCE: Subtract. 

DAVID MALAN: So I want to subtract because I want to go from like 97 to 65 or 98 to 66, so indeed, if you do some quick math, that gives you 32. So it's suffices to just treat chars as numbers, subtract the 32, and printing it with %c, I think, will just convert lowercase to uppercase. If you now fast forward to the real world, Microsoft Word or Google Docs, if you've ever chosen the menu option that forces things to uppercase or lowercase on occasion, literally, that's what Microsoft and Google have done. They iterate over every character in the document, check if it's lowercase, and if so, they subtract 32 from it and show you the new value. 

What if, though, it is not a lowercase letter? I think I can keep it easy and just print out the current letter unchanged, if my goal is to simply force things to all uppercase, and that letter, then would be s[i]. So let me go ahead now and make uppercase, hopefully, no errors. ./uppercase, and I'll now type in David with an uppercase D, but lowercase everything else. 

But now the after version is DAVID-- an aesthetic bug. Notice here, I forgot to include, just for prettiness sake, a backslash n at the end. No problem, I'll add that. Let me fix my mistake. 

Make uppercase, ./uppercase, Enter. D-A-V-I-D, Enter, and voila. And I deliberately added another space after, just so they would line up pretty, even though before and after have different numbers of letters. Questions then, on this implementation of forcing something to uppercase, which in and of itself is not all that enlightening, but is representative now of how you can leverage these low level primitives. Question? 

No? All right, well, this honestly is tedious. My God, like does Microsoft, Google, everyone, you have to literally write out this code just to do something simple? Well, no, that's, again, why we have things like libraries. And increasingly now, for problem sets, projects, and beyond, well, you just use libraries more often off-the-shelf so as to solve problems that, surely, other people have had before you. 

So how can I now use this library, ctype.h? Well, let me go back into my code. Let me include this among my header files here. Just so I can skim things easily, I tend to alphabetize my headers. But that's not strictly necessary, but it allows me, at a glance, to realize, did I or did I not include something I need? 

Now, let me go ahead and do this. It turns out if you read the documentation for the C type library, there's a function, wonderfully called, if islower, that takes in a character as its argument, essentially, so s[i]. And if that returns true, a Boolean value, if you will, well, I'm going to force it to lowercase. 

But I don't have to do this math anymore. Turns out, in the C type library, there's also a function called to upper that takes a character as input, like s[i], and it just does the math for you. So that you can abstract away the 32 thing, and just know that someone else has solved that problem for you. Otherwise, I can leave my code unchanged down below because I'm not changing anything else. 

So if I do make uppercase now, and then ./uppercase, D-a-v-i-d, with just a capital D, and now it still works. But if you read the documentation further, it turns out that to upper is smart. If you pass in a character to to upper, that's lowercase, it obviously converts it to uppercase by doing that math. But if you pass in a character to to upper that's already uppercase, the documentation you would see tells you that it leaves it unchanged. 

So I can tighten all of this up. I can get rid of the whole else. I can get rid of the whole if, and arguably now, implement a program that's just as correct, but better designed. Why? Fewer lines of code easier to read, lower probability of mistakes, assuming the library is correct. It just makes it easier and faster for me, now, to write code. 

So if I now do, one last time, make uppercase, Enter, ./uppercase, and type in my name, still working. But now notice, we've whittled this down to far fewer lines of code, albeit, using now this additional library. Questions then on how we did this? 

Well, even though this code, I daresay, is correct, it's not necessarily well-designed just yet. In fact, there's one line of code, one function call in this current implementation that's more inefficient than it needs to be. And allow me to draw your attention to this here, line 10, wherein we're calling strlen. But we're calling it inside of this for loop, specifically, inside of the condition. And why might that not necessarily be the best idea? 

Well, is the length of the string as changing, ever? I mean, certainly not within the span of this loop. And so here we are within our for loop on line 10, 11, 12, and 13, asking on every iteration that same question. What's the length of s? What's the length of s? What's the length of s? 

And in turn, we're calling strlen every time, even though we're getting back the same answer. So I daresay a better solution here would be to maybe figure out the length of s earlier on in my code, and maybe declare a variable. Or perhaps do something that's syntactically a little more elegant, and in fact, a very common design in a loop like this, would be to declare not just one variable like i, but to actually declare a second variable called n, for instance, where n is just some number, set n equal to the length of s. 

But thereafter, inside of this condition, instead of calling strlen of s again and again and again, what might I now do? I could instead just compare i against n itself, because n now will only be calculated once when it's initialized, just as i is initialize to zero. And thereafter, we're going to be comparing i, which is changing, against n, which will not be. So it's going to be marginally more efficient by design. 

Now with that said, a good compiler could also recognize that there is this optimization possibility, and maybe do it for us. But for now, best to get into the habit, best to develop the muscle memory for making those better design decisions yourselves. Questions, then, on how we did this? No? 

All right, a few final building blocks for the day. So we started by talking about those command line arguments that clang uses, whereby, anything after the command that you type at a prompt, be it make or clang or even CD in Linux, any word thereafter, or something cryptic like -o is a command line argument. It's an input to the command. It's different from a function argument because a function argument, of course, is an input to a function. 

But it's the same idea. It's just different syntax after the dollar sign at the prompt. Well, it turns out that command line arguments are something you can now use in your own programs by accessing words after the prompt. And let me propose that we invent this as follows. 

Let me propose that we switch back to VS Code here, and I'll open a new file here called greet.c. So in greet.c, it's going to be a program that very simply greets the user. Had we written this last week, we would have done this. Include cs50.h, and then include stdio.h, and then int main void, and then we might do something simple like string name equals getString, quote unquote, "What's your name?" 

And then we would have printed out, as always, Hello, %s, and then plugging in that name. So this is the same program we've implemented many times, just to make sure it works-- although, nope, that's not quite the same program. Semicolon's in the wrong place. 

This now is the same program. So make greet, dot ./greet, and I'll type in my own name. hello, David. So we're back there. 

Now, what's arguably a little annoying about this program, if I type in something else like, Carter, Enter, I have to run the program, wait for the prompt, type in my name, hit Enter. And that's fine, but imagine if every program worked like this. Like make, suppose you could only type make, then you wait for a prompt, then you type the name of the program you want to make, then you hit Enter. 

Or worse, in Linux when you have to change directories, as you might have for problem set one, what if you had to type CD, Enter, now type the name of the folder you want to change into, Enter-- I mean, it just slows life down. And so it just gets annoying quickly. So command line arguments just let you express your whole thought all at once. 

So how can I do this? Well, if I want to express the notion of command line arguments in my code, I could do something like this. I could, for the very first time, go up and get rid of this void, which as of today means, this program takes no command line arguments. And I can change it to exactly this. Int argc, string argv, with brackets. 

Now it's cryptic, admittedly. And let me zoom in. But I think we can perhaps infer now, what's going on. If main now does not have void as its input, which means it takes no arguments, surely, the spoiler here is that now main will take command line arguments somehow. 

Any guesses as to what argv is or will be? What might this represent? It's an array of strings, right, by way of the syntax. Yeah? 

AUDIENCE: All the characters will be typed out. 

DAVID MALAN: Exactly. It will be all of the characters, or really all of the words that you type at the prompt. Argc, as an int, any guess? Argument count is what it generally stands for, though technically, you could call these things anything. But this is the convention. 

Because I claimed earlier that arrays don't keep track of their own length, if you want to know how many words the human typed at the prompt after your program's name, you have to be told, not just the array of the words, but the length of that array. The strings, you can figure out the length of using strlen, but you can't figure out the length of the array of strings, the collection of words that the human typed in. 

So how can I now use this? Well, let me go ahead and do this. Let me go ahead and change this program now just to be printf, quote unquote, "hello, %2 /n", then argv[1]. So this is not the best version of my code yet, but it's my first. 

Make greet, and now let me do ./greet, David all at once. Enter, hello, David. Now let me run it again, ./greet, Carter. Enter, hello, Carter. 

It's a marginal improvement, but I don't have to wait for getString to prompt me to hit Enter. It's just speeding things up, twice as fast. One less command to type in. 

But I deliberately did [1], but what's the beginning of argv? It would be [0]. Well, what's that? 

This is sometimes useful, though for now, it's not. Suppose I recompile my code and run this program now, greet David. Anyone want to guess what's in argv[0]? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Say again? 

AUDIENCE: Greet, hello. 

DAVID MALAN: Greet, Enter, hello, ./greet. So if you want to sort of inception style your program to figure out what its own name is, or at least how it was executed at the command line, at the terminal, you can look at argv[0]. In general, probably not that useful, probably better to start looking at [1], which was the first word after the program name. 

And if there were more, I could do this how about argv[2], let me add in a second %s. Let me recompile greet. Let me do ./greet David Malan, Enter, and that, too, now works, taking in two words at the prompt. 

If I really want to be smart at this now, I could do something like this, though. How about if the count of arguments, A.K.A. argc, equals equals to, then assume that the human typed in only their first name, and do printf hello comma %s /n, and then argv[1]. Else, if the human did not provide exactly two arguments, the name of the program and their own name, let's just print out a default value, lest they forgot their name or they typed in two names or three names. Let's just do, hello comma world as a default. 

And we'll just ignore what the human typed in. If I recompile this, make greet, I can do ./greet and David again, Enter. Oops-- sorry, what am I missing? Yeah, so newbie mistake. Else, all right, make greet again. ./greet, David, Enter, there's my hello, David. 

But if I omit my name, I just get the generic, like a default value. And if I get a little curious and I type in both names, then I get ignored too. Why? Because I just haven't built in support for argc of three. I could do anything I want, but now we have access to these kinds of building blocks. 

All right, what else might I do here? Well, it turns out there might be some final features for us to now execute. Notice, though, that in C, despite what you might see in books or online tutorials, nowadays, the two official formats for defining a main function are either this, which we've been using now for two plus weeks or now this, whereby, you change the void to int argc, and then for now, string argv, and then empty brackets. 

And we'll see that this, too, is a simplification, some training wheels if you will. But for now, those are the two forms, even though you will see in online tutorials and even books, some people use main in different ways. These are the two now to keep in mind. And I'll note that these command line arguments are kind of all over the place. Didn't probably expect to see this word on the screen here. 

And what does it mean? Well, it turns out that for decades-- there's actually this program that comes with Linux systems in particular called cowsay. Why? Probably because someone had too much free time once and decided to write a program that creates ASCII art out of a cow saying something textually on the screen. But you use cowsay, just for fun, by way of command line arguments. 

So for instance, let me propose that I go back to VS Code here, not because I want to write any code, but I just want to use my terminal window. And let me maximize my terminal window here. And let me go ahead and type in something like, how about cowsay, space moo? 

So cowsay is not a program I wrote. It's been around for decades. But we installed it in VS Code for you in the cloud. It takes at least one command line argument. What do you want the cow to say? 

I can say, cowsay moo, and hit Enter, and voila, there is my ASCII art of a cow saying moo on the screen. It can say multiple words. So I can say, Hello, world, Enter. And now it says, Hello, world. So this is just an example of a silly program that uses command line arguments, but it takes others too. 

Just like clang, use this convention of hyphens to change the output of the program. Dash something is just a super common convention with command line arguments when you want a very terse notation for some option like output. In cowsay, I read the documentation, and it turns out there's a dash f command line argument that allows you to change the appearance of the cow, if you will. 

So if I do cowsay dash f, duck, and then some other word like quack, it's no longer a cow. That command line argument turns it into a tiny, adorable duck instead. And then lastly, just for fun, because I spent way too much time playing with command line arguments. Cowsay dash f, dragon, and then how about, rawr, Enter, you can even get this on the screen here. 

So this, too, is just an example of what you can do with these command line arguments now that we have this building block. And there's one final thing we can now do with code. There's one last feature today that we'll introduce before we now connect all of these dots to readability and encryption by talking, lastly, about something called exit status. It turns out that whenever your main function exits, it returns a secret integer that you can figure out, as the programmer or an advanced user, what it was. And these exit codes, exit statuses, are typically used to indicate errors. 

So for instance, over the past couple of years, if you've used zoom and you ever got some kind of error, you might have seen a screen like this. It's usually not that helpful, maybe tells you to click Report Problem or Contact Support. But very often in our human world on Macs, PCs, and phones, you see cryptic error codes, like literally numbers that probably only Zoom knows, or Microsoft or Google or whatever company wrote the software you're using. But that number corresponds to a specific error that some human somewhere knows might very well happen. 

These are used similarly, although under a different name that we'll talk about later in the term, on the web as well. Have you ever seen this-- maybe not character, but number? So, 404 means what? 

AUDIENCE: Error. 

DAVID MALAN: So error, yes, but really, not found. So, why? I mean, this is the most arcane thing. And we'll talk in a few weeks about what this and other numbers mean, but numbers are all around us in technology, and they very often mean something to the technical people who wrote the software, less so to humans like you and me. 

Why so many of us recognize 404 is kind of weird, that like that's been around long enough that we all know it. But it really is just a special number that represents an error of some sort. So it turns out, the last thing we'll reveal today about what we've been taking for granted for two weeks, is what the int is in main. 

We've seen, just a moment ago, that the thing in the parentheses, which up until now has been void, which means no command line arguments. now int argc string argv brackets just means, yes, command line arguments. And we've seen how to access them. So the last piece of the puzzle, honestly, of all the cryptic syntax the past two weeks, is just what int means. Int is always there for main, and it indicates that main will always return an integer, even though you and I have never done so explicitly. 

Usually, main returns 0, by default. But it would be weird if you saw an error message saying 0, so 0 is just hidden. You would never see it on the screen. But it's happening automatically by way of how C is designed. So let me write one final program here. I'll call it, for instance, status.c to show you these exit statuses. 

Code of status.c, and then up here, let me do something simple like include cs50.h, then include stdio.h, and then int main-- actually, let's use a command line argument. int argc, string argv[], so that's copy, paste. But now let's do this. 

If argc does not equal to-- why don't we do something like this? Let's not just default to hello, world like last time. Let's yell at the user. So let's say something like printf missing command line argument, so that they know they screwed up and they need to run the program again correctly. Else, let's go ahead and say, print out, as before, Hello, comma %s, and then plug in argv[1], so the human's name from the prompt. 

Now at this point, let me go ahead and run status, ./status, and I'll type nothing first. I get yelled at. This time, I'll type it again. ./status David, and it works properly. 

But now let me show you a somewhat secret, cryptic command. You can type this at your prompt, and it's just a coincidence that there's another dollar sign. Echo $?, totally arcane, but it allows you to see what exit status your program has ended with. So let me run this again the wrong way. 

./status, I get the error message. What was secretly returned? I can't see it. There's obviously no error screen, but by typing echo $?, I can see that, oh, my program automatically, by default, returns zero. 

However, if I run it again correctly, ./status David, Enter, this is the correct version. But if I run echo $? status again, it's still entered with 0. And long story short, this is just a missed opportunity. When something goes wrong, why don't I return a value other than 0? 0, by default, means success. And it's always there automatically. 

But you can control this. I can go into my code here and return 1, else, if something works fine, I can return 0, by default. And honestly, if I omit the return zero, again, zero automatically is returned. So let me go ahead and go be explicit, just so I know what's going on. 

Make status again, ./status, and let's do this correctly with David. Enter, hello, David. Echo $?, zero. So all is well. But now if I do ./status and nothing, or multiple things, but not just David, Enter, I get the error message. But now if I do echo $?, voila, there now is the one. 

So what does this now mean? This is, in the graphical world, we would just show something like this on the screen, which is a little more informative to the user. But even in the Linux world where you don't have a GUI, necessarily, even for the programs we've written, you can check these exit statuses. And in fact, more comfortable, more advanced programmers, when they write code that calls programs, be it cowsay or anything else, you can encode, check what the exit status is of a program, and then decide, did my program work or did it not? 

And now let's connect the final dots before we adjourn for some fruit snacks. Cryptography, namely one of the applications this week via which you'll be able to send, if you will, secret messages, and better yet, decrypt secret messages. This will be in addition to perhaps analyzing the readability of text using heuristics, like we identified at the start of class two. 

So cryptography is just the art, the science of encrypting information, scrambling information so that if you have a secret message to send in so-called plaintext, you can run it through some algorithm and turn it into what's called ciphertext, thereby, encrypting it. And only someone who knows what algorithm you've used and what input you've used to the algorithm, theoretically, can decrypt that process and convert it back to the original message. So if we use our mental model from last week, here is a problem. Here is an input and output. 

The goal I claim here is to take some plain text, like the message you want to send, think back to grade school if you ever passed a note to a friend or to your crush saying, I love you, it's a little awkward if the teacher or someone else intercepts the paper. And in English, it just says, I love you, or whatever it is. It'd be nice if you had at least encrypted it in some way. But the other person needs to know what algorithm you used and what inputs you use to that algorithm so that, ultimately, they can decode the so-called ciphertext, which is the output. 

So what goes inside of the box today? Well, an algorithm, as it relates to cryptography, is called a cipher. And a cipher is a fancy name for an algorithm that encrypts text from plaintext to ciphertext. The catch is, there needs to be not just the algorithm, there needs to be an input to it. 

And so, for instance, you might draw the picture like this for the first time today. And we've seen this in code. You can give multiple inputs or arguments to functions. So in this black box, can you imagine passing in the message you want to send, and then some secret. 

So for instance, suppose that, the simplest thing I could think of as a kid was instead of sending the letter A, why don't I write the letter B? Instead of the letter B, why don't I write the letter C? So I can kind of shift the English alphabet by one space. So A becomes B, B becomes C, dot, dot, dot, Z becomes A. You can wrap around at the end. And let's assume no punctuation in this part of the story. 

So that's a very simple algorithm-- add a value to each letter and send the value as the ciphertext. And now the teacher, the classmate, they have to know that you use, not only this rotational algorithm, also known as a Caesar cipher, they also need to know what number you use. Did you add 1 to every letter, 2 to every letter, 25 to every letter? 

Now if they're super smart and probably not the young age in this story, they could also just try all possibilities. And that would be an attack on the algorithm. This is not a sophisticated algorithm, but it's enough to send a message in class. 

So if the two inputs now are HI! as the plain text message, and 1 as the so-called key, the secret number that only you and the other person know, you might be able to encrypt a message from one way to the other. And so in this case, for instance, HI! would become I-J-!. In this version of the algorithm, we're not going to bother with numbers or punctuation. We'll only operate on A through Z, be it uppercase or lowercase. 

So now if you were to receive a slip of paper in class with I-J on it, you, the recipient, would know what it is so long as you know that the sender used one, because you just reverse the algorithm and you subtract one instead. The teacher, they probably don't know what this means, and they're not going to spend time hacking the message, so it just looks scrambled to them. And that's what we get from encryption. Someone who intercepts it, be it in class or in the real world, on the internet or anywhere else, can't actually figure out, ideally, what it is you have sent. 

The opposite, of course, is indeed called decryption, but the process is the same. We now pass in negative 1. And so how about this? Why don't we end with a demonstration here? UIJT XBT DT50-- there's a bit of a tell there. If we pass that in and do negative 1, well, how do we get out the plaintext originally? 

Well, if this is the ciphertext, and we subtract 1 from each letter, I think U becomes T, I becomes H, J becomes I, T becomes S, X becomes W, B becomes A, T becomes S, D becomes C, T becomes S, and this was, indeed, CS50. Have a duck on your way out, and some snacks in the lobby. 

[APPLAUSE] 

[FILM ROLLING] 

[MUSIC PLAYING] 
