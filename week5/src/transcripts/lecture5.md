---
title: LECTURE5 - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DAVID J. MALAN: All right. This is CS50. And this is week five, which is going to be our last week in C. But what that means is that we'll have OK-- 

[CHEERING AND APPLAUSE] 

But with this week, with last week, and really all of the weeks prior, have you been hopefully acquiring, if slowly and with some challenge, some fundamental building blocks that are still going to underlie everything we continue doing in the semester, even as we transition to so-called higher level languages. 

Next week, indeed, we'll introduce Python, a very popular language that does not have pointers, does not have memory management at this very low level. But that's really just because someone else wrote the code that will do that for you. 

And it's going to make our lives easier. Because it means when you want to solve a problem conceptually up here to just get real work done or build something amazing, you don't have to really get into the same weeds as we have been deliberately this week and now last. But the goal ultimately is that you better understand and can better harness then all that a computer can do even in those higher level languages. 

So today, we're going to focus particularly on data structures, how you might structure your data in memory, which really amounts to building things digitally, stitching together ideas and concepts in memory using this new building block from last week, which of course are these pointers. 

Pointers allow you to store addresses in memory, like in variables. But with those simple addresses we can leave these breadcrumbs. We can point from here to there. And we can conceptually stitch pieces of data together. But there's going to be different ways of doing that. 

And today we'll focus first on what's generally known as an abstract data type. And similar to a type in C more generally, it does actually have some properties in it. But the underlying implementation details of an abstract data type are ultimately up to you. That is to say, an abstract data type can represent one thing and can do something. But how you implement it allows you some discretion underneath the hood. 

So for instance, in the world of computer science, a queue is actually a technical term. This is a type of data structure that we could theoretically build in code in C or really any other language. But a queue has properties just like queues in the real world. For instance, if you've ever lined up for something to get food in a restaurant, or go into a store, or wait for the airport to clear you, well, you've lined up in a queue. A queue being some sort of line. 

But what's noteworthy about queues are specific properties. They are first in, first out data structures, either virtually or in the human world. Which is to say the first person in the line should ideally be served first at the restaurant. Or the first person in the line should get through airport security first. 

By contrast, if it weren't first in first out, you can imagine how frustrated you would be if you have this inherent unfairness. In fact, if you've ever been in line at a store, a supermarket, or the like, and all of a sudden they maybe open a new line. And now the person behind you gets to cut ahead and go forward. That's because they've broken the concept of the queue. So it has this inherent potential for unfairness unless you maintain this first in first out property. 

This would be true too for a to-do list, just for productivity's sake. If you're in the habit on paper or virtually making a to-do list, ideally you probably want to go through that list top to bottom so that you actually get the first stuff you thought of done first rather than always focusing on your most recent thought. 

Now, within the world of queues, there's generally two operations, two functions, if you will, that any queue would have either in the real world or in the virtual. Enqueue is usually the technical term to mean adding something to a queue. But specifically, it means adding it to the end of the queue so that someone isn't cutting in line, for instance, to go up front. 

And then dequeue is just the opposite. When it's time for the first person in line to be served, the time for the first person in line to go through security, they are dequeued, so to speak. So a technical concept, ultimately, as it's implemented in code. But it's really just a real-world concept. 

And these are in contrast to another abstract data type that we might call a stack. And a stack, much like a stack of trays in the cafeteria has fundamentally different properties. You can still add and remove things from them, but consider what happens. Whenever they clean all of the trays in the cafeteria or the dining hall, they put one of the trays down here and then the next one on top of it. And then the next one on top of it, it, it, and so forth. 

But of course, which tray do you presumably take as a user of that physical stack? The top one, presumably. You're not going to futz down here and try to pull one out. And so, that would seem to have an opposite property. LIFO, last in first out is what characterizes something like a stack. And that just makes sense, certainly, in the physical world of stacking all of those cafeteria trays because it just makes more sense to grab the most recently added one, the last added one first. 

And at least in that context, the trays don't necessarily care what order they're used in. But even then, you could imagine that maybe there's some old dirty nasty tray at the very bottom that never gets used because you're constantly replenishing the stack. So there might very well be side effects of these kinds of features. 

You might be familiar with using Gmail for instance, or really any email program. What you're looking at in your inbox is technically a stack, at least if you've left the defaults configured. Why? You get a new email? Where does it end up? Not five pages of emails later, presumably right at the top. And the next one's right at the top, right at the top, right at the top. 

And so, if you're like me, you're guilty of eventually losing track of some emails. Why? Because you've pushed so many more emails onto the stack that you lose track of the things you got earliest. Last in first out though, is maintained. The most recent email you get might very well be the first one you reply to. But that's not necessarily good for responsiveness to everyone else out there. 

Similarly, if you store all of your sweaters in a stack like this, like a pile of black ones, below which is a red and then a blue. Stack might be perfectly fine for keeping things organized. It's the sane way to do it if you just have a shelf in your dorm room or home. But what's going to be a side effect of using a stack to store your sweaters if there are these in this way as opposed to a queue? Yeah. 

AUDIENCE: It's harder to get the red and blue ones? 

DAVID J. MALAN: It's harder to get the red and blue ones. So presumably you're going to much more often wear, for instance, if you will, black instead there. Now, the operations for adding things to a stack are similar in spirit, but just different vocabulary. You push something on top of a stack. Even though it's more like in the tray world you place it or rest it. 

But pushing means adding something to the top of the stack. And popping means removing something also from the top of the stack. So it's not a matter of enqueuing at the end and dequeuing at the beginning. With a stack, everything's happening on top. You're pushing onto the top and then popping off of the top. 

Now, when it comes to actual code, how might we implement something like this? Well, let's just focus on really how you might implement the data structure itself. And we won't implement any functions. You might implement the notion of a stack like this. We've seen typedef before. It just means define a new type of my own. 

Struct means here comes a structure, a.k.a. a data structure of one or more variables within. And let's suppose, like last time, we've had-- we defined already a person data type using a separate typedef. And every person has a name and a number or whatever. Let me just stipulate that person exists already. 

So here, you might have to implement a stack, an array called people of some capacity. Maybe it's an array of size 10, or 100, or whatever. This is a constant here in this context, capacity. And every element in that array is a person structure. And I now have this too, size. 

Now, this almost seems like a synonym for capacity. But maybe intuitively, anyone want to propose why I'm apparently maintaining separately the capacity of the stack but also the size of the stack? Why these two distinctions here? Yeah. 

AUDIENCE: Capacity is how high the stack could be. 

DAVID J. MALAN: Yeah. 

AUDIENCE: Size is how high it actually is right now. 

DAVID J. MALAN: Perfect. The capacity is how high the stack could be, like how much room is there for those sweatshirts in my closet, for instance. Whereas size is just literally at this moment in time, how many sweatshirts are in the stack. It's either capacity or fewer presumably in total there. 

So what is capacity? Well, we could implement this in perhaps a familiar way. I might just define a const somewhere else in my code of type int that just defines it to be capacity 50. 

But what perhaps is going to be the downside of implementing a stack in this way? Of using an array inside here? What's a downside now of implementing a stack using an array and this size variable within. What's a caveat here perhaps? Any hands? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: So it's going to be harder to reach elements that aren't the last one. That is the most recently added one. So there could be some sweatshirts, so to speak, way down below. So we've seen that before too. But at some point too a limitation of this design is what it's going to be finite. 

I can maximally fit in this example 50 sweatshirts, or 50 emails, or 50 cafeteria trays, which is fine. But at least it's indeed finite. And at least in the computer's memory, it might be nice to use more, and more, and more, maybe as more things are getting added to the computer. So maybe I make this 500. Or heck, why don't I make it 5,000 or 50,000? 

Well, what's the trade-off there? If I want to have enough room to grow, seems like I should just crank up the value of capacity endlessly. But why might I not want to change the 50 to 500, or 5,000, or 50,000? What's the trade-off there perhaps just intuitively? Yeah. 

AUDIENCE: Because I don't want to touch memory that I'm not supposed to. 

DAVID J. MALAN: You don't want to touch memory that you're not supposed to be touching. And in this case, it wouldn't be-- that wouldn't be a risk per se unless you indeed overflow the stack. But there's a related issue in asking for that much memory. What would another downside be? 

AUDIENCE: You only have one element and you have [INAUDIBLE] 5,000 [INAUDIBLE]. 

DAVID J. MALAN: Yeah. [LAUGHS] Exactly. So if you've got a capacity of 5,000 but you're only using one of those elements, it's awkward to say it non-technically. Which is just to say very, very wasteful. That's just bad design. It's correct, it will work for up to 5,000 elements. But my gosh, you're wasting 4,999 extra spots. 

And that's not going to end well, especially if you're using more data structures in memory. Your Mac, your PC, your phone is surely going to run out of memory if you ask for that much. So it'd be nice if there was a bit more dynamism there, whether it's a stack or a queue, both of which might be implemented a little similarly in spirit. 

But let's conclude this abstraction by comparing-- thanks to a friend of ours, Professor Shannon Duvall of Elon University, who kindly put together this graphical animation that's just under two minutes long that paints a picture of these two types of abstract data structures. And then we'll dive in underneath to how we might implement problems like these. If we could dim the lights dramatically. 

[VIDEO PLAYBACK] 

[MUSIC PLAYING] 

- Once upon a time, there was a guy named Jack. When it came to making friends, Jack did not have the knack. So Jack went to talk to the most popular guy he knew. He went up to Lou and asked, what do I do? Lou saw that his friend was really distressed. Well, Lou began, just look how you're dressed. Don't you have any clothes with a different look? Yes, said Jack. I sure do. Come to my house and I'll show them to you. 

So they went off to Jack's. And Jack showed Lou the box where he kept all his shirts, and his pants, at his socks. Lou said, I see you have all your clothes in a pile. Why don't you wear some others once in a while? Jack said, well, when I remove clothes and socks, I wash them and put them away in the box. Then comes the next morning and up I hop. I go to the box and get my clothes off the top. 

Lou quickly realized the problem with Jack. He kept clothes, CDs, and books in a stack. When he'd reach for something to read or to wear, he chose a top book or underwear. Then when he was done he would put it right back. Back it would go, on top of the stack. 

I know the solution, said a triumphant Lou. You need to learn to start using a queue. Lou took Jack's clothes and hung them in a closet. And when he had emptied the box, he just tossed it. Then he said, now, Jack, at the end of the day, put your clothes on the left when you put them away. 

Then tomorrow morning when you see the sun shine, get your clothes from the right from the end of the line. Don't you see? said Lou. It will be so nice. You'll wear everything once before you wear something twice. And with everything in queues in his closet and shelf, Jack started to feel quite sure of himself. All thanks to Lou and his wonderful queue. 

[END PLAYBACK] 

DAVID J. MALAN: All right. [LAUGHS] 

AUDIENCE: Great! 

[APPLAUSE] 

DAVID J. MALAN: Sure. So that paints a picture of these two abstract data structures. But if we really were to dive underneath the hood we could implement them in a number of different ways. But we really, I think, need some building blocks via which we could solve problems like those. And we'll see today too, some others as well. 

So let's rewind back to week two when we implement-- we introduced you to your very first data structure. That is an array. And an array, recall, was just a chunk of memory whereby elements were stored by design back to back to back. It's an array of contiguous memory specifically. 

So with an array, we could certainly store not just one thing but two, or three, or even more. And so, for instance, if we treat my computer's memory as this abstraction here, and pictured here are three bytes or some multiplication thereof, suppose we're storing in the computer's memory an array of size three, storing the digits one, two, and three. 

Well, remember, that if we zoom out per last week, there's other stuff going on in memory. So even if we want to add another number to this array that we didn't think of when we first started the program, like the number four, ideally we would put it right here next to it. Otherwise it's no longer an array. So by definition, if we're using an array, it's got to end up right there after the three. 

But what else is going on inside of your computer's memory? Well, assuming your program is of any length, and you've got other variables, other functions, you've been running it for a while, there's a lot going on. And your memory's being used and reused. 

So for instance, somewhere in memory might be immediately adjacent to this, Hello, comma, world, backslash zero, the null character, just because maybe you have another variable somewhere in there that is storing that particular string alongside your existing array of size three. 

And all of these Oscar the Grouches here really just represent what we called last week garbage values. There's obviously bits there because they don't disappear. They're always going to be inside of the computer somehow implemented. But we don't really know or care what they are. They're the remnants of those bytes having been used for other older variables, previous function calls, or the like. 

But the problem clearly here is that, OK, one, two, three is there. But the H is here. And unless I want to start taking a bite out of my string by overriding the H with a four, we just can't fit it right there. And yet, even though there's Oscars all over the place, those are indeed garbage values. And therefore, we could use that space because it's technically unused. 

We just don't know or care what the values are. So where could I put one, two, three, four? Well, my gosh. I have all this memory down here that's unused. I could certainly change those garbage values to be one, two, three, four. 

But to do that, I might need to do a bit of work here. It's not just a matter of just saying boom and it happens. Now with C and with code, I'd have to do this a little more methodically. So let me abstract away everything else that's a distraction. 

Let me assume that there is indeed at least four bytes available for numbers, just down here that we could have put them in a bunch of different spots. What's involved now in moving the one, two, three to this new chunk of memory so we can add the four? 

Well, I think conceptually we're going to have to copy the one from old to new. Copy the two from old to new. Copy the three from old to new. And then ultimately, we can get rid of the old memory. Those three original bytes could now look like Oscar the Grouch and just be garbage values for all intents and purposes. But now I have room for a fourth byte wherein I can put the number four. 

So this is nice. But what's a downside of this approach? What's a downside of solving the problem in this way, where the problem at hand is just to grow the array, so to speak, to increase its size, to fit one or more numbers? Seems pretty straight forward. But yeah. 

AUDIENCE: That it's just out of order. You move the one, two, three, four to the very bottom. 

DAVID J. MALAN: Maybe it's out of order. But I think that's OK because the order is just matters that it's relative. So so long it's still contiguous back, to back, to back in a different chunk of memory, I think we're OK there. It's not like I changed it from four, three, two, one. But a reasonable hunch. Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah. I didn't really plan ahead here. If I have to add another number, like five or anything else, well, I might have to jump through these hoops again. Maybe I get lucky and maybe there's space there. But not if I have other variables and other things going on, that too might be used at some point. Other thoughts? Yeah. 

AUDIENCE: Slow efficiency. 

DAVID J. MALAN: Slow efficiency, why? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah. I mean, it's just inefficient. It's bad design arguably. Why? Because I had a copy all of my original work down here. And as you note, if I want to add a fifth number, I'm going to have to copy it again, and again, and again. And do things n times again and again. 

Now, maybe that's necessary. We'll soon see for sure. But it feels like this is not going to end well, especially if the array isn't of size three or four but 300, 400. Your computer ends up spending so much time just spinning its wheels. I mean, honestly, better might be this. If this is my same array physically incarnated now, one, two, three, it's literally on the edge of the shelf. So there's no room for the number four. 

Maybe where we could take this story is, well, let's just find room for the four. Let's just put the four, for instance, over here, replacing some available garbage value, some spare byte over here. But now, wait a minute. I've broken the definition of an array. I can't have one, two, three and then four over here. So maybe there maybe could be a mechanism if I put this thing on again, where when you get to the end of the existing elements maybe I just somehow digitally point to the fourth array. 

And maybe we can stitch together all of these different values in memory so that if you follow the arrows, so to speak, we can reconstruct exactly what the order is even without having to find or make room here or pick up all of these numbers and move all of them over there. So that's perhaps the direction in which we'll go here. So let's see how we might get to that spot as follows. 

Let me go ahead and open up, say, VS Code here. Let me open up a program called list.c in my terminal. And let me go ahead and whip up a relatively simple program that just demonstrates what we did back in week two when we introduced arrays as follows. 

Let me include stdio.h so we can print stuff out. Let me do int main void. No command line arguments for now. Let me give myself an array called list of size three. And I'll just hard-code it to keep it simple for lecture's sake, each of which is going to be an integer. 

And now, just so we have some specifics to talk about, let me put it list bracket zero the number one, list bracket one the number two, and list bracket two the number three. So I'm just translating into code what we just had pictorially on the screen and also physically here with these numbers on the desk. 

Now, let's just do something mildly useful for this. How about we do four int i get zero, i is less than three, i plus, plus. Let's just print each of these numbers out just to make sure they're indeed in memory as I intended. So percent i backslash n comma i and then a semicolon. 

And I think that's it for now. So nothing interesting. No problem solved just yet. Just a proof of concept. So that now when I clear my terminal and run make list no apparent errors at the terminal. And so, when I now do dot slash list, I should see, hopefully from left to right, one, two, three. 

But of course, if I want to add a fourth number now, there's no mechanism for such. Certainly in the code that I just wrote I could go back in here and change this to a four. I could go down here and change lists bracket three equals four. I could just manually change the code, recompile the code. But of course, that doesn't give me any additional runway for the fifth or sixth number. 

So let me try to take a different approach drawing some inspiration from last week. If I want to allocate memory dynamically, maybe because I don't know when I wrote the program how many bytes I want, we have another function as of last week that does not require that you commit in advance to a certain number of bytes via what function can you just ask the operating system for a chunk of memory. 

So malloc, allocate memory. Now, an array is just a chunk of memory. And even though since week two we've been using this syntactic sugar, this convenience of just using square brackets and indexing into it, it's just making it easier to manipulate a chunk of memory that's contiguous all together back, to back, to back. 

So today, just like last week, we can take those training wheels off and maybe be a little more deliberate in how we allocate memory. Let me go, for instance, and do this. Let me delete my contents of my main function here. Go back into main. 

And let me propose now that I declare, for instance, how about my list no longer as an array but as a pointer. So int star list. And I'm going to go ahead and initialize this to be how about a chunk of three integers for now? So I'm still going to hard-code it. But I'm taking a step toward more dynamism for now. 

So let me allocate three times whatever the size is of an int. But it's usually going to be four bytes, as we know. So this is really going to be 3 times 4 equals 12. But it's a little more dynamic. 

And now, what can I do down here? Well, this is just a chunk of memory. So I can do literally list bracket zero equals one. List bracket one equals two. List bracket two equals three. And voila, achieve the exact same effect. Because, again, an array is just a chunk of contiguous memory. But malloc gives you any old chunk of contiguous memory so you can rather treat one like the other here. 

Now, if you really want to be cool, you can do something like this instead. You could dereference the address in list and go there. You could go down here and dereference list plus one and go there. But honestly, no one really writes code like this. It's just too cryptic. It's a little too far over the line at least for most people. 

And so, I think the syntactic sugar as I keep describing it, just the more user-friendly square bracket notation does the exact same thing, figures out the pointer arithmetic, and puts each of these integers in the right chunks therein. 

Now, just to be super pedantic, let me make sure if something went wrong. So if list equals equals null, that means that something went wrong. Like my computer is out of memory, which we should check for typically. So let me just immediately return one signaling anything other than zero, which means success typically, just to get out of this program because something's wrong. 

But now let me propose that I've had a-- well, let's do this. For int i gets zero, i less than 3, i plus plus. Though a better design would always be to use a const. But I'm just doing this for demonstration sake. Let's print out each of these ints too. 

And just make sure I didn't mess anything up. And let me open my terminal window again. Let me do make list again. Huh. Implicitly declaring library function malloc we type void star something, something implicitly declaring is the operative words there. What did I mess up? Yeah. 

AUDIENCE: [INAUDIBLE] need the header [INAUDIBLE]. 

DAVID J. MALAN: Yeah. I forgot the header file in which malloc is declared. I remember now, OK, that's in standard lib.h. And it's fine to look stuff like that up if you forget. So let me include standard lib.h. Now let me clear my terminal. Run make list again. Now we're good. dot slash list. 

And now, what did I do wrong? Oh. [LAUGHS] OK. Not intended, but teachable moment. What did I do wrong? [LAUGHS] Yeah. 

AUDIENCE: You are printing [INAUDIBLE]. 

DAVID J. MALAN: Yeah. I'm printing the values of i instead of what is at location i in the array. So what I actually meant to do was print this out. Thank you. So now let me recompile make list dot slash list. And now, those are the three values I was expecting, not the indices thereof. 

Now, let me just propose that for the sake of discussion that I regret having only allocated space for three integers. And maybe I really should have allocated enough space for four. Now, this is not how you would do this in practice. Because presumably if you have a change of thought just go back in and correct the code. 

But let me propose that somewhere in here is a more complicated program and time passes, dot, dot, dot. There's a lot of other interesting code there. But at some point, I might want to give myself more memory. 

So how can I do this? Well, let me just ask the operating system now for four new bytes of memory so that we can at least in version one implement the idea on the board where I just copied the three bytes into the new four bytes and then added a fourth value. 

So I'm going to use malloc again. And I'm going to say, here's a new pointer. I'll call it temp, tmp for short, which is quite common when you just need it briefly. I'm going to then call malloc again. I'm going to say, give me four integers using size of. Let me again make sure. So if temp equals equals null something went wrong. 

So let me just immediately return one. And for good measure, before I return one, let me free the original list so that I don't leak memory. So I'm not just immediately returning one. I'm being a good citizen and remembering, well, if this malloc call did succeed and indeed I got as far as line 18, but then line 18 failed, I should free the memory that I previously malloc'd. So again, that's the rule of thumb. If you allocate it, you should be the one to free it even before you're about to quit. 

Now, once I've done that, I think I need to do what we did pictorially on the screen where I need to copy the one, the two, the three from the old array into the new. So how might I do this? Well, let me give myself a loop. So for int i get zero, i less than 3, i plus plus, because the size of the original is still the same. 

Let me go ahead and treat the new chunk of memory called temp as an array itself. And so, I can absolutely use these square brackets just like before. It's just a chunk of memory. I'm treating it like an array. And let me add to that value whatever is at the original list at location i as well. So this, again, is just this exercise of copying from old to new step by step the one, the two, and the three. 

But I still need one additional step. If my goal at hand now is to have ultimately a fourth value here, well, I'm just going to hard-code this for demonstration sake. And I'm going to go to the very last location of temp, which is of size four. Which means the last element in temp is temp bracket three, because it's zero-indexed. 

But there's four total spaces there. And I'm just going to arbitrarily for the sake of discussion put the number four there. And that is what happened when we proposed changing the final garbage value there to that four. 

But now I need to do what the slide did for us magically on the screen. I should now do a couple of final things. I should free the original list, which I've not done yet, because I only called free earlier in cases of error. And that was just to be safe. I can now free the list. 

And now, if I want to inform the computer that I want list, quote unquote, my variable called list to point at not the old chunk like it originally did but the new chunk, I think I can just do this-- list equals tmp. And again, that's just saying that if list is a pointer, which it was. Because look at the very top line here, on line six I declared list to be a pointer to a chunk of memory. 

Temp meanwhile is a separate pointer to a chunk of memory. So down here, this line 33 is just a matter of my saying, OK, now henceforth, because I've already freed the old chunk of memory, my list variable should point not at this chunk of three bytes but this chunk of four bytes or really 12 in total now. Or rather 16 now because we have four such bytes. 

Questions now on this code, the point of which was quite simply to demonstrate how we could implement in code this idea of fairly correctly but inefficiently allocating a new array of sufficient size and then populating it with a new fourth value. Questions on what we've just done here? No? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Good question. At this point in the story, with line 33, do I not have two different variables pointing at the same chunk of memory? Short answer, yes. 

But here's where the semantics are perhaps compelling. List is the variable that I intend to use longer term and keep around in memory. And again, assume that there's even more code going on here that we just didn't write yet. So it's useful to have that variable. 

Temp was just a necessary evil. Because up here, it would not have been correct to do this. It would not have been correct to say list on line 18 equals the new chunk of memory because this would have represented a memory leak. 

If I prematurely change temp to point not at the old chunk but the new chunk, at that point no one's pointing at the old chunk. And so I've lost those three bytes. Valgrind, for instance, would yell at you for having lost as many bytes in memory. 

So in this case here, I do leave this as temp. Yes, it's duplicative at this point. But it's not a huge deal if it was just meant semantically to be a temporary value. But down here, at the risk of one more line of code, I still want to, to be a good citizen, free list, and maybe just for good measure return zero explicitly. 

But notice, it's not doing it twice per se on line 31. What am I freeing? The original address of list. The three-integer version. Then I change what list points at. So it's pointing at a completely different chunk of memory, this one of size four. 

So eventually, when I'm all done using this memory for this demonstration, I still need to free list. But at this point in the storyline 40, it's pointing at the new chunk of memory, which I similarly need to hand back to the operating system by free. Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: When would temp equal null? So let me scroll back up slightly. This is being a good citizen and a good programmer. Whenever it comes to using malloc, malloc can return null if the computer is out of memory. So this is maybe a much bigger program. You've got other things going on in it. And so, you just don't have enough memory available to be handed. 

Malloc needs to signal to you that there's some error. And so, it will buy convention per the documentation, per the manual pages return null. So this is just me being a good citizen. Otherwise, here's another error that might cause your program to crash with a segmentation fault. If you get back null but you assume that it's good memory going to address zero, a.k.a. null, will crash your program intentionally. Yeah. 

AUDIENCE: If you want to write [INAUDIBLE] at the very bottom of a program, and you just put [INAUDIBLE], it would [INAUDIBLE] the same [INAUDIBLE], right? 

DAVID J. MALAN: Correct. If I were to change my final line 40 here to be free temp, this would also work as well. And here, this is really a matter of design. It's a very nitpicky thing. We could probably debate it. But because at this point in the story my main variable for remembering where the list is is called list. 

This is the more responsible way to do it, freeing the list, just so that my colleagues, my TA doesn't wonder why are you freeing temporary memory that you already freed. It just is a semantic thing at this point. But good instinct. It would also work. Correct. Maybe just not good design. 

So it turns out that this gets annoying quickly as it did in the picture of doing all of this duplication. And even though technically it's necessary to copy those values, if you need a newer, bigger chunk of memory, there is at least a function in C that simplifies a lot of this for us. 

And in fact, let me go ahead and do this. Instead of using malloc, this second time on line 18 in addition to the first time I used it on line six, I'm actually going to try and introduce another function called realloc, which as the name suggests tries to reallocate memory for you. 

And it works a little differently from malloc. realloc expects two arguments. The first one is what is the chunk of memory that you want to try to grow or shrink, that is, reallocate to be a different size. And then you specify what size you would want. 

And indeed, in this case, I want four times size of int. And that will now give me hopefully a new address of a chunk of memory that's big enough to fit all four numbers. But what's wonderful about realloc is that it will handle all of the copying for me. 

So in fact, I'm going to go down here. I'm going to get rid of all of this, this extra for loop. And what I'm simply going to do instead is this. Once I can trust after lines 18 through 23 that realloc worked, and it didn't return null because I'm out of memory, I can just say, OK, just immediately remember that the new list points at this new chunk of memory instead. 

And then, I can still now do this line. But I can tweak the semantics here and just say list bracket three the new final location in the new list is four. I don't need to free this here. I don't need to do this. All I need now at the bottom is the final for loop to just print out these values. 

So in short, even though that was somewhat quick, using realloc just moves the entire copying process that I implemented myself a moment ago using a for loop. It just moves it to realloc and lets it deal with the copying for me. It's no more efficient. But at least means I'm writing less code, which is more pleasant. And hopefully, the people who wrote malloc or realloc are smarter than me and they just will introduce bugs with lower probability too. That was a lot. Any questions? 

AUDIENCE: Why do you still have to [INAUDIBLE]? 

DAVID J. MALAN: Good question. Why do you still need to make list equal temp as I did on line 24? So ideally, I would do this. Ideally I would just change this line 18 to be list. That is to say, call-- or actually, even better, ideally I would just say reallocate this list to be of this new size. 

But again, things can go wrong when allocating memory. You need to check a return value to see if it was successful or not. And so, we need to use a return value. So let's not introduce temp. Let's just use list. But here's where a memory leak might happen. In the off chance realloc fails and doesn't have enough memory for your four bytes, therefore it returns by definition null. 

You can't overwrite the original value of list with null to then check it. Why? Because now who remembers where the original three bytes were? If you prematurely change the value of list, you've lost. You've leaked memory in that sense. 

And so, that's why-- let me undo this change-- I declare a temporary pointer for the sole purpose of making sure I can check the return value. And then, once it's good, now I'll update the value of list. So it's doing a switcheroo by making sure first that you have a new value to swap with the old. Other questions on this code? Yeah. 

AUDIENCE: Does realloc [INAUDIBLE] memory where [INAUDIBLE] is stored? 

DAVID J. MALAN: Indeed. realloc automatically frees the previous memory for you. And better yet, it's even smarter than that. If you get lucky and there happens to be space right after your existing chunk of memory, so one, two, three, garbage value, instead of one, two, three, Hello, world, realloc won't even bother copying things from old to new. It will just say, OK, I'm going to now reserve for you more bytes than you originally asked for so it doesn't have to waste time doing that copying. 

And so, in that sense, this version is now not only still correct, it's even better designed because we're not wasting time with that for loop. We might have to resort to it if there is, in fact, Hello, world or something else in the way. But hopefully, we'll get lucky and save those steps. Other questions on this manipulation of code here? Yeah, in the middle. 

AUDIENCE: So [INAUDIBLE]? 

DAVID J. MALAN: What if you want to resize a two-dimensional array? So very similar in spirit whereby you can use the same trickery. Let me wave my hand at that for now just because I think that's going to significantly increase the complexity. But very same primitives ultimately. 

A two-dimensional array is essentially just a doubly long or quadratically longer list of memory that using square bracket notation is doing some of that mental math for you. But it's fundamentally no different of what's going on underneath the hood. 

So with that said and that code under our belt, even though that's not going to be something you'll frequently need to code yourself, let's propose now how we might go about building some actual data structures ourselves. 

The new ingredient here being this reality that if you want to resize a chunk of memory so as to make room for things, we now have that ability. Memory addresses. And pointers just give us the ability to point around at things and move things around in memory. 

But now that we have malloc and even realloc, you can imagine, maybe rewinding, and you could implement that stack, that queue using not an array per se, because you have to commit to an array size in advance. But if you implement your stack or your queue using a pointer and then malloc and realloc, and maybe someone else writes all that code for you, perhaps now you can imagine that now the stack can grow or shrink by using realloc accordingly. 

You don't have to preemptively say give me five bytes, or 50, or 500, or 5,000. You can say, just give me one initially. And if I need more, I'll realloc, realloc, realloc. And if you keep popping things off the stack, you can realloc in the other direction and ask for fewer and fewer bytes and the operating system can take that memory back as well. 

So we now have this building block. Let's see what we can do with it. So we've had a few pieces of syntax in recent weeks, all of which we're going to combine now in just a slightly more clever way. So struct is this keyword in C that lets us build our own structure in memory, like a collection of two or three or more variables, like a person that we've seen before. 

The dot operator, recall, we've used when you do have a struct like a person and you want to go inside of it. So person.name or person.number. We did this a few weeks ago. Now but the dot operator just allows you to go inside of a structure and get the individual variables within. 

And then, the star operator, unfortunately, has a lot of uses now. One was multiplication. My God, that was easy back in the day. Now it's used to declare pointers. It's also used to dereference pointer. So to make one exist and then go to that address. Unfortunately, it's the same symbol for all of those. But it's all related. 

But with these three symbols, it turns out-- you're going to get one last one today-- and my God, it finally looks like the concept. It turns out there's a clever way any time you want to use the dot and the star together, that is, to go somewhere, and go to an address, and then look inside of a structure, you can actually literally use an arrow symbol on your keyboard. It's not a single keystroke. It's a hyphen and then an open angle bracket. But at least it looks like an arrow. 

And we'll see indeed in code today, the things I was drawing pictorially on the screen last time with yellow arrows, you can actually now express as well in code. And so, here we have our next data structure called a linked list. And this is one of the most useful powerful concepts in C. It's the kind of thing that you can take for granted in Java and Python and higher level languages. 

But today, we'll see how we or others can actually build these things just using these same primitives. So a linked list is going to allow us to actually do what we used a foam finger for last week allow us to link together, for instance, these three values maybe with that fourth value over there. And then if there's a fifth, maybe this other foam finger points even farther over way to that fifth value. 

The key being that you can stitch together fancier data structures without having to pick all of these up and find new space. You just have to at least connect the dots somehow. We just need to somehow point from one to the other. And that's going to make things much more efficient, it would seem. 

So how do we get there? So here's my computer's memory as always. Suppose that I'm storing the value one somewhere in there and it's at 0x123 address, whatever. And I'm storing the number two somewhere else in memory, 0x456. And number three at address 0x789. This is not in array by definition. Why? Even though it's the only three things on the screen, what makes this not an array? 

AUDIENCE: It's not contiguous. 

DAVID J. MALAN: It's not contiguous. So this violates the definition of an array. But you know, especially since they're sequential, it kind of looks to a human like a list. So it would be nice if there were a data type called list. And there isn't in C. There will be in Python. 

But you know what? If I could somehow stitch together these three values so I can get from one to the next to the next, then I think we could achieve the idea the concept of a list without this really annoying constraint that they all be contiguous as in an array. 

So how do I do that? Well, at the end of the day I only have memory at my disposal. There's no more training wheels to take off here. This is what we've got underneath the hood of a computer. So if all I have is memory, I think the solution to this problem of stitching together those values in a list must be to spend a bit more memory. That's literally the only resource we have right now. 

So let me propose that if we want to create a list conceptually out of three values that are in random although pictorially pretty positions in memory, let me just add a little bit more memory to the picture. So in addition to storing the one, I'm going to leave myself some room, a little scratch pad if you will, to use some other bits as well. Same for the two, same for the three. 

And you can perhaps see where this is going based on last week. If I want to somehow connect the one to the two, any instincts as to what I should write in this box here that would lead me effectively from one to the two? What could go here? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: We could store the address of two. And so, specifically, what would you have me write here? 

AUDIENCE: [INAUDIBLE] pointer 0x456. 

DAVID J. MALAN: Perfect. Ideally, I would just put in this box another integer, one that happens to be represented in hexadecimal. But that's just a base system. It's just a human thing for us to look at. I'm going to put the value 0x456 here. 

So let me go ahead and reveal that. 0x456 goes there. You can perhaps see further where this is going. Well, if I want to get from the two to the three, I think I need to put below the two the address of the three, which gives me 0x789. 

Now if three is the end of the list, I don't want to let it be some garbage value. Because that would imply that who knows where it's pointing. I need some definitive value. And just what would your instincts be? If I want to make clear with some special sentinel value that the buck stops here, what do I put? What might my options be? 

AUDIENCE: Null? 

DAVID J. MALAN: Yeah. So null. Not N-U-L, per se, but N-U-L-L, which was the new keyword we introduced last week, which just represents an empty pointer, if you will. Technically the address 0x0. So literally, the zero address. 

And what humans did years ago, they just decided, you know what? Nothing should ever live at address zero in memory. We're just going to reserve that one special byte to be a special signal, a sentinel value such that if you ever see a zero address in a pointer, it just means it's invalid. It does not exist. 

Now, we write that though a little more pleasantly for the eyes as just N-U-L-L in all caps. And that's a keyword in C as well. But of course, last week, I claimed that who cares where things are in memory. And honestly, this quickly gets tedious even worrying about these values. 

So let me abstract this away and propose that if we want to remember where all of these numbers are in memory, let's give ourselves one final piece of memory that just allows us to start the whole process. 

Let me allocate on the left-hand side here not room for a number, like one, two, three, just room for a pointer that henceforth I think I'll call list by convention. And then store in that one additional pointer a value that just kickstarts the whole process. This is the treasure map, if you will, that you get handed. And this has the address of the very first actual node in memory. 

Now, technically, we could just start with this. But it turns out we'll see it's just a little cleaner to use a simple single pointer that leads to the things you care about, as opposed to just starting with the first element y. Well, if you ever want to get rid of this element, it'd be nice if you could at least still hang on to an empty sheet of paper that indicates that the list is empty would be one argument for that. 

So again, who cares about these addresses now? Now with the wave of the hand, let's just abstract it away. And there are our pointers. Each of those addresses in the squares at the bottom are simply pointing to the next element in the list. 

The jargon to introduce here would be that now that we have these integers one, two, three, but they're in these wrappers, if you will, these structures that have metadata that is additional data that is related to but not the data you actually care about. This is data. This is metadata. This thing here, rectangularly we'll call a node-- N-O-D-E. And it's just a term of art that means it's like a container in code for storing some values. 

This then is a linked list. And this then is the graphical incarnation of one node pointing to the other. In this case, they happen to be by chance and by design of this desk contiguous initially. But there's no requirement that they be such. The one could be over there. The two over there. The three over there. I would just need more foam fingers to point at one to the next. Questions on this concept of a linked list? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, in the back. 

AUDIENCE: [INAUDIBLE] array [INAUDIBLE] by pointer that is outside of the array itself? 

DAVID J. MALAN: Can you say that again? 

AUDIENCE: Do traditional arrays always start [INAUDIBLE] pointer that is outside of the [INAUDIBLE]? 

DAVID J. MALAN: A good question. Do traditional arrays start with a pointer that's outside of the structure? Short answer, no. Arrays are special in C and certain other languages. And the name of an array is technically a symbol, if you will, that the computer-- the program knows maps to a specific location in memory. It's just a label, a synonym for an memory address. It does not take up space. 

So to be clear, the name of an array does not take up space like that extra square on the left. But you do need that extra square on the left when implementing a linked list so that you can determine if the list is of size zero there's nothing being pointed at, or size three in this case. We're taking on more responsibility ourselves. Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: How do you point to the next element? Can you elaborate? 

AUDIENCE: These elements pointing to the next one, how does [INAUDIBLE]? 

DAVID J. MALAN: Ah, good question. If each of these elements is pointing to the next, how does three point to the others? Short answer, it doesn't. At least in this design we have more technically what's called a singly linked list. And as the arrows imply, it only goes in one direction. 

So if you somehow find in code maybe a for loop, maybe a while loop, somehow you're in code over here, you have no way in code to go backwards unless we change this to a doubly linked list where I add another box that lets me have arrows in both directions. 

Or maybe I just make it circular and I connect the three back to the one, which you can totally do. But that tends to make life harder because now you have to figure out when you're stuck in a loop in your data structure. But it's doable as well. But as is, it's a dead end by design. Other questions on this design here? 

Well, how might we implement this structure in code? Well, let me just connect the dots to something we've seen before here. This is how a couple of weeks ago, we introduced the notion of a person. And we claimed a person might have a name and a number. 

Last week, of course, we took off some of these training wheels. And a string is really technically a char star in both cases. But really, there's no conceptual difference beyond that. But let's use this same paradigm to implement a node as I described it in that picture. 

So let me get rid of the name and the number because that's related only to a person. And let me rename this structure for discussion's sake to node. That then invites the question, well, what needs to go inside of a node? Well, minimally, an integer. 

But this is now where we need to think a little harder, just conceptually. Even if you have no idea how to type it at the keyboard, what else needs to be part of a node based on these rectangular pictures that we've drawn? What more do we need? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah. We need a pointer to another node. So if I don't know how to implement this yet, it could be something like pointer to another node, how do I do that? Well, you know what? It turns out you would ideally say this. If you know that the next node is itself a node by definition, well, any time we've needed a pointer we just use the data type and a star. 

And I'm going to arbitrarily, but I think reasonably, call this second squared at the bottom of those rectangles next as the name of my attribute here. But node star just connotes that the next variable is going to be not a node per se but the address of a node. 

And that's exactly what we did. You had me put 0x456, 0x789 in that box, which is the address of another node. So the way we would express this in code would be node star next. But we could call the variable anything we want. 

Now, this is a bit of a white lie. But we'll fix this right now. This code won't actually compile. C takes you pretty literally, recall. And if you use some term at the top of your file that you don't define until later in your file, you're going to see some error message. We've seen this when I've messed up and I forgot to include the function prototypes at the top of my code. 

This is related in spirit. I seem here on my one, two, three, fourth line of code, I'm trying to use this new term of art that I invented here in my code called node, even though it's a CS term as well. But nowhere above this it would seem did I even define what a node is. It's not a data type in C. 

Every computer scientists know what a node is. But it doesn't come for free with the language. So I need to do something else. I need this word here to come first so that I can use it here. And so, we have this catch-22. How can a structure be self-referential, that is, point to another version of itself if the word doesn't yet exist? 

So the solution to this in C, which we didn't need for a person because there was no notion of listing-- connecting is a list-- we need one more keyword here that we didn't need for a person. And we reuse that keyword here. So kind of an annoying detail. 

But if we preemptively call this whole thing struct node, you can now refer to the thing on the inside as a struct node star. But then you can shorten the name of the whole thing from struct node to just node. Sort of an annoying sequence of steps. 

But in short, any time you're building a node, a linked list in memory, this is just the paradigm. You use typedef, struct, the name of the thing you want to define, like node. You use that name on the inside if you want to point from one to another. And then you can shorten it down here to just be called node. Questions then on this code here? Questions on what we just did? 

Well, if I rewind just a moment to that final picture, what would be the upside to be clear, of having jumped through these hoops and added this complexity if you will? What problem did we just solve by linking together these three values to be clear? Yeah. 

AUDIENCE: Making lists that are not [INAUDIBLE]. 

DAVID J. MALAN: Making lists that are-- 

AUDIENCE: Not [INAUDIBLE]. 

DAVID J. MALAN: Oh, that are not contiguous, if you will. So making lists that are not contiguous in memory. The upside of which is that if I want to add the number four to this list, it looks like I could choose from any chunks of available memory on the screen. I just need to point from the end of the current list to wherever that other one is in memory. 

What I don't need to do, to be clear, is copy the one, the two, or the three. Everything can just stay put. Which means time-wise I can do this much more quickly, it would seem, without copying things again and again. And even without using realloc to let it do all of the copying potentially for me. 

But as we'll start seeing even more in the coming weeks, every time we benefit and solve some problem, we pay a price. There's a trade-off. What is a downside as you might perceive now of using a linked list instead of an array? Yeah. 

AUDIENCE: You use twice as much memory. 

DAVID J. MALAN: Yeah. I mean, we use twice as much memory. Because now in addition to storing the integers one, two, three, I also need to store a pointer for each of those. And honestly, even this picture is a bit of a simplification. Technically, in most systems today, each int would be four bytes. 

Technically today, most pointers though would be eight bytes. I just didn't want to draw this weird shape on the board where the bottom square is even bigger than the top square. But technically, we're using even more than twice as much space for these pointers. So there's that trade-off. 

Now, thankfully, decades after C was invented, memory is generally much cheaper nowadays. And so, it's OK to spend more of it if you need to. And it depends on what you want to optimize for. But that's absolutely here a downside. What's another downside of having transitioned to a linked list? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: You can't index into it. Now, I haven't even tried in code. But when you have a linked list you can no longer use square bracket notation. Because why? Well, square bracket notation just assumes the contiguousness of memory. Location zero is here. 

Location one is literally one to the right. Location two is literally one to the right, one to the right. These things, even though I've drawn it from right to left to just keep things pretty, there are gaps here. 

And this is just my interpretation of this. These gaps could be big. They could be narrow. They could be down here, up here. They could be anywhere so long as we're linking things together in this list. The computer can't just use bracket zero, bracket one, bracket two anymore because it can't do simple arithmetic and jump to the middle. 

And now, here's perhaps the worst price we've paid. If you don't have square bracket notation, or really, you don't have contiguousness, what algorithm did we just sacrifice for this dynamism? If you rewind even back to week zero. And we gave it a name in week three. What algorithm can we not use now if we can't assume that the memory is back, to back, to back, to back? 

AUDIENCE: Binary? 

DAVID J. MALAN: Binary search. Why? Because binary search, just like the phone book, back in the first week, requires being able to arithmetically jump right to the middle. Take the total length of it, divide by two, and boom. You're right there in the middle with some simple arithmetic. Here they might be laid out, again, with these big or small gaps. There's no simple math I can do to just jump immediately to the one in the middle. 

And in fact, again, if this TV were bigger, the two could technically be in memory be way down here or even way over here. The foam finger could be pointing in any number of directions depending on where malloc put the thing. There's just no way to do binary search. And so, it would seem that we've paid another price indeed in terms of a performance. We're now talking about linear time again. So that's a regression. 

Now, that's also a lot. Feels like a good time for some muffins and fruit out in the lobby. And when we come back, we'll try to solve the problem we just created. So see you in 10. 

So we are back. And let's see if we can't now take some of these higher level concepts of stitching together these nodes in memory and translate it to some actual code. But we'll do it step by step first before I actually start writing it in VS Code. So if, Carter, you wouldn't mind helping me step through with some visuals, let me propose that line by line we solve some of the problems that we've just created for ourselves in building this thing in memory. 

So let's go ahead and first consider how we could build a linked list containing the numbers indeed one, then two, then three. And let's translate each of those steps to code and then we'll put it all together into something that actually runs. 

So how about the first step here will just be this. To declare a pointer called list that's initially has no value, at least at this point in the story. List is the name of the variable. Node star just means that this is essentially going to be our little square over here that points to the beginning of the list. 

Of course, it's ideal if it ultimately has a value. Because when we initially call this line of code, it just gives us indeed that square over here on the left. But it's got a garbage value because there's no equal sign on the other side there. So let's propose that we do one more step here and actually initialize it to null so that if only we know that it's not garbage, it at least has some known value. 

And null is a good way of signifying that at this point in the story the list is empty. Indeed, null indicates there's no nodes in the list. So that picture would now look like this, whereby let's just draw-- instead of writing null everywhere, I'll just leave the squares blank when it's not a garbage value, per se. It's literally 0x0 or null. So that's it for building a linked list of size zero. We're done then. But we want to now add a one, and then a two, then a three. 

So next step here might be this. If I want to allocate the first of my rectangles on our previous picture, I'm going to call malloc. And I'm going to ask for enough memory to fit a whole node. Now, technically, I think that's going to be four bytes for the int and eight bytes for the pointer even though I did not draw it to scale on the board. 

So that's technically going to be what, 12 bytes? But again, size of node just figures out how many bytes I actually need dynamically. That's going to return to me the address of that chunk of memory, which apparently I'm going to store inside of a temporary variable called n for short for node. But let's see what this does pictorially. 

So when this line of code is executed, I first get, on the left, that variable n. It's got a garbage value by default because I haven't executed the whole thing from right to left. Meanwhile, on the right-hand side of the expression, I've got now a node somewhere in memory. It happened to be free here. This is where malloc put it for me. But it does have two garbage values initially. 

But because it's a node per my typedef earlier, every node I proposed is going to have a number and a next pointer. So we can see those labeled here. But they've got two garbage values initially. But all I care about initially is that ultimately n is pointing at that chunk of code. So initially, if we could back up two steps, we have-- two steps. 

So we have initially-- oh, one step forward. We have this line of code gives us this variable here, which has garbage. When this side of the expression is executed, that allocates the memory. And then, when we copy from right to left the address of that chunk of memory, that's what gives us conceptually this arrow. And the garbage goes away because that's a valid pointer now. 

Of course, there's still two garbage values there because we haven't set this node to store a number like the number one. So let's go ahead and execute one other line of code like this, which, while cryptic-looking, is just an application of ideas we've seen in week four and prior. Star n means to start at this variable and go there. Follow the arrow is what the star or the dereference operator does for us. 

And then, the dot operator, recall, when we first introduced structs, like for a person struct, allows us to go at the number field or the next field. So if I do star n, and then in parentheses to make sure order of operations is preserved, dot number, and then assign it the actual number one, which puts the one in the top of that rectangle. 

Now, admittedly, this syntax is not very user-friendly. It's annoying to remember. You have to have the parentheses. So there's another syntax for this. Whenever you're doing two things like this in code, dereferencing a pointer that is going to an address. 

And then further using the dot notation to go inside of the structure, you find that wonderfully C gives us this syntax, whereby you can just change the star and the parentheses and the dot to just be an arrow. 

And again, it's not a single character on your keyboard. It's a hyphen and then an open angle bracket. But I kind of like the semantics of this. Because this code now pretty much matches the picture-- n arrow leads you to the value that you want to access or ultimately change in this way. 

There's one step, though, we've forgotten, of course, which is that we can't leave this garbage value here. Because the garbage value is some unknown value that effectively is pointing who knows where. And we don't want to accidentally misinterpret that garbage value as being a valid address and risk going there. 

So of course, what value should we put here instead? Our old friend null, just to signify that this is indeed the end of the list. And we could do that with a line of code like this. And again, we'll connote as much by just leaving that empty box blank. 

So now, we have a list of size one. Let's go ahead and add the second number to it as with these lines here. List equals n allows us to remember that indeed, we have this list here. So if we can step one step forward. Here's what the picture now looks like. 

And technically, let's go one step further here. This is now really what's going on in memory once my list of size one exists. My main variable called list is pointing at exactly that first node. At this point in the story I don't need to know or care about the temporary variable that I called n, even though it might very well still be there. 

But indeed, this now represents that linked list. Let's now indeed add the number two. So with the same line of code as before, I'm going to allocate another node. Size of node. Ideally, I would be checking for null here. But we're doing the juicy parts only on the slides. Let's now go ahead and depict that. 

So what happens with this? This brings back our n pointer, which might have been there the whole time. But we're doing this step by step. It's a garbage value though because we haven't yet copied from right to left. Malloc, of course, gives us a second chunk of memory, which maybe ends up there with two garbage values by default. I've omitted the labels now just because they're still going to be number and next respectively. 

Once we copy from right to left, the garbage value indeed becomes an arrow. Oscar disappears because it's now indeed a valid pointer pointing here. Now, the values themselves number and next are invalid-- garbage value. So here is where we can now start using our new syntax like the arrow notation or the star and the dot if you prefer. And we can change the value of n-- follow the arrow to number. And that becomes two. 

Similarly, we can do this again and set n arrow next. So start at n, follow the arrow, access the next field, and set that equal to null. Now, we're not quite done yet because we haven't actually linked things together. So here's now where things get interesting. How do I combine these two? Well, let me propose this. 

Let me propose on our next line here we actually update for now list equal to n. That is to say, whatever address this is, whatever it's pointing at, change list to be the same address that is point at the same thing. So if n is pointing here, let's change list to point here. 

And go ahead and do that, Carter, if you could. I don't like this. Can you go one further step? This is bad. What is wrong about my sequence of operations here where I updated list to point at my new node? Yeah. 

AUDIENCE: We [INAUDIBLE]. 

DAVID J. MALAN: Yeah. We lost the pointer to the other node. So I don't even care about the ordering, two one or one two. The bigger problem now as the lack of arrows over there suggests is that I have a memory leak. I have orphaned my original node in the sense that nothing is pointing at it anymore. 

Now, absolutely, I could fix this by adding some temporary variables. I could add it to the mix. But at this point in the story I have not done any such recollection thereof. So let me back this up. And let's go forward in the slides. 

This is where we left off a moment ago. I think I need to take into account order of operations. And I'm going to keep this simple. I'm not going to care about the order of the numbers for now. I'm fine with a list that is two and then one. 

So with that said, let me go ahead and update, I think, this box here to point at my original node. So let's see how we could do this in code. n arrow next. So n, arrow, next should equal the current list. 

And this is a little weird again. But recall what list is. List is this pointer here that just contains the address of the original address of the list, or equivalently, it contains this arrow, whatever it's pointing at. 

So what this means in this line of code, n bracket next means start at n, follow the arrow, access the next pointer, and set it equal to whatever list equals. So if list is pointing here, then next should point there as well. 

This, I think, is safe. Because now we have redundancy. Now we've got two pointers pointing at the original list. And now I think we can do another step whereby we update list to equal n, same line of code before that got us into trouble. But I'm doing it second now instead of first. 

When I execute list equals n, this now sets list equal to the same thing that n equals. And so, now I have successfully inserted my new node containing two into the list. 

And in fact, if we advance one more, we can just clear up the clutter, assume that the temporary variable is gone from the story. Now we have a linked list where admittedly ordering is wrong. It's two one instead of one two. But at least it's linked correctly. And I didn't orphan or leak any memory. Questions on this sequence of steps here? Yeah, in back. 

AUDIENCE: So [INAUDIBLE] this is all [INAUDIBLE] type, right? [INAUDIBLE] 

DAVID J. MALAN: Yeah. Spot on. So this would fall under that category of a stack, if you will. Although I've not called it that by name because I just pushed the number two onto this data structure, if you will. And indeed, it ended up at the beginning of the list instead of the end. 

And so, here's where we see a distinction between an abstract data structure, which is where we began. A stack is a thing like the pile of sweaters that just has push and pop properties and LIFO access-- last in first out. 

How do you implement something like that in memory? Well, it would seem that you could implement the notion of a stack here not for sweaters but for numbers using a linked list. So long as you implement insertion a.k.a. pushing by pretending new values to the list by pretending again and again. 

And if, Carter, you don't mind hitting the keyboard one more time. If I wanted to add the number three now, you could imagine prepending it to the list. Why? Well honestly, especially as this list gets longer and longer, I kind of like the appeal of prepending these elements. Why? Because even if this list gets crazy long and way, way out here, you didn't notice me following all of the arrows earlier to do the insertions. 

If I want to insert a fourth number, a fifth number, a sixth number, all I have to do is insert it here, if you will, point it at the original start of the list, then update this pointer, and done. And I would say that's two steps, give or take. It's not going to be n steps as it would be if I had to append the new nodes to the end of the list. 

Now, of course, we've sacrificed ordering of these numbers. They're literally in the opposite order or whatever order they were inserted in. But that might very well be OK depending on the goal at hand. Thank you to Carter for stepping through this. What if now we wanted to translate this-- 

[APPLAUSE] 

Oh, sure. Thank you. [LAUGHS] It's all for you, none for me in this example. So here we have perhaps a way of translating this now to some actual code. And this will be the last of the intense code here just to give you a sense of how we can translate this idea now to actual steps. So this is list.c in VS Code here. 

Let me go ahead and make a couple of changes up top. Let me go ahead. And how about declaring a node using typedef struct node using our new framing as before. I'm going to give every node a number, as I proposed. 

And every node a pointer to the next element, which is going to be implemented just as before. And I'm going to simplify the whole name as just node. So all that is is the exact same typedef that we proposed earlier. 

Now, let me go ahead and get rid of all of this code which we wrote earlier. And recall that this was the most recent version that was not a linked list. This was just an array that we allocated and then reallocated. So this is the old way of doing things. 

But it was inefficient because we might have to lean on a for loop or lean on realloc to copy everything around. We're now going to re-implement the notion of a list as an actual linked list, not as an array. 

So my main function now might do something like this. And I'm going to really just copy the lines of code that we just stepped through on the board. So let me give myself a special variable called list. That's going to be initialized to null. And this is just my pointer, the square on the left-hand side of the screen that represents the start of the list. And if it's null, it means the list is empty. So done. I'm done implementing a linked list of size zero. 

Well, now, how do I want to run this code? Well, let me propose for the sake of discussion that this version of the program will take command line arguments. So I want to be able to do something like this. I want to run this program ultimately and type in three command line arguments like this, one, two, three. 

And I want my program in a couple of minutes to allocate one, two, three nodes and stitch them together just like the visualization on the board. I could use get int. But it's just going to be faster if we use command line arguments. So again, I'm just borrowing some concepts from week two. But none of that's possible yet until I change my code here. 

So let's do this. Int argc string argv. But you know what? We know that strings are not actually a thing anymore. So I can change my command line argument definition to be what it really is. It's really char star. 

But it's the exact same thing as in week two, just strings are no more, at least without the training wheels on anymore like last week. And now let me do this. For int i equals one, i is less than argc i plus, plus. 

So what I'm doing with this loop is I just want to iterate over the command line argument. So I have one number at a time from the prompt. What else do I want to do here? Well, let's go ahead, and how about do this. Let's get a number. So int number equals argv bracket i. 

So a couple of notes here. One, I'm starting for loop at one instead of zero. But I'm going up to argc. argc is argument count, how many words are at the prompt. Why am I starting at one instead of zero though given my goal? Why am I starting one? Yeah. 

AUDIENCE: Because [INAUDIBLE] the first value [INAUDIBLE]. 

DAVID J. MALAN: Yeah. So the first value in argv is actually the name of the program. That's obviously not a number. So I want the second value. So I'm going to start iterating over those command line arguments at i equals one. So that's all. I just want to get the actual numbers at the prompt. 

Unfortunately, argv, bracket i, is a string, a.k.a. char star. That is not an int. So this line of code won't work. But can anyone think back to week two where we had a function for converting strings to integers? Anyone? 

AUDIENCE: a to i 

DAVID J. MALAN: Yeah. So a to i is a function that converts ASCII to an integer assuming what you give it as an argument looks like a number like one, or two, or three. So let me fix this. Let me actually do the conversion. 

If I were really being careful, I would error-check this, make sure that there's no digits, just like you might have in problem set two. But for today's purposes, I'm just going to assume the honor system that the user, me, is going to run the program correctly. 

So now that I have a variable containing the number from the command line, let's just allocate a node for it. So let me do node star n, just like we did in the visualization. And let's malloc enough space for the size of one such node here. I now need to just be super safe. So if n equals equals null, like if I'm out of memory, you know what? Let me go ahead and just immediately return one here. 

Otherwise, if that's not the case, let me go ahead and update the number field of this new node, which at line 24 does exist because it did not return null. So I did not exit early with return. And let me just store whatever number this human typed in first. So the return value of a to i, which per line 17 is in my variable called number. 

And then, let me go ahead and just prepend this to the list. Let me go ahead and say that this next field first has a known value null, just so that we get rid of that second garbage value. And let me go ahead and now prepend it to the list. So if I want to prepend it, that means this new node must have a next field that points to the current beginning of the list. 

And again, the goal here is to prepend, prepend, prepend. So whatever the current list is, let's change it so that this new node points to that existing list. And now, step two, as before, was to update the actual list to point at this node. 

So recall in red on the screen before, I screwed up originally. And I only did this line by moving the pointer too early, if you will. But I fixed that once Carter helped me rewind and we got rid of the red line, which indicated error. And I just do n arrow next to change the next field of this new node to point to the existing list. So I'm not orphaning anything. 

At this point in the story, I think my code is correct, not batting very well though today. But I think my code is correct. But the program doesn't do anything interesting. So it would be nice to now iterate over this linked list in memory whatever its order is and print things out. Well, how do we do that? 

Well, it turns out if you want to iterate over a linked list, the general paradigm is to do something like this. To define a temporary variable, I could call it temp. But another convention that you might as well see is called pointer, ptr for short. But you can call it anything you want. And you can have a temporary variable first point at the first node in the list. 

And then in some kind of loop, like a while loop, you point it at the second node in the list. And then you keep iterating. You point it at the last node in the list. And then, eventually, you iterate too far, effectively pointing at null, at which point your while loop can presumably terminate. 

So how do I implement that idea of allocating a temporary pointer that just points at each node in the list and lets me print out ultimately each of those numbers? Well, let's go back to my code here. 

And let me do this. Let me go ahead and declare this temporary pointer, which is going to be a node star also. Why? Because it's the address of a node. The first, the second, the third. And I'm going to set that equal to whatever the beginning of the list is. 

So that is going to be equivalent to this version of the picture here, where pointer is just temporarily pointing at the first node in the list. It's not pointing at list per se, it's pointing at the first node in the list, which list is also pointing at itself. 

Once I've done this, I think I can translate this to code that's a little new-- but it's conceptually familiar perhaps now-- while that pointer does not equal null. So while I have a valid pointer, like my finger or that arrow is pointing at an actual node in memory, well, let me go ahead and print it out. 

So let me print out with percent i backslash n whatever is in the current node at the number field within. And again, this is going to have the effect, hopefully, of first printing the three. And I think I just need to now update the pointer so that on the next iteration it's pointing at the next value. 

So if this is where the story is, how do I update pointer to point at the second element of the list? Well, I want pointer to point at the two. And I want pointer to eventually point at the three. Well, how do I do that? 

Well, the way in code I can follow these arrows is as follows. If I currently have pointer pointing at this node but I want to point it at the next node, I can borrow this pointer here. So whatever this address is in the first node, a.k.a. the next field, I can copy that into pointer. Because then, pointer will point at whatever this is pointing at by just setting one equal to the other. 

So once I've done that, the picture will become this. And how do I translate that to code? Well, new syntax is surprisingly straightforward. All I need do is say pointer after printing it equals whatever pointer currently is, but grab its next field instead. 

And this is a very common paradigm when iterating over a linked list and you're using some temporary variable like pointer, you can simply set pointer equal to pointer next. And what that means here is as follows. If this is pointer pointing from here down to here, pointer next is follow the arrow, grab the next field. 

So if you set pointer equal to this thing, that's the same thing as pointing this at this same box. And indeed, if I advance to the next slide, even though the arrows are technically pointing at different parts of the rectangles, that's just for graphic's sake, pointer is now pointing at the second node. And when I do this again on my next iteration, it points at this. 

And then, this last step, notice, when I keep doing pointer equals pointer next, this will become eventually this value. But what's this value in this linked list? It's null, technically. So this arrow will eventually take on this value when I set pointer equal to pointer next. And at that point ptr, my temporary pointer is going to be null. 

So it might as well look like this pictorially. And what does that mean for my loop? Once pointer is null, because you've walked off the end of the linked list, what's going to be true of this loop here started in line 32? Any observations here? What's going to be true? What will happen now as soon as we hit the end of the list? Yeah, sorry. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: The loop is going to break out. Why? Because line 32, which is constantly asking, well, pointer does not equal null. Well, if pointer finally equals null three steps later, the while loop is now done. 

And so, what I can do at the end of this program once I printed out those values, well, first let's go ahead and open my terminal window. Let's make list. Compile dot slash list. 

And let me try the same values, one, and two, and three. That's going to again allocate one node, two node, three nodes by prepending, prepending, prepending each of those values. And it's then going to iterate over them from left to right. And so, when I hit Enter now, what should I see on the screen if my code is correct? What will I see? Feel free to just call it out. 

AUDIENCE: Three, two, one. 

DAVID J. MALAN: Three, two, one, because I've prepended presumably. And here we go. I indeed see three, two, one. So the list is backwards. But all of the elements are there. 

Now, technically, if I ran Valgrind on this, Valgrind would not be happy because I have never freed any of my memory. So I should probably now have a second loop here that does something like this. 

Let me again set pointer equal to list. I don't need to redeclare it because I've already created this thing on line 31. I just want to reset it to be the beginning of the list again. And now, I can do the same kind of thing. While prt not equals null, go ahead and do this. 

Well, I don't want to just do free pointer and then do pointer gets pointer next. Why? My goal is to free all of my memory. But I think this is going to get me in trouble. Pointer equals list just gives me a temporary pointer that points at the three, and then eventually the two, and then the one. How? 

Well, while pointer not equal null, I'm freeing the pointer. So this is like saying to malloc, free that node, free that node, free that node. But what's the problem with what I've just done here? This code is technically buggy. Yeah. 

AUDIENCE: After you free your pointer, you have no [INAUDIBLE] what's next [INAUDIBLE]. 

DAVID J. MALAN: Exactly. After you call free on pointer, you are by social contract with C not allowed to touch pointer anymore. It is invalid. Now it's still going to be a number. It's still going to be a pattern of bits. But it's invalid. 

And you'll very often get a segmentation fault if you tempt fate in that way. So I can't free the pointer and then use it literally the next line. The solution here, like our swapping of the liquids last time, was to maybe just have a temporary variable. So I can do a switcheroo. 

And so, a common way to solve this problem to get the order of operations right would be to do something like this. Give yourself a temporary pointer like node star next. Set it equal to the place you want to go next, so we're one step ahead. Now you can free pointer. And then you can update pointer to be that next value. 

So essentially, you need two hands now. You create on line 41 another pointer that if this is pointing at the first node, the three, your new pointer is pointing at the two temporarily. So now you can tell malloc via free, release this memory. But I haven't forgotten where I want to go next. And so, I can now continue on. 

So a common paradigm for just iterating over these nodes and then freeing them, a couple of observations. Strictly speaking, I could have consolidated this. I don't need two loops to print the nodes and then free the nodes. I could do that all at once. But let's assume that there's other stuff of interest in my program and I don't want to just immediately free it. 

There's one other bug that I should probably address here. There is still a potential memory leak up here. And this one is super subtle, though Valgrind would help you find it. Notice that in this loop here when I'm calling malloc, this line of code is fine if the first line of malloc fails and returns null because I immediately return and I'm done. 

But what if the second call-- but not the first, or the third call, but not the first or second fail? This line of code has me returning immediately. You really need to do some garbage collection, so to speak, whereby you really need to go in and free any nodes that you did allocate successfully earlier. 

Honestly, that's going to be a pain in the neck. We won't do that here. But probably what I'd want to do is write a function called free list or something like that and call that function to free any nodes I had previously created. So it's not quite at the finish line. But the building blocks are indeed here. 

Questions on this code? And I think it's safe for me to promise that it won't escalate further from that. Questions on this? No? Well, let me show you one alternative that you might prefer. And I'm pretty sure this isn't an escalation, it's just an alternative formulation. 

Another way you can iterate over nodes in a list could be this. Instead of a while loop, for instance, let me actually show you one other piece of syntax here. You could technically use a for loop. You could give yourself a node pointer here that is initialized to the list. 

You can then check in your for loop that it's not equal to null. And then, you can do your update as usual like this. Either of these are equivalent. Even though this one I suspect looks scarier, it's doing the exact same thing in one line instead of two. But there's no reason we can't use for loops instead of while loops to achieve the same idea. 

But I'll leave these two as demonstrations of one approach or the other. But that's just like in week one, for loops, while loops, whatever looks simpler to you. Even though admittedly neither of these probably looks super clean. 

So let's take things back to things more conceptual here. Up until now, we've been inserting elements into this linked list by prepending them. Let's consider what the running time then is of these operations. So if I've got a linked list of size three or size n more generally, time has passed and I've added a lot of things to it, what's going to be the running time, for instance, of searching a linked list for some value? 

And I'll tell you already, it's not log n. Because again, binary search is off the table as per before break. So what might the running time be of searching a linked list for some value, like two, or three, or one, or 50? What might the running time be? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: O of-- I heard it over here. O of n. And why? Who was that? Oh, in the middle here? Who O of n? 

AUDIENCE: Because you're [INAUDIBLE] item in the list [INAUDIBLE]. 

DAVID J. MALAN: Exactly. You're going to have to go through every [? item ?] in the list starting from the left from the beginning, which is how we've been drawing things and connecting the dots. And in the worst case, the element might very well be at the very end. So it's going to be big O of n. 

What about insertion? How many steps in terms of big O notation has it been taking me to insert elements into the linked list using this prepend design? 

AUDIENCE: One. 

DAVID J. MALAN: Yeah. So it's technically constant time, big O of one. And again, one is just representative of any constant. It could technically be two steps, or three steps, or even 10 steps, or 100 steps. But if it's always finite and fixed, then indeed you can say it's in big O of one. 

Now, why is that? Well, again, no matter how long this list gets, so long as there's memory available for me I can just create a little splice at the beginning of the list to put in the new node, update the original list, and I'm on my way. And it keeps getting longer even though it might not be spread out in memory. So big O of one is possible with these linked lists if I indeed prepend things. 

Of course, if I prepend things, everything's going to get out of order potentially. And we're going to have maybe the stack property instead of a queue property. So we might want to do things slightly differently. So instead of doing this, whereby we kept prepending, prepending, prepending, suppose we append to the end of the list instead. 

So if we now insert the one, the two, and the three as we might want to for a queue, to maintain that fairness property, we might start with an empty list. We might add the one. We might append the two, append the three. And so, it just is laid out differently in memory. And again, if I can come to you in the middle, what's the running time of search, again, when the linked list uses this append implementation? 

AUDIENCE: Still big O of n. 

DAVID J. MALAN: Yeah. Still big O of n. Because in the worst case, you're going to have to go through the whole list just to find it. And notice, it doesn't matter if you have an intuition now that the bigger numbers might very well be at the end. You have no way to jump to the end. You have no way to jump to the middle or do anything resembling binary search. 

Every search has to start from the left and follow the arrows again and again. So I don't think we've done any better there. And in fact, what is insertions running time now in big O when we're appending to the list in this way, as we might to implement a queue instead of a stack? What's the running time of inserting a new value? Big O of? 

AUDIENCE: One. 

DAVID J. MALAN: So not big O of one in this case, but big O of n. Because if I'm appending, by definition I have to start here and traverse the whole thing looking for the end. Now, this is a bit of an overstatement. 

You could obviously optimize this slightly by maybe adding another variable that always points to the last element, sort of a cheat sheet or a shortcut that gets you all the way to the end. That's totally fine. It's not-- it doesn't really fit the traditional definition of a singly linked list. 

But there's absolutely smart engineering solutions to these kinds of problems. But as designed, it would indeed be big O event to insert to if you've got to go all the way to the end and you're not using a little extra memory to get yourself there quickly. 

Well, what if we want to take things one last step and not just append blindly, because even though I inserted one, two, three, if I inserted them in random order, they would end up in random order. What if you want to maintain a sorted list from smallest to largest? Well, then you might want to insert numbers like this. Starting from an empty list, we might have a two, then we might try inserting a one. 

But we want to keep it sorted. So now we're going to prepend in our code. But then you might want to insert a four. So you would append the four because you're probably going to look for the right spot to insert it. Then we're going to insert a three. And this one is getting a little annoying. Because now you have to iterate over the list, look for the right spot, and then do a little smarter of a splice. But it's possible. 

But you don't want to orphan the four, for instance. And then, ultimately, we get back to this question. What would the performance be of your linked list if you're trying to maintain sorted order? Well, search I think is going to be big O of n for the same reasons as before. What about insertion? Big O of what for inserting into a sorted linked list? Yeah, in the worst case? 

AUDIENCE: Big O of n 

DAVID J. MALAN: Yeah. It's still a big O of n. So it's no worse than, but it's not really any better than appending. But we gain the additional property of maintaining a sorted list, which might very well be useful if you're sorting your contacts in your phone or something like that where it just makes sense to maintain sorted order. 

Now, in the code for online today, if you take a look at some of the final versions of code, like list 6.c and list 5.c as we'll post on the website, you can actually see code that will solve all three of these problems, the prepend version that we wrote live, the append version which we talked through, as well as this sorted order one. But I think I'll avoid showing it live just because I do think that starts to escalate quickly. 

But I think we have enough of a building block if we're comfortable with prepending to at least solve some real-world problems with these linked lists. Questions then on linked lists which we'll now leave behind on their own but now use this technique to solve fancier problems but much less code. Questions on linked lists? 

So to recap, we've taken a sidestep with linked list. We have this dynamism now where we can grow and shrink our chunks of memory without over-allocating or accidentally under-allocating as in the world of an array. We don't have to worry about copying values endlessly because once you allocate the node, it can just stay wherever it is in memory. And you can just maintain-- you can just stitch it together somehow. 

But unfortunately, we've sacrificed what we started the class with in week zero, which was binary search, divide and conquer, which was like gave us that log and running time, which was really compelling if you think back to the demonstrations and the visuals. Can we get the best of both worlds? Can we get the speed of binary search, something logarithmic, but the dynamism of something like a linked list? 

Well, we can, actually, I think, if we start to think not in a single dimension, just the x-axis, if you will, but two dimensions, such that our data structures can maybe now have width and height, if you will. And so, a tree is perhaps the right term here. 

Much like a family tree, if you have your elders up here in the tree and then the branches below them for their children and grandchildren and the like. That's actually what a computer scientist means when they talk about trees, not a tree that grows up like this, but really one that typically is depicted growing down. Although this is just an artist's depiction no matter what. 

But there are certain types of trees in the world called binary search trees that are structured on paper and in visually like a family tree. But they have a special property that lends themselves to exactly that feature binary search. So for instance, here is an array back from week two. 

And I've sorted a whole bunch of numbers herein from one to seven. We know we can do binary search on this structure if it's implemented as an array. But what feature do arrays, to be clear, not have that linked lists do? Today's kind of a seesaw. What did we just gain by adding linked lists that arrays do not allow Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah. You can insert more elements without having to copy or moving everything else around. Right now, in this single dimension, if these values to the left and/or right are already used, then you have to move everything. And that's where we started today's story. 

So arrays kind of paint you into a corner. Because you have to, by definition, decide in advance how big they are. Well, couldn't we have some kind of array that can still grow but still is contiguous so we can do binary search in some way? Well, yes, if we rethink how we implement binary search. 

Let me propose that this, I've chosen these seven elements in the array much like the lockers from week two to be ordered from smallest to largest. I've highlighted now in yellow the middle elements here. 

And if we were telling the story of week two going left or going right, let me highlight in red the middle elements of the left half and the right half. And then, let me further highlight in green the other elements in between those. 

And there's actually a pattern here, as you might notice. Whereby there's one yellow in the middle and then there's the two red and the four green. There's an implicit structure there, if you will. And what if I do start to think in two dimensions, and instead of laying out an array of lockers like this on the x-axis only, what if I slide the four up, and pull the one, the three, the five down and draw this in two dimensions instead? 

Well, let me do that, as by separating these things like this. Such that, now, let me propose that each of these squares maybe it doesn't have to be contiguous. It can be anywhere in the computer's memory. But I can't have these crazy gaps among them. How could I perhaps keep these things connected conceptually? What should I add to the picture, if you will? Yeah. 

AUDIENCE: Branches? 

DAVID J. MALAN: Say again? 

AUDIENCE: Branches. 

DAVID J. MALAN: So branches metaphorically here. And more technically in the language of C, maybe just some arrows, some pointers. So I won't bother drawing things as rectangles constantly. Let me propose that we're now just abstracting away what a node is. But let me claim that each of these squares now is a node. And a node might have a number. But it might also have a pointer. Heck, maybe even two or more pointers. 

And let me draw those now. I don't care about addresses like 0x123, 456, 789 anymore. Let's just draw our pointers with arrows. But now, let me propose that we could very well think about this as a tree storing what was previously array data. But now, each of these nodes can be anywhere in memory. 

And moreover, even though I've painted myself into a corner visually on the screen, so long as there's more memory in the computer, I could put the number zero over here. I could put the number eight over here. And if I'm smart, I could probably, if I want to insert other numbers, like 2.5 or 1.54 values in between, I bet we could make room by swiveling things around and just hanging things off of these branches slightly differently. 

And so, what does this gain me? Well, if I instead start to model my data not single dimensionally but in two dimensions, and I connect those nodes with these pointers, what can I now do? I think I just gave myself back binary search. Why? Suppose I'm searching for the number five. How do I find it? 

Well just, like in a family tree where you might visually start reading from top to bottom, I'm always going to start from the so-called root of a binary search tree. This is just like the list pointer that kicks off the whole linked list process. This is the so-called root. Here I am at the number four. I want to find the number five. 

What decision can I make when I see that I'm currently at the number four, just like the phone book from week zero? Where is five not? It's not to the left. And if I had built a little mobile here or something we could very dramatically snip off this branch, this [LAUGHS] is very low-budget animation. These nodes could fall to the ground. And we're left with half of essentially, a tree. 

But what do I now know? It's obviously the five to the right. So let me go to the right. Six is obviously not the one I'm looking for. But what do I now know about the five? Well, five is less than the six. So I can snip this off here because I know it's not going to be down there. And I can follow the remaining arrow here. And voila, I just found it. 

And now, without getting into the weeds of the math, I've got here what, seven elements. That's roughly eight if I round up. And if I do some log base two, I actually-- one, two, three is the key detail here. The height of this tree is three. Because I took a list of size seven, and I halved it, and I halved it in order to let it dangle in these two dimensions, plus or minus one for rounding sake. 

So what do I get back? I now have binary search. But it's not like the middle of the middle of the middle. I now follow these arrows in one of two directions. So each of these nodes now has an int and maybe a left pointer and a right pointer. But you can call them anything you want. 

And so, I've gotten back binary search and dynamism. Because if you want to add zero, or eight, or nine, or 10, we can just dangle them at the bottom of the binary search tree. 

So what would this look like in code? But we won't actually implement it line by line. Well, here was previously our definition of a node for a linked list, which was one-dimensional, if you will. Even though it might bounce up and down on the screen. It was still just a line, if you will. 

Well, let me get rid of the single pointer in the linked list. Let me make a little bit of room here in this typedef. And let me propose that we just add two pointers, each of which is a struct node star. One will be called left by convention. One will be called right by convention. 

And so, long as someone, not me, not today, not in class, writes the code that stitches together this data structure too, handling both the left child and the right child so to speak, I think we can indeed stitch together that two-dimensional structure. 

And moreover, once you have this in memory, you can translate pretty elegantly to code binary search itself using a principle we talked about recently too. Here is, for instance, a function that I'll write by just clicking through steps called search whose purpose in life is to return a Boolean. True or false, the number I'm looking for is in the tree? This search function therefore takes two arguments, the number I'm looking for called number, and then a pointer to the tree, the so-called root of the tree. 

Now, how can I implement binary search in code? Well, recall our brief discussion of recursion. It turns out recursion is a beautiful technique. And honestly, more obvious technique when you have two-dimensional structures, which finally after five-plus weeks we now do. 

Here is maybe my first line of code here. If the tree is null, then obviously return false. You've handed me an empty tree. There's nothing going on. Obviously, the number you're looking for is not going to be here. So that's my safe base case to make sure I don't screw up and recursive infinitely. 

Well, what else might be the case? Well, if the number I'm looking for is less than the tree's own number. And now, recall that tree is a node star. So even though I'm calling it a tree, it's really the current node that's been passed in. So if the number I'm looking for is less than the current node's number, then I must know that the number I'm looking for is to the left, so to speak. 

So how can I solve that? Well, this is where the magic of recursion. Just return whatever the answer is to calling search again but on a subtree, if you will. This is the equivalent of snipping off half of the tree. Pass in the left subtree, if you will, with the same number. 

Else, if the number you're looking for isn't less than the current node's number but greater than, snip off the other subtree instead. And just return whatever search says it finds in the right subtree here. And then, there's a fourth and final case. What else could be true logically? yeah. 

AUDIENCE: Number equals [INAUDIBLE] number? 

DAVID J. MALAN: Perfect. If the number you're looking for equals equals the number in this node, then I'm just going to return true. And you might recall from our recurring discussions of design, I don't strictly need to ask that explicitly. Either there's no node, it's to the left, it's to the right, or you found it. So I can just whittle that down as usual to an else. And this now returns my true. 

So here too, this is where recursion, once you get comfy with it, start it gets pretty elegant and cool in the sense that, wow, even though there's a lot of lines here, I mean, there's only a few interesting lines. A lot of it's curly braces at that, which strictly speaking I could get rid of. And so, recursion lends itself to elegance when it comes to traversing these two-dimensional data structures as well. So that is in code how you might implement something like search. 

Questions then on these trees? We have dynamism. We can insert more nodes to them. They're faster because we get better your search back. But, but, but, there's got to be a price paid. Any downsides, or question, or downside? 

AUDIENCE: Question. 

DAVID J. MALAN: OK, let me come back to that and just one sec. Downside though, what price have we paid for this dynamism and for this binary searchability? Even though I've abstracted it away in the picture? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Say again? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: We're using a lot of memory. I'm kind of misleading you now because I'm just drawing these little squares with the simple numbers. But there's actually three things in there. A four-byte integer, an eight-byte left pointer, an eight-byte right pointer. 

So we're already up to 16, 20 bytes now to store individual INTs. That's probably OK though if memory is relatively cheap and voluminous as it nowadays is. But these are the kinds of trade-offs. 

And here, too, you see a hint of why some people still do like, and you see-- and in fact, it's so omnipresent. Because when you have C you can really fine-tune how much memory is being used for better or for worse under the hood. 

As we transition soon to Python, these decisions get made for you. And you have much, much less control about how much memory is being used by your program because someone else made the design decisions for you. Question. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Is it bad if we don't the parent node? Not necessarily. There's no reason why you need to have pointers in both directions. However, that can lend itself to efficiency. By spending more space and having arrows go up to you can actually save more time when searching the tree and other contexts. This though would be the canonical way, the typical way to implement it. But absolutely, just like a doubly linked list, that could help you solve other problems too. 

So turns out I'm overselling binary search trees. There are perversions of them, so to speak, whereby they won't actually behave as advertised. For instance, here's a good situation. Suppose you've got an empty tree initially. And you insert the number two. Well, it's got to go somewhere. So it might as well become the root of this binary search tree. And let's assume that someone wrote the code to do this. 

Now you want to insert the number one and you want to maintain the searchability of this tree. Well, it's important to note that binary search tree is different from tree. If you've just got a tree in memory, there is no social contract with where the numbers need to go. They can be completely random all over the place. 

Binary search tree means that you can do binary search, means that any node here is going to be greater than every node here and less than every node here. And that's a definition. It's a recursive structural definition that must be true to be a binary search tree or BST. 

So if we maintain that property ourselves, let me insert two, let me insert one. One belongs there by that definition. Let me insert three. Three belongs there by that definition. But I kind of got lucky in that I in the story inserted two and then one and then three. 

Let me propose a sort of perversion of the algorithm whereby we just get unlucky let me propose that we insert one first. And then, we insert two. Well, where does two go? Well, logically, it goes to the right because it's larger. 

Now, the user inserts three. Where does it go? It goes there, logically. And how does this story unfold? The user inserts four, five, six. It's wonderfully sorted in advance by luck. 

But this is a perversion of the structure in what sense? It's still technically a binary search tree. But what is it look more like? It really is devolving, if you will, into a linked list. 

And so, if you, the programmer, don't implement a binary search tree with some kind of repairs going on, such that as soon as something gets, whoa, a little too long and stringy, I think I can fix this. It's going to be an annoying line-- a number of lines of code, which we're not going to write here or in a P-set. 

But we could pivot this thing. And we could just rejigger things so that the two becomes the new root. The one becomes the left child. The three becomes the right child. But that's what, two, three-plus lines of code. It's possible. It's doable. But it's extra work. It's extra code. 

So unless you write that code though and maintain balance of these trees, just because it's a binary search tree does not mean its height is going to be log base 2 of n. The height could be n, in which case you don't get those properties. 

So when it comes to looking up in a balanced binary search tree, yes, it's log n. But if it's unbalanced, if you don't add that additional logic in those repairs so to speak, it could devolve into big O of n. And this is a whole category of algorithms and fanciness that you would explore in a higher level course on algorithms and data structures. There's lots of way to do that sort of fixing that I'm alluding to in the picture there on the screen. 

A few other data structures, if you will, toward an end of a sort of computer science Holy Grail. So log n is repeatedly a really good place to end up. We started in week zero and we got log n. We lost it earlier today by introducing linked list, but we just got it back, albeit at the price of spending more space. 

But the Holy Grail, so to speak, when it comes to algorithms would not be big O of n, certainly. Definitely not n squared like our bubble sorts and selection sorts. And not even big O of log n. What's better than all of those? 

Just big O of one, constant time. That's the Holy Grail. Because if we could store huge amounts of data but find it instantly in one step, or two steps, or heck, even 10 or 20 steps. But independent of the size of the data structure that's pretty powerful. I mean, that's the secret sauce of the Google's and the Twitters of the world trying to get back results really, really fast. 

Well, it turns out another abstract data type or abstract data structure might be something called a dictionary. Just like the Merriam-Webster Oxford English dictionaries that you might know which associate, say, words with definitions. 

Well, you can think of a dictionary really abstractly as this. Two columns maybe on a spreadsheet of sorts where the left column represents something and the right column represents something else. The word is on the left and its definition is on the right. And that's almost literally what a dictionary is on paper. You've got all the words and all the definitions right next to it. 

But more generally, in computing, a dictionary really just has not words and definitions per se, but key value pairs. This is a term of art. And we're going to see this again and again, especially as we transition to web programming, keys and values. Key is what you use to look for something. 

The value is what you find ultimately via that key. So that's the generic term there. We've seen key value pairs really in the past. In week zero we talked about your contacts and your iPhone or Android phone being an app that has a whole bunch of contacts presumably alphabetized by first name, or last name, or the like. 

Well, one of those contact cards ultimately has someone's number, for instance, like John Harvard in this case. So in that type of application, the keys is the name, like John Harvard that you use to find information. 

And the value is the number that you find there. Or if there's more information like where he lives and email address and the like, the whole contact card could be the value thereof. The key is what you use to look up John Harvard. 

Now, back in week zero-- oh, and rather, the corresponding table then if we draw this in two columns wouldn't be word and definition or key value generically, it would be name and number, for instance. So we're just slapping some new terminology on this old contacts problem. 

Well, this is the picture we drew way back in week zero, whereby I claim that log of n was really, really good. And indeed it was and has been since. But the Holy Grail would indeed be something more like this in this dashed green line constant time. 

And maybe not literally one step, but a fixed number of steps that even as the problem gets huge and you go way, way out on the right of the x-axis, the problem does not depend on the size-- the time to solve the problem does not depend at all on the size of the problem itself. You can have 1,000 contacts or 100,000 contacts, constant time means it takes the same number of steps no matter what. 

Well, how can we get to that point? Well, there's a couple of final building blocks today. And there's one called hashing. And this is something that will recur a few times. But for now, hashing is all about taking as input some value and outputting a simpler version thereof. 

So for instance, here's a gratuitously large deck of cards, which are all the more visible as a result. And in a deck of cards, typically you've got what, 52 cards plus maybe the jokers and whatnot. And each of those cards has a number of sorts and a suit on it. And here are literally four buckets on the stage. 

And how might I go about sorting these cards? Not just by number but also by suit. Well, you could certainly spread them all out and make a mess of things and just reason your way through it and get everything in order according to suit and according by number. 

But most of us, even if you don't have four buckets at home, probably are going to do something a little more intuitive, feels like an optimization. Where if I find the nine of hearts, I'm going to put that into the hearts bucket. The king of spades, I'm going to put that into the spades bucket. The jack of diamonds over here. And I'll do this with the queen of diamonds, and the ace of clubs here, and the three here, and the 10 here. 

And even though it's still going to be 52 steps, why am I-- and maybe at home, why would you perhaps do this step first? What's the value of bucketizing the values in this way? And that actually is a term of art. What's the value of doing this first before you sift through and try to sort the numbers? Yeah. 

AUDIENCE: It's easier to make sure you're not [INAUDIBLE]. 

DAVID J. MALAN: Yeah. It's easier to make sure you're not missing anything. And it's taking a problem of size 52 and shrinking it into four problems of size 13, if you will. And so, that just helps simplify things, maybe reduces the probability of errors and the like. And what I'm doing here, to give it a technical term, is that I'm hashing the values. I'm taking as input a card like this. And I'm reducing it more simply from a larger domain to a much smaller range, if you will. 

So here is a domain of 52 possibilities. I want to map that to a range of four possible outcomes-- the diamonds, the clubs, the hearts, or the spades here. And by doing that I'm just shrinking the size of the problem. So hashing does that. It's literally an f of x type arrangement whereby you pass something in and you get back a simpler known value. 

Well, a hash function more technically is the algorithm, or even the math, or even the code that implements that idea, converting something bigger to something smaller to this indeed finite range of values. 

And it turns out that hash tables are a wonderful application of arrays and linked lists to try to leverage the best of both worlds. The goal being theoretically to achieve that Holy Grail of constant time. And that's going to be a bit of an overstatement because you're not always going to achieve it exactly. But at least we can get a little closer there too. 

So with hash tables, you have something that looks like this. This is just an array. This is an artist's rendition of drawing it vertically instead of horizontally. But that's just a detail graphically. And this array, for instance, maybe is of size 26. And where am I going with this? 

Well, how does Apple, how does Google store your context alphabetically in your phone and search for things quickly? Well, they might-- they probably alphabetize at least in English according to A through Z. Or if we convert that to numbers it's like what, 65 through whatever. Or really, zero through 25 suffices. If we're using an array of size 26, we start counting at zero and we count up to 25. 

But let's abstract that away as just letters of the alphabet. So maybe what Google and Apple are doing in your phone is storing all of the A's up there, all of the Z's down there, and everything else in between. And so, this works pretty well if you start adding your friends and your family. 

So for instance-- and I'll get rid of the letter so as to not distract. Alvis might go in that first spot because A, you subtract a 65, maps to zero. So we put him in the first bucket, the A bucket. Maybe Zacharias ends up all the way at the end there. And then in the middle might here be Hermione. And if we do this dot, dot, dot, you keep adding all of your classmates, you might get a contacts database that has all of this data herein. 

Now, each of these nodes, they're drawn differently because this is just another artist rendition. These rectangles, these long rectangles represent a contact card, like John Harvard's that's got the name, maybe email, definitely phone number, and things like that. 

So this seems great. Why? How can I find Alvis? Well, I go to the A bucket. How do I find Zacharias? I go to the Z bucket. How do I find Hermione? I go to the H bucket. But, but, but, I've done this very deliberately. What problem will arise eventually assuming you have enough classmates? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah. There'll be too many people, too many contacts for all of the available spaces in the array. There's still some room here. But I'm pretty sure if I think back to this particular class, we've got not Hermione but also Harry, who's also an H. Hagrid, who's also an H. So where do put them? I could just put them arbitrarily in any of the open spots. But then you lose the immediacy of jumping right to the H, right to the A, right to the Z. 

But now that we have linked lists, we can combine these ideas. Use an array to get to the first letter of the name you care about. And then if you have a collision, so to speak, whereby someone's already there, you don't do something stupid like put Harry down here just because it's available, or maybe Hagrid down here just because it's available because then you're losing the immediacy of the lookup. Why don't you just stitch them together in a link list? 

Now what does this mean. This means for most of the characters here, you have constant time lookup. You look up Alvis, boom, you're done. Zacharias, boom, you're done. OK, Harry, Hermione, Hagrid, it might be one, two, or three steps. So that's actually devolving into something linear. 

But here we make a distinction today between theoretical running times, which we keep talking about, and honestly, a clock on the wall running times that actual humans care about. This is way faster than a linked list because you don't have to search every name. It's even faster than an array because you don't need to do binary search. 

You can literally, for most of the names, find them in constant time-- one step. And again, it's not theoretically constant because these-- if you only befriend people who have H names, it's going to be a crazy long linked list anyway. So again, it really depends on what the nature of the data is here. But this is pretty close to constant time. 

And in fact, how could we get even closer? How could we reduce the probability of collisions for the H's or any other letters? How could we avoid putting too many H names together? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Say a little louder. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: OK, yeah. So we could add another dimension, if you will. But let's not add a third dimension, per se. But let's indeed look at not just the first letter of everyone's name but the first and the second. And in fact, let's see if that gets us a little further along. 

So let me go ahead and propose, if you go through the whole Harry Potter universe, there's actually a lot of collisions if we keep going. And so, we've got the L's here, the R's, the S's, and so forth. Well, let's clean this up here. Hermione originally went to the H location. 

But let's decrease the probability of collisions there and everywhere else. Instead of putting Hermione, Harry, and Hagrid all together, let's go ahead and do this instead. Instead of labeling these buckets A through Z, let's give ourselves more buckets. So in fact, this might be H. Well, instead of H, maybe this should be HA, and then this should be HB, HC, HD, HE, HF. 

Now, some of those are a little nonsensical because I can't think of names that match most of those. But it's deterministic. At least we know the bucket will be there, which is important even if it's empty. And now, we can put Hermione here. We can put Harry here. 

But oh-oh. We didn't do this perfectly well. Hagrid still collide. So let me come back to you. How can we reduce the probability of Harry and Hagrid colliding? 

AUDIENCE: [INAUDIBLE] another letter? 

DAVID J. MALAN: Yeah. So we can look at the third letter. So let me try that. Instead of HA, let's look at HAA, HAB, HAC, dot, dot, dot, HAQ, dot, dot, dot, HEQ, HER, HES, and so forth. 

And now, I think those names and probably all of the others we saw are now much more cleanly distributed. There is much lower probability of collisions unless two people have almost the same names or one is a prefix of the other. 

But, but, but, even though we're now closer than ever to constant time because the odds that we hit a collision and have to devolve to a linked list are much lower, what's the downside that's not completely obvious from how I've depicted this on screen? What's the price I'm paying here? Yeah. 

AUDIENCE: So much memory. 

DAVID J. MALAN: This is a huge amount of memory. The number of cells here in the array is now what, 26 times 26 times 26 for the first, the second, and the third possible characters all combinatorically combined here. That's a lot. I didn't even draw them. I have the dot, dot, dot. [? Could you ?] evoke that instead? 

That's a huge amount of memory. This is a very sparse data set now. And odds are, you're going to waste so much memory, even for the names like HAE, HA, HEQ. I can't even think of names. So many of those buckets are going to be empty, not to mention the AAA and the ZZZ and everything else in between. 

So it's a trade-off. And it might be too expensive a trade-off. And so, you might have to tolerate something like the collisions we had earlier, whereby even though they might very well happen, at least you are decreasing the probability by perhaps having more buckets like this. And in fact, if I rewind now to where we might have gone with this, here's how we might represent these nodes in the tree. 

Previously, in the past, we've had a person who had a string name and a string number, a.k.a. now char star. And so, here now might be how in this hash table we represent someone's name and number as well as a pointer to the next element in the list. 

Let me rewind just to the picture here. We keep drawing different shapes, because, again, these are abstractions. Who really cares if they're at a scale now. We've got enough room for the person's name, not pictured on the screen it's Hermione's number. But that's somewhere in this rectangle. But yes, pictured here in this little square is a pointer to the next node in the list. 

So by storing name and number, maybe her address, maybe her mailing address, whatever, in addition to a pointer allows each of these nodes to be connectable just like the nodes in the linked list. But where they're starting is in an array. So the array gets us 126-- or gets us-- narrows the problem from size 26 to one, gets us to the linked list in question. Hopefully, it's a single person or perhaps it has more than that. 

Meanwhile, what is the hash table itself-- the hash table, the whole thing is literally just an array. I've hardcoded the simplest version of size 26 but what do each of those boxes in the vertical array represent just a pointer to potentially a node, a node in a linked list. And if there's no one there, if there's no one in location y, or x, or the like in that universe, well, it's just a null pointer signifying there's no one there. 

But if there is, it's going to be a pointer to a valid node from which we can get to any of the others as well. And that so-called hash function, just like the one I did with the greeting cards, well, it's just a black box, if you will, but implemented somewhere in code, like in C. And so, if you pass in Albus, what is the hash value of Albus? 

Well, in the first version of the story with 26 buckets, it should be a zero. If you pass in Zacharias, it should be 25. And so, just as my cards were being hashed to one of one, two, three, four values, now these names are being hashed to one of 26 possibilities, or 26 times 26, or 26 to the third power if you have more and more granularity than that. Questions on this implementation now of this idea of a hash table? 

AUDIENCE: Should we [INAUDIBLE] the value of null and then [INAUDIBLE]? 

DAVID J. MALAN: If you-- say that again with the null? 

AUDIENCE: Could you ever be [INAUDIBLE]? 

DAVID J. MALAN: Oh, a good question. So if there's so much sparseness, there's all of these empty cells in the array. Couldn't you just go in and free them, or delete them, or just shrink the array and not have AAA, and AAB, and AAC only have the prefixes, two or three characters that you need, you absolutely could do that. 

But now, what you lose is the arithmetic benefit of being able to map each letter to a number if you start freeing up unused space, you don't know that Zacharias is necessarily at location 25. Albus is still going to be at location zero. But if you've deleted some of the elements in the middle, Zacharias could be at 24 if you've deleted one, 23 if you've deleted another. 

And so, you don't have that arithmetic immediacy that you need in order to index into the array with constant time. And the same is going to be true if it's two letters or three letters. You need to be able to trust that you can do some quick math and jump to the right index in constant time. And that's, again, the appeal of these arrays. 

So when it comes to the running time of a hash table, inserting values into it, searching for values therein, at the end of the day, it technically is big O of n. Because in the craziest case, you might have a huge fancy hash table. But everyone in the universe has a name starting with H. And then, it just evolves into a really long linked list just like a binary search tree could do the same. 

But if you choose a smarter hash function, maybe you mitigate that and you don't rely only on the first letter but on the second, or the third as well, or some other combination of that input and make your hash function smarter, odds are if you get a good hash function you want to get it to be more of order of n divided by k, where k means constant mathematically. And so, k is the number of buckets. 

So ideally you want a uniform distribution. You want this many people here, this many people here. You don't want there to be some or no people. You want a uniform statistical distribution. And maybe you get that from human names, maybe you don't. But that's the challenge of a hash function. Of course, big O of n over k is not a thing because we always throw away constants like k. So it's still big O of n. 

But again, the distinction today is that, OK, yes, academically you learned in CS50 that, sure, it's big O of n. But my God, it's 26 times faster if you do the hash function well and you spread everyone out over the hash table. And that's the appeal of these kinds of structures. 

And we've got one more for you, if I may. And that's something now known as a try. So it turns out that a try is even cooler, if you like this kind of thing, in that it does not devolve into big O of n. It is truly constant time. 

But there's going to be a price. There's going to be a gotcha. A tri is sort of a fancier tree. And it's short for retrieval, but pronounced tri for weird historical reasons. But a tri is a tree, each of whose nodes is an array. 

So this is all crazy mash-ups now. People started inventing data structures just by combining different ones. So unfortunately, a lot of the good ideas are taken. But you just have benefits from certain aspects of those data structures. And combining them, ideally, gives you the best of both worlds, so to speak. 

So here might be the root of a tri. It's literally a big node, a big rectangle. But it's actually an array. So there's 26 locations in this picture here. 

And here's how you use a tri, for instance, the store names just like the hash table. You treat each of the elements of that array in that node as a letter of the alphabet. So A through Z or zero through 25. And if you want to store someone's name in here, you do so as follows. If you want to store an H, you index into the H location. 

And if you want to store the second letter of someone's name, like an A, well, you add another node below it. And such. One is connected to the other. And you then identify the A in that array. And then you go on and maybe put a G if the goal is to store-- spoiler now-- Hagrid in this data structure. And then the R, and the I, and then the D. 

But when you get to the D, the end of the name, you have to somehow flag that this is the end of a name that we've embedded into this data structure. So whereas all of these are called out in white just to make it obvious what we're connecting to what, green has to be like a bool that's true that just indicates the buck stops here. 

D is the last letter in someone's actual name. And what's kind of cool now about a tri is that we can repeat this for other names as well. So for instance, here's where we might put Harry as well. 

And notice, they share a common prefix, HA for Hagrid, HA for Harry. So we're reusing some of these nodes, some of these arrays. We can even slip Hermione in here too borrowing only the H. But she gets the H, then the E, then R-- R-M-I-O-N-E, and so forth. And we mark at the end of her name too that she's in there. 

Now, what's the takeaway here? Well what is the running time of a tri? How many steps does it take to find someone in this data structure? And let me zoom out so that it suddenly becomes a massive data structure with even more in it. Maybe it looks-- sorry. No, I'll keep it on this one. Maybe it looks a little something like this with just these three names. 

But how many steps does it take to find Hagrid, or Harry, or Hermione, no matter how many names are in this data structure? There's three at the moment. But it takes what? H-A-G-R-I-D, so six steps to find Hagrid. H-A-R-R-Y, five steps to find Harry. H-E-R-M-I-O-N-E, eight steps to find Hermione. 

But notice, that those steps are only dependent on what the lengths of the humans names. And let's assume that no one's going to have a infinitely long name. It's going to max out at what, eight? No, maybe 18, maybe 20, 30. There's actually some pretty long human names out there. But it's going to be finite. You know it's a bounded. Whereas most contexts in could grow forever. 

So what's compelling here is if you assume that the longest name is, I don't know, 50 for the sake of a theme here, then you know that finding anyone in this data structure will take more than 50 steps. 50 is thus a constant, which means you have big O of one running time. 

It doesn't matter if there's a million people in this phonebook or a billion people in this phonebook. That's going to definitely add more nodes to it. But it's still going to take you H-A-R-- I'm sorry-- H-A-G-R-I-D, six steps to find Hagrid. H-A-R-R-Y, five steps to find Harry even if there is a billion other people in that data structure. 

So now, we actually do seem to have constant time if you assume that there's going to be a bound on the length of the name. Why don't we use tries for everything then? What's the price we're paying for this data structure even though we've represented just three characters here? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: It's a lot of memory. Yeah. And you can see it even with these three names, most of the squares on the screen are empty, bytes and bits that are there and are allocated. And they need to be there because you need to be able to do that arithmetic thing of this being zero, this being 25. 

So you can jump from boom, boom, boom, boom, based on each of the letters. But it's a hugely sparse data structure, which means it takes up a crazy amount of memory. 

Now, maybe that's tolerable, especially for short names. But that's going to be the trade-off as well. And this is such a tension in computing. Almost any time you want to improve time, you want to speed up the efficiency, the speed of your algorithm, you're going to spend space. 

If by contrast you want to decrease the amount of space, you might very well have to increase the running time. And it is indeed, this seesaw back and forth. And you, your colleagues, your company need to decide what resource is the most precious. 

Heck, it might be much harder to code one of these data structures than another. You're a human. Your time is valuable. Do you really want to spend hours implementing a tri when, hey, in 30 minutes I can bang out an array nowadays or a linked list even. There too, development time is going to be yet another resource and why sometimes there's good code or bad code, it depends on what you're prioritizing. 

So what do each of these nodes look like in a tri? Well, we can keep calling it a node. This is a very generic term for just a container in these data structures. In this story though, let me claim that everyone has a number, like a phone number, a string, a.k.a char star. Every node has 26 children, or technically an array of size 26 that can point to more of these nodes. 

Notice that I don't need to store the name of someone in a try because it's implicit in the path that you take to find them. So that's a minor optimization. But it saves us some space. But this would be just a different data structure we could use to actually solve this problem as well, albeit at a very expensive cost. 

And what do we need our variable to be that stores the try? Just like before, we just need a single pointer that hangs on to the root of this structure that's null if it's empty or non-null if it's actually pointing at something. 

Any questions then on tries? And if it's feeling like a lot, the fire hydrant, it is. We started with arrays, then linked list, then tries. But questions on how we've just assembled from these basic building blocks? Yeah. 

AUDIENCE: Why isn't the root of tri [INAUDIBLE]? Why does that matter? 

DAVID J. MALAN: A good question. Why is this not size 26? It's just like with the linked list before, it just tends to be in code convenient to have a separate additional pointer that's small that just points to the beginning of the data structure. Because that way, it can be null, thereby clearly indicating there are no nodes. The whole structure is empty. 

If you allocated one of those nodes, you absolutely could. But then you'd be just wasting space, even if it's empty. And it creates an ambiguity. So just having a single pointer linked to the beginnings of all of these things is a good thing. Other questions now on tries, or trees, or hash tables, or arrays? 

So what problems might arise? Well, here's a counterexample. What names are manifest in this tri here? Feel free to just call it out. What do you see? 

AUDIENCE: Danielle. 

DAVID J. MALAN: Danielle and Daniel. So presumably, if these are two names here, one of which is a prefix of another, notice that the data structure still works. And I chose a friend's name and then appended a couple of more characters to it that's also a name because we have here D-A-N-I-E-L. 

And the green technically is implemented as a bool or something like that that indicates a word stops here. But we don't want to preclude storing Danielle as well, who's a superstring, if you will, of Daniel. And so, that's OK too, so long as the structure allows for the pointers to keep going. 

So even that works out OK whereas it might not have otherwise. And in terms of the running time, just to be clear, at the end of the day, tries do give you actual constant time for insertions, lookups, deletions, and the like because it's dependent only on the length of the input, the key, if you will, and not on how many other people are in your phone or address book. 

And I thought we'd conclude with a visual. If you've gotten out into the square, anyone recognize this? Sweet Green, a local salad place. What are we looking at here and what's its connection to today? 

You're about to become all the geekier in the real world because you will start to see data structures everywhere. What is this? Or how does this work maybe in salad form? Who's been to Sweet Green. Either of you. So how does this work? 

[LAUGHTER] 

AUDIENCE: [INAUDIBLE] They'll put your order [INAUDIBLE] your name [INAUDIBLE] L. 

DAVID J. MALAN: OK, good. So if you order a salad for someone named L, when it's ready, they put it in the L section here. And so, this is a set of key value pairs, right? If L is the first letter of someone's name, the value hopefully is the salad. And so, what you kind of have here is a dictionary, key value pairs, where it's not words and definitions. It's names and salads. 

And you can think of this too as kind of a hash table. Why? Even though it actually doesn't fit on one long shelf because the store is only so big, this is really an array. And apparently, A is missing or maybe it's around the corner. But this array just happens to wrap onto multiple lines. But it's still conceptually a single dimension. But suppose two people have the name L? What do they do typically? 

AUDIENCE: They just put the one [INAUDIBLE] second letter [INAUDIBLE]. 

DAVID J. MALAN: Yeah. So maybe they-- if they want to put that much effort into it. They might look at the second letter and then the third letter. Odds are this is not that interesting a problem to solve optimally in that way. But they probably do start stacking the salads on top of each other or maybe scooching it over just a little bit. 

And so, what do you have there? Well, now, if you start to view the lens through CS50 glasses, OK, you have an array. And then you have these linked lists that are sort of growing here. 

But even then you run into a problem. Why? Because it's not really a linked list. Because at some point you're going to hit the boundary here. So it's kind of like an array of arrays because you can only fit, what, three or four salads here. 

And so, long story short, we started today deliberately talking about real-world things like stacks and queues. And even though it did escalate quickly into binary search trees, and hash tables, and tries, even those things are everywhere. Even though they don't call them as such, these are just solutions to problems. 

And now, with this final week of C under your belt, you have all the more of a technical toolkit by which to implement these things in code. Next week we'll be able to trust that someone else solved all these problems. We'll introduce Python. And lines of code like this will finally become lines of code like that. So that's the promise ahead. And we'll see you next time. 

[APPLAUSE] 

[MUSIC PLAYING] 
