---
title: SHORST1 - DATA TYPES - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] SPEAKER: All right. So let's talk about another thing that's kind of unique to C, which is data types and variables. When I say unique to C, I really only mean in the context of, if you've been a programmer for a really long time, you've probably not worked with data types if you've used modern programming languages. Modern languages like PHP and JavaScript, which we'll also see a little later on in the course, you don't actually have to specify the data type of a variable when you use it. 

You just declare it and start using it. If it's an integer, it know it's an integer. If it's a character, it's knows it's a character. If it's a word, it knows it's a string, so-called. 

But in C, which is an older language, we need to specify the data type of every variable that we create the first time that we use that variable. So C comes with some built-in data types. And let's get familiar with some of those. And then afterwards we'll also talk a little bit about some of the data types that we've written for you, so you can use them in CS50. 

The first is int. The int data type is used for variables that will store integer values. So 1, 2, 3, negative 1, 2, 3, and so on. Integers, which is something you should keep in mind for the quiz, always take up four bytes of memory, which is 32 bits. There are eight bits in a byte. 

So this means that the range of values that an integer can store is limited by what can fit within 32 bits worth of information. Now as it turns out, it was long ago decided that we would split up that range of 32 bits into negative integers and positive integers, each getting half of the range. So the range of values that we represent with an integer range from negative 2 to the 31st power to 2 to the 31st power minus 1, cause you also need a spot for 0. 

So basically half of the possible values you can fit in an int are negative, and half are positive. And roughly here, this is about negative 2 billion to about positive 2 billion. Give or take a couple hundred million. So that's what you can fit in an integer variable. Now we also have something called an unsigned integer. Now unsigned ints are not a separate type of variable. Rather, unsigned is what's called a qualifier. It modifies the data type of integer slightly. 

And in this case, what unsigned means-- and you can also use unsigned other data types, integer's not the only one. What it effectively does is doubles the positive range of values that an integer can take on at the expense of no longer allowing you to take on negative values. So if you have numbers that you know will get higher than 2 billion but less than 4 billion, for example-- which is 2 to the 32nd power-- you might want to use an unsigned int if you know your value will never be negative. 

You'll occasionally have used for unsigned variables in CS50, which is why I mention it here. But again, the range of values that you can represent with an unsigned integer as to t regular integer, are 0 to 2 to the 32nd power minus 1, or approximately 0 to 4 billion. So you've effectively doubled the positive range that you can fit, but you've given up all the negative values. 

Now as an aside, unsigned is not the only qualifier that we might see for variable data types. There are also things called short and long and const. Const we'll see a little bit later in the course. Short and long, we probably won't. 

But just know that there are other qualifiers. Unsigned isn't the only one. But it's the only one we're going to talk about right now. So all right. So we've covered integers. What's next? 

Chars. So chars are used for variables that will store single characters. Char is short for character. And sometimes you might hear people pronounce it as car. 

So characters always take up one byte of memory, which is just 8 bits. So this means that they can only fit values in the range of negative 2 to the seventh power, or negative 128, to 2 to the 7th power minus 1, or 127. 

Thanks to ASCII, it was long ago decided a way to map those positive numbers from 0 to 127 to various characters that all exist on our keyboard. So as we'll see later on in the course, and you'll probably come to memorize at some point, capital A, for example-- the character capital A-- maps to the number 65. And the reason for that is because that's what's it's been assigned by the ASCII standard. 

Lowercase A is 97. The character 0 for when you actually type the character, not representing the number zero, is 48. You'll learn a couple of these as you go. And you'll certainly come to need them a little bit later in CS50. 

The next major data type is floating point numbers. So floating point numbers are also known as real numbers. They're basically numbers that have a decimal point in them. Floating point values like integers are also contained within 4 bytes of memory. Now there's no chart here. There's no number line, because describing the range of a float isn't exactly clear or intuitive. 

Suffice it to say you have 32 bits to work with. And if you have a number like pi, which has an integer part 3, and a floating point part, or decimal part 0.14159, and so on, you need to be able to represent all of it-- the integer part and the decimal part. 

So what do you think that might mean? One thing is that if the decimal part gets longer and longer, if I have a very large integer part, I might not be able to be as precise with the decimal part. And that's really the limitation of a float. 

Floats have a precision problem. We only have 32 bits to work with, so we can only be so precise with our decimal part. We can't necessarily have a decimal part precise to 100 or 200 digits, because we only have 32 bits to work with. So that's a limitation of a float. 

Now fortunately there's another data type called double, which somewhat deals with this problem. Doubles, like floats, are also used to store real numbers, or floating point values. The difference is that doubles are double precision. They can fit 64 bits of data, or eight bytes. What does that mean? Well, it means we can be a lot more precise with the decimal point. Instead of having pi to seven places maybe, with a float, we can maybe have it to 30 places. If that's important, you might want to use a double instead of a float. Basically, if you're working on anything where having a really long decimal place and a lot of precision is important, you probably want to use a double overfloat. Now for most of your work in CS50, a float should suffice. But do know that doubles exist as a way to somewhat deal with the precision problem by giving you an extra 32 bits to work with for your numbers. 

Now this is not a data type. This is a type. And it's called void. And I'm talking about it here because we've probably seen it a few times already in CS50. And you might be wondering what it's all about. 

So void is a type. It does exist. But it is not a data type. 

We can't create a variable of type void and assign a value to it. But functions, for example, can have a void return type. Basically, if you see a function that has a void return type, it means it doesn't return a value. Can you think of a common function that we've used so far in CS50 that doesn't return a value? 

Printf is one. Printf does not actually return anything to you. It prints something to the screen, and it's basically a side effect of what printf does. But it doesn't give you a value back. You don't capture the result and store it in some variable to use it later on. It just prints something to the screen and you're done. 

So we say that printf is a void function. It returns nothing. 

The perimeter list of a function can also be void. And you've also seen that quite a bit in CS50 too. Int main void. Does that ring a bell? Basically what that means is that main doesn't take any parameters. There's no argument that get passed into main. Now later on we'll see that there is a way to pass arguments into main, but so far what we've seen is int main void. Main just doesn't take any arguments. And so we specify that by saying void. We're just being very explicit about the fact that it doesn't take any arguments. 

So for now, suffice it to say that void basically should just serve as a placeholder for you as thinking about as nothing. It's not really doing anything. There's no return value here. There's no parameters here. It's void. It's a little more complex than that. But this should suffice for the better part of the course. And hopefully now you have a little bit more of a concept of what void is. 

So those are the five types you'll encounter that are built-in to C. But in CS50 we also have a library. CS50.h, which you can include. And which will provide you with two additional types that you'll probably be able to use on your assignments, or just working generally programming. 

The first of these is bool. So the Boolean data type, bool, is used for variables that will store a Boolean value. If you've ever heard this term before, you might know that a Boolean value is capable of only holding two different distinct values. True and false. Now this seems pretty fundamental, right? It's kind of a surprise that this doesn't exist in C as it's built-in. And in many modern languages, of course, Booleans are a standard default data type. But in C, they're actually not. But we've created it for you. So if you ever need to create a variable whose type is bool, just be sure to `#include` CS50.h at the beginning of your program, and you'll be able to create variables of the bool type. 

If you forget to `#include` CS50.h, and you start using Boolean-type variables, you might encounter some problems when you're compiling your program. So just be on the lookout for that. And maybe you can just fix the problems by pound including CS50.h. 

The other major data type that we provide for you in the CS50 library is string. So what is a string? Strings are really just words. They're collections of characters. They're words. They're sentences. They're paragraphs. Might be whole books, even. 

Very short to very long series of characters. If you need to use strings, for example, to store a word, just be sure to include CS50.h at the beginning of your program so you can use the string type. And then you can create variables whose data type is string. Now later on in the course, we'll also see that that's not the entire story, either. We'll encounter things called structures, which allow you to group what may be an integer and a string into one unit. And we can use that for some purpose, which might come in handy later on in the course. 

And we'll also learn about defined types, which allow you to create your own data types. We don't need to worry about that for now. But just know that that's something on the horizon, that there's a lot more to this whole type thing than I'm telling you just now. So now that we've learned a little bit about the basic data types and the CS50 data types, let's talk about how to work with variables and create them using these data types in our programs. If you want to create a variable, all you need to do is two things. 

First, you need to give it a type. The second thing you need to do is give it a name. Once you've done that and slapped a semicolon at the end of that line, you've created a variable. 

So here's two examples. Int number; char letter;. What have I done here? I've created two variables. 

The first, the variable's name is number. And number is capable of holding integer type values, because its type is int. Letter is another variable that can hold characters because its data type is char. 

Pretty straightforward, right? If you find yourself in a situation where you need to create multiple variables of the same type, you only need to specify the type name once. Then just list as many variables of that type as you need. 

So I could for example, here in this third line of code, say int height;, new line. Int width;. And that would work too. I'd still get two variables called height and width, each of which is an integer. But I'm allowed to, things to C syntax, consolidate it into a single line. Int height, width; It's the same thing. I've created two variables, one called height one called width, both of which are capable of holding integer type values. 

Similarly here, I can create three floating point values at once. I can maybe create a variable called square root of 2-- which presumably will eventually hold the floating point-- that representation of the square root of 2-- square root of 3, and pi. I could have done this on three separate lines. Float, square root 2; Float square root 3; float pi; and that would work too. 

But again, I can just consolidate this into a single line of code. Makes things a little bit shorter, not as clunky. 

Now in general, it's good design to only declare a variable when you need it. And we'll talk a little bit more about that later on in the course when we discuss scope. So don't necessarily need to create all of your variables at the beginning of the program, which some people might have done the past, or was certainly a very common coding practice many years ago when working with C. You might just want to create a variable right when you need it. All right. So we've created variables. How do we use them? After we declare a variable, we don't need to specify the data type of that variable anymore. In fact, if you do so, you might end up with some weird consequences that we'll kind of gloss over for now. But suffice it to say, weird things are going to start happening if you inadvertently re-declare variables with the same name over and over. 

So here I have four lines of code. And I have a couple of comments there just indicating what's happening on each line just to help you get situated in what's going on. So int number;. You saw that previously. That's a variable declaration. 

I've now created a variable called number that's capable of holding integer-type values. I've declared it. 

The next line I'm assigning a value to number. Number equals 17. What's happening there? I'm putting the number 17 inside of that variable. 

So if I ever then print out what the contents of number are later on, they'll tell me it's 17. So I've declared a variable, and then I've assigned it. 

We can repeat the process again with char letter;. That's a declaration. Letter equals capital H. That's an assignment. Pretty straightforward, too. 

Now this process might seem kind of silly. Why are we doing this in two lines of code? Is there a better way to do it? In fact, there is. Sometimes you might see this called initialization. It's when you declare a variable and assign a value at the same time. This is actually a pretty common thing to do. When you create a variable, you usually want it to have some basic value. Even if it's 0 or something. You just you give it a value. 

You can initialize a variable. Int number equals 17 is the same as the first two lines of code up above. Char letter equals h is the same as the third and fourth lines of code above. The most important takeaway here when we're declaring and assigning variables is after we've declared it, notice I'm not using the data type again. I'm not saying int number equals 17 on the second line of code, for example. I'm just saying number equals 17. 

Again , re-declaring a variable after you've already declared it can lead to some weird consequence. So just be careful of that. 

I'm Doug Lloyd. And this is CS50. 