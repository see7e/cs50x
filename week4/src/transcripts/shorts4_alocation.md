---
title: SHORST4 - DINAMICALY MEMORY ALOCATION - TRANSCRIPT
tags: studies, programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DOUG LLOYD: So in this video, we're going to talk about how to dynamically allocate memory in C. Now, as a disclaimer, if you haven't watched our video on pointers or aren't generally familiar with the concept of pointers, you're probably going to want to take a look at that before this. This video, dynamic memory allocation in general, works specifically with pointers. So you're going want to make sure that you're comfortable with that before diving in to this particular video. Without further ado, let's get started. Now, we've already seen how to work with pointers before. But typically, we've only done it in the context of pointing a pointer variable that we declare statically at another variable that already exists. You may recall from our video on pointers, we had a line like int x equals 5. And then we would say int star px equals ampersand x. But that's the only way we've seen how to work with pointers. And that's static pointer usage, basically. In order to work with pointers statically as we have, we need to know exactly how much memory we're going to use at the moment we compile our program. So we're not going to be creating any memory on the fly. All the memory that we're going to use is already set up when we begin. That presents sort of an issue, right? What if we don't know how much memory we're going to have when we get started? Maybe you're going to be asking the user to give you a number and they're going to generate a hundred linked list object. So they're going to generate hundreds of something and you don't know that. Or maybe they generate 200 or 400. We wouldn't be able to predict this in advance, and so we need to use dynamic memory allocation in order to get new memory in our program while the program is already running. And that's a little bit different than anything we've seen before. We can do this by allocating memory from something called the heap. The heap is a giant pool of memory. And so far, the only pool of memory that we're familiar with is called the stack. But dynamically allocated memory comes from the heap and statically allocated memory-- which is anything that you give a name to, typically, like a variable name-- is going to be set up on the stack. And anything that you create dynamically while your program is running is going to come from the heap. But as we can see from this diagram, the stack and the heap are actually the same big chunk of memory. It just so happens that the stack we allocate from the bottom to the top, typically, to visualize it. So the stack memory addresses will be a bit lower numbers and the heap will have higher numbers and it'll allocate downward. So it's really one giant pool of memory, but we call it two different things depending on how it's being used. The stack for statically declared memory grows up and the heap for dynamically allocated memory grows down. How do we get at this dynamically allocated memory? How do we access memory on the heap? We need to use a new function called malloc. You can get malloc by pound including standard lib.h, stdlib.h. And the only argument that you need to pass to malloc is how many bytes of memory that you want. So if you want an integer, you say malloc 4. If you want a character, you malloc 1. If you want to double, you malloc 8, and so on. And you can be more complex than that, as we'll soon see. What malloc will then try and do is find some chunk of memory the size that you asked for on the heap. So it'll go and try and find eight contiguous bytes of memory, for example. If we're allocating a double, it will go and try and find eight contiguous bytes of memory from the heap. And what it will do is it will return to you a pointer to that memory. So the only way we're going to be able to access dynamically allocated memory or use it is by dereferencing the pointer that we get back from malloc. And that's why it's important to understand pointers before going forward. Now, it's possible that malloc might not actually be able to give you back memory, in which case it's going to return to you null. And so one of the first rules to remember about dynamically allocated memory is to always check for null after malloc. Now, why might this happen? Maybe you've run out of memory. The stack and the heap have just completely run out or there's been some sort of catastrophic failure that we can't predict. But either way, if you recall from our pointers video, dereferencing a null pointer, bad news. So the first thing you want to do-- after you malloc, of course-- is to check to make sure that you didn't get back null. And if you did, you're going to need to abort your program because something has gone wrong and you can't proceed with what you currently have. So if we want to just get an integer, statically declare it, we can just say int x. That's going to create a variable called x on the stack that we can then assign any value that we like to. If you want to dynamically allocate an integer, we say the following-- int star px equals malloc 4. And the reason we say four here is because there are four bytes in an integer. I easily also could have used the sizeof operator, which is available in C. Basically, you pass it a type-- so it's a little bit different. Usually with functions you pass in a variable. With malloc, you pass in-- or with sizeof, rather, you pass in a type and it will return how many bytes that type takes up on the system. So int star px equals malloc size of int or int star ps equals malloc 4 basically means malloc going to go try and find you four bytes of memory that are next to each other on the heap. And malloc will return to you a pointer to that memory called px. And then we could dereference that pointer, as we've seen in the pointers video, to manipulate it, to put a value in there, to do whatever we want to do with it. Let's see another example of this. Maybe we want to get an integer from the user. So recall that CS50 we have the get_int function that we can use. Int x equals get_int. We're basically prompting the user for some integer value. And it'll give us some number, hopefully, in this example, a positive number. Let's say I want to declare an array of that many floats on the stack. I can do this by saying float stack_array and then in square brackets-- which, again, indicates the size of the array-- x. This is legal in C 99 and C 11. If you're using a very old version of C, this was actually previously not allowed. But you can do this. We can basically get a variable-sized array on the stack, which we're doing here because we don't know how big it's going to be in advance. We're just getting it from the user. But this is how we would declare an array of floats on the stack where the number of items in that array is the number the user just gave us. And I can also dynamically allocate an array of floats on the heap-- not on the stack, remember, because we're dynamically allocating the memory this time. Float star heap_array. So that's my pointer to the memory that I'm getting. And I want to malloc x times the size of a float. So if I want to have 50 floats, I need 50 times the size of a float, so 50 times 4. Maybe I want 100, so it would be 100 times four. So that's why we're doing the multiplication there. And malloc is going to return to us one giant block of memory that size, which we can then just treat like any other array. There's one catch with dynamically allocated memory, though, that we have to deal with, and that's something that we haven't seen before, and that is that it is not released back to the system when you are done. So if you haven't yet seen our video on the call stack or stack frames, this might not be something you're aware of yet. But typically, when a function finishes running, what happens is all of the memory that was created for purposes of that function's existence gets destroyed and it is released back to the system to be used somewhere else. So another function call that might come up can use that same bit of memory before. That's kind of convenient, right? This system is constantly recycling where it can. But when you tell the system, I want a block of memory, the system is not going to assume anything about it. It's not going to assume that it hasn't seen you make a call with it for 50 lines or whatever, and it's just going to dynamically free it or release it back to the system. And if you fail to release enough memory back to the system, what you get is something called a memory leak. And memory leaks are really not good because they can really slow down your system. And in fact, there are some browsers that shall remain nameless that are sort of notorious for not freeing memory or not releasing memory back to the system when it's done. And that can really cause your computer to slow down because that browser is basically hogging a bunch of memory and the other programs on your computer can't use it because the browser has sort of allocated it and said, no, this is mine. I need it. But it never releases it back to be shared by the other things on the system. So that's why if you leave a browser open for days-- or some browsers open for days or weeks-- you might notice your computer starts to slow down. Now, the rule is, as I've mentioned before, when you're done working with dynamically allocated memory, all you have to do is free it. And free is another function that is available in standard lib.h. And basically what you passed to free is a pointer to any memory that you have dynamically allocated previously. And basically that's just telling the system, I'm done. You can use this memory for whatever you'd like. So here's another example let's say we want to malloc a 50 character long array-- so basically a big string. We're going to call it word. We dynamically allocate it. Then we just do some stuff with it. Maybe we were in the middle of a function. You know, we're changing its value. We're assigning new characters. We're printing it out, for example. And then we decide that we're done with it. How do we release this back to the system? We just need to free it. So we free word. Word is the pointer to that block of memory. That's the thing that we want to free. So there are three basic rules for malloc and free that are really important to internalize. The first is that everything that you malloc has to be freed before your program finishes running. Now, granted, if your program actually finishes running, once it's completely done, once you've returned zero from main, for example, then it will be freed. But it's a good practice to make sure that everything that you allocate you specifically free by explicitly calling the free function, as opposed just relying on the system to do it once your program is completely done. So everything that you malloc, you have to free. Rule number two, only things that you malloc are things that you should free. So if you statically declared a variable, you don't want to free it. The system is going to take care of releasing all statically declared memory for you. It's only dynamically allocated memory-- only memory that you malloc are things that you should free. And then make sure not to free the same block of memory more than once because that can create the problem of a double free and you have sort of an inverse memory leak, like a memory flow or something, where you tricked the system into thinking that you have more memory than you do. It's not the kind of thing that you actually want to do. So remember, everything you malloc you should free. Only things that you malloc you should free. And don't free anything more than once. Let's just close this video by taking a look at a couple of lines of code and a visual example to show you exactly what's happening as we do it. So first, let's statically declare an integer called m. And so this would look something like this. I've colored the box green because in my head, sort of, integers are always in green boxes. And I've written the label m on the box. Then I'm going to say int star a. So here I'm statically declaring a pointer called a. So recall that I like to think of it's an int star, so it's int-like, so it will be green. It's a green-ish box. It's not a green box because that's for ints. But int stars are sort of green-ish. They refer to ints. So this is another box and this one is called a. Then I can say int star b equals malloc sizeof int. So what's going to happen here? Well, I'm going to have something called b that I'm giving a name to. So that's going to be sort of a light greenish box. And I'm asking malloc to dynamically give me one int's worth of space. And so what actually happened sort of visually is this. Notice that the actual integer I didn't give a name to. I don't have a name for it. It's one way typically that I know I don't have a statically declared integer. The only way that I can refer to that green box is by dereferencing the pointer called b. So b has a name, and that's statically declared. But I dereference b in order to get to this dynamically allocated memory. And of course, I'm not going to do this here. But the first thing I should do immediately after this is check to make sure that b is not null. If b is null, something has gone wrong and I need to stop my program immediately. Next, I can say something like this-- a equals ampersand m. If you recall from our video on pointers, basically this just means a points to m. So that just creates this arrow here. Next up, let's say a equals b. Before I show you what's going to happen here, can you try and guess a little bit about what it's going to be? Take a look at the diagram. Think about how relationships might change. If I say a equals b, what am I saying? What I'm saying is that a and b are now going to point to the same location, in particular, a is going to a point where b currently points. And so instead of pointing to m, a is now going to point over here to this dynamically allocated block that I can currently only reference-- now I can reference it multiple ways. Now I could say star a or star b. I can reference it either way because both of those same statically declared variables point to the same location. I can then say m equals 10. That's not a problem because 10 was statically declared. It's a box that I know about already. It's got a name. So when I say m equals 10, I'm just saying put 10 into this green box called m. Star b equals m plus 2. It's a little weird, right? But what's m plus 2? Well, m is 10, so 10 plus 2 is 12. And star b equals 12. When I say a star b, I'm dereferencing b. So I'm going to travel along the arrow to where b points. And I'm going to put 12 in that location. OK? Next up I'm going to free b. So remember what happens with free is we are telling the system we're no longer working with this. We're done. You can take these four bytes back, or whatever the size of it is. This one happens to be four bytes. You can take it back and use it for whatever you want in some other program. So when I free b, this memory basically goes away. a and b still point to where it used to be, but I no longer have access to it. If I try and touch it, the system might get upset with me. So for example, if I try and say this-- star a equals 11-- what's going to happen? Unpredictable behavior. We don't know. We might get a segmentation fault because we're touching memory that we're no longer-- we don't have write privileges to anymore. You might get away with it, depends on where that memory happened to live on the system. But it's unpredictable. So once you free memory, remember, you're telling the system, I don't need it anymore. So if you then try and use it, some strange things might result. Dynamic memory allocation is a little strange to get used to because we're so used this idea of creating a variable and assigning it a value and just manipulating it in that way that using pointers to sort of control where memory is and change it indirectly through pointers can be a bit strange. But just keep practicing with it. Internalize those rules about how to malloc and free successfully to make sure that you don't create memory leaks or anything like that. And you should be off to a good start. I'm Doug Lloyd. This is CS50. 