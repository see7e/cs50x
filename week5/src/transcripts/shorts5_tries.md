---
title: SHORTS5 - TRIES - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DOUG LLOYD: So we've been inching closer and closer that holy grail of data structures, one that we can insert into, delete from, and look up in constant time. Right. That's sort of the goal. We want to be able to do things very, very quickly. 

Have we found it here when we're talking about tries? Well, let's take a look. So we've seen several different data structures that handle the mapping of so-called key-value pairs, mapping some piece of data to some other piece of data so we know where to find information in the structure. 

So for array, for example, the key is the element index or array location 0 or array 1 and so on. And the value is the data that exists at that location. So what is stored in array 0? What is stored in array 1 versus just 0 and 1, which would be the keys. 

With a hash table it's sort of the same idea. With a hash table, we have this hash function that generates hash codes. So the key is the hash code of the data. And the value, particularly we talked about chaining in the video on hash tables, is that linked list of data that hashes to that hashcode. Right. What about another approach this method, though? What about a method where the key is guaranteed to be unique, unlike a hash table, where we could end up with two pieces of data having the same hashcode. And then we have to deal with that by either probing or more preferably chaining to fix that problem. 

So now we can guarantee that our key will be unique. And what if our value was just something as easy as true and false that tells us whether or not that piece of information exists in the structure? A Boolean could be as simple as a bit. Realistically it's probably a byte more likely than a bit. But that's a lot smaller than storing maybe a 50-character string, for example. 

So tries, similar to hash tables, which combine arrays and linked list, tries combine arrays, structures, and pointers together to store data in an interesting way that's pretty different from anything we've seen so far. Now we use the data as a roadmap to navigate this data structure. And if we can follow the roadmap, if we can follow the data from beginning to end, we'll know whether that data exist in the trie. 

And if we can't follow the map from meaning to end at all, the data can't exist. Again, the keys here are guaranteed to be unique. And so unlike a hash table, we'll never have to deal with collisions here. And no two pieces of data have exactly the same roadmap unless that data is identical. 

If we insert John, then we search for John. That's two identical pieces of data, right, we're looking through. But otherwise, any two pieces of data are guaranteed to have unique roadmaps through this data structure. And we're going to take a look at a visual of this in just a moment. 

We'll do this by trying to create a new data structure, mapping the following key value pairs. In this case, we're not going to use something as simple as a Boolean. We actually will store the string. And that string is going to be the name of a university. 

And the key is going to be the year when that university was founded. All years for universities are going to be four digits. And so we'll use those four digits to navigate through this data structure. And we'll see, again, how we do that in just a second. 

At the end of the path, we'll see the name of the university that corresponds to that key, those four digits. The basic idea behind a trie is we have a central route. So think about it like a tree. And this is similar in spelling and in concept to a tree. Generally when we think about trees in the real world, they have a root that's in the ground and they grow upward and they have branches and they have leaves. And basically the idea of a trie is exactly the same, except that root is anchored somewhere in the sky. And the leaves are at the bottom. 

So it's kind of like taking a tree and just flipping it upside down. But there are still branches. And those would be our pathways, those will be our connections from the root to the leaves. In this case, those paths, those branches are labeled with digits that tell us which way to go from where we are. 

If we see a 0, we go down this branch, if we see a 1, we go down this branch, and so and so on. Well, what does this mean? Well, that means that at every junction point and every node in the middle and every branch, there are 10 possible places that we can go. So there are 10 pointers from every location. 

And this is where tries can get a little bit intimidating for somebody who's doesn't have a lot of experience in computer science before. But tries are really pretty awesome. And if you have the chance to work with them and you're willing to dig-in and experiment with them, they're really quite interesting data structures to work with. If we want to insert an element into the trie, all we need to do is build the correct path from the root to the leaf. Here's what every step along the way might look like. We're going to define a new data structure for a new node called a trie. 

And inside of that data structure there are two pieces. We're going to store the name of a university. And we're going to store an array of pointers to other nodes of the same type. So, again, this is that sort of concept of everywhere we are, we at 10 possible places we can go. If we see a 0, we go down this branch. If we see a 1, this branch, and so on and so on and so on. If we say 9, we go down this branch. So at every junction point, we can go 10 possible places. So every node has to contain 10 pointers to other nodes, to 10 other nodes. 

And the data we're storing is just the name of the university. So let's build a trie. Let's insert a couple of items into our trie. So at the very top, this is our root node. This is probably going to be something you're going to globally declare. And you're going to globally maintain a pointer to this node always. 

You're going to say, root equals, and you're going to malloc yourself trie node. And you're never going to touch root again. Every time you want to start navigating through, you set another pointer equal to root, such as trav, which is the example I use in many of my videos here on stacks and queues and link lists and so on. 

You set another pointer called trav for traversal. And you use trav to navigate through the data structure. So let's see how this might look. So right now, what does a node look like? Well, just as our data structure declaration indicated, we have a string, which in this case is empty. There's nothing here. 

And an array of 10 pointers. And right now, we only have 1 node in this trie. There's nothing else in it. So all 10 of those pointers point to null. That's what the red indicates. 

Let's insert the string Harvard. Let's insert the University of Harvard into this trie, which was founded in the year 1636. We want to use the key, 1636, to tell us where we're going to store Harvard in the trie. Now, how might we do that? 

It might look something like this. We start at the root. And we have these 10 places we can go. The root is just like any other node of the trie. There are 10 places we can go from here. 

Where do we probably want to go if the key is 1636? There's really two options. Right. We can build the key from right to left and start with 6. Or we could build the key from left to right and start with 1. 

It's probably more intuitive as a human being to understand we'll just go left to right. And so if I want to insert Harvard into this trie, I probably want to start by starting at the root, looking at my 10 options in front of me, and saying I want to go down the 1 path. OK. 

Now, 1 path is currently null. So if I want to proceed down that path to insert this element into the trie, I have to malloc a new node, have 1 point there, and then I'm good to go. 

So I basically am at a point where I'm standing at the root of the tree or the trie and there are 10 branches. But each branch has a gate in front of it. Right. Because there's nothing else there's. No safe passage. That means that there's nothing down any of those branches. If I want to start building something, I want to remove the gate. I want to remove the gate in front of number 1. And I want to walk down that. And I want to build another place for me to go. 

And that's what I've done here. So 1 no longer points to null. I've said it's safe to go down here now. I built another node. And when I get to that node, I have another decision to make. Where am I going to go from here? 

Well, I've already gone down the 1. So now I probably want to go down the 6. Right. Again, I have 10 locations I can choose. So let's now go down number 6. So I clear the gate in front of number 6. And I walk down there. And I build another node. And I've reached another junction point. 

Again, I have 10 choices for where I can go. I've moved from 1 to 6. So now I probably want to go to 3. 3, there's nowhere I can go. So I have to clear the way and build myself a new space. And then from 3, where do I want to go? I want to go down 6. 

And, again, I had to clear the way to do it. So now I've used my key to insert create nodes and start to build this trie. I've started at the root. I've gone down 1636. And now I'm at the bottom there on that node. And you might be able to see it on your screen. 

It's highlighted in yellow. That's where I currently am. My key is done. I've exhausted every position in my key. So I can't go any further. So at this point, all I really need to do is say, OK. It's kind of like looking down at the ground, if you're envisioning yourself as this sort of path with different connections. Sort of looking down and sort of spray painting Harvard on the ground. That's the name of this. Know that's what's at this location. If we start at the root and we go down 1 and then 6 and then 3 and then 6, where are we? Well if we look down and we see Harvard, then we know that Harvard was founded in 1636 based on the way we're implementing this data structure. So that was hopefully straightforward. We're going to do two more insertions. And hopefully it'll help to see this done twice more. 

Now, let's insert another university. Let's insert Yale into this trie. Yale was founded in 1701. So we'll start at the root, as we always do. And we set a traversal pointer. We're going to use that to move through. The first thing we want to do is go down the 1 path. That's the first digit of our key. Fortunately, though, we don't have to do any work this time. The 1 path has already been cleared. I cleared it previously when I was inserting Harvard at 1636. So I can safely move down 1 and just go there. If can move down the 1. 

Now, though, I want to go to 7. I cleared the way at 6. I know I can safely proceed down the 6 path. But I need to proceed on the 7 path. So what do I need to do? Well, just like before, I just need to clear the gate, get out of the way, and build a new node from the 7 path. Just like this. 

So now I've moved 1 and then 7. And now notice, I'm sort of on this new subbranch. Right. Everything else from 16 on, I don't care about. I'm not doing 16 anything. I'm doing 17 stuff. 

So now from 17 on, I have to sort of blaze new trails here. The next digit my key is 0. I clearly can't get anywhere. I just built this node. So I know there's no paths forward from here. So I have to make one myself. 

So I malloc a new node and have 0 point there. And then one more time, I malloc a new node and have one point there. Again, I've exhausted my key, 1701. So I look down and I spray paint Yale. That's the name of this node. 

And so now if I ever need to see if Yale is in this trie, I start at the root, I go down 1701, and look down. And if I see Yale spray painted onto the ground, then I know Yale exists in this trie. Let's do one more. Let's insert Dartmouth into this trie, which was founded in 1769. 

Start at the root again. My first digit of my key is 1. I can safely move down that path. That already exists. The next digit of my key is 7. I can safely move down that path. It exists as well. 

My next is 6. From here, from where I currently am in yellow there in that middle node, 6 is currently locked off. If I want to go down that path, I have to build it myself. So I'll malloc a new node and have 6 point there. And then, again, I'm blazing new trails here. 

So I malloc a new node so that from that node-- path number 9-- and then now if I travel 1769, and I look down. There's nothing currently spray painted there. I can write Dartmouth. And I've inserted Dartmouth into the trie. 

So that's inserting things into the trie. Now we want to search for things. How do we search for things in the trie? Well, it's pretty much the same idea. Now we just use the digits of the key to see if we can navigate from the root to where we want to go in the trie. 

If we hit a dead end at any point, then we know that that element can't exists or else that path would have already been cleared. If we make it all the way to the end, all we need to do is look down and see if that's the element we're looking for. If it is, success. If it's not, fail. 

So let's search for Harvard in this trie. We start at the root. And, again, we're going to create a traversal pointer to do our moves for us. From the root we know that the first place we need to go is 1, can we do that? Yes, we can. If safely exists. We can go there. 

Now, the next place we need to go is 6. Does the 6 path exist from here? Yeah, it does. We can go down the 6 path. And we end up here. 

Can we go down the 3 path from here? Well, as it turns out, yes, that exists too. And can we get on the 6 path from here? Yes, we can. 

We haven't quite answered the question yet. There's still one more step, which is now we need to look down and see if that's actually-- if we're looking for Harvard, is that what we find after we exhaust the key? In the example we're using here, the years are always four digits. But you might be using the example where you are storing a dictionary of words. 

And so instead of having 10 pointers for my location, you might have 26. One for each letter of the alphabet. And there are some words like bat, which is a subset of batch, for example. And so even if you get to the end of the key and you look down, you might not see what you're looking for. 

So you always have to traverse the entire path and then if you were successfully able to traverse the entire path, look down and do one final confirmation. Is that what I'm looking for? Well, I look down after starting at the top and going 1636. I look down. I see Harvard. So, yes, I succeeded. What if what I'm looking for isn't in the trie, though. What if I'm looking for Princeton, which was founded in 1746. And so 1746 becomes my key to navigate through the trie. Well, I start at the root. And the first place I want to goes down the 1 path. Can I do it? Yes, I can. 

Can I go down the 7 path from there? Yeah, I can. That exists too. But can I go down the 4 path from here? That's like asking the question, can I proceed down that little square that I've highlighted in yellow? There's nothing there. Right. 

There's no way forward down the 4 path. If Princeton was in this trie, that 4 would have been cleared for us already. And so at this point we've reached a dead end. We can't go any further. And so we can say, definitively, no. Princeton does not exist in this trie. 

So what does this all mean? Right. There's a lot going on here. There's pointers all over the place. And, as you can see just from the diagram, there's a lot of nodes that are kind of flying around. But notice every time we wanted to check whether something was in the trie, we only had to make 4 moves. 

Every time we wanted to insert something in the trie, we have to make 4 moves, possibly mallocing some stuff along the way. But as we saw when we inserted Dartmouth into the trie, sometimes some of the path might already be cleared for us. And so as our trie gets bigger and bigger, we have do less work every time to insert new things because we've already built a lot of the intermediate branches along the way. If we only ever have to look at 4 things, 4 is just a constant. We really are kind of approaching constant time insertion and constant time lookup. The tradeoff, of course, being that this trie, as you can probably tell, is huge. Each one of these nodes takes up a lot of space. 

But that's the tradeoff. If we want really quick insertion, really quick deletion, and really quick lookup, we have to have a lot of data flying around. We have to set aside a lot of space and memory for that data structure to exist. 

And so that's the tradeoff. But it looks like we might have found it. We might have found that holy grail of data structures with quick insertion, deletion, and lookup. And maybe this will be an appropriate data structure to use for whatever information we're trying to store. I'm Doug Lloyd, this is cs50. 