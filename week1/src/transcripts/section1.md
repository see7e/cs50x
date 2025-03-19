---
title: SECTION1 - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

CARTER ZENKE: Hello, one and all. And welcome to CS50's very first super section for week 1. My name is Carter Zenke. I'm the course's preceptor. I'm joined here by many of our wonderful staff members that are going to stand up and say hello. 

[APPLAUSE] 

Yeah, a round of applause for these folks. They're wonderful. They'll be helping you through this super section today. 

This is our first super section for the course. On a normal week, you actually attend your own section online by course's head teaching fellow. You signed up for those online at Harvard. And you'll attend those starting next week. But this week, given the odd schedule, we thought we'd come together for one large section overall. 

So here are these details here. You're going to email if you've got any questions, heads@cs50.harvard.edu. And all of our slides and intros for today will be at this URL down here on the course website, going to the super section page there. To kick things off, though, I thought we'd actually have you all talk to each other and think about these two questions. 

So think back to lecture and think about this first question. What did you find exciting from that lecture? And what are you still confused about? What do you still have questions about? So turn to somebody, perhaps who you don't know and talk about those two questions for 2 minutes here. One, what are you excited about? Two, what do you still have questions about? 

Let's come back from these conversations. So glad you are having this wonderful discussion here. And let's hear from a few different groups on what you were thinking about for these questions here. Thank you, all. Let's actually turn to this left-hand section. Could one group over here tell me what you're excited about for this week and one thing you're still wondering or you have questions about? One group from this side of the room? 

Can I narrow it down to somebody from the front row perhaps? What are you interested in? What do you still have questions about for this week? Yeah, go ahead. 

STUDENT: I think it's more of the-- and less of the code, the syntax itself. Because that, you can kind of pick up quite quickly. I think the hardest thing is probably to how you construct efficient code. You sometimes just have to think in a different way. 

CARTER ZENKE: Nice. 

STUDENT: That's something that I guess, we'll really take some time to come to terms. 

CARTER ZENKE: Totally, yeah. So there's a question, how do you write efficient code? And later today, we'll actually work on the course's lab, this practice problem to help you see how we can write efficient code in that instance. You can work together on this practice problem and get ideas from each other as we go through. Let's hear from maybe one more group over on this side, maybe somebody in the second row back here, if you mind. One thing you're interested in, yeah, go ahead. 

STUDENT: I'm really interested in also this kind of stuff, but also creating stuff, just coding to have a the final product. And now I'll get opportunities to make a final product. And somebody else to think about lecture, I feel like there's so much syntax to learn. And that's sort of giving me pause. It's like, I don't even know what's out there. I think somebody said, actually in the orientation, sometimes like students will go something all the way out because they don't even know that there's a program for it already. 

CARTER ZENKE: Yeah, exactly. So there's this idea of how you take this idea you have and what you want to build and turn into the syntax, like actually write to make the computer do what you want it to do, right? 

So all these are good questions. And here are a few we'll actually dive in to today. The first is, why are we using C? Why we're using this ancient language to start off programming with? And how do we learn and read its syntax here? How can we actually learn how to create and read these variables, these loops and conditionals, and so on. 

As we go through that, we'll talk about this particular instance of a data type because C requires us to tell what type each pieces of our data are. We'll also talk about compiling C programs, taking them from source code to machine code. And then finally, at the very end, we'll talk about how many years it will take to double our number of llamas that we have in the lab. 

So to kick things off here, we can go back to actually lecture zero, I think, back to our contact application. So in this application we stored names and phone numbers and other things too. What else could we store in a contact's application? Could I ask maybe somebody from the second row, in this middle row here? What can we store in a contact's application? Yeah, go ahead. 

STUDENT: Phone numbers. 

CARTER ZENKE: Phone numbers, right, other things too. Maybe somebody in the row up now. 

STUDENT: Emails. 

CARTER ZENKE: Emails, OK. Other things? Let's go one row up again. What else can we store? 

STUDENT: Addresses. 

CARTER ZENKE: Addresses, nice. So all these things we can store in our contact's application. But let's say you want to store the number of times I want to actually have made a call before in my application, on my phone, right? So here we have an instance of a variable, some number or some value that can change. And I'm going to give a name to it, in this case, calls, number of times I called somebody here. 

So this is our mental representation of what a variable is. It's some name for a value that can change. But in C, we have a particular syntax I'll use to make variables. As you all go through and work on the course's problem set, build your own programs, you really should get familiar with this syntax and how to read and write it here. 

So here we have the syntax in C to create this variable named calls. And there are some components to it that we should actually dive into here. So the first part is the variable's name. This name is calls. Notice how it's in the middle of this sentence here. We also have the variables type, this int type. And what does this int type stand for? What kind of number are we going to store in here? Could I ask somebody from down here? Yeah, go ahead. 

STUDENT: An integer. 

CARTER ZENKE: An integer, so a whole number, right? Then we have the value, in this case, 4, that value we're putting inside this variable here. But there's one piece we're missing, we haven't talked about yet. What haven't we named here yet? Could I ask somebody from maybe this side of the room? Take a guess? We talked about the name of the variable, the type, the value. What syntax haven't we shown yet? Yeah, go ahead. 

STUDENT: [INAUDIBLE] semicolon [INAUDIBLE]. 

CARTER ZENKE: The semicolon, right? So this is a statement in C. And every closing statement that we have, we want to include a semicolon there. The other thing we haven't talked about, the one piece we haven't talked about here, could I ask somebody from down here now? We have the semicolon, the value, the name, the data type. One more thing, yeah. 

STUDENT: The equals sign. 

CARTER ZENKE: The equals sign, and is it an equals sign, could I ask you? No, you're shaking your head. 

STUDENT: It's and assignment. 

CARTER ZENKE: It's an assignment operator, right? So we'll say this is going to assign the value 4 to the space we've created for this variable named call. So if you say this in English here, we're going to create an integer variable. Notice how this type aligns with this type here. Named calls, the name lines up here. That gets, or that kind of stores this value 4, in this instance. 

So let's try again with another value here. Int x equals sign 50, and let's actually say this one all together, if we could. How do we say we create a what? 

STUDENT: Integer. 

CARTER ZENKE: (CLASS REPEATING AFTER) Integer that called x that gets the value 50. Nice. That's what it would be in English here. Amazing. Yeah, high fives all around. 

So why does C care so much about data types though? The very first thing we say here is not the name of the error but actually the data type. So we saw briefly this idea in lecture, but let's go ahead and talk to the person next to you. Why do you think C cares so much about these data types? Why is it the first thing we tell the computer when we make this variable here? We'll come back in just a minute. 

OK, let's come back and hear some ideas for why does C care so much about data types? Why is it the very first thing we put in a given line of code to make a variable in this case? And can we go back to maybe this side of the room now. And anyone in particular like to share what your group talked about, what ideas you had for this question here? Yeah, go ahead. 

STUDENT: Basically, we said that C wants to know data type. That's in order restrict the values that we input. For instance, if we're talking about [INAUDIBLE] input 3.5, so for [INAUDIBLE]. So it limits [INAUDIBLE]. 

CARTER ZENKE: Yeah, there's some value for specificity, right? I want to be able to make sure that I'm not putting in some value I couldn't store in this variable, like a text, for example. Other reasons too. Could we go to maybe down here? Yeah. 

STUDENT: The computer needs to know how much memory to allocate to the [INAUDIBLE]. 

CARTER ZENKE: Yeah, and why would that matter? Can I ask you, get a little deeper too? Why does this size matter? 

STUDENT: Because I think an integer is a lot less size than-- a lot less [INAUDIBLE]. 

CARTER ZENKE: Totally, so using-- or storing different values makes that value take away different space in a computer's memory. So integers take up maybe 32 bits, but a character might take up only eight bits. And so it tells the compiler how much memory, how much space to reserve here too. 

One other reason that we saw a little bit in lecture as well is we have some binary here, these eight bits that can represent a certain, well, really anything. What does this represent here? Anyone know off the top of their head? Yeah. 

STUDENT: No, sorry. 

CARTER ZENKE: Oh, no, OK. I'd be surprised if you do. But one thing this represents is the number or the integer 65, right? But as we saw in lecture a little bit too is this can also represent the letter A. Those same binary bits can represent both 65 and this character A. So it's important we tell C which thing we're talking about here by giving us our data types. 

So that's the reason we have these data types here. If we want to go further into variables, we can update them if we'd like. And here we have on this very first line the declaration and initialization of this variable calls. And down below we just update that value. 

So notice the type is on that top line, but it's not on that next line. And why would that be, if I can ask somebody from this side of the room now? Why is it on that top line but not that second line? Yeah, go ahead. 

STUDENT: On the first line you're initiating the variable and telling the computer what the data type is. On the second line, you're reassigning it to the new value, and it already knows that that variable [INAUDIBLE]. 

CARTER ZENKE: Yeah, so the computer is pretty good at remembering things, right? And once you've told it that this variable has a certain type, no need to tell it again. It already knows that. We can just keep going as we go. So here we're going to initialize and declare the variable calls. But when we use it again, we don't have to tell it the type as we go through. 

Now, if we wanted to change that value, we could do it like this. We also have some operators at our disposal. We could add 1 to it using this plus sign. We could even subtract some numbers. We could maybe multiply some numbers using that star operator. We could even divide some numbers, and so on. So feel free to take a look at those. If you go through the course, I'm sure these come top of your head as we go through. 

But when it comes to assigning some variable, what looks like a function, right, that's where things get a little bit weird. We saw in lecture we're trying to get some input from a user, right? And we didn't say that maybe string name equals quote "Carter." We said it equals this, maybe, function, get string. Or here, if we wanted to store a value in calls, get int. 

And in this case, before we're reading left to right. But in this case, it's actually better to read right to left when you see this function call on the right-hand side. 

So what's happening here is, when you have this function on the right-hand side, this function is wanting to run and then give us back some return value that will be stored inside this variable on the left-hand side. 

So before anything else, we run this function on the right-hand side with some certain arguments, some input to that function tell it what exactly to do. That function runs. Maybe it asks the user for this integer number here. And we then store that value right where that function was called. And it then goes into that variable. And now we're back to simple variable assignment here. 

So usually, if you're simply assigning numbers, you can read left to right. But if you have these function calls, best to read right to left, and knowing that your function runs first and then assigns that value as we go through. So questions on this before we dive even deeper. 

Seeing none. So now that we have these values stored in these variables, it's probably worthwhile to think about how we print them to the screen. And here's what we saw a little bit in lecture as well, this % and then this i here. And what is this doing for us? Could I ask somebody from this middle section here. Let's go to the first row, if you don't mind. Yeah. 

STUDENT: It's a placeholder for our variable call. 

CARTER ZENKE: Yeah, placeholder for your calls. And why is it %i? Do you know? 

STUDENT: Because it's an integer [INAUDIBLE]. 

CARTER ZENKE: Yeah. 

STUDENT: i represents [INAUDIBLE]. 

CARTER ZENKE: Right, so %i. This % is kind of saying like, hey, this is a placeholder. And that i specifies what kind of variable can go inside of that placeholder there. So because call is an integer, it's %i. And that's called, more specifically a format code, as we might have said. And we have this value that we can store in that format code there. 

We could have multiple format codes and multiple values. We just separate them by commas. So you can imagine, for example, I have %i here and maybe %i later on. I could have calls and then comma, some other variable. And those would go inside those placeholders one by one, aligning with whatever order I put them in as we go through. 

Now, it's not worth memorizing any of these, but there are a great number of format codes for different data types. And as you work with a variety of data types, best you can maybe reference these once in a while. So here on the left-hand side, we have number format codes, like ints and longs, floats and doubles, and the right-hand side some chars and strings, where chars are individual characters. And strings are collections of characters as we go through. 

One thing we haven't quite seen as much yet is this long and double. Anyone want to hazard a guess as to what that might be here? Could I ask somebody from this middle row again? What is this long and double doing for us? Yeah, go ahead. 

STUDENT: Does the long [INAUDIBLE] more room [INAUDIBLE] you have to have the long to [INAUDIBLE]? 

CARTER ZENKE: Yeah, exactly. So here we had an integer that could store up to four billion values. But when that's not enough, we might want to have a longer value, in this case, called a long, that will have twice as much space for us. We can store twice as many different combinations as we go through. Really, more than that. We're just having twice as many bits to represent that information. 

And similarly, for the float, that's a decimal number. But this double is called a double precision floating point. So we'd have twice as many decimals, twice many binary digits representing that decimal number there for us as well, so just more space for us to use as we go through. 

Now, what we'll do here is a brief exercise and invite you to load up code.cs50.io on your own laptop here. And you should see something that looks a bit like this. Maybe you have a File Explorer on the left-hand side. But you should certainly have a terminal down below. I see a question. Yeah. 

STUDENT: I'm not sure if this was a typo to be like this. But if you go back to the slide-- 

CARTER ZENKE: Yeah, yeah. 

STUDENT: So the double says f, and the float says f. Is that correct? 

CARTER ZENKE: That is correct. So both the float and the double have the same format code, yeah. Good question. 

STUDENT: So how does the computer [INAUDIBLE] recognize between [INAUDIBLE]? 

CARTER ZENKE: How does the computer recognize each one? In this case, it doesn't quite matter because, in this case, the float and the double are both decimal numbers. And so the computer knows when it sees %f, I'm printing a decimal number. It just so happens to be that the double is twice as long. And so it just prints that many more-- well, it can print that many more spaces after the decimal point if you'd like it to. Yeah, other questions here before we move on? 

All right, so we'll work on a brief exercise here. And once you've loaded up your IDE in code.cs50.io, you go ahead and create an application called phonebook.c. And the goal is to prompt the user for these three things and then print them back out to the user as confirmation that this data is stored in your program. 

So if I wanted to do this, I would first go down to my terminal down below. And I would make a new file. What would I do to make a new file down here? Could I ask somebody from maybe this right-hand bottom side? How can I make a new file in this program here? Yeah. 

STUDENT: Code and file name. 

CARTER ZENKE: Yeah, code and the file name. So I could do code, if it will load here. Let me refresh. But on your own, you could certainly do code and in the file name here. And for our purposes, I'll do code space maybe phonebook.c. But you could call your program whatever else you'd like to call it here. And maybe yours is doing the same thing. We'll be back in just a minute here. 

Now, once you have your file, what tends to go at the very top of that file? What's the first thing you might add? We saw this in lecture. Yeah, go ahead. 

STUDENT: The header. 

CARTER ZENKE: The header files or these libraries, right? And do you remember the syntax for that? 

STUDENT: Hashtag include, and then the caret thing. 

CARTER ZENKE: Yeah, hashtag include this little caret thing. Let's see if this one is loaded now. Not quite, but this hashtag include is saying, I'm going to try to get some file in my computer's memory that has these functions declared for me that I will then use in my own program here. So what two header files might you want to include in your program here? Yeah. 

STUDENT: Standardio.h [INAUDIBLE]. 

CARTER ZENKE: Nice, so two off the bat that you often want to use are standardio.h or stdio.h cs50.h. Both of these have some pretty common functions you'll be using as you write your own program. 

And we'll wait for this to continue connecting, and what we'll actually do is, now that you maybe hopefully have your file open, you have your header files at the top, we'll take some time, let's say maybe 10 minutes, to work on this on our own. I'll put the slide back up. And we'll come back in those 10 minutes and share how you approached this problem. Maybe if the staff would like to run around and help you as you work. Feel free to raise your hand. We'll come around and help you out. 

All right, let's come back. And we'll be working in a slightly different environment just because the internet is not quite what we want it to be. But we're going to make here our own phone book file where we can actually store the data we want to store. 

So if you remember our slide back here, we wanted to store a few different things. You wanted to store the user's name, their phone number, and I think it was their address. Let me actually take a look at that slide again, if we go back over here. A name, an age, and a phone number. 

So here we have this template for our program, but what are we missing right now? We have our header files, these libraries where I have functions we're going to use. What else are we missing in this program right here? Could I ask somebody from-- Yeah, down here. 

STUDENT: Int main void. 

CARTER ZENKE: Int main void, right. So I'll type int main and void up here. And this just symbolizes-- this is the kind of when flag clicked block in Scratch. This is going to be the main part of our program here. We're defining this new function called Main that will be the main part of our program. 

Now, the first thing we want to do is probably prompt the user for some information. So what functions did you all use to get the user's name, or that contact's name we're trying to story here? Could I ask over here? Yeah, go ahead. 

STUDENT: Get string. 

CARTER ZENKE: Get string. And how did you make your variable in this case? 

STUDENT: So because our variable is a string, I put string. And then I titled my variable name. 

CARTER ZENKE: Nice. 

STUDENT: And then I said equals get string what's your name. 

CARTER ZENKE: Get string, what's your name. So something like this? 

STUDENT: With a space after the name. 

CARTER ZENKE: Yeah, and why would you have that space there? 

STUDENT: Just for readability. 

CARTER ZENKE: Just readability, right? If we don't have that space there, if we maybe remove this, the user will be typing in their name right up against that question mark there, which is not what we want to have happen here. 

So it seems pretty logical to represent a name with a string. But how about the age here? Can I go maybe to this side of the room? How did you all work on getting the users the contact's age? Yeah. 

STUDENT: I did int age equals get int, and then in brackets I had-- 

CARTER ZENKE: What's your age with a space, right? And then the semicolon. Perfect. So that'll close that statement. And again, this function on the right will be called. It will run and then give us back some return value, which is whatever the user typed in, and store it inside of this variable named age. And then comes one with some-- question here? 

STUDENT: Can we also write string age [INAUDIBLE]? 

CARTER ZENKE: Yeah, so did you try that one here? 

STUDENT: Yeah, what's the [INAUDIBLE]? 

CARTER ZENKE: Good question. So we could do either of these here. One is an integer. One is a string. But you could imagine, if I later wanted to do something like this, let's say I wanted to actually increase every person's age in my phone by one, maybe it's their birthday next year. So I say age equals age plus 1. Is that going to work with a string, do you think? 

STUDENT: No. 

CARTER ZENKE: No, because I'm going to add 1 to this quote unquote maybe 40, for example. And I can't add numbers to strings. That's not going to happen for me. So it's best when you're making these to just think about what you want to do with them as you work in your program here. So I want to maybe change my age as I go through. So I'll actually maybe make this an integer here and say get int instead. 

And now for the phone number. If you go to this middle section here, how did you all choose to represent the phone number? Yeah. 

STUDENT: Long number is equal to get long. 

CARTER ZENKE: Long number is equal to get long. And you'd ask maybe what's your phone number. 

STUDENT: Yeah. 

CARTER ZENKE: And I think I'm most curious here about why you chose a long. Why would you have that? Yeah. 

STUDENT: Because it's more than 2 billion, so you need the extra [INAUDIBLE]. 

CARTER ZENKE: Yeah, so a phone number is what? Maybe 10 digits long. And so if I had any phone number that begins with anything higher than two, that's going to be higher than two billion, which is the highest positive number I can have as an integer. So I want to actually have a long here. Yeah, question. 

STUDENT: Could you use a string to-- 

CARTER ZENKE: You absolutely could use a string. And why would maybe you advocate for using a string? 

STUDENT: [INAUDIBLE] 

CARTER ZENKE: Nice, so hyphens. You could also include, if you're maybe in different countries, plus 1 for this country code plus other country codes as well. You could even have parentheses if you'd like to put the area code in front. Yeah. 

STUDENT: Also, I think that if you use an integer or a long, you are supposed to be able to calculate stuff based on that number. And usually, you don't add stuff or divide the phone number. So there is no actual purpose to ask for a [INAUDIBLE]. 

CARTER ZENKE: Yeah, definitely. So we tend not to add things to phone numbers. So why store it as number we could add things to or subtract things to or divide or whatever we'd like, right? Good question there. 

So we have it as a string here. The string also preserves things like leading zeros. Maybe there's an odd chance that somebody has a 000 number, and we could store that with a string but not, for example, a long. We tend to remove those leading zeros in that case. Yeah. 

STUDENT: But [INAUDIBLE] to use the long [INAUDIBLE] one that doesn't really require that? 

CARTER ZENKE: If I were to say maybe long age here? 

STUDENT: Yeah. 

CARTER ZENKE: And maybe get long to have parity. Nothing bad would happen here. I'm probably just using twice as much space as I would need to. So generally, I don't think people have an age above two billion. And so I would probably want to just use a regular integer to store that value. Nice. Other questions on these representations of this information here? 

OK, so we'll go with this integer. And then just real quickly to review our format code, so let's say I wanted to print out some of this data. I could say printf. And let's say, maybe age is-- what would I then say? Maybe just call it out. 

STUDENT: %i. 

CARTER ZENKE: %i, OK. Age is %i. I'm going to put period here. Name is %s. And let's go ahead and say phone number is %s, all right? And now to store this, as we saw earlier, I could simply just put these variables in the same order I want them to show up in those placeholders here. 

So I could say, OK, age is first. So I'll say age, then name. So I'll say name. And then finally number, so I'll say number and close everything out with the semicolon here. And I were to make this, I just type make phone book and run it. I would then see this information printed back out to me on the screen as such. So questions on this before we move on. 

All right, so one of the other building blocks that we have besides these variables and representations here are these conditionals and these loops. And we saw these in lecture as well, but we'll use these now for the course's lab to work on together. 

So first thing here, we have this question. Have I called less than one time? And if I have, then I'll say call more often. But just to get some vocabulary down here, this on the inside of that conditional is our Boolean expression. It's either yes or no. Have I called less than one time or not? 

On the outside here is that conditional itself. So conditionals have these Boolean expressions on the inside of them. I could make this a little more advanced though, and I could have this else in the middle. And what would that do for me? Could I ever execute these two things at the same time? Could I ask over here? Could I ever do these two things at the same time? Shaking your head no. Right. 

So these two things are mutually exclusive. If I have this else here, I'm saying it's either one or the other. If calls is less than 1, I will do that first thing. If it's not, I will do that second thing. You can chain these statements together if you saw-- even in Scratch. 

You could say if and then else if and then else if, and finally, it's long else. In general, we have these if statements followed by these else if statements, followed by if you need them, that final else to say, like a catch all for everything else that we could happen have happen here. 

For loops though, if you wanted to do something multiple times, we have something that looks a bit like this, this while loop. And what would this print to the screen? Could I ask somebody from maybe this side of the room? What would you see on the screen with this loop here? Yeah, go ahead. 

STUDENT: 0, 1, 2, 3 up to 9. 

CARTER ZENKE: Up to 9, and why not the 10? 

STUDENT: Because it's while i is less than 10. 

CARTER ZENKE: Nice. Yeah, so we wouldn't see the 10 because we're going to stop while-- we're going to stop if this is not true. And so 10 is not less than 10, so we would stop and we wouldn't do the code on the inside, right? 

So to break things down even further, we have our initialization of this loop. I is first set to 0. Then we have our Boolean expression, this question we're going to ask, either yes or no. Is this case true or is it not? And then finally, this implementation, changing that value as we go through. And finally, when our Boolean expression is no longer true, we will not be inside of that loop there. 

This is really handy. We can actually try to make our code run a certain number of times. And this is so handy that C actually has our own syntax to write this kind of loop in even abbreviated format. So here we call a for loop that has all those same elements but now just on one clean line. We have this initialization, this Boolean expression, and then this incrementation here. 

And we'll do whatever a piece of code is on the inside as long as this Boolean expression is true. So questions on this kind of syntax for these loops? Pretty good. 

And finally, I just wanted to get a little more advanced. We have this-- yeah, go ahead. 

STUDENT: I have a question [INAUDIBLE]. Why int [INAUDIBLE] parentheses [INAUDIBLE]? 

CARTER ZENKE: Good question. So you saw the int here? 

STUDENT: Yeah. 

CARTER ZENKE: And why is that there, right, because previously, we had the int i already done for us, right? So these are actually two different contexts. So here, I have created this variable named i, and I'm going to use it inside of this loop. And this variable i, because it's outside of this while loop, will persist as we go through my program. So I could use this variable i again. 

In the for loop though, if I were to create this variable i anew, I can only use it inside this for loop. I could not use it outside of that for loop. So as long as it's inside for loop, I can't use whatever variable I create here outside of it. It has to be limited to the inside of that for loop there. Does that help? Great. Other questions here too. 

STUDENT: I see no semicolon at the end of the for loop. 

CARTER ZENKE: Yeah, why is there no semicolon? Well, probably a rule of thumb is this. Semicolons come after complete statements. And this for loop is kind of setting up some set of statements. It's saying, I'm going to eventually have something I want to do, but it's not there yet. So I'm going to actually have these braces to tell what statements I want to execute sequentially as I go through. 

So you'll get used to this as you go through and write more code. But in general, statements end with a semicolon, but things that set up statements generally don't. They might have these braces, yeah. Yeah. 

STUDENT: So you mentioned [INAUDIBLE] variable i only exists within the parameter. 

CARTER ZENKE: Exactly. 

STUDENT: Does that mean when you do multiple for loops in a row not with [INAUDIBLE]? 

CARTER ZENKE: Yeah, it's a good question. So let's say if I go back to my actual programming environment here, let's say I have a loop. And I'm going to say four int i equals 0. i is less than 10. i++. So now, I can access i inside of these two braces. That's something called scope. It's a scope of the variable. It persists in this space here. 

I can't use i out here. So I can't access it there, but I could, for example, have another for loop on the inside. I could say for int j equals i. That's totally valid because i's inside this loop. Maybe j is less than 10 in this case, and then j++. And I do something else in that. 

And actually, j is not accessible here. I can't do that, but it is accessible inside that loop there. Other questions here too? Yeah. 

STUDENT: I'm a little confused. Where's the part that, I guess, senses what i is? It just appears [INAUDIBLE]. 

CARTER ZENKE: Yeah, can you tell me what you mean by senses what i is? 

STUDENT: Right, so because it's like a Boolean expression, right, whether i is greater than 1 or less than 1, like that kind of thing. So where's the input of whether it's going to be 1 or i what value it is? 

CARTER ZENKE: Yeah, so probably best to think of it like this, where my code is read top to bottom. And when it gets to this for loop, it's read kind of left to right. So the first time I get to this for loop, I'm going to make this variable i and set it to 0. Then I'm going to ask the question, is i less than 10? OK, it is, so I'll actually go inside this for loop and maybe run this code on the inside. 

Once I get to the bottom of this for loop here, I'll then go to the top. And I'll do this. I'll increase i by 1. And I'll ask the question again. Is i less than 10? It is. OK, I'll do this code again. Once it finishes, I'll increase i by 1 again, ask the question, keep going, and keep going. Does that help? 

STUDENT: OK, got it. So the input was i equals 0 first, and then [INAUDIBLE]. 

CARTER ZENKE: Exactly, this is our initialization. This is the first time for loop runs, set it to this value. Every time this code on the inside finishes running, ask-- or actually, before we start running this code, ask this question. If this is true, run this code. And we get to the bottom, increase i by 1 or do whatever is here, yeah. 

STUDENT: This should do it 10 times? 

CARTER ZENKE: This should do it 10 times, right? 0, 1, 2, 3, 4, 5, 6, 7, 8, 9. It won't do 10 because that is not less than 10. 

STUDENT: Is this called a do while? 

CARTER ZENKE: It's called a for loop just because of the 4 on the-- right there. Yeah, but we do have the do while loop, if we could go just quickly to that one here. The do while loop has the words do while in it, right? And what this is going to do is actually not ask a question first. Just unconditionally, run this piece of code and then ask the question later. 

And this is handy for trying to get some input from the user because it'll always ask the user that question. What input do you want to give me? And then maybe reprompt them, depending on whether that input is invalid or not what you want it to be, all right? 

So down here we would say this is the condition under which our input is invalid. And we should go back up and do it all over again. So questions on these kinds of loops still. Yeah. 

STUDENT: Would this be good, the do-while loop if you were to-- you were asking a question within the while loop that didn't say you're doing [INAUDIBLE] same with [INAUDIBLE] while loop give a given number? Would there be an easier way to terminate the function if say you don't [INAUDIBLE] the right age? 

CARTER ZENKE: And by terminate do you mean like-- 

STUDENT: Terminate the funct-- like it just stops. If you use-- say you're looking for the age range from 25 to 30, and then if it's in there, you go to the while loop. Would you then have the while loop-- would there be a way to stop the while loop from [INAUDIBLE]? 

CARTER ZENKE: And so, if I'm understanding what you're asking correctly, it's often better to check for what we don't want to have happen than to check for what it is we do want to have happen. So for example, I might not want to do this. I might not want to say int age is get int age, here. And then ask the question, if, let's say, age is between-- what did you say, like 15 and 20? 

STUDENT: Yeah. 

CARTER ZENKE: If age is between 15 and 20, then do the rest of my program because what I'm doing here is I'm separating my program from-- I'm indenting it by a lot, and maybe I have more conditions. Maybe I also want to say, if the name starts with A, and then it keeps getting more and more indented. 

So what I could do instead is I could do something like this. I could say, well, let me do this. Let me create this variable named age. Let me get some value for it. Whoops. Let me get some value for it. And while the age is not what I want, let me keep reprompting. Is that answering your question? 

STUDENT: Yeah, i got it, yeah. 

CARTER ZENKE: OK, so age is like less than 15, or age is greater than 20. Let me reprompt, right? OK. Yeah. 

STUDENT: Is that [INAUDIBLE] to write age less, equal, between? Or is it better time to say age less [INAUDIBLE]? 

CARTER ZENKE: Probably depends on the context. So the question was, is it better style to use this less than or this less than or equal to? In general, when you're writing for loops, where you just want something to repeat a certain number of times, we tend to use the less than and always start at 0. 

So let's say I want something to repeat five times. I'll say int i equals 0, i is less than 5, i++. And the math on this just works, right? 0, 1, 2, 3, 4, that's five times. If I were to do something like this, let's say int i is 1, then I'd have to do less than or equal to 5. And because programmers start counting at 0, meaning this absence of anything. It's starting from the very basics. We're not going to actually have this less than or equal to sign here. Is that helpful? Yeah. OK. 

All right, so with these building blocks of these loops, we'll spend some time working on our lab for the next 10 minutes or so. In our lab-- if I go back to my slides here-- we're going to be asking this question of how many llamas do we currently have? And how many years will take us to get to an aspirational number of llamas, some gold number of llamas for ourselves here? 

So if we look at this, you can find the lab at this URL right here. It's on the course website. Go to the lab page. And in that lab, you'll find these questions. Actually, sorry. Within this lab page, you're going to work on this problem all together. But we'll get started working on this up front here. 

So the first thing that we'll do for this lab is think about how we're going to work an example ourselves, and then walk through and write our code. When you're working on your problems, often good to think about how you're going to write your algorithm first, and then write your code. 

So these seven steps can help you, whether you're working on the lab, in the problem set, or so on. And notice how more than half of these are about writing things down, thinking through them, not necessarily programming. But these final three steps are all about translating that idea into code. So we'll do that here today. 

If we look at our llamas, we have a certain number of llamas. We want to figure out how many years it'll take to get to another number of llamas. And we know that every year, maybe a third of our llamas are born, and 1/4 of our llamas sadly pass away, right? And let's take a look at this particular example here. 

We have 12 llamas. And so in this current year, 12 over 3 new llamas will be born, and 12 over 4 llamas will pass away. And the question is, how many years will it take to get to 13 llamas? So to work this example, we have these 12 llamas. And now, what would we do? We want to birth a 1/3 llamas. So how many more will we add here? 

STUDENT: Four. 

CARTER ZENKE: Four, OK, let's add 4. And how many would pass away? 

STUDENT: Three. 

CARTER ZENKE: Three, so we'll take away 3 here. And we are at 13 llamas now, right? And that was one year overall. We birthed our four more llamas, and three llamas passed away. Now, we're at 13. 

So as you go and write this program, we'll get started up here in a minute. We want to first prompt the user for this starting number of llamas, ask them for a goal number of llamas, and then do some math perhaps in a loop to figure out how many years it will take to get to that goal number of llamas, and finally, print out that number of years. 

So if you are in your code space, you might go over to your environment here. You might type code population.C to open up that file. Here I have mine. You might then type, include standardio.h to print something to the screen later on. And you might also do the cs50 library, cs50.h here as well. 

What else do we need for this boilerplate code? 

STUDENT: Int main. 

CARTER ZENKE: Int main void, right? So I'll say int main void. And I'll leave this rest up to you, but make sure you're asking-- your prompting the user for a starting number of llamas, prompting them for an ending number of llamas, and then finally, maybe using some kind of loop to figure out how many years it will take to get to the goal. And keep in mind that every year a 1/3 of our current llamas are born and 1/4 pass away. 

All right, so work on this for, let's say, 10 minutes or so. And we'll come back and work the example together. 

OK, so I hope you've made some good progress on this lab. Let's come back and work the example together. We had a few steps to work through, the first one being prompting the user for a starting number of llamas. And could I ask maybe a group from this side of the room, maybe towards the back, if you don't mind, how did you prompt the user for your starting number of llamas? Yeah, go ahead. 

STUDENT: So the first [INAUDIBLE] start. And we ran a do-while loop. So it says starts equals get int and then start size. And then the condition was while the start was less than 9. 

CARTER ZENKE: Gotcha, so while start is less than 9. And why did you choose less than 9 for that case? 

STUDENT: Because the lab said that the minimum number that the start size could be was 9 or else the population would fail to grow. 

CARTER ZENKE: Right, so we want to reprompt the user if they give us a number less than 9, right? That seems pretty good. And then similarly, how could we prompt them for an ending number of llamas? Could I ask maybe in the middle this time, somebody from maybe the back few rows, how did you try to prompt for an ending number of llamas here? Yeah, go ahead. 

STUDENT: I created an int variable called n. 

CARTER ZENKE: Nice. 

STUDENT: And then I used a do-while loop. [INAUDIBLE] had n equals get int, and then end size. And then the condition for the while was while end was less than start. 

CARTER ZENKE: Yeah, and then just to ask you why would you have that in your conditional down there? 

STUDENT: Because in the lab it wanted us to keep prompting if the ending size that the user inputs is less than starting point. 

CARTER ZENKE: Yeah, totally. So we can't have fewer llamas than we began with. So just checking to make sure that is the case here. And if not, we reprompt the user. 

And then our final bit down here was keeping track of how many years it will take to get to our goal number of llamas now stored in this variable called end. And how did you all choose to represent the year, or how many years have passed in your program? Could I ask somebody from this side of the room now? What kind of variable did you use to count the number of years here? Maybe somebody from the first few rows. Yeah, go ahead. 

STUDENT: As an integer. 

CARTER ZENKE: As an integer, and did you give it a special name or anything? 

STUDENT: i called it int years. 

CARTER ZENKE: Int years, OK. And what did you set it first to? 

STUDENT: Zero. 

CARTER ZENKE: Zero, OK. And now we have some math to do. If we look maybe-- this group [INAUDIBLE] mind. How did you all add llamas, subtract them? How did you adjust your population of llamas as the years went on? Any ideas for how you might do it or how you did do it? Yeah, go ahead. 

STUDENT: Just add 112 llama each year. 

CARTER ZENKE: Added 112 llamas each year. Nice. So can you tell me, if we look at our program here, we have a starting number of llamas, so how would you adjust that here? 

STUDENT: You would go, like you said, at start-- 

CARTER ZENKE: Start. 

STUDENT: It would be start equals-- I'm sorry, plus equals. 

CARTER ZENKE: Start plus equals. 

STUDENT: Start divided by 12. 

CARTER ZENKE: Start divided by 12. And how did you get start divided by 12? What kind of math did you do to get there? 

STUDENT: Common denominator of 1/3 and 1/4. And then you're adding 1/3 and subtracting 1/4. 

CARTER ZENKE: Nice, so ultimately, every year we're just adding 1/12 new llamas after we add a 1/3 and subtract a 1/4. It comes out to 1/12 new llamas every year. But we need some kind of loop to run this. Anyone want to help me out here with this final piece? How do we have the loop to increase this-- llama, know when to stop too. Yeah. 

STUDENT: We could do while start is less end [INAUDIBLE] start. And after that [INAUDIBLE] add [INAUDIBLE]. 

CARTER ZENKE: Yeah, and so add 1 to year? 

STUDENT: Yeah. 

CARTER ZENKE: Yeah, so we could say years++ for increase years by 1. And at the very end we ultimately want to print out the number of years. So I'll say printf %i. And maybe just to clarify, years percent and then years down at the bottom here, with a backslash n at the end. 

And if I make this make population, run ./population, I'll type in maybe 12 and 13. And I get one year, as we expected. Yeah, question or comment. 

STUDENT: What is the plus equal [INAUDIBLE] start plus equal start? 

CARTER ZENKE: Good question. This is basically shorthand for doing this. I could say start equals start + start over 12 because I'm trying to add to start as we go through. So this plus equals is simply saying, let me add to what start currently is this value on the right-hand side. Does that makes sense? 

STUDENT: Yes, thanks. 

CARTER ZENKE: Gotcha. 

Now, there's one question here, which is, let's say, I have-- oh, yeah, go ahead, somewhere over here. Yeah. 

STUDENT: I have a question regarding this start in line 12. We have one part that is the [INAUDIBLE] form and one part that is [INAUDIBLE] our time. Therefore, you need to round the first part and then round the second part because you cannot have half a llama die and 1/3 being alive. So in some cases, where the number is divisible by one part of it and not divisible by the other, could create some differences. 

CARTER ZENKE: Yeah, so maybe it is better for us to add start over 3 and then subtract maybe start over 4 

STUDENT: Yeah, but what if you-- 

CARTER ZENKE: --and keep going. 

STUDENT: --round these numbers? I guess divided by 3 [INAUDIBLE] or 3.3333. So you need to round it 3 because, otherwise, you cannot have 1/3 of a llama [INAUDIBLE]. 

CARTER ZENKE: Yeah, we don't want 1/3 third of a llama. So we got to round this in some way. And I think what we want to do is always round down, which brings us to some feature or, in some cases, a bug in C-- you might run into this-- called truncation. And we didn't see this as much in lecture, which to highlight it here, in C, when you divide two integers, you will always get back an integer. 

So if I divide perhaps maybe 2 and 3, 2 divided by 3, both integers, I won't get 2/3. I'll get 0. Always round down, cut off the rest of that data there. So to show an example of this, I might do code truncation.c. And I will have the same boilerplate code, standardio.h. I'll include cs50.h. 

And I'll say int main void. And I'll type in maybe int a is, let's say, 2. Int b is 3. And let's print out the result of dividing them like this. Let's say-- actually, sorry, int c is a divided by b. And I'll say this gets the result c here. I'll say make truncation and do ./truncation. And I'll get 0 and not 2/3. 

So always rounding down here. If I do want the decimal though, what I can do is I can convert on the fly one of these to a decimal. So I could say, actually, I want a to be a float and then complete this division. And as long as one of your numbers is a float, you'll get a float in the very end. 

So I'll say maybe %f here. I'll do make truncation. Whoops. Let me say this is actually now a float in the end. Make truncation, I'll say ./truncation, and I will get that 0.6667. If I were to not do this, if I were to not do this, I would get 0 all around. So just something to keep in mind as we go through here. 

Happy to stick around and answer any questions that you all have, but this should bring us to the end of our lab today and our super section as well. Thank you all for coming. It's wonderful to see you here. Hope to see you next week in section.