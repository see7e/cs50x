---
title: LECTURE3 - TRANSCRIPT
tags: studies, programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[FILM REEL] [MUSIC PLAYING]

DAVID MALAN: All right, this is CS50. And this is Week 3 already, wherein we'll take a look back actually at Week 0 where we first began. And in Week 0, recall that everything was very intuitive, in a sense. We talked not just about representation of information, but algorithms. And we talked about tearing a phone book again and again. And that somehow got us to a better solution.

But today, we'll try to start formalizing some of those ideas and capturing some of those same ideas not in pseudocode just yet, but in actual code as well. But we'll also consider the efficiency of those algorithms, like just how good, how well-designed our algorithms actually are. And if you recall, when we did the phone book example wherein I first had an algorithm searching one page at a time, and then second one two pages at a time, and then third, started tearing the thing in half, recall that we, with a wave of the hand, kind of analyzed it as follows.

We proposed that if the x-axis here is the size of the problem, like number of pages in a phone book, and the y-axis is the time required to solve the problem in seconds, minutes, page tears, whatever your unit of measure is, recall that the first algorithm, which is the straight line such that if you had n pages in the phone book, it might have this slope of n-- and there's this one-to-one relationship between pages and tears. Two pages at a time, of course, was twice as fast, but still really the same shape, the yellow line here indicating that yeah, it's n over 2, maybe plus 1 if you have to double back, as we discussed. But it's really still fundamentally the same algorithm one or two pages at a time.

But the third algorithm, recall, was this one here in green, where we called it logarithmic in terms of how fast or how slow it was. And indeed, the implication of this algorithm was that we could even double the size of the phone book, and no big deal-- one additional page tear, and we take yet another 1,000 page bite out of the phone book. So today, we'll revisit some of these ideas, formalize them a bit, but also translate some of them, ultimately, to code.

And all of that now is possible because we have this lower-level understanding, perhaps, of what's actually inside of your computer. This, of course, is your computer's RAM or memory. And recall that if we start to abstract this away, your computer's memory is really just a grid of bytes. In fact, we don't have to look at the hardware anymore. And we looked at a grid of bytes like this, whereby each of these bytes could be used to store a char, an int, a long, or even an entire string, at that.

But let's focus perhaps just on a subset of this because last week, of course, we emphasized, really, arrays, storing things in arrays. And that allowed us to start storing entire strings, sequences of characters, and even arrays of integers if we wanted to have multiple ones and not just multiple variables as well. But the catch is that if you look inside of an array in the computer's memory-- and for instance, suppose these integers here are stored-- it's pretty easy for us humans to glance at this and immediately find the number 50. You sort of have this bird's eye view from where you're seated of everything on the screen. And so it's pretty obvious how you get to the number 50.

But in the world of computers, of course, it turns out that this is hardware. And computers, for today's purposes, can only do one thing at a time. They can't just take it all in and find instantly some number like 50. So perhaps a decent metaphor is to consider the array of memory inside of your computer really is a sequence of closed doors. And if the computer wants to find some value in an array, it has to do the digital equivalent of opening each of these doors one at a time.

Now how can code do that? Well, of course, we introduced indices or indexes last week, whereby we, by convention, call the first element of an array location 0, the second location 1, the third location 2, and so forth-- so-called 0 indexed. And this allowed us to now bridge this conceptual world of what's going on in memory with actual code, because now we had this square bracket syntax via which we could go searching for something if we so choose.

And it turns out, if I now paint these red instead of yellow, it would seem that we actually have a pretty good physical metaphor here standing in place for what would be a computer's array of memory if, for instance, you're storing some seven numbers like that. And so today we begin with a look of a specific type of algorithm. That is for searching.

Searching is all over the place. All of us have probably gone to google.com or some equivalent already multiple times per day. And getting back answers fast is what companies like Google are really good at. So how are they doing that? How are they storing information in computers' memory?

Well, let's consider what this really is. It's really just a problem as it was back in Week 0. The input, though, to the problem, for now, might be this array of seven lockers. So that's the input to the problem, inside of which is a number. And maybe for simplicity now, we just want a yes/no, a true/false answer-- a bool, that is to say-- of whether or not some number like 50 is in that array. It's not quite as fancy as Google. That doesn't just tell you yes, we have search results. It actually gives you the search results. But for, now we'll keep it simple, and just output as part of this problem yes or no, true or false, we have found the number we're looking for given an input like that array.

But it turns out inside of this black box that we keep coming back to, there's all sorts of possible algorithms. And we talked about this at a high level conceptually in Week 0 with the phone book. But today, let's consider it a little more concretely by way of a game that some of you might have grown up with, namely Monopoly. And so behind these doors, it turns out, will be hidden some denominations of monopoly money. But for this, we now have two volunteers. If you'd like to greet the world?

JACKSON: Hi, I'm Jackson.

STEPHANIE: Hi, my name is Stephanie.

DAVID MALAN: And do you want to say a little something about yourselves-- years, house, dorm?

STEPHANIE: I'm a first year living in Matthews.

DAVID MALAN: Nice.

JACKSON: And I'm a first year in Canaday.

DAVID MALAN: Nice. Well, welcome to our two volunteers. So why don't we do this? Would one of you like to volunteer the other to go first?

STEPHANIE: I'll go.

DAVID MALAN: OK. All right, so Stephanie's up first. And behind one of these doors here, we've hidden the monopoly money 50. And so we'd like you to find the 50. We'll tell you nothing more about the lockers. But we would like you to execute a certain algorithm. And in fact, I'm going to give you some pseudocode for this. And I'm going to give you the name for it.

It's called linear search. And as the name implies, you're pretty much going to end up walking in sort of a straight line. But how are you going to do this? Well, let me propose that in a moment, your first step will be to think kind of like a loop.

For each door from left to right, what do we want you to do on each iteration? Well, if 50 is behind that door, then we want to go ahead and have you return true. And hold up the 50 proudly, if you will, for the group. Otherwise, if you get through that whole loop and you haven't found the number 50, you can just throw up your hands in disappointment. False-- you've not found the number 50.

So to be clear, step one is going to be for each door from left to right. How would you like to begin? Yep. Oh, and then-- yep. There we go. Yep. And if you'd like to at least tell-- good, good acting here. What have you found instead?

STEPHANIE: It's not 50, but 20.

DAVID MALAN: Oh, OK. So step one was a fail. So let's move on to step two. Inside of this loop, what are you going to do next?

STEPHANIE: I'm going to move to the next door.

DAVID MALAN: OK.

STEPHANIE: Almost.

DAVID MALAN: OK, almost. Sort of. A 500 instead. Next locker?

STEPHANIE: I would rather take that. No.

DAVID MALAN: OK, we're not telling the audience?

STEPHANIE: It was a 10.

DAVID MALAN: OK, so keep going. This is step three now.

STEPHANIE: Oh, man.

DAVID MALAN: Five, OK. A few more lockers to check.

STEPHANIE: A little sad, guys.

DAVID MALAN: All right, second-to-last step.

STEPHANIE: It's 1. Kind of close.

DAVID MALAN: All right. And finally, the last step. Clearly you've been, perhaps, set up here.

STEPHANIE: Let's go!

DAVID MALAN: All right, so the number 50. And Stephanie, if I may, let me ask you a question here. So on the screen, this is the pseudocode you just executed. Suppose, though, I had done what many of us have gotten to the habit of doing when you have an if condition. You often have an else branch as well. Suppose that I had done this now. And I'm marking it in red to be clear this is wrong. But what would have been bad about this code using an if and an else, might you say? Any instincts?

STEPHANIE: Then you would end up canceling the code before you found the 50.

DAVID MALAN: Yeah, exactly.

STEPHANIE: I mean, you'd just be eternally sad.

DAVID MALAN: Indeed. When Stephanie had opened the first locker, she'd have found 20. 20, of course, is not 50. She would have decreed false. But of course, she hadn't checked all of the rest of the lockers. So that would seem to be a key detail that, with this implementation of the pseudocode, we actually do go through-- as we did-- and only return false not even with an else, but just at the end of the loop such that we only reach that line if we don't return true earlier than that.

Well, let's go ahead and do this. Let me take the mic from you. If you'd like to take a seat next to Jackson? And Jackson, in just a moment, we'll have you come up. Carter, if you don't mind reorganizing the lockers for us. But in the meantime, let me point out how we might now translate that same idea to code.

Pretty high level, pretty English-oriented with that pseudocode-- but really now, as of last week, we have syntax via which Stephanie and, soon, Jackson could treat this locker, this set of lockers, as really indeed an array using bracket notation. So we can now get a little closer in our pseudocode to actual code. And the way a computer scientist, for instance, would translate fairly high level English pseudocode like this to something that's a little closer to C or any language that supports arrays would be a little more cryptically like this. But you'll see more of this syntax in the coming days.

For i from 0 to n minus 1-- this is still pseudocode. But that's the English-like way of expressing what we've known come to know as a for loop. If 50 is behind doors bracket i-- so I'm assuming for the sake of discussion that doors, now, is the name of my variable, this array of seven doors. But then the rest of the logic, the rest of the pseudocode really is the same way.

And so you'll find in time that programmers, computer scientists more generally, when you start expressing ideas, algorithms to someone else, instead of maybe operating at this level here, you now have a new vocabulary, really a new syntax that you can be a little more specific, not getting so into the weeds of writing actual C code, but at least now doing something that's a little closer to manipulating an array like this. So Jackson, would you like to stand on up? All right.

Yes, yes. Support for Jackson here, too. Nice. And here now, I'm going to allow you an assumption that Stephanie did not have. Stephanie clearly was really doing her best searching from left to right using linear search, as we'll now call it. But they were pretty much in a random order, right? There was a 20 over there, there was 1 over there, and then a 50. So we deliberately jumbled things up and did not sort the numbers for her.

But Carter kindly has just come up to give you a leg up, Jackson, by sorting the numbers in advance. And we'd like you this time, much like in week 0, to do something again and again, but this time using what we'll now call binary search. It's exactly the same algorithm conceptually as we did in Week 0. But if we translate it to the context of this array, we now might say something like this.

The first step for Jackson might be to ask the question-- if 50 is behind the middle door, where presumably he's done some mental math to figure out what the middle is, then he's going to just return true. And hopefully we'll get lucky and 50 will be right there. Of course, there's two other possibilities at least, which would be what? 50 is, with respect to these doors?

Yeah, so to the left or to the right, alternatively. So if 50 is less than the middle door, then presumably, Jackson's going to want to go left. Else, if 50 is greater than the middle door, he's going to want to go right, much like I did physically last week with the phone book, dividing and conquering left to right.

But there's actually a fourth case. Let's put it on the board first. What else might happen here that Jackson should consider? Yeah. Oh, it's not there. So let me actually go back and amend my pseudocode here and just say Jackson, if we don't hand you any doors at all, or eventually, as he's dividing and conquering, if he's left with no more doors, we have to handle that situation so that the behavior is defined. All right, so with that said, Jackson, do you want to go ahead and find us the number 50 and walk us through verbally what you're doing and finding?

JACKSON: All right, so it looks like this one is the middle door. So I'm going to open it. But it's 20, not 50.

DAVID MALAN: Aw. What's going through your head now?

JACKSON: So now I'm looking-- because 50 is higher than 20, I want to look to the right.

DAVID MALAN: Good.

JACKSON: And look for the new middle door, which would be here.

DAVID MALAN: Nice.

JACKSON: And it's 100-- bad. But 50 is less than 100. So now we to look left, which would be here. And ta-da.

DAVID MALAN: Nice. Very well done this time around, too. So thank you, first, to our volunteers here. And in fact, since you're a fan of Monopoly, as we're so informed, we have the Cambridge edition of Monopoly with all your Harvard favorites.

JACKSON: No way.

DAVID MALAN: Here you go.

STEPHANIE: Thank you.

JACKSON: Thank you so much.

DAVID MALAN: Thank you to our volunteers for finding us 50. So-- that was more popular than we expected. So here, we can translate this one more time into something a little closer to code. And again, still pseudocode-- but here, now, might be another formulation of exactly what Jackson just did, just using the nomenclature now of arrays, where you can be a little more precise with your instructions and still leave it to someone else to translate this, finally, to code.

But here we have same question at the beginning. If no doors left, return false. If 50 is behind doors bracket middle-- so I'm assuming here, because this is pseudocode-- that somewhere I've done the mental math or the actual math to figure out what the index of middle is. For instance, if these are seven doors in an array, this would be location 0, 1, 2, 3, 4, 5, 6.

So somehow I've taken the total number of doors, 7, divided by 2 to find the middle. That's 3 and 1/2. We have to deal with rounding. But suffice it to say there's a well-defined formula for finding the middle index. Given the total number of lockers, divide by 2 and then round accordingly. So that's presumably what Jackson did just by counting or in his head to find us door number 3. Not the third door, the 4th door, but door bracket 3.

So this is just saying if 50 is behind doors bracket middle, return true. That was not the case. He found a $20 bill instead. Else, if 50 is less than the doors bracket middle, go ahead-- and now it gets interesting-- search doors 0 through doors middle minus 1. So it's getting a little more into the weeds now. But if middle is 3, this one here, what we want to now have Jackson search if 50 had been-- if the number had been less, we want to start at bracket 0 and go up through this one. And we deliberately subtract 1 because what's the point of looking in the same locker again? We might as well do 0 through middle minus 1.

Else if 50 is greater than doors bracket middle, which it was, what did we then do? So Jackson intuitively searched for doors middle plus 1 through doors n minus 1. And honestly, it gets a little annoying having the pluses and minuses here. But just think of what it means. This is the middle door. And Jackson then did proceed to search through doors middle plus 1 because there's no point in searching this one again.

And then the last element in any array of size n where n is just our go-to number for the size is always going to be n minus 1. It's not going to be n. It's going to be n minus 1 because we always start counting arrays at 0. So here then we have a translation into pseudocode that's a little closer to C of this exact same idea. And here, we come full circle to Week 0.

In Week 0, it was pretty intuitive to imagine dividing and conquering a problem like this. But if you now think back to actual your iPhone, your Android phone, or the like, when you're doing autocomplete and searching the list, it's possible, if you don't have many friends or family or colleagues in the phone, you know what? Linear search, just checking every name for the person you're searching for, might be perfectly fine.

But odds are your phone's being smarter than that, especially if you start to have dozens, hundreds, thousands of people in your contacts over the years. What would be better than linear search? Well, perhaps binary search. But, but, but-- there's an assumption, a requirement, which is what? Why was Jackson ultimately able to find the 50 in just three steps instead of a full seven, like Stephanie?

Because the array was sorted. And so this is sort of a teaser for what we'll have to come back to later today. Well, how much effort did it take someone like Carter? How much effort does it take your phone to sort all of those names and numbers in advance? Because maybe it's not actually worth the amount of time.

Now someone like Google probably somehow keeps the database of web pages sorted. You can imagine it being super slow if, when you type in cats or something else into google.com, if they searched linearly over their entire data set. Ideally, they're doing something a little smarter than that.

So we'll formalize, now, exactly this kind of analysis. And it's not going to be so much mathy as it still will be intuitive. But we'll introduce you to some jargon, some terminology that most any programmer or computer scientists might use when analyzing their own algorithms.

Let's formalize now what this kind of analysis is. So right now, I claim binary search better than linear search. But how much better and why, exactly? Well, it all comes back to this kind of graph. So this, recall, is how we analyzed the phone book back in Week 0. And recall that, indeed, we had these formulas, rough formulas that described the running time of those three algorithms-- one page at a time, two pages at a time, and then tearing the thing again and again in half.

And precisely, if you counted up the number of pages I was touching or the number of pages I was tearing, it's fair to say that the first algorithm, in the worst case, might have taken n total pages. It didn't because I was searching for John Harvard at the time, which is somewhat early in the alphabet. But if I were searching for someone with the last name of Z, I would have had to keep going and going, in the worst case, through all n pages.

Not as bad for the second algorithm, and that's why we do n divided by 2. And even that's a bit of a white lie. It's probably n divided by 2 plus 1 in case I have to double back. But again, I'm sort of doing this more generally to capture the essence of these things. And then we really got into the weeds with like log base 2 event for that third and final algorithm. And at the time, we claimed any time you're dividing something in half, in half, in half, odds are there's going to be some kind of logarithm involved. And we'll see that today.

But today, we're going to actually start using computer science terminology. And we're going to formalize this imprecision, if you will. We are not going to care, generally, about exactly how many steps some algorithm takes because that's not going to be that enlightening, especially if maybe you have a faster computer tomorrow than you did today. It wouldn't really be fair to compare numbers too precisely. We really want to, with the wave of a hand, just get a sense of roughly how slow or how fast an algorithm is.

So the notation here is deliberate. That is literally a capital O, often italicized, refer to as big O. And so the first algorithm is in big O of n. The second algorithm is in big O of n divided by 2. The third algorithm is in big O of log base 2 of n. But even that is kind of unnecessary detail.

When using big O notation, you really don't care about, we'll see, the smaller order terms. We're not going to care about the divided by 2 because you know what? The shape of these algorithms are is almost the same. And really, the idea-- the algorithm itself is sort of fundamentally the same. Instead of one page at a time, I'm doing two. But if you throw millions of pages, billions of pages at me, those algorithms are really going to kind of perform the same as n gets really large, goes off toward infinity.

And the same is true for logarithms. Even if you're a little rusty, it turns out that whether you do the math with log base 2, log base 3, log base 10, you can just multiply one by the other to really get the same formula. So this is only to say a computer scientist would generally say that the first two algorithms are on the order of n steps. The third algorithm is on the order of log n steps. And we don't really care precisely what we mean beyond that.

And this big O notation, as we'll see-- and actually, let me zoom out. If you can imagine suddenly making the x-axis much longer-- so more pages on the screen at once-- it is indeed going to be the shapes of these curves that matter, because imagine in your mind's eye as you zoom out, zoom out, zoom out, zoom out, and as n gets much, much, much bigger on the x-axis, the red and the yellow line are essentially going to look the same once n is sufficiently large. But the green line is never going to look the same. It's going to be a fundamentally different shape. And so that's the intuition of big O, to get a sense of these rates of performance like this.

So here, then, is big O. Here is, perhaps, a cheat sheet of the common formulas that a computer scientist, certainly in an introductory context, might use when analyzing algorithms. And let's consider for a moment which of our first two algorithms-- linear search and binary search-- fall into these categories. So I've ordered them from slowest to fastest, so order of n squared. It's not something we've actually seen yet, but it tends to be slow because it's quadratic. You're doing n times n. That's got to add up to a lot of steps.

Better today is going to be n log n. Even better is going to be n. Even better than that is log n. And best is so-called order of 1, like one step or maybe two steps, maybe even 1,000 steps, but a fixed, finite number of steps that never changes no matter how big n is. So given this chart, just to be clear, linear search-- let's consider the worst case.

In the worst case, how many steps did it take someone like Stephanie to find the solution to the problem, assuming not seven doors but n doors? Yeah? So on the order of n. And in this case, it's exactly n. But you know what, maybe it's arguably 2n because it took Stephanie a couple of steps. She had to lift the latch. She had to open the door. Maybe it's three steps. She had to show the money. So now it's 3n, 2n.

But we don't really care about that level of precision. We really just care about the fundamental number of operations. So we'll say yes, on the order of n. So that might be an upper bound, we'll call this, for linear search. And how about binary search? In Jackson's case, or in general, me in Week 0, if there's n doors, how many steps did it take Jackson or me using binary search?

In this case, it was literally three. But that's not a formula. Yeah so it's on the order of log n. And indeed, if there are seven doors, well, that's almost eight, if you just do a little bit of rounding. And indeed, if you take log base 2 of 8, that does actually give us 3. So the math actually checks out. And if you're not comfortable with logarithms, no big deal. Just think about it intuitively.

Logarithm of base 2 is just dividing something again and again. So on this chart, when we consider big O, which to be clear, allows you to describe the order of an algorithm's running time-- like the magnitude of it-- but it also describes, more specifically, an upper bound. So in the worst case, for instance, these are pretty good measures of how good-- or rather, of how bad-- linear search and binary search might be.

Why? Well, suppose you're searching a 1,000-page phonebook and the person's name starts with Z. The algorithm is still going to be on the order of n steps. Why? Because it might take you as many as all n steps to find it. Now that's not necessarily going to be the case in practice. If I use big O as an upper bound, well, it would be nice if there's a corresponding lower bound, especially if you want to consider not just worst cases, but maybe best cases.

So what might we use here? Well, this is a capital Greek omega symbol. So omega is the symbol that a computer scientist uses generally to describe a lower bound on an algorithm, often in the context of best case, though not necessarily. So a lower bound means how few steps might an algorithm take? And here, too, same formulas. And we'll fill in these blanks over time.

Some algorithms might always take a minimum of n squared steps, or on the order of n steps. Some might only take n log n, or n, or log n, or 1. So something like a linear search-- when Stephanie started with linear search, she didn't get lucky this time on stage. But what if she had, and the first door she opened were 50? How might you then describe the lower bound on linear search in this so-called best case, using this list of possible answers? Yeah?

Yeah, so omega of 1. So in the best case, the lower bound on how many steps it might take linear search to find something might just be one step. Why? Because maybe if Stephanie had gotten lucky and we had prefilled these lockers with the numbers in some other order such that she might have opened the first locker, and voila, the number 50 could have been there, so a lower bound arguably could indeed be omega of 1 for linear search.

And how about now for Jackson? He used binary search. So he dived right into the middle of the problem. But what would be a lower bound on binary search using this logic? Yeah?

Yeah, so again, omega of 1. Why? Because maybe he just gets lucky. And indeed, right in the middle of the lockers could have been the number 50. It wasn't. And so more germane in Jackson's actual practice would have been the big O discussion. But big O and omega, upper bound and lower bound, just allow a computer scientist to kind of wrestle with what could happen maybe in the worst case, what can happen in the best case? And you can even get even more precise like the average case or the like.

And this is, indeed, what engineers might do at a whiteboard in a company, in a university when designing an algorithm and trying to make arguments as to why their algorithm is better than someone else's, by way of these kinds of analyses. And just so you've seen it, it turns out that if some algorithm happens to have an identical upper bound and lower bound, you can actually use a capital Greek theta as well. And this is the last of the Greek symbols today. But a Greek theta indicates a coincidence of both upper bound and lower bound. That is, they are one and the same. That was not the case for our discussion a second ago of linear search, not the case for binary search. But you could use the same kinds of formulas if it turns out that your upper bound and lower bound are the same.

So for instance, if I were to count everyone literally in this room-- one, two, three, four, five, six and so forth-- you could actually say that counting in that way is in theta of n because in the best case, it's going to take me n points, people in the audience. In the worst case, it's going to take me n. It's always going to take me n steps if I want to count everyone in the room. You can't really do better than that unless you skip people. So that would be an example of the cuff of something where theta is instead germane.

Are any questions now on big O, on omega, or theta, which are now just more formal tools in the toolkit for talking about the design of our algorithms? Any questions? No? Seeing none. Oh, is this-- yes? No? OK, so we're good.

So let's go ahead and translate this, perhaps, to some actual code. Let me go over to VS Code here. And let's see if we can't now translate some of these ideas to some actual code, not so much using new syntax yet. We're going to still operate in this world of arrays like last week.

So let me go ahead and create a program called search.c by executing code space search.c in my terminal. And then up here, let's go ahead and include our usual, so include cs50.h so I can get some input. Include standard io.h so I can print some output. We'll do int main void, the meaning of which we did start to tease apart last week. The fact that it's void again today just means no command line arguments.

And let me go ahead and do this. Let me go ahead and declare, just for discussion's sake, a static array, like an array that never changes. And the syntax for this is going to be give me an array called numbers using the square bracket notation. And I'm going to immediately initialize it to 20, 500, 10, 5, 100, 1, and 50, reminiscent of those same denominations as before.

So this is a slightly new syntax that we've perhaps not seen. And the curly braces here, which are different from for loops and while loops and functions, just tell the compiler please give me an array of whatever size this is containing those numbers left to right. I could alternatively use last week's syntax of saying something like this. Let's see, 1, 2, 3, 4, 5, 6, 7 denominations. I could alternatively do this. And then I could say numbers bracket 0 equals 20, numbers bracket 1 equals 500. And I could do this five more times.

That's just a little tedious. If you know the numbers in advance, you don't have to tell the compiler how many there are. You can just let it figure it out that your numbers will be 10, 500, 10, 5, 100, 1, and 50. So this is how you statically define an array.

All right, let me just go ahead and ask the user now for a number. We'll call it n by using get_int and prompting them for a number-- so nothing new there. And now let me go ahead and implement linear search. And the pseudocode we had for this before used some array-like notation. Let me go ahead, then, and start similarly. For int i-- and you almost always start counting at i by convention. So that's perhaps a good starting point.

I'm going to do this so long as i is less than 7. Not the best design to hard code the 7, but this is just for demonstration's sake for now, because I know how many numbers I put in there. And then I'm going to i++. So now I have the beginnings of a loop that will just allow me to iterate over the entire array.

And let me ask this. If the current number at location i equals equals n, which is the number the human typed in, then let's go ahead and do something simple like printf, quote unquote, found, backslash n. And then per our discussion last week, to indicate that this is successful, I'm going to return 0 if I found it. And if I don't find it, I'm just going to go down here and, by default, say not found, backslash n.

And just for convention-- whoops, just for good measure, per convention, I'll return 1 or, really, any value other than 0. 0, recall, means success. And any other integer tends to mean error of some sort, irrespective of the number I'm looking for. So just to revisit, the only thing that's new here is the syntax.

We're creating an array of seven numbers, these numbers. And then after that we have really highlighted here an implementation of linear search. I mean this is the C version, I daresay, of what Stephanie did on the board, whereas now the array is called numbers instead of doors. But I think it's pretty much the same.

Let me go ahead and open my terminal window and run make search. Seems to compile, ./search. And let's go ahead and search for a number. We'll start with what we did before, 50. And it's found. Let's go ahead and run it again, ./search. Let's search for maybe 20 at the beginning. That one, too, is found.

Let's run it one more time searching for like 1,000, which is not among the denominations. And that one, indeed, is not found. So we've taken an idea from Week 0, now formalized in Week 3, and just translated it now to code. Questions on this implementation of linear search? Linear search. Nothing. Oh, so successful so far today.

So let's see if we can't maybe make this a little more interesting and see if we can't trip over a detail that's going to be important in C. And instead of doing numbers, let me go ahead and do this. We'll stay on theme with Monopoly. And I went down the rabbit hole of reading the Wikipedia article on Monopoly. And the original pieces or tokens that came with Monopoly-- and it turns out we can represent those with strings.

So I'm going to create an array called strings, plural, of whatever size I defined here. And the very first monopoly pieces back in the day were a battleship that you could play with, a boot, a cannon, an iron, a thimble, and a top hat, some of which you might from the game nowadays. Turns out they've been changing these-- had no idea-- over the years.

So here is, now, an array of strings. Let me go ahead and prompt the user now not for an integer anymore. I want to now search for one of these strings still using linear search. So let me create a string s, set it equal to get_string, prompt the user for a string to search for. And then I think my code here is almost the same, except for one detail. I now have an array called strings. I now have a variable called s.

But it turns out, for reasons we'll explore in more detail next week, this line of code is not going to work. And it turns out the reason has to do with what we discussed last week of what a string really is. And what is a string, again?

A string is an array. And it turns out, though, that equals equals is not going to generously compare all of the characters in an array for you just because you use equal equals. It turns out it's not going to compare every letter. And so thankfully, there is, in the string library that we introduced last week, a solution to this problem. The reason for the problem, we'll explore in more detail next week.

But for now, just know that when you want to compare strings in C-- especially if you've come into the class knowing a bit of Java or Python or some other language-- you cannot use equals equals. Even though you could in Scratch, you cannot in C. So what I have to actually do here is this. I have to ask the question, does the return value of a function called str compare, or strcomp, equal 0 when passed in the current string and that's user input?

So if you read the documentation for this function called str compare, you'll see that it takes two strings as input, first one and second one. It then-- someone decades ago wrote the code that probably uses a for loop or a while loop to compare every character in each of those strings. And it turns out it returns 0 if they are, in fact, equal. Turns out, too, it will return a positive number or a negative number in other situations.

Any intuition for why it might actually be useful to have a function that allows you to check if two strings are equal? If they're not equal, what else might be interesting to know when comparing two strings? If certain values are?

STUDENT: [INAUDIBLE]

DAVID MALAN: OK, possibly. Maybe you want to just how similar they are. And that's indeed an algorithm unto itself. But str compare is a little simpler than that.

STUDENT: [INAUDIBLE]

DAVID MALAN: Exactly, if you're trying to alphabetize a whole list of strings, just like your phone probably is for your contacts or address book. It turns out that str compare will actually return a positive number or a negative number or a 0 based on whether, maybe it comes alphabetically first or later, or in fact, equal. So that can be a useful thing. And that's just a teaser for a lower level explanation that we'll see next week.

So now, let me cross my fingers and see if I got this right. Let me go ahead and do make search. Did compile, albeit slowly. Dot slash search, and let's search for something like the thimble. And we see that that's, indeed, found.

Otherwise, let's search for something that I know isn't there, like a race car, which was there when I grew up. But huh, segmentation fault, core dumped. And actually, some of you have tripped over this error before. Anyone want to admit seeing this? So yeah, not something we've talked about, and honestly, not something I intended just now. But that too, we'll see next week.

Any intuition for why my program just broke. I didn't really change the logic. It's still linear search. Let me hide the terminal so you can see all of the code at once. The only thing I did was switched from integers to strings. And I switched to str compare here.

But segmentation fault happened. And the teaser is that that somehow relates to the computer's memory. Yeah.

STUDENT: [INAUDIBLE]

DAVID MALAN: Yeah, and this is subtle, but spot on. So one, two, three, four, five, six elements total in this array, versus the seven numbers of monopoly denominations that we had earlier. And this is where, see? Sort of case in point, this came back to bite me.

The fact that I hardcoded this value as opposed to maybe separating it out as a constant or declaring it higher up, kind of bit me here, because now, I'm iterating over an array of size 6. But clearly, I'm going one step too far, because I'm literally going to iterate seven times, not six. So it's as though I'm looking at memory that's over here.

And indeed, next week, we'll focus on memory. And that's just a bad thing. So odds are, not even seeing your code from this past week, if any of you have had segmentation faults, odds are, you touched memory that you shouldn't have. You maybe looped too many times. You might have used a negative number to get into your array.

In general, you touched memory that you shouldn't have. And you touched a segment of memory that you shouldn't have. The fix, though, at least in my case, is simple. Just don't do that.

So let me go ahead and recompile this. Make search dot slash search. And I'll search again for race car, Enter. And now it does not crash. But it does tell me it's not found. So subtle, but something you might yourself have tripped over already. Questions then, on what I just did, intentionally or otherwise. Yeah, in front.

STUDENT: One thing is the program still works if you do return-- if you don't do return 0, return 1. So what is the purpose of doing [INAUDIBLE]?

DAVID MALAN: A really good question. So the program will still work even if I don't return 0 or return 1. In fact, let me go ahead and do that and just hide my terminal window for a second. Let's get rid of the return here. Let's get rid of the return here.

However, watch what happens here. Let me go ahead and recompile this, make search. Let me scroll up in my code here. Let me go ahead and do dot slash search. And let me go ahead and search for the first thing in the list, battle ship, so I know that this should be found.

I hit Enter. Huh, interesting. So it's saying found not found. But do you see why, logically, in this case?

STUDENT: Is the loop still running?

DAVID MALAN: Exactly. So the loop is still running. So there's a couple of solutions to this. I could, for instance, somehow break out of the code here. But that's going to still result in line 18 executing. I could then instead just return here.

I don't strictly need to return 1 down at the bottom. But I made this claim last week that it tends to be helpful as your programs get more sophisticated, to at least signify, just like a real world programmer, error codes when something goes wrong. So returning 0 in main is the easiest way to signify my code is done. I'm ready to exit successfully, that's it.

But down here, I could absolutely still return 0, because that's not a huge deal. It's not really an error that deserves annoying the user with some kind of pop up that something went wrong. But return 1 is just a lower level way of signaling, eh, it didn't really find what I was looking for. And remember from last week, you can see this as follows.

If I recompile this again, now that I've reverted those changes, so make search. And if I do a dot slash search and search for battle ship, which is indeed found, recall I can execute this magical command, echo dollar sign question mark, which you're not going to often execute. But it shows you what main returned.

If I run search again and search for race car, which is not found, I see not found, but I can also run this command again and see that, oh, it returned 1. So now if you fast forward a few months, a few years, when you're actually writing code in a company or for larger projects, you might want to be automating software. You might not want the human to necessarily be running it manually.

You might want code to be automated by some nightly process or something like that. Using these exit codes, can a program determine yes or no that other code succeeded or failed. Other questions on linear search in this way.

No? All right, well, let's translate this to one other feature of C here by incorporating these two ideas now into one other program. So I'm going to create a phone book in C by doing code space phonebook dot C. And let's combine some of these ideas and implement this notion of searching a phonebook for an actual name and getting back a number.

So I'm going to go ahead and quickly include some of the same things, cs50.h so we can get input. standard io dot h so we can print output. And I'm going to preemptively include string.h in case we need that one as well. int main void, no need for command line arguments today.

And let me give myself, now, an array of names for this phone book. So string names equals. And then in curly braces, how about Carter will be one person in the phone book, and David, myself, will be the other. So we'll keep it short so we don't have to type too many names.

But this is a phone book with two people thus far. Suppose, now, we want to also store Carter's phone number in mind. So it's not just saying found or not found. It's literally looking up our phone numbers like a proper phone book.

Well, at the moment, there's really no way to do this. I could do something hackish like I could put a number like 617-495-1000 after Carter. I could maybe do something like 949-468-2750 after me. But now you're kind of doing the whole apples and oranges thing.

Now, it's not strings. It's a string int, string int. All right, so maybe I could just make all of these strings. But now it's just a conceptual mixing of apples and oranges. Like yes, that's an array of four strings. But now you're on the honor system to know that the first string is a name, the second string is a number, the third string is-- you can do it. But it's a bit of a hack, so to speak.

So what might be cleaner than this? Instead of combining our phone numbers into the same array as our names, what else might we do that's perhaps a little better? Say it little louder.

A 2D array, possibly something we could do. I'm going to keep it even simpler now, because we haven't used those by name, even though that is, we saw last week, technically what argv is. What else could I do if I want to store names and numbers? Yeah.

STUDENT: [INAUDIBLE]

DAVID MALAN: Yeah, let me go with this suggestion. It's a little simpler. Rather than complicate things in literally different dimensions, let me go ahead and do string. Well, I could do int numbers.

But you know what? So that we can support punctuation like dashes or even parentheses or country codes, I'm going to do this instead. I'm going to do string numbers so that I can represent Carter's number as quote unquote plus 1 for the US, 617-495-1000, complete with hyphens, as is US convention.

And then for mine I'll go ahead and do +1-949-468-2750 semicolon. And now down below, let's actually enable the user to search this phone book, just like in week 0 we did. String name equals get string. And let's ask the user for a name, presumably David or Carter or someone else.

And now let's re-implement linear search. So 4, int i get 0. i is less than 2. And do as I say, not as I do. I think we should beware this hard coding, but we'll keep it simple for now. i++. And then in this for loop, I think we have all of the ingredients to solve this.

So if the return value of str compare of all of the names bracket i comparing against the name that the human typed in, if all of that equals equals 0, that is, all of the characters in those two strings are equal, then I think we can go ahead and say found, just like last time. But you know what? Let's actually print Carter's or my phone number.

So found percent s, and we'll plug in numbers, bracket i. And then just for consistency, I'll return 0 here. And down here, how about I'll say something like printf not found, just to be clear. And then I'll return 1 as well.

So just to recap, here's all of the code. It's almost the same as before, except now it's useful. I'm not just saying found or not found. I found a number in monopoly, or I found a piece in monopoly. I'm looking up in one array, one of the strings. And then I'm printing from the other array, the answer.

So let me go ahead here and run the compiler, make phone book, Enter. OK, that's promising, no errors. Dot slash phonebook now. And let's search, for instance, Carter Enter. All right, so we found Carter's number. All right, let me do that again.

Phone book, let's search for David. All right, we seem to have found David's number. All right, let's do it one last time. Phone book, Enter. And now we'll search for John Harvard. Enter, not found.

All right, so I daresay, albeit with minimal testing, this code is correct. Would anyone now like to critique the design? Does something rub you the wrong way, perhaps, about this approach here?

And as always, think about how, if the program maybe gets longer, more complicated, how decisions like this might unfold. Yeah.

STUDENT: If i is less than 2.

DAVID MALAN: OK, so if i is less than 2, so technically, if I change the number of people in this phone book, I'm going to have to update i. And we've already seen that I get myself into trouble. So that's bad design. Good.

STUDENT: Say you add someone's name to the phonebook, but you don't have the corresponding number. So then when you go to pull their number, it [INAUDIBLE] someone's number.

DAVID MALAN: Yeah. So again, I'm sort of trusting myself not to screw up. If I add John or anyone else to the first array but I forget to add their number to the second array, eventually things are going to drift and be inconsistent. And then code will be incorrect at that point. So sort of a poor design setting me up for future failure, if you will. Other thoughts? Yeah.

STUDENT: [INAUDIBLE] so if you were to switch the order of the numbers but not the main [INAUDIBLE]

DAVID MALAN: Yeah, really good. We're assuming the same order. From left to right, the names go, and from left to right, the numbers go. But that's kind of just the honor system. Like, there's literally nothing in code preventing me from reversing the order for whatever reason, or maybe sorting the names.

Like, they're sorted now, and maybe that's deliberate, but maybe it's not. So this honor system here, too, is just not good. I could put a comment in here to remind myself, note to self, always update arrays the same way. But like, something's going to happen eventually, especially when we have not two, but three, but 30, 300 names and numbers. It would be nice to keep all of the related data together.

And so in fact, the one new feature of C we'll introduce today is one that actually allows us to implement our very own data structures. You can think of arrays as a very lightweight data structure, in that it allows you to cluster related data back to back to back to back. And this is how strings are implemented.

They are a data structure effectively implemented with an array. But with C and with other languages, it turns out you can invent your own data types, whether they're one dimensional, two dimensional even, or beyond. And with C, can you specifically create your own types that have their own names?

So for instance, wouldn't it have been nice if C came with, not just char and int and floats and long and others. Wouldn't it be nice if C came with a data type called person? And ideally, a person would have a name and a number.

Now, that's a little naive and unrealistic. Like, why would they define a person to have just those two fields. Certainly, people could have disagreed what a person is. So they leave it to us.

The authors of C gave us all of these primitives, ints and floats and strings and so forth. But it's up to us now to use those in a more interesting way so that we can create an array of person variables, if you will, inside of an array called people, just to pluralize it here. So how are we going to do this? Well, for now, let's just stipulate that a person in the world will have a name and a number that we could argue all day long what else a person should have. And that's fine. You can invent your own person eventually.

At the moment, I'm using just two variables to define a person's name and number. But wouldn't it be nice to encapsulate, that is, combine these two data types, into a new and improved data type called person. And the syntax for that is going to be this.

So it's a bit of a mouthful. But you can, perhaps, infer what some of this is doing here. So it turns out C has a keyword called typedef. As the name kind of suggests, this allows you to define your own type.

Struct is an indication that it's a structure. It's like a structure that has multiple values inside of it that you are trying to define. And then at the very bottom here outside of the curly braces, is the name of the type that you want to create.

So you don't have discretion over using typedef or struct in this particular case. But you can name the thing whatever you want. And you can put anything in the structure that you want as well.

And as soon as the semicolon is executed at the bottom of the code, every line thereafter can now have access to a person data type, whether as a single variable, or as an entire array. So if I want to build on this then, let me go ahead and do this. Let me go back to my C code here. And I'm going to go ahead and change just a couple of things.

Let's go ahead and do this. I'm going to go ahead and, first, get rid of those two hardcoded arrays. And let me go ahead and, at the top of my file, invent this type, so typedef struct. Inside of it will be a string name and then a string number. And then the name of the structure will be person. And best practice would have me define it at the very top of my file so that any of my functions, in fact, could use it, even though I just have main in this case.

Now, if I wanted, I could do this. Person P1 and person P2. But we know from last week, that already is bad design. If you want to have multiple instances of the same type of variable, we should probably use what instead?

STUDENT: [INAUDIBLE]

DAVID MALAN: And--

STUDENT: An array.

DAVID MALAN: Yeah, an array. So let me not even go down that road. Let me instead just do this. Person will be the type of the array. But I'm going to call it-- I could call it persons. But in English, we typically say people. So I'll call the array people. And I want two people to exist in this array, though I could certainly change that number to be anything I want.

How, now, do you put a name inside of a person and then put the number inside of that same person? Well, slightly new syntax today. I'm going to go ahead and say this.

People bracket 0 just gives me the first person in the array. That's not new. But if you want to go inside of that person in memory, you use a dot. And then you just specify the name of the attribute therein.

So if I want to set the first person's name to Carter, I just use that so-called dot notation. And then if I want to set Carter's number using dot notation, I would do this, +1-617-495-1000. And then if I want to do the same for myself, I would now do people bracket 1 dot name equals quote unquote David.

And then people bracket 1 still dot number equals quote unquote +1-949-468-2750. And now, at the bottom of my file, I think my logic can pretty much stay the same. I can still, on this line here, prompt the user for the name of the person they want to look up. For now, even though I admit it's not the best design, I'm just doing this for demonstration's sake, I'm going to leave the two there, because I know I have two people.

But down here, this is going to have to change. I don't want to compare names bracket i anymore. What do I want to type here as the first argument to str compare? What do I want to do here? Yeah.

STUDENT: People i dot name.

DAVID MALAN: So people i dot name, yeah. So I want to go into the people array at the ith location, because that's what my loop is doing. It's updating i again and again. And then look at name, and that's good. I think now I need to change this too.

What do I want to print if the person is found? Someone else? What do I want to print here, if I found the person's name? Yeah.

STUDENT: [INAUDIBLE]

DAVID MALAN: Say it a little louder.

STUDENT: People i dot number.

DAVID MALAN: Perfect. So people bracket i dot number, if indeed I want to print the corresponding number to this person. And then I think the rest of my code can stay the same. So let me go ahead and rerun make phone book to recompile this version. So far so good. Dot slash phone book.

Let's go ahead and type in Carter's name, found. All right, let's go ahead and run it again. David's name, found. Let's go ahead and run it one more time. Type in John Harvard, for instance, not found, in this case.

So fundamentally, the code isn't all that different. Linear search is still behaving the same way. And I admit, this is kind of ugly looking. We've kind of made a two line solution five lines of code now.

But if we fast forward a week or two when we start saving information to files, we'll introduce you to files like csv files, comma separated values, or spreadsheet files, which you've surely opened on your Mac or PC at some point in the past. Suffice it to say we'll soon learn techniques for storing information, like names and numbers, in files.

And at that point, we're not going to do any of this hackish sort of hard coding of the number 2 and manually typing my name and Carter's name and number into our program. We'll read the information dynamically from a file. And in a few weeks, we'll read it dynamically from a database instead.

But this is, for now, just syntactically how we can create an array of size 2 containing one person each. We can update the name and number of the first person, update the name and the number of the second person, and then later search across those names and print out the corresponding numbers. And in this sense, this is a better design. Why? Because my person data type encapsulates, now, everything that it means to be a person, at least in this narrow world.

And if I want to add something to the notion of a person, for instance, I could go up to my type def, and tomorrow, add an address to every person and start reading that in as well. And now it's not the honor system. It's not a names array, a numbers array, an addresses array, and everything else you might imagine related to a person. It's all encapsulated, which is a term of art inside of the same type.

Reminiscent, if some of you have programmed before, of something called object-oriented programming. But we're not there yet. C is not that. Questions on this use of struct or this new syntax, the dot operator being really the juicy part here. Any questions? Yeah.

STUDENT: [INAUDIBLE]

DAVID MALAN: On what line number?

STUDENT: 16.

DAVID MALAN: 16? So yes, so syntactically, we introduced the square brackets last week. So doing people bracket 0 just means go to the first person in the array. That was like when Stephanie literally opened this door.

That's doors bracket 0. But this is, of course, people bracket 0 instead. Today, the dot is a new piece of syntax. It means go inside of that person in memory and look at the name they're in and set it equal to Carter and do the same for number.

So that's all. It's like, open the locker door, go inside of it, and check or set the name and the number. Yeah.

STUDENT: [INAUDIBLE] can you set default values for each of the [INAUDIBLE]?

DAVID MALAN: Attributes is fine. Good question. In the struct, can you set default values? Short answer, no. And this is where C becomes less feature-able than more modern languages like Python and Java and others, where you can, in fact, do that.

So when we transition to Python in a few weeks' time, we'll see how we can start solving problems like that. But for now, it's up to you to initialize name and number to something. Yeah.

STUDENT: [INAUDIBLE]

DAVID MALAN: Really good question. How can we adjust or critique the design of what I'm doing? This is one of the few situations where I would say, hypocritically, do as I say, not as I do. I am using pretty ugly lines like this, just to introduce the syntax.

But my claim, pedagogically today, is that eventually, when we start storing names and numbers or other things in files or in databases, you won't have this redundancy. You'll have one line of code or two lines of code that read the information from the file or database and then fill the entire array with that data. For now, I'm just doing it manually so as to keep our focus only on the new syntax, but that's it.

So forgive the bad design by design today. Other questions on this? All right, that's been a lot already. Why don't we go ahead and take our 10 minute break with snacks first. We have some delightful brownies in the lobby.

All right, we are back. And up until now, it clearly seems to be a good thing if your data is sorted, because you can use binary search. You know a little something more about the data.

But it turns out that sorting in and of itself is kind of a problem to solve too. And you might think, well, if sorting is going to be pretty fast, we absolutely should do it before we start searching, because that will just speed up all of our searches. But if sorting is slow, that kind of invites the question, well, should we bother sorting our data if we're only going to search the data maybe once, maybe twice? And so here is going to be, potentially, a trade off.

So let's consider what it means really to sort data. In our case, it's just going to be simple and use numbers. But it might, in the case of the Googles of the world, be actual web pages or persons or the like. So here is our typical picture for sorting, for solving any problem. Input at left and output at right.

The input to our sort problem is going to be some unsorted set of values. And the output, ideally, will be the same set of values sorted. And if we do this concretely, let's suppose that we want to go about sorting this list of numbers, 7, 2, 5, 4, 1, 6, 0, 3.

So it's all of the numbers from 0 to 7. But they're somehow jumbled up randomly. That's going to be the input to the problem. And the goal is now to sort those so that you, indeed, get out 0, 1, 2, 3, 4, 5, 6, 7 instead.

So it turns out there's lots of different ways we can actually sort numbers like these here. And in fact, just to complement our search example earlier, could we perhaps quickly get some eight volunteers to come up if you're comfortable appearing on the internet? If you want to do 1, 2, 3, 4, 5, 6, 7, 8, how about? All right, come on down.

All right. Come on over here, and I'll give you each a number. And if you want to start to organize yourselves in the same order you see the numbers on the board. So look up on the overhead and organize yourselves from left to right in that same order.

And let's have the first of you-- perfect. If you want to come right over here, how about right in line with this? All right, and a few more numbers. All right.

Number 2, 6, and perfect. Just the right number, all right. Uh oh. All right, there we go, number three.

All right. So let's just do a quick check. We have 7, 2, 5, 4, 1, 6, 0, 3, very good so far. Do you want to just scootch a little this way just to make a little more room? All right, and let's consider now who we have here on stage. You want to each say a quick hello to the audience?

RYAN: Hi, my name is Ryan. I'm a first year from Pennypacker.

ITSELLE: Hi, my name is Itselle. I'm a first year at Strauss.

LUCY: Hi, my name is Lucy. And I'm a first year from Greenough.

SHILOH: Hi, my name is Shiloh. I'm a first year in Wigglesworth.

JACK: Hi, my name is Jack. And I'm a first year in Strauss.

KATHRYN: Hi, my name is Kathryn. I'm a first year at Strauss.

MICHAEL: Hi, my name is Michael. I'm a first year at Pennypacker.

MUHAMMAD: Hi, my name is Muhammad. I'm a first year in Matthews.

DAVID MALAN: Hi, nice, welcome aboard. All right. So let's consider, now, how we might go about sorting our kind volunteers here, the goal being to get them into order from smallest to largest so that, presumably then, we can use something smarter than just linear search. We can actually use binary search, assuming that they are already then sorted.

So let me propose that we first consider an algorithm that actually has a name called selection sort. And selection sort is going to be one that literally has me, or really you, as the programmer, selecting the smallest element again and again, and then putting them into the appropriate place. So let me go ahead and start this here, starting with the number 7.

At the moment, 7 is the smallest number I've found. So I'm going to make mental note of that with a mental variable, if you will. I'm going to move on now. Number 2 is obviously smaller, so I'm just going to update my mental reminder that 2 is now the smallest, effectively forgetting, for now, number 7.

5, not smaller. 4, not smaller. 1, smaller. And I'm going to make mental note of that. 6, not smaller. 0, even smaller. I'll make mental note of that, having forgotten now everything else. And now number 3 is not smaller. So what's your name again?

MICHAEL: Michael.

DAVID MALAN: So Michael is number 0. He belongs, of course, way down there. But unfortunately-- you are--

RYAN: Ryan.

DAVID MALAN: Ryan is in the way. So what should we do? How should we start to sort this list? Where should number 0 go? Yeah. Do you want to say it louder?

STUDENT: I will swap, I think.

DAVID MALAN: Yeah, so let's just go ahead and swap. So if you want to go ahead and 0, go on where 7 is. We need to make room for number 7. It would kind of be cheating if maybe everyone kind of politely stepped over to the side.

Why? Because if we imagine all of our volunteers here to be an array, like, that's a crazy amount of work to have every element in the array shift to the left just to make room. So we're going to keep it simple and just evict whoever's there now. Now, maybe we get lucky, and number 7 is actually closer to its destination. Maybe we get unlucky, and it goes farther away.

But we've at least solved one problem. If we had n problems at first, now we have n minus 1, because number 0 is indeed in the right place. So if I continue to act this out, let me go ahead and say 2, currently the smallest. 5, no, 4, no, 1 currently the smallest. I'll make mental note.

6, 7, 3, and now let me pause. 1 is obviously the now smallest element. So did I need to keep going? Well, turns out, at least as I've defined selection sort, I do need to keep going, because I only claim that I'm using one variable in my mind to remember the then smallest element.

I'm not smart enough like us humans to remember, wait a minute, 1 is definitely the smallest now. I don't have that whole recollection. So I just am keeping track of the now smallest.

So number 1, your name was?

JACK: Jack.

DAVID MALAN: Jack, where should Jack go? Probably there. And what's your name?

ITSELLE: Itselle.

DAVID MALAN: OK, so Jack and Itselle, if you want to swap places, we've now solved two of the n total problems. And now we'll do it a little faster. If each of you want to start to swap as I find the right person, so 5 smallest, 4 smaller, 2 is smaller. Got to keep checking. OK, 2 was smaller.

All right, now I'm going to go back to the beginning. All right, 4 is small. 5 is not. 6 is not. 7-- oh, 3 is small. Where do you want to go? OK, good. I'm going to go back here. And I can be a little smart.

I don't have to go all the way to the end, because I know these folks are already sorted. So I can at least optimize slightly. So now 5 is small. 6 is small. 7 is 4, 4 is smaller. If you want to go in place there.

And now, here things get interesting. I can optimize by not looking at these folks anymore, because they're obviously problem solved. But now 5 is small, 6 is not, 7 is not. OK, 5, you can stay where you are.

Now, a human in the room is obviously going to question why I'm wasting any more time. But with selection sort, as I've defined it thus far, I still have to, now, check 6 is smallest, not 7. And now my final step, OK, they're all in place.

So here, too, is this dichotomy between what we all have is this bird's eye view of the whole problem, where it's obvious where everyone needs to go. But a computer implementing this with an array really has to be more methodical. And we're actually saving a step here.

If we were really doing this, none of these numbers would be visible. All eight of our volunteers would be inside of a locked door. And only then could we see them one at a time. But we're focusing now just on the sorting aspect.

So let me just, before we do one other demonstration here, propose that what I really just did here in pseudocode was something like this. For i from 0 to n minus 1, keeping in mind that 0 is always the left of the array. n minus 1 is always the right end of the array.

For i from 0 to n minus 1, I found the smallest number between numbers bracket i and numbers bracket n minus 1. And that's the very geeky way of expressing this optimization. I'm always starting from numbers bracket i wherever I am. And then everything else to the right. And that's what was allowing me to ignore the already sorted volunteers. If, though, my last line says swap smallest number with numbers i, think that implements what our humans were doing by physically walking to another spot.

All right, so that, then, would be what we'll call selection sort. Let's go ahead and take a second approach here using an algorithm that I'm going to call bubble sort. But to do this, we need you all to reset to your original locations. We have a little cheat sheet on the board if you'd like to go back to this position here.

And let me take a fundamentally different approach, because I'm not really liking selection sort as is, because it's kind of a lot of walking back and forth. And the lot of walking suggests a lot of, lot of steps again and again. So what might I do instead? Well, bubble sort is going to have me focus a little more intuitively on just smaller problems.

And let's see if this gets me somewhere else. So if I just look at this list without looking at everyone else, 7 and 2, this is obviously a problem. Why? Because you're out of order.

So let's just solve one tiny problem first. So 7 and 2, why don't you swap? I know 2 is in a better place now, because she's definitely less than 7. So I think I can now move on.

7 and 5, problem. So let's solve that. 7 and 4, problem. Let's solve that, 7 and 1, let's solve that. 7 and 6, let's solve that. 7 and 0, solve that. 7 and 3, solve that.

OK, done. Sorted, right? Or obviously not, if you just glance at these numbers here. But we have, fundamentally, taken a bite out of the problem. 7 is indeed in the right place. So we maximally have n minus 1 other problems to solve.

So how do I do this? I think I can just repeat the same logic. Let me go over here. 2 and 5, good. 5 and 4, no. 5 and 1, no.

5 and 6, yes. 6 and 0, no. 6 and 3, no. So now we've solved two of the problems. And what's nice about bubble sort, at least as this glance, it's nice and simple. It's nice and local.

And you just keep incrementally solving more and more problems. So let's go ahead and do this again. And I'll do it-- we can do it faster. 2 and 4, we know are good.

4 and 1, 4 and 5, 5 and 0, 5 and 3, 5 and 6, 6 and 7, good. So we go back, 2 and 1. Ah, now another problem solve. 2, and 4, 4 and 0, 4 and 3, 4 and 5, 5 and 6, 6 and 7.

And so notice 2, as per its name, the largest elements have bubbled their way up to the top. And that's what seems to be happening just as we're fixing some remaining problems. So almost done.

1 and 2, 2 and 0, 2 and 3, 3 and 4, 4 and 5, 5 and 6, 6 and 7, almost done. Obviously, to us humans, it looks done. How do I know as the computer for sure? What would be the most surefire way for me to now go, it's not done, sorry. That's a bug.

OK, 1 and 0, 1 and 2, 2 and 3, 3 and 4, 4 and 5, 5 and 6, 6 and 7. OK, so now it's obviously sorted to the rest of us on stage. How could I confirm as much as code? You're doing it with your mind, just glancing at this. How would the computer, the code, know for sure that this list is now sorted? Yeah.

STUDENT: [INAUDIBLE] one more time.

DAVID MALAN: Let's do one more time. And look, draw what conclusion?

STUDENT: That nothing has to switch at all.

DAVID MALAN: Yeah, let's do it one more time, even though it's a little wasteful. But logically, if I go through the whole list comparing pairs again, again, and again, and I don't do any work that time, now it's obviously logically safe to just stop, because otherwise, I'm wasting my time doing the same thing again and again if no one's actually moving.

So I'm afraid we don't have monopoly games for all of you. But we do have eight stress balls. And round of applause, if we could, for our volunteers. If you want to put your numbers on the shelf there.

So if we consider for a moment-- thank you. Thank you so much. Sure. Thank you. Thanks. Sure.

So if we consider now these two algorithms, which one is better? Any intuition for whether selection sort the first is better or worse than bubble sort the second? Any thoughts? Yeah.

STUDENT: Bubble sort's even better because it's less work [INAUDIBLE].

DAVID MALAN: So bubble sort seems like less work, especially since I was focusing on those localized problems. Other intuition? Selection sort versus bubble sort.

Well, let me propose that we try to quantize this so we can actually analyze it in some way. And this is not an exercise we'll do constantly for lots of algorithms. But these are pretty representative of algorithms.

So we can wrap our minds around, indeed, the performance or the design of these things. So here is my pseudocode for selection sort, whereby as per its name, I just iteratively select the next smallest element again and again. So how can we go about analyzing something like this?

Well, we could just do it on paper pencil and count up the number of steps that seem to be implied logically by the code. We could literally count the number of steps I was taking again and again, left to right. We could also just count the number of comparisons I was making with each of the persons involved.

And I was doing it kind of quickly in selection sort. But every time I was looking at a person trying to decide, do I want to remember that number is smallest? That number, I was comparing two values with an equals equals or less than or greater than sign, at least if we had done this in code.

So that tends to be the norm. When analyzing algorithms like these, counting the number of comparisons, because it's kind of a global unit of measure we can use to compare different algorithms entirely. So think, too, that in the general case, when we have more than eight volunteers, more than seven doors, we can generalize our array in general, as this is the first element at bracket 0. And the end of it is always n minus 1. So arrays or doors, in this case, or volunteers, are always numerically indexed from 0 on up to n minus 1, if there's n of them in total.

So how do we analyze the code of selection sort? Well, how many steps did it take me to find the first smallest element? Or more precisely, how many comparisons did I need to make when I walked to left to right to find our first-smallest person, which ended up being 0?

How many comparisons did I do when walking left to right? If there were eight people on stage, how many total comparisons that I do? Like if there's eight people, I compared these folks. Then this person, this person, yeah.

Yeah, so seven total, right? Because if there's eight people on stage, you can only do seven comparisons total, because otherwise you'd be comparing one number to itself. So it seems like, in the general case, if you've got n numbers that you're trying to sort, finding the smallest element first takes n minus 1 comparisons.

Maybe n total steps left to right. But the number of comparisons, which I claim, is just a useful unit of measure, is n minus 1. How about finding the next smallest person? How many steps did it take me to find the next smallest number, which ended up being the number 1? Yeah.

STUDENT: [INAUDIBLE] n minus 2.

DAVID MALAN: Yeah, so just n minus 2. Why? Because I'd already solved one problem. Someone was already in the right position. It would be silly to keep counting them again and again. So I can whittle down my number of comparisons for the next pass to n minus 2.

The third pass to find the third smallest number would be n minus 3. And then dot, dot, dot, presumably this story, this formula, ends when you have just one final pair, the people at the end, to compare. So if this is looking a little reminiscent of some kind of recurrence from high school or high school math or physics or the like, let me just stipulate that if you actually do out this math and generalize it, that is the same thing as n times n minus 1 divided by 2.

And if you're rusty on that, no big deal. Just kind of commit to memory that any time you add up this kind of series, something plus something slightly smaller, plus something slightly smaller, each of which differs by 1, you're going to get this formula. n times n minus 1 over 2. If we, of course, multiply that out, that's really n squared minus n, all divided by 2. If we keep multiplying it out, that's n squared divided by 2 minus n over 2.

And now, we have kind of a vocabulary with which we can talk about the efficiency, the design of this algorithm. But honestly, I don't really care about this level of precision, like n squared divided by 2 minus n divided by 2. As n gets really large, which of these symbols, which of these terms is really going to dominate, become the biggest influencer on the total value of steps? Right? It's the square, right? It's definitely not n divided by 2. That's shaving some time off.

But n squared, as n gets big, is going to get really big. If n is 100, then n squared is bigger. If n is a million, n squared is really bigger. And so at the end of the day, when we're really just talking about a wave of the hand analysis and upper bound, if you will, let's just say that selection sort, as analyzed here, it's on the order of n squared steps.

It's not precisely n squared steps. But you know what? n squared divided by 2, the intuition here might be that, well, it's half of that. n squared is what really matters as n gets really, really large.

And that's when you start thinking about and trying to solve the Google problems of the world. When n gets large, that's when you have to be smarter than just sort of naive implementations of any algorithm. So where, then, does this algorithm fall into this categorization here? Well, n squared, it turns out, is on the order of n squared steps, in the worst case, whether it's sorted or not.

It turns out, though, lower bound, if we consider this same code, suppose the best case scenario, like our eight volunteers came up on stage. And just because they already sorted themselves, so 0 through 7. Suppose they just happened to be in that state. How many steps would selection store take to sort an already-sorted list of volunteers? Any intuition? Yeah.

STUDENT: Would it still be [INAUDIBLE]?

DAVID MALAN: Would it still be n--

STUDENT: Still be 7 [INAUDIBLE].

DAVID MALAN: So for the first pass, it would still be 7 for the first pass across the humans. Because even though, yeah, I'm claiming 0 is here, I don't know that 0 is the smallest until I make my way all the way over there doing all seven comparisons. OK, fine, first pass took seven or more generally n minus 1 steps. What if I look for the next smallest element, and the humans in this story are already sorted 0 through 7?

Well, yes, the number 1 is here, and I see them first. But I don't know they're the smallest until I compare against everyone else get to the end of the list. And we're like, oh, well that was stupid. I already had the smallest person in hand then.

And so this pseudocode, this implementation of selection sort, is sort of fixed like this. There's no special case that says, if already sorted, quit early. It's always going to take n squared steps.

And so in this case, if we borrow our jargon from earlier using omega notation, just to be clear, selection sort is also going to be in this incarnation in omega of n squared, because even in the best case, where the list is already sorted, you're going to waste a huge amount of time essentially verifying as much or discovering as much, even though we humans of course could see it right away. So selection sort would seem to take both n squared steps in the worst case, n squared steps in the best case. And so you know what? We can use our theta terminology for that.

Here would be an algorithm, just like counting earlier, that always takes n squared steps, no matter whether the array is sorted or not from the get go. All right, so hopefully we can do better. And someone proposed earlier that bubble sort felt like it was using fewer steps.

Well, let's consider that next. With bubble sort, we had this pseudocode, I claim. Whereby, let's focus on the inside of the code first. Down here, what was I doing? For i from 0 to n minus 2.

That's curious. We've never seen n minus 2 before. But I asked this question. If numbers bracket i and numbers bracket i plus 1 are out of order, swap them.

So that was when I was pointing at our first two volunteers here. I saw that they were out of order, so I swapped them. How come I'm doing that again and again up to n minus 2, though, instead of n minus 1, which we've always used up until now as our rightmost boundary? Any intuition for why I'm doing this from 0 to n minus 2? Yeah.

STUDENT: [INAUDIBLE] number, you can't get rid of the ith number. There's no benign character you can swap with.

DAVID MALAN: Exactly. Because I'm looking at the ith person per this pseudocode here and the ith plus 1 person, I better make sure I don't go step beyond the boundaries of my array. So if you think of my left hand. When my back was to you here, pointing at the current person at the first position, my right hand for this if conditioner is essentially pointing at the person next to them.

And you want to iterate with your left hand all through these people. But you don't want your left hand to point at the last person. You want it to point at the second to last person.

But we know that the last person is always at n minus 1. So the second to last person, just mathematically, is at n minus 2. So it's a subtlety. But this is a seg fault waiting to happen. If you implemented bubble sort using n minus 1, you will, my right hand would go beyond the boundaries of the array, so just bad.

All right, so why am I saying this n times? Well, we did it very organically with humans. But each time someone-- each pass I did through the array, someone bubbled their way up to the end. Number 7, then number 6, then number 5.

So if on each pass through the array of volunteers, I was solving at least one problem, it seems like bubble sort can just run n times total to solve all n problems, because the first pass will get at least one number into place. Second pass, second number into place. You might get lucky, and it would do more. But worst case, this feels like enough. Just do this blindly n times, and they'll all line up together.

Well, technically-- all right, now we're getting into the weeds. Technically, you can just repeat it in minus 1 times, because if you solve all n minus 1 other problems, and you're left with 1, literally that person's where they need to be, just logically. If you've already sorted everything else and you've got just the 1 left, it's already bubbled up.

So how do we analyze this? Well in bubble sort, we might do something like this. I'm essentially doing n minus 1 things n minus 1 times. Now, let me back up to the pseudocode, because this one's a little less obvious.

This is where you can actually mathematically infer from your loop how many steps you're taking. So this first line literally says, repeat the following n minus 1 times. So that's going to translate very straightforwardly to our mathematical formula.

Do something n minus 1 times. This loop, just because I'm using for loop terminology, it's framed a little differently. But if you're iterating from 0 to n minus 2, you're iterating a total of n minus 1 times.

And again, the arithmetic is getting a little annoying. But this just means do the following n minus 1 times. So do n minus 1 things n minus 1 times. We can now run out the math as follows.

We have the formula n minus 1 times n minus 1. We do our little FOIL method here, n squared minus 1 times n, minus 1 times n, plus 1. We can combine like terms. n squared minus 2n plus 1.

But at this point, when n gets really large, which term are we really going to care about? This is on the order of? Yeah, n squared. So at least asymptotically. Asymptotically means, as n approaches infinity, gets really large.

Turns out that the upper bound on selection sort and bubble sort are essentially the same. Now, if we really nitpicked and compared the total number of comparisons, they might differ slightly. But as n gets large, honestly, you're barely going to notice the difference, it would seem, between these two algorithms.

But what about the lower bound? If the upper bound on bubble sort is also big O of n, what about the lower bound here? Well, with this pseudocode, what would the lower bound be on bubble sort? Even in the best case when all of the volunteers are sorted. Any intuition? In this pseudo code. Yeah, in the middle.

STUDENT: Sorry, quick question. Isn't bubble sort structured such that you wouldn't need to compare numbers that have already bubbled up?

DAVID MALAN: Good question. Isn't bubble sort designed such that you wouldn't need to compare numbers that have already bubbled up? That's what's happening here in the middle, implicitly.

I'm always going from left to right. But remember that even when I screwed up at the end and the last two people were out of order, I do always need to restart at the beginning, because the big numbers are going that way, and the small numbers are coming this way.

STUDENT: [INAUDIBLE]

DAVID MALAN: So that is true. There are some slight optimizations that I'm kind of glossing over here. Let me stipulate that it would still end up being on the order of n squared.

But that would definitely shave off some actual running time here. But what if the list is already sorted? Our pseudocode, at the moment, has no allowance for if list is already sorted, quit early.

So we're going to blindly do n minus 1 things and minus 1 times unless we modify our pseudocode, as I did verbally earlier, I proposed this. Inside of that outer loop, if you make a pass across all of the volunteers, and your mental counter has made no swaps, you have to keep track with some kind of variable, well then, you might as well stop. Because if you do a whole pass and make no swaps, why would you waste time doing it again expecting different behavior?

So to help visualize these, whereby now bubble sort can be advantageous if the data is already sorted or mostly sorted. Why? Because it does have this short circuit detail. At least if we implement it like that, how can we go about visualizing these things a little more clearly? Well, let me go ahead and do this.

Let me pull up, here, a visualization of exactly these algorithms, thanks to a third party tool here that's going to help us visualize these sorting algorithms as follows. Small bars represent small numbers. Big bars represent big numbers. And so the idea, now, is when I hit a button here to get all of the small bars this way, all of the big bars this way.

So just like our volunteers. But instead of holding lighted numbers, it's bars representing their magnitude. So let's go ahead and start with, for instance, selection sort.

And you'll see in pink, is being highlighted the current number that is being selected and then pulled all the way to the left. So this is selection sort. And again, it's selecting the next smallest element. But you can see here, all the more visibly, that just like my human feet, we're taking a lot of steps.

So is this algorithm touching these elements, again and again and again. And this is why the n squared is really a thing. There's got to be some inherent redundancy here. Like, why do we keep looking at the same darn elements again and again? We do, in terms of our pseudocode need to do so. But it's this redundant comparisons that kind of explains why n squared is indeed the case.

So now it's done. Small bars here, big bars there. And I had to just keep talking there to kill time, because it's relatively slow.

Well, let me re-randomize the array, just so we start with a different order. And now let me click on bubble sort. And you'll see similar idea, but different algorithm.

So now, the two bars in pink are the two that are being compared and fixed, potentially, if they're out of order. And you can see already that the biggest bars are bubbling their way up to the top. But now, you can also see this redundancy, like we keep swooping through the list again and again, just like I kept walking back and forth.

And this is n squared. This is not that many bars. What? 10, 20, there's like 40 or something bars, I'm guessing. That's pretty slow already just to sort 40 numbers.

And I think it's going to get tedious if I keep talking over this. So let's just assume that this too is relatively slow. Had I gotten lucky and the list were almost sorted already, bubble sort would have been pretty fast. But this was a truly random array, so we did not get lucky. So indeed, the worst case might be what's kicking in here.

So I feel like it'll be anticlimactic, like holding in a sneeze, if I don't let you see the end of this. So here we go. Nothing interesting is about to happen. Almost done.

OK, done. All right, so thank you.

[APPLAUSE]

Thank you. So still somewhat slow though. How though can we, perhaps, do a little better fundamentally? So we can do so if we introduce yet another technique. And this one isn't so much a function of code as it is concept. And it's something that you might have seen in the real world, but perhaps not so obviously so.

So it turns out, in programming, recursion refers to the ability of a function to call itself. In the world of mathematics, if you have a function f, if f appears on both the left side and the right side of a formula, that would be a recursive function in the math world too. Whenever f is defined in terms of itself, or in our case, in compute-- in programming, any time a function calls itself, that function is said to be recursive.

And this is actually something we've seen already in class, even though we didn't call it as much. So for instance, consider this pseudocode from earlier, whereby this was the pseudocode for searching via binary search, a whole bunch of doors. If no doors are left returned false, that was the additional conditional we added.

But then if number behind middle door returned true, and here's the interesting part, if number is less than middle door, search the left half. Else if number is greater than middle door, search the right half. This pseudocode earlier was, itself, recursive.

Why? Because here is an algorithm for searching. But what's the algorithm telling us? Well, on this line and this line, it's telling us to search something else. So even though it's not explicitly defined in code as having a name, if this is a search algorithm, and yet the search algorithm is using a search algorithm, this pseudocode is recursive.

Now, that could quickly get you into trouble if a function just calls itself again and again and again. But why, intuitively, is it not problematic that this code, this pseudocode, calls itself? Why will the algorithm still stop? Yeah.

STUDENT: It has an exit condition, as in if there is no doors left, [INAUDIBLE].

DAVID MALAN: Exactly. It has some exit condition, like if no doors left. And more importantly, any time you search the left half, you're searching a smaller version of the problem. Any time you search the right half, you're searching a smaller version of the problem, literally half the size.

So this is why, in the phone book, obviously I couldn't tear the phone book in half infinitely many times, because it was literally getting smaller each time. So recursion is this ability to call yourself, if you will. But what's important is that you do it on a smaller, smaller problem, so that eventually, you have no more problems to solve or no more data, no more doors at all.

So these two lines here would be the recursive elements here. But if we go back to week 0, we could have used recursion in some other way. So this was our pseudocode for the phone book back in week 0. And recall that we described these yellow lines as really representing a loop, some kind of cycle again and again.

But there was a missed opportunity here. What if I had re-implemented this code to do this? Instead of saying open to middle of left half of book and then go back to line 3, like literally inducing a loop, or open to middle of right half a book and go back to line 3 inducing another loop, why don't I just recognize that what I'm staring at now is a algorithm for searching a phone book? And if you want to search a smaller phone book, like A through M or N through Z, we'll just use this same algorithm.

So I can replace these yellow lines with just this, casually speaking. Search left half of book, search right half of book. This would be implicitly, and now I can shorten the whole thing, a recursive implementation of the phone book pseudocode from week 0.

And it's recursive, because if this is a search algorithm, and you're saying go search something else, that's fine. That's recursive. But because you're searching half of the phone book, it's indeed going to get smaller and smaller.

Even in the real world or the real real virtual world, you can see recursive data structures in the wild, or at least in Super Mario Brothers like this. Let me get rid of all the distractions here and focus on this pyramid, where you have one block, then two, then three, then four. Well, this itself, is technically recursively-defined in the sense that, well, what is a pyramid of height for? Well, it's really, what? How would you describe a pyramid of height 4 is actually the same thing as a pyramid of--

STUDENT: Height 3.

DAVID MALAN: --of height 3, plus 1 additional layer. Well, what's a pyramid of height 3? Well, it's technically a pyramid of height 2 plus 1 additional layer. And so even physical structures can be recursive if you can define them in terms of itself.

Now, at some point, you have to say that if the pyramid is of height 1, there's just one block. You can't forever say it's defined in terms of a height negative 1, negative 2, you would never stop. So you have to kind of have a special case there.

But let's go ahead and translate something like this, in fact, to code. Let me go back to VS code here, and let me implement a program called iteration that refers to a loop iterating. And let me implement a very simple pyramid like that. So let me go ahead and include the CS50 library.

I'll include our standard io.h int main void, no command line arguments today. And let's go ahead and do this. Let's declare a variable called height, ask the human for the height of this pyramid. And then let's go ahead and draw a pyramid of that height.

Now, of course, draw does not yet exist. So I'm going to need to invent the draw function. Let me go ahead and define a function that doesn't have a return value. It's just going to have side effects. It's just going to print bricks on the screen, called draw. And it takes in an integer, n, as its input.

And how am I going to implement this? Well again, I want to print one block, then two, then three, then four. That's pretty straightforward, at least once you're comfortable with loops.

Let me go back to the code here. Let me go ahead and say 4, int i, get 0. i is less than n. i plus plus. And that's going to iterate, essentially row by row.

And on each row, I want to print out one, then two, then three, then four bricks. But I'm iterating from 0 to 1 to 2 to 3. So I think that's OK. I can just say something like 4 int j get 0.

j, let's be clever about this, is less than i. j++. And now, let me go ahead and, inside of this loop, I think I can get away with just printing out a single hash sign. But then outside of that loop, similar to last week, I'm going to print my new line separately.

So a little non-obvious at first. But this outer loop iterates row by row, line by line, if you will. And then the inner loop just makes sure that when i equals zero, let's see. Oh nope, there's a bug.

I need to make sure that it's j is less than i plus 1. So when i is 0 on my first line of output, I'm going to print out one brick. When i is 1, I'm going to print out two bricks and so forth.

So let me go ahead and run make iteration. All right, and now, seems to compile. Uh oh, huh. Implicit declaration of function draw. So I'm making week one mistakes again. What? Say again.

STUDENT: [INAUDIBLE]

DAVID MALAN: Yeah. The prototype is missing. I didn't declare it at the top. That's an easy fix, and the only time, really, it's OK and necessary to copy paste. Let me copy the functions declaration there and it with a semicolon. So that clang now knows that draw will exist.

Make iteration. Now it works. Thank you. dot slash iteration. We'll type in something like 4. And there we have it, our pyramid of height one, two, three, four, that looks pretty similar to this, albeit using hashes.

So that's how we would have implemented this, like, two weeks ago in week one, maybe last week, but just using arrays. But let me propose that we could do something recursively instead. Let me close this version of the code. And let me go back to VS Code and open up recursion.c, just to demonstrate something recursively.

And I'll do it incorrectly deliberately the first time. So let me include cs50.h. Let me include standard io.h. Let me do int main void. And let me just blindly draw a pyramid initially of height 1.

But now in my draw function, let me re-implement it a little differently. So my draw function this time is still going to take a number n. But that's how many hashes it's going to print. So let's do 4, int i get 0. i is less than n. i++.

Then let's go ahead and print out a single hash mark here. And then after that, let's print out the end of the line, just as before. But now this, of course, is only going to draw a single row.

It's going to print out one hash or two hashes or three hashes, but only on one line. Let me now, incorrectly, but just kind of curiously say, all right. Well, if this draws a pyramid of height 1, let's just use ourselves to draw a pyramid of height n plus 1.

So the first time I call draw, it will print out one hash. Then the second time I call draw, it will print out two hashes, then three, then four. So we're kind of laying these bricks down from top to bottom.

Make recursion. Whoops, I screwed up again. So let's copy the prototype here. Let's put this down over here, semicolon. Let's do this again.

Make recursion. All right, all good, dot slash recursion. And now let me increase the size of my terminal window, just so you can see more of the output. And here we have.

OK, bad, but thank you. So we have an infinitely tall pyramid. And it's just flying across the screen, which is why it looks kind of like a mess. But I printed out a pyramid of height 1, and then 2, and then 3, and then 4.

And unfortunately, what am I lacking any sort of quick condition, any kind of condition that says, wait a minute, when it's too tall, stop altogether. So this is an infinite loop. But it's not a loop. It's a recursive call.

And actually, doing this in general, is very bad. We'll see next week that if you call a function too many times, you can actually trigger yet another of those segmentation faults, because you're using too much memory, essentially. But for now, I haven't triggered that yet. Control C is your friend to cancel.

And as an aside, if you're playing along at home or playing with this code later, I actually cheated here. We have a special clang configuration feature that prevents you from calling a function like that and creating a problem. I overrode it just for demonstration sake. But odds are at home, you wouldn't be able to compile this code yourself.

But let me do a proper version recursively of this code as follows. Let me go back into the code here. Let me go ahead and, not just blindly start drawing one, then two, then three layers of bricks. Let me prompt the human as before for the height of the pyramid they want using our get int function.

And now let me call draw of height again. So now I'm going back to the loop-like version. But instead of using a loop now, this is where recursion gets rather elegant, if you will. Let me go ahead and execute and code the draw function as follows.

Per your definition, if a pyramid of height 4 is really just a pyramid of height 3 plus another row, well, let's take that literally. Let me go back to my code. And if you want to draw a pyramid of height 4, well go right ahead and draw a pyramid of height 3 first, or more generally, n minus 1.

But what's the second step? Well, once you've drawn a pyramid of height 3, draw an extra row. So I at least have to bite off that part of the problem myself.

So let me just do for int i get 0. i is less than n i++. And let me, the programmer of this function, print out my hashes. And then at the very bottom, print out a new line so the cursor moves to the next line.

But this is kind of elegant now, I dare say, in that draw is recursive, because I'm literally translating from English to C code, this idea that a pyramid of height 4 is really just a pyramid of height 3. So I do that first. And I'm sort of trusting that this will work.

Then I just have to lay one more layer of bricks, four of them. So if n is 4, this is just a simple for loop, a la week 1, that will print out an additional layer. But this, of course, is going to be problematic eventually. Why? It's not done yet, this program. How many times will draw call itself in this model?

STUDENT: It's infinite.

DAVID MALAN: Infinitely many times. Why?

STUDENT: Because there's no quit function.

DAVID MALAN: Yeah, there's no equivalent of quit. Like, if you've printed enough already, then quit, well, how do we capture that? Well, I don't think we want this to go negative. It would make no sense to draw a negative height pyramid.

So I think we can just pluck off, as the programmer, an easy case, an easy answer, a so-called base case. And I'm just going to do this. At the top of my draw function, let me just say, if n is less than or, heck, less than or equal to 0, that's it. Go ahead and just return. There's nothing more to do.

And that simple condition, technically known as a base case, will ensure that the code doesn't run forever. Why? Well, suppose that draw is called with an argument of 4. 4 is, of course, not less than 0, so we don't return. But we do draw a pyramid of height 3.

And here's where things get a little mentally tricky. You don't move on to line 20 until draw has been called. So when draw is called with an argument of 3, it's as though you're executing from the top of this function again.

3 is not less than 0. So what do you do? You draw 2. How do you draw 2? Well, 2 is not less than 0, so you don't return.

So you draw 1. Got to be careful here. Draw 1. And now, we go ahead back to the beginning. How do you draw 1? Well, 1 is not less than 0, so you don't return. You draw height 0.

How do you draw height 0? Wait a minute. 0 is less than or equal to 0. And you return. And so it's kind of like this mental stack, this to do list.

You keep postponing, executing these lower lines of code, because you keep restarting, restarting, restarting the draw function until, finally, one of those function calls says there's nothing to do, return. And now the whole thing starts to unravel, if you will. And you pick back up where you left off.

And this is, perhaps, the best scenario. We won't do it in class. But if you'd like to wrestle through this on your own using debug50 to keep stepping into, step into, step into, each of those lines, logically, you'll see exactly what's actually happening.

So let me go to my terminal and do make recursion, which is now this correct version of the code, dot slash recursion. Let's type in a height of 4. And voila, now we have that same pyramid, not using iteration per se, though admittedly, we're using iteration to print the additional layer. We're now using draw recursively to print all of the smaller pyramids that need come before it.

STUDENT: Can you only use recursion for void function? [INAUDIBLE]

DAVID MALAN: No. Question is, can you only use recursion with a void function? No, not at all. In fact, it's very common to have a return value like an integer or something else so that you can actually do something constructively with that actual value. Other questions on this.

STUDENT: When is line 21 getting executed?

DAVID MALAN: Say it a little louder.

STUDENT: When is line 21 getting executed?

DAVID MALAN: When is line 21 getting executed? So if you continue to-- let me scroll down a bit more so you can see the top of the code. So line 21 will be executed once line 19 is done executing itself.

Now, in the story I told, we kept calling draw again, again, again. But as soon as one of those function calls where n equals 0 returns immediately, then we don't keep drawing again and again. So now if you kind of think of the process as reversing, then you continue to line 21, then line 21 again, then line 21 again, and as the sort of logic unravels.

And next week, we'll actually paint a picture of what's actually happening in the computer's memory. But for now, it's just, it's very similar to the pseudocode for the phone book. You're just searching again and again. But you're waiting until the very end to get back the final result.

Google now, who I keep mentioning by coincidence today, is full of programmers of course. Here's a fun exercise. Let me go back to a browser. I'm going to go ahead and search for recursion, because I want to learn a little something about recursion.

Here is kind of an internet meme or joke. If I zoom in here, the engineers at Google are kind of funny. See why?

STUDENT: Ah.

DAVID MALAN: Ah, there you go. Yes. Yes, this is recursion. And there's going to be so many memes you'll come across now, where recursion, like if you've ever pointed a camera at the TV that's showing the camera, and you sort of see yourself or the image again and again, that's really recursion.

And in that case, it only stops once you hit the base case of a single pixel. But this is a very funny joke in some circles when it comes to recursion and Google. So how can we actually use Google, or rather, how can we actually use recursion constructively? Well, let me propose that we actually introduced a third and final algorithm for sorting that hopefully does better than the two sorts thus far.

We've done selection sort and bubble sort. Bubble sort, we liked a little better, at least insofar as in the best case where the list is already sorted. Bubble sort's at least smarter, and it will actually terminate early, giving us a better lower bound, in terms of our omega notation.

But it turns out that recursion, and this is not necessarily a feature of recursion, but something we can now leverage. It turns out, using recursion, we can take a fundamentally different approach to sorting a whole bunch of numbers in such a way that we can do far fewer comparisons and, ideally, speed up our final results. So here is the pseudocode for what we're about to see for something called merge sort.

And it really is this terse. Sort the left half of numbers. Sort the right half of numbers. Merge the sorted halves. This is almost sort of nonsensical, because if you're asked for an algorithm to sort, and you respond with, well, sort the left half, sort the right half.

That's being difficult, because well, I'm asking for a sorting algorithm. You're just telling me to sort the left half and the right half. But implicit in that last line, merging is a pretty powerful feature of this sort.

Now, we do need another base case at the top. So let me add this. If we find ourselves with a list, an array, of size 1, well, that array is obviously sorted. If there's only one element in it, there's no work to be done.

So that's going to be our base case. But allowing us now, in just these, what, four, six lines of pseudocode, to actually sort some elements. But let's focus first on just a subset of this. Let's consider for a moment what it means to merge sorted halves.

So Carter has wonderfully come up to volunteer here just to help us reset these numbers. Suppose that in the middle of the story we're about to tell, we have two sorted halves. I've already sorted the left half of these numbers, and indeed, 2, 4, 5, 7 is sorted from smallest to largest. And the right half appears to be already sorted, 0, 1, 3, 6, already sorted.

So in my pseudocode, we're already done sorting the left half and the right half somehow. But we'll see how in a moment. Well, how do I go about merging these two halves? Well, because they're sorted already, and you want to merge them in order, I think we can flip down. We can hide all but the first numbers in each of these sublists.

So here, we have a half that starts with 2. And I don't really care what the other numbers are, because they're clearly larger than 2. I can focus only on 2, and 0 too, 0 also. We know that 0 is the smallest there, so let's just ignore the numbers that Carter kindly flipped down.

So how do I merge these two lists into a new sorted larger list? Well, I compare the two on my left with the 0 on my right, obviously, which comes first, the 0. So let me put this down here. And Carter, if you want to give us the next element.

Now I have two sorted halves. But I've already plucked one off. So now I compare the two against the 1. 1 obviously comes next. So I'm going to take out the 1 and put it in place here.

Now I'm going to compare the two halves again. 2 and 3, which do I merge first? Obviously the 2 comes next. And now, notice, each time I do this, my hands are theoretically making forward progress. I'm not doubling back like I kept doing with selection sort or bubble sort, back and forth, back and forth.

My fingers are constantly advancing forward, and that's going to be a key detail. So I compare 4 and 3, 3 obviously. I compare 4 and 6, 4 obviously. I compare 5 and 6, 5 obviously. And then I compare 7 and 6, 6 of course.

And then lastly, we have just one element left. And even though I'm kind of moving awkwardly as a human, my hands technically were only moving to the right. I was never looping back doing something again and again. And that's, perhaps, the intuition, and just enough room for the 7.

So that, then, is how you would merge two sorted halves. We started with left half sorted, right half sorted. And merging is just like what you would do as a human. And Carter just flipped the numbers down, so our focus was only on the smallest elements in each. Any questions before we forge ahead with what it means, then, to be merged in this way?

So now, here is an original list. We deliberately put it at the top, because there's one detail of merge sort that's key. Merge sort is technically going to use a little more space.

And so whereas, previously, we just kept moving our humans around and swapping people and making sure they stayed ultimately in the original positions. With merge sort, pretends that here's our original array of memory. I'm going to need at least one other array of memory.

And I'm going to cheat, and I'm going to use even more memory. But technically, I could actually go back and forth between 1 array and a secondary array. But it is going to take me more space.

So how do I go about implementing merge sort on this code? Well, let's consider this. Here is a array of size 8. If only one number quit, obviously not applicable. So let's focus on the juicy part there.

Sort the left half of the numbers. All right, how do I sort the left half of the numbers? I'm going to just nudge them over just to be clear, which is the left half. Here is now a sublist of size 4.

How do I sort the left half? Well, do I have an algorithm for sorting? Yeah, what do I do? Here's a list of size 4. How do I sort it? What's step one? Sort the left half.

So I now sort of, conceptually in my mind, take this sublist of size 4. And I sort it by first sorting the left half, focusing now on the 7 and 2. All right, here's a list of size 2. How do I sort a list of size 2?

STUDENT: [INAUDIBLE]

DAVID MALAN: Sorry? I think we just keep following our instructions. Sort the left half. All right, here is a list of size 1. How do I sort a list of size 1?

STUDENT: [INAUDIBLE]

DAVID MALAN: I'm done. It's done. So I leave this alone. What was the next step in the story? I've just sorted the left half of the left half of the left half.

What comes next? I sort the right half of the left half of the left half, and I'm done, because it's just a list of size 1. What comes after this? Merge. So this is where it gets a little trippy, because you have to remember where we're pausing the story to do things recursively again and again.

But if I've just sorted the left half and I've just sorted the right half, now I merge them together. This is a super short list, so we don't need Carter's help here as before. But I think the first number I take here is the 2. And then the second number I take, because it's the only option, is the 7.

But what's nice now is that, notice, the left half of the left half is indeed sorted, because I trivially sorted the left half of it and the right half of it. But then merging is really where the magic happens. All right, again, if you rewind now in your mind, if I've just sorted the left half of the left half, what happens next? Sort the right half of the left half.

So again, you kind of rewind in time. So how do I do this? I've got a list of size 2. I sort the left half, just the 5, done. Sort the right half, 4, done.

Now the interesting part, I merge the left half and the right half of the right half of the left half. So what do I do? 4 comes down here. 5 comes down here.

And now, notice what I have. Left half is sorted. Right half is sorted. If you rewind in time, where is my next step, 3? Merge the two halves.

And so this is what Carter helped me do before. Let's focus only on the smallest elements, just so there's less distraction. I compare the 2 and the 4. 2 comes first, so let's obviously put that here.

Now, I compare the new beginning of this list and the old beginning of this list. 4 obviously comes next. And now, I compare the 7 against the 5. 5 obviously comes next. And now, lastly, I'm left with one number. So now I'm down to the 7.

So even if you've kind of lost track of some of the nuances here, if you just kind of take a step back, we have the original right half here still untouched. But the left half of the original input is now, indeed, sorted, all by way of doing sorting left half, right half, left half, right half, but with those merges in between. All right, so if we've just sorted the left half, we rewind all the way to the beginning.

What do I now do? All right, so sort the right half. So sort the right half. How do I sort a list of size 4? Well, I first sort the left half, the 1 and the 6.

How do I sort a list of size 2? You sort the left half, just the number 1. Obviously, there's no work to be done. Done, sorting the left half. 6, done, sorting the right half.

Now, what do I do? I merge the left half here with the right half here. And that one's pretty straightforward. Now, what do I do? I've just merged.

So now I sort it. I've just sorted the left half of the right half. So now I sort the right half of the right half. So I consider the 0, done. I consider the 3, done. I now merge these two together.

0, of course, comes first. Then comes the 3. And now I'm at the point of the story where I've sorted the left half of the right half and the right half of the right half. So step 3 is merge.

And I'll do it again like we did with Carter. All right, 1 and 0, obviously the 0 comes first. Now, compare the 1 and the 3. Obviously, the 1 comes first. Compare the 6 and the 3, obviously the 3. And then lastly, the 6.

So now, where are we? We've taken the left half of the whole thing and sorted it. We then took the right half of the whole thing and sorted it. So now we're at, lastly, step 3 for the last time.

What do we do? Merge. And so just to be consistent, let me push these down, and let's compare. Left hand or right hand, noticing that they only make forward progress, none of this back and forth comparisons.

2 and 0, of course, the 0. So we'll put that in place. 2 and 1, of course, the 1. So we put that in place.

2 and 3, we merge in, of course, the 2 in this case. 4 and 3, we now merge in the 3 in this case. 4 and 6, we now merge, of course, the 4 in place. And now, we compare 5 and 6. We keep the 5.

Bug. OK, well pretend that the 5 is on. Oh, this is why. All right, so now we compare the 7 and the 6. 6th is gone.

And lastly, 7 is the last one in place. And even though I grant that of all the algorithms, this is probably the hardest one to stay on top of, especially when I'm doing it as a voice over. Realize that what we've just done is only those three steps, recursively.

We started with a list of size 8. We sorted the left half. We sorted the right half. And then we merge the two together.

But if you go down each of those rabbit holes, so to speak, sorting the left half involves sorting the left half of the left half and the right half of the left half, and so forth. But this germ of an idea of really dividing and conquering the problem, not such that you're having the problem and only dealing with one half. Clearly, we're sorting one half and the other half and merging them together, ultimately. It does still lead us to the same solution.

And if we visualize the remnants of this now, if I depict this as follows, where on the screen here, you see where the numbers originally started in the top row from left to right. Essentially, even though this is in a different order, I divided that list of size 8, ultimately, into eight lists of size 1. And that's where the base case kicked in and just said, OK, we're done sorting that.

And after that, logically, I then merged two lists of size 1 into many lists of size 2 and those lists of size 2 into lists of size 4. And then finally, the list of size 4 into one big list sorted of size 8. And so I put forth this picture with the little line indicators here, because how many times did I divide, divide, divide in half? Or really double, double, double. So exponent is the opposite-- spoiler.

How many times did I divide? So three, concretely. But if there's eight elements total, and there's n more generally, it really is a matter of dividing and conquering log n times. You start this, and you can divide one, two, three times, log n times.

Or conversely, you can start here and exponentially double, double, double three times, which is log n. But on every row, every shelf, literally, I made a fuss about pointing my hands only from the left to the right, constantly advancing them, such that every time I did those merges, I touched every element once and only once. There was none of this back and forth, back and forth on stage.

So if I'm doing something log n times, or if I'm doing, rather, n things log n times, what would be our big O formula, perhaps? n things log n times?

STUDENT: Oh, it's n log n.

DAVID MALAN: Yeah, so n log n. The order of n log n is, indeed, how we would describe the running time of merge sort. And so of all of the sorts thus far, we've seen that merge sort here, actually, is n log n, which is strictly better than n squared, which is where both selection sort and bubble sort landed. But it's also slower than linear search, for instance. But you would rather expect that.

If you have to do a lot of work up front sorting some elements versus just searching them, you're going to have to put in more effort. And so the question of whether or not you should just search something blindly with linear search and not bother sorting it, really boils down to, can you afford to spend this amount of time? And if you're the Googles of the world, odds are you don't want to be searching their database linearly every time.

Why? Because you can sort it once and then benefit millions, billions of people, subsequently using something like binary search or, frankly in practice, something even fancier and faster than binary search. But there's always going to be this trade off. You can achieve binary search only if the elements are sorted.

How much does it cost you to sort them? Well, maybe n squared, if you used some of the earlier algorithms. But it turns out, n log in is pretty fast as well.

So at the end of the day, these running times involve trade offs. And indeed, in merge sort 2, I should note that the lower bound on merge sort is also going to be omega of n log n. As such, we can describe it in terms of our theta notation, saying that merge sort is, indeed, in theta of n log n.

So generally speaking, probably better to use something like merge sort or some other algorithm that's n log n. In practice, most programmers are not implementing these sorting algorithms themselves. Odds are, they're using a library off the shelf that themselves have made the decision as to which of these algorithms to do.

But generally speaking, and we're seeing now this for the first time, if you want to improve time, like use less time, write faster code, you've got to pay a price. And that might be your human time, just takes you more time to code up something more sophisticated, more difficult to implement. Or you need to spend something like space.

And as these shelves suggest, that too is one of the key details of merge sort. You can't just have the elements swapping in place. You need at least an auxiliary array, so that when you do the merging, you have a place to put them.

And this is excessive, this amount of memory. I could have just gone back and forth between top shelf and bottom shelf. But it's a little more interesting to go top down. But you do need more space.

Back in the day, decades ago, space was really expensive. And so you know what? It might have been better to not use merge sort, use bubble sort or selection sort even, or some other algorithm altogether. Nowadays, space is relatively cheap. And so these are more acceptable trade offs.

But it totally depends on the application. The very last thing we thought we'd do is show you an actual comparison of some of these sorting algorithms. It's about 60 seconds long. And it will compare for you, selection sort, bubble sort, and merge sort in parallel simultaneously with some fun sorting music, showing you ultimately what it really means to be an O of n squared, or better yet, big O of n log n.

Selection on the top. Bubble on the bottom. Merge in the middle.

[MUSIC PLAYING]

All right, that's it for CS50. We'll see you next time.
