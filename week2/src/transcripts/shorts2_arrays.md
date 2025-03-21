---
title: SHORST2 - ARRAYS - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DOUG LLOYD: All right. Working with single variables is pretty fun. But what if we want to work with a lot of variables, but we don't want to have a bunch of different names flying around our code? In this case, arrays are going to come in really handy. Arrays are a really fundamental data structure for any programming language that you will use. And they're really, really useful, particularly, as we'll see, in CS 50. 

We use arrays to hold values of the same data type at contiguous memory locations. That is to say, it's a way that we can group a bunch of integers together in memory or a bunch of characters or floats in memory really close together and work with them without having to give each one its own unique name, which can get cumbersome after a little while. 

Now, one way to analogize arrays is to think about your local post office for a second. So step away from programming and just close your eyes and visualize in your mind your local post office. Usually, in most post offices, there's a large bank a post office boxes on the wall. 

An array is a giant block of contiguous memory, the same way that a mail bank in your post office is a large space on the wall of the post office. Arrays have been partitioned into small, identically sized blocks of space, each of which is called an element, in the same way that the wall of the post office has been partitioned into small, identically sized blocks of space, which we call a PO box. Each element of the array can store a certain amount of data, just as each post office box is able to hold a certain amount of mail. 

What can be stored in each element of the array is variables of the same data type, such as int or char, just like in your post office box, you can only fit things of a similar type, such as letters or small packages. Lastly, we can access each element of the array directly by index number, just as we can access our post office box by knowing its mailbox number. Hopefully, that analogy helps you get your head around the idea of arrays by analogizing to something else that you are probably already familiar with. 

In C, the elements of an array are indexed starting from 0, not from 1. And this is really important. And in fact, this is why we, in CS 50, and why computer scientists frequently will count from 0, is because of C's array indexing, which always starts at 0. So if an array consists of n elements, the first element of that array is located at index 0, and the last element of the array is located at index n minus 1. Again, if there's n elements in our array, the last index is n minus 1. 

So if our array has 50 elements, the first element is located at index 0, and the last element is located at index 49. Unfortunately, or fortunately, depending on your perspective, C is very lenient here. It will not prevent you from going out of bounds of your array. You could access the minus 3 element of your array or the 59th element of your array, if your array only has 50 elements. It won't stop your program from compiling, but at run time, you might encounter a dreaded segmentation fault if you start to access memory that is outside the bounds of what you asked your program to give you. So do be careful. 

What does an array declaration look like? How do we code an array into existence like we code any other variable? There are three parts to an array declaration-- a type, a name, and a size. This is very similar to a variable declaration, which is just a type and a name, the size element being the special case for an array, because we are getting a bunch of them at the same time. 

So the type is what kind of variable you want each element of the array to be. Do want it to an array of integers? Then, your data type should be int. Do you want it to be an array of doubles or floats? Data type should be double or float. The name is what you want to call your array. What do you want to name this giant bank of integers or floats or chars or doubles, or whatever have you? What do you want to call it? Pretty self explanatory. 

Lastly, size, which goes inside of square brackets, is how many elements you would like your array to contain. How many integers do you want? How many floats do you want? 

So for example, int student grades 40. This declares an array called Student grades, which consists of 40 integers. Pretty self explanatory, I hope. Here's another example. Double menu prices 8. This creates an array called Menu prices, which consists of room in memory for eight doubles. 

If you think of every element of an array of type data-type, so for example, a single element of an array of type int, the same way you would think of any other variable of type int, all the familiar operations that we discussed previously in the Operations video will make sense. So here, we could declare an array of Booleans called Truthtable, which consists of room for 10 Booleans. 

And then, just like we could just assign a value to any other variable of type Boolean, we could say something like Truthtable square bracket 2, which is how we indicate, which element of the truth table? The third element of the truth table, because remember, we're counting from 0. So that's how we indicate the third element of the truth table. Truthtable 2 equals false, just like we could declare-- or we could assign, rather, any Boolean type variable to be false. 

We can also use it in conditions. if(truthtable 7 == true), which is to say, if the eighth element of Truthtable is true, maybe we want to print a message to the user, printf("TRUE!n");. That causes us to say Truthtable 10 equals true, right? Well, I can, but it's pretty dangerous, because remember, we have an array of 10 Booleans. So the highest index that the compiler has given us is 9. 

This program will compile, but if something else in memory exists where we would expect Truthtable 10 to go, we could suffer a segmentation fault. We might get away with it, but in general, pretty dangerous. So what I'm doing here is legal C, but not necessarily the best move. Now, when you declare and initialize an array simultaneously, there's actually a pretty special syntax that you can use to fill up the array with its starting values. It can get cumbersome to declare an array of size 100, and then have to say, element 0 equals this; element 1 equals this; element 2 equals that. What's the point, right? 

If it's a small array, you could do something like this. Bool truthtable 3 equals open curly brace and then comma separate the list of elements that you want to put in the array. Then close curly brace semicolon. This creates an array of size three called Truthtable, with elements false, true, and true. And in fact, the instantiation syntax I have here is exactly the same as doing the individual element syntax below. These two ways of coding would produce the exact same array. 

Similarly, we could iterate over all of the elements of an array using a loop, which, in fact, is a very strongly recommended at-home exercise. How do you create an array of 100 integers, where every element of the array is its index? So for example, we have a array of 100 integers, and in the first element, we want to put 0. In the second element, we want to put 1. In the third element, we want to put 2; and so on and so on. That's a really good at-home exercise to do that. 

Here, it doesn't look like too much has changed. But notice that in between the square brackets, this time, I've actually omitted the number. If you're using this very special instantiation syntax to create an array, you actually don't need to indicate the size of the array beforehand. The compiler is smart enough to know that you actually want an array of size 3, because you put three elements to the right of the equal sign. If you had put four, it would have given you a truth table of size four; and so on and so on. 

Arrays are not restricted to a single dimension, which is pretty cool. You can actually have as many side specifiers as you wish. So for example, if you want to create a board for the game Battleship, which, if you ever played, is a game that is played with pegs on the 10 by 10 grid, you could create an array like this. You could say Bool battleship square bracket 10 closed square bracket square bracket 10 closed square bracket. 

And then, you can choose to interpret this in your mind as a 10 by 10 grid of cells. Now, in fact, in memory, it really does just remain a 100 element, single dimensional array. And this, in fact, goes for if you have three dimensions or four or five. It really just does multiply all of the indices-- or all of the size specifiers-- together, and you just get a one-dimensional array of that size. 

But in terms of organization and visualization and human perception, it can be a lot easier to work with a grid if you're working on a game like Tic-tac-toe or Battleship, or something like that. It's a great abstraction, instead of having to think about a Tic-tac-toe board as a line of nine squares or a Battleship board as a line of 100 squares. A 10 by 10 grid or a three by three grid is probably a lot more easy to perceive. 

Now, something really important about arrays. We can treat each individual element of the array as a variable. We saw that earlier when we were assigning the value True to certain Booleans or testing them in conditionals. But we can't treat entire arrays themselves as variables. We cannot, for example, assign one array to another array using the assignment operator. It's not legal C. 

If we want to, for example-- what we would be doing in that example would be to copy one array into another. If we want to do that, we actually need to use a loop to copy over each individual element one at a time. I know it's a little time consuming. 

So for example, if we had these couple of lines of code, would this work? Well, no, it wouldn't, right? Because we're trying to assign food to bar. That's not going to work, because it's an array, and we just described that that's not legal C. 

Instead, if we want to copy the contents of food into bar, which is what we're trying to do here, we would need a syntax like this. We have a for loop that goes from J is equal to 0 up to 5, and we increment J on every iteration of the loop and assign elements like that. This would result in bar also being one, two, three, four, five, but we have to do it this very slow element-by-element way, instead of by just copying the entire array. In other programming languages, more modern ones, you can, in fact, do just that simple equals syntax. But C, unfortunately, we're not allowed to do that. 

Now, there's one other thing I want to mention about arrays that can be a little bit tricky the first time you work with them. We discussed in a video about variable scope, that most variables in C, when you call them in functions, are passed by value. Do you remember what it means to pass something by value? It means we're making a copy of the variable that's being passed in. The callee function, the function that's receiving the variable, doesn't get the variable itself. It gets its own local copy of it to work with. 

Arrays, of course, do not follow this rule. Rather, what we call this is passing by reference. The callee actually does receive the array. It does not receive its own local copy of it. And if you think about it, this makes sense. If arrays are really large, it takes so much time and effort to make a copy of an array of 100 or 1,000 or 10,000 elements, that it's not worth it for a function to receive a copy of it, do some work with it, and then just be done with the copy; it doesn't need to have it hanging around anymore. 

Because arrays are some bulky and cumbersome, we just pass them by reference. We just trust that function to, don't break anything. So it does actually get the array. It doesn't get its own local copy of it. 

So what does this mean, then, when the callee manipulates elements of the array? What happens? For now, we'll gloss over why exactly this happens, why arrays are passed by reference and everything else is passed by value. But I promise you, we will return and give you the answer to this in a later video. 

Here's one more exercise for you before we wrap up things on arrays. The bunch of code here, that's not particularly good style, just I'll make that caveat. There's no comments in here, which is pretty bad form. But it's only because I wanted to be able to fit everything on the screen. 

At the top, you can see that I have two function declarations for set array and set int. Set array apparently takes an array of four integers as its input. And set int apparently takes a single integer as its input. But both of them don't have an output. The output, the return type, of each one is void. In Main, we have a couple of lines of code. We declare an integer variable called A and assign it the value 10. We declare an array of four integers called B and assign the elements 0, 1, 2, and 3, respectively. Then, we have a call to set int and a call to set array. The definitions of set array and set int are down below, at the bottom. 

And so, again, I ask you the question. What gets printed out here at the end of Main? There's a printout col. I'm printing out two integers. I'm printing out the contents of A and the contents of B square bracket 0. Pause the video here and take a minute. Can you figure out what this function will print at the end? Hopefully, if you recall the distinction between passing by value and passing by reference, this problem wasn't too tricky for you. And the answer you would have found is this. If you're not really sure as to why that's the case, take a second, go back, review what I was just discussing about passing arrays by reference, versus passing other variables by value, and hopefully, it'll make a little bit more sense. 

I'm Doug Lloyd, and this is CS50. 