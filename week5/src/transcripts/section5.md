---
title: SECTION5 - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

CARTER ZENKE: OK. Hello, everyone. It is so good to see you here for our Week 5 Section. If you don't remember, my name is Carter Zenke. I'm the course's preceptor here on campus, and it's so delightful to see you all over Zoom. 

I thought what we'd do just to kick things off, assuming you can hear me this time, is to on the count of three, we'll all unmute at the same time and say a big hello. So on the count of three, we'll do one, two, three, hello. 

AUDIENCE: Hello. 

AUDIENCE: Hello. 

AUDIENCE: Hello. 

AUDIENCE: Hello. 

CARTER ZENKE: All right. 

AUDIENCE: Hello. 

CARTER ZENKE: It is so wonderful-- 

AUDIENCE: Hello. 

AUDIENCE: Hello. 

AUDIENCE: Hello. 

CARTER ZENKE: Hello. It is so wonderful to see you all here. 

AUDIENCE: Hello. 

AUDIENCE: Hello. 

CARTER ZENKE: And we'll go ahead and mute. 

AUDIENCE: Hello. 

CARTER ZENKE: OK. All right. So if you'd like to participate, feel free to do so via the chat. You're welcome to type in the chat to ask questions via the chat. Again, the goal for these sections is really to make sure that you're able to ask the questions you want to ask and for us to dive into this learning together. 

So today, focused on data structures. And this week, you build your own data structure with a speller problem set. And I want to focus on this big idea behind data structures. 

Why would we use them? What are the trade-offs between them, and how to actually use them in the real world. So to that end, we'll have three questions during our section today. 

The first will be this idea of the trade-off between data structures. When should we use one data structure versus another? The second question will be about these linked lists. 

We saw these in lecture, but how can we build our own linked lists? What can we do with them? And how can we better figure out how to actually use them in our code? 

And then, finally, our third question will be this idea of how do we build our own hash table where hash tables rely on a lot of fundamentals that linked lists can give us here, but can run maybe a little bit faster, as we'll see in the problem set for this week. So to really dive into things here and to make things a little more concrete, we saw all kinds of data structures. But often, when you're actually programming in the real world, you might choose one or another, depending on the scenario, what you're trying to build something. 

And in this case, what I'd like to do is show you all one scenario we can think about here. So imagine that you are working for some software company and they are making this digital assistant that runs on a mobile device. Maybe it's something like, hey, Siri, or hey, Google, or something that responds to people's voice over time on their personal device. You can do something for that person as they activate this assistant. 

Now, you've seen, or you've heard, that people who are using this assistant aren't often able to wake it up at the right moment. Maybe it sometimes doesn't work if I were to say maybe, hey, Siri, or, hey, Google. It doesn't quite work as I want it to. 

And so this is sort of a problem that we're running into here. But what we ultimately want to do is figure out, OK, well, how could we fix this? And maybe the first solution is to try to improve this by adding more words that could wake up this voice assistant. We want to store more data, more words, that could activate this voice assistant for ourselves. 

And the question that you might run into as a software engineer is, well, how could we best store all of these phrases we want our voice assistant to wake up to? What kind of data structure would you use to actually store these phrases that might activate our voice assistant? And we saw a few tools in our toolkit, a few structures in our toolkit. 

And one of these was the linked list, one of these was the try, one of these was the tree, and so on. So there's lots of ways we can do this. But let's think first about the different priorities we might have for this data structure, right? 

If we want to actually make this. Well, what do we want to prioritize here? So let's think about this. 

If we to add lots of words, we could really think of trying a few different approaches here. We could think of, well, a few different aspects, like, if our data structure is going to do a certain number of things, we might care about different aspects of how data structures are formed. Like, do we care about deleting things quickly? Do we care about inserting things quickly? 

Do we care about searching for phrases quickly? Like, for example, if I were to have this voice assistant and I'm trying to do something with it, do I care about deleting words quickly, or do I care about inserting new words quickly, or do I care about maybe if I were to speak something, if I can search and find that word really quickly? So often, when we're choosing data structure, we care about these kind of three things. 

How fast does it perform in these three areas? And so here, we run into our first question, right? If we want to figure out which way to prioritize, well, we could maybe say that we care about search the most. 

We want to be able to search and find a phrase really quickly. Maybe if the user speaks some word, we want to be able to figure out, is that word in the wake word list. Or maybe we really care about the user being able to quickly add a new wake word, like, I could say not just, hey, but hello, or hi. And I want to be able to program this data structure to sort of respond to that quickly. 

Now, what priorities might you have if you were faced with a scenario? If you want to chime in in the chat, which would you prioritize here between a fast insertion, a fast search, a fast deletion, if you're trying to do this? Feel free to chime in in the chat. 

OK. I'm seeing one person for search, OK, lots of searching, some insertion, too. Yeah. And so these are things we could probably reasonably disagree on, right? 

If I want to prioritize searching for some word, being able to speak it and have my assistant recognize it really quickly, well, that seems reasonable where we can make search our top priority. Or maybe it's also reasonable to say, well, I want people to make their own custom wake words. And so inserting something is really important to me, too. So it depends on what you're trying to build here. 

And so let's take a look at some of these tools in our tool kit. So the first one we said before was this idea of the linked list. And here's the linked list in full here. 

And the idea behind the linked list was that we're able to have these nodes where each node has a certain phrase inside of it-- at least in this case, trying to store phrases now in our linked list. And we have these nodes kind of follow each other in memory. They're no longer back-to-back, like, in an array, but they sort of build on top of each other and sort of follow each other throughout memory, being woven in to our bits and bytes, thereof. 

So if we were to use a linked list here, which of these three priorities would be kind of well-served by this linked list, like, what would a link list be good at in this case, do you think? Feel free to chime in the chat. 

OK. So I'm seeing some insertion. And, yeah, it's correct. So linked would be really fast to insert something into. In fact, we saw in lecture that all it takes to insert into a linked list is to simply make a new node and put it at the very front. And that's, basically, a constant time operation. It takes a fixed number of steps. 

So inserting into linked list is very fast and could be a good priority for our insertion here. But, again, what's the trade-off here? If we were to go with a linked list, what would be slower because we used the linked list now? 

Maybe insertion is fast, but what's not fast? Well, deletion is not very fast, right? But at least in this scenario, let's say we don't really want to care about deleting wake words, what's the other ones we can use, a little bit slow for us? 

Yeah. So I'm seeing search, right? Search would be pretty slow because, again, we have to sort of start at the very first node. Like, hey, and ask, OK, is this what the user said? No, it's not, let's go onto the next one. Oh, is this what the user said? Oh, it's not, let's go onto the next one. 

So we can only do linear search, basically, with a linked list. And this is a bit of simplification for how we actually do kind of voice recognition. But you get the idea, nonetheless, that we're trying to find and go through phrases that the user could have said. 

In a linked list, we have to go through every single node that we have, which, as I see in the chat is indeed going to be in big O of n going through n nodes to find a certain element inside of it. OK so we have linked lists here. But let's actually think of a new data structure. What if we use something like the hash table? 

And the hash table looks a bit like this. I'm going to go to the full screen mode here where it's a bit like a linked list. But what we've done is sort of categorize our linked list based on the very first character. 

And not all hash tables use the very first character, but this one, for example, does, and it is helpful in some ways. Like what would now be faster because we're using the hash table? What would be faster now? Feel free to write in the chat. 

OK. So I'm seeing some search, like, search is faster. And why is search faster, if you want to write in the chat quickly? Why would search be faster with this hash table now? 

So I'm seeing some of these ideas of indexing, right? And so-- right. If we look at the side of our hash table in this array on this left-hand side here, we've kind of split our linked list into several indexes, like, H, I, J, K and L. 

And in the computer's memory, these are represented with, actually, like, H, I, J, K and L. They're assigned some number. And we have a hash function that finds the number for each of these values on the left-hand side. 

But the idea here is that we're able to use indexing to figure out, OK, if I want to find the words beginning with H, I know right where to go, and I can only search those words. Or if I want to find the words beginning with L, I can search in that location, just find the words beginning with L. So indexing here is helping us breaking down our linked list into lots of smaller linked lists, too. 

So it seems if we were to insert into this hash table, it's also pretty quick, right? It's both faster searching and faster insertion. So why would we just not always use a hash table over a linked list? Like what's the problem with the hash table now? What's the trade-off here? 

Yeah. So I'm seeing this idea of memory. Like this hash table is going to take up much more memory than our linked list assuming, maybe, we have some buckets, some indexes that aren't really filled with these phrases. But it's also going to take us more memory to have all the different indexes possible here that we might want to actually have in order to make our lookup really, really fast. So it's a trade-off here is memory, as well. 

And now, it's got one other structure to consider, which would be this idea of the trie. And here's some brief visual of a trie. Would you like to point out some words you see inside of this trie, reading from left to right? What words do you see? 

You see hello, you see hey. Any other ones? We see help, certainly. Yeah, there's a few other ones in here, too. 

So this trie worked by trying of storing a node for every letter in our words. And this is very fast for lookup, right? If you want to figure out if hello is in this trie, well, all we have to do is see, OK, I see H, I see E, I see L, I see L, and I see O. 

Well, hello is in this structure, right? We know that it's in Here. So look up is very fast. 

And similarly, insertion is also really quickly. If I wanted to add Hi to this trie, well, I could simply go to the H node and say, OK, well, that covers the first letter. Now, I'll add I, maybe somewhere up above, and that's it. I've inserted Hi. 

So insertion and search are also really fast in our trie. But again, what's the trade-off here? Why wouldn't we always use the trie? 

Yeah. So I'm seeing this idea of memory again. Like, this is going to take up a lot more memory to store all the combinations of all the letters that could make up all the words we might want to have as our wake word for our assistant, right? And even beyond that, beyond the computer's memory, if you think about the time it would take to make a trie, a more complex data structure, well, that's real human time that you have to work on this, and might actually delay your shipment of some new feature, right? And 

So it's going to matter, not just how much time it takes for the computer, but also how much time it takes you to make the structure, if you wanted to actually make some feature for your own program, or your own company in the end. So questions on these structures so far? Happy to take some in the chat, if you have any. 

What questions do you have? A question about, does AI use data structures? Yes. So a lot of how AI can work so quickly is because we choose to organize data in these really efficient ways. 

And so by getting creative with the ways we actually make our data structures beyond even just linked lists and tries and trees, we can actually make AI a lot more quickly-- run a lot more quickly because it has access to this data structure laid out in such a way that it can run quickly in the end. So, yes, it makes use of a lot of different data structures, too. 

And this question about memory being so cheap these days. It is true. So memory is very cheap, right? If we wanted to make the trie here, maybe we don't care how much memory it takes up because memory is so cheap. 

But it also takes us time to allocate that memory, to put things in that memory. And so, perhaps, it's not always the case that because we have so much memory, we should just be kind of loose with it. We really need to take care that we're not using too much memory when we could, theoretically, maybe use less, if we wanted to. Nice. 

OK. So this is some of the ideas of trade-offs here, choosing one or the other, often going to cost us one thing or another. But, really, behind all of these structures is the idea of a node, where, if we look back at our structures here, we had maybe a trie, we had a link, we had a hash table, and we had a linked list. And it was composing all of these was this idea of some kind of node, some place we store data. 

And along with that, a pointer to some other pieces of data. So we saw last week, in Week 4, that pointers are helpful for pointing certain locations. Well, now, we're seeing the application of those pointers. 

Why would we even want pointers in the first place? Because we can build these much more complex data structures. So let's think about building these very first building block for these data sets, which is called this node. 

And in our code that we'll see in just a minute, we have this new idea of creating this node in code. And we've seen this kind of syntax before, right? Here is the code we would use to make a structure called a node. 

And we're seeing that same syntax for structs, like, we created a struct for candidates, we created a struct for people earlier. Now, we're using that same syntax to create a node. And what do you notice here? 

So first, we're going to look at the top. And C reads this top to bottom. So as it reads this code, it'll do the following. 

It'll say, OK, here I'm seeing we're going to define a new structure called a node. That seems OK so far. And then inside of the structure called node, we're going to ensure we have the following pieces of data. 

We're going to make sure we have a phrase. If we look at this, we're going to have space for a phrase that is going to be a string. And then we also have some space for a pointer to a node called next. And, again, we can store, like, Hi or bye in here. 

But we also have some new space for next, a pointer to a node. And that could have a real address in it, like, 0x123, or 0x456. But it has to point to some kind of node, right? 

So now inside this node, we have a phrase and a next portion currently empty, but we could put this data inside of it. And then once we finish reading this, we're going to say, all of this, everything we've done so far, the phrase, the next portions that are-- all of that to be wrapped up into this thing called a node. So we've created kind of here a template for what a node is. 

A node has a phrase in it and some next pointer in it. And we're going to call all of that a node. Now, you could change this. You can make sure it has an integer, you can make sure it has some character inside of it. You could even store more attributes, if you'd like, inside a single node. 

But for now, I'll focus on phrases, trying to store these activation words for our voice assistant for now. Now, questions on this structure so far? 

Yes, I'm seeing a question, is the next location inside the computer's memory? Is it actually in the byte below? Like here in our picture here, we see that the phrase portion is kind of first, and then comes the next portion. Are these two really next to each other in memory? 

And the answer for that is, generally, like, yeah. So these are going to be very close to-- they're in memory. They're going to be kind of right next to each other as we create this node throughout. 

And a question about, well, could we have a before field, like, a pointer to a before? And we absolutely could. So if we wanted to modify this, we could simply add a new attribute called before, and we could theoretically point to linked lists that are-- to nodes that are behind us, as well, in our current node. And that allows us to make more even more complex data structures overall, too. 

Now, a question here, we see a struct node if we go back here. So struct node, star, next. Is that a pointer to the struct, or just a simple pointer? And the answer here is a pointer to the struct. 

So here, we're seeing that this is a node pointer. And a node, technically, is a structure. So we're going to have a pointer to that node that is itself a structure combined with a phrase and another pointer to another node. So good questions there. 

All right. Any other questions on this structure here? OK. So that all seems pretty good so far, and kind of a simple template for a node. But keep in mind that just this code doesn't actually create the node for us. It gives us a template for the node, but we haven't actually created it in code yet. 

So let's actually go ahead and see how we might do that. If you were to go ahead and create our own linked list, let's say. Like, let's say, out of all these three structures, we chose a linked list now. We could start by making a single node and have that be at the head of our linked list. 

So to create a linked list, we'll often do this. We'll often create a new pointer to a node and first set it equal to null because it's pointing to nothing. There are no nodes in our linked list. 

But once we've done that, well, we probably want to add at least one node, right? So let's go ahead and do that. Let's make a new pointer, this one called n, and make sure we have some space in which to store it. So let's read this from right to left. 

Let's call malloc first. And malloc will give us some space in memory to actually put this node. So you can see at the visual right below we have some new space our program could use to actually store this node inside of and add a phrase, or some next pointer, right? 

But now if we go all the way to the left, we're going to see this pointer called n will then point to that space. And notice how n is a type node star. It's pointing to some space for a node, right? OK. So that makes our first node. 

But what we probably want to do is actually add some data to it. Currently, it's empty, right? So what can we do? 

Well, we can actually use this new syntax, this arrow syntax, to actually add in some data. So down below, we could say, n arrow phrase gets the value high. And what does that mean? 

So if you look at our visual here, we could see-- OK, we see n, and we see an arrow. And now, we're going to go to the phrase portion of this new piece of memory we've allocated and make sure we put the phrase Hi in there. So n arrow phrase is saying, start with that pointer and follow it to the structure that you have, go to that phrase attribute, that phrase portion, and make sure that says Hi in the middle, right? 

And that's all fine and good, but now, we also have to include the next portion. Like, currently it's empty, but we want to have some value. And if this is our first node, what's the logical value for this next attribute for our node? This is our very first node. What could we set it to? 

All right. So I'm seeing null in the chat. And the correct version is the N-U-L-L, not N-U-L. N-U-L is nul, and the concept of character is like a nul character. But N-U-L-L is null in the context of an address. So this is an empty address, zero address here. 

So if we say n arrow next gets the value null, we'd see something like this. Here, we have our new node n, it's phrase is Hi, its next pointer is null. It's the very first node in our list. 

So any questions on this so far, actually, making up our first node? To your question on the arrow syntax, so again, the arrow syntax is kind of best visualized by actually reading from left to right. So if we look at the very first thing, we see n. OK. n is a pointer. 

Now, the arrow says, let's follow that pointer to our structure, right, because n is pointing to a structure. And let's go to the next field, that next attribute, and set it equal to some value we put on the right-hand side. So here we said, start with n, follow n's pointer to our node structure, and go to that next attribute and set that equal to null, as we see down below here. 

OK. So there's one more step, though, which is our list is still looking pretty empty. We have our node, but our list is still empty over here. So what could we do to actually add this node to our linked list? 

What kind of code do we need here, or where do we want list to point now? Feel free to type in the chat if you think you might have it. So I'm seeing two competing opinions here. 

So one opinion is that we should say list equals n, which would be list gets the value n. And I'm seeing n equals list, or n gets the value list. Which one do we think might work here? 

Let's try one. So let's say, first, that list would get the value n. So list equals n, and let's try that. So here we have that up here and let's execute it. 

And now we'll see, OK, we'll list an n point to the same thing. Because n is a pointer and list is a pointer. If we set list equal to n, though, both point to the very same thing, which is our very first node. What would happen if we did it the other way around? If we said n equals list, instead of list equals n, where would n point to? 

Any ideas in the chat? So I'm seeing null, right? If list is currently null, it's pointing to really nothing in general, well, if we say n equals list, we're going to make sure that end points to null and we'll have lost this node over here that we just had, right? So we probably don't want to do that. 

So this will be our last step in adding our node. And now we have our very first node inside of our linked list, which is great. Questions on this here, too, before we keep going? 

OK. Not seeing too many here, so why don't we keep on going. And if we want to kick off the very first node, this is how we would do it. But let's say we wanted to actually keep adding more and more nodes. 

We could start thinking about inserting nodes to our linked list. And there are a few ways we could do even that. So if we think back to our picture as it is right now, let's say we wanted to create this new space for a node. 

We could say, OK, I'm going to have this new node called n, and I'm going to use malloc to give me some space for it. So same thing we did before. We're going to say, get some space, make sure n points to it. And now, how could we best actually add this node to our list? Would we add it at the end maybe, or the beginning, which do you think? 

Could we add n at the beginning or the end, and which would be faster? So I'm seeing some competing opinions. I'm seeing end and I'm seeing beginning. 

Now, if you think about a longer linked list, let's say we had not one node but really like 50 nodes. Would we want to add it at the end? And if so, how many steps would it take to add this node at the end of that linked list? 

If we have 50 nodes, how many steps would it take to add this node at the end? It would take 50, right? And that reason is that you have to actually find the last node and then add it there. So to find that last node, we have to go through all 50 of our nodes. 

So if we want the very quick insertion we talked about before, we have to add a node at the beginning, right, make sure that this new node points to the current first node in our list. So let's actually do that here. We have some space for a node, we have a pointer to that node. But let's see how we might add it in. 

So we probably first give this node a phrase, like, Hey. We'll say, OK, n arrow phrase gets the value Hey. And now, we want to say, hum, where should we point n's next pointer to? If we look at this picture here, where should we point n's next pointer? In the chat, if you will. 

Yeah, to list. So we want to make sure that this new node called n points to the very first node in our list, that being called, well, just list. So here we'll say, OK, n arrow next gets the value list. So now we're saying that n is a node, it has the phrase, Hey, and its next arrow is pointing to this list node, the very head of our list here. 

All right. But now, you'll notice that our linked list is not quite in the state we want it to be in, like, list is still pointing to our second node. So what's the next step here, if you want to make sure our list now includes this very first node? What should we do? 

We should point list to n, as I'm seeing in the chat. So let's make sure we have list pointing to n now. So we'll do this. 

We'll say, list equals n, and we'll run this and we'll see, OK, list gets the value n, meaning list now points to this new first node. And now we have our own linked list of more than one node, right? We went from one to two. And now, I could even do the same thing, three, or four, or five, even 500 times, if we wanted to. 

So questions on this, inserting this new node here? OK. So not seeing too many here. Let's actually try to translate this bit to code. 

So this is all fine and good with our visual, but let's actually try it out in code. I'll go over to my Visual Studio code over here. And here, I have my terminal, a file already called list.c. So I'll code up list.c. 

And if we take a look at this file, what we'll see is a very basic kind of linked list file. Here at the top, I have my headers. And down below, I have my structure called a node. And this is the same as we saw before, right? 

We have a new structure called a node that's going to hold a phrase, and it's going to have a pointer to the next node. And we're going to call all of this node throughout our code using this typedef syntax up here. Now, down below, we have some functions to actually implement. 

One is called unload, that we'll see in a bit, to actually make sure we're not using too much memory, we're actually freeing it as we go. And the other down here in main is actually add items or add phrases to our linked list. And as we do, we have this function down here called visualize that I wrote myself and should actually help you see what's happening inside of our link list. Don't worry about all this kind of scary syntax down here. We'll see what happens as we add nodes to our linked list. 

So currently, if we wanted to add some phrases to our linked list, well, we could just kind of run this program and see what happens. Well, first, I could-- let me bring up my terminal here. And I could say, I want to make list like this. 

And let's go ahead and make this full screen. I'll say ./list to run it. And now, what phrase should we add? Maybe we add Hi, exclamation point. So I'll hit Enter. 

And it doesn't show anything, right? Nothing's here yet. What if I did Hello! I could say Hello! And nothing's there. OK. But why is nothing there yet? In the chat, why is nothing here? 

Yeah, we didn't add anything. So if you go back to our program here, we still have a to do, to add phrases to a new node in this list. So here, if we look back, very familiar syntax, we're creating our very first linked list. And initially, this list is null. There's nothing in it. So that's why, when we ran this program before, we didn't see anything inside of our linked list. 

But now, what we're going to do is iterate list size times to ask the user for some phrase and add it to our linked list and visualize that addition. So how big is list size? Well, list size is 2. We'll iterate two times. And each time, we'll go ahead and add some new phrase, right? 

So let's think first-- how are we going to make this new node? We first probably want to actually create some space for it. So how could we do that here? 

We're trying to add a new node now. So we're going to need malloc, OK. So we're going to need malloc in some form. And how much space should we ask for, do we know? 

So we want to create some space for a node. And maybe a node is-- I don't know-- I could guess and say it's five bytes. But is that right? Or maybe it's 10. I mean, I don't know. It could be anything. 

We don't really quite know, and so that's why we want to use this function called sizeof. And we can pass sizeof a certain type, like, node, right? I don't know how big a node is, but sizeof does. It'll tell malloc how much memory to create to have this node in place. 

But now that I've asked for memory, I should probably keep track where that memory is. So I need some variable to store that location memory, which might be called what? What could we store here? 

Maybe we could have a node pointer. Let's call it n. So we could say, OK, this is going to point to some variable-- point to some new piece of memory called n. And we're going to make sure it points to a node, right? 

This is going to be some new chunk of memory where n points to. All right. So we do that kind of first bit, and now we have some space for our node. But what do we need now? We need to make sure that we add in a phrase. So how can we do that? 

We would probably use our arrow syntax like we saw before. So we could say, n arrow phrase. And let's store the phrase that we have right now inside. And similarly for the next portion, we could do this. We could say n arrow next gets the value. But what should it get, if this is our maybe first node? 

I'm seeing a few different ideas here. So I'm seeing one for null. Let's try that. So we'll say, OK, n arrow next is null. It's our first node. 

And now what we want to do is make sure that list points to that very first node we just made up above. So let's try it. Let's go ahead and compile this. 

We'll open up our terminal again. We'll say, make list and-- oops-- we forgot our semicolon, so we'll do that. And we'll go back here and we'll say, make list. And then we'll do ./list. And I'll say, OK, my first phrase is Hi! 

And that seems all right, like, I have this new node at this location. It's phrase is Hi! And its next pointer is null. That seems OK. What if I did this? What if I said Hello! now. 

And I'm seeming to actually be missing my very first node. It kind of went away. What happened here? Any ideas in the chat? 

Yeah. So I'm seeing we didn't quite add this node. Because if we take a look at our code, we're always setting the next pointer for our new node to be null, and that means nothing. So whenever we add a new node, well, we're just going to make sure that the next pointer is null, like, it doesn't point to anything? That isn't quite right. 

So let's make sure we actually update this to point to the head of our list. Our first node should point to whatever is the first element in our list. So let's say this, n arrow next gets the value list. And how will this work at the beginning? 

So notice how list is null at the beginning. Then we'll go through and add our first node. We'll say, OK, let's get a phrase, and let's make sure we have some space for this new node called n. Let's make sure this n has the phrase that we've been typing in. 

And now, n arrow next is equal to list which, in fact, is null, right? So our very first node will still have null as its sort of beginning next pointer. And then we'll go ahead and make sure list is updated to have the very first node at the head. 

But then if we do it again, if we go through again, we'll say that, OK, this list pointer's next is actually pointing to the previous node we just created. So now I can actually have the string together as we go through. And let's visualize this now. So let's go back to our terminal. 

Let's say, make list, and let's do ./list. And we could say Hi! And then we could say Hello! And now we see our list being built. So notice how our very first node here is at this location. It has the phrase Hello! 

And the next pointer is this, it's pointing to some new location here. But notice how this is now in our next node, 56f0. And the phrase here is Hi! And the next pointer is null here. 

OK. So that seemed to work for us. Let's go back to our code. What questions are there on this? 

A good question. So is this some kind of recursion? This isn't quite recursion because, again, recursion involves having a function call itself. And here, we're really inside of a loop. So it isn't quite recursion. 

But you're onto an idea, which is that every node that we add is going through that same process. So this really could potentially be a recursive function, if you wanted it to be. But here, you're just noticing that the same thing we're doing for one node, we're doing for another, as we add it, as we go through. 

And that's a good question, too. Is the last node we add becoming the first? That is also true. So here if we were to say, Hi! And then Hello! Well, Hello! becomes our new first node, right? That's because we're trying to insert new nodes at the front where the first node we add becomes the first-- sorry-- the last node we add becomes the first node in our list, ultimately. 

OK. So there is one final thing to do here, which is to make sure that if we're asking for memory, we do want to make sure that this memory is actually given to us. And before we go ahead and use this pointer called n, we do want to make sure that we're not getting back some null value. So if n is null, what we want to do is simply print something like couldn't allocate memory for node, or whatever you want to type here, some descriptive error. And then we could return 1 to symbolize that something went wrong here. 

OK. A question then, is this a stack? Well, it has the beginnings of a stack where if you remember, a stack is this data structure where the first thing we add becomes the last thing we get out. Or otherwise, the last thing we add is the first thing we get out, which is the case here. So we're saying that the last node, the last phrase we add, is going to be the first node we see in our structure. 

But it also depends on how we access this linked list. If we always access it from the very first node, well, that could be kind of similar to a stack. But if we always want to access it by looking at the very last element first, well, that could be then a queue, right? So a queue in a stack kind of depends on how you actually use them, and not so much what you build kind of underneath the hood. 

All right. So let's keep going here. And I would say that this code is mostly correct. But if I go down to my terminal and I now do this, I do make list again just to compile it. And then I say, let's try to memory check this and see if there are any memory errors. Well, I could do valgrind./list. And let me type in, let's say, once it loads, I can type in Hi! Right? 

And now that seems OK. I can type in Hello! And my program ends, but it seems I've definitely lost some bytes. I've definitely lost 16 bytes. And I've indirectly lost 16 bytes. So what happened here? What did I fail to do in my code? 

Yeah, I didn't free the memory. So if I look back at my program, if I do this and I say, OK, well, unload. I trust that unload will work for me, right? But if I actually look down here, it's still a to do. I didn't actually free any nodes here. 

And if I look above, well, I used malloc several times. I used it twice. And I didn't call free any of those times. So every time we call malloc, we want to make sure we call free, and that's what unload is going to do for us down below. We're making our own function that takes in some pointer to a list and should go through and free every node in that list. We can give back that memory to the computer. 

So let's visualize, if we're actually writing it in code. If we go back to our slides here, we could think about actually trying to free this linked list. And maybe your initial thought is, let's do this. Let's actually just free the list. Let's say this. 

But why would this be bad? If we say free the list, what goes wrong? Here's the original picture. Here's freeing the list. What happened here? 

Yes, I'm saying we lost the other nodes. So notice how in this picture, if you go back, well, the very first node is still pointing to that next node. And the only reason we know where that next node is located is because it's in the next portion of our very first node. 

But if we free that, if we get rid of it, well, where is that second node? We don't know. So if that's going to be a problem for us, what we don't want to actually just free the head of the list, we want to make sure we're going through and freeing nodes step by step and keeping track of where the rest of our nodes are. 

So instead, one way we could approach this is as follows. We don't want to do this, just free the head of the list. What we could do, instead, is say, let's make a new pointer, let's add that to the equation. Let's do this. 

So let's say that-- let's make a new pointer, just called maybe ptr, for example. And that will point to whatever the head of our list is, the next node. So now, a pointer is pointing to that second node in our list. And now, we could safely free list. We could do this. 

We could say, OK, free up list, and that's gone. But what is still pointing to the rest of our list now, which variable? Maybe in the chat? 

Yeah. So ptr is pointing to that second node in our list. So we still have this in our memory. We know where all the rest of our nodes are. 

OK. So that's all good. But now, we want to actually get back to the head of our list and make sure that we're actually kind of moving forward. So what we'll do is say that list gets the value for ptr. So we're going to update what our list looks like and say that we're going to move this over here. 

So now, the head of our list points to whatever pointer points to. And we could, perhaps, do this in a loop. We could say, OK, in this case, well, pointer will get list arrow next again. And what would pointer be now, though? 

If pointer is list arrow next, what is pointer going to be? It will be the second node of the node after the first one. But what's the actual value right now? 

Yeah. It'll be null, or [INAUDIBLE] because notice how right now list is pointing to this very, now, the first node in our list, whose next value is null. So if pointer equals list arrow next, well, pointer will be null. OK, that seems OK for now. 

But if we wanted to kind of keep going, let's say we free list, all right. And then we say, well, list gets pointer. What is list now? There's nothing left, so list would also be null, right? 

So what we've done, we've kind of gone full circle. We've made-- we've gone from the very first node to our very last node, and we've ended when list equals null, when there's nothing left to free, back at, for example, the same place we started. If we go back to our code, we could see that the very place we began was with list equaling no, no nodes in our list. And now, if we unload them, we also want to end in that very same place, right? 

OK. So let's try implementing this in code now so we can get rid of those memory errors. If we go down below here, we're going to free all of our allocated nodes. And we know we want some kind of loop to do this. But let's hold off on that for now. 

We know, first, we want to make this new pointer to our next nodes. We can do this. Node star pointer equals whatever list is pointing to and getting that next value there. 

Then we could safely free list because pointers pointing the rest of our list. And, finally, we could say, list updates to 0.2, what pointer is now pointing to. But how long do we want to do this? How do we know when to stop? 

Maybe in the chat? This seems good for one node, but want to keep doing this. Yeah, we want to keep doing it until our list is null. And we don't really know how many times we want to iterate, so a while loop seems like a good choice. A while loop we can do something until something else is true. 

So we could say, while list doesn't equal null. While we still have nodes, essentially, let's go ahead and make sure that we have a pointer to the next node. Let's free the current node, and then let's update the current node to point to whatever it was previously, the next one. 

So we could do something like this. And now, if we run our code, if we go back to our terminal here, we'll make list. We'll run valgrind on ./list. And what do we get if we type in, let's say, Hi! here, and then Hello? 

We see, successfully, all heap blocks were freed. No leaks are possible down below here. So what questions are there on this, if you look at our code for unloading here? 

Yeah, a good question, is nil the same as no? So if we look at our terminal and we actually run this again, call it a make list, I'll run ./list, and I'll say Hi! And notice how this very first node has the next pointer of nil. Nil is simply the terminal representation of null. So nil means null in the terminal. 

All right. And now, I'm seeing another question, is this a recursive function? So this still is probably not a recursive function, because a recursive function would kind of call itself like this function might then call unload somewhere in here. So it's not quite recursive, but you are correct in noticing that this is a good application for recursion because we're doing the very same thing for every node as we go. So you could certainly write this recursively. Here, we're going to iteratively using a loop. 

OK. Other questions on this? 

OK. So let's keep going on. And we've seen linked lists now. We've seen these really two core operations for linked lists, like, how do we add some data to them, and how do we unload them? What you might ask, though, is how can we speed this up? And that's where hash tables come in. 

So hash tables are simply an array of linked lists. We take linked lists, we break them into smaller pieces. And so let's get a visual for that and see if we can make this run even faster. 

So if we go back to our slides here and we see this idea of a linked list, we have maybe, Hey! Hello! Lo there! Different kind of activation words for our voice assistant. Well, what we could do is try to make sure we can access certain parts of this linked list faster to make sure we can actually search this linked list faster. And we could for that use a hash table. 

So recall from earlier that a hash table looks a bit like this. We have some array on the left-hand side. And we have different, what we call, buckets in here, where a bucket might, in this case, be a letter of the alphabet. And that letter of the alphabet is maybe the first character in a word. 

You could have other buckets, other ways of assigning these phrases to buckets. But for now, let's focus on this alphabetical hash function here and alphabetical hash table. So with this, we have different letters for every hash bucket. 

And how does C know where in the array H, I, J, K and L are? If we wanted to add some nodes to a certain bucket, well, how do we figure out where that bucket is? Anyone in the chat want to chime in on that? 

Yes. So it seems to be that they're ordered. They're certainly in the right alphabetical order. That's helpful. Other things, too, for how we know where H is located, or L is located? 

Yes, we could use maybe ASCII numbers and so on. And we're on the right track here. But because if you look at the left-hand side, this is just an array, and we've kind of ourselves as humans assigned those array buckets, those array segments, some letter. But we have to assign them some number, really, some index. 

And so you might recall from very early on, all arrays have these indices, right? So maybe zero to however big your array is. And now we have, in this case, maybe H corresponds to the 7 index in our table, or I corresponds to the 8 index, and so on. 

And so in those indexes, we can actually add in our linked list. And so here, if we notice that H corresponds to 7, well, H is the eighth letter of the alphabet. But if we were counting from zero, it would be the seventh. So in this case, H corresponds to zero as that seventh letter of the alphabet counting from zero here. 

That's how we know how we actually add in these linked list nodes. Now, if I were to give you some new phrase, not Hey! or Hello! or Lo there! How would you figure out where to put it in this case? Maybe in the chat? If I gave you some new phrase, what could you do to figure out where to put it? 

Yeah. So I'm seeing maybe at the start. I don't really know until we see the phrase, right? And that's where this idea of a hash function comes in. 

So in order to figure out where Hey! and Hello! and Lo there! go, we need to have some kind of function that takes our phrase and gives us back some number that tells us where to put it. So here we have, maybe, the phrase Hey! And our hash function should ideally give us some number that tells us where to put that given phrase. 

So if I gave you not Hey! or Hi! or Hello there, maybe I gave you the name Carter. Well, that should give us some new number that then corresponds to an index in our array, or we could start this new linked list that might have all the C words, for example. So let's actually take a look at this kind of in code now. 

If we go back to our Visual Studio code over here, I'll open up this new file, this one called table. So I'll code table.c. And it's already a bit done for me. But notice how we have a few different things. 

We have the same node structure from before for making our linked lists. And now, we have this new array of pointers to node. And we're calling this a table. And notice how we have 26 buckets, 26 places in which to have a linked list now. And we can figure out where these new phrases should go by running this function called hash that we'll see down below. 

So let's scroll down. We see that, here, we have this function called hash. And hash is right now just returning zero. Because if I give it a new phrase, I haven't really finished this yet. I just want to return zero for every phrase I get. 

And ideally, if I run this program, I should type in a phrase and see the index that I should place this phrase inside of my hash table, and then print out, OK, this phrase hash is to whatever number I have. So let's see an example. So if I go to my terminal now, I could make this full screen and I could simply type, make a table. 

And now, I'll run ./table, and I'll type in Hi! And I get zero, which is maybe OK. But let's try now-- let's try Lo there! as we saw before, and we get zero. So why would this be bad? Besides it being unfinished, why would we not want Hi! and Lo there! to kind of hash to that same value? 

Any ideas in the chat? Yeah. So I'm seeing that this is kind of similar to a linked list, if we were to do this. Like, if we have-- back to our visual here. If we have some array of linked lists, but every word hashes to zero, well, we have all this other space to put our linked lists, but we're just putting everything in the zero bucket, which it makes-- turns us back into this picture, which is just a single linked list, right? 

The goal of this hash function is to have many shorter linked lists, and that's the goal of trying to put things in different buckets, different indexes here. So ideally, we don't want to have everything hash to the same value, we want to have different hash values for different phrases that we might input. So one way to do this, as we're seeing right now, is trying to make sure we have different linked lists that depend on the very first letter of the phrase we add. 

And let's go back to our hash function and figure out how we could do that. So let's exit our program here. And let's go ahead and go back here. 

And let's try to implement hash so that we get a value 0-25 for a given phrase. So here, let's try this. Let's actually try returning not just zero, but let's say, depending on the very first letter of our phrase, we return that and see how that goes. 

So here we have returning phrase, bracket zero. And we'll go back to our terminal now. We'll say make table, and then ./table, and let's try Hello! And we see 72. 

Is that-- I mean, it's better. Right now, I have actual number. And if I type in Carter, well, that's a different number, which is good. And Lo there! perhaps, is also a different number. So we're off to a good start. 

But what's wrong with this? If I get 72, and 67, and 76, I go back to my code and I look at my table, what's wrong? Yeah. So I'm seeing I only have 26 buckets. 

So if I wanted to, let's say, get a phrase and put it in my bucket somewhere, well, I can't really do that because maybe Hello! hashes to, what was it if we look at it? 72. Well, that's not a valid index in my table. So I need to actually make this shorter a little bit. 

And one way to do that is maybe just subtract A from it. So I could do something like this. And what this will do is, maybe if you recall how A maps to 65, well, if I get A as the very first character, well, what is 65? A minus A is zero. 

If I get B, B is 66 in ASCII. So B minus A is 1. And if I get all the way down to Z, well, Z minus a is going to be 25. And if I wrap back around to A, well, that's just zero again. 

So what I've done now is I've made sure that every index I get is going to be inside the kind of length of my table here. I won't get any indexes that are out of bounds for this list. And now, if I kind of go back here, we run this code, I'll do make table. 

I'll run ./table, and I'll do Hello! now, and I get 7, which is better. Now, I'll do maybe Lo there! and I get 11. And now, I'll type in just Z to see how that works, and I get 25. 

So that seems to be pretty good for myself. But what still am I missing here? What could go wrong? Any ideas? 

Yes. So lowercased letters-- right now, I'm working with phrases that are all capital. But let's say someone wants to add a phrase that is in lowercase. So I could actually open a terminal again, make table. 

I'll do ./table, and I'll do maybe hello! in lowercase. And I get 39, which isn't quite what I want. So what could I do instead? Maybe any ideas in the chat? What can I do instead? 

I could, perhaps, maybe standardize on capital letters. So I could say, I want to make whatever this first letter is uppercase, and then subtract that capital A. So if I go back to my terminal, I could say, make table. 

I could say ./table. And now I want for it to be the case that lowercase hello and capital Hello! hash that same value. So I'll type hello here, and capital H Hello! here, and I get 7 in both cases. So that seems to work for me now. 

All right. Any other-- if we go back to our terminal here, that will tell us where to put individual phrases. So questions on this hash function so far? 

All right. So not seeing too many questions here. Why don't we do this? 

So let's go ahead and think about what makes for a good hash function? So if we think about this as our very first hash function, this idea of putting nodes into individual buckets, well, it's not going to be quite what we want it to be. And if we actually go through down here and we think about how could we try to make sure we actually better hash function than this, what we could do is actually make sure we have a good distribution of values across it. 

So if you think about our buckets here, we want to try to have-- to make sure that every node in our linked list is kind of going to go in every bucket here. Like, we actually have a lot of I words, a lot of J words, a lot of K words. And here, the way we hash this isn't going to quite do that for us. 

We're not going to actually have any words that start with I, or J, or K, so we probably think of a new hash function to use in this case. And if we go back over here, we can think of some good points for our hash function. We can think of, OK, we always try to get the same value for a given input. 

We always want to produce an even distribution across the buckets, and we always want to make sure that we use all the buckets that we're given in this case. So these are some ideas for a good hash function. Here, what we'll actually do is let you all go off and write your own hash functions to go off and build your own overall. 

So if we think of some other ideas here, you could use the length of the phrases, you could make sure you maybe add up their values, and so on. But what we could do is go ahead and have you all do that for the rest of this week now. And I think that will probably conclude us for this section. 

It is so good to see you all here today. Thank you all for joining us. We will see you next week.
