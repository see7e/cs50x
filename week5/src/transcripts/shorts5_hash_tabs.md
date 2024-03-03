---
title: SHORTS5 - HASH TABLES - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DOUG LLOYD: By now you know a lot about arrays, and you know a lot about linked lists. And we've discuss the pros and cons, we've discussed that linked lists can get bigger and smaller, but they take up more size. Arrays are much more straightforward to use, but they're restrictive in as much as we have to set the size of the array at the very beginning and then we're stuck with it. 

But that's, we've pretty much exhausted all of our topics about linked lists and arrays. Or have we? Maybe we can do something even more creative. And that sort of lends the idea of a hash table. 

So in a hash table we're going to try combine an array with a linked list. We're going to take the advantages of the array, like random access, being able to just go to array element 4 or array element 8 without having to iterate across. That's pretty fast, right? 

But we also want to have our data structure be able to grow and shrink. We don't need, we don't want to be restricted. And we want to be able to add and remove things very easily, which if you recall, is very complex with an array. And we can call this new thing a hash table. 

And if implemented correctly, we're sort of taking the advantages of both data structures you've already seen, arrays and linked lists. 

Well an average insertion into a hash table can start to get close to constant time. And deletion can get close to constant time. And lookup can get close to constant time. That's-- we don't have a data structure yet that can do that, and so this already sounds like a pretty great thing. We've really mitigated the disadvantages of each on its own. 

To get this performance upgrade though, we need to rethink how we add data into the structure. Specifically we want the data itself to tell us where it should go in the structure. And if we then need to see if it's in the structure, if we need to find it, we want to look at the data again and be able to effectively, using the data, randomly access it. Just by looking at the data we should have an idea of where exactly we're going to find it in the hash table. 

Now the downside of a hash table is that they're really pretty bad at ordering or sorting data. And in fact, if you start to use them to order or sort data you lose all of the advantages you previously had in terms of insertion and deletion. The time becomes closer to theta of n, and we've basically regressed into a linked list. And so we only want to use hash tables if we don't care about whether data is sorted. For the context in which you'll use them in CS50 you probably don't care that the data is sorted. 

So a hash table is a combination of two distinct pieces with which we're familiar. The first is a function, which we usually call a hash function. And that hash function is going to return some non-negative integer, which we usually call a hashcode, OK? The second piece is an array, which is capable of storing data of the type we want to place into the data structure. We'll hold off on the linked list element for now and just start with the basics of a hash table to get your head around it, and then we'll maybe blow your mind a little bit when we combine arrays and link lists together. 

The basic idea though is we take some data. We run that data through the hash function. And so the data is processed and it spits out a number, OK? And then with that number we just store the data we want to store in the array at that location. So for example we have maybe this hash table of strings. It's got 10 elements in it, so we can fit 10 strings in it. 

Let's say we want to hash John. So John as the data we want to insert into this hash table somewhere. Where do we put it? Well typically with an array so far we probably would put it in array location 0. But now we have this new hash function. 

And let's say that we run John through this hash function and it's spits out 4. Well that's where we're going to want to put John. We want to put John in array location 4, because if we hash John again-- let's say later we want to search and see if John exists in this hash table-- all we need to do is run it through the same hash function, get the number 4 out, and be able to find John immediately in our data structure. That's pretty good. 

Let's say we now do this again, we want to hash Paul. We want to add Paul into this hash table. Let's say that this time we run Paul through the hash function, the hashcode that is generated is 6. Well now we can put Paul in the array location 6. And if we need to look up whether Paul is in this hash table, all we need to do is run Paul through the hash function again and we're going to get 6 out again. 

And then we just look at array location 6. Is Paul there? If so, he's in the hash table. Is Paul not there? He's not in the hash table. It's pretty straightforward. 

Now how do you define a hash function? Well there's really no limit to the number of possible hash functions. In fact there's a number of really, really good ones on the internet. There's a number of really, really bad ones on the internet. It's also pretty easy to write a bad one. 

So what makes up a good hash function, right? Well a good hash function should use only the data being hashed, and all of the data being hashed. So we don't want to use anything-- we don't incorporate anything else other than the data. And we want to use all of the data. We don't want to just use a piece of it, we want to use all of it. A hash function should also be deterministic. What does that mean? Well it means that every time we pass the exact same piece of data into the hash function we always get the same hashcode out. If I pass John into the hash function I get out 4. I should be able to do that 10,000 times and I'll always get 4. So no random numbers effectively can be involved in our hash tables-- in our hash functions. 

A hash function should also uniformly distribute data. If every time you run data through the hash function you get the hashcode 0, that's probably not so great, right? You probably want to big a range of hash codes. Also things can be spread out throughout the table. And also it would be great if really similar data, like John and Jonathan, maybe were spread out to weigh different locations in the hash table. That would be a nice advantage. 

Here's an example of a hash function. I wrote this one up earlier. It's not a particularly good hash function for reasons that don't really bear going into right now. But do you see what's going on here? It seems like we're declaring a variable called sum and setting it equal to 0. And then apparently I'm doing something so long as strstr[j] is not equal to backslash 0. What am I doing there? 

This is basically just another way of implementing [? strl ?] and detecting when you've reached the end of the string. So I don't have to actually calculate the length of the string, I'm just using when I hit the backslash 0 character I know I've reached the end of the string. And then I'm going to keep iterating through that string, adding strstr[j] to sum, and then at the end of the day going to return sum mod HASH_MAX. 

Basically all this hash function is doing is adding up all of the ASCII values of my string, and then it's returning some hashcode modded by HASH_MAX. It's probably the size of my array, right? I don't want to be getting hash codes if my array is of size 10, I don't want to be getting out hash codes 11, 12, 13, I can't put things into those locations of the array, that would be illegal. I'd suffer a segmentation fault. 

Now here is another quick aside. Generally you're probably not going to want to write your own hash functions. It is actually a bit of an art, not a science. And there's a lot that goes into them. The internet, like I said, is full of really good hash functions, and you should use the internet to find hash functions because it's really just kind of an unnecessary waste of time to create your own. 

You can write simple ones for testing purposes. But when you actually are going to start hashing data and storing it into a hash table you're probably going to want to use some function that was generated for you, that exists on the internet. If you do just be sure to cite your sources. There's no reason to plagiarize anything here. 

The computer science community is definitely growing, and really values open source, and it's really important to cite your sources so that people can get attribution for the work that they're doing to the benefit of the community. So always be sure-- and not just for hash functions, but generally when you use code from an outside source, always cite your source. Give credit to the person who did some of the work so you don't have to. 

OK so let's revisit this hash table for a second. This is where we left off after we inserted John and Paul into this hash table. Do you see a problem here? You might see two. But in particular, do you see this possible problem? 

What if I hash Ringo, and it turns out that after processing that data through the hash function Ringo also generated the hashcode 6. I've already got data at hashcode-- array location 6. So it's probably going to be a bit of a problem for me now, right? 

We call this a collision. And the collision occurs when two pieces of data run through the same hash function yield the same hashcode. Presumably we still want to get both pieces of data into the hash table, otherwise we wouldn't be running Ringo arbitrarily through the hash function. We presumably want to get Ringo into that array. 

How do we do it though, if he and Paul both yield hashcode 6? We don't want to overwrite Paul, we want Paul to be there too. So we need to find a way to get elements into the hash table that still preserves our quick insertion and quick look up. And one way to deal with it is to do something called linear probing. 

Using this method if we have a collision, well, what do we do? Well we can't put him in array location 6, or whatever hashcode was generated, let's put him at hashcode plus 1. And if that's full let's put him in hashcode plus 2. The benefit of this being if he's not exactly where we think he is, and we have to start searching, maybe we don't have to go too far. Maybe we don't have to search all n elements of the hash table. Maybe we have to search a couple of them. 

And so we're still tending towards that average case being close to 1 vs close to n, so maybe that'll work. So let's see how this might work out in reality. And let's see if maybe we can detect the problem that might occur here. 

Let's say we hash Bart. So now we're going to run a new set of strings through the hash function, and we run Bart through the hash function, we get hashcode 6. We take a look, we see 6 is empty, so we can put Bart there. 

Now we hash Lisa and that also generates hashcode 6. Well now that we're using this linear probing method we start at 6, we see that 6 is full. We can't put Lisa in 6. So where do we go? Let's go to 7. 7's empty, so that works. So let's put Lisa there. 

Now we hash Homer and we get 7. OK well we know that 7's full now, so we can't put Homer there. So let's go to 8. Is 8 available? Yeah, and 8's close to 7, so if we have to start searching we're not going to have to go too far. And so let's put Homer at 8. 

Now we hash Maggie and returns 3, thank goodness we're able to just put Maggie there. We don't have to do any sort of probing for that. Now we hash Marge, and Marge also returns 6. 

Well 6 is full, 7 is full, 8 is full, 9, all right thank God, 9 is empty. I can put Marge at 9. Already we can see that we're starting to have this problem where now we're starting to stretch things kind of far away from their hash codes. And that theta of 1, that average case of being constant time, is starting to get a little more-- starting to tend a little more towards theta of n. We're starting to lose that advantage of hash tables. 

This problem that we just saw is something called clustering. And what's really bad about clustering is that once you now have two elements that are side by side it makes it even more likely, you have double the chance, that you're going to have another collision with that cluster, and the cluster will grow by one. And you'll keep growing and growing your likelihood of having a collision. And eventually it's just as bad as not sorting the data at all. 

The other problem though is we still, and so far up to this point, we've just been sort of understanding what a hash table is, we still only have room for 10 strings. If we want to continue to hash the citizens of Springfield, we can only get 10 of them in there. And if we try and add an 11th or 12th, we don't have a place to put them. We could just be spinning around in circles trying to find an empty spot, and we maybe get stuck in an infinite loop. 

So this sort of lends to the idea of something called chaining. And this is where we're going to bring linked lists back into the picture. What if instead of storing just the data itself in the array, every element of the array could hold multiple pieces of data? Well that doesn't make sense, right? We know that an array can only hold-- each element of an array can only hold one piece of data of that data type. 

But what if that data type is a linked list, right? So what if every element of the array was a pointer to the head of a linked list? And then we could build those linked lists and grow them arbitrarily, because linked lists allow us to grow and shrink a lot more flexibly than an array does. So what if we now use, we leverage this, right? We start to grow these chains out of these array locations. 

Now we can fit an infinite amount of data, or not infinite, an arbitrary amount of data, into our hash table without ever running into the problem of collision. We've also eliminated clustering by doing this. And well we know that when we insert into a linked list, if you recall from our video on linked lists, singly linked lists and doubly linked lists, it's a constant time operation. We're just adding to the front. 

And for look up, well we do know that look up in a linked list can be a problem, right? We have to search through it from beginning to end. There's no random access in a linked list. But if instead of having one linked list where a lookup would be O of n, we now have 10 linked lists, or 1,000 linked lists, now it's O of n divided by 10, or O of n divided by 1,000. 

And while we were talking theoretically about complexity we disregard constants, in the real world these things actually matter, right? We actually will notice that this happens to run 10 times faster, or 1,000 times faster, because we're distributing one long chain across 1,000 smaller chains. And so each time we have to search through one of those chains we can ignore the 999 chains we don't care about , and just search that one. 

Which is on average to be 1,000 times shorter. And so we still are sort of tending towards this average case of being constant time, but only because we are leveraging dividing by some huge constant factor. Let's see how this might actually look though. So this was the hash table we had before we declared a hash table that was capable of storing 10 strings. We're not going to do that anymore. We already know the limitations of that method. Now our hash table's going to be an array of 10 nodes, pointers to heads of linked lists. 

And right now it's null. Each one of those 10 pointers is null. There's nothing in our hash table right now. 

Now let's start to put some things into this hash table. And let's see how this method is going to benefit us a little bit. Let's now hash Joey. We'll will run the string Joey through a hash function and we return 6. Well what do we do now? 

Well now working with linked lists, we're not working with arrays. And when we're working with linked lists we know we need to start dynamically allocating space and building chains. That's sort of how-- those are the core elements of building a linked list. So let's dynamically allocate space for Joey, and then let's add him to the chain. 

So now look what we've done. When we hash Joey we got the hashcode 6. Now the pointer at array location 6 points to the head of a linked list, and right now it's the only element of a linked list. And the node in that linked list is Joey. 

So if we need to look up Joey later, we just hash Joey again, we get 6 again because our hash function is deterministic. And then we start at the head of the linked list pointed to by array location 6, and we can iterate across that trying to find Joey. And if we build our hash table effectively, and our hash function effectively to distribute data well, on average each of those linked lists at every array location will be 1/10 the size of if we just had it as a single huge linked list with everything in it. 

If we distribute that huge linked list across 10 linked lists each list will be 1/10 the size. And thus 10 times quicker to search through. So let's do this again. Let's now hash Ross. 

And let's say Ross, when we do that the hash code we get back is 2. Well now we dynamically allocate a new node, we put Ross in that node, and we say now array location 2, instead of pointing to null, points to the head of a linked list whose only node is Ross. And we can do this one more time, we can hash Rachel and get hashcode 4. malloc a new node, put Rachel in the node, and say a array location 4 now points to the head of a linked list whose only element happens to be Rachel. 

OK but what happens if we have a collision? Let's see how we handle collisions using the separate chaining method. Let's hash Phoebe. We get the hashcode 6. In our previous example we were just storing the strings in the array. This was a problem. 

We don't want to clobber Joey, and we've already seen that we can get some clustering problems if we try and step through and probe. But what if we just kind of treat this the same way, right? It's just like adding an element to the head of a linked list. Let's just malloc space for Phoebe. 

We'll say Phoebe's next pointer points to the old head of the linked list, and then 6 just points to the new head of the linked list. And now look, we've changed Phoebe in. We can now store two elements with hashcode 6, and we don't have any problems. 

That's pretty much all there is to chaining. And chaining is definitely the method that's going to be most effective for you if you are storing data in a hash table. But this combination of arrays and linked lists together to form a hash table really dramatically improves your ability to store large amounts of data, and very quickly and efficiently search through that data. 

There's still one more data structure out there that might even be a bit better in terms of guaranteeing that our insertion, deletion, and look up times are even faster. And we'll see that in a video on tries. I'm Doug Lloyd, this is CS50. 