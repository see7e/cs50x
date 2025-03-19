---
title: SECTION2 - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

CARTER ZENKE: All right. Well hello, everyone. It is so wonderful to see you. My name is Carter Zenke. And I am the course's preceptor. I'm joined here by all of you all. So all that we do is just take a minute to unmute and do something unusual for Zoom, which is say hello all at the same time. So on the count of three, I'd like to invite you to unmute and say hello. One, two, three, and 

AUDIENCE: (IN UNISON) Hello! 

CARTER ZENKE: Amazing. So it's good to have this nice chorus of voices here today. Everything we'll do today is here at this URL right here, CarterZenke.me/section. You'll find all of the slides we'll work on. The exercises we'll work on together. If you like to get in touch with me in particular, you can email me at Carter@cs50.harvard.edu and feel free to email me there. 

So I thought we'd start off with, it's just a kind of refresher on lecture. And so I invite you to think back to two questions from this week's past lecture. The first is, what did you find exciting from lecture? What are you interested in? And next is, what are you still confused about or what do you still have questions about? So take a minute to think about those two questions, again, what are you excited about and what you still have questions about? And we'll come back in maybe 30 seconds or so and share out a few of these ideas here. So we'll come back in 30 seconds. 

[MUSIC PLAYING] (SINGING) Need to close your eyes here too, and I at the time doesn't matter, we don't care about the others. You stay on my mind because you know you're my lover. Oh, baby you'll love it and I can't ignore it. A light and you can notice, my body gets carried away. I know what it is, yeah. You know the feel of me. All right. All right. And I don't want to leave. Talk, tell me maybe what you would do. 

Dance, dance. And wear your feeling's high. So hot. So hot, so hot. 

CARTER ZENKE: All right. So I think that'll be enough time to do some thinking on this past lecture this week. I hope you don't mind if we do a few warm/cold calls to get a feel for what we're interested in, what we're wondering about this week. So if you wouldn't mind, can I go to maybe Elena and ask you what you find exciting, what you are still wondering about this week? 

AUDIENCE: So I think this week, something that was pretty interesting was I thought the section about debugging was pretty interesting. I definitely had to do a lot of that for my presit. I'm not really wondering so much so far, I think. I think we kind of just getting intro to things, but yeah. 

CARTER ZENKE: Yeah, that's good to hear. So some interesting debugging and how we do that. Well, I think we'll do a little bit of that today in section, write some programs and hopefully de-bug the errors we'll find in them and maybe could we go to Dewey, if you don't mind. Maybe something you're interested in or things you're wondering about? 

AUDIENCE: Yeah, no problem. I guess, like, the most interesting thing from the lecture this week was actually the command line arguments. So I've programmed before, but I've never actually used command line arguments in a program that I've made. So that was actually really cool. And then what I'm looking forward to, I guess, just working on some more complicated assignments because those tend to be quite fun. So yeah. 

CARTER ZENKE: Yeah, yeah. Very cool. So we saw command line arguments which, again, are these inputs to your program that we can type in the terminal itself before your program runs. And those then decide how the program will run, gives it some options to work with as it runs. Just a few questions for us here today as well. Something we'll talk about in section today are, what are the steps involved in compilation? So we take the source code, this code written in C and convert it to binary. But how do we do that and why do we do that? 

We'll dive deeper into arrays, what are they? Why would we use them? We'll talk about strings, particularly in the context of arrays. And finally, to Dewey's point earlier, we'll talk about command line arguments as well. And throughout this, we'll hope to figure out what makes for good design. In this course, we'll talk about correctness, which is, does your code work, but also about design, which is how well does your code work? So we'll figure out what good design looks like in a few different contexts here. 

Kick things off with compilation though. We saw this program in lecture, if I can go to full screen here, and can have somebody just shout out what would this program do? If I were to run this program, what would you see on your screen? Maybe could I ask McKenna, if you don't mind? Do a warm/cold call. 

AUDIENCE: Yeah, you were just saying "hello, world". 

CARTER ZENKE: Yeah, just saying "hello, world", right? And go back to this here. Now if we were to compile this from C to machine code, to binary, we'd have a few steps along the way. So we saw this lecture. We saw that this source code first gets converted to assembly code, this kind of esoteric language here that isn't quite binary, but is almost there. And in the next step, we end up getting down to this binary that your computer actually runs. 

So we have this maybe, Hello.C file that then gets converted to this regular hello file that's written in binary here. And to do this, we have this program called Clang, or C-language, C-language compiler here. And if we were to run Clang like this, we would probably need to provide a little more context for Clang because Clang wants to actually take some source code and convert it to machine code. But here, it wonders what source code should I convert to machine code. So we might use an example of a command line argument here and actually tell it what we want to convert. We can type Clang hello.c to tell it we want to convert this hello.c file down to binary. 

But we could also be more specific. We could say, I want not just the a.out we would get from this we saw in lecture, but more specifically, a file called "hello". So I could say "clang-o" and then "hello" to say this is the output file I want. And then finally, the hello.c file we would actually want to compile from source code to machine code here. And all of this can get a little bit complicated, this isn't the full command we need to compile all of our saved programs. We might want to link in some libraries. And there's a lot of other things you might type here to make your compilation successful. 

So what we've done is we've given you this command called "make" that sort of simplifies a lot of that for you. So "make" runs in the background. Clang, along with a lot of options behind the scenes to compile your program to binary, ultimately. But in this class, and even if you do more programming in the future, you'll probably use a command called "make" to simplify that and keep yourself from typing all this stuff in the terminal as you go. Now what questions do you all have on compilation, or on converting from source code to machine code, if any? 

All right. So seeing none here, and I imagine you've gotten to do this a little bit so far in the class. So let's dive a little more deeply into arrays now. So if we talk about converting source code to machine code, getting down to like the low level details of computer. And arrays themselves are the most basic data structure we can have. The most basic way we can organize our data. So I'm curious to hear your thoughts on what is an array? What would you define as an array? And can we go maybe to Bianca, if you don't mind? What in your mind is an array? 

AUDIENCE: OK. So this was the most confusing part of lecture for me. But I think it compiles like-- it's like smaller pieces that are like elements, so it compiles all the elements into essentially, so that they're all next to each other. And it also sorts, for lack of a better term, elements of the same value so that they're next to each other. 

CARTER ZENKE: Yeah. So I like a few things about what you said there. So I like that you said that it combines these elements, these pieces of data that we have. And it puts them back to back in memory. So let's take a look at an example here. One CHT final project was this one called SleepS50. And the goal of this project was to actually store the number of hours somebody has slept every day. So somebody might come back to this application and type in, I slept eight hours last night. They come back the next day, they type maybe nine hours, or seven, depending on how much they slept. 

And if we wanted to store this data, at least currently in our story so far, we would need a whole bunch of variables. We'd have to say, OK, I need hours one, I need hours two, hours three and so on as that we're going through the days here to store all of this data. But what is not so well designed about this? Where would this go wrong? And maybe could I ask Elena, if you don't mind? 

AUDIENCE: I'm not too sure. 

CARTER ZENKE: OK. So we're trying to store all this data, right? And if we had to keep track of all of these variables, let's say I wanted to have a sixth day of hours, what would I have to do now? 

AUDIENCE: You have to add another line? 

CARTER ZENKE: Yeah, add another line and presumably, another variable. But that would get pretty messy, pretty quickly because assuming I want to keep track of maybe like a whole year's worth of sleep, I wouldn't want to have hours 1 through hours 365. That would just be a whole lot of individual variables, right? And so to Bianca's point earlier, these arrays help us keep track of this information all in one piece. 

So let's take a look at an example of an array here. Here we have one called "hours". And as we're thinking about these arrays, this really good mental model is this long line of individual pieces of data. So here we have those same five hours, but now under one block of memory that we're going to call "hours". And when we're trying to create this block of memory, there are really three things you're going to need to take care of first. 

So the first one is the name of this block. What are we going to call this array? So here, we're going to call it "hours". And maybe I'll turn it over to you all for the other two that matter here. We have a name for the array, but what else do we care about if we're going to try to create this block of memory? Could I ask maybe you, Dewey? Yeah, go ahead. 

AUDIENCE: You would need the length of the array. So here, we would probably want seven because there are seven days in a week. 

CARTER ZENKE: Yes, so probably seven days in a week. So we could make maybe this array of length seven to store seven hours of sleep every day. In this case, we'll probably just go with a week day calendar. So we'll have five in this case. But the size is certainly something we care about here. And there's one other thing we care about too, the name, the size, and what else would we need? Could I maybe ask you, McKenna, if you have any ideas here? 

AUDIENCE: I'm honestly not sure. 

CARTER ZENKE: That's OK. No worries. 

AUDIENCE: This is like a topic from lecture I was a little confused on. 

CARTER ZENKE: Yeah, yeah. Other thoughts here? 

AUDIENCE: The type of value? 

CARTER ZENKE: Yeah, totally. So we need the type that we're actually storing here. So three things we care about for arrays when we make them. The name, the size, how many elements are we storing and then also what kind of type are we storing in this array? And the type matters because we want to know how much space to allocate to our array. Different types have different numbers of bytes that represent them, like an integer might have 32 bits, or maybe 4 bytes, in that case. But maybe just a character would have only 8 bits, or one byte. 

So the type depends-- the type matters for how much memory we're going to allocate to our array here. So with this in mind, we keep in mind the name, the size, the type. We have some syntax we would use in C to actually create this space for the array. And this is what that would look like here. Up top, we have "int" and what would "int" represent in this case? Could I, maybe, go back to you, Dewey? What would "int" represent here? 

AUDIENCE: It would represent the data type of the stuff stored inside the array. So we're storing integers so we want "int". 

CARTER ZENKE: Yeah, nice. So similarly to how we declare our variables with the type first, so similarly, for our arrays, we say what type do you want to put in this array first? And then next is the name of the array. So "hours". And then what is inside these brackets? Maybe could I ask you, Bianca? Do you mind telling me what's inside these brackets? What pieces of the puzzle is that? 

AUDIENCE: That's the size of the array. 

CARTER ZENKE: Yeah, it's the size of the array. So here, we're saying we have an array called "hours" that will store integers. And it will be of size five, so we'll store five integers. And this is all well and good, but one thing to keep in mind is that our array isn't quite useful unless we can access individual elements of the array. So we have this syntax that also uses this bracket notation. And we can see it a little bit down below here. 

So if we wanted to get the very first element of our array, we'd say, hours[0]. If we wanted to get the next one, we'd say hours[1], and so on. And all the way at the end here, we have hours[4]. But why would we not have hours[5] to get that last element there? How does that make sense? Maybe Elena, would you have any thoughts here? McKenna, I see your hand raised. 

AUDIENCE: Well since we start from 0, like if we want 5 pieces, if we count all the way up to hours[5], then we actually have six pieces. 

CARTER ZENKE: Yeah, totally. So if we counted from 0 to 5 inclusive, well, that's actually six elements. But we only have five in our array. If we start from 0 and count up to four, well, that's five distinct elements. And so that is the length of our array, meaning we're not going beyond the length of our array here. And if we wanted to go ahead and add some data to this array, it'd be a simple assignment. So here, I might say, I want to put seven in the very first array spot. Hours[0] gets the value seven. Remember, we read this equal sign as a "get" in English. 

And then we could say, OK well, hours[1] should get the value 9 and so on and so forth. And so we fill up our array as we go. Now we could fill up the entire array at once, if we wanted to enough to have all these lines of code here. We could do this. We could say, let's create this array named "hours" that has five elements. And let's have it "get" this set of numbers here, 7, 9, 8, 7, 8. And overall, that would give us the entire array filled up for ourselves here. And even then, we might not even specify the size in this case because we know, well, there are five elements over here. So we could just have C infer how much space our array takes up. 

You take out that five there and say, well, we just have these five elements here, we'll make sure we have an array of size 5. So I just want to pause here for any questions you all might have on this array syntax, or how arrays are working here? 

All right. So seeing none so far. Let's keep going then and get to an exercise in just a bit. One thing we might want to do with our arrays is, again, access each element. And sometimes, we want to start at the very first element and then keep accessing things as we go through. And a for loop is a great way to do that because a for loop lets us specify a variable that can increase. And we can then use that variable to access individual parts of our array. 

So here, I might have the same array, "hours" up at top. And now this for loop here, that is starting at I equals 0, going up to, but not including I will be equal to 5. And then we'll go ahead and print out whatever is at hours[i] here. And so a question for the group now is what would this print out if I were to run this? What would I see on my screen? And feel free to raise your hand if you'd like. 

What would I see on my screen for to run this for loop? Yeah, Dewey? 

AUDIENCE: You would see and, then a new line, 9, new line, 8, and then onwards until the end of the list-- array, technically. yeah. 

CARTER ZENKE: Yeah, yeah. And I'm curious, you said a new line, so what is indicative of the new line here? There's a slash, n. So that means-- that tells the computer to start a new line. 

CARTER ZENKE: Right, so in this print statement here, we have that %i, which is like a placeholder for an integer that will print out. And we'll specifically add in the hours bracket I integer there. And we'll make a new line here to say, OK, once you're printing that integer, let's go to a new line, print that one, go to new line, print that one and so on and so forth right here. So with that in mind, let's go ahead and try and exercise in small breakout rooms here. And this exercise is called powers of 2. 

So the goal here is to make an array that has a certain size, maybe given to us by the user. And then we'll want to create an array where every element is 2 times the previous number. And we can start the array at one. So we might have an array like, 1, 2, 4, 8, 16, 32 and increasing by two times every time we go through and add this new element here. And let's go ahead and get started on this one together. 

So if you want to ahead and pull up code.csu.io, that would be great. And you can follow along over here while mine boots up as well. And what we'll do once your code space loads is create this file called array.c. Go ahead and make this program where we'll have this array that will be every element two times the previous one. And just to kick us off here in a discussion, what kind of boilerplate code would we really need here, and by boilerplate, I mean default code we want to have in every program that we write? 

Maybe at the top of our file, what's the first thing we would do here? Can I ask maybe Sotanalie, if you don't mind? What would we have to have the top of every area of our programs? And I'll have mine booted up here. So what we want to do very first is make sure we have our program up. So we can type code array.c. And that will make sure we have this new file called array.c. And that ".c" is important there. That means this is a C file. And now at the very top of our programs, what we're going to need? Can I maybe turn to Elena, If you don't mind? What would we want to incorporate the very top of our file in most programs we write? 

AUDIENCE: You would have to include from the one, the packages, like, from like CS50 and ST-- I forgot it. 

CARTER ZENKE: Yeah, yeah. You're totally right. So we want to make sure we include some libraries or some packages perhaps in our program because we actually use those functions in our program. So we might first include the CS50 library by include CS50.h. And we might also want to include the standard I/O library. The first standard input and output, meaning some functions we can use to get user input and then print something out to the screen here. 

And then what else would we need, kind of template here? What kind of function is going to be the core part of our program here? How would we do that? Could I ask McKenna? 

I'm so sorry. For the core part of our program, we would need main void, right? 

CARTER ZENKE: Yeah, totally. "Int main void". So I could type "int main(void)" here and then have this to dileanate where I'm going to type the rest of my program inside of these curly braces here. And we'll see why in particular, we type "int main(void)" just a little bit. We saw it briefly in lecture two. But for now, we want to make sure that we're going to get some user input. 

So I might have you all finish this part together before sending you off to work on the actual array building piece. But what kind of function would we use to get user input in this case? We want to get a number that we could use for the length of our array. So what kind of function have we seen in CS50 that could help us with that? Do you mind if I ask maybe Bianca if you have an idea, or maybe some steps forward for us? 

AUDIENCE: Can you repeat what you said? I'm sorry. 

CARTER ZENKE: Yeah, yeah. So we want to make sure we have user input to get the length of the array. So what kind of function could we use to get a number from the unit that we've seen so far? 

AUDIENCE: A number you said? 

CARTER ZENKE: A number. 

AUDIENCE: The "get int". 

CARTER ZENKE: Yeah, "get int". So we could say I want to maybe create the length of this array and I want to make sure I get an "int" from the user, maybe prompt them for a length, right? And here's a question of design. What if these are typed in a negative number? Well, I can't have a negative length array so I should probably do my best to make sure they give me a good number and not assume that they're going to cooperate. So I might do this. I could say, "do", I want to make sure that I get the length from the user here. And I'll make sure to declare my variable up above. 

But then before moving on, I want to make sure that this length is definitely going to be at least one. So I'll say if the length is less than 1, I want to re-prompt the user as we go through. This just ensures that you just don't type in negative 1 or 0, like values that are invalid for our right length. So we have some initial code here and feel free to jot this down on your own array.c file. But we'll do next is we'll break out into a few rooms and we'll come back in maybe five minutes or so. But the goal here will be to finish this prompt here. 

So you're going to create an array that is of size, whatever the user typed in. And then we'll make sure that every number is two times the previous one. Yeah, Dewey? 

AUDIENCE: Would it be possible for you to copy and paste the prompt into the chat so that we have it on hand? 

CARTER ZENKE: Absolutely. I'll make sure to do that. Yeah. All right. So let me go ahead and type that in the chat, but once we do that I'll send you all to breakout rooms and come we'll come back in maybe 5 or 10 minutes or so. 

AUDIENCE: Can I ask you a really quick question? Because I know for the lab, we had a folder that we unzipped to invest code, is there something like that for this section or should we just create our own file? 

CARTER ZENKE: Good question. Yeah, so normally for a problem that you're working on in a problem set or a lab, you might download a file, unzip it. Here, we're just making our own file. So if you want to, you can go to your terminal down below, just type "code array.c" and that should make you this new file. You can type in your code as we go. 

AUDIENCE: OK. Thank you. 

CARTER ZENKE: Yeah, yeah. So let me type this in the chat. So we'll create a program that prompts the user for a size. And then we're going to create an array of that size where each element is 2 times the previous one. And you can start the array at 1. And your goal is to ultimately print the array of integer by integer. So I hope that's helpful. I'll send you all into breakout rooms in just a second here. We'll come back in let's say, about five minutes. 

Welcome back, everyone. I hope you got the to make at least some progress here, but no worries if you didn't get all the way there. What we'll do now is work on this together a little bit. So here I have-- go back to my view here-- where we left off in our program. And again, the goal was to make this array that every element was 2 times the previous one. And it had the length of whatever the user gave us in this case. So going back to some of the slides that we just talked about earlier, how would we even declare or make space for this array in our program? 

We want to have an array that stores integers of a certain size and a certain name. And maybe could I have Alena, if you don't mind, you want propose our array name and length and what it stores? 

AUDIENCE: So for the type, it would just be "int" I think. 

CARTER ZENKE: Yeah, exactly. Storing integers. 

AUDIENCE: As for the size, I think the size would need to be the user input. 

CARTER ZENKE: Yeah, definitely. So it would be the variable length here. And before we can give it a size though, we have to give it a name. So you propose a name for us? 

AUDIENCE: I don't really know what you would name it. But-- 

CARTER ZENKE: Yeah, I mean, it could be anything. We could call it-- I would call it-- well, for fun, we call it "twice", like twice the previous number. But you could also call it array, you could call it whatever you want to call it. Here we'll say it has a certain length and that length is literally this variable length here. So whatever we type in, that will be the length of our array. 

Now if we wanted to go through every element in the array, what loop might we use here? We want to go through every element and we want to make sure that we set each of those elements equal to some number. So what kind of loop could we use? Could I ask maybe Bianca if you might have some thoughts here or ideas? 

AUDIENCE: I want to say a for loop, but or maybe another dua loop, unsure. 

CARTER ZENKE: Yeah, so for loop is the right intuition. And why is because if we know how many times we want to do something, we know we want to go through every element of the array and it's like a fixed size, a for loop is great because a for loop can do something a certain number of times. So here, let's say I want to loop from maybe I equals 0, all the way on up to I is less than length. And increase I every time I go through. And so here's what that looks like here. 

And the goal here is, maybe we're accessing every element of twice. By going from I is 0, all the way up to I is not length, but one less than length. So it goes to every element inside of "twice". But what should every element inside of "twice" be? How do we complete this statement here? It should get a value, but what value should it get? Could I ask maybe McKenna if you have any ideas here? 

AUDIENCE: Sorry, could you repeat the question one more time? 

CARTER ZENKE: Yeah, yeah. So we're just trying to figure out what number should we put into each element of this array called "twice"? We know that we want it to be two times the previous number, but how would we actually put that in code if you have any ideas here? 

AUDIENCE: Two times i minus 1. 

CARTER ZENKE: Yeah, nice idea. We could say two times twice I minus 1. And this is going to do is say, OK, let's make sure that the current space we're looking at inside of "twice" is going to be two times the previous value that's in twice here. So for example, if I is 1, then we'll look back at 0, index 0 here. Multiply that by 2 and make that the value of "twice" at the index 1. So let's go ahead and try running this if I type "make array". Let's actually try printing out this value as we go too. So I'll say, not only do we want to set the value, I want to print it out as we go. So I'll say %i and then twice[i]. 

I'll then recompile my program and I'll do a ./array, maybe a size 5. But I get just 0s. Any ideas about this bug in our program? Yeah, Dewey? 

AUDIENCE: Forgive me, sorry, I had to unmute. So essentially, we need to set a value for the first element in our array. Otherwise, it's just going to take 0 and then just multiply it by 2, which is obviously 0. 

CARTER ZENKE: Right. Yeah, so we need to set a first element here. And more specifically, what's happening is let's say i is o, well OK, twice[0] should be 2 times twice[-1]. And so negative 1 will look one space in memory before our array. And really, who knows what's there. It could be 0, it could be some random number. If I were to try re-running this program, I get a different answer. Still 0, we run this again. Still 0, but we might get some random number there eventually because we're not really sure what's one space memory before our array. 

So to Dewey's point, let's actually first set twice[0] to 1. That first element of twice, set it to 1. Then we'll go ahead and start from i equals 1 and look one behind us, multiplying that by 2 as we go through. So I'll do "make array". I'll do a ./array of size 5. And now I get something that looks pretty good, but I don't think I have the full array here. What else do I still need to do? 

Let me go back my terminal I only see 2, 4, 8, 16. Any thoughts, Dewey, if you want to finish the debugging here? 

AUDIENCE: Give me a second. Let me just pull up-- OK. So we're not seeing the entirety of the array. So we're only seeing up until the last four, even though we want five. So it's not showing the zeroth element, which is 1. So we should probably should printf twicE[0], for instance. 

CARTER ZENKE: Yeah, so we've got to print it out here as well. So I'll say print out whatever's in twice[0], right after we set its value there. So basically, we're going to fill in the very first element of our array on lines 15 and 16. Then we're going to fill in the rest of our array on lines 18 through 22. So now if I compile this, "make array", I'll run array. And now I'll see every element inside of that array. So what questions are there on this program, or arrays in general? Any lingering thoughts or questions? 

AUDIENCE: Could you go back to where you had after "int twice", the line of code you have after that. And explain that, if you don't mind? 

CARTER ZENKE: Yeah, totally. So here, let me actually comment the code, just to make it little clearer. So here, we're going to get the length from the user. Now once we have that length, we're going to declare our array, which means make some space for it in our computer's memory. And here what we're doing is going to set the first value. 

So our array should start at 1. And so we'll take the very first element inside of twice using that 0 index here. Remember, we start from 0 and go on up. We'll say that gets the value 1. I will then print out that value. And then we'll look at the rest of our array. We'll start at i equals 1 instead of i equals 0 here. Move on up to the length, increasing i as we go. And as we do it, let's go ahead and make the current element twice the previous. And then we'll print out the current element. Does that make sense? Nice. 

Other questions on this one? All right. So let's keep moving in that case. And our next topic following through on arrays is this idea of a string. And what are strings really? We saw this in lecture a little bit. Strings are these collections of characters, like a name, like Carter, or maybe a location, like Harvard. But what data structure are they really? 

Maybe could I ask Elena if you have any thoughts or guesses here? 

AUDIENCE: From what I understand, I just thought of strings as strings of characters instead of just one character. 

CARTER ZENKE: Yeah, totally. So a string is like a string of characters. We've taken some individual characters and strung them together, so to speak. And this name comes from the fact that we have some characters now all grouped together. And so similarly, how we had these hours that were previously individual variables, but now I put them in this array called "hours", we can do the same for strings. We're taking these individual characters, putting them together into this one, big array here. 

So if I take a look at this string, this string is "Emma". And if we take a look at the entire string, we'll see it's basically the same idea as an array. We have this name for the array. We have some elements inside each individual block of that array. And we have that same syntax to get access to individual elements of that array. So name[0], name[1], and so on. But what's kind of special about this string here? 

If we take a look at that last element, does anyone remember what that last element was called? Just to show you again, looks like a "slash 0". What was that called? 

AUDIENCE: Wasn't it the null character? 

CARTER ZENKE: Yeah, right. It was the null character. And you remember what its purpose was? Maybe go ahead, Dewey, yeah. 

AUDIENCE: It marks the end of the string. 

CARTER ZENKE: Yeah, It marks the end of the string. So otherwise, we wouldn't really quite know where to stop if we were looking at a string. We have to have some way of knowing, OK, this is the end of our string now. But here, we have this null character tell us, OK, that is going to be the end of our string. If we want to make this same string, we could do so by making an array of characters. So here, we have up above, this array called name. And it's full of characters. And we've given it some elements here, E, m, m, a, and that null character. 

So we've composed this string ourselves from individual characters. And this syntax here, string name gets the value "Emma" is kind of some sugar that we've given you to make it easier to declare an array. This is based in the CS50 library, but on your own, if you were off into the world and programming C more generally, you might make strings a little bit more like this, or you might use some libraries to simplify things for you, but basically, under the hood, this array is this array-- or the string is this array of characters. 

And notice similarities here between this array called "name", and this array called "hours". It's much the same thing, just here we're storing integers versus storing characters. That's handy because we can do all the same things we could do with arrays earlier. We can have name[0] to get that first character, name[1] to get that second character, and so on. And so just curious here, any questions on strings or how they're similar to arrays or the syntax that we've seen here? All right. 

AUDIENCE: Sorry, just one quick question. You can't circle through a string in the same way you can with an array? Like in a string, you couldn't say the first character with square brackets for stricter-- square bracket 0 and then 1. That's unique to arrays? 

CARTER ZENKE: It's unique to arrays. Arrays are the only data structure that have that bracket notation, but the nice thing about a string is a string just is an array. So you can get that same functionality. So here, even if we didn't do this, we didn't spell out the array like this, we just did string name gets the value "Emma", we could still do this syntax. Name[0] gets that capital E at the beginning, name[1] gets that second character, that m there and so on. Does that make sense? Nice. Other questions too on these strings? 

OK. So one of the interesting things about these characters is that they're represented ultimately, by binary, everything in the end is. But in C, we have this dual representation of characters, where this capital A is represented by the number, 65. Lowercase a is represented by the number, 97. And somebody came up with this, The American Standard Code for Information Interchange, I believe. I'm not misremembering there, or ASCI. And so ASCI defines these relationships between these characters and these numbers. And the interesting thing is, if I were to go to my code space here, let's say I wanted to make a file called "string.c", I could include all the files I need, like this. 

I could make my main function, and let's say I did have this string called Emma, well, what I could do is I could print out every letter, kind of like this. I could say for int i is zero, i is less than-- oh. Well, how long is Emma? How many characters should I go? We don't-- I mean, you could look at it and say it's for. But there's a better way to do it. And we saw a function in lecture. What could we do? Yeah, Dewey? 

AUDIENCE: Str len? 

CARTER ZENKE: Yeah, we need str len. str len is this function in the string.h library. We might say strlen, kind of for short here. And we want to get the length of our strings. We could say this new variable, called length, gets the length of name. And now we can kind of finish for loop. We could say, i is less than the length of that string, i plus, plus, it's increasing by 1 as we go. 

And now we'll say, OK, print out for me whatever character is inside of name[i]. And so however, to make this, compile it to machine code. I could run .string and I see E, M, M, A. All of these individual characters. But what I could do too is I could say, I want the integer representation of this. I want to print this as an integer. 

I could recompile this. And I'm going to actually add this new line at the very end of my program now. I could say, "make string" and then "./string". And now I don't get E, M, M, A, I get 69, 109, 109, 97. So whenever you're working with characters, you can also treat them as numbers. And we can do this interchangeably as we go through. I could say is a certain number-- or is a certain character more than or less than some number, or things like that. 

It'll be useful for us as we work on this next exercise here where we're going to try to figure out if a string characters are in alphabetical order. So what do we notice here if we go back to this ASCI chart? We look down at this lowercase half. What do you notice as the numbers get further in the alphabet? What happens to the numbers? 

Can I ask maybe Bianca, if you don't mind? How are these numbers changing as we go further in the alphabet? 

AUDIENCE: They increased in value. 

CARTER ZENKE: Yeah, they keep increasing in value. So to figure out if a strange character is in alphabetical order, what we could do is just check to see is each character greater than the one behind it? So let's go ahead and get start on this one together. We could maybe go to our terminal here and code up alpha.c. And this would be our new file, not downloading anything, just making a new file here. And we could say I want to include the CS50 library. I want to include standard IO.h to print things out and I want to have this main function still. This main part of my program. 

And now what I could do is I could say, I want to get some string from the user. So I could say, string word is going to get-- what? What kind of function can we use to get a string from the user from the CS50 library? Maybe Elena, do you have any thoughts here? 

AUDIENCE: So I'm not sure. 

CARTER ZENKE: It's OK. We're trying to get a string from the user here. So how could we-- what kind of functions in CS50 library might be useful for us? 

AUDIENCE: Get string. 

CARTER ZENKE: Yeah, get string. So we could say, "get string". And maybe in this case, enter a word. And the rest of our program I might leave up to you. But again, the goal is to check if a lowercase strings characters are in alphabetical order. And if they are, print "yes". If they aren't, we'll print "no". And you might want to have some kind of loop that goes through a every character and does that check for you, checking to see if each character is more than or less than the one behind it and making a decision based off of that to figure out if it's in alphabetical order or not. So I'll go ahead and paste this one in the chat for you all, but any questions before we begin here? Not seeing any I'm just finishing typing in the chat. 

And you might find ASCIchart.com useful to go ahead and take a look at the representation of these characters as numbers in this case. So we'll go back into some breakout rooms for, let's say, five minutes. We'll come back afterwards to do this together and then talk more about command line arguments and yeah. So let me go ahead and open these up and I'll see you in a few. 

All right. Welcome back, everyone. Again, I hope you made at least a little bit of progress or you learn something while you were working on this. It's a little bit more on the advanced side. So what we do is take a look at a solution together, walk through what it does and see what questions come up as we do so. So here is one way of approaching this problem. I can Zoom in a little bit here. And what we'll do is we'll first get our string from the user on this line 7. And then we'll go ahead and figure out how long that word is. 

Now what we'll do is we'll go through every character front to back and say, OK, let's check if the character is not alphabetical. Often in computer science, it's easier to check for something that if it's not true, then it is to check for something if it is true. So here we're going to say, I want to see if it's not alphabetical. And if it is, I want to go ahead and print "no" it's not alphabetical and return 0, meaning I'm going to exit my program. Nothing else will happen here. 

But assuming I actually get through this loop, all the way through, I'll go ahead and print "yes". The key intuition here is that we know if something's not alphabetical when the current character has a value that's greater than the character that's before it. So here, if I were, to example, say look at-- actually, yeah, before the character that is-- yeah, so here, I would look at B and say, OK, B in this case is greater than A. If we look at that chart from earlier, let me go back here. Open this up. 

We could see that B is a 98 and A is 97. So in this case, if we ever find that this character here is greater than the character ahead of it, we know that we've found a non-alphabetical sequence. And we can go ahead and say "no". In this case. Assuming we get all the way through though and we don't ever trigger this and we don't ever end our program early, we could assume that everything must be alphabetical unless "return 0" at the end. 

So questions on this or places you were getting stuck as we were going through? Yeah, Dewey? 

AUDIENCE: You don't need the return 0 at the end, right? like, after the "print yes". You need it for the "print no" I think, but not the "print yes". 

CARTER ZENKE: Yeah, we don't really need this here. Maybe it's good for completeness sake to have some return value there. But C will automatically return 0 as soon as you hit this bottom semicolon of your main function. The return 0 here, though, as you said, is necessary because it ends our program early and keeps us from printing no, no, no, no, no as we go through our program. 

AUDIENCE: Could you explain-- 

CARTER ZENKE: Other questions? 

AUDIENCE: Could you explain one more time how you need to do string length as the first-- like at the top? 

CARTER ZENKE: Oh, yeah. Like up here? Yeah. So in general, when you want to do something for every character in a string, you generally want to have some form of strlen. And strlen is going to tell you how many times you should loop in your for loop. So here, for example, if I wanted to figure out how do I do something for every character in my array? Well, I have to know how many times to loop and thus I have to know how long my string is. So I know I need strlen to figure that out for me and I can use that variable in my for loop later on. Does that make sense? Nice. OK, other questions here too? All right. So not seeing any there. 

So let's go ahead and move on to some command line arguments just to wrap up our section today. I know there was some excitement around command line arguments. They're pretty cool actually. You could actually use them to modify our program behavior as we type it in at the terminal. And so maybe you're used to using a GUI or a graphical user interface, but you'll get used to, as you do more programming, using this terminal interface. You can type in a program's name and then go ahead and give it some options to run with. 

And we saw Clang earlier, this compiler for the C language. And Clang does take some command line arguments. So we saw it could take this argument called Mario.c. And this is a command line argument because it's given to the program at the terminal, it's not an option we give to a program as it's running, it's given to our program before it runs. We could also give more. We could say the output of this compiler should be Mario, this file called Mario. And even make itself takes command line arguments, that Mario right there at the very end. 

And we could even have another program called "initials", for example. Actually no, I think we-- we'll get to initials in just a minute, sorry. But the intuition behind command line arguments comes from this idea of these functions that take their own arguments. So in an earlier problem, you maybe saw this calculate quarters function. And here, this calculate quarters function takes this argument called "sense". And this program or this function takes that input and then does something different because it's given that input, this argument over here. 

Similarly in our programs, we have this main function where this is the function that gets called as we type the name of our program in the terminal. So if I were to type maybe ./mario, again, my main function is being called. Now Mario didn't take any command line arguments and because of that, we typed "int main and void, where void says no input to our program is given at the command line. We do return something from this function, an integer, kind of like a status code that we saw in lecture. But the input to this program is void, is currently nothing. 

If we did though want to give our program some input it could run with, typically, in our programs we would write something like this, "int argc" and "string Argv". That's an array. And the reason we do this, we often want two pieces of information as our program starts. We want to know how many arguments were given, and that's argc for argument count. Notice how it's an integer called argc for argument count. That's how many arguments you've given at the command line. 

And we're also given this array of those arguments called argv, which stands for argument vector. And so argument vector, argv is this array of strings that have been given to our program at the command line. And we can use those in our program to modify its behavior. Now for example, if we were to go in and make our own program here. I could do maybe "code CLA" for command line arguments. And I could then do all the usual stuff. I could include "stdio.h". I could include maybe "CS50.h". And I could do "int main", but this time, I want to take command line argument. So I could say, "int argc, string argv". And what this will do for me is allow me to figure out what else was typed along with my program? 

And to do so, I might do the following. I try to go through every element of this argv array. So I could say "for int i is zero". I is less than argc, I plus, plus. Let me loop through every argument I've been given here. And then go ahead and print out, as a string, whatever is inside of argv at that location here. Let me fix this. 

And let me just make it a little clearer here, even too I could say, maybe argc is-- and then some number. And argv is, or sorry, argv-- let me actually makes this clear-- so you can say "argv, bracket, whatever we're currently looking, at is whatever's inside of argv. So here, when I run this program, I'll see argv, bracket, 0, bracket, 1 is whatever's at that location here. So I'll then go to my terminal. I'll compile this. I'll say, "make CLA". And I'll run "/cla". And now I see argv, bracket, 0, is ./CLA. 

But if I did ./CLA, maybe, Carter Zenke, well now I see more. I see argv, bracket, 0, is ./CLA. Argv[1] is Carter. argv[2] 2 is Zenke. So I've been given this array that contains everything I typed in to the terminal here. Just to make this even clearer, I could go back to this diagram over here. When we "make Mario", that very first make over here is argv[0], the very first element of argv, or argument vector, or argument list. And argv[1] is that second element there. We can get using our program here. 

And often that you'll see when you write your own programs in CS50, you might want to maybe kick off your program with some number. Maybe in Caesar, you might type a number to help us figure out how much to rotate a certain cipher, and so on. And this is helpful for actually making our programs change behavior as we go through. So I just wanted to pause here and ask for your questions on command line arguments. Maybe you've tried them already, maybe you haven't, but what questions do you have about why they're used, or how we use them? 

OK. So seeing none so far. Let's go ahead and try to do a bit of brief exercise together here. We want to write this program called "initials", where if I were to run it with some command line arguments, I would get back the initials in the certain name here. So here, I would get back CZ, for example. And notice how we have, again, this argument vector that has every element inside of it. And if we want to access individual characters inside of these strings, we can just have another bracket notation appended. We could say argv[1][0] gives me that very first element of that second element in our argv. 

And similarly, argv[2][0] gives me that very first element of that third element inside of argv. So we're kind of nesting these arrays as we go through. And towards that end, let's try to actually implement this program together. So we'll go over to our terminal here and type "code initials.c". And I'll do all the same stuff. I'll do "include CS50.h. I'll do, "include stdio.h. And finally, I'll do "int main, not void, but int argc and string argv. I want to eventually, do something like this, ./initials. Carter Zenke. 

So let's try printing out first this very first C. How could I print that piece out? Could I ask maybe, McKenna, if you're feeling up for it? How could I try to print out that very first C here? 

AUDIENCE: Wouldn't you do like printf, something having to do with the argc[1][0], right? 

CARTER ZENKE: Yeah, totally. So you want to print out a character. So we'd use this format code for a character, like %c. And now I have to say, OK, what goes in this placeholder here? And we could do the following, we could say, well I know I want to look inside my argument vector, this list of strings I've been given. This we know is that very first one. So that's argv[0]. This one is argv[1], which is getting us closer. But we don't want to print out the full name here. So if I were to do this, for example, print out a string. Let me do, "make initials". And then run it-- and just a minute, oops, let me add a semicolon. 

Make initials, do ./initials. Whoops! ./initials Carter Zenke. Notice I get back the full string Carter. But I don't want that. I just want the actual first character. So I could then, as you were saying, we go ahead and say, bracket 0 to get that very first character in there. And I'll go ahead and add a /n here. 

So I'll say, "make initials". Run initials with Carter's Zenke, and now I get backseat, which is nice. But maybe to finish things out, could we go to Bianca, if you don't mind? Maybe figure out how we could get that second initial here? 

AUDIENCE: So you would do the same thing that we have instead of the one and the zero, you would do one-- well, the first one, is that from the Carter, or is that from your last name? 

CARTER ZENKE: Yeah so this one here, if we-- yeah, so when we ran this, this is from trying to get this initial C here, right? 

AUDIENCE: Yeah. 

CARTER ZENKE: So now I want to get the z. 

AUDIENCE: Got it. OK, so you would do the same thing, but instead of argv[1] and 0, you would do two and 0. 

CARTER ZENKE: Yeah, two and 0. And the reasoning here is that we're going to first index into that argument vector this argument list here. And here, we're going to get that third element, this index of 2 gives us a third element. And then within this string here, that is also an array, we're going to get that very first element. So we'll go to the z here. 

And if we do this, I would tend to maybe make initials. And then I could do ./initials, Carter Zenke. I would see C, Z, and then I would C, Z. So there's much more to this. If you like, you can maybe use a loop here to go through and do multiple Clang line arguments, but I think for now, we'll leave it here. This is going to conclude our section, officially. It was wonderful to spend time with you all today. 

And this was CS50 for now. There are also going to be labs, tutorials and office hours this week. So make sure you go to all of those to get help as you need it. I hope this was helpful for you. I'm looking forward to seeing you all throughout the term and again, thank you all for joining us on Zoom today. 
