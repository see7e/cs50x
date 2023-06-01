---
title: SECTION3 - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

CARTER ZENKE: OK, well, hello one and all. It is so good to see you here over Zoom today. My name is Carter Zenke. I am CS50's preceptor here on campus. I'd love to see you all over Zoom. I thought we'd do is beginning with a bit of an unusual thing for Zoom, which is on, the count of three, everyone unmute and say hello. We'll hear a chorus of voices, and we'll all be here together in this Zoom room. So again, on the count of three, feel free to unmute and you all say hello. 1, 2, 3, unmute and say, hello. 

AUDIENCE: Hello. 

CARTER ZENKE: Hello. All right, it's so good to hear your wonderful chorus of voices. We're here today for a CS50 section, and the goal of sections will be to review lecture content interactively, to ask questions, to dive into exercises. And so today what we'll do is do exactly that. We'll dive into algorithms. We're doing some things more interactively and talking amongst each other for how we might solve some of these problems in computer science. 

All right, sorry. Hello, everyone, I was unmuted. I was muted. So here what we're going to do is talk about CS50 section. So the goal of section is really to dive into lecture content interactively, to review content, to ask questions, to do so through exercises and through each other. And so today we'll be diving into algorithms and data structures and a little bit more in terms of recursion as well. 

So let's begin, and let's see a few questions for today. So here, our first question is going to be, how can we compare algorithms? In lecture, we saw binary search. We saw linear search. We also saw things like selection sort and bubble sort. So how should we compare algorithms and figure out which one's better than the other for which case. 

We're also going to talk about structs. Why are structs useful? When would we even use them? And we'll then talk about recursion. What is recursion? How do we build our own recursive algorithms, and have an exercise for ourselves and actually write our own recursive algorithm here. 

So let's dive first into this idea of how do we compare algorithms. So we saw in lecture this idea of trying to search for some value. So here I have maybe an array of different colors from this white color here to this dark green color. And let's say I want to find the color white in this array. 

Now, knowing we have some indices here, like 0, 1, 2, 3, 4, 5, and 6, where is this white color in this array? If you have to type in the chat, where is the white color in this array? What index is it at? OK, so I'm seeing 2, right? 

And it seems pretty obvious here. We can just see that this white color is right here in this third spot but index 2. And maybe, how would we know that this is there? We eyeball it as humans. But a computer doesn't necessarily have access to this entire array of information. It can only look at one thing at a time. And so going metaphorically, we might think of the computer as shining a spotlight on some numbers as we go through and try to find this white color. 

So if we're doing linear search here, trying to search this array from start to back, we might start on, let's say, the left side of this array, right? We might go to that very first location, index 0. So we'd shine our spotlight on that color there. Is this white? Have we found our color? 

I'm seeing some head nods. Maybe in the chat, I'm seeing no. This is not the color white, so what are we going to do next? Which number should we go to after 0, if we're doing linear search? I'm seeing some 1's, right? OK, let's go to 1 and see what's there. So let's shine our spotlight there. And that is not white either. 

Maybe we're getting closer. Maybe not. We don't quite know. What's the next one to go to though? Index 2. So let's go to 2 now. So let's go from 1 to 2, adding 1 to our index. And oh, there is the color white. So we found it here. 

Now, how many steps did it take us to do this linear search to find the color white? I'm seeing three steps. OK, so keep that number in mind. It took us three steps to find white using linear search here. All right, so that's one algorithm we could use to find this color white in this array. 

But now let's say this array is sorted. So we're going from maybe light to dark green now. And we want to, again, find the color white. But now that the array is sorted, it enables this new algorithm called binary search we saw in lecture and through a phone book example, right? 

So if we're going to dim the lights again, we have to shine our spotlight somewhere. Now, where should we first shine our light if we're looking for this first element in binary search now? I'm seeing this idea of the middle, OK. We're trying to find the middle of this array. 

And if we know that we have-- let's go back a little bit-- index 6, all the way on this side, maybe our middle index would be 6 divided by 2. So 3, right? That will be the middle index here. So let's go to 3. So we'll dim the lights. We'll then look at 3. Now, is 3 white? I'm seeing no, right? 

So where should we look now? If we know that we're sorting our array from light to dark, we might want to look left, right? But at what index should we look now? We might divide 3 in half again. So 3 divided by 2 is-- well, it's 1.5. Maybe we round down and go to one, right? 

So let's go from 3 down to 1. And we're not quite there. Where do we go again now if we're sorting from light to dark green? I'm seeing some left in the chat. OK, let's go one on the left. 1 divided by 2 is 0.5, but we can't go to index 0.5. Let's round down, and let's go to 0. So we found white here now at this 0th index. 

And now, again, how many steps did this binary search take in this case? Again, took us three steps, right? So if we're trying to compare these two algorithms, we might talk about their running time, which is how many steps they take for us to find the number or color that we're looking for in this case. 

Well, we might compare linear search in binary search like this. How many steps did they take us in this case? And so again, linear search, how many steps does that take us for this particular case here? I'm seeing some 3s. So linear search took us three steps. And binary search, how many steps did that take us again? Also took us three. 

OK, so which algorithm is better than the other? Anyone want to raise their hand, we can call on you and maybe tell us which algorithm you think is better here? Or maybe type in the chat if you'd like. Which algorithm would you choose? 

So I'm seeing some binary. And now my question here is, why would we choose binary, right? Each one, linear search and binary search, took three steps. So is one really better than the other? Maybe on the chat, what do you think? So I'm seeing binary search is more dynamic. It depends on the arrangement. 

So there's this idea that the input we had right now was a very particular input. And for this single input, linear search and binary search did take the same number of steps. But this isn't quite the question we want to be asking when we're talking about running time for algorithms. 

Often, what we want to ask instead is not how many steps we take for a single input but, in general, for any input, what is the most number of steps my algorithm will ever take, right? And another way of asking this question is, for maybe the worst case input, if I were to give my algorithm a completely unsorted list, what number of steps would always run faster then? 

So let's take a look at this. If we call this the upper bound for our algorithm, meaning that this algorithm will never run slower than this number of steps, we might say that linear search takes how many steps? Let's assume we have maybe n elements in our array. In this case, this most recent example, we had seven. How many steps would linear search take in this case? 

So I'm seeing about n steps, right? Let's say we have seven elements, it would take us maybe seven steps in the worst case to find that number if it's all the way at the very end of our array. So linear search might take 7 steps in the worst case. Or in general, if we have n elements, it might take n steps, one step for every element in that array. 

But binary search though might be a little different because we're dividing the problem in 1/2 and 1/2 and 1/2. And so what are we seeing now? So I'm seeing maybe it takes n over two steps, and that's a little close. Any other ideas for how many steps binary search might take in this case? I'm seeing n minus 1. I'm seeing log n. 

And indeed, so binary search would take about log n steps if we had n number of elements to search for here. And people who said n over 2, you're not quite wrong, right, because what we can do is we can take our array of seven elements. We can divide it in 1/2. We've looked at one element. Let's divide it in 1/2 again and divide it in 1/2 again. And this idea of dividing things in 1/2, in 1/2, in 1/2 is a logarithm that we need twice as many elements to do one more step in our algorithm now. 

So binary search in this case, in the very worst case, the upper bound of the binary search algorithm is log of n steps. And now the question becomes, which one would you rather do? Would you rather do linear search, or would you rather do binary search? 

And so I'm seeing binary, right, because we know that, for these really worst case inputs, binary search might, in fact, be better. And this is OK for now, and we can talk about things in terms of the number of steps they take. But in computer science, to be a little more precise, we try to say that something is in the running time, on the order of something. 

And this is because, in computer science, we're often not trying to search an array of seven elements or an array of eight elements. We're often trying to search an array of maybe a billion elements or a million elements. And so who cares if something takes maybe a billion plus 1 steps or a billion minus 1 steps. It's on the order of about a billion steps, right? 

And so we saw in lecture this idea of these algorithms that can take a certain amount of running time. And here, if we look at the bottom of our graph here, we have the size of the problem going up as we go to this side and the time to solve that problem going up as we go up as well. 

So notice how maybe we have two different algorithms, this red line and this yellow line, one taking n steps, one taking n over 2 steps, this other one here taking log 2 of n steps here. 

Now, that's all fine and good. We can be that precise, but often, when working with a billion elements, a million elements, and so on, we might talk about things being on the order of some number here, often n or log n, removing those terms like divided by 2 or plus 2 or minus 2, and so on. 

So here, we might say that this is the upper bound, noting that with the big O notation. And when we do that, we get rid of that division. We say, OK, we don't need that divided by 2 there. And then similarly, we might also do something like this. We might say, if we zoom out, these n over 2 and the n, they look very similar. So let's maybe call those both O of n and the second one here that still looks very different log n over here. 

So we might then characterize linear search and binary search like this as being in big O of n and big O of log n, respectively. So what questions do you all have on this big O notation or these running times? Happy to help answer some of these. 

All right, seeing none so far. Oh, I'm seeing some question in the chat. Does binary look at all the possibilities? So binary search doesn't necessarily look at all of the possibilities. What it does instead is it takes for granted that a list is sorted. And because of that we don't need to look at every possible element. 

If we know that we go to the middle one and we find maybe a number that's too high or a color that's too dark, well, we know we should look to the left of that number. If though we're looking for a number that is greater than that number or darker than that color, we can look to the right and keep dividing in 1/2 and in 1/2 again. 

And so binary search doesn't take n steps, one for every element. It only takes log n of steps, dividing in 1/2 and in 1/2 and in 1/2 again. I'm also seeing what if it's an unordered list? What will be the running time of binary search? And by unordered perhaps we mean unsorted. So let's say maybe our list is not maybe sorted from light to dark or from lowest to highest, and so on. 

Well, in that case, binary search breaks down, doesn't quite work. So the prerequisite for binary search is that our list is indeed sorted. If it's not sorted, what will happen is it will go to that middle element, and we won't really know anything about where the other elements might be. We won't know if we can look left or look right. And so binary search really breaks down in that case. And we're forced to use linear search of looking at every element step by step by step here. 

And a question about what is the use of big O notation? Why would we even care about having this big O notation here? Well, one reason we might care about this is because we care about this question earlier about, for any input, what is the most number of steps my algorithm will ever take? What is the very worst case running time of this algorithm? 

And so this big O notation is saying, OK, this is going to be the number of steps your algorithm will always run faster than, so to speak, will never run more than this number of steps, in general, on the order of this many steps, so to speak. 

All right, so let's keep going. And we have this question of what is the most number of steps this algorithm will ever take? But also, we can ask another question of, what is the least number of tests my algorithm could ever take? So we answered this one already using big O notation. But using omega notation, this different Greek symbol, this other question. What is the least number of tests my algorithm will ever take? Or another way of saying this is, for the best case input, how many steps will my algorithm take? 

And so for example here, we could go to linear search and binary search, and each one maybe takes one step in the very best case. And what kind of case would this be where linear search takes one step and binary search takes one step? What kind of input would we give here? Anyone in the chat? 

Maybe another way of phrasing this is, at what point will we get lucky with linear search or binary search? Yeah, so maybe-- I'm seeing-- so maybe with linear search, maybe our element is that very first one at the zero index, right? In that case, linear search took one step. We can end early. And similarly, for binary search, maybe our element is right in the middle. So we can just go right to the middle and find the element there. 

So this is why, in the best case, our lower bound for linear search and binary search will be one step. These algorithms will, in effect, will never be, let's see, never be slower than-- well, let me think about that. In the very best case, lower bound will be one step and one step here. 

And so what we often use for this notation is this omega of 1. So we're saying this is on the order of about one step or a finite number of steps for linear search and binary search here. 

All right, so what questions do you all have on this omega notation? 

All right, so seeing no questions here, let's keep going. And let's try to find-- let's try to analyze the runtime of a new algorithm that we did see in lecture, of course, one called selection sort, right? 

So in selection sort, we want to basically go through every element and sort this list. And here we have an array that is currently unsorted. But we do want to sort it in the end. And selection sort has an algorithm that works like this. It will say, let's start by looking at that very first element, and let's go through and find the very smallest element in our list and put it at the very beginning now. 

So currently, if we can only look at one element, let's say this 5 here, well, that's currently the smallest number. But let's look at 3. Is 3 smaller than 5? Give me a yes or a no. Yeah, so 3 is smaller than 5. So 3 is our new smallest number. So let's go again. 2 is certainly smaller than 3, and so is 1. And if we were to go through this entire list, we would see that 1 is indeed that smallest number here. 

So what do we do with 1 if we want to sort this list? We found the smallest one currently. Where do we put the 1? Move it to the very first element, or swap it with 5. So we'll say, let's put 1 where 5 is and 5 where 1 is. So now we know that 1 is in the right space. 

Now, our list is not quite sorted. We have 1, 3, 4, 8, 2, 5. That's not quite what we want yet. What we'll do instead is keep going through that list. We'll say, OK, well, let's find the smallest number in this list. 3 seems pretty small. 4 is higher, but 2 is smaller. And 2, right, as people are saying, is going to be our smallest number here. 

So what do we do with the 2 now? 2 will swap with 3. So we'll put the 2 in the 3's place and the 3 in the 2's place. And now we're getting a little closer to having this list sorted. So what we'll do is we'll go ahead and find the next smallest number in the numbers that remain. We'll look at 4, 8, 3, 5, 7, and 6, and we'll find that ultimately 3 is that new smallest number. 

What do we do with 3? Swap it with 4, as people are saying. OK, now let's find the 4. Let's put that, top it with 8. Now, we'll find the next smallest, which will be 5. Then we'll find, in this case, 6. So 6 will go up here. And finally, we'll try to find the smallest again. That's 7. Smallest again, and that's 8. 

All right, so this is selection sort. And we might want to analyze the runtime of selection sort. How many steps does this take? If we were to give an upper bound in omega notation, or not omega, sorry, in big O notation, what would selection sort run in? If we're doing maybe a certain number of steps for every element, what might we do here? 

OK, so I'm seeing something like n squared. And let's get some intuition for this. So let's say, if we go back up to these slides here, notice how, if we go back to this unsorted list, we started by looking at the 5 and trying to find the very smallest element in this list. That took us n steps. We had to go through every element to find the smallest. That's n steps here. 

So n steps to put the 1 in the right place. But now we have to go through another about n steps to put the 2 in the right place. And have to go through another n steps put the 3 in the right place, and another n steps to put the 4 in the right place. And so we're doing n steps how many times? How many times are we doing n steps to find that smallest number? 

We're doing it n times or, in this case, 8, right? So if there are eight elements, we're doing it n times. So here, we're thinking of selection sort really is big O of n squared. For every element we're doing another n steps, n times n, about O of n squared. 

OK, now though, we need to figure out the omega notation, that lower bound. How could we figure that out? Or if we gave it maybe an already sorted list, in the best case, what might selection sort do? 

Yeah, so I'm seeing a few answers. I'm seeing O of 1. I'm seeing O of n, O of n squared. And in this case, if selection isn't optimized, selection sort will take an already sorted list, one that looks a bit like this, and still try to do those swaps, it'll take it a whole n steps to find that smallest number, put it in the right place, go to the next number, do another n steps to put it in the right place. 

And so selection sort isn't quite smart, at least as we've seen it so far. It isn't going to end early. And so selection sort will still be in omega of n squared, meaning that the upper bound and the lower bound for this algorithm are really the same. And that's where we might use this theta notation that I saw some people referencing earlier to say that these upper bounds and these lower bounds are the same in this instance. 

So what questions do you all have on upper bounds and lower bounds and selection sort in this case? So I'm seeing a question about how do we reason about spending time sorting a list in order to be able to use a faster search later on? It's a good question. 

So we saw that with binary search that's faster than linear search, but it takes time to sort something, right? So how do we reason about that? Well, we might do is figure out what are the upper bound and lower bound for our sorting algorithm? And are we willing to spend the amount of time to then get that much faster algorithm for searching later on? 

And if you are maybe often searching, maybe it makes sense to spend that time to sort first and then have that faster search. If though you're only searching occasionally or maybe you're not even really searching a data set at all, maybe it doesn't make sense to sort it in that case. So maybe it comes into play with what do you want to do with your list in that case. 

Yeah, and so I'm seeing what's the main difference between the big O notation and omega notation? So really, the main difference is that they're asking two different questions. The big O notation is asking, in the very worst case, how about how many steps will my algorithm take? 

The omega notation is asking, in the very best case, about how many steps of my algorithm take? And we often say that the big O notation symbolizes the upper bound for the algorithm, meaning that our algorithm will never run slower than this. And similarly, for the lower bound, we're saying that our algorithm will never run faster than this, will never run faster then, at least, the omega notation down here. 

Answer your question too about how do we use this in practice? Would we compare algorithms or things like that? And certainly, you would. So let's say you're working on an application and you want to figure out, is it worthwhile for me to use this algorithm or that algorithm? And often, what you'll do is, before you even write some code, you'll figure out what algorithm you want to use. And so these running times can be a clue to you what kind of algorithm is best for your particular data set. And once you know that, you can then go off and find the time to write that algorithm. But often, it's good to know which one to choose before you spend all that time writing the algorithm you want to write here. 

All right, so these are all really good questions. What we'll do now is spend just a bit of time on this idea of structs. So if we look at this idea of structs, we saw this newly in lecture this week where a struct is simply some combination of data types. And a question we might ask is, when would we even use structs? If we already have strings, we already have INTs, we already have Booleans, why do we need a struct, this new structure we could use in our program? 

And to that I might ask you, let's say, how would we represent maybe these two people in our program? Let's say we want to write a program that represents maybe political candidates, as you might work on in the problem set this week. How could we do this? Or what information would we store about these candidates? 

So I'm seeing names. We might want to store names. I'm seeing your party. Might want to store their party. Other things too I want to reference about these candidates here. Maybe gender, position, maybe their height, right? 

So there are lots of things we could store about these candidates to represent them in our data structure. And often, I would bet you that we can't represent a candidate with just a single data type. I could represent their name, but there's other information I want to couple with that or put together with that that I need to use a struct for. 

So for example, let's say we wanted to make this structure for candidates. We wanted to make this new type, so to speak, called candidate in our program. Well, what we could do is use this kind of syntax. We could say let's make ourselves, essentially, a new type, roughly a type, not necessarily a type like a string or an int, but a new combination data type we could use throughout our program. 

And this typedef is helpful because it's basically helping us define-- that's where the def comes from-- a new type, right? The next piece we see is this struct, that struct keyword at the very top there. And that's saying we're going to have some combination of basic types, like string and int, that will form our candidate here. 

So we'll have the name of that down below, our candidate right here. And then on the inside we'll say, what are the basic types that are inside of this structure? In this case, we'll have a candidate be maybe a string for their name and an integer for their votes. And these two pieces of data will be tied together in this new structure called a candidate. 

And this is helpful because we can actually have maybe a single variable that keeps track of both of these information at the same time. So let's say we want to make a new variable called president. Well, president has this type called candidate that we just defined earlier, right? And we know that a candidate has a name and a number of votes. 

So if we wanted to keep these two pieces of data together, their name and their votes, we could do this. We could say, maybe the president's name is Alyssa. And the president has maybe 10 votes. And so here we're using this new dot syntax, president.name gets the value Alyssa. And president.votes gets the value 10. 

And so in this single variable called president that is of type candidate, we are storing now a name and a number of votes close to each other in memory here. What questions do you all have on this syntax or what structs are so far? 

So your question about the maximum arguments for a struct, and maybe to go back here and show just some vocabulary. Here we often call this the attributes of a struct or the fields of the struct. And so here, there's really no limit to the number of fields we could define. 

But often want to keep things reasonable and compact for ourselves design-wise. It's a good question of design to figure out how many elements do we need or how many fields do we need in our struct. And so in this case, we might have 2, 3. And you can get up to maybe, I don't know, maybe tens of fields or so. But often, if you're doing that, your struct might be a little too complex. 

I'm seeing some other questions here. Is the C code we need to use in our code just key value pairs, like a dict in Python? This is maybe similar to a dictionary, if you're familiar with that, in Python in the sense that, when we say the president's name is Alyssa and the president's votes is 10, we can later on just get that same value by referencing president.name and president.vote, so similar in spirit to a dictionary where we're trying to have a key, like name, correspond to a value, like Alyssa. 

Question about the dots. Why do we have these dots, president dot name, president dot votes? Simply speaking, long ago, it was decided that we would have this dot syntax to reference the fields or the attributes of a struct, so president dot name, president dot votes. And as you get used to it, you'll probably see it's pretty handy just to type that little dot there to get access to that individual attribute of that struct there. 

A question, can we use struct without typedef? Indeed, you could. So if you go back to this syntax here, we saw that typedef was the very first syntax piece we typed here. But if you didn't want to maybe reuse this struct, you want to just use a struct once, no need to use typedef. 

Typedef lets you specify a candidate, in this case, define a name for this new structure that you're building, and then reuse that name. So let's say I wanted to do this at the top of my program. I could do that. Later on, I would then be able to reuse the name candidate to refer to this structure. But maybe I don't want to reuse it. Maybe I only want to use it once. In that case, you could just have the struct there and not the typedef and you could use it just once in your program there. 

All right, I'm seeing a question, are structs similar to objects? There are some distinctions between structs and objects. You're familiar with this idea of an object and maybe you've done Python programming or Java programming and you've seen this idea of an object. Structs are a bit like objects, but you cannot tie a function to a struct. So objects in Python and Java might have methods or functions tied to them. Structs, though, do not have that distinction. They don't have functions tied to them. 

All right, so let's keep going on with these structs here and figure out what else we can do with them. Let's actually do a little exercise here, work on this together, where we'll create our own get candidate function. So you maybe are familiar with this function get string or get float in the CSFD library where you can use those functions to get a string, get a float, get an integer, whatever you want to get from the user. 

And similarly, we'll actually write our own function called get candidate that will return to us a new candidate that the user has created for us by being prompted for some information about that candidate. So let's go on over to our code spaces. And if you're like me, you'll need to wait a little bit for yours to load. 

And once you get there, let's go ahead and open up this file called candidate.c. So once you get there, feel free to type maybe code candidate.c, or make a new file and title that one candidate.c. And once you do that, what are you going to include at the very top of your file? Can anyone tell me in the chat what you often want to include at the very top of your program 

So I'm seeing some-- yeah, some libraries, right, like standard io, cs50.h. Certainly, you want to use these libraries inside of our own program here. So all right, now I have my terminal up and running. So if you're following along with me, what you can do is simply type maybe code-- oops, let me go clear that. you do get rid of the activity bar there. 

What we'll do is do code candidate.c, and now we'll get to make a new file, again, called candidate.c up here. And that dot c is important. That means there's a c file here. So what we'll do, as people have suggested, we'll include some libraries up here. We'll say, include maybe the cs50 library to get access to functions, like get int and get string, and so on. Maybe we'll also include standard io.h to be able to print things to the screen, use printdef. 

All right, now often what we'll do is we'll declare our struct at the very top of our file below our includes or our libraries here. So what syntax would we need here? We might want to create a new type, right? So we'll type typedef, and we want to make a struct. So we'll say this is a new struct. And what are we going to put inside of this struct? What attribute did we have earlier? If you want to type in the chat. We're trying to make a candidate here. 

All right, so name and votes. So maybe name is a string. So let's say this attribute is called name. It's of type string. And then we'll also say, let's give a new attribute called votes, and that will be of type int. And now finally, we'll need to close this out with a name for our struct. So we'll call it candidate down here. 

All right, so now we can re-use this idea of a candidate throughout our program because we've used typedef. We can say, I want to create a new candidate using this new amalgamation of types that we're going to call candidate throughout our program here. 

All right, and now what is the main part of our program now? We have our libraries. We have our struct. What kind of function do we need now? Maybe in the chat, feel free to type. Yeah, we need our int main void. So we need the main function for our program. 

So we'll do int main void and have some space there for us to write our program. But here, if we go back to our slides, our goal is to make our own function called get candidate. So what we want to do is probably define that down below. And what you'll notice about defining new functions or declaring new functions is that their signature here, or we call this line here, has a few key elements to it. 

So it has the type that this function gives back to us, that it returns to us. It has the function's name, and it has the function's inputs. So if we're trying to write a function called get candidate, what name would we type in? Maybe an obvious answer here, if we type in the chat. What name would we type in for get candidate? 

We probably should type get candidate, right? Get candidate is the name of our function. And now, what type does it return to us? I'm seeing a few-- I'm seeing string, and I'm seeing candidate. So notice now, we're not going to return a string. We're actually going to return an entire candidate because we've defined a candidate as this combination of a string that is called name and an integer that is called votes. 

So here, we're going to give back to our program a whole candidate, not just a string, not just an int, but a whole candidate, those two types put together. And because we use typedef, we can say this down below. We can say get candidate. And now, we can go ahead and define this function called get candidate, but we need one more step now. 

We need to give some inputs or some arguments here. And if we're using our modeling off of get string, for example, we might want to take a prompt. We could say, maybe it takes a prompt that is a string here. All right, so what questions are there on this so far? All right, seeing none so far. 

Now, let's go ahead and try to fill in the rest of our get candidate function. So ideally, we want to be able to use it like this. We could say, within my main function, I want to create a new candidate. Maybe I'll call this one president. But to actually fill in that variable, to give it a value, I'll call get candidate, similar to what I did for get string, for example. 

Here, I could say maybe Enter a candidate is the prompt. And now I'm seeing a question. Is candidate a type because we've declared it above the main function? Indeed. So we've used typedef here, which is that key word that says, all of what follows should be considered reusable in our program. 

So here we're saying that this struct that we're going to call candidate is a bit similar to a type that we can use throughout our program. We can say that a function does indeed return an entire candidate and not just those basic data types, like a string or an int. 

All right, and so we're going to be able to use get candidate like this. We'll create a variable called president that is a candidate and then have get candidate returned to us that new candidate that we've created with get candidate down below. 

OK, so we now have this function get candidate, but we need first to be able to print out the prompt to the user so they know what to type in. So here I might say, OK, let me print out the prompt with a new line here. So I'll say, whatever the user gives to me as the prompt, let's say this string here, I'll then print it back out to the user when I run Get candidate, and I'll make a new line. 

Now though, I need to do the work of creating this new candidate and filling in its attributes and ultimately returning that candidate to my main function. So what we could do is we could say, I want to create a new candidate. And it's like a throwaway candidate. I'm just going to create it here, add some attributes and return it back to our main function. 

So I'll just call it candidate c. Maybe we can come up with a better name, but we'll just call it candidate c for now. This is a new candidate variable I've created in my get candidate function. And now what I could do is this. I could say c.name should be what? What kind of function could I use to fill in the value for name? Remember, it's a string. 

Ah, I could use get string, right? I could say get string and, let's say, Enter a name, right? So now the candidate's name will be filled in by the user when they enter in some text after get string. And now here we'll see c.votes. And how could I fill in the votes? What kind of function would I use here, maybe in the chat? Get int, right? So I could do get int and then enter a number of votes. Awesome. 

And now finally, I've created this new candidate called c. I've added in the name, the number of votes. What's left to do? I need to give it back to my main function. So what would let me do that? Return, so I'll return c. 

And now what will happen here, if we go back up to the very top, line 13, this new variable called president that is a candidate will first call get candidate. We'll go ahead and prompt the user. Then we'll create this new candidate, fill in the name of the votes, return that candidate, and ultimately, store it in this variable called President. 

So what I should be able to do is maybe type in, for example, print maybe the name. So I'll say president.name. And then what I'll do is I'll print, let's say, the votes. I'll say president.votes. And when I run this, I should be able to see that result there. 

So let's go ahead and go down to our terminal. I'll type make candidate. Oh, and I got an error. What did we forget to do? If you take a look at this error here. Seeing a few answers. What did we forget to do here? Implicit declaration of function get candidate is invalid in C99. 

Yeah, so I'm seeing I'm missing the prototype for this function. So notice how we got ahead of ourselves here. We went and defined our function down below, but we actually use it before it is defined. So what we should do is really go to line 10, after our definition of this candidate here. And we should say something like this. 

We should say, let's copy and paste the prototype for this function, the prototype being what it returns, its name, and any arguments it has, and put a semicolon to say that, look, this function will come up. I promise to you, I will define it later as this a compiler reads our code from top to bottom in this case. 

All right, so let's go back in. Let's go ahead and clear our terminal window. Type make candidate. Oop, and we still have an error. Let's see this one. Hmm. President.votes, this error is a little cryptic. But if the format code for a string, you'll know that this is maybe the wrong format code. I'm seeing we need %i right there. 

Good, so I'll click my terminal again. I'll type make candidate. And now, it seems to work. So what I can do is I can do dot/candidate. I now see the prompt Enter a candidate that I typed up above here. I can say maybe the candidate's name is Carter, and maybe the number of votes is 10. And I'll hit Enter, and now I see those same elements here in my program or my terminal. 

OK, so what questions are there on this program so far? All right, so seeing none right now. But what we might want to do at the very end is, maybe we don't just want one candidate. We want, actually, an array of candidates or a list of candidates. And you'll see this in the problem set for this week of CS50. 

What we can do is we can actually use this same type we've defined to create an array of that type. So we could say, I want an array of candidates that I'll call the candidates array. And I want to have three of them in there. So notice how, if I zoom in again, you'll see we're going to define an array called candidates array that is full of these candidate types that we've declared up above. And it has space for three of them, right? 

So what we could do in this case is actually go ahead and fill in the array. We could say, let's start at index 0. Let's go on up to but not including that third index. So we'll go 0, 1, and 2, and increase i by 1 as we go. 

And as we do that, we'll say, OK, maybe the candidates array at location i, first 0, then 1, then 2 is going to use Get candidate. So I'll say get candidate, and let's say, Enter a candidate. 

And now what I can do is, if I were to run this program, I would get prompted again and again and again to enter a candidate until my array is full. 

Now, if we were to do that and also to access some of these candidates inside that array, we need some combination of the syntax we've seen before. So what we might do is, in the problems that you'll see maybe an array of candidates like this, like name and number of vote. And to access the candidate as a whole, like Alice as well as Alice's votes, you would just type candidates bracket 0 to get that very first element in this array here. 

But if I wanted to get maybe just the candidate's name, I could do as follows. I could say candidates brackets 0 dot name, or, similarly, candidates brackets 0 dot votes. And that would allow me to get, not just the whole candidate at that array location, but the actual attribute I'm interested in here as well. All right, other questions on this. 

All right, so seeing none so far, that will conclude our little brief foray into structs her. And certainly, we can take a minute to go back if there are questions towards the end. But for now, with our last bit of time, what we want to do is figure out how we can use recursion. 

So recursion is not necessarily an algorithm. It's more so an approach to problem solving in computer science. There is no single recursive algorithm, but there are algorithms that use recursion. So recursion is simply a way of solving problems. 

And recursion, more specifically, is about taking a large problem, one that seems a little daunting, and breaking it up into smaller pieces that we know we can solve. And so one example of this is often used when teaching recursion is this idea of a factorial. 

So if we look at a factorial, if you're not familiar, we can say 1 factorial is 1, right? We can say 2 factorial is 2 times 1. And we can say 3 factorial is, well, 3 times 2 times 1. And if you're not getting the pattern, 4 factorial might be? Well, just 4 times 3 times 2 times 1. So a factorial is multiplying a number by 1 less than that number and moving down until we get to 1, right, so 4 times 3 times 2 times 1 for 4 factorial, 3 factorial, 3 times 2 times 1, and so on. 

Now, what do you notice about this problem, particularly in 4 factorial? What do you notice, or what do you see if we're trying to use recursion on this problem, trying to find a smaller problem within 4 factorial? Maybe type in the chat if you'd like. What kind of pattern do you see when you look at 2 factorial, 3 factorial? 

So seeing a few ideas, right? I'm seeing it's repeating the same steps. It's a little repetitive. And I'm seeing, more particularly, if we look at 4 factorial, we actually see that 3 factorial is included in 4 factorial, right? 3 factorial is 3 times 2 times 1. Well, that's actually right there in 4 factorial, 3 times 2 times 1. 

So if we were to look at the problem this way, we might make it a little more obvious, right? 4 factorial really has the solution 3 factorial inside of it. And similarly, 3 factorial has 2 factorial inside of it. And then finally, 1 factorial, that's just kind of on its own. It's just 1, right? We know that for a fact. 

This is really a good place for recursion to come in because recursion is all about taking this larger problem, like 4 factorial, and breaking it down into smaller pieces. So let's look at it from a recursive standpoint. 

Let's go ahead and say we want to find 4 factorial. Well, what is 4 factorial? Well, it's 4 times what? What's the smaller problem within 4 factorial? 4 times 3 factorial, I'm seeing in the chat. So 4 factorial is just 4 times 3 factorial. But what then is 3 factorial? 

So this is where what comes in as we call it a recursive call. This is saying we are going to solve this smaller problem before we can solve this larger problem, right? We can't solve 4 factorial until we know what 3 factorial is. 

So let's go ahead and solve 3 factorial. Well, what is 3 factorial? That is just 3 times what? 3 times 2 factorial, right? So that's fine, but what is 2 factorial? Well, 2 factorial is? 2 times 1 factorial. And what is 1 factorial? At some point, we do have to stop here. Otherwise, we'll keep finding smaller and smaller problems and never end. 

Well, 1 factorial, in this case, is just 1. We know that for a fact. And so this down at the bottom is what's called our base case. This is the problem that we know how to solve just for a fact. 1 factorial is 1, no computation necessary, no need to break it down into a smaller problem. 

And now, once we've gone down to that base case, well, the rest follows, right? We know that 1 factorial is 1. So let's go ahead and make sure that we can solve 2 factorial. And we're going, what we call, back up the call stack, where we made a recursive call earlier to go ahead and solve a smaller problem. Now we've found our base case, so we'll go back up this stack of calls we made to find the answer here. 

What we'll do is say, OK, 2 factorial, that's actually just 2 times 1. We know that now because 1 factorial is 1. Well, 3 factorial, that's actually just 3 times 2 times 1 because we know now that 2 factorial is 2 times 1. And similarly, for 4 factorial, we know that, in this case, 3 factorial is just 3 times 2 times 1. So now we can say 4 factorial is just this expression, 4 times 3 times 2 times 1. And that, as a whole, is 24. 

All right, and so I'm seeing in the chat, it's like backwards logic. It is a little backwards logic. We have to go down to the bottom first and then work our way back up. So let's work on this one together. Let's actually see what might be able to work on with here. And what we'll do is write our own function called factorial, where factorial should take an integer and return the factorial of whatever number we pass in as a parameter. So if we pass in 4, we should find 4 factorial, or 5, we should find 5 factorial here. 

All right, so let's go ahead and actually open up our own program. We'll go ahead and go back to our terminal. We'll type code factorial.c to open up this new file called factorial. And let's get the same template code in there. We need to make sure we have cs50 library. We need to have standard io.h. And we also need to have, of course, our int main void function, that main function in our program. 

And now we can also make sure we have our factorial function. So I'll zoom in just a little bit more. We might want to have a factorial. What type is factorial returning to us, do we know in this case? If you want to type a chime in the chat. An integer, right? 

So we'll say int, and then the name of this function, factorial. And then does it take any inputs? What kind of input does it take? Yeah, it takes a number that is also an integer. So I could say int, maybe, number in this case. 

So here we have this function, again, called factorial that takes a argument called number that is an integer. And it returns to us an integer, that number factorialized, right? And now we know from our past mistake we need to actually go ahead and include this prototype up at the very top of our file in order to use this function in our code. 

OK, and let's just go ahead and fill our main function here. Let's make sure we maybe prompt the user for a number. So we could say, let's give ourselves maybe int n is get int, and we'll say type a number to our user. And then what we'll do is maybe print the resulting integer that comes from running factorial in this case, so factorial of n. 

Now, it's up to us to actually implement factorial down here. And when we think about implementing recursive functions, we often want to start first with our base case. What is the thing we know to be a fact? And if we look at our factorial call stack here, what was our thing we know to be a factor down here? Feel free to type in the chat. 

Seeing 1. So yeah, 1 factorial is 1. We know that. That is always true. So what we should do is go back to our factorial function and then say, OK, well, if number is 1, if it's equal to 1, let's go ahead and just say the answer. Let's say the answer is 1. 

So now, if I were to type in 1 and pass it to factorial, I would get the right answer. 1 factorial is 1. But there's more to do here. If I were to type in factorial of 3 or factorial of 4, that wouldn't quite work because I haven't figured out how to solve that piece yet. 

Now, if we go back to our diagram here, what did we notice about how each factorial problem is composed of some other problem? What should be our recursive step here? 

Yes, I'm seeing something like n minus 1. And if you notice, you'll look at maybe 4 factorial, and see, well, 4 factorial is really just 4 times 3 factorial. And 3 factorial is just 3 times 2 factorial. So it's really whatever number we're at times the factorial of a number minus 1. 

Now, there is a way to use a loop here, and that would be called what an iterative approach using a loop to solve this problem. But here we'll actually use a recursive solution, which is one that calls itself in the definition. So factorial will call the factorial function to try to solve this problem here. 

So if we know that we don't have the answer already, if we know that we aren't at 1 factorial, what we can do instead is try to solve this problem by breaking it down into smaller pieces. We could say, well, we know that a certain number factorial is really just that number times that number minus 1 factorialized like this. 

If I go full screen here, we'll see that really the solution is just number times the factorial of that number minus 1. And let's go ahead and try to get a visual here, but just first confirm it works. So I'll say make factorial and run./factorial. And maybe I'll type in 4, and I get 24. So let's type n factorial of 3, and I get 6 because 3 times 2 times 1 is 6. 

But why is this working? It seems a little odd that we can just solve this problem with only a single if statement and this expression down here that uses itself in the definition, right? So to visualize this, we actually want to use something called a debug50, if you're familiar with that. Debug50 lets you step through your code and go through and see how things are working here. 

So while we're at it, let's set a breakpoint right at this point in our code, meaning we'll stop at this point, and then we'll step through piece by piece to see what's happening in the computer's memory. So we'll go ahead and run this using debug50. And we'll wait for debug50 to pull itself up. And we'll step through our code in a minute here. 

All right, let me zoom out just a little bit. OK, so I'm seeing type a number in my prompt. So I'll go ahead and type in the number for, right? All right, so notice debug50 on the side here. We now have number 4, and what we've done is we've given our program a number. 

Now, we're at this stage. We've called factorial with n is 4, which means that number here is equal to 4. And if we look down at our call stack, that vocabulary term we learned earlier, we see that we first called main, and then we called factorial, right? 

But we still need to call probably factorial again because, if we go in here, we see that number is not 1. Number is 4 right now. It's not 1, so we can't return 1. We will instead need to do this line of code. But we can't solve this line of code until we run the factorial function again with number 1 less than that. 

So what we'll do is we'll step into this function factorial. And now, see in our call stack, factorial shows up again. We call factorial once, we're calling it again. But now, what's going to happen? Number is 3, so we're getting closer. We're not quite there. 3 is not 1, so we're going to continue down again. We'll go ahead, and we can't return 1 there, but we can figure out what is 3 factorial? 

Well, to find 3 factorial, we've got to find 2 factorial. So we'll dive in again. We'll say, OK, let's go deeper in our call stack. Notice how if we scroll down, factorial is being called yet again. we've called it the third time now. Now, number is 2. OK, let's keep going. Number is not 1 yet. To find 2 factorial, we got to find 1 factorial. Let's go dive in again. Look at our call stack. We've called factorial four times now. 

But at this point, we know number is 1, and so we can simply and safely return 1. We know the answer now, right? So we'll do that, and then, that's correct, we called this number 1 our base case. We've hit our base case now. We can start going back up our call stack. So we can say let's finish that call of factorial. Now, we're back at our third factorial call where number is 2. 

Well, we solved that problem. We know that 2 factorial is just 2 times 1. And now we can return that 2 times 1. Now, we're at that later version of factorial, that second call where number is 3. We know 3 factorial now is 3 times 2 times 1 based on the earlier calls of factorial. We're going to go again. 

Now, we're at that very first call a factorial, number is 4. Well, the answer here we now know is 4 times 3 times 2 times 1 based on this call stack we've done. And now we can finish that program and type out 24. 

So a bit of a leap of faith wherein you're trying to take for granted that your program knows exactly what to do. And it will eventually hit this base case. If it doesn't hit that base case, we'll know that maybe our program will keep running, keep running, keep running. And that's not a good thing. So we always need this base case here to stop the call stack from growing and growing and growing and growing and always finding that end case there. 

But certainly, feel free to take some time thinking about this one. So what questions do you all have about how this works or how the recursion is working here? Yes, so your question about, you know how recursion works, but how do you know if a recursion is a good approach to a problem? 

And what I encourage you to do is really try to draw things out before you end up trying to code a recursive function. So similarly, if we go back here, we saw that factorial was we drew things out. We saw, hey, I notice that 3 factorial is embedded inside of 4 factorial. So maybe it's a good use of a recursive algorithm here. 

If you can find a problem and you find that problem is made of a smaller problem that can be solved in the same way, that's a hint you might want to use recursion in that instance. 

What other questions are there on recursion in this case? Let's see. I'm seeing, what do we call the thing we did on line 4? So if you scroll up to the top here in our program, we'll see on line 4 we declared the function. We gave the compiler our prototype. 

So this right here is called our function prototype and, more specifically, putting this piece right here is declaring our function. We're telling c, hey, we have this function that returns an integer. It is named factorial and takes an argument called number that is an integer. And that in respect we're declaring our function there. 

Is there a way to make this code shorter? Perhaps. I won't go out on a limb and say that this is maybe the most short you can make it. Maybe there is a way to do it. But certainly, if it seems well designed for us here. 

And another question is, can we use a loop here? We actually could use a loop here. So let's say we didn't want to use recursion. Maybe it feels a little too much like a leap of faith. So what we'll do is we'll, maybe instead of this, we'll say, OK, we know that, when number is 1, we'll go ahead and return 1. But otherwise, we know that factorial is really just that number times 1 less than it times 1 less than it. 

So we could do this. We could say something like a for loop. We could take for. Maybe we'll start at i is equal to our number and go until i is-- maybe, let's say, as long as i is greater than 0, and then keep subtracting from i as we go through. 

So what we could do is maybe say that our solution is going to be first probably equal to number. And then we could say solution is equal to that solution times some other-- times i, I believe. And feel free to correct me if I'm doing anything wrong here. 

I think what might happen though, is we have solution times number. Something like this, number minus 1, and so on and so forth. But basically what we're doing here is trying to make a loop out of this, trying to say, OK, let's start with 4 and multiply 3 to it and then 2 to it and then 1 to it through a loop. And we could do that. 

But often what happens is that maybe recursion is more elegant solution here. This seems like much more lines of code. So maybe, in this case, we could use our recursive solution that we had before. 

And a question related to this is, can all recursions be rewritten as loops? It's a good question. I would say that at least some of them could be, as we demonstrated here. I think there are some problems though where recursion is really going to be helpful for you because what recursion does is it allows you to have a whole new smaller problem to work with and take a big chunk out of that problem and work with that smaller one. 

So often, in computer science, we want to solve bigger problems by first solving smaller ones. And a loop might not always give you that same leverage that you might have by breaking down a big problem and making it into a smaller one. But a great question. Other questions to you on this recursion here? 

All right, so that does just about bring us to the very end of our section. We talked about algorithms, how we compare them. We talked about structs and how we might use them. We talked about recursion, how we can identify recursion and ultimately write our own recursive functions. 

As you go off into this week, you will, in fact, do your own kind of algorithms that involve structs, that might involve recursion, that might involve all these different elements. And so I wish you the very best as you're going off and working on your own work this week. 

Thank you so much for joining us over Zoom. It was wonderful to see you all here. Hope to see you in the coming weeks, and I'll be happy to stay around and answer questions. Thank you all. 