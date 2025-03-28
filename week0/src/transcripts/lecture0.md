---
title: LECTURE0 - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DAVID J. MALAN: All right. This is CS50, Harvard University's introduction to the intellectual enterprises of computer science and the arts of programming. My name is David Malan, and I actually took this course myself, back in 1996. I was a sophomore at the time. I was actually concentrating in government, because a year prior, as a first year, I'd come into Harvard thinking that I liked history and constitutional law and similar classes in high school. And so when I got here, I rather gravitated toward that which was familiar. I figured, if I liked and if I were good at that particular subject in high school, then that's presumably who I'm supposed to be here. 

But it wasn't until sophomore year that I got up the nerve to step foot in the CS50 classroom, and even then, it was only out of curiosity. Like I had no intention of studying computer science of even taking CS50 when I got to campus. But people were talking about it, and there was a lot of beware. And it was perhaps for the initiated only, and I didn't really ultimately what computer science was. 

But for me, the light bulb went off. I found that, contrary to what I'd seen in high school, where I saw friends of mine like programming away in the computer lab, heads down, antisocially just doing whatever it was they were doing, it really wasn't that, once I got to this particular class and this particular place. It was much more about problem solving more generally and just learning how to express yourself in code, in different languages. So that you can actually solve problems of interest to you. Even if you have no intention of being a computer scientist or an engineer, but just want to be able to solve problems, analyze data do interesting things, in the arts, humanities, social sciences, physical sciences, or really any other field. 

And indeed, this particular path led me to computer science, but the hope for CS50 more generally is that, indeed, you just find your way to applying principles that you'll learn over the coming months to whatever field is of interest to you. With that said, it was definitely a lot of work and not without its frustrations for me. But there was no better feeling than like banging your head proverbial against the wall for some number of hours, even days, trying to fix a bug, a mistake in your code. And then, oh my God, the rush of emotion of accomplishment of pride of exhaustion when you finally solve some problem that's really been weighing on you. It's just so incredibly gratifying but also empowering. 

Because unlike a lot of fields, like computer science was built by humans themselves. And so if a human built this, surely, you, another human, can understand it as well. And so even though there's going to be some distractions along the way, you're going to see what looks incredibly cryptic, if you've never programmed before. Over time and with practice, everything just starts to make more sense. And with time and with practice, you just get better at this particular field. 

And indeed, really, the key to success in programming in general is just to allow yourself enough time. And so at least, thankfully, I quickly got into the habit of starting early in the week, for instance, when writing actual code. Why? Because you're going to run up against a wall. You're not going to see some bug. Something's not going to jump out at you, and that's fine. That's when you call it a day, take a break, move onto something else, and then just come back to it. And that's what keeps programming fun for me, even all of these years later, whether it's teaching or actually applying it. 

But there's, down the road, a history of an MIT hack, and it looked a little something like this, in yesteryear. And there was a little sigh the MIT students, when they made this hack. On the wall it says, getting an education from MIT is like drinking from a fire hose, which indeed they have connected to what should have been otherwise just a water fountain. And that's going to be what it feels like, sometimes, not just in computer science per se, but just an unfamiliar field. 

If you're not from STEM, if you're not from CS, that's fine. But so much of it, ultimately, is going to be absorbed by you and going to be within your grasp by terms end. So just keep in mind, that's very much the intent, but you'll be amazed what you're able to create, to accomplish, just three or so months hence. Indeed, 2/3 of you, contrary to what you might think are assume, have never taken a CS class before. So it's absolutely not the case that the person to the left or the right surely must know more than you. Indeed, it's quite the opposite. 

And as you'll see in the coming weeks, as you write your own code and solve your own problems, what ultimately matters in this course is not so much where you end up relative to your classmates but where you end up relative to yourself when you began. And it really is all about that delta, whether you've programmed or not, just getting something out of a class like this. And if it does take time, and if you do feel those frustrations, but you simultaneously eventually feel that sense of accomplishment, that just means it's all working. And indeed, hopefully, all the more worthwhile and gratifying, ultimately, as a result. 

So what are we going to do in the coming weeks? So here we are in week zero. We'll soon see why computers and computer scientists start counting, if you will, from 0. But week 0, is one in which we explore computational thinking, thinking like a computer, and starting to clean up your thought processes. Getting you to think, to solve problems more methodically, and then ultimately, translating that into code. 

And some of you might recognize this environment here, a.k.a. Scratch, coincidentally also from MIT. You might have used it in grade school. We'll use it today and a little bit this weekend in the course's first homework assignment or problem set. But not so much to play around in a way that you might have if you did use it in yesteryears, but to explore ideas of computer science and programming that we're going to use and reuse every week hereafter as well. 

Thereafter, we're going to transition just next week to week one, so to speak. Whereby, we'll introduce you to a more traditional language, a lower level language, an older language called C. And in C, you're going to use your keyboard, not so much your mouse and pointing and clicking, but you're going to write code that soon is going to look a little something like this. And if you've programmed before, you can probably glean what this is going to do. If you've never programmed before, which is the case for most of you, this too will soon make sense. 

But this is the most canonical program that most any programmer ever writes called Hello, World, and indeed, that and all of the surrounding syntax above and below just that sentence Hello, World, will soon make all the more sense. 

You'll learn how to use industry-standard tools, so to speak. Pictured here is something called Visual Studio code, or VS Code. You'll use a cloud based version of it initially, so you don't have to suffer with any technical difficulties or headaches like that. It'll just work right off the bat, but we'll use that to [INAUDIBLE] others ultimately to then explore ideas in computer science, principles that you can apply. And we'll take a look underneath the hood, so to speak, of your computer at your memory or RAM, Random Access Memory, where all of the data is ultimately going to be stored. 

We'll also take a look thereafter at bugs. A bug is a mistake in a program. Here is an actual bug in an actual computer in yesteryear, but we'll teach you how to debug programs, find your own mistakes, find others' mistakes, and improve that code as well. We'll transition then to algorithms, step-by-step instructions for solving some problems, which we'll touch on today too. And if you picture here, this is actually a pretty representative problem. Odds are, you haven't had to deal with something like this, but it's representative sorting, for instance. 

If you think of each of these small bars as being a small number, each of the bigger bars is being a bigger number, you might wonder, well, how could you as a human sort all of these bars, like get all the short bars over here, all the big bars over there? Well, odds are, if you're like me, you would probably kind of eyeball it, and if you could physically interact, you might just start grabbing the smallest elements first, put them over on the left. Maybe grab the biggest elements, put them over on the right. 

But what's your algorithm there? Like how would you teach someone younger than you, who's never done that before, how to do it? How would you compel your Mac or PC or phone to do something like that? You can't just wave your hand, and say, oh, figure it out. Move things around. You have to express yourself more methodically. So we'll translate even ideas like this into code too. And that's what the Googles and others of the world are doing constantly, as they sort and organize the world's information. 

We'll use metaphors along the way, if it helps. We'll talk about your computer's memory as being like a postal address. Like every mailbox in the world has some form of postal address, street, city, state, country, and the like, and it turns out, that's how your Mac, your PC, and your phone also work. You've got a whole bunch of memory, like the picture before, but you can think of it really as individual mailboxes. 

And you can put anything you want in those mailboxes, and you can go to a mailbox to grab information that's from it. So at the end of the day, that's really all your computer is doing with information. It's just organizing it, not into mailboxes per se, but a term you probably know called bytes, for instance, instead. 

We'll talk about problems that arise even nowadays. In fact, most of you are familiar with your Mac, PC, even phone like spontaneously rebooting sometimes, crashing, the little annoying spinning beach ball or hourglass icon that happens. Like what is with that? Well, those are just bugs in programs that humans at Apple and Google and Microsoft and others, they screwed up, and they wrote buggy code. And your computer, when it encounters those mistakes, doesn't know what to do. And so 9 times out of 10, so to speak, it just crashes or freezes or the like, but that kind of stuff will make more sense. 

So even the real world will make sense, and pictured here are some lower level terms we'll eventually get to mid-semester. But generally speaking, when something is going this way, as per this arrow, and something is going this way, as per this arrow, like that does not end well. And that often is what happens when your computer crashes. Someone's using memory up here, but someone else is using memory down here, and then they're not really talking left hand and right hand. So that is just a high level overview of some of the problems we'll encounter, but we'll focus to on data, ultimately. 

So pictured here is something fairly technical called a hash table. It's an amalgam of something we're going to soon call an array and also something we call a link to list. And these are just fancy terms for describing how you can organize information even more flexibly than just putting individual values in mailboxes. Like how could you build structures, like actual data structures so to speak, two-dimensional structures at that? 

And so what you're seeing here is a glimpse, as some of you might have recognized, of some Harry Potter universe names, but they're organized somewhat alphabetically. And notice, that any time there's multiple people with a name that starts with H, like Hermione, Harry, and Hagrid, well, they can't all fit in that mailbox, if each of these squares along the left is that same mailbox. So you have to chain them together. 

Well, you'll learn how to do that in code. So that even if you get more data than you expect, if your business is booming, and you're some web-based business, how do you keep adding and adding information to your software to actually keep up with it? But this, again, is what code's going to soon look like, as soon as next week, in week one, this here being C, but we'll transition in a few weeks to a more modern, higher level language, so to speak, called Python. 

Indeed, the course very deliberately, back in my day and now this, introduces you first to C, which funny enough, many people don't tend to program in certainly every day. I use C, generally, September, October, November, December, when teaching CS50 itself. But it's everywhere, nonetheless. 

In fact, even today's other languages, with which you might be familiar, like Python and Java and yet others still, you see this same primitive language underneath the hood, because it's so darn fast. And as you'll learn over the coming weeks, it really gives you access to and an understanding of what's going on conceptually down here. So that thereafter, after CS50, when you're writing code, you can think at a very high level what's actually going on. So in fact, in just a few weeks, what looks like this in C is going to look instead like this in Python. And you'll better understand what's going on underneath the hood, and odds are, after this class, you'll reach for a language, like Python more frequently than C, but you're going to benefit from that bottom-up understanding thereof. 

Thereafter and towards term's end, we'll introduce you to a few other ideas, like where do you put large amounts of data? In things called databases, not things like spreadsheets, like here, but actual databases. We're using those same kinds of data structures, you lay things out in an interesting way in memory. Thereafter, we'll transition to a very familiar environment that you and I use every day, the web. Like the web has become rather the User Interface, or UI, that we use everywhere, on the laptops, desktops, and even mobile devices, nowadays. 

Well, pictured here is a language called HTML. It's not a programming language. It's a markup language, and some of you might have made home pages or portfolios in the past. But you'll understand what's going on here, but more powerfully, you'll understand how the computer sees that same kind of code, builds up a hierarchical family tree-type structure in memory. And then you can manipulate that tree with code to actually add more and more information, chat messages, anything on the screen that you like. 

And finally, we'll tie all of this together by introducing what are called frameworks and libraries, third-party code that makes it a lot easier to solve problems of interest to you. And so in particular, here, this is the very first web app that I myself made back in like 1997. I was part of the first-year intramural sports program, not as an athlete but as the programmer, and I was teaching myself how to build web applications. I only knew C and maybe a little bit of something else at the time. 

But this became, for Harvard at least, the very first website for the first-year intramural sports program, and it wasn't just a static website with links and images and the like. It was interactive. You could register for sports. We could input exactly who was in a tournament bracket or the like, and it could actually automatically keep track of this data. So there too, after just three months of a class like this, you'll go from writing quite simply this week and next Hello, World to building things like this for whether it's web, mobile, or other platforms as well, if you so choose. 

But we'll get you off of the course's infrastructure, by the end of the term. You won't be using any toy environments along the way. We'll empower you, ultimately, to write code after CS50, especially if this is the only CS class you ever take, on your own Mac or PC, using the same software, but not the cloud-based version thereof. But all of this software is itself free and can be used by you powerfully after the course's own end. 

But along the way, as you may know, there is this tradition within the class, particularly in healthy times, of a number of events that really brings people get together, not just collaboratively and academically, but to just solve problems and generally engage with each other as well. Coming up first, CS50 Puzzle Day, which is meant to be not jigsaw puzzles but logic puzzles that require no prior experience with computer science or programming. But it's just an opportunity to quietly work on a packet of puzzles with some number of friends for prizes and more. 

Later in the semester, once you tackle your final projects, the capstone of the course, where we don't give you a homework to write, you yourself come up with something to build. We'll get together generally around 7:00 PM in the evening, wrap up around 7:00 AM, if you so choose. And it's an evening, a 12-hour opportunity to collaborate with classmates on your very own final project, in a large space on campus, that ends-- if you're awake with us-- at 5:00 AM. We can hop on some CS50 shuttles and go down the road for some pancakes at IHOP around 6:00. 

Of course-- of course, this is 6:00, 7:00 AM at that point, but it's an opportunity finally to lead into what's called the CS50 fair, which is an end of semester celebration, an exhibition, of everything that you'll accomplish over the coming months. And in fact, pictured here are some of your predecessors in healthy times. The CS50 fair allows you to come with your laptop or phone and exhibits of students, faculty, and staff across campus put together something in person and on video that people can delight in seeing, as you exhibit what it is you created and what you learned over the course of the several weeks. And ultimately, a chance to just share and inspire others as well. And you'll all walk home, ultimately, with your own I took CS50 T-shirts saying as much as well. 

So with that high level overview of the course, I propose that we begin to take a look at what computer science itself is and what it is we're going to be doing over the next several weeks at this lower level [INAUDIBLE] too. So what is computer science? Right? If you're maybe like me or new people like my friends in high school, you probably assume that it means programming. And that's absolutely a big part of it for a lot of people, because with code, you can write, you can express ideas, and solve actual problems, especially involving data. 

But computer science itself is really the study of information, if you will. How do you represent it, and how do you actually process it? And in that sense, computational thinking is just the application of ideas from computer science, a course like this, to problems of interest to you, again, in the arts, humanities, sciences, social sciences, whatever the domain of interest is to you. 

So with that, if computer science is all about information and with it the solving of problems, well, what does it actually mean to solve a problem? Let's see if we can't propose a model into which all of the lessons learned will ultimately follow. And I'd propose that this is problem solving. 

You've got some input, which is like the problem you want to solve. The goal is to solve it. So that's the so-called output, and then somewhere in here, the proverbial black box, is some kind of secret sauce that gets the work done. And in the coming months, we'll have to decide, well, how are we going to represent these inputs and outputs, and really, how do we code up? How do we write solutions for what it is that's solving the problem of interest to us? 

So when it comes to representation of information, like there's a lot of ways we can do this. And for instance, if the problem at hand quite simply is to take attendance at the beginning of class, on the first day of school, well, how could we go about doing this? Well, we could actually use a system called unary. 

Well, what is that? Well, that's a fancy way of saying 1, 2, 3, 4, 5, maybe 6, 7, 8, 9, 10. And I can use my digits-- pun intended-- on my fingers to actually count everyone up. And eventually, you need toes and whatnots, if you have to count so high. But unary is a very simple system of using a single symbol, a human finger in this case, to just solve some problem, like counting the number of people in the room. 

Let's make this slightly more technical for a moment, a little more mathy. That's just called base-1, where the base under which you're operating has one digit in it, like literally a human finger, and maybe multiple such fingers, if you need to count higher. But of course, most of you, if not all of you, generally, vaguely know that computers use something other than unary-- and even you and I probably don't use this that often-- they use what language or alphabet instead. 

Yeah. So binary, so binary is indeed the system that computers somehow use. So in this case, bi implying two, and so computers have two digits, it turns out, at their disposal. And in fact, if you've ever heard the technical term bit, which is like a smaller version of a byte-- more on that soon. Well, a binary digit is the origin of that term "Bit," because if you get rid of some of the letters, and are left from binary digit with just B-I-T, thus is a bit. 

A bit is just a 0 and 1. It's two more digits than you might have on your own finger, and of course, it's fewer though than you and I have. You and I typically use, as humans, the decimal system. Dec meaning 10, because you and I generally use 0 through 9. 

So on the one hand-- another pun intended-- you've got unary. Computers use binary. We humans generally think and talk in terms of decimal. But at the end of the day, these are fundamentally going to be the same thing, which is to say that it's all pretty accessible to us. Even if you're not a computer person, I daresay you're about to be. 

So what is a bit? Well, a bit then is a 0 or a 1. That is a so-called binary digit. But how do computers only speak in binary? How do they solve problems, represent information, using only binary? Well, at the end of the day, if they want to represent 0 and 1, we need to do so physically somehow. And I daresay that maybe the simplest way to think about a bit, a 0 or a 1, is like a light bulb. 

And so by human convention, let's just assume that if you were a computer, be it a laptop, desktop, phone, or the like, and you want to represent the number 0, you know what, you just keep the light switch off. You keep a light bulb off. If by contrast, you're that same computer, and you want to represent the number 1, you take that same switch, that same light bulb, and just turn it on. So a light bulb that's on represents a 1, and a light bulb that's off represents a 0. 

So why is this relevant to computers? Well, at the end of the day, you and I are charging our laptops or phones at night. So there's some physical resource being replenished there, whether you're on battery or some power cord. 

And so inside of a computer are just thousands, millions of tiny little switches, nowadays. You can think of them metaphorically as light bulbs, but they don't actually shine light. But there are tiny, tiny little switches, and those switches, if you've ever heard the term, are just called transistors. 

So like computers have millions of transistors that can either be flipped on to represent 1's or flipped off to represent 0's. And from that very simple mechanism, electricity is there, or it's not, a 1 or a 0. Computers can actually count, obviously, from 0 to 1, but it turns out, even higher, if they use a little more electricity as well. 

So how might I do this? Well, let me go ahead and propose that I just grab one of our own light bulbs here on stage. This one is off. So for instance, if this were miniaturized inside of your Mac, PC, or phone, this would be a transistor, and indeed, here's the little switch on the bottom. 

And if your computer wants to represent a 0, it just leaves the switch off, and the light is not shining. If you want to represent a 1, well now, I've counted as high as 1, because the switch is now on. I've grabbed a little electricity. I'm holding on to it inside of the computer, and so now I see that this is a 1. 

All right, but unfortunately, with just one switch, one light bulb, I can only count from 0 to 1. How do I count out higher, might you think, intuitively? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Say it again. 

AUDIENCE: More lightbulbs. 

DAVID J. MALAN: Yeah, so more light bulbs. So let me do this. Let me just grab something to put these on, so I can use a few of them at a time. And let me propose that here, instead of having just one light bulb, let me give myself maybe three in total. 

So all of them are initially off, and if you think of this in miniature form, in your mind's eye, this is like a computer with three transistors. Three switches representing now the number you and I know as 0. Why? They're just all off. 

So how does a computer go about representing the number 1? Well, it turns on one of these light bulbs. And how does the computer represent the number 2? Well, you might think, if I may, you just turn on a second light bulb. 

And if you might think, how does a computer represent 3? You just turn on the third light bulb. And so as such, with three bits, a computer would seem to be able to count from 0 on up to 1, 2, 3. 

But it turns out, if I'm a little smarter here, I can actually count higher than that. Why? Well, I'm just considering the combination of bulbs being on here. What if I do something like this? This is still 0, I will claim, but what if I propose now that this will be how a computer represents 1-- on, off, off. 

This, though, will be how the computer represents 2. Notice, I didn't turn on the same two. I'm just turning on the one in the middle. This I now claim will be how a computer represents 3. This is going to be-- in just a second-- how a computer represents the number we know as 4, and yet, I'm still only using three bulbs. 

This is going to be the number the computer represents as 5. This is going to be how the computer represents the number 6, and then lastly, it turns out, with three light bulbs, if you're smart about it, you can count it seems as high as 7. Now, even if you lost track of what I was turning on and why, I claim there were eight different patterns, from all of them off to all of them on. But notice that I started to permute them. I took into account which ones were on and which ones were off. 

Why, though, do these represent the numbers we know as 0 through 7? Well, let me go ahead, and maybe let's do this. Instead of just considering there to be light bulbs, let's assign some special significance to each of them, based on where it is. And maybe for this, could we get maybe three volunteers, three volunteer? 

OK. You're being volunteered. OK. Come on up. If you want to go over to the stage there. Yeah. You want to come on up as well, and over here as well. So there are some stairs on either end. Maybe a round of applause for our first volunteers of term. 

[APPLAUSE] 

All right. So you want to be our number 1, and if you want to go ahead and stand roughly right here. How about do you want to be number 2? 

AUDIENCE: Yeah. 

DAVID J. MALAN: Come on over right to the right of here, and you'll be number 4, it turns out. If you want to come over here, on this end, let's give you all a moment to introduce yourselves briefly to your classmates, if you'd like. 

AUDIENCE: Hi. I'm Ellie. I'm a senior. 

DAVID J. MALAN: Nice to meet. 

AUDIENCE: I'm [? Rayhanna, ?] and I'm a first year. 

DAVID J. MALAN: Welcome. 

AUDIENCE: Hi. I'm Joseph, and I am a first year. 

DAVID J. MALAN: Welcome. All right. So so glad to have all three of you up here. Thank you. 

[APPLAUSE] 

Let me propose now that we'd like you three to represent how about the number 0. And I claim now that if each of you now represents a switch, you have fancier light bulbs now. One is a 1. One is a 2. One is a 4, but each of you is still just has a switch on the bottom, in fact, of your plastic devices. 

I claim these three volunteers are representing the number 0. Let me ask you all now, how might you represent the number 1? How should you cooperate here? OK. So we would have on, off, off, which I think matches what I did with my three light bulbs as well, if you want to go and turn yours off. 

How might you three represent the number 2? OK, so off, on, off now, from right to left. How would you three represent the number 3? Ah, so that's why my two light bulbs went on at the end. 

How would you three represent the number 4? Perfect. Number 5, number 6, and number 7? All right, and give us one more. How would you represent 8? 

AUDIENCE: We can't. 

DAVID J. MALAN: OK. You can't. How about then one more volunteer, one more volunteer? OK. Come on up. All right. What's your name? 

AUDIENCE: My name is [? Moin. ?] 

DAVID J. MALAN: If you want to say it into there. 

AUDIENCE: My name is [? Moin. ?] 

DAVID J. MALAN: All right, [? and Moin, ?] you're going to be number 8, and if now you all-- actually, let's make this how would you represent number 8, all collectively, as 4 bits or for switches? OK, 8, and now lastly, give me 15. Everyone's awkwardly doing arithmetic in their head, oh, using unary. Yeah. Is that everyone-- Yes. OK. Round of applause. OK. Thank you all. 

If you want to leave your numbers over here, we have a CS50 stress ball for you, but thank you for volunteering. You can turn those numbers off and leave them over here. So thank you. 

So how do we go about-- how do we go from there to creating these patterns? Well, even though we still had three bits, initially, and three switches, later four bits and four switches, ultimately, we still used the same approach fundamentally to actually representing information. 

And now why were they those patterns, and why did I very deliberately have our volunteers line up in that way? Well, I wanted them using base-2, a.k.a. binary, but with binary there comes certain rules. And even if you're not familiar with binary beyond that it exists and relates somehow to computers, it's actually pretty much identical to the system you and I use every day, known as base 10, a.k.a. decimal. 

So let's consider, if you will, by rewinding to primary school for just a moment, like how decimal works. And you'll see that even if you're not a computer person, you actually are. You just have to tweak your mental model ever so slightly. 

So here is the number that you're probably viewing as 123, but why is that? Well, it's not really 123. This is just a pattern of three symbols on the screen, 1, 2, 3, and your mind is rapidly assigning mathematical meaning to them, 123, but why is that? Well, if you're like me, you probably learned back in the day, when you have a three-digit number like, this the rightmost number is in the 1's place, the middle digit is the 10's place, the leftmost digit is in the 100's place, and why is that relevant? Well, if you then quickly do some mental math, as you and I just do instantly nowadays, that just means 100 times 1 plus 10 times 2 plus 1 times 3, of course, 100 plus 20 plus 3 gives us the number you and I know as 123. 

But beyond that, how do we get to just two digits instead of as many as 9 in the decimal system? Well, let's generalize this. In the decimal system, you and I know, if we've got three digits represented by these hashes here, yes, it's the 1's place, 10's place, 100's place, and if we keep going 1,000's, 10,000's, and so forth, but why is that? 

Well, base terminology is now a little more germane. That's technically the 10 to the 0th column, the 10 to the 1, 10 to the 2. So these are powers of 10, where 10 is your base. 

Computers just simplify things a little bit, because computers, at the end of the day, only have access to electricity, on or off. They don't have access to 10 different types of electricity, just 2, on or off, if you will. Well, they just use a different base. 

And the rightmost digit would be in the so-called 2 to the 0ths. Then the middle digit is 2 to the 1. The left most is 2 to the 2, a.k.a. 1's place, 2's place, 4's place, and as we kept going, 8, and if we keep going, 16, 32, 64, 128, and so forth, but the idea is fundamentally the same. 

So why is this how the computer represents the number you and I know is 0? Well, off, off, off, from right to left or in this case left to right, is just 0. Why? Because that's 4 times 0 plus 2 times 0 plus 1 times 0 is, of course, 0. This is why 001 represents 1. This is why 010 represents 2 and 3 and 4 and 5 and 6 and 7 on up. 

And why did we need a 4th bit to represent 8? Well, we kind of needed to carry the 1, so to speak, using our familiar human terminology. But for that we need a 4th bit, another transistor, and this now represents the number 8. And that's why we ended with on-- from left to right-- off, off, off. 

So I keep saying on and off, or the light bulb is on or off, but really, I just mean 1 or 0. And so computers and we humans think of things digitally as just being 0's and 1's, but mechanically, you can think of it indeed is these light bulbs. 

Now, a bit is not very useful. Even 3 bits, 4 bits, not that useful. You can count to 7 or 15, generally speaking, bytes are a more useful unit of measure. 

And anyone familiar how many bits is in a byte? Yeah. So 8 bits are in a byte. You can think of it as an octet equivalently. In some contexts, there are nuances there, but think of a byte as just being 8 bits, and that's just a more useful measure. 

So what does this mean in real terms? So if you've ever downloaded like a music file or a photograph or a video, those are measured in bytes. Probably not small numbers of bytes, probably kilobytes for thousands of bytes, megabytes for millions of bytes, gigabytes for billions of bytes, especially for video. That just means you have a lot of patterns of 8 bits, some combination of 0's and 1's on your computer's hard drive. 

Here then, with a byte of bits, 8 bits, is how a computer would typically represent the number 0. And if that same computer uses all 8 of its bits, its full byte, to change it to 1-- anyone who's quick with math or have seen this before, how high can a computer count with 8 bits or 1? 

[INTERPOSING VOICES] 

Yeah, 255. Why is that? Well, we're not going to turn this into a constant math exercise. Indeed, after today, we're not really going to think about or talk about bits at this low level. But this is the 1's place, 2's, 4's, 8s, 16, 32, 64, 128, and if I do all of that math from left to right, that indeed gives me 255. It ignores how we might represent negative numbers, but perhaps more on those some other day. 

But computers, of course, do so much more than numbers and math and all this low level stuff. We send text messages, write documents, emails, and the like. So how might a computer represent something like the letter A? I claim, at the end of the day, your Mac, your PC, your phone just has lots of transistors, lots of switches that it can use in units of 8, in units of bytes. 

How, though, if it's already using those patterns of 0's and 1's apparently to represent numbers from 0 on up, how do you go about representing letters of the alphabet, might you think? Yeah? OK. So we could assign a number to every letter. OK. So let me just conjecture, well, let's just call A 0, for simplicity, B 1, C 2, and now let me play devil's advocate. OK, how do I now represent 0 or 1 or 2? 

Well, we've maybe created a problem for ourselves, if now we have to steal some numbers to represent letters. We kind of have to pick a lane, but there's a solution to that too that we'll see. And it turns out the world is not quite as simple as A being 0. A typically is represented, by computers everywhere, phones everywhere, with the number 65, the decimal number 65. Using 8 bits, if we turn some of the 0's to 1's, let me just stipulate, you can represent the letter A using 8 bits, by turning certain ones on and certain ones off, but we will try not to focus on that binary level too much. 

So if A is 65, it turns out that B is going to be 66, and C is going to be 67, and so forth, and so where does that get us? Well, it turns out there's a whole system that maps numbers to letters. And here, as I alluded to verbally a moment ago, is the pattern of 0's and 1's via which you'd represent 65. 

And just quick check here, we won't constantly do math 1's place, that's easy, 2's, 4's, 8's, 16's, 32's, 64's place. So 64 plus 1 gives us 65. So once I do that, how do I get to all of the others? 

Well, it turns out a bunch of Americans years ago came up with this ASCII, the American Standard Code for Information Interchange. Now, what does that mean? Well, it's just an acronym describing what really you proposed, a mapping between numbers and letters, not quite as simple as 0, 1, 2. Starts at 65, 66, 67 for capital letters, but here are most of the letters in use today, at least with this system. 

So this is just a big chart from online, and you'll see in the middle of this chart, here, here's my 65, A. Here's my 66, B, C, and let's see, 72 is H, 73 is I, and so forth. So there's a mapping, at least for English, between all of these numbers and all of these letters. And if we focus here, those are the beginning of our uppercase alphabet. 

So suppose then that today, tomorrow, you receive a text message from someone, and underneath the hood, now that you're a computer person, you figure out a way to see what pattern of 0's and 1's was sent. In this case, it's wireless as opposed to wired, but it's still some pattern of 0's and 1's. And your phone is turning some switches of its own on and off to represent that message from a friend. 

Suppose that the three patterns you received were these three bytes, from left to right, spelling out a three-letter word. Well, if we do out the math, 1's place, 2's place, and so forth-- I'll spoil it for you. Suppose that you received a text message that doesn't literally say 72, 73, 33, but you've received a pattern of 8 plus 8 plus 8, 24 bits that if you do out the math represent the decimal number 72, 73, 33. Anyone recall what message you might have received from the green and white charts? Yeah? 

AUDIENCE: Hi. 

DAVID J. MALAN: Hi. Yes, hi is the message, but 72, 73 gives us H and I. What's 33? Any guesses to 33? Yeah, over here. 

Yeah. So it's an exclamation point. How would you know that? Well, you really do need some kind of cheat sheet, a.k.a. ASCII in this case. And if we look elsewhere-- let me highlight the left of the chart-- you can see that next to 33 in decimal is indeed the exclamation point. 

So back in the day, a bunch of humans got in a room, decided that, hey, when we start building PCs and later Macs and phones, we all just have to agree on this form of representation of letters of the English alphabet, in this case. We just need to agree on this mapping. 

But somewhat curiously, notice this. It turns out that, once you paint yourself into this corner and start using 65 for A, 66 for B, well, how do you represent 65 the number and 66 the number, if you want to do math or use Excel or something like that? Does anyone see the solution, perhaps? How do you represent the number 1 in ASCII? Yeah, in the middle? 

AUDIENCE: [INAUDIBLE]. 

DAVID J. MALAN: Yeah. So this is getting a little maybe inception or something, but you could represent numbers with other numbers. And so if you want to represent the number you and I know as 1, like when you type it on your keyboard, turns out the computer stores that as the decimal number 49. If you hit 2 on your keyboard, the computer is not storing 2, per se. It's storing the decimal number 50. 

Now, thankfully, the paradox stops there. We just have a mapping now of numbers to numbers. But really, at the end of the day-- and you're going to learn this when we start writing code in that other language, C, next week-- it's just context-dependent, at the end of the day. 

Inside of your Mac, PC, and phone, there's just all of these permutations of bits, all of these patterns of 0's and 1's. And generally speaking, when you open up a text message that you've received from someone, it's 0's and 1's. But obviously, if it's a text message, the whole point of text messages is to send text, and so those patterns of 0's and 1's, by default, will typically be interpreted as letters of the alphabet. 

So you won't see 0's and 1's. You won't see decimal numbers. You'll see the English message that your friend intended. 

By contrast, if you open up something like Excel, that same pattern 0's zeros and 1's might indeed work out to be 72, 73, 33. You might see cells in your spreadsheet with literally those three numbers. Why? Because spreadsheets are all about numbers and number crunching and math, in many cases. 

If by contrast, you open up Photoshop and try to look at that same pattern of 0's and 1's, it's not going to be 72, 73, 33. It's not going to be 0's and 1's. It's not going to be hi. It's going to be some color of the rainbow. You're going to use those patterns of 0's and 1's, it turns out too, to represent colors. 

And indeed, so long as you and I just agree, as humans long have, what these patterns are going to be, all of our systems, many of our systems nowadays are indeed interoperable. But I'm being very biased here, and indeed, the A and ASCII is very American-centric. What do you not see in this chart? If you speak any other language than English, odds are, you're not seeing characters you know and love and need every day to type or send messages. 

Well, there's a huge character set that's not supported here, whether it's accented characters and a lot of Asian alphabets. You have many more symbols than can fit even on this screen here. And so humans kind of painted themselves into a corner, early on, or really, Americans did. But on a typical keyboard, US English keyboard, yeah, you have A's and B's and C's, uppercase and lowercase, but you also have accented characters here. 

And nowadays, not sure if this is maybe necessary, but nowadays, you have other characters on your keyboard, like these. And these are a playful incarnation of what's actually a technical solution to this problem. If I claim for the moment that ASCII historically used 7 bits to represent letters-- and let's just round that up to a byte-- 8 bits to represent letters, ASCII can represent as many as 255, or really 256, total characters. 

Why 256? Well, if you have them all 0, that's 0, and the highest number I claimed a moment ago was 255. So that's 256 total possibilities. That's not many letters. It's fine for English, but not a lot of human languages. 

So what might the intuitive solution be, if you want to represent accented characters, Asian characters, emoji, even like these, which are just keys on a keyboard nowadays? What's the intuitive solution, if a byte's too few? Yeah? 

AUDIENCE: Add another digit. 

DAVID J. MALAN: Yeah. So add another digit. Just like we had a 4th volunteer come on up to give us a 4th bid, let's just throw hardware at the problem and use a few more bits. So maybe instead of 1 byte, let's use 2, or heck, let's use 3 or 4 bytes. Even though it's getting a little expensive-- we're going from 8 to 16 to 24 or 32 bits-- that's how computers do things, these days. And thankfully, we have so much memory inside of our computers and phones, we can certainly spare a few to represent these things. 

And the solution then to ASCII is what we'll call Unicode. So Unicode is also just a mapping of numbers to letters but in many different languages. And indeed, the Unicode Consortium is a bunch of people from all different companies-- a lot of different companies and countries and cultures whose mission, as an organization, is to capture digitally all forms of human language in this case. And to ensure that especially smaller demographics of humans speaking lesser-known languages are nonetheless represented and preserved digitally using some mapping of these 0's and 1's. 

It turns out, though, if you start using 32 bits, as many as 32 bits, to represent characters on a keyboard, that's 4 billion possible permutations of 0's and 1's. That's way more than we need for most human languages. So there's a little bit of room in there for some of those more playful things, like those emoji. 

So for instance, suppose you got a text message with this pattern of 0's and 1's. Or if we do out the math, suppose you receive a text message that, if you do out the math in decimal, is 4,036,991,106. Anyone know what emoji you're looking at? It would be weird if you do, but what is this? 

Well, it turns out that, as of this past year, this is the most popular emoji to be sent by many measures, Face with Tears of Joy. So that is the pattern that a bunch of humans in the Unicode Consortium decided would represent this. But you'll notice, many of you might have iPhones, some of you might have Android devices too, and sometimes, these don't actually look quite the same. This happens to be the current version of Face with Tears of Joy on iOS. 

On Android, it tends to look a little something more like this, and here is kind of a curiosity. Even though you and I look at these things and they look like images, they're not images. They're characters, at least as we've defined them now in Unicode. And iOS and Android and Windows and Facebook and other companies and apps, nowadays, really just have different fonts, if you will. 

So just like fonts with English and other languages can give you different characters with serifs or not, emoji are themselves, yes, drawings that someone made, but they're really just a font. And so that same pattern of 0's and 1's might just render slightly differently on someone's phone or another. If you've ever gotten like an icon on your phone that's broken, and you've been sent an emoji, but it's like a square or something arbitrary and not sensible, it might just mean that you have not updated to the latest version of iOS or Android, which just updates the font of supported emoji. Because those folks at Unicode, pretty much every year nowadays, are adding more and more emoji to that particular character set. 

Now, I went down the rabbit hole of figuring out the other day just which are the most popular emoji these days. On Twitter specifically, this past year, the most popular emoji, by contrast, was Loudly Crying Face. I don't know if that says more about 2021 or about Twitter, but you'll see different trends, certainly, in how these are used. 

But even humans themselves didn't necessarily think two steps ahead, and now a lot of the emoji are the default yellow color. But there's a lot of emoji that aren't these cartoon characters, but they're meant to represent humans in various professions or gestures or the like. And nowadays too, you've probably noticed on your phone and Macs and PCs, there are different skin tones that you can assign to certain emojis. If it's supported by the company and by Unicode, you can actually touch and hold on a certain emoji, and then you can choose the appropriate skin tone to represent yourself or someone else. And that then modifies the display. 

Well, let's just think for a moment here, how did Apple and Google and Microsoft and others go about implementing support for emoji with different skin tones? How could you do this? If you want to represent some smiling emoji but in five, in this case, different skin tones, you could come up with what? Five different patterns that are identical, structurally, except for the skin tone used in places in that image. 

But that's a little inefficient to just do copy, paste, paste, paste, paste, and change the color in Photoshop, if you will. That's going to use more bits, more information than you might need to. How else, if you now start to think a little bit more like a computer scientist, if at the end of the day, all you have are 0's and 1's, how else could you implement skin tones, might you think? Yeah? 

AUDIENCE: RGB. 

DAVID J. MALAN: OK. So RGB, we'll come to that in just a moment. That stands for Red, Green, Blue. That's one way. In this case, though, I'm seeking an alternative to just using five different patterns of 0's and 1's to represent the same emoji but different skin tones. So not quite RGB. Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: OK. So store one copy of the emoji and then store different variants of the color that you want to assign to that emoji. Yeah. So this is actually an example of-- do you want to elaborate? 

AUDIENCE: You could use a loop. 

DAVID J. MALAN: OK. So you can use a loop to actually output these things. More on that in a moment. Let me go down this road for just a moment. This would be in some sense a better design, if you will, but why? Yeah? 

AUDIENCE: A filter? 

DAVID J. MALAN: OK. So filter, if we think of in the Instagram sense. You can change the color of something, and that could be related here too. 

AUDIENCE: Could it be another font [INAUDIBLE] 

DAVID J. MALAN: Oh, interesting. So maybe it could be just a completely different font. And you have five different fonts that are almost identical, except for the various interpretations of skin tone for those same emoji. 

Let me spoil. I think if we go down this one particular road, the way the Unicode folks decided to do this some years ago where the first byte or bytes that you receive via text or email just represent like the structure of the emoji, the default yellow version, thereof. But if it's immediately followed by a certain pattern of bits that these humans standardize to represent each of these different shades of skin tone, then the phone, the Mac, the PC will change that default color, yellow in most cases, to whatever the more apt human tone is. 

So you just use twice as many bits, but you don't use five times as many bits. So what do I mean? You don't have five completely distinct patterns, per se. For each of these possible variants, you have a representation of just the emoji itself, structurally, and then reusable patterns for those five skin tones. 

Unfortunately, that wasn't quite versatile enough for other features that were in the pipeline, and nowadays too, and there's a double meaning now to representation. Emojis intended to focus on certain professions, and early on too, were certain professions associated with certain genders and vice versa. And you couldn't necessarily be one gender or another, in a certain profession or another. There were these combinatorics that just weren't possible. 

But nowadays, as you might have seen, you can have couples in love for instance that actually look a little more like three emojis, but just kind of combined into one. And indeed, this is just one key press on your phone, and you can combine different emoji on the left and then the right with the emoji in the middle. And so it turns out how computers nowadays represent these patterns are one set of bits for the character on the left, one set of bits for a character on the right, one set of bits for whatever emoji you want in the middle. And then you assemble more complicated compositions of emoji by just reusing those same patterns and bits and bits. 

The Unicode folks don't have to come up with a whole new representation for some very specific incarnation. They can create one for person, for male, for, female for other characters that you might want to display, and reuse those same patterns of 0's and 1's. And so here, you see the imperfection, of or lack of foresight, of humans for building a system early on that was entirely American-centric, no characters, emoji, or the like, that's evolved too. And so that's an important detail in computing, nowadays. It too is evolving, and the languages you're about to learn in the coming days, those too are evolving as well. 

And new features are getting added, and even programming languages have version numbers. You might have a different version of an app on your phone. Programming languages too have different versions as well. Questions then thus far on how information is represented using ASCII or Unicode or anything in between? 

Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Oh, good question. So to recap, why can't you just-- well, let me summarize that as why can't you similarly use different patterns to change the context of what these patterns of bits represent, whether it's a number or a letter or a graphic? In actuality, that's kind of what's happening underneath the hood. It's not standardized in quite the same way, but starting next week, when we transition from scratch to C, you'll learn about types, data types. Where the onus initially is going to be on you, the programmer, to tell the program whether or not this pattern of bits should be interpreted as a number or as a letter or as a color or something else. Nowadays, though, and toward the end of the semester, you'll use languages, like Python, where the computer just figures it out for you by context, which makes it even easier and faster to program as well. 

Other questions on Unicode, ASCII or the like? All right. Well, how about just a few other forms of information? RGB was called out earlier, Red, Green, Blue. How do images get represented in computers? 

Well, in fact, it's typically an assembly of some amount of red, some amount of green, some amount of blue, but there are other representations. If you're a graphic designer, you might know them, but RGB is still pretty common. What does this mean? This means to represent every dot on your phone or every dot on your TV or your laptop or desktop, there is a number representing how much red that dot should show, a number representing how much green, and a number representing how much blue it should show, red, green, blue, respectively. 

So for instance, if a dot on your screen were using these three numbers, these three values or bytes, 72, 73, 33, in a text message or email, that would be interpreted as I claimed "High." But in Photoshop or in some graphical program, that same pattern would be interpreted as let's call it a medium amount of red, a medium amount of green, and a little bit of blue. And why medium and little? 

Turns out, each of these are bytes, the smallest value you can have in a byte we said is 0. The largest value you can have a byte is 255, so I'm just kind of spitballing here. This is like medium, medium, and a low amount of red, green, blue, specifically. Those three colors, like wavelengths of light, are combined in such a way that you would have this dot on the screen, a sort of murky shade of yellow or brown. 

That is how a computer would store precisely that color, and in fact, we've seen this color. When you type in Face with Tears of Joy, generally, on your screen, it looks like this, typically much smaller. But let's zoom in, or let's Zoom in a little more. What are you starting to see, if you know the term? 

AUDIENCE: Pixels. 

DAVID J. MALAN: So pixels, it's getting very pixelated. A pixel is just a dot on the screen, and if you really zoom in on it, you can literally see all of the dots that compose an emoji, in this case on iOS, in the font that Apple is using to represent this particular pattern of 0's and 0's. So one of those yellow dots-- and there's many of them all kind of blend together here-- each dot on the screen I claim is 3 bytes. How much red, green, blue for this dot? How much red green blue for this dot? How much red green blue for this dot? 

And you'll notice too, that when it gets to be sort of brownish here, the dots really stand out. The 3 values, the 3 bytes, a.k.a. 24 bits, are just slightly different. And so underneath the hood, this is why images, photographs that you take or gif that you download, get so darn big, potentially, because you have a number representing every dot on the screen. 

Well, if this I claim is indeed how images are typically represented, using pattern of bits that are assigned to some amount of red, green, or blue, how do you get video? What is a video, if at the end of the day, all we have are 0's and 1's? What's a video, perhaps? Yeah? Let's go here, way in back. Yeah. Pixels really changing values over time. and do you want to confirm or deny, the hand that went up here? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, or equivalently, a sequence of images that, over time, are changing on the screen. So both of those are valid interpretations, and just for fun, if you grew up with these picture books, you might remember a little something like this. if we could dim the lights? 

[MUSIC PLAYING] 

So that's the old school analog way to implement a video, in the sense that that artist wrote out like hundreds of pieces of paper, with almost identical images, but where the ink from their pencil or pen was slightly moving. And if you digitize that, such that each of those strokes are represented with dots instead, that's really what you're seeing is a sequence of all of these images flying across the screen. And if we dive into the real world, if you've ever watched a film, a Hollywood movie is typically 24 FPS, Frames Per Second. That really means you're seeing 24 images per second, or on TV or in soap operas, it's often 30 frames per second. That makes things look a little more smooth. 

So it's not actual motion picture, if you will. It's sequences of pictures, and your brain and mind are interpolating that, oh, this is smooth movement, even though we're just seeing a lot of pictures really fast. Now, that gets really big, and we'll talk later in the semester how you can compress information, so that you're not using way more bits than you actually need to. And there's fancy algorithms that folks have developed, but at the end of the day, that's really all a video might be is a sequence of images. Conversely, if you want to represent the music that accompanies that or something else, if any of you play an instrument and can read sheet music, how could you digitize this? 

[PIANO MUSIC] 

Like how could you represent musical notes in a computer? You and I hear them when we play files, but what's really going on underneath the hood? Any musicians, piano players? Anyone? Yeah? 

AUDIENCE: Hertz value? 

DAVID J. MALAN: OK, so Hertz value, so some frequency. So sound is some frequency, and it's kind of hitting your eardrum. And that's what makes it sound low or high or somewhere in between. 

So maybe we could assign, just like there's letters A through G here, maybe we could assign specific frequency values, which are just going to be numbers measured in something called Hertz, something per second. And maybe we could have a few other numbers for each of these notes, not just the note or the frequency. Maybe, we could represent the loudness of it, like how hard or how softly a human might equivalently press it. Maybe a third number, like duration, like how long is there finger on the keyboard? 

So you can imagine quantifying something like music that in the real world is perfectly continuous as something more discrete, by representing each note over time as just some sequence of values. And there's so many different ways to do this, MIDI, if you've heard, mp3's, AAC. Almost all of the file extensions you see on your Mac or PC, if you see them at all, ultimately just mean there's a different form of representation for, in this case, something like sound. 

So let me just stipulate, there are these and many more ways to represent inputs and outputs, and thankfully, humans have standardized a lot of this. They don't always agree, and this is why we have different file formats for Apple numbers and Microsoft Excel and Google Spreadsheets and stupid incompatibilities like that. But generally speaking, humans have standardized how we represent the inputs and outputs to and from problems. 

But let's now focus on this Black box, so to speak, in the middle, this abstraction. So abstraction is technically a term that you'll see all over the place in computer science, and really, problem solving, that just refers to the simplification of something, so that you don't focus on the lower level implementation details. You really just focus on the high level goals or the process itself. 

Therefore, your car, if you have a license and have driven or have been in a car, a car, so far as you're concerned, is probably an abstraction. Most of us, if you're like me, probably don't really know or care how the engine works and all the parts that are moving. To you, it's just a way of getting from point A to point B. It's an abstraction, but someone, hopefully the mechanic, does know those lower level implementation details. 

If you had to understand how a car works every time you want to go to school or to the store, it's probably going to be a pretty slow process. You just want to think and operate at this higher level of abstraction, and we're going to do this all the time when writing code and solving problems. So what then is in this black box, this abstraction at the moment? Well, generally, it's what a computer scientist would call an algorithm, step-by-step instructions for solving some problem. 

Now, let's consider the implementation details, that is to say how you might solve certain problems, and let's take a old school example but in modern form. 

This icon, if you have an iPhone, is, of course for your contacts application. And if you've got a whole bunch of family members or friends or colleagues in your phonebook, you have some kind of contacts pictured here, and it's alphabetized typically by first name and last name. And odds are, you and I are in the habit, if they're not already a favorite, of like clicking on Search and then using autocomplete. 

And what happens when you start typing autocomplete? Well if you type in the letter H, you'll see only, presumably, Hagrid, Harry, Hermione, and so forth. If you type in H-A that shows you only Hagrid and Harry, and it all happens super fast. 

So how is that happening? Well, typically, you could just start at the top and look to the bottom, searching for all of the H's or all of the H-A's, but for larger data sets that's going to get slow. For the Googles of the world, that's going to get really slow. And even on our phones when you have hundreds, thousands of contacts, eventually, even that kind of approach, that algorithm step by step it might be slow. 

So how might we go about searching for someone in a phonebook like this, like say John Harvard? Well, here's an old school incarnation of this, and odds are, you might not have had occasion to even physically use this thing, nowadays. And in fact, this is a bit of a white lie, because this is the yellow pages, which means this is a book of companies not people. But this is all you can find, and at that, it's even hard to find this. But this is the same thing in analog form, physical form. 

So if I wanted to search for someone like John Harvard, how could I do that? Well, I could start on page 1, and I could start searching for page 2, page 3, page 4, page 5. A little hard to do physically, especially since no one's used this phone book in a lot of years. But is this algorithm correct, turning page by page, very inelegantly? Is this correct? 

Will I find John Harvard, if he's in here? All right. So yes. This is a little stupidly tedious, because if there's like 1,000 pages, he might be a few hundred pages into this, but it's correct. At some point, I will find him, and if he's on the page, I'll be able to call. Why? Because presumably, the names are alphabetized in here, and there's no cheat sheet on the edge. 

So I have to search for John Harvard from left to right, searching for H, if it's alphabetized by last name. Well, what would be marginally better? Well, how about two pages at a time? It's hard to do with a 20-year-old phone book, where the pages are grown together, but 2, 4, 6, 8, 10, 12. This algorithm, is this correct? 

AUDIENCE: No. 

DAVID J. MALAN: All right, so no. Why? 

AUDIENCE: You're skipping pages. 

DAVID J. MALAN: Yeah. So I'm skipping every other page. So if I don't consider that, and I find myself in like the I section or the J section, well, I might accidentally conclude, nope, I haven't found John Harvard yet, just because I skipped him, because it was sandwiched between two pages. Now, I can fix this, I think, if I do hit the I section, well, let me just double back one page, just in case he was in that last page. So it's recoverable, but it's almost twice as fast, minus that hiccup there. 

But what most of us would do, and what your phones are doing, albeit digitally, is they open up roughly to the middle of the phonebook. And they look down, and they say, oh, I'm in roughly the M section. So I'm roughly halfway through the 1,000-page phonebook. But what do I now know about John Harvard? Where is he, to my left or to my right? 

All right. So alphabetically, he's presumably to my left, and so here I can, both metaphorically and physically, tear the problem in half. You don't need to be impressed. It's really easy down the spine that way, but I know that John Harvard is to the left here. But now I can throw, unnecessarily dramatically, half and page one out of the way, and what do I now know? I've gone from 1,000 pages to like 500. 

I can repeat roughly the same algorithm. Go to the half of this, and so this time, I went back a little too far. I'm in now the E section. So what do I know? Is John Harvard to my left or to my right? 

To my right, so I can, again, tear the problem in half. Throw this half away, and now I'm really flying. I'm doing it verbally slowly, but that went from 1,000 pages to 500 to now 250. And now I can do it again, 125. I do it again, roughly like 67, and keep doing it again and again and again, until I get left with, hopefully, just one single page or in this case an ad for, ironically, a mechanic. 

OK, so what is the implication for our performance? Well, let's just do this sort of in the abstract, if you will, if that first algorithm were to be plotted just quickly on a chart without even numbers. Here's my x-axis, size of problem on the x-axis. So the bigger the problem, the farther out that way. Time to solve the problem. The higher you go up on the y-axis, the more time you're taking to solve it. 

How would we draw the running time, the amount of time taken to run that first algorithm? Well, it's going to be a straight line. Why? Because if you add one more page next year because more people move to Cambridge, you're going to add one more page turn potentially, so one more second, one more unit of time. So it's a straight line. And we'll abstract it away as "n." If there's n pages in the phone book, the slope of this line is essentially n. 

The second algorithm, wherein I was doing two pages at a time, was twice as fast, but it's still a straight line. And in fact, let me just draw some dotted lines here. If the phone book is this big, with my first algorithm, it might take this many units of time, this many steps, this many page turns. But with that second algorithm, notice that the intersection is much lower on the yellow line than on the red. 

So n over 2 means there's half as many pages here, if n is the number of pages. So indeed, that algorithm-- the second one-- is twice as fast minus the little hiccup that I have to double back one page. But that's not a big deal if I'm still doing things twice as fast. But the third algorithm looks fundamentally different. It looks like this. Logarithms, if you recall from high school or prior-- if you don't, that's fine too. 

It's just a fundamentally different function, a different shape. And notice that the green line is going up and up and up but a much slower rate of increase, which means crazy things are possible. If two towns in Massachusetts, like Cambridge and Allston, across the river, merge next year, for instance, in terms of their phone book, they're phone book just got twice as big. 

For the first algorithm, that's going to take me twice as many steps to go through. The second algorithm, almost it's going to take me 50% more steps to go through, two at a time. But the third algorithm, that I ended with, tearing things again and again, dividing and conquering, if you will, in half and in half and in half, how many more steps will my third algorithm take if Cambridge and Allston merge into a phone book that's twice as big? 

AUDIENCE: Four steps. 

DAVID J. MALAN: Just one more step, right? No big deal. You just take a really big bite out of the problem once you decide if John Harvard is to the left or to the right. And so you've made much faster progress. And so this, in essence, is what your computer, your phone is probably doing underneath the hood when searching for Harry or Hermione or Hagrid or anyone else because it's that much faster, especially when you have large data. 

If you don't have that many contacts, it probably doesn't matter if you search from top to bottom or more in the form of this divide-and-conquer algorithm. But if you're the Googles of the world or you're analyzing large data sets, indeed, this is going to add up quite quickly. So where do we go with this? Well, we're going to introduce next something called pseudocode. How can I translate what I did verbally there, sort of intuitively, to actual code? 

Well, this won't be Scratch. This won't be C or Python just yet. It's just going to be an English-like syntax. And this is how many programmers would start solving a problem. They don't start typing out code in C or Python or the like. They use English or whatever their human language is to jot down an outline for their ideas. My first step, really, was picking up the phone book. My second step was opening to the middle of the phone book. 

My third step was somewhat different-- look at the page, because why? My fourth step was if person I'm looking for is on the page, I then do what? It never happened in my example, but I call the person. So I'm done. Else if the person is earlier in the book alphabetically, as John Harvard was in the case of my H, then I should search to the middle of the left of the phone book. And then I should go back to step three. 

Step 3 is look at the page, thereby repeating the same process again and again. Step 9, though, might be else if the person is later in the book, then let's go ahead and open to the middle of the right half of the book and then go back to line 3. Else there's a fourth scenario we should probably consider, lest my search process freeze or crash or give me one of those spinning beach balls with a bug. Yeah-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, what if John Harvard isn't in the phone book? I'd prefer that my algorithm, my phone not just reboot or freeze. I should handle that with some kind of catch all. Else, so to speak, let's just quit the program. So there's well-defined behavior for every possible scenario of the four. Now, let's call out a few of these salient terms. It turns out, if I highlight in yellow here, there's a pattern to what I've been doing here. 

These are all of my English verbs. And in a moment, we're going to start calling those verbs "functions." When you program or write code and you want the program or the computer to do something for you, some action or verb, we're going to refer to those actions or verbs as these things called "functions," like those here. By contrast, I've just highlighted, instead, my "if," my "else if," my "else if," and "else." 

This is going to represent what we're going to start calling a "conditional," a proverbial fork in the road where you can either go this way or that way, do this thing or this other thing. And you're going to decide which of those things to do based on what I've now highlighted here, which are going to be called "Boolean expressions"-- Boole, referring to a mathematician, last name Boole. 

A Boolean expression is just a question with a yes/no, a true/false, a 1 or a 0 answer, if you will. And it governs whether you do this thing or this thing or this thing or that. The indentation, in this case, is important. The fact that I've indented line 5 implies, by convention in programming, that I should only do line 5 if the answer to line 4 is a yes or a true, and same for these other indented lines as well. 

And the last characteristic here is this here. Someone called this out earlier, in fact. These lines, 8 and 11, are now highlighted and represent what? What might we call these in code if you've done-- yeah, so these are loops, some kind of cycles that result in my doing the same thing again and again, but there's a key detail with this algorithm in pseudocode. Even though it's telling me to go back to line 3, why is this algorithm eventually going to stop? 

Why do I not constantly keep looking for John Harvard forever by nature of these loops telling me to keep going back to line 3? Good. Eventually, he'll be on the page or, to your point earlier, he won't be at all and we're out of pages, and so we just quit. And that's the key about going to the left half or the right half. It doesn't matter if you do the same thing again and again. 

You're not going to get stuck in a so-called infinite loop so long as you keep dividing the problem and shrinking it into something smaller, smaller, smaller. Eventually, there's going to be no problem left to solve. So even if you don't think of yourself as a computer person, even if you've never written code, what you'll find in the coming days is that these ideas that we've just kind of harnessed from real life are at your fingertips already. 

And a lot of the process of learning to code is just going to be some bumps in the road because you can't quite see the new syntax in a familiar way. But you'll find that the ideas, in fact, are going to be more familiar than you might otherwise think. And so we'll see in a bit-- and we'll take a break in a moment to take a breather-- that you will see these same ideas in a moment in the context of Scratch, an actual programming language via which we'll drag and drop puzzle pieces to make actual code work. 

We'll see some variants of these ideas, things called "arguments" and "return values" and "variables." But we'll ultimately convert it into this somehow. Anyone want to wager what this program will do if fed to your Mac or PC or phone? Here's just a massive pattern of zeros and ones. 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: It will indeed say, rather disappointingly, apparently, just, "Hello, world." And indeed, baked into all of these 0's and 1's are not just the H-E-L-L-O, but also the verbs, the action of printing something to the screen. And there's other stuff too so that the program knows how to start and how to stop, a lot of stuff that we won't have to worry about, that whoever designed the computer or the language did. 

But at the end of the day, you're never going to be writing the 0's and 1's yourselves, though our ancestors, once upon a time, did in some form. We'll be using a much higher-level language, like this in C, or better yet, in just a moment, like in Scratch, like this. 

And indeed, this is why today we focus on and begin with Scratch, this graphical programming language, so we have a way of expressing ourselves with functions, conditionals, loops, and more, but in a way that doesn't have stupid parentheses and curly braces and all of these visual distractions in the way and will translate that thereafter to this lower-level language. But for now, that was a lot. 

That was definitely a fire hose. Let's go ahead and take a 10-minute break. Feel free to get up or stay here. And we'll resume in a bit with some actual code. 

[VIDEO PLAYBACK] 

[MUSIC - THE WEATHER GIRLS, "IT'S RAINING MEN"] [MUSIC PLAYING] 

[THUNDER RUMBLING] 

- (SINGING) Hi. Hi. We're your Weather Girls, and have we got news for you. You better listen. Get ready, all you lonely girls. And leave those umbrellas at home. All right. Humidity is rising. Hmm, rising. Barometer's getting low. How low, girl? 

According to all sources-- what sources, now-- the street's the place to go. We better hurry up. 'Cause tonight, for the first time, just about half-past 10:00-- half-past 10:00-- for the first time in history, it's going to start raining men-- start raining men! 

It's raining men, hallelujah! It's raining men, amen! I'm going to go out. I'm going to let myself get absolutely soaking wet! It's raining men, hallelujah! 

DAVID J. MALAN: [CHUCKLES] All right, so-- 

[END PLAYBACK] 

[APPLAUSE] 

So this then is Scratch, a graphical programming language from our friends down the road at MIT's Media Lab that indeed some of you might have used in grade school or the like, for playing and writing code and the like, but you maybe didn't necessarily think about how some of these primitives ultimately worked. 

And in fact, everything you've done-- if you've used Scratch before-- and everything you'll see today is going to apply to all of the weeks to come, as we explore these things called "functions" and "loops" and "conditionals," "Boolean expressions" and more. With Scratch, because it's so graphical and animated-congruent, can you create animations, like this one, interactive art, and software more generally. 

But you'll do so by dragging and dropping puzzle pieces that only lock together if it makes logical sense to do so. And you won't have to deal with, in this first week of class, is curly braces, parentheses, all of the weird symbology that you might recall seeing, when we just wanted to say, "Hello, world." Now, this particular program, "Raining Men," was written by a former CS50 teaching fellow, Andrew Berry, who's actually now the general manager of the Cleveland Browns, the American football team. 

And so these are just some of the programs that some of your predecessors in the class have created. And you'll see, in the remainder of class here, a couple of others as well, and more in the course's first assignment, namely, problem set zero. So how do we get there? Well, first a quick tour of what it is we're going to do. This, in Scratch, is perhaps the simplest program you can write. 

And even if you've never seen Scratch or any programming language before, you can probably guess that this just says, on the screen somehow, "Hello, World." But what you don't have to do is type esoteric commands and weird syntax, those curly braces and parentheses I keep alluding to. You just drag this yellow puzzle piece. You drag this purple puzzle piece. Let them magnetically lock together, so to speak. 

Click a button and boom. With those same building blocks and several others, can you make exactly the sorts of things that Andrew brought to life as well. So here's what we're about to see. At Scratch.MIT.edu is a cloud-based programming environment on MIT servers. You can also download it offline on your own Mac or PC. And it gives you an interface like this. 

On the left-hand side of the screen, you'll see a blocks palette. These puzzle pieces, a.k.a. blocks, come in different colors which rather categorize them. So pictured here, for instance, in blue, are a whole bunch of motion-related blocks. So Andrew used a whole bunch of those to have the singer and the men moving around on the screen in synchronicity with the song that was playing in the background. 

Meanwhile, in the middle of this interface is going to be the code area. And this is where Andrew, and soon you, will drag and drop some of those puzzle pieces and other colors as well and lock them together to get your character-- soon to be invented-- to do something on the screen. Indeed, at the bottom right here, will you see, ultimately, a sprite area, where a sprite is a technical term for like a character in a video game or a programming environment like this. 

By default, historically, Scratch is the cat, the mascot, if you will, for this programming environment. And so here we see, by default, just one sprite selected because on the top right of the screen is the stage for that sprite. And you can click and zoom in to make it full screen. But this is the world in which Scratch-- by default, the cat-- will live. But you can change Scratch's costume so that it looks like a singer or the man falling from the sky or the like or anything else, either creating the art yourself or importing some of the things that come with it or elsewhere online. 

So what is this world that Scratch rather lives in? Well, generally speaking, we won't have to care too much about numbers because we'll be able to ask questions, like interactive ones, like is Scratch the cat, or any character otherwise, touching the edge of the screen, touching something else? But Scratch does exist in this two-dimensional coordinate-system world. So when the cat or any character is dead center in the middle, that would be xy location 0,0, if you will. 

Meanwhile, over here is 240 pixels, or dots, all the way to the right. So this would be 240,0, where y is 0 because it's right on that midline. So it's neither up or below. Over here to the left, of course, would be -240 and 0. Above the cat would be x equals 0, because it's right on that vertical midline, and 180. And then down here, as you might guess, would be 0, negative 180. 

Generally speaking, we don't have to care about those precise pixel coordinates. But it's helpful, ultimately, if you do want the cat to move up, down, left, or right. Having some sense of direction according to the x-axis and y-axis as well can help you express your ideas, ultimately. So what might some of those ideas be? Well, let's do this. I'm going to go ahead and create, on Scratch.MIT.edu, just an empty screen like this one here. 

And so this is the exact same interface. But now I'm in my browser, full screen, so that I can start writing some code. And let's get that cat to say something actually on the screen. Now, this takes a little bit of practice. But honestly, just by scrolling through these puzzle pieces can you quickly get a sense of what's possible, not just categorically, but specifically. And I'll jump around because I've done this, of course, before. 

But I'm going to go to events, in yellow, first. And I'm going to drag and drop this first block, called when Green Flag clicked. And I've zoomed in there just to make it a little more legible. And notice that the shape of this Green Flag just so happens to mirror this Green Flag here at top, next to this red Stop Sign, of sorts. And the Green Flag is going to mean go and the red Stop Sign is going to mean stop, to start or stop our program. 

Next week, you're going to be writing a textual command at your keyboard to do the exact same idea. But for now, it's a button. So when Green Flag clicked, what do I want Scratch to do? Well, how about we have Scratch just initially say something like, "Hello, world," which indeed, historically, is the first program that most any programmer might write. So anything related to what the cat looks like it's doing is actually going to be under looks, here in purple. 

So I'm going to drag over Say "hello." And you'll notice something curious and different about this purple block. It says, of course, "Say" in purple. But then there's this white oval and some text that, by default, is "hello" because MIT just decided that, by default, the placeholder will be "hello." But anytime you see this white oval, it's an opportunity to provide an input into the function called Say. 

And so here I'm borrowing terminology from before. Problem solving, again, is all about inputs producing outputs. And in between there is some algorithm. In a moment, we're going to start referring to algorithms quite frequently as "functions." Why? Because it's the implementation of some algorithm. So let me override the default with, "Hello, world." I'll zoom out. And now if I go to the top right of the screen and click the Green Flag, we'll see, hopefully, my very first program in code. 

Now, it wasn't a huge lift, right? It only was a matter of dragging and dropping puzzle pieces. But what has now happened? Well, it turns out that two things have happened. When I, the human, clicked on that Green Flag, I triggered, what we're going to start calling now, an "event." An event is generally something graphical or interactive that just happens in a computer program. 

You and I trigger events on our phones all day long. Whenever you tap or drag or long press or pinch or any of those gestures in vogue nowadays on phones, you are triggering events. And people at Apple and Google and elsewhere have written code that listen for those events and do something when that event happens. That's what I just did. When Green Flag is clicked, I want something to happen, namely, I want this purple function, this verb, this action called Say, to do something. 

What do I want it to do? I want it to say what this input is. And I'm going to introduce another vocabulary term. The white ovals here are, yes, inputs, very generically. But in a programmer's terminology, they're called "arguments," otherwise known as "parameters." And that just means an input to a function that modifies its behavior in some way. When I click Stop, that's just another event. 

And that one is just built into Scratch. Scratch knows that when you click the green Stop Sign, everything should just stop automatically. I don't have to write code to support that feature. So that's all fine and good, "Hello, world." But if I keep doing stop and start and stop and start, it's going to do the same thing again and again. And it's really not that interesting, at the end of the day, maybe gratifying once, but it'd be nice if this were a little more interactive. 

So it turns out that we can do that too. But we need a different mental model instead. So in this case here, when we think about this function, Say, in this input, "Hello, world," this actually maps pretty cleanly to this model earlier, that I propose is problem solving, is computer science, if you will. The input to the current problem is going to be in white here, "Hello, world." 

The algorithm is the "say" algorithm. Now, I don't know how MIT got it to print out the little, pretty speech bubble on the screen. But they wrote those underlying low-level implementation details. And they gave me and you a purple function, called Say, that just does that for you. You and I don't have to reinvent that wheel. The output of Say is another technical term, now, called a "side effect." 

A side effect is usually something visual that happens, like as a side effect of you calling a function. And so the side effect here is that the cat has this speech bubble magically appear, inside of which is "Hello, world." So we have an input. We have an output. We have an algorithm. But now we're talking about these ideas in the context of programming. So now the input is an "argument." 

The algorithm is a "function." And the output, in this case, is a "side effect"-- terminology that you'll just hear more and more. And it'll eventually sink in, but not to worry if the terminology doesn't come naturally early on. So what more might I do with this? Let me go back to Scratch here and make this maybe perhaps more interactive and actually get the cat to say something a little more dynamically. 

So instead of "Hello, world," why don't we get him to say hello to me or to you or anyone else? So let me do this. Let me go under, say-- let me get rid of this first. And you'll notice this neat trick. As soon as you start dragging on a block, if it gets close to it, it kind of goes gray, and it can be magnetically snapped together. You don't have to do it very precisely. Conversely, if I want to get rid of a puzzle piece, I can just drag it anywhere on the left, let go, and that deletes it. 

Or you can Right-click or Control-click and a little menu will let you delete it as well. Well, let me do this instead. Under Sensing, which I know is there because I've done this before, are a whole bunch of things related to Sensing, whereby the cat can kind of feel out its world, in some sense. It can do things like ask this question, "Am I touching the mouse pointer?"-- like the user's cursor. 

"Am I touching a specific color that you can override to be anything you want?" "Is the distance to the mouse pointer some specific value?" But for now, I'm going to focus on this, this blue puzzle piece that asks a question, which itself is this white oval that I can apparently change, and then it's going to wait for a response. But this puzzle piece is a little different. It's a little special. It comes with a freebie. 

It comes with what we're going to call, technically, a "return value." So some functions don't just do something on the screen. They hand you back, so to speak, a value that you can do anything that you want with. Nothing happens immediately unless you do something with that so-called return value. So let me go ahead and drag this thing over here, ask, "What's your name?" And I'll use the default question. 

That seems a reasonable place to start. I'm not going to override that default. And now let me go ahead and zoom out. Let me go back to Looks. Let me go to Say. And let me just form the English sentence I want. So let me zoom in here and type in "hello," maybe comma, space. I could do "David," but that's obviously not right because I'm asking for a name, and then I'm like, in advance, hard-coding my name. That's not what I want. 

I just want, "hello," comma. And now let me zoom out and grab one more Say block. Let me maybe Say here. OK, I don't want to say, "Hello, hello." I don't want to just type in my own name because, again, then what's the point of asking the user for their name? But notice this. If I go back to the sensing block, this is where that oval that's blue, called Answer, is useful. 

This will be the so-called "return value" of that function. So I'm just going to go ahead and do this and drag and drop. Even though it's not the right size, it is the right shape. And so Scratch will be smart about it and grow to fill that puzzle piece for you. Let me zoom out now. And now let me click the Green Flag. You'll see that Scratch is indeed prompting me with a speech bubble, "What's your name?" 

Notice the little text box below the cat is asking, what's your name? So I'm going to type in D-A-V-I-D and hit Enter. Or I can click the blue check. Enter. OK, it's a little weird. I wanted him to say, "hello," not just my name. So let me Stop. Let me start it again. All right, hello, what's your name? D-A-V-I-D. Enter. Huh-- kind of rude. Why is there this bug? Like, I wanted to say, "Hello, David," not just "David." And yet twice it has failed to do so. Yeah-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, the computer's processing my directions, my actions, really quickly. And so it actually is doing it. It's just, you and I, in the room, are just way too slow to notice that it said-- (QUICKLY) "Hello, David." 

It just seems to have just said, "David." So all right, how can I fix this? Well, here's where you start to poke around and think about how you might solve this. Let me go back under Looks. Maybe there's a smarter way to do this. Maybe I could do-- OK, I could do this. How about instead of just Say "hello," there's apparently another puzzle piece where I can time it so I can maybe slow things down a little bit. 

So let me do this. Let me throw away all of this. Let me drag a Say "hello" for 2 seconds. Let me drag another Say "hello" for 2 seconds. Let me change the first one to, indeed, "hello" comma. And then let me go back to Sensing. Let me grab that same answer because I threw it away a second ago, and I'll just change it. I don't even have to delete "hello." I can just overwrite it like this. 

So now I think we'll kind of pump the brakes and see things more slowly. Let me Stop. Let me start. D-A-V-I-D, Enter. Hello, David. OK, so it's better, like it seems to be working. I think your hypothesis was right, just looks kind of stupid, right? Like, the fact that it's saying Hello-- 

[PAUSE] 

--David, like we can do better. And like, literally every piece of software on your phone or Mac or PC is better than that. It adds words together in the user interfaces you and I are familiar with. So let's go a little more fishing here. Let me throw away these. Let me go back to Looks and just get the simpler Say. I want this to say, "Hello" comma name, where name comes from that Answer return value. 

So how can I do this? Well, let me go under Operations, which we haven't been before. There's a lot of stuff in here. Some of it's mathematically related, adding, subtracting, and so forth. You can generate random numbers which might be useful. And if I keep scrolling down, there's this Join "apple" and "banana." But that's just placeholder text. You can join one piece of text with another piece of text, by default "apple" and "banana." 

But let's change it to "hello" and my name. So this, too, wrong size but right shape. So let me let it snap into place. Let me go ahead now and do "hello" comma. And now I think I just want to go grab that Answer return value. Let me drag the same oval as before, clobber-- that is, overwrite-- banana. So now I'm kind of composing functions. The output of one function, Join, is going to be the input of another function, Say. 

So let's see what happens now that they're kind of stacked on top of each other or nested, so to speak. Click the Green Flag, D-A-V-I-D. Enter. "Hello, David." All right, that was pretty fast. Let's just do it once more. Stop. Start. Here we go, D-A-V-I-D. Enter. OK. All right, it's not the most exciting program in the world. But it's more correct. It's better designed just because that's what you would kind of expect the software to do and not be some kind of lame user interface that's just inserting random delays to just make it kind of work, like that's a workaround, a hack, if you will. 

But there's some cool things you can do with Scratch. And we won't really go down the rabbit hole of all of the fun and family-friendly features that it has. But there is one that's kind of cool here. Let me go into the Extensions button at the bottom left of my screen. And this one's kind of cool. Let me go to Text to Speech. And you'll notice that this one requires internet because it's cloud based. 

But this just gave me some new puzzle pieces in a new category, Text to Speech. And these green ones do exactly what they say. So let me do this. Let me zoom out again. Let me keep the Join block. And I'm just going to temporarily toss it over here. It's not going to delete itself because I didn't drag it over to the other side. But I'm going to get rid of the Say block, in purple. I'm going to do the Speak block here, in green, and let it snap into place. 

And then I'm going to drag and drop this onto the input to Speak. And now, perhaps a little more adorably, let's try this. Green Flag, what's your name? D-A-V-I-D. Enter. And-- 

COMPUTER: Hello, David. 

DAVID J. MALAN: OK. 

[LAUGHTER] 

It's a little robotic. But at least now it has synthesized speech. And I've kind of got my own, like, Siri or Google Assistant or Alexa thing going on here now, where it's now recognized whatever text it is, and it's played it. Well, let's make this an actual cat that doesn't talk in that weird human voice. Let me go ahead and get rid of most of this stuff. And let's get the cat to actually meow, like a cat tends to. 

And let me go under the Sounds block. Now MIT gives you a few sounds for free because it's designed around a cat, by default. And I'm going to go ahead and grab this one, Play Sound Meow until done. And now-- and we heard a teaser for this earlier in the crowd-- 

[MEOW] 

It's a little piercing, admittedly. Maybe we can lower the volume a little bit there. But notice, if I want the cat to meow a second time, I'll just click it again. 

[MEOW] 

OK, and over there, too, I hear-- 

[MEOW] 

OK. 

[MEOW] 

All right, so it's kind of cute now, right? So it's just meow-- OK, yes, echo, echo. So it's meowing now every time I hit the Green Flag. Now, that's great, but even a kid is probably going to-- 

[MEOW] 

--like would prefer that it-- 

[MEOW] 

--just meow, perhaps, like again and again, without having to keep-- 

[MEOW] 

--hitting the button. So how might we do this? All right, well, if I want it to meow multiple times, why don't I just, like, grab it another time and another time? Alternatively, you can Right-click or Control-click a puzzle piece and just duplicate it from a little menu that drops down. So here we go, three meows. 

[MEOWING] 

All right, that's not really a happy cat. It sounds maybe hungry. So can we slow that down? Well, maybe. In fact, if I poke around, let me go under Control. It looks like there's a Wait block. Wait 1 Second, by default. And notice, Scratch will be pretty accommodating. If you just hover in between blocks, it will grow to fill that too. So I could change it to 1 or 2 or anything, seconds. I'll just leave it at the default for now, 1. And now I'll go ahead and do this. 

[MEOWING] 

OK, so cuter and less hungry and just more friendly. But this isn't the best design. It is correct. And let's use that as a term of art. Correct means the code does what you want it to do. I want the cat to meow three times slowly. And it did. So I'd wager this is correct. But it's not the best design. And this is where things get more subjective, right? Like, you could write accurate sentences in an essay for an English class, but otherwise, it's just completely a mess. 

Like, your arguments here and there, and you don't say anything wrong, but you don't say it well. In the context of code, we can do better than this. And Copy/Paste or repeating yourself again and again tends to be bad practice. Why? Suppose that you want to change the Wait to 2 seconds instead of 1. It's admittedly not a big deal. Fine, I click there, I change it to 2. I click there, I change it to 2. 

But what if you meow 5 times, 10 times? Now I have to change the Wait, like, in 5, 10 different places. Like, that's just stupid. It's taking unnecessary human time, and you're going to screw up eventually, especially if your program is getting longer. You're going to miss one of the inputs. You're going to leave the number wrong. And that's a bug. 

So just based on what you've seen already or if you've program before, which a few of you have, what's the term of art here that will solve this? How can we design this better? 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: I heard it here. Yeah, so a loop-- a loop, some kind of cycle that says, do that again. Do that again-- not infinitely many times, necessarily, but some finite number. Well, you can perhaps see a spoiler on the screen. Under the same orange Control category is a Repeat block. And by default, it's proposing 10. But we can change that. So let me do this. I'm going to throw away most of this Copy/Paste as redundant. 

I'm going to detach this temporarily just to make room for something else. And I'm going to drag a Repeat block over here and let that snap into place. And I'm going to change it for now, just to be 3, for consistency. And this is the correct shape even though it's too small, but Scratch will accommodate that for us. And now-- same output but arguably better designed. 

Why? Because if I want to change the number of meows, I change it in one place, no Copy/Paste messiness. If I want to change the waiting, one place. I don't have to change it in multiple places and not screw up. So let me hit the Green Flag. 

[MEOWING] 

All right, so-- nice. Now, it would have been nice if MIT had just given us a meow block that just automates all of this for us. Let me wager, they gave us the low-level implementation details. They gave us the Play Sound Meow. But I had to implement a decent number of blocks just to get a cat to meow again and again. I feel like we should have gotten that for free from MIT. 

Well, they don't have to be the only ones that invent blocks for us to use. You can write your own functions, your own verbs or actions. So how can we do this? Let's make our own puzzle piece, called Meow, that uses this code but creates it in such a way that it's reusable elsewhere. So let me do this. Under my blocks in pink here, I'm going to go ahead and click, literally, Make a Block. 

Now, here's an interface by which I can give the block a name. M-E-O-W will be the name of this block. And I'm just going to go ahead and quickly click OK. That just gives me a very generic, pink puzzle piece that starts with the word Define because scratch is asking me to define, that is, implement or create, this new puzzle piece for me. Well, what does it mean to Meow? 

I'm going to claim that it means to do these two steps, to play the sound meow and then just wait for 1 second. But what's powerful about this idea is look at this up top. Now that I've made a block, it exists in Scratch. MIT didn't need to create this for me. I created it for myself and even you, if we end up sharing code. So I can now drag Meow up in here. And what's nice about Meow is that itself is, yes, a function, but it's also an abstraction. 

Like, never again do I or even you need to worry or care about what it means to meow or implement it. I can sort of drag it out of the way. I didn't delete it-- drag it out of the way. Out of sight, out of mind. Why? Because my code is now even better designed, in some sense, because it's more readable. What is it doing? When the Green Flag is clicked, repeat 3 times Meow. 

It just says what it means. And so it's a lot easier to read it, and it's a lot easier to think about it, especially if you're using Meow in other projects too. Now, let me go ahead and click Play. 

[MEOW] 

Same thing. 

[MEOW] 

So it's not really fundamentally any different. 

[MEOW] 

But I can make this custom puzzle piece, this own function of mine, Meow, even more powerful. Let me kind of rewind a bit and go to my Meow puzzle piece. And I am going to Control-click or Right-click on my pink puzzle piece. And I'm going to edit it. So I kind of regret making Meow so simple. Wouldn't it be nice if Meow took an input, a.k.a. an argument, that tells Meow how many times to meow. 

Then I can get rid of that loop and just tell Meow how many meows I actually want. So I'm going to click on another button here called, literally, Add an Input. And it's going to have placeholder here. So I'm just going to put a placeholder there. I keep using "n" for number, which is a go to in computer scientist terms. And I'm going to add some descriptive text just so that it's a little more self-explanatory. 

I'm just going to say Meow n Times. But there's only one oval. Times is just going to be explanatory text. And now notice what has happened. Now my puzzle piece takes an input, a.k.a. an argument, that will tell that function to meow some number of times. But it's not just going to work magically. I need to implement that lower level detail. So let me zoom out. I have to remind myself what this function was. 

So I'm going to drag it higher up just so they're on the screen at the same time. I'm going to go ahead now and temporarily move this over here. I'm going to temporarily detach this over here. Why? Because what I thing I want to do is move my loop into the function itself, move the Play and the Wait into the loop. But I don't want a hardcode 3. Notice that n here is its own oval I can drag a copy of n and just let it go there. 

So now I have a new version of Meow that takes an argument, n, that tells Meow how many times to meow. And now let me, again, drag this out of sight, out of mind, because who cares how I implemented it? Once it's implemented, it's sort of done. Now my program is even better designed, in some sense. Why? Because now it really just says what it means. There's no loop. There's no repeat, no implementation details. 

When Green Flag Clicked, Meow 3 Times. And so functions indeed let you implement algorithms, like they're just code that do something for you. But they're also themselves abstractions. Why? Because once a function exists, it has a name. And you can think about it in that term. And you can use it by its name. You don't have to care or remember how the function itself was built, whether it's by you or even MIT. So again, here I'll click the Green Flag. It's the same thing. 

[MEOWING] 

So still correct, but better and better designed. And so any time, here and out, with Scratch, or soon C, and eventually Python, when you find yourself doing anything resembling Copy/Paste or again and again grabbing the same code, probably an opportunity to say, wait a minute. Let me refactor this, so to speak, that is, rip out the code that seems to be repeated again and again and put it in its own function so you can give it a descriptive name and use and reuse it. Any questions just yet on now saying or these loops or these functions that we're using? Yeah-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: How did I make it so it meows three times? So I originally only had a puzzle piece called Meow. And I decided to improve it. So I held down Control and I Right-clicked or Control-clicked on the pink puzzle piece at top left. And I clicked Edit. And that brought back the original interface that lets me add some arguments to the puzzle piece itself. And I clicked Add an Input on the left here. 

And then I clicked on Add a Label over here. So that just lets you customize it even further. All right, so we've done this. Let's add one of those other primitives too to do something optionally. So how about we make the cat meow only if it's being petted by a human, as by moving the mouse to hover over the cat, like a human would pet a cat? Well, let me go ahead and throw away the meowing for now. 

And let me simplify it by just using a sound. I'm going to go ahead and do this. I'm going to go ahead and have a Control block that says If, because I want to implement the idea of if the cursor is touching the cat, then play sound meow. Or I could use my same pink puzzle piece. But I'm going to throw that away and focus only now on the sounds. And I'm going to do this. 

If touching mouse pointer-- so I need to sense something about the world. And we saw this earlier-- so If Touching Mouse Pointer. So notice this shape here, way too big. But it is the right shape. So if I hover just right, it'll snap into place. And this now, in blue, is my Boolean expression, a yes/no question, true false. "If" is a conditional. And what do I want to do? Well, if the cat is touching the mouse pointer, I want to go ahead and play sound meow until done. 

So let's do this. I'm going to hit Green Flag, click. Now nothing's happened yet because it's a conditional, right? It's only supposed to do something if I'm touching the cat. Let me move the cursor over to the cat. And-- wait for it. Hmm-- another bug. Why is the cat not meowing even though I very explicitly said, If Touching Mouse Pointer, Meow? Yeah, in the middle-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, this is-- again, my computer's just so darn fast, like yours. I click the Green Flag, it asks the question, am I touching the mouse pointer? Well, no, because my cursor was up there, not touching the cat. It's too late. The cat's out of the bag. And so we have to instead solve this by some other means. How can we fix this? How do we fix that sort of race? Yeah-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, so why don't we just keep asking the question until I eventually am or am not actually petting the cat? So let me detach this temporarily. Let me go under Control. Let me go under-- instead of repeat some finite number of times, let's just do it forever. So sometimes loops that do work forever are a good thing. The clock on your phone, that's in a loop forever because you want it to always tell time and not stop at the end of the day. 

So sometimes you do want code to loop forever, as in this case. So let me go ahead and drag and drop it there. Let me, again, click the Green Flag. Nothing's happening yet. But notice, the program is still running. And so if I move my cursor, move my cursor, move my cursor, and-- 

[MEOWING] 

OK, so maybe we could add some Waiting. But the cat does not want to be pet, in this case. But it's indeed conditional. So there we have an incarnation in Scratch of doing something conditionally. Now, we can make this really cool, really fast, if you will. Let me stop this version. Let me go ahead and do this. Let me go ahead and throw all of this away. Let me go into my little Extensions bucket over here. 

And let me do Video Sensing, since most laptops or phones these days have cameras. And there, indeed, I am, with Sanders behind me. And let me do this. When Video Motion-- and let me get out of the way. When Video Motion is Greater Than some value. So 10 is the default. This is just a number that measures how much motion there is or isn't. So small number is like no motion. 

Big number is lots of motion. So I'm going to choose 50, somewhat arbitrarily here-- so 50. This is not normal to program off to the side. But I'm now going to say this. When Video Motion is 50, go ahead and Play Sound Meow like this. So the cat is still in that world. I'm going to stop the program and rerun it. So here we go, Green Flag. And now here comes-- all right, this is a little creepy, the way I'm petting the cat, but-- and-- [SIGH] 

[MEOWING] 

OK. 

[LAUGHTER] 

There we go. OK, so 50 was too big of a number. I have to pet the cat faster. 

[MEOWING] 

Whereas this, if-- I don't know-- 

[LAUGHTER] 

Yeah, so-- 

[MEOW] 

OK, so you can make things even more interactive in this way by just assembling different puzzle pieces. And honestly, there are so many different puzzle pieces in here. We're not going to even scratch the surface of a lot of them. But they generally just do what they say. And indeed, when you see on the screen here this pallet of puzzle pieces, really a lot of programming, especially early on, when learning a language, is just trying different things and try and fail. 

And if it doesn't work quite right, look for an alternative solution there too, as even I just had to do a moment ago. Well, let's go ahead and use, actually, how about another example of something a predecessor of yours made? Let me go ahead and grab a program I opened in advance here called Whack-A-Mole Might we get a brave volunteer to come up, who is willing to whack a mole with their head, virtually? 

Maybe-- OK, let's see, how about in way back? You want to come on down? All right, come on down. Sure, a round of applause for our volunteer. 

[APPLAUSE] 

All right, so here we have-- come on down. 

AUDIENCE: Hi there. 

DAVID J. MALAN: What's your name? 

AUDIENCE: I'm Josh. 

DAVID J. MALAN: Oh, actually, say it into the microphone. 

AUDIENCE: Hi, I'm Josh. 

DAVID J. MALAN: OK, nice. Welcome, Josh. Come on over. 

[APPLAUSE] 

All right, so same idea here-- I'll take the mic back. You'll have to stand in front of the camera. In just a moment, you're going to have to position your head in a box that your classmate from yesteryear created. 

[MUSIC PLAYING] 

And we'll start with Beginner. 

AUDIENCE: OK. 

DAVID J. MALAN: So line your head up in the box in a moment. 

AUDIENCE: All right. 

[LAUGHTER] 

DAVID J. MALAN: Nice. 12 seconds. 5 seconds. Notice the score's up to 18 already. Pretty good. All right, a round of applause for Josh, if we could. 

[APPLAUSE] 

So notice how using some fairly simple primitives, things do get interesting pretty fast. And how was that implemented? Well, there were probably at least four sprites. So you're not confined to just one cat. You can create more and more sprites, change what they look like. So they actually look like a mole, in this case. There's probably some conditionals in there, some loops for 30 seconds. 

That's checking if Josh's head's movement is exceeding some value over this way or over this way, then increment something called a variable. We'll see those too. Just like in algebra you might have x and y and z, storing values like numbers, so can computer programs, have variables called x or y or z, or more descriptively called Score, as in this case at top right, or another variable called Countdown, typically one word in code, but in this case two words, that just store some value. 

So there's probably some math going on in there whereby the author of this program just is incrementing, that is, adding 1 and 1 every time it detected that a mole had been whacked, in this case, with movement. So back in the day, I, myself, actually implemented my very first program in Scratch when I was a graduate student, actually, at MIT-- cross-registered at MIT, taking a class from MIT's Media Lab, specifically, the lifelong kindergarten group, which is the group that created Scratch, itself. 

And the program I wrote all those years ago and still rather cling to is a little something here called Oscartime, that I thought I'd play just a quick excerpt of myself here. So in this case, consider, as the music starts playing, how this program, which is much more sophisticated, certainly, than the earliest "Say hello" examples we just did might also be implemented. Let me go ahead now and click the Green Flag. 

[MUSIC - OSCAR THE GROUCH, "I LOVE TRASH"] 

OSCAR THE GROUCH: (SINGING) Oh, I love trash. 

DAVID J. MALAN: OK, so some trash is moving, presumably in some kind of loop from the top. If I'm touching the mouse cursor, it follows me. If I hover over the trash can, it responds. If I let go, in some kind of loop, Oscar pops out, creates a variable with the current score. And it happens again. 

OSCAR THE GROUCH: (SINGING) It's awful, the holes. And the laces are torn. A gift from my mother the day I was born. I love it because it's trash. Oh, I-- 

DAVID J. MALAN: It's pretty easy at first but-- 

OSCAR THE GROUCH: (SINGING) --anything dirty or dingy-- 

DAVID J. MALAN: So I don't need to keep playing this up on stage in front of everyone. So my score is already now up to some 6 or so. But in a moment, too, you'll see that it's going to escalate. So I'm taking into account some time apparently. So now-- 

OSCAR THE GROUCH: (SINGING) I have here some newspaper, 13 months old. 

DAVID J. MALAN: So more and more sprites are suddenly appearing. And notice, that each time they're appearing from a different part of the screen. That's an illusion, perhaps, too, that-- pick a random number between x and y. So you can actually pick some range of values to have the game constantly changing. And indeed, I'm going to go ahead and click Stop, since I spent like eight hours plus, years ago, making this. 

And I can never listen to the song again, not that I should be anyway at this point in my life. But this song is synchronized then with a lot of the actions that's happening. And ultimately, there's just a lot of building blocks. But I didn't sit down and implement Oscartime, as I called it, all at once. I really did take baby steps, so to speak. And I figured out, well, how could I decompose this vision I had at the time to create this game ultimately? 

And how do I bite off maybe the easiest parts first? And honestly, the first thing I did was I found this image, and I just dragged and dropped it into Scratch-- OK, done-- like, lamppost is installed. It doesn't do anything. It's not interactive. But I at least set the stage, so to speak, for the program. Then what else might I have done? Well, let me do this. Let me go ahead and open up in another editor here an early incarnation of Oscartime by doing this. 

Let me go into Oscartime here. Let me full screen this. And here you have-- let me hide the trash for just a moment-- is what I might call the second version of my program, wherein, at the top right of the stage here, I had the lamppost, which I just dragged and dropped and got going, but then I added an actual sprite. And it has to be a sprite if you want it to do things interactively. 

The lamppost-- not a sprite. It's just an image a costume, if you will, for the whole stage itself, a backdrop. But this thing is indeed a sprite because it needs to respond to code and events, like dragging and dropping. So what might I have done early on with that code? Well, maybe the first version would have been something like this, whereby my very first version of Oscartime might have said something like, oh, this. 

How about, let me control the program as before-- or, rather, events. When the Green Flag is clicked, what do I want to do? Well, I want to go ahead and forever do something like this. Forever-- so I want the lid to open up if I touch it. So if the cursor gets near the lid, I want the lid to open up. And then if I move away, I want it to close. So how can I do that? I want an If, but I just don't want one question, I really want two, a fork in the road that goes left or right, so to speak. 

And let me grab this puzzle piece here, as I did long ago. So notice, it grows to fill. What's the question I want to ask? Well, under Sensing, I'm going to go ahead here and say If this trashcan is Touching the Mouse Pointer-- what do I want to do? Well, I want to change what the trashcan looks like. And this part, I did in advance of class. If you go up here to Costumes, this is where all the graphical stuff happens. 

And you'll see that I imported a whole bunch of different costumes that effectively, much like a video, when you play them quickly, creates the illusion of movement, some animation. But it's really just dot, dot, dot, dot, dot-- different images showing on the screen. Well, some of these costumes are called like Oscar1, Oscar2. Oscar1 is closed. Oscar2 is open. So let's just deal with those first. 

So if I'm touching the mouse pointer, let me go under-- how about Looks? And we didn't use this before, but there's this block, Switch Costume to Something Else. I'm going to drag and drop this inside of the If. And notice it's a little bit indented. I'm going to change it not to Oscar8, but Oscar2. Otherwise, If Not Touching the Mouse Pointer-- this is the other direction in the fork in the road-- let's go ahead and switch the costume back to what I described as Oscar1. 

So let me run this program. And not much of interest is happening yet. But notice, if I move the cursor up, down-- but how is that working? It's just changing the costume that's being overlaid on the sprite. So it looks like interactivity, but you are really just changing the aesthetics. And we humans are just kind of assuming, oh, it's opening up. Well, no, it's just changing a costume. 

So here's the difference. The high-level abstraction-- trashcan opening. The lower-level implementation detail-- costume changing, creating that illusion. And if I want it to look prettier, I could just have many other costumes and go boom, boom, boom, boom, boom to create more frames per second, if you will. So I need to do one other thing. Maybe if I accidentally leave the trashcan open, let me make one change here. 

Let me make sure that the very first thing I do when the Green Flag is clicked, is always start with the trashcan closed because otherwise, you might accidentally leave it open. So this gets me into some default state. So now it's always closed until I manually hover over it instead. Well, what might I have done next? Well, if I wanted to introduce something like the trash, I need a second sprite. 

And here, in advance, I grabbed the image already. Let me pretend that this never happened. Let me drag this away here. And now I have nothing in my code area for this piece of trash. But it is the second sprite. And all I did was I clicked on the little cat plus icon here, created a second sprite. I named it trash. I added a costume for it. Sort of the aesthetic stuff, I did in advance. 

But here I'll do now the code. How do I want to do this? Well, how about when the Green Flag is clicked, for the trash can, I want the trash can in parallel to do-- I want the trash, the piece of trash, to do its own thing. So what I want it to do is maybe let's do Motion, how about? And let's go to a specific coordinate. Now, there's a lot of options here. There's Turning, Go to a Random Position, Go to x,y, Glide, more elegantly. 

There's a lot of different ways to implement movement. I just want it to go to a very specific location first. So I'm just going to go to x,y first. And I'm going to say x, how about, will be-- let's not hardcode this. Let's just have it be-- well, let's do it at 0, initially, and then 240. So-- whoops-- let's do 0,240 so that this piece of trash always starts at the top middle of the screen. 

If you think back to that coordinate system, 0,0 is in the middle. 240 is straight above it. All right, now, after I do that, what do I want to do? Well, how about I control this thing by forever falling. Now, how do I make the trash move? We haven't seen this puzzle piece yet. But under Motion, the very first thing is called Move Some Number of Steps. By default, it's 10. But we'll do it more simply. 

Let me go ahead and move-- oh, sorry. Move is going to move it in whatever direction it's facing. I only want it to move down. So here, even I'm getting confused as to how many different ways there are to do things. What I thing I want to do is this. Let me only change my y-axis as follows. So here's another puzzle piece called Change y. So again, y is the vertical. 

So let me just change y by one pixel downward at a time, so -1 one pixel at a time. So it's kind of slow. And I think now-- I think that's it. Let me hit Stop. Notice that my trashcan is still going to be interactive. I haven't changed or deleted that code. I've just added now code for my piece of trash. If I click the Green Flag, notice that-- after I enable it-- let me start that again. 

I had it hidden for before class. But let me enable it now-- Green Flag, notice it starts dead center, at x equals 0, y equals 240, and it's dropping one pixel at a time. If that seems a little boring, we can change it to -10 pixels at a time and, boom, it's done. So that's how you might change the speed of a program. But I'm going to leave it more simply as -1. And honestly, it would be nice if it doesn't always start from the top. 

Otherwise, this game is not going to be very interactive. I'm literally going to be grabbing the trash from the same place every time. So why don't I, instead, Stop this. Let me go under Operators, and let's pick a random number. So let me change the hardcoded-- the manually inputted-- 0, and let's make x be somewhere between 0, so in the middle and all the way over to-- what was it-- oh, I got my numbers wrong-- 240 and my y will be 180. 

Sorry, I got my x and my y confused. So let me play this again. And now we have a game that's more like games you might have played growing up or even now, like there's some randomness to it. So the CPU, so to speak, is doing something more interesting. Let me run it again. Now it's a little to the left. Let me run it again. Now it's a little more to the left. Again-- now it's back to the right. So randomness just makes games more interesting. 

And this is why when you play any video game, if different things are happening, there's probably just some randomness. And it's quantized as just a simple number. Now, I think I just need one final flourish here, if I may. Let me go ahead and add this. How about Events-- or rather-- yes, Events. When Green Flag is clicked, I can do multiple things within the same sprite. They don't all have to be attached to the same one. 

Let me go ahead and forever go ahead and do something else. How about, Whenever the Trash is-- how about-- Touching the Trash Can-- so Forever If-- let's see, I need a Sensing block. So how about, Is Touching-- not the Mouse Pointer, this time, but Touching Oscar himself there. Now let's see what happens. All right, so let's go ahead and click the Green Flag. 

Now I go down over here and let go. OK, I kind of want it to go into the trash can. How do I make it go into the trash can? How can we take this high-level idea, put trash into the trash can, and make it seem to disappear? Logically, what could we do? Yeah-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: OK, so when it touches it, let's have it disappear. So I could hide it. Or honestly, if the game is going to be ongoing, like it was, letting me drop more and more trash, let me just have it go ahead and pick a new random location. So let me do this. Let me go ahead and Copy this puzzle piece up here and Duplicate. And I don't want the whole thing, sorry. Let me get rid of this. Let me just do this. 

Let me go back to some random location at the top. So now notice what happens. If I click and drag on it-- here it goes-- and I let go, it looks like it's going into the trash can because it snaps back up to some random location. Now, the only thing I'm not doing really is keeping track of any kind of score. And it turns out, if I full screen this, it's not going to be draggable, by default. 

So just as a corner case, so to speak, something that you might trip over otherwise, let me go ahead and under, let's see, Sensing, it turns out I also need this for the piece of trash. There's this way of setting, in Scratch, a sprite to be draggable or not draggable. I need to explicitly make it draggable so that when I do full screen this thing now, it still remains draggable and someone like myself can play it again and again. 

Well, how about we supplement this with one final flourish? Why don't we keep track now of the user score? So how about, when the user actually drags the piece of trash to the trash can, let me go under Variables here, where, in advance, I've already made myself a variable called Score. I could have called it x or y or z or ABC, but that's not very descriptive. In programming, you typically give things a more descriptive English, or some other language, name. 

So I called this one Score. So how do I want to do this in my Score? Well, let me go ahead and initially set this game score to 0 at the very top of one of these scripts-- one of these programs up here. And then any time my piece of trash is touching Oscar, let's not just jump to the top, let's change the score by 1 up here. So now notice, If Touching Oscar, Change the Score-- that is, Add 1 to the Score-- and then Pick a new Random location. 

And now Green Flag-- let's do this slowly. Here it goes. The trashcan opens. I let go. And now notice, at the top left of my program, notice the score is now 2. Notice the score, if I do this again, is about to become 3. And so here we have building blocks, literally, of making this program better and better and better. And so, indeed, that's how you generally approach solving any problem with code, be it in Scratch or C or Python or some other. 

You take this vision you might have or some vision you've been assigned in a homework assignment and try to break it down into these constituent parts and just pluck off the easy ones first. Put the lamp post there first, and at least feel like you're making some progress. Then pluck off something like the trash can, and just make it do a little thing. And it doesn't have to be in some same order here. 

I could have done this in a million different ways. But figure out what the small pieces are that, ultimately, like a few of the problems we've solved today, assemble into a greater solution there too. So that you have now a mental model for these types of blocks and others, let's return for a moment to this. We saw a moment ago that when I started saying, "Hello, David," and nesting those puzzle pieces, we had a whole different paradigm altogether. 

My input for that second version of, "Hello, world," was to now pass in, for instance, "What's Your Name?" into my function, called Ask. That gave me not a side effect, but what I called, again, a return value, called Answer, by default, in Scratch. And now notice and recall, when I had that same output become the input to my next block, it looked a little something like this-- Say. 

So how does this type of block and this nesting, this stacking of blocks, fit into the same mental model? Well, same idea-- my input for that part of the story is now taking in not one input but two-- two arguments-- "hello" and the answer from before. The function, in this case, is that new block called Join. The output thereof is, "Hello, David," which itself became-- if we sort of animate this-- the input to my final function, which indeed was still Say. 

And this is only to say-- no pun intended-- that almost everything that you do with these puzzle pieces, be it in the context of Oscartime or the mole whacking or even just something simple like, "Hello, world," will ultimately fit into that relatively simple mental model there. Now, I thought we'd end by taking a look at just a couple of final examples. These ones, too, made by some of your predecessors. 

And for this, I thought we would not write code together, but read it instead. And so allow me to open up one other example here that will show us a few different versions of a program that a predecessor made. Give me just a moment here. And we'll see how we might build up to something even more interactive. And in just a moment, we'll see something they called Ivy's Hardest Game, focused here on these particular mechanics. 

So here is version 0, so to speak, of this program, wherein the goal was to create a game where you have to get out of some kind of maze. And you have to get out, in this case, the Harvard crest from this maze. Let me go ahead and just hit Play on this Green Flag so you can see what the first building block for this program might have been. Notice that my hand here is actually on the Arrow keys on my keyboard. 

And it seems that by moving up, down, left, or right, this little crest on the screen responds in exactly that way. Now, let's hypothesize for just a moment. Even though we've not done anything quite like this before, how might this code be implemented? How do you get a sprite, be it a cat or a crest, to respond to keys on a keyboard-- might you think intuitively? Yeah-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, there could be something sensing what key you're pressing on. And if you do it again in forever a loop, you'll just constantly be listening for keystrokes. And this is how, like, every piece of software nowadays works. It's constantly waiting for your phone to be tapped or something to be typed on the screen. So let me go ahead and look inside of this existing program here. 

And there's more going on, but we'll take a quick glance what's actually going on. Well, up here at top left, notice, we just have Go To x Equals 0 and y Equals 0. That means put the Harvard crest dead center in the middle of the stage. Then we have Forever two functions that we made in advance as custom functions-- Listen for Keyboard, Feel for Walls. 

So it's doing two things at once. It's forever listening for the keyboard-- up, down, left, right-- and feeling for the walls, in the sense that if I get too far to the left, I don't want it to keep moving past that black wall. And if it moves too far to the right, I don't want it to blow through that wall either. So it's going to do two things constantly, listening for keyboard and feeling for walls, so to speak. 

And how are those implemented? Well, this one's a bit long. But on the left here is Listen for Keyboard. So this pink puzzle piece, Listen for Keyboard, first checks If the Key Up Arrow is Pressed, question mark, Boolean expression in a conditional, Change y By 1. That means, move it up 1. Else If the Key Down Arrow is Pressed, then Change y by -1, and similar for Left Arrow, similar for Right Arrow. 

And even though there's not a loop in this pink function, there is where I'm using it. So it's constantly being asked again and again. How about feeling for walls? Well, over here to the right-- it's a little cut off-- but here you have, If Touching Left Wall, Change x by 1. So if you hit the wall, it's too late. You're kind of blowing through it already. So I want to move it back one pixel so it's no longer touching that wall. 

Similarly, if it's touching the right wall, I want to back it up one pixel so it's no longer touching that wall. So it's kind of like bouncing off ever so slightly so that it doesn't slip through that actual wall. And what are those walls? Well, notice down here, it's just a simple sprite with a black line that I've oriented vertically instead of horizontally. And that's just so that I can ask questions of these other two sprites. 

Now, that gives me that form of interactivity. What more can I now do? Well, what if we make things a little more interactive here? Let me go ahead and see inside version 1 our second. And let me propose what's going to happen here. Well, how might we add a little something like Yale into the mix? Well, what's Yale going to do when I hit the Green Flag now based on this code? Any hunches? Here is the code for my Yale sprite. Yeah-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, it's kind of going to be an adversarially by blocking my path, theoretically, if I keep writing more code. So why? It too goes to the middle of the screen. It points in direction 90 degrees. So similarly, there's a whole degree system as well. And it forever asks this. 

If Touching the Left Wall Or-- notice the green block-- Touching the Right Wall, then just Turn around 180 Degrees. And indeed, if you think this through logically, that just means you're bouncing this way and this way by just flipping yourself around 180 degrees for just this Yale sprite. So if I go ahead and zoom in on this and click the Green Flag, I can still move up and down. 

But Yale is just kind of doing this all day long, back and forth and back and forth, forever. Nothing bad happens if I try to go through it. But we could add that, certainly, to the mix. In fact, let's add one final feature before we play this particular game. And let me go ahead and open up the final version of these building blocks that adds MIT to the mix. So here is MIT. 

Someone want to explain what this code does? And this is what we're doing. This itself is a skill. Reading someone else's code and understanding it is half of the part of programming besides writing. Yeah-- 

AUDIENCE: [INAUDIBLE] 

DAVID J. MALAN: Yeah, it's chasing down the Harvard logo outline. So this is apparently the name of the costume that this student made, Harvard logo outline. And apparently, it goes to a random position first. But then it forever points to Harvard. So no matter where I'm moving it, up, down, left, or right, MIT is being a little more strategic than Yale, bouncing back and forth like this. 

So let's go ahead and play this one in full screen. And here we have a Green Flag. So if I move up, MIT, rather strategically, is following me no matter where I go. All right, so still, nothing bad happens. But now it's struggling, right? It's going up, down, up, down. It's trying to follow me even though I'm not moving. So we need some final flourishes. And so I think, for this, we need perhaps one final volunteer. 

After this, cake awaits for everyone outside, as is an end of first lecture CS50 tradition. Would you like to come up and be our volunteer? 

[APPLAUSE] 

All right. And so this will be the actual version but written by one of your predecessors that I'll full screen here. It's going to stitch together all of these same primitives and more, but add the notion of scores and lives so that there's actually a goal, which in this case is to move the Harvard crest to constantly pursue the character on the right-hand side so that your sprite touches that one. Would you like to introduce yourself? 

AUDIENCE: Hi, my name is Mohammed. 

DAVID J. MALAN: All right, wonderful. Welcome aboard. And here we come with some instructions and final flourish if we want to keep the lights up but perhaps increase the music. 

[MUSIC PLAYING] 

[MUSIC - MC HAMMER, "U CAN'T TOUCH THIS"] 

MC HAMMER: (SINGING) You can't this. You can't touch this. 

DAVID J. MALAN: Notice he is using the up, down, left, right. But there's many more walls now. First level's pretty easy. But now Yale's in the mix, bouncing back and forth. Again, pretty easy. Now there's two Yale's at slightly different positions. MIT is coming soon. But first, we have three Yales. 

MC HAMMER: (SINGING) As such. And this is a beat, uh, you can't touch. 

DAVID J. MALAN: Very nice. 

[APPLAUSE] 

MC HAMMER: (SINGING) I told you, homeboy, you can't touch this. Yeah, that's how it look when you know you can't touch this. Look at my eyes, man, you can't touch this. Yo, let me bust the funky lyrics. you can't touch this. Fresh new kicks and pants, you got to like that. Now, you know you want to dance. So move out of your seat and get a fly-- 

DAVID J. MALAN: You got to go quick. 

MC HAMMER: (SINGING) Catch this beat while it's rolling. Hold on. Pump a little bit, and let them know what's going on, like that, like that. Cold on a mission, so fall on back. Let them know that you're too much and this a beat, uh, they can't touch. Yo, I told you. You can't touch this. 

[APPLAUSE] 

Yo, sound the bell. School's in, sucker. You can't touch this. Give me a song, a rhythm. Making them sweat, that's what I'm giving them. Now they know, you talk about the Hammer, you talking about a show that's hyped and tight. Singers are sweating, so pass them a wipe or a tape to learn. What's it going to take-- 

DAVID J. MALAN: Second-to-last level. 

MC HAMMER: (SINGING) Legit. Either work hard or you might as well quit. That's word because you know-- 

DAVID J. MALAN: Last level. 

MC HAMMER: (SINGING) You can't touch this. 

DAVID J. MALAN: Hey! [LAUGHS] 

[APPLAUSE] 

Congrats. All right, that's it for CS50. Welcome. Cake is now served. We'll see you next time. 

[PROJECTOR CLICKING] 

[MUSIC PLAYING]