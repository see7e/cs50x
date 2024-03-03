---
title: LECTURE7 - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DAVID MALAN: All right. This is CS50 and this is already week seven. And this is the week where we'll continue where we left off with Python, introducing you to a bit more syntax and capabilities of the language so you can solve interesting problems. But a lot of those problems increasingly are now going to involve data in some form. 

After all, if you think of most any website or mobile app or process nowadays that involves solving problems, it almost always involves some amount of data and often data at scale. Lots and lots of data. And so what we're going to see first today is that, yes, you can use Python to solve all the problems past that we've seen and also some data specific ones, but sometimes it's just going to be annoying. It's going to be a little painful. It's just going to be more work than you might like to just get to some answer. 

And so today we'll too introduce you to a new language called SQL, Structured Query Language. And this is a language that rest assured is actually much smaller, relatively speaking, than C and Python. It sort of does less, but it doesn't really well. And it's a language for querying databases, storing data in it, updating it, inserting it, deleting it, and so much more. And it's the kind of technology that's used nowadays in, indeed, web apps and mobile apps, data science, analytics, and so much more. It's really good at storing lots and lots of data. 

Now, this is yet another language. And believe it or not, next week we'll introduce you to three more languages, HTML and CSS, which are not technically programming languages. They're all about aesthetics and markup of information. But also JavaScript, which is, in fact, a programming language. But the goals here in CS50 really are going to be to empower you to program more generally. 

And indeed, when you're out there in the real world some years from now, invariably there's going to be some new other popular language out there. And hopefully in this week and next week and beyond, among the goals is not just to teach you these languages specifically but again, how to teach yourself the future languages that we've not even heard about just yet. 

So with that said, let's begin with a survey of sorts. If you go to this URL on your phone or laptop, cs50.ly/favorites, a very simple Google Form awaits you that's just going to ask you a couple of multiple choice questions. 

So go to cs50.ly/favorites, and that should lead you to a Google Form that looks a little something like this asking you first, as of now in week seven, what is your favorite language among those options here. And then further down, one more question. If you think back on problem sets 0 through 6, what was, if any, your favorite problem set problem? Be it in Scratch or C or Python. 

So answer those two questions. And in a moment, I'll flip over to my screen here where you'll see, and anyone who's used Google Forms knows, the spreadsheet that's collecting now this data. Microsoft Office 365 can do the same if you use one of those forms. And what you see here now is a spreadsheet in Google Sheets enumerating all of the audience's questions. Language is in column B, problem is in column C, and each row represents one student who has responded. 

A few of you were super eager for class today at 8:33 AM Eastern time. 10:32, 11:10. OK, so now we're getting into the actual class time here. And if I scroll down, we'll probably see a few dozen, a couple of hundred answers by now. And yeah, so we're getting a whole lot of answers here. And I'm seeing some patterns emerge, but it's not necessarily obvious to the human eyes what those patterns are. 

Now of course, you can use Google Spreadsheets. You can highlight the data and you can create charts magically out of it. But you can only do what Google lets you do with the data. And same thing for Microsoft Excel or Apple Numbers. But wouldn't it be nice to just be able to manipulate the raw data, relatively simple though it is, to just answer questions about the data? Maybe long term create your own charts, customize it just the way you want rather than beholden to software that's off the shelf like this. 

Well, how could we go about doing this? Well, let me propose that we treat this data set now as what we're going to call for now a flat file database. We'll see today that there's fancier databases, but the simplest database in the world is really just like a .csv file. And we saw that a couple of weeks ago in C. We wrote a bit of C code that used fprintf to write data to a file using commas as the separator. 

We didn't really do much more with CSVs at the time though, because it's really annoying, painful, time consuming, not fun to use C for something like that because of malloc and memory and all that stuff. But with Python, it's going to be much easier. 

And so any time you have access to some data set where you can just download it to your own Mac or PC or your cloud environment, it's sort of a candidate for now writing code to do something with the data. Maybe analyze it right away. If it's been human imported manually, maybe you have to clean it up by doing a lot of find and replace but not with your keyboard but rather with code. 

And so let me go ahead and do this. Let me go back to my Google Sheet here that has all of the data that's come in now. And let me go ahead and download this via the File menu here. And let's see. Download. And you can see a whole bunch of options. Most formats might be familiar, but today we'll focus just on this one, Comma Separated Values or CSV. That's going to go ahead and download it on my Mac here into my own Downloads folder. 

And now I'm going to go ahead and do this. Let me go ahead and pull up VS Code in the cloud here. And if you've never done this before, there's a couple of ways to do it. But the simplest way to upload a file to your code space, so to speak, is just a sort of drag and drop. That's going to magically upload it to the server there. 

And we'll see that, one, it has a very long file name, which I'm actually going to clean this up because that's going to be very tedious to type in my code. So I could either right click, of course, up here, but I'm going to use my Linux command. So let's move this file called CSV 50 2022 something or other and let's just name it more simply favorites.csv. So all lowercase, no spaces, sort of good basics. 

And let me go ahead now and open up this file with code favorites.csv. I'll close my File Explorer and we'll see exactly the same data as before but not quite as pretty as Google Sheets makes it be. Rather we see here that I still have three columns, timestamp, language, problem, and then all of the values down below, including the timestamps and the answers they're for. But it doesn't have proper columns. It just has commas separating them. 

Now, we could very easily write Python code just like we wrote C code to manipulate files like this either to write or read. But instead let's do something that's a little more pleasant, which is indeed in the form of Python. So Python actually comes with native support for CSVs. It has indeed a package called CSV that just lets you read and write and do a whole bunch of useful stuff when it comes to CSV files. 

So let's go ahead and do something with this file. Let me go back here to VS Code. I'm going to close favorites.csv for now. But just remember in your mind that timestamp was the first column, language was the second column, and problem was the third. And notice because we're using commas, they don't again line up perfectly, but that's not a problem. There are two commas in every line presumably. 

And I'm going to go ahead and now create a file called how about favorites.py so that I can start writing some code to manipulate this data. And let's do something simple. Let's just write a simple program in Python that opens this file, reads it, and print something out just as a safety check that I know what I'm doing, even though it's not going to be useful. 

So in Python, if you want CSV support, you import CSV. And that gives you access to all the magical capabilities thereof. Let me now go ahead and use this technique to open a file in Python, which is similar in C. 

But with Python, we're going to do this. The keyword with. I'm going to open a file called favorites.csv, which was the shorter name I gave it. This is optional, but just for explicitness, I'm going to open it in read mode explicitly, just like f open took a second argument as well. And I'm going to name this file once open quite simply file, though I could call it anything I want. 

And now it's just an open file. So far as Python knows at this moment, it's just text, or better yet, it's just zeros and ones. If you want this Python package called CSV to actually do something useful with it, you have to load this file now into the library. And the simplest way to do this is to give myself a variable called reader because I want to read this file. Though this too I could call anything else. I'm going to then set that equal to the return value of a function called csv.reader. And I pass to that per the documentation the open file. 

So step one, I open the file. And this just gives me access to the bytes therein. Step two now with csv.reader tells the Python package called CSV to do something useful with it and start analyzing the commas and allow me to parse it further. So let's go ahead and do this. 

Let me go ahead now and within this loop let's say this. Sorry, within this open file, let's do this. For every row, if you will, or line in the file, a.k.a. reader, let's go ahead and print out just how about row bracket 1. Now what's going on here? Well, it turns out if you read the documentation for the CSV reader function, what it hands you back is essentially this special object, so to speak, that allows you to treat it as though it's just a really big list of lines from the file, a.k.a. reader. 

So by saying for row in reader, this is a way more succinct way of saying give me the first line in the file plus plus, give me the second line in the file plus plus, and so forth that we would have done what much more mechanically in C. This is just much more Pythonic and English friendly, if you will. 

So in every iteration of this loop, row is going to contain all of the data from the current row. But better yet, what the reader function does for me is it hands me each row not just as a big string or STR of text in Python. It gives me what apparently based on the syntax on line six. Any instinct? Yeah. 

AUDIENCE: A list. 

DAVID MALAN: It's giving me back indeed a list. And I presume the visual clue for you was the fact that we're using square brackets here. And indeed, row bracket 1 is going to be not the first but the second element in that list. And so just take a guess. When I run this code in a moment, what's going to get printed? The timestamp, the language, or the problem? Yeah? 

AUDIENCE: The language. 

DAVID MALAN: The language because it's the second column that is in the file delimited by those commas. So let me go ahead and do this. Let me clear my terminal down here. Let me run Python of favorites.py and Enter. And there's everything. It was super fast. 

But there's a really long list here. And in fact, if I increase the size of my terminal and start scrolling up, you'll just see all of the raw data. Now, this isn't that useful yet. I could have just glanced at the CSV. But clearly now I have the ability to open the file, parse it, so to speak, that is break it up into its constituent parts, and do something with specific parts therein. 

All right. So if I want to do this a little more pleasantly though, let me at least make this semantically a little cleaner. And you know what, just for clarity, let me just give myself a variable. It's not strictly necessary, but I know that this is the favorite, for instance, language. 

So let's just call it favorite. Set it equal to row bracket 1. And now just to be more explicit in my code, even though again, we don't need the variable per se, this code is, of course, going to do the same thing. It's just using an additional variable called favorite. If I go down here, scroll up, run the program again, I get back to the exact same data. 

But this is a stepping stone to something that's even more powerful about Python support for CSV files is that you don't have to just treat the return value as a list with 0 and 1 and 2. So just thinking intuitively here, why is this maybe not the best design to hand you, the programmer, back the data in a list that's numerically indexed with 0, 1, 2? It clearly works, but critique this. What could go wrong? What's a little poorly designed? Yeah? 

AUDIENCE: You have to always remember what the things are, what the order is [INAUDIBLE] 

DAVID MALAN: Exactly. So yeah, so it's up to you to repeat-- it's up to you to remember what column the data is actually in. And God forbid you're collaborating with someone else on the spreadsheet. If you've used Google Spreadsheets, you can move columns around maybe just because you want to visually reorganize things. 

And if you do this and then someone else downloads that same data, all of their code is going to break. So that's just really bad design. It's fragile just because you're sort of on the honor system that one means the data that you want. So wouldn't it be nice if it could be a little more explicit? 

Well, recall that the very first line in this file is actually this. And I paused the output this time so that we can see more optionally. I just reran favorites.py. And notice one of these things is not like the other. Every output was either scratch or C or Python except for this first one. Why am I seeing the word language here? Where did language come from? You didn't have the ability to manually input. No. Where did it come from? Yeah. 

AUDIENCE: That would be the header. 

DAVID MALAN: Yeah, the header. The very first row in the file, which by human convention generally just defines what the columns represent so that there's some human useful information there. Now, that's not really intended to be part of my output at the moment, so there is a way to skip this. If you want to skip the first row, you can actually do something like this. You can say next row, and that will just ignore that row. So then I'm starting really with the every row thereafter. 

But there's a better way to handle this than that. That will get rid of the row in the output, but let me go ahead and use a different feature of the CSV package that's just going to make this a little cleaner all together. So let me clear my terminal window here. Let me undo this next thing that I just added. 

And instead of using a reader, let me go ahead and use a dictionary reader, abbreviated dict reader, that's going to now return me the equivalent of all of the rows one at a time. So I can still call it reader just as before. But as the name implies, what this reader is going to return is not a list after list after list but a dictionary, a dictionary, a dictionary. And remember, a dictionary is just a collection of key value pairs. So what does that mean? What are the keys? What are the values? 

Well, now that I'm using a dictionary reader, I can actually do this. Instead of on the honor system remembering that I want column one, I can treat row now not as a list but as a dictionary. And that means I can go in here and say quote unquote "language." And we saw that back in week six. Python allows you to index into dictionaries using square bracket notation in strings or STRs on the inside, just like lists allow for numbers. But this now I think is going to be a little more robust. 

If I run this again, Python of favorites.py, of that worked out fine. And let me pause the output too by using this program called more. Now I don't even see the header. So now whoever works with Python wrote the code for this package to just analyze that first line of code, use the header as you just called it as the keys, and then every time you iterate through this loop, it updates the values, the values, the values, but the keys stay the same. Any questions then on this technique? Suffice it to say this would be painful in C. Yes? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Exactly. So the keys are always going to be quote unquote "timestamp, language, and problem." But on each iteration of this loop here, the row is going to contain a different row of values, different row of values, different row of values. So you're going to get back one dictionary for every student who submitted the Google Form, if you will, while iterating through it there. 

All right. So once we have this ability here, why don't we go ahead and transition to how about not just using that dictionary reader, which it makes the code a little more robust. Because now if you move the columns around, no big deal. It doesn't matter if the numeric indices change. You can still use those keywords instead. 

But let's actually analyze the data now. I'm just spitting it out, which is not solving any problems for anyone. So let's go ahead and count the popularity of Scratch, C, and Python and see what everyone's been thinking here. 

All right. So how might I do this? Well, let me go ahead and do this up here. Before I start iterating, let me give myself, let's say, three variables. And to keep things simple, I'll say one variable called Scratch. Set it equal to 0 for 0 students so far. C is going to equal 0 and Python is going to equal 0. 

There's a slightly prettier way of doing this, just because this is like three lines of code to do something very simple. You could alternatively in Python but not C do Scratch comma C comma Python equals 0 comma 0. So kind of slightly more elegant just to fit it all into one line. 

But now let's just do something more interesting. On line seven, I'm still going to figure out what the current favorite language is. And now I'm just going to do some conditional checks. How about if that favorite equals equals quote unquote "Scratch," 

Let's go ahead and increment Scratch by 1. We can't do plus plus in Python, but we can do plus equals 1. How about elif if favorite equals equals C, then let's do C plus equals 1. We could do else. This is actually a good design question. Should I do else? Should I do elif? Any instincts here? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, really good instincts. Just in case someone goes and adds another language to the form next week because we're obviously going to introduce another language today, you don't want your code to now artificially inflate the scores for Python just because you're conflating multiple languages together. 

So the more defensive sort of better way to write this code, I agree, would be elif favorite equals equals Python. Then let's go ahead and increment Python plus equals 1. And if there's a new language next week, we're obviously going to have to update the code, but at least we're not miscounting. We're just missing the new language. So I think that's slightly more robust. 

All right, now at the very bottom of this program and outside of the loop when I'm all done counting, let me go ahead and print out using some f strings. How about the total number of people whose favorite is Scratch? So this is just week six f string syntax. Let me go ahead and print out another f string for C. And I'm, of course, putting the variables in curly braces, all lowercase, but the English words I'm doing capitalization for. Let's do a final one with f Python colon and then in curly braces Python close quote. 

And I think I'm done. So let me just hide my terminal for a second. Here's the total program. Same stuff as before. Open favorites.csv. Open it further with the dictionary reader to do that processing for us. Initialize three variables to 0 just so we have something to count with. And then iterate over the file row by row. And this is just some sort of week one style conditional logic, albeit in Python, counting things. 

All right. So how can we now execute this? Let me go back to my terminal. Python of favorites.py. And here we go. As of today, everyone who's reporting in live via the Google Form, their favorite languages are-- interesting. That's pretty interesting too after just one week of Python no less. But Scratch is a healthy contender there. A lot of C. So a pretty good mix here. 

So is this going to be the best way to write this program long term? Well, as you noted, if there's a new language next week, this week we're going to have to constantly update this. And here's where you should let your mind wander to the future. If we have a fourth language, fifth language, sixth, seventh, eighth, which aspects here might kind of have some code smell to it? This probably isn't the best design to set us up for the future. What might be better than this? Yeah. 

AUDIENCE: We need to add a language to line five. 

DAVID MALAN: Yeah. We have to keep adding a language to line five. And OK, not a big deal. We could add SQL today and maybe JavaScript next week. But any time a line of code, a line of logic, it's just going to grow out of control. We've had this chat a couple of times with different syntax. There's probably a better way than that. 

So let's do that. Instead of using these individual variables, we could maybe use a list, but a list would be a little confusing because what does bracket 0 mean? What is bracket 1, bracket 2? But a dictionary, recall, is this Swiss army knife of data structures whereby you can associate anything with anything else, keys with values. 

So I dare say a cleaner way to solve this problem that sets us up for less work or confusion later would be to create a new variable called counts, if that's what we're doing, counting things up, and just set it equal to an empty dictionary. And you can literally say dict with the open parenthesis, close parenthesis and nothing or the more Pythonic just use open and close curly braces with nothing inside. That gives me an empty dictionary just like square brackets gives me a list. 

Now, my logic down here has to change a little bit. But what's nice is I don't need one conditional for every language. Because again, if we have a fourth, a fifth, a sixth, that chunk of code is also going to grow a bit out of control too. So I can get rid of this here. And what I think I'm going to do is say this. Whatever the current favorite is from the current row in the file, why don't we go into our counts variable at that key? 

And again, favorite is a variable. It's not quote unquote "favorite." It's going to be Scratch or C or Python. And then why don't we go ahead and just increment whatever the value of that count is at that key? Now, this is technically buggy. We're really close, but there is a bug. Does anyone want to conjecture what the bug is? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: A good question that answers my question nonetheless. So no. The magic you describe will not happen. And to repeat the hypothesis, will this automatically create a key for every language that we try plugging into those square brackets? Short answer no. Odds are this is going to create a key error, one of those traceback error messages that you've probably seen by now either in class or in problem sets whereby if Scratch hasn't appeared in the dictionary before or C or Python, then the dictionary has no clue what you're talking about. 

So I think we actually still need some conditional logic but not that's going to grow longer and longer with each language. What I think we probably want to do is this. If the current favorite is in the count dictionary, and this is the Pythonic way of just saying is this key in this dictionary, then go ahead and safely do counts favorite plus equals 1. 

Else, to your conjecture now, else what I want to do. Counts favorites equals, yeah, 1. So initialize a brand new key to a brand new value of 1 because I'm obviously just seeing this language. Otherwise increment again and again. 

And now down here I just need to tweak my syntax a little bit. I don't need to print out all of these things one at a time manually. I can actually get away I think with another loop at the very bottom here. 

So how about I do this? For each favorite in those counts, and this is, again, the Pythonic way to iterate over all of the keys in a dictionary, go ahead and print out using an f string whatever the current favorite is, Scratch or C or Python, and then a colon and then figure out what its count is. And you can do that by going into the counts dictionary, looking at the favorite key, and get back its value. So I close my curly braces. I close my quotes. 

And even though this looks ugly at the moment, now this is much more dynamic. Because if we go and add SQL to the CSV file tomorrow or we add JavaScript next week, this will just work. It will keep working now automatically. All I change is the Google Form, not my actual code. 

All right. Let's try Python of favorites.py. Cross my fingers as always. And there now is the data as of now. Questions on this code here? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Really good question. What if you wanted to print it in a particular order? Well, I could give you a couple of solutions. If you want to print it out in-- it's already coincidentally in alphabetical order. So you got that for free although that's just by chance here. But there is a way to do this. And let me propose that we go down here to my loop. And I explicitly use a function you might not have seen in Python yet, but it's literally called sorted, which is going to take either a list or, in this case, a dictionary and by default sort it by key alphabetically. 

Now, if my intuition is correct, this is not going to change the output, because it's already alphabetical. But if you read the documentation for the sorted function, it takes multiple parameters potentially, some of which are named parameters. 

And so you can actually do this. If you want to the counts but you want to reverse the order for whatever reason here so that it's reverse alphabetical order. Now let me go ahead and rerun this and I'll keep the previous output on the screen. Enter and now it's backwards alphabetically, if you will. Other questions on this here? No? 

How about then we transition to changing sorting by value. And this is going to escalate a little quickly briefly but then we'll tone it down again. Notice that right now this is indeed sorting by key. What if, especially if I have lots of data, it'd be nice to make a top 10 list or, in this case, a top three list and actually see in order of the counts, the values what these popular ones are. So it's not C, Python, Scratch. It should ideally be Python, then C, then Scratch because of the values and the magnitude thereof. 

So how can I do this? Well, it turns out there is another key, another parameter that you can pass to the sorted function that is typically implemented as a function itself. And so I'm going to go ahead and do this. I'm going to temporarily define a function called get value just to make my life easier. And this get value function is going to take I'll say a language parameter. 

And then all I'm going to do is return whatever the count is of that language. So out of context, this is just a super simple function that you hand it a language like Scratch or C or Python, it's just going to tell you what the count is thereof in that dictionary called counts. 

But what I can do now down here in my newly introduced call to sort it is I can tell it what to use as its key. Instead of using literally the key, Scratch, C, Python, I can sort of override that behavior and say, you know what? To figure out what to sort by, go ahead and call this function called get value. 

Notice that I have not put parentheses after get value because I don't want to call get value right then and there. I want to pass the get value function as itself in argument to the sorted function so that the sorted function written years ago by the people at Python can call my version of get value again and again and again when they try to sort this actual data. 

So now if I add that and I leave reverse equals true, let's see what happens. Python of favorites.py. Enter. And now I get my top 10, or in this case, top three list. And if I had more sophisticated data with more columns all together that I actually care about, I could even sort this more powerfully as well. 

But let me clean this up a little bit, just so you've seen it, even though we won't use these that often in CS50 until the end of the class will they come up again. Technically this is a little bit-- this isn't necessarily the best design to spend all this time implementing a function and then only use it in one place. In general, we've argued that you don't necessarily need a variable if you're only going to use it in one place. You don't really need a function if you're only going to use it in one place. And here we kind of have a good candidate for that. 

And so it turns out in Python if you don't want to bother creating a function just to use it once, you can create what's called an anonymous function, a.k.a. a lambda function, like the lambda symbol familiar. And a lambda function, the syntax is a little strange looking, but you say this. You literally say lambda. You literally then say the name of the argument that you want this anonymous function with no name to take. Then you have a colon. 

And then quite simply, you write what you want the return value of this function to be. You don't even say return literally. These lambda functions are meant to be used super tersely so that you can in one line express something like this. And I admit this looks more cryptic, I think, than the previous version. 

But as you get more comfortable with Python or other languages that support this feature, it allows you to not bother with lines of code like that and just tighten up your code a little bit. So this line here, lambda language colon counts language, is the one line version of this. And you don't even need to bother picking a name for it. Lambda tells Python I didn't waste any time thinking of a name for this function. 

So questions then on this technique of using Python to analyze data like this? Any questions? We're almost done with Python. Questions? No? OK. 

So why don't we make things a little more interesting? Because we had a much juicier data set with the problems that we've assigned over the past several weeks. Why don't we go ahead and, quite simply, I think we wrote pretty darn good code here. So I think we can pretty much just change a bit of it to say, let's see, if I don't want language, I want problem. 

And if I want to sort by not language but problem, I think that's it. I think if I didn't overlook something here just by changing what column I'm reading the data from and then just to be consistent renaming my variables just so I know what I'm looking at, what will this program now do after those minor changes? What will I see when I run this? What would be the first thing I see when I run this? Tough crowd today. Yes. 

AUDIENCE: The problem. 

DAVID MALAN: Yeah. The top problem. So the most popular problem, which I'm a little worried it might be hello or just Scratch, but let's go ahead and see. So let me go ahead and open my terminal window. I'll even maximize my terminal window so we can see a lot. Let me go ahead and run Python of favorites.py. I'm going to go ahead now and cross my fingers that I didn't mess up and hit Enter. 

And OK, great. We peaked early. So Scratch was the most popular program according to the data at the time I downloaded it. I'm sure other votes have come in since. Filter in week four was tied then with Tideman as well. Mario is a close third there and so forth. So this is helpful for us on staff that not so much love down here at the bottom of the list. 

So it was a bunch of code to write, but now that we've written it in this very versatile dynamic way, it's pretty good for just like crunching data and doing some analytics. But it's still a decent number of lines to have had to write manually. 

And this is where sometimes it isn't necessarily the right tool for the job, but rather a candidate for using some other language altogether, especially when it's not just a one time program that you run and you want to see the answer. What if you want to take input from the user and answer questions dynamically like a mobile app would, like a website would, like Microsoft Excel or Apple Numbers or Google Sheets would for you. 

Well, let's make one final change for now to this version of the program and actually take in some user input. So besides just loading all of the data into memory, let's go ahead and down below here not just print out the top 10 list, if you will, but prompt the user for their favorites. I'm going to use Python's input function and I'm going to prompt them with "favorite," quote unquote, like tell me what your favorite problem-- what problem rather you are interested in. 

And now let me go ahead and say if that favorite is in the count's variable, so you didn't type in something random that we didn't actually assign as a problem, then let me go ahead and print with a format string whatever that favorite is of yours and show you the actual popularity thereof by indexing into counts using that favorite as the key and printing this. 

So now it's a dynamic program. It doesn't dump all of the data and all of the summations. Rather it's going to allow me to see what my choice of favorite is. And I'm going to go ahead and say, let's see, I'm a fan of Mario here. So Enter. And indeed, we see the same value we saw a moment ago but just for Mario. 

But the point now is that, one, all of this is possible. Two, it's way easier and more pleasant than this would have been in C. This is still only 15 lines of code. And in C, again, there's the memory management. There's the iterating over the strings trying to find the commas. There's just a lot more work. But honestly even when you just want to answer a question like this in Excel and Apple Numbers, Google Sheets, generally, you can just highlight things. You can click a button and boom, you get your answer for summation or max or min or any of those sort of basics. 

Wouldn't it be nice if we weren't taking a step backwards as programmers and being more powerful and yet we now have to do more of the work? So maybe sometimes Python's not or any language is not the best tool for the job. And that's going to now allow us to introduce more generally something called a relational database. Graduating from mere flat file databases like text files or binary files in which all of your data is stored to something more proper. But first, questions. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Really good question. To reiterate, if I were-- is this case sensitive? So if I were to type in Mario in all lowercase and hit Enter, I actually get no such response. Now that might be acceptable, because the problem technically is a capital M. But that's a little ridiculous to be that pedantic about the input. So how could we solve this? Any tips for how we can make this a little more robust? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: OK, yeah. Yeah. So we could use a few different functions, one of which is called title, which will change it to title case where it capitalizes, like in most English sentences, the first letter of that sentence. We could use capitalize. We could use upper. We could use lower. But indeed, we could just decide how we want to standardize the capitalization. Either uppercase, lowercase, or some combination thereof. 

And just make sure that you change the counts themselves. Make sure that you do the same to favorite and make sure that maybe you keep a backup of the data if you want to show the original version that came from the CSV without presuming to just capitalize everything for the user. But indeed, that would be the most common scenario. You just make things case insensitive when doing those matches. Other questions now on Python before we leave it behind for the coming week? 

All right, well then let's introduce these relational databases. So relational database is what every-- it's a super popular way of storing lots of data. This is what the Twitters of the world, the Googles of the world, the Metas of the world use to store some of their data at scale. There are alternatives to relational databases. Indeed, today we'll talk about a language called SQL. 

There's also a movement, if you will, or an alternative generally called NoSQL, which is just the opposite. You don't use SQL. There are things called object oriented databases and the like. But if you've ever heard of MySQL or PostgreSQL or Microsoft SQL Server or Oracle or MariaDB or a bunch of other products, both free and commercial, this is what they're talking about. Databases that are designed to store lots of data. 

And what's nice about relational databases is that they're really similar to the spreadsheets with which you were presumably familiar long before today's class. So a relational database is going to store, as you'll see, all of the data in rows and columns. Now, the terminology will thereafter be a little different. Instead of having sheets, you're going to have tables. But those tables are still going to have rows and columns. 

And you're going to have even more control over the performance of your data when you start to access it using this Structured Query Language or SQL. This is a language you can use for web apps, mobile apps. A lot of analysts would sit down at their Mac or PC and actually ask questions of data to get back the answer. 

And wonderfully, even though there will be some new syntax today, SQL really just does four basic things. CRUD is the sort of crude acronym here. CRUD is a way of remembering that a relational database supports ultimately creating data, reading data, updating data, and deleting data. So even if you're feeling like, wow, this is a lot of new syntax, which it isn't relative to our past languages, the only things you're doing really are creating data, reading data, updating, and deleting the same. 

Now a little confusingly in SQL, the corresponding functions or commands that exist that map to CRUD are actually this. So it's still create, but there's another one called insert. It's not read, which is more of the computer scientist way of saying it, but select, which is a little more explicit. Like select data you care about. Update is still update. Delete is still delete. But there's another command called drop, which lets you drop, that is delete, entire tables as well. 

So you can create tables using syntax that's generally going to look like this. You'll say create table. You'll give the name of the table, which you can call most anything you want, but generally all lowercase, no spaces is best. Then in parentheses, you can specify a comma separated list of the columns that you might want in this table. 

So this is the code equivalent in the SQL language of manually opening Google Sheets or Excel or Numbers and clicking in the top left cell and like typing timestamp and then in the next typing language and then the third typing problem. This is the way to define what your headers are, if you will, in a spreadsheet. But now it's called a table. 

Now, we won't use this command manually first. Let's do something a little simpler. We're going to start off by just importing this data ourselves. And I'm going to go ahead and do this. Let me go back to VS Code here. I'm going to leave behind favorites.py for now, because now we're going to transition to this other language called SQL. 

And to do this, I am going to create a new database file. And I'm going to do so using a command called sqlite3, which is just the third version thereof, and I'm going to give the database a name of favorites.db. There's different conventions, but this is one of the most common. When I hit Enter, this is going to create for me a new empty database just like opening an untitled spreadsheet in Excel, Google Sheets, or Apple Numbers. I'm being prompted do I want to create favorites.db. I'll hit Y for Yes. OK, we're up and running. 

Now, you're going to notice a different prompt. I'm not in my Linux prompt per se, which is always the dollar sign. I'm now inside of the program called SQLite. And we're going to use SQLite, SQLite3, as just an interactive way for now of playing with SQL code. At the end of today, we'll show you how you can use SQL in Python code so that you still write Python code to do whatever you want, but you can talk to databases using Python. 

And this is exactly how web apps, mobile apps work. For instance, on iOS, on an iPhone, an iPad, or the like, if you want to store data, it's very often stored in a SQL database, as we're about to do. But you might use a language called SWIFT or Objective C. And the same exists in the world of Android using Java or Kotlin or something else to query the database. So we're going to see SQL in isolation for now like an analyst might just use with their Mac or PC, but we're going to tie it together by day's end. 

So at this terminal SQLite, let me go ahead and execute this command first. I'm going to first put SQLite into CSV mode, because I'm going to cut some corners initially. And I'm just going to automatically import all of the data that was submitted via the Google Form, which I exported as a CSV and uploaded to my code space. And I'm just going to automatically say turn this CSV file into a SQL database for me just so I don't have to figure out what those create table commands are. 

So to do this, I'm going to say mode csv so that SQLite knows that this is the command, knows that this is a CSV file. It's literally .mode. So the dot comes before the keyword there. And now I'm going to say .import and then the name of the file I want to import, which is favorites.csv. And now the name of the table that I want to create with that data. And just for consistency, I'm going to call it favorites. I could change these things to be anything I want, but I'm going to do that. 

And voila, nothing seems to have happened. But just like in C and in Python and Linux when nothing seems to happen, that's usually a good thing. It means I didn't mess up. So if I want to see what just happened, there's this other command. And these commands that start with dots, these are SQLite specific, which is indeed a lightweight version of SQL. They're not SQL, per se. So if you're using Oracle or something else like that, you're not going to use these exact commands. You'll see the ones we use in just a moment. 

And here's the first. When I type .schema, the schema of a database is the design of the database. What are the tables? What are the columns and all of that? So when I type .schema, this actually in this case shows me the create table command that was automatically drawn for me by just doing this import line. Once I get more comfortable with SQL, I could literally type this out myself or use some program to generate that as well. 

But what it's creating for me is this. Create table if it doesn't exist, even though it's more terse than that. I want to create a table called favorites. And then the columns for that table are going to be timestamp, which is going to be text, comma, language, which is also going to be text, comma, problem, which is also going to be text. 

That was just inferred very trivially by the .import command to just figure out that, yes, just give me a three column database table based on the Google Form. Questions on this? These are commands you run once to get up and running. You don't run these commands frequently, but we have them on the slide just for reference. 

All right. So now let's do something a little more interesting. I'm going to clear my SQLite terminal here, but I'm still in SQLite. I'm going to now use some of my first SQL commands, which recall were among them select. So CRUD, C-R-U-D. The R was select. This is maybe the most common, the most useful, the most powerful thing to use with a SQL database selecting data to answer questions akin to the ones we were trying to answer with Python. This is the general syntax. 

Any time you want to select data from a SQL database, you literally say select. You then specify the column or columns that you want to select data from. You literally write the word from and then you specify the name of the table. You want to get that data from semicolon, in this case. 

Everything that's in capitals here is a SQL keyword. Strictly speaking, you don't have to capitalize things, but we would encourage you to do so stylistically. And especially as you're learning and even as you're writing it, it just helps to distinguish SQL from words you chose, like the names of the columns and the data therein. So do adopt early on this convention. 

So let me go back now to my code space here. I'm running my terminal window with SQLite3 inside of it. Suppose that I just want to get all of the data from the favorites table, which was automatically imported. Let's do this. Select. I want everything. Well, I can do timestamp comma language comma problem. But you know what? Here's a convenience already. If you want everything, there's what's called a wild card character in SQL, which is just a star, an asterisk, which means give me every column without my knowing even what they're called. 

Let me go ahead now and say from favorites semicolon. And this is the SQL way of opening the database, iterating over every row therein, printing out every row therein, done. So those three steps, which was like nine lines of Python code give or take earlier, is now one line of SQL. I hit Enter. There is all of the data. So I see now all of the data. Just output it as a CSV here. But it's not the CSV file. It's now actually the table. 

And in fact, just for good measure, let me do this, because you'll see the behavior a little differently the next time we open the file. I've just exited out of SQLite3. I'm going to rerun it, but I'm not going to reimport the data or do anything like that, because my file now exists. In fact, let me take one step back. If I type ls at my Linux prompt, there's my favorites.py from before. There's my favorites.csv from before. And here's a third file that I did create a moment ago when I first ran SQLite3. So the data is persistent. It's not using RAM or memory. Anything I do now is saved there. 

So let's go ahead and rerun SQLite3 with the same file. But I'm not going to-- I don't have to reimport everything, because the file already exists. Let me now do that same thing again. Select star from favorites to get all of the data. And what you'll see now is the same data, but it's a little prettier now. Because I reran it, I effectively disabled CSV mode this time. And what I'm now seeing is the entire contents of this database table called favorites. Now, there's nothing new here, but you're just seeing now like an ASCII or Unicode version of all of the same data from that database. 

Well, suppose I want to get a subset of the data. Well, let me clear my screen. And just like in Linux, I can Control L just to clean things up aesthetically. Suppose I want to get just the languages. So I could do select language from favorites. And this will now select not all three columns, a.k.a. star, this will only select the language column and all of the data therein. If I hit Enter, voila. Now I just see those there. No timestamps, no problems. It's just a slice of the table, if you will. 

All right, not that interesting still because it's just a big column of data. But now things get more interesting. It turns out in SQL that there are functions that come with this language, just like C, just like Python. In SQL, some of the more useful ones, some of the simpler ones, are these here. Average, count, distinct, lower, max, min, upper, which pretty much do what they say. 

And count is a particularly useful one. Let's start with that. It's a reasonable question to be asked how many people submitted the Google Form by the time I actually downloaded the CSV. Well, why don't we go ahead and do this? Let me go back to VS Code here in my terminal window. Let me select not star but the count of star. So give me the count of the rows that are being returned from the database called-- the database table called favorites. 

Now when I hit Enter, I'm not going to get all of the data. I'm just going to get simply a number. 430 rows came back. So that's pretty good. I now know how much data is in there. Well, what languages were in there? Well, I could do select language from favorites just as before, but that's not that useful, especially if I'm inheriting the data. Like I'm the analyst who's been handed a data set by my boss and they want me to crunch some numbers. OK, I could load this into Excel. I could sort it. 

But you can use SQL now to answer pretty basic questions too. If you want to select the distinct languages in the data set because you weren't privy to the Google Form, let me go ahead and select only the distinct languages from the favorites table. And now I hit Enter and I get back a much more succinct answer. Just the three languages in question. Not really that useful since I created the Google Form, but certainly if you're inheriting data from someone else, you've just downloaded a data set, at least now I'm arguably wrapping my mind around what's going on. 

Now, this is not necessary for such a small data set, but I can combine these things. Select the count of the distinct languages in this data set called favorites. And now I should get back what answer? So hopefully indeed an answer called three. And what you're getting back notice aesthetically too is like a mini temporary table. When I asked for just the distinct languages, what SQL hands me back is this temporary table in memory that has one column called language and then three rows. 

Now, this is not saved anywhere. It's just executed ephemerally like this. But that's why it's depicted in this way. What you're getting is subsets of your data, smaller tables containing some of your data. And same thing down here. This is a crazy long column name. You can rename it if you really want. But that's all we're seeing there. 

And in fact, if that's a little ugly, we can actually alias these things. N is a common name for a variable, a number in any programming language. So I can actually alias this to be a column called n. Hit Enter. And now I'm getting a tiny, tiny table whose column is called n that just has the one value there. All right, questions on these application of these functions here? Questions, yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Say a little louder. 

AUDIENCE: A-S. 

DAVID MALAN: Oh, A-S. As. Literally in English. So rename this column as this. Technically it creates an alias for the column. So that's all. Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Exactly. Distinct will operate on whatever you hand it in parentheses and get rid of all of the duplicates, giving you back just the uniques. Correct. Other questions here? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Good question. When you define an alias like n, which I just did, does it become like a variable you can reuse? Short answer, no in this case, but you can reuse it within your same query. Even though these queries are getting a little longer, admittedly, statements that they are, you can actually reuse n in an even longer query. So later in your query. And we'll see a few that are going to start to grow in length. So it's a nice way of nicknaming things just to be a little more terse in your query. 

So we can transition to some of these more sophisticated queries because it turns out there are some other techniques we can introduce as well. Here are some other keywords in SQL. And again, even though this is another list of things, there's only four things fundamentally we're doing. Creating, reading, updating, and deleting data. These are just allowing us to fine tune how we do it exactly. 

So where is going to allow us to filter data, as we'll do in just a moment. Like select data where this conditional is true. Like is going to be an alternative to an equal sign. So instead of looking for exactly Scratch or exactly Python or exactly C, you can look for something like dot dot dot and it can be a little bit of a fuzzier match, if you will, with other characters as well. Order by is going to deal with sorting. 

Limit is going to just let me limit the total number of rows that come back to 1 or 10 or finite if I don't want to see all 400 plus rows all at once, because I'm just trying to wrap my mind around it. 

And group by is best shown by example. So let's play with just a couple of these as well. Let me go back to VS Code here. I'll clear my screen. I'm still in the same SQLite instance. And let's count how many of you liked C without writing Python code as before. So let me go ahead and select the count of the rows from favorites where the language in each row equals C. 

And the convention in SQLite is to use single quotes any time you're surrounding a string that's meant to represent a literal piece of text as opposed to C, which was double quotes, or Python, which was either. So this is selecting the count of rows from favorites table where the language in question is C. Enter. And this gives me 98. 

Notice, though, if I omit that predicate like we did before, you'll get back the total number of rows that were in the table. So where is what's called a predicate that just allows me to filter things just like an if condition or the like in a language that we've seen before. You can be a little more specific like how many people really liked C and the Mario problem specifically? 

Well, let's do this. Let's go ahead and do select the number of rows from the favorites table where the language is C and. So it's still literally the word ands and or, just like in Python but not like in C. And problem equals Mario. So let's see if there's any fans of both C and the Mario problem. And three of us really like those two things together in this case. 

All right, what else can we do? Well, more compelling might be to see, kind of like in Python, for each language, what was the popularity thereof? And at the moment, we don't really have a way of doing that except in Python where we had the loop and we had those variables and the dictionary that did all of that counting for us. Totally doable but tedious, especially if your job is to analyze data. My God, even writing 15 lines of code to answer simple questions is kind of ridiculous. SQL can do better for us. 

So let me go ahead and do this. Let me go ahead and select every language and the count thereof from the favorites table but this time group by language. So this was another one of the keywords that we can use in this abbreviated list of extra features of SQL. 

And this one takes a moment to wrap your mind around, but this is going to give me a two column temporary table where the first column is a language and the second column is the count thereof from this data set. And group by language just means that only show me Scratch once, only show me C once, only show me Python once. That is group all of the identical values together, but keep track of how many of them there are. 

And so now if I go over to SQLite and I hit Enter, now I have in SQL version the exact same output that I had from Python that took me, what, 15 plus lines before. Now we're down to just one because SQL, Structured Query Language, is all about constructing queries like this to answer questions and get back answers quickly. 

If we want to clean this up a little bit, you asked earlier about sorting order. Well, we can do that too. There's another key phrase we can use here. We can order by the count of those rows and then run that query here. So now unfortunately they're from smallest to biggest, but we can reverse that. It turns out, and my query's starting to wrap here. I'll zoom out for a moment. 

If you want to order by count, the default is in ascending order, abbreviated A-S-C. If you want to reverse the sort in SQL, instead of using reverse equals true like we did in Python, you say D-E-S-C for descending order. And now we get almost the same output but flipped in reverse. So it's just a lot faster to answer questions once, of course, you get some muscle memory and some comfort with it. 

Well, what else can I do? What if I just care about the most popular language? I don't care about the second place or the third place languages or anything else. Well, let me add one more clause here. Limit the answer to one. And no matter how many rows should come back now, I just get the number one language as of the data set we collected with 270 votes for it. Questions on this? Any questions here? No? 

Well, what if we're starting to introduce SQL and it was kind of too late to make it into the Google Form? So it turns out there's syntax for this too. You can create data, of course. Not just the tables, but the data therein and here's the typical syntax for inserting data into a SQL database. You literally say insert into the name of the table. 

And then in parentheses, you specify one or more columns for which you have values that you want to insert. This is to say you don't have to give values for every column in the given row. If you only have answers to some of those questions, you can enumerate them here like this. But the values you insert are going to be these. So you literally say after the close parenthesis values. And then in a second set of parentheses with a same length comma separated list, you specify what values do you want to insert. 

So it's a little verbose. And frankly longer term, you're going to use Python code to automatically do these kinds of insertions, but let's go ahead and try this. Right now if I do select distinct language from favorites, again, we see this. Just these three candidates. But we've now taught you a bit of SQL. So let's do insert into favorites the column called language. 

And you know what? I'm going to give a problem here. The values for which, and let me zoom back out, are going to be quote unquote "SQL" and quote, unquote "fiftyville." You'll soon see what that's all about. Semicolon. Nothing seems to happen, but that's usually a good thing. And now if I scroll back up in my queries, in SQLite3 you can scroll back and forth in time to avoid retyping things, now I should see indeed four candidate languages here. 

Now, suppose that you were never really a fan of C and maybe you programmed a little bit in high school or in the real world and you liked C++. Well, there's a whole lot of answers for C. So select star from favorites where language equals quote unquote "C." So here's everyone who submitted the answer for C. Let's presume that, no, they didn't really want C, they wanted C++, which is not a language we teach in the class. 

But I could also now do this. You can use the update command to set a column or columns to different values where some condition is met. So if I do update table name set column name equal to some value filtering it perhaps by where some condition is true. So suppose I've changed my mind, or you know what, let's go ahead and do update favorites set language equal to maybe C++ where language equals C. 

Now, this is destructive, so you generally don't want to do this unless you have a backup of your data too, overriding what people's answers are. This seems to have been successful, because no error messages. And if I rerun the previous select that gives me all of the favorites where language equals C, now indeed I get none. But if I search for C++, now I get a lot. And if I get rid of that where clause altogether and just look at the contents of my database, now you see that indeed C++ is comingled with all the other data. 

This is not what you all intended, of course, so I can undo this. Let me go ahead and undo what I just did. Let me set my favorite language to C where language equals C++. But the predicate is important. This I'm not going to do. What if I accidentally omitted this predicate, the where clause? How would that screw things up might you think? Yeah, in the back. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: It would set every row's language to indeed C. And this is dangerous. And if you start googling around for SQL mistakes or the like, people in the real world have accidentally run commands like this. And without naming names, a former member of our teaching staff at one point accidentally ran a command like this and changed every student's name in our database to Bobby I think it was. The same name for every row because they simply forgot a predicate. 

So here too there's dangers in code, and you should adopt the habit quite quickly of always, one, backing up your data like with CP, for instance, in Linux or any other technique or just making sure before you hit Enter that, yes, this is indeed the query I want to execute. And generally speaking in the real world, there should be process controls in place. Like the intern should not have access to the production database, the live database, and the like. 

But you have a lot of power now with these queries. So just be all the more careful, because very easily can you do bad things. So let me undo this. Where language equals quote unquote "C++." And I'll zoom back out. Enter. And now I think we're back in business. C is among the answers. Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: It's essentially doing what at the end? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: It's essentially find and replace. Yes. In layperson's terms, this is find and replace implemented with SQL. And in fact, the authors of Microsoft Word or Google Docs might very well be using language like this SQL when you go to the nice graphical user friendly find and replace box. This may very well be what they're doing underneath the hood or, of course, they could be using some other language altogether. 

There's one last syntax that's worth knowing, delete, which for better or for worse is even more destructive whereby it allows you to delete rows from tables. It's distinct from drop, which lets you delete tables themselves. This focuses on rows. 

So suppose that you really, really didn't like, let's say, Tideman was a little challenging if you tackled that more comfortable problem. So if you really don't want to even think about Tideman anymore, so why don't we do delete from favorites where problem equals, and I won't execute it for real, Tideman. This would have the effect of deleting every row, including the language therein and the timestamp, where the student answered Tideman. 

Worse than this would be this. Why might this be bad? OK, chuckling because there's no predicate. There's no filter, which means literally this would delete all of the data. So again, with great power here comes great responsibility. 

Now, this has just been a data set of 430 rows by us dynamically created. There's, of course, some really juicy data sets in the real world. And one website you might have heard or an app you might have used is IMDb, the Internet Movie Database, which wonderfully makes some of their data available for download as CSV files or technically TSV files, Tab Separated Values. 

But what we did in advance of class was download some of that data for both TV shows in the real world and movies in the real world. And what's wonderful about this data set is it's not just dozens or hundreds or even thousands of lines. There are millions of rows of juicy data, TV shows and movies with which most folks are probably familiar, at least with a subset. And we'll see in just a little bit that this data comes in the form of now six different tables that we've given you. 

And the tables in question for today are going to be the people in the TV business, the stars therein, the shows that people are producing and the like. This is a picture we'll revisit to enable you to wrap your minds around what the actual data is. This feels like a good opportunity though for a snack. In fact, in just a moment, we have a whole lot of Rice Krispie treats out in the lobby. But if folks could perhaps acknowledge this mini wedding cake here. CS50 zone Carter Zenke is getting married this week. So congratulations to Carter as well. Congrats. All right. 

[APPLAUSE] 

There's only one piece of cake in that box but a lot of Rice Krispie treats in the transept. Let's take 10 minutes and we'll be back with Internet Movie Database in 10. 

All right. We are back. So if you've never been, you can actually go to imdb.com right now and play around or download the mobile app. And it's just big database of a lot of TV shows and movies and actors and the like. But what indeed is nice is you can download some of that data. And that's what I've done in advance. 

And what we've done is we wrote some Python code to convert some of the flat file databases that they let you download and we converted it into a SQL database with six tables. So not just one but six that ultimately are these here. And let me just help you wrap your minds around what this picture is, which is an entity relationship diagram, which is just to say each of these boxes on the screen represents a table. 

And each of the arrows or edges represents some kind of relationship across the tables. Because up until now, the only data we had were those three columns in the favorites table. But what gets really useful about SQL databases, just like a Google Spreadsheet or an Excel file, is you can have multiple sheets or in a database multiple tables. 

And so what we're about to see is that in the IMDb database for TV shows, there's going to be a dedicated table for all the people in the TV business. There's going to be a dedicated table for all of the TV shows that are in their database as of right now. There's going to be a dedicated table for writers in that industry, for the ratings of shows, for the genres to which shows belong, comedy and the like. And then lastly, there's going to be this table, which somehow associates people with the TV shows that they star in and vice versa. 

And so let's consider first what this looks like in code. And we'll see that it's going to overwhelm intentionally at first, but I'm going to do this. I'm going to go back to my terminal window. And during the break, I downloaded from the course's website a file called shows.db, which we made in advance for you. And if I type ls, I'll see all of my favorites files from before. The CSV, the DB, and the Python file. But now they're shows.db. 

So I'm going to go ahead in my full screen terminal window here. I'm not using actual tabs or code files. Now I'm going to run sqlite3 on the file called shows.db. And I'm just going to see this version information here. Let me clear my screen and run the one command I ran earlier to show us the schema of the favorites database. Now we'll see the schema for the shows database. 

And there's a lot going on here, but let me scroll back up to the very top, the beginning. And we see this here. So when I run .schema, we see a dump, really, of all of the SQL create table commands that were run in order to create this database for you. And one of those tables is called genres and another people, ratings, shows, stars, and so forth. 

And the columns therein, even though it's formatted a little more prettily than the automatically generated create table statement for favorites whereby we have one column per line of output here in the, for instance, people table, there's going to be an ID column, like a unique identifier like a Harvard ID, a Yale ID or the like, a name column, a birth year, and then some other stuff. If I scroll down to shows, every show in the world is going to have a unique ID as well, a title of course, the year in which it debuted, and the total number of episodes as of the time we downloaded the data. 

And then what else is there? Some of these are a little less obvious like ratings here. So ratings don't have an ID column, but they have a show ID column and a rating like on a five point scale or a 10 point scale or the like and then the total number of votes that were collected to contribute to that rating. IMDb allows people to upvote and downvote shows and movies and the like. And then similarly is genre structured. There's a show ID and then there's a genre, which is going to be an English word like comedy or drama or something else. 

And then what else? Let's go a little further at the bottom here for stars and writers. If we go to the very bottom here, stars and writers are similarly structured too. They have a show ID and a person ID. So show and person. And then this writers table has a show ID and a person ID. And there's a whole lot of other words that we'll come to in just a moment. But what is this code hinting at? Well, if I go back to the picture from earlier here, you'll see that this picture captures the relationships among these various tables. 

So for instance, if we focus on shows for just a moment, a show, again, has a unique ID, a title, a year in which it debuted, and a total number of episodes. If you want to figure out what genre or genres a show belongs to, because some shows are just comedies, some shows are just dramas, but some shows are arguably comedies and dramas depending on the episode or the like. So you can imagine wanting to associate two or three or even more genres with a show. 

This line here in this second table allows us to do that. Every row in the genres table we'll see has two items, a show ID which relates to the ID of a show. And that's why these lines literally line up with that specific column name. And a genre, which is going to be like, quote unquote, "comedy," quote unquote "drama," or something else. 

Now with that said, design question. Why have we deliberately not just gotten rid of this genres table and made our lives simpler by just adding a genre column to this show's table? And again, a table is just like a sheet with rows and columns. At the moment, shows only have four columns, ID, title, year, episodes. Why not just add a fifth column called genre and put the show's genre there? Any intuition here? Why not just keep things simple? Yeah, in back. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Exactly. If you add a fifth column here and call it genre, then you have to pick a genre specifically. You have to put in that cell presumably comedy or drama or musical or something else. Now, you could write multiple words in the cell, but generally speaking, that would be sloppy, bad design. Like every cell just like in a spreadsheet should really have one value. It might have multiple words, but it shouldn't be a weirdly comma separated list of multiple things. It should just be in a different cell in that case. 

So if you instead were to design this with just a single column called genre, you're imposing what a computer scientist would call a one to one relationship. Every show has one genre. And that's not necessarily a good thing. Or strictly speaking, it would be a many to one, because the same genre could belong to multiple shows, but each show could only have one genre in that case. 

What a relational database allows you to do, and relational is indeed the operative word, it allows you to factor out some of your information and then have maybe one show here in one row but then in this genres table, you could have one row for that one show genre, or you could have two rows in the genres table for comedy and for drama. Or if it has a third genre, you could just add another row here. So you still have one row for the show itself with all the juiciest details but a variable number of rows by having this relationship with another table. 

Meanwhile, ratings work the same way, at least in this case. A show has ID, title, year, and episodes. But if you want to figure out its rating, you have to follow the arrow here, so to speak, and look up the corresponding show ID in this table. Find the rating of that show and the total number of ratings. So that's been factored out too, for better or for worse. 

Now let's consider people. People have just three columns, ID, name, and birth. But there's no mention of the TV show in which people have starred or the TV shows that a person has written. Well, why is that? Well, if you just had a fourth column here called show, well, you would have to decide what show is that person in. And no one could ever act again in another show, because there's no room to store the data. But if someone, of course, a popular actor can star in multiple shows, well, we could have one ID for that person, one name, one birth year, obviously. 

Like there's only one Steve Carell as an actor in the world of people. But Steve Carell in this example could have his person ID, whatever his Harvard ID equivalent, Yale ID equivalent is, appear in multiple rows in this table so that it can be associated with multiple shows. And this allows you to create what's called a one to many relationship, or technically it's bidirectional. It's a many to many relationship. 

Why? Well, one show can certainly have multiple people in it and multiple people writing for it, just in the real world. But conversely, one person could certainly act in multiple shows or write multiple shows. 

So this is what you get with relational databases. You put your sort of canonical data for people in one place, for shows in another place, and then you use these additional tables to relate one thing to another. So we won't dwell on the pictures. That's just if you sort of can wrap your mind around the data set better that way, that's one way of thinking about it. But recall that the code we just saw for the schema, again, escalated quickly. 

There's a lot of keywords I haven't mentioned yet. But some of these are perhaps familiar. They're capitalized differently here. But integer is on the list here. Null is on the list, albeit technically not null. So let's tease apart some of these keywords and consider what they're actually doing for your database, because now we're exploring features that do not exist in the world of spreadsheets alone. 

So it turns out in a SQL database, specifically SQLite which is the version of SQL we use in CS50 and which is commonly used for things like mobile applications nowadays. It's like a lightweight version of SQL. It's when you aren't trying to run Twitter and have billions and billions of rows necessarily. You've got hundreds, thousands, tens of thousands, maybe even a few million, but not crazy numbers, crazy amounts of data. 

In the world of SQLite specifically, there's these five data types. So just like in C, we had int and char and the like. In SQL, we have these. Blob, which is kind of funny, but it just means binary large objects. So it's like a binary data type. Zeros and ones that aren't necessarily fitting into the other categories. Integer, which of course, is an integer as we know it. 

Numeric, which is kind of a catchall for numbers that are formatted specially. So like a date would be like year, year, year, year, dash month, month, dash day, day. And this is actually a wonderful thing. Depending on the country you're from, you might think your date system in your country is great or it's horrible. The US system is horrible because we have month, day, and then year, which is impossible to sort. 

It is the wrong way objectively to store data. And yet here we are using this at scale. Other countries have gotten this better. Numeric in SQL itself standardizes that stuff. So it doesn't matter what country you're from. You're storing your data in this particular way for instance. Times are standardized and other types of numeric data as well. 

Real is synonymous with flow. So something with a decimal point and some number of digits thereafter. And then text is just for strings and the like. 

With other even fancier databases like MySQL, PostgreSQL, Oracle, and other products you might have heard of, there's even more data types where you have to make even finer grained decisions. But for SQLite, it's indeed pretty lightweight and you or we just have to decide the data types for each column in a table. 

But there's these additional constraints in the world of SQL. You can additionally say that cells in this column may or may not be null. So if you want to protect yourself from yourself so you don't screw up and insert a null, that is a blank value, you can explicitly design a table to have a column that cannot be null. 

And so in fact, someone came up during the break to ask me about my having manually inserted SQL, quote unquote "SQL," into our favorites database. You might recall that I kind of cheated. I just inserted "SQL" quote unquote and "fiftyville," the name of a new problem, quote unquote. But what did I not insert into the database? A timestamp. And I could have. I could have put the current day and time a few minutes ago, but I didn't. 

And that's fine if it's acceptable to you and the product you're building. But I could have prevented that. If we had defined the table to have a timestamp column that isn't just text but it's text that's not null, SQL would have complained and would not have let me complete that insertion. So there's these kinds of built in defenses that you don't necessarily get with a spreadsheet alone. 

And unique means exactly that. If you want to make sure that every row in that column is unique, maybe for email addresses or in the US Social Security numbers or anything that you want to make sure you don't have two versions of, you can specify that the column is unique. And there's other such constraints as well. But again, this is just a list of features that you get from a proper relational database. 

But perhaps the most intellectually interesting one and the most powerful one is what's called here a primary key and a foreign key. And let me go back now to this output. If we look at shows, you'll see that a show, again, has an ID, a title, a year, and a number of episodes. And now the data types might make sense. 

The ID it turns out, just like a Harvard ID, a Yale ID, is going to be an integer. So a simple number. The title, of course, is going to be text but not null. It would be weird if a TV show had no name. That can't be. The whole world would break or your TV Guide and whatnot. So that makes sense there to say not null. Year is numeric. So it's a standardized form. Episodes is an integer, like how many episodes have been produced. 

And then lastly, notice this. The primary key of the show's table is apparently the column called ID mentioned a few lines earlier. This just means that the database will use the ID column as the unique identifier. So it's similar to the unique keyword, but primary key just means the database is going to treat it as special too and make sure that it is uniquely identifying your data. 

But what's interesting is this. Notice if I scroll back up to people, people were sort of similarly structured but with different attributes. Like up here we had a person has an ID, a name, a birth year, and a primary key of ID. So a ID is, again, integer. Name is text but not null, because it'd be weird to have a human with absolutely no name textually. Birth is going to be numeric. But the primary key of people is ID as well. So those are the unique columns that the database will just treat special. 

Why? Well, we just looked at shows. We just looked at people. Let's focus now on this one down here, stars. How do you determine who stars in a TV show? Well, we had two columns. The show ID and the person ID. This is the incarnation of a many to many relationship. One person could be in many shows. One show could certainly have many people in it or writing for it. 

But notice this. Within this table of two columns, show ID and person ID, there's what's going to be called a foreign key called show ID that references the show's table's ID column and then another foreign key called person ID, though I could call these things in parentheses anything I want, that references the people table's ID column. 

Now, you're not going to often have to type commands like this. Again, you set the database up once in the beginning typically, maybe with some help from a TF, maybe with help of Google or the like. But once your database is designed, it's back to the CRUD. Create, read, update, delete, the selects, the inserts, the deletions, and the like. 

But what's this implying? These keywords like primary key and foreign key are what are doing in code what this picture was painting a moment ago. These lines here are drawn literally to line up with the corresponding things. People's ID lines up with person ID. Show's ID lines up with show ID. And so you're just seeing graphical version, code version, graphical, code that creates these relationships. 

Now, given that, let's actually see what these things look like. So let me go back to VS Code here. Let me clear my screen. I'm still within SQLite with shows.db. Let me go ahead and do what I do with any new database. If I ever download something or I'm trying to wrap my mind around a problem, usually it doesn't come with a pretty picture or a three hour lecture to explain what the data set is. Rather you just have the data set in your own knowledge of SQL. 

So let me play around. So .schema shows me all of the tables. That might be a starting point. OK, this is interesting. I know what people are. Let's go ahead and show me all the people. So select star from people. I'm just trying to wrap my mind around what this data set looks like in a more user friendly way. 

That's already a lot of people. As you see the years flying by, there's been a lot of people in the TV business. So this was maybe not the best query to run. But this is indicative of just how large this data set is from IMDb. When in doubt and whenever you lose control over your computer, Control C is your friend to interrupt. 

What would have been better, because I don't think I need to know all of the million people in the world, I could do limit me to 10 people. And that's enough now to get a sense of Fred Astaire has an ID of one, the first person ever. Birth year of 1899. Lauren Bacall and all of these other people from yesteryear. You see that they are the first 10 people in the database. So there's an example of some of the data. 

Now if I want to wrap my mind around what a show is, I know it technically. I know it from the picture. But let's just look at some raw data. So instead of saying select star from people, let me go ahead and select star from shows limit 10. And OK, I've only heard of or seen a couple of these, but these are older shows at that. But I see that every show has an ID, a title, a year in which it debuted, and a number of episodes. 

But perhaps most opaque is going to be this. Select star from stars where this is the table that associates people with shows. Am I going to see any names or show titles here? Not according to the definition we saw earlier. Oh, I should have done my limit. Let me interrupt that. Let me do that again. Limit 10. No. 

And this is where now you're definitely in the programmer world, because this would be the most annoying spreadsheet to use on your Mac or PC ever. If you just had a sheet with all of these numbers that associates one thing with the other, my God, how do you figure out who this is or what this is? You have to manually Control F or Command F looking for the data. But a database doesn't care. Once you know SQL, you can stitch these things back together. 

So what you're seeing here are foreign keys. Foreign keys. Why? Because show ID corresponds to the same numbers from that other table called shows that has a proper primary key called ID. Person ID is a foreign key in this context, because it refers to numbers that belong to really the people table and its ID column. So this is just a way of somehow linking them. 

And so if you think of I always think of this in my mind's eye as this. If this is the people table, this is the shows table, and there's this middle table in between, the stars table. There's some way of stitching those two together by lining up the IDs of one with the other and getting back some more data. 

So let's actually play with some of this data. How about we start where we emphasized earlier, genres. So let me go ahead and take a quick look at all of the genres in this database. So select star from genres. Star is usually going to be a little overwhelming, but it just gives me a sense of what the data is. But let's actually look at-- let's go look at all of them there. OK, that's a lot. These are all official genres from IMDb. OK, it wasn't terribly long. 

Let me filter that down. So from genres where genre equals Comedy, capital C just based on the data I'm seeing. OK, so what am I seeing now? And in fact, let me limit this arbitrarily to 10, though I could limit it to anything I want. Here are 10 comedies. What are they? Well, who the heck knows? All I know are the 10 show IDs. 

Now, I could do something like this. As we've seen before with SQL, I could do, all right, well let's figure out what this show ID is. Select star from shows where the ID of the show I'm looking for equals what? 62614 semicolon. So I could manually look it up by cross referencing the other table. So that was the show in question there, the first comedy in the data set. Let me look up the second one. So instead of that, let's do 63881 Enter. OK. So that's that show. And let's do one more. 

And suffice it to say, this is just getting tedious and vulnerable to mistakes quickly. This surely can't be the way to do this. And indeed, SQL is going to let us do this a little more powerfully instead. 

Let's do this. Instead of getting this table temporarily with all these show IDs and all these genres, let's refine the query. So let's just select the show ID from the genres table where the genre equals quote unquote "comedy." Now I have a big list of show IDs, all of which are comedy. How many? Well, I can combine ideas from earlier. I can just count all of those show IDs or star if I want to just do that too. But I can count all those show IDs. 48,706 comedies on IMDb's database for TV shows. So feels like a lot. 

But how can I now use that information and get back the titles of comedies in the database without doing it manually? Well, let's do this. I have a moment ago this query. Select the show ID from genres where the current genre is quote unquote "comedy." What if I kind of nest these queries, kind of like grade school math in parentheses? What if I combine this whole thing in parentheses? 

And now let me select what I really want. Let me go ahead and select how about the title of all shows where the idea of the show is in this list of show IDs. So if you agree that the shows table has an ID column, which is otherwise known as its primary key, the unique ID that identifies it, just like our Harvard IDs, our Yale IDs, and you agree that per a moment ago this shorter query will give me back just the show IDs of all of the comedies in the database, you can actually combine or nest these queries together. 

It's going to respect SQLite order of operations with parentheses, just like grade school math. So the thing in parentheses will be executed first. That gives it back a list of IDs, like 48,000 IDs. And then this query, the outer query, is going to get the title from all of the shows where the ID of the show is in that big list of 48,000. 

So if I now execute these together, I think the list is still going to be a little long, but let me execute it together. Now I see this long list of outputs. A little overwhelming. Let's go ahead and maybe limit it to just 10 as before for discussion's sake. And now I see 10 comedies ordered arbitrarily from however they're in the database that happen to indeed have comedy as their genre. 

If I want to do this a little more cleanly, I could do this. Let's see. Why don't I order by title ascending order, which is alphabetically, or the default is also an ascending. Limit 10. Now I see the top 10, I mean, weirdly named things with hash symbols presumably to get their titles up to the beginning or maybe these are hashtags. Here now we have alphabetically the first 10 shows that are comedies. 

Any questions on these kinds of queries? It's kind of a lot, but at the same time it's just like composing the smaller ideas from before into slightly more useful queries. Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Do foreign keys have to set the relationship? When you create the table, the programmer or the database administrator would create that relationship by using those keywords primary key and foreign key that teaches the database what is related to what per the picture. So you do that once. And now I being the sort of programmer who's familiar with the database, I am just using these foreign keys in a manner consistent with their design. 

And this is where it's useful at some point, even if no one hands you a picture, to make sure you understand the database, because that's going to inform literally what you type in SQL to get the data you care about. 

Well, let's do something a little more precise. How about-- very reasonable question. And honestly, this is exactly what imdb.com and the app or for. What if you want to find all of the shows that Steve Carell is in? Kind of a reasonable query. Literally something someone might type into Google or more specifically IMDb. It's not really obvious at first glance how to do that, though, because from my database, if these are my six tables, well, I can pretty easily get Steve Carell from here. 

But I can really only get his ID number, whatever that is, his name, which I know already, and his birth year. OK, interesting but has nothing to do with the shows that he's in. I can look at shows over here, but there's no mention of Steve Carell because there's no person ID here. Where is that relationship implemented? Well, it's implemented down here. 

So how do we do this? Well, here's the perfect example of a lesson we've been trying to emphasize for weeks of taking these baby steps. Break larger problems down into smaller ones and let's do something like this. 

Let's just get everything I know about Steve Carell from the database. Let's select star from people where the name of the person is quote unquote "Steve Carell." I just want to see what data we've got. And here's what we have. There's only one Steve Carell born in 1962 and his unique ID is 136797 according to IMDb. This isn't some global actor identifier, per se. 

All right, well how do I get now all of the shows that Steve Carell is in? Well, I could do this. Select star from stars, not to confuse the two. One's the symbol, one's the table name. Where person ID equals 136797. So I think this will now give me everything from the stars table that relates to Steve Carell. And you'll see person ID is the same because I'm literally searching for just Steve Carell. But there are like 20 or so shows that he's been in. 

All right, well here's where things would get tedious. What are those shows? Well, I could do select title from shows where the ID of the show equals. And here's whenever you copy paste, you're probably doing something wrong. OK, he was in The Dana Carvey Show. Familiar with that. Let's do another one. We'll copy paste this. Where ID equals this. Over The Top. Another. And if we keep digging, we'll probably find The Office. But my God, that's going to take forever to do 20 queries manually. It's not very dynamic. 

But what if we just nest these queries a little more dynamically? So let me start from the beginning again. What if we go ahead and select everything we know about people whose name equals Steve Carell. That gave us earlier this data. I don't need all of that data. I know his name. I don't care about his birth year. So let's change this to just be give me the ID of Steve Carell. And that gives me back now this smaller temporary data set. 

All right. Can I now use this inside of another query? Well, let me wrap the whole thing with parentheses. And now let me say select star from the stars table where the person ID equals this. So I'm deliberately not using in because I'm assuming there's indeed only one Steve Carell in the world. So I'm not getting back a list of Steve Carells. I'm getting back the one and only in this case. So equal is fine. In is when you have multiple. Equal is when you have one. Let me go ahead and hit Enter now. 

OK, that's more data than I need. I don't need like 20 copies of Steve Carell's person ID. So let me hit up. Let me go back and let me just get show ID from Steve Carell. And now I have a list of just the 20 or so show IDs that he has been in. 

All right. How can I now use this? Well, let me hit up. Let me put the whole thing in parentheses. And now let me select what I really want. Select title from shows where. And here's the final flourish. The shows table has an ID, has a title, has a year, and has an episode. And what I really want, though, is to check which shows have ID that is what? Anyone want to finish the thought? I just want to-- yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Exactly. ID in this. And this is getting ugly. And when you actually write your queries in a text file, you can format them nicely and indent them. My font is just getting-- I don't want to make it too small to fit everything. But now we have three queries. One is in doubly nested parentheses, then there's the middle one, then there's the outer one. So this last query is going to get me the title from shows where the ID of the show is in this big list of 20 or so show IDs that Steve Carell is in. And I knew that because I looked up his name here. 

And notice what I did not do this time is I didn't manually hardcode his ID number. There's no need. That would be kind of a bad way to implement a website if you're using a database underneath the hood. You want the IMDb for real to search for whatever the human typed in and no one's going to know Steve Carell's person ID or anything else. So here we've done this all dynamically. 

And now if I hit Enter, I think I get all of his shows. Let's go ahead and order this by title just to make it tidy. And you probably will see at least one or more shows that. And probably the most popular is, dot dot dot, The Office. 

So this is literally the kind of query that's being executed underneath the hood when you go to websites or apps like IMDb. Your textual query is probably being plugged into a longer SQL query like this where some programmer at IMDb probably wrote this whole query in advance weeks, months, years ago and they're just somehow plugging in the value that you the human typed into the search box or the like. Questions now on finding this data or any other? No? OK. 

So where else could we go with this? Well, let's consider how else we might combine data. Suppose that the next question actually perhaps appropriately would be focusing in on not just people and shows and these stars, but how do we gather more information about the shows themselves, like the genres, the ratings, or the like. 

So indeed, let's focus on just these two tables here. Recall that every show has an ID, a title, a year, and episodes. But it also might have one or more relationships with rows and this other table called genres. And this is so that a show can be a comedy, can be a drama, can be any number of other things. One row per. So you would see the same show ID again and again and again with a different genre written in English like comedy, drama, or the like. 

Well, how do I kind of reconstitute that data? Well, turns out there's a few different ways to do this. And let me propose that we introduce this keyword here, join. And this is really the most powerful of the keywords in SQL itself. It doesn't have to be used. We've seen with nested queries that you can still select data across multiple tables, but here is another way. 

So let me do this. Let me go back to my SQLite database. And let me select sort of in one breath exactly the data I want. Select star from shows. And let's just limit this initially to 10 to see what it looks like. All right. That's, again, the shows data. Select star from genres. Let's limit that to 10 too, just to wrap our minds around it. And now this is not that useful. 

However, the data in the leftmost column here is the primary key in the shows table. These are just unique IDs. The data here in the genres table, recall, show ID is the foreign key. So it's the same numbers but just copied into another table so that we can have this relationship across them. 

How do I kind of line up these numbers with these numbers to get back a wider table that has title and year and episodes and genre and, heck, ratings and all of that too if we want? Well, you can join these tables by just telling the database what to join on what. 

So let me do this. Select star from shows. Join that table though on the genres table. Well, how do you want to join those two tables? And again, the two tables from the picture looked like this. How do you tell SQL programmatically to put one of them right next to the other, line up all of the ID so that you just get one larger data set? Well, we can use indeed this syntax called join. 

So back to VS Code here. And let me join these two tables. Sorry, typo here. Join genres on the shows table's ID column, a.k.a. its primary key, equaling the genres table's show ID column, a.k.a. the foreign key. So in other words, it looks a little cryptic, but I'm just telling SQL how to line up these two tables and what column to match with the other so that the numbers line up and I get essentially a wider table. 

Let me go ahead and hit semicolon and Enter. And this is now going to give me a lot of data. We might have to interrupt it. But notice even at a glance, we're getting the ID, the title, the year, the number of episodes, the ID again redundantly, but that's to be expected if I'm joining them, and the genre all the way on the right. Let me hit Control C to interrupt. Let me just limit this to The Office. So where title equals quote unquote "The Office" so we can focus on just one sample data. 

And here, fun fact, there's been more than one Office. The one that you all probably like is this one that started in 2005 with 188 episodes. Its ID in the shows table is 386676. That's confirmed over here too. So again, we've just joined the two tables. How? By lining up those fields. But now that we can see that almost all of The Offices produced over the decades are comedies except for this one. There was a version of The Office produced in 2001 that was considered more of a drama. Unsure if it's related to the other. 

How can we link in other data? Well, let's go ahead and link in ratings too or instead. So instead of joining this with genres, let me go ahead and rewind here and join shows on ratings on shows.id equals ratings.show_ID. And let's limit it to The Office too for discussion's sake where title equals quote unquote "The Office" semicolon. 

And now you can see that among the various Offices, it looks like the one that most of us probably know and love is the highest rated also with a 9.0 with like 585,000 people having cast votes for whereas this other shows seem to have been less popular. And perhaps that's why indeed you see fewer episodes for them as well. 

So even though we've put the data in multiple places, you can still kind of reconstitute it by lining things up in this way and rejoining the tables. Questions now on this? This is the heart of what SQL does and what relational databases do for you. Questions? 

All right. A few final features. There's not all that much that-- SQL takes practice like anything else. But in terms of syntax and capabilities, let's just introduce you to a couple of final features here and problems that arise and how we might solve them. Let's do this as well. 

So let me go back into VS Code here. And let's just find out Steve Carell's information again. Last time we did it with this nested query by getting his ID and then the show IDs and then the titles for those show IDs. With join, you can do it a little differently. And any of these ways are fine. One might become easier to mentally than another. 

Let's go ahead and select the titles from what. Let's select the title from the people table. And I'm going to hit Enter. And when you're using SQLite3 interactively, if you ever find yourself with a prompt that says dot dot dot angle bracket, it means you're continuing your thought onto the next line. 

If you didn't intend that, you can sometimes hit semicolon to just end the thought and hit Enter even if it triggers an error. But this is one way of formatting my queries now a little more nicely. I'm just going to add some white space so that it's a little easier to read. 

What do I want to select? Well, I want to select the title of shows from the people table joined with the stars table on the people table's ID column equaling the stars table's person ID column. So in other words, if you think back to what people are and what stars are, one has an ID, one has a person ID, I'm just now connecting those two tables. I'm joining those two. But I want to do this as well with another table. 

Let me additionally join in. So now I only have two hands, but now I'm putting a third table joined in together here. Join shows on stars.show_id equals shows.id. So this is now linking three tables together. But I only care about this for one person, so where the name of the person equals quote unquote "Steve Carell." 

So more cryptic, to be sure, but what we're doing with this query is just taking all three tables that we care about and we're joining them all together at once using this new join syntax literally telling the database what columns to line up with what. And then we filter at the very end just like before to get back, if I hit Enter, the answer we want, which in this case is a little slower at the moment, but that same list of 20 or so shows that he's been in. 

There's one other way to do this. And again, these are all in the slides online. So you can repeat them without having to jot down everything and we'll put them in the notes too. But there's another way to do this. I could also use an implicit join. So that was an explicit join because I literally typed the word join multiple times at that. 

But let me go ahead and select the title from these three tables. People, stars, and shows. And this might just be nicer because if you know what tables you want to select data from, just enumerate them separated by commas, which you might prefer in your mind, where the people ID equals the stars person ID and the stars show ID equals the shows ID and the name of the person equals Steve Carell. So this is an implicit join. 

And honestly, I constantly reference my notes for some of this stuff too. It's not the kind of thing that's going to come like this to you after just one day. But it's just a different way of expressing the same thing. I want to select data from three different tables. And hey SQL, here is how I want you to line those tables up so that I can get like related data for Steve Carell. 

And this now will achieve the same results ultimately. Let me hit Enter. And there we go. So a little slower. And performance might vary based on computer, based on implementation of SQL, but I think I still have the same answers. 

Now suppose, as I often do, and I had to look it up again last time, suppose you forget how to spell Steve Carell's name. Is it two R's, two L's, or the like? Well, I could also do something like this. 

Well, let's just keep this simple. Select star from people where name equals. I've been deliberately getting it right so as to not embarrass myself. That's the Steve Carell I keep querying. If you forget, well you could try searching for just Steves, but interestingly, there's a bunch of Steves. We don't know when they were born. But that's probably not the Steve Carell we want if we don't have his last name. 

So I could alternatively do, well it's Steve and then it starts with a C, I think. Well, it turns out there's another wild card you can use in SQL. We used the asterisk to select all of the columns. You can in quotes use a percent sign to say C something. So there's 0 or more characters after the letter C. And now this doesn't work because now I would be literally looking for Steve space C something. 

But recall earlier I mentioned that one other keyword, which is for fuzzier matching, so to speak, where it's not exactly what you're looking for but it's like what you're looking for. If you instead say where his name is like Steve space C something, now we'll get back a whole bunch of Steves. But I think now I could probably find the one I'm actually looking for if I don't remember his name. You can use multiple percent signs. If you forget what his first name is, you could reverse the order. But that too is a very powerful SQL feature at that. Questions on these queries here? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Sorry? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: What about it? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Oh yeah, sure. So the query I used here. There's a lot of Steves whose last name starts with C. Oops, too far. The last query I executed was this one here. So where the name is like quote unquote "Steve C%." So that's just another tool for your toolkit here. 

But you'll perhaps have notice that those two-- prior to that query, the joins I did were sort of slow. And honestly, this database isn't even that big. Like yes, it has tens of thousands of rows in it. But in the real world and most of the apps you and I use a lot every day or websites, there's millions, even billions of rows of data. And if I had to wait on my computer here or my code space a second or two to get the data, that's not going to work for millions of users or customers certainly. 

So how can we actually improve things? Well, it turns out another upside of a proper relational database is that it's not just a spreadsheet where the onus is on you to find the data you're looking for. You can also tell the database to index the data for you. An index is an efficient cheat sheet for finding data fast. Like books in the real world often have indices at the end of the book where you can look things up alphabetically and then you can cross reference it for the pages that topic appears on. 

Same idea in a database. If you tell the database in advance that you want to search on a certain column frequently, you can tell it to build a fancy index that will just allow you to search that column faster. By default, these columns are going to be searched most likely by a linear search. Not even binary search, because the data might not be sorted because it came in any order. But if you create an index, you're probably going to get something closer to logarithmic than linear, and that's going to be a big plus overall. 

So let me do something simple here. First let me turn on a SQLite specific feature that just is going to time all of my queries by writing .timer on. I just want to keep track of how long each of these commands takes. This one is not a slow command, so this is just going to be relative. But let's just select everything from the shows table where the title thereof is The Office. Let's see how long this relatively simple query takes. 

All right, not very long at all. In real terms less than a second, 0.035 seconds. So not slow by any means. But if you've got hundreds, thousands, millions of users, every one of those milliseconds could very well add up. So can we do better? 

Well, we can if I do this. If I use syntax like this once in the beginning of the design of my database, I create not a table but an index with some name on a specific table on one or more columns. I can give a clue, a hint to the database in advance saying please optimize with some secret sauce searching or selecting on this column in this table so that my searches are faster. 

So let me do this. Let me go back to VS Code here. Let me create an index called how about title index. I could call it anything I want, but I want to search faster on titles. So I'm going to call this a title index where rather title index on the table called shows. And then in parentheses is the syntax. The column called title. So again, I've just borrowed this canonical syntax and I've just translated it into something that's TV show specific. 

All right. What is this going to do for me? Once I hit Enter, this is going to create in the computer's memory, the database's memory something called a B-tree. It's not a binary tree. A B-tree is actually a potentially more efficient data structure that we didn't talk about a few weeks back in week five, but it looks a little something like this, which looks similar to a binary tree. But does anyone notice what makes this not a binary tree? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Exactly. Binary tree, bi implying two, has no more than two children per node, but here's a perfect example, one, two, three. And there could be four children, five children or more. But the effect of that, if you have a very wide tree, the upside is that it's very short. It pulls the data higher up closer to the node, to the root node. 

And recall that the root node is where we began our searches in the past, whether it was a BST, a Binary Search Tree, even a tri or other data structures. We always began at the top. So the higher up you can pull the data, even if it makes the data structure very wide, you're going to be able to do boom, boom, boom, look up queries or look up data probably much faster certainly than if it's just a very long list like a column by default. 

So with that said, let me go back to VS Code. I didn't create the index yet. Let me go ahead and hit Enter and create it. All right, it took a minute, a moment. It took like half a second, which obviously is not that slow. But with more data, that could have been even slower. But it's a one time operation as of now. 

And now let me hit up and let me select the same data from shows where title equals The Office. Last time just a moment ago it took 0.035 seconds. Not slow but also that's going to add up if I have lots of users of IMDb. Let's go ahead now and execute the same query again. How long did that take? 0.001 seconds now. I mean, practically nothing. 

And so that's the sort of opportunity now. When you've got lots of data and you want to really speed up these searches, these indexes, these indices that just create for you these magical data structures in the databases memory, it allows you to search on columns that you are pretty sure you want to search on more effectively. 

Now, by contrast, if you've ever used Google or Bing or some search engine that has advanced search, some of those text boxes that you can search more precisely in might very well be slower. Why? Well, probably you don't want to go crazy and just index every column on every table. Why? 

What might be the intuition? If logically indexes speed things up, why not index everything? There's always going to be a trade off here. What might that be? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, it's going to take a lot of storage. This is just a slide on the screen. But this has to go somewhere. This needs space in the computer's memory or on the hard drive or the like. And that's fine if you have unlimited space, but odds are you don't. And that's going to get expensive for different reasons. So maybe you only want to index certain columns and certain tables and not all of them. 

Because you know what? What even if a user really wants to search maybe via advanced search on some other column or table altogether, fine. If once in a while a query is slow, we're probably getting the bigger bang for our buck by optimizing the common cases, the more popular queries that people actually care about too. 

All right. So let's come full circle and bring this now back to how we actually began, which was with some Python code. So it turns out these are not either or decisions. It turns out in the real world, developers are constantly using one, two, three languages at once. And in fact, next week I rattled off HTML, CSS, and JavaScript, one of which is a proper programming language, but those languages are often used together. 

Totally normal and common to use Python and SQL or Java and SQL or SWIFT and SQL or any number of different combinations with a database language. You might use your preferred programming language, Java, Python, C++ to create the user interface and the logic that implements the program itself. But for your data, SQL's a really good candidate. And indeed, we've seen already that SQL can just speed up certain operations. You can change. You can collapse 15 lines of code into just one and you can use these things together. 

So let me come back to-- I'm going to quit out of SQLite. I'm going to minimize my terminal window. And here's where we left off before with favorites.py. With favorites.py, everything was being stored in favorites.csv. And recall that we eventually imported that CSV file into favorites.db automatically with .import just so we could start playing around with SQL. 

But we can now tie these two together. And a way to do that is as follows. CS50 has a library for Python. You might recall having available get string, get int, get float. You don't strictly need to use them in Python because it's much easier to just use the input function and then try, accept, and convert things to int or float or the like. But it's a lot more work to use SQL in Python without a third party library. 

A lot of the commercial options or popular open source options are actually just complicated to use. So CS50 does have a very useful function inside of its library for Python that you should use and must use for the problem set that just makes it easy to execute Python, execute SQL inside of your Python code. But it's built on top of a very popular open source alternative. So you can use that too in the real world. So the documentation for that is at this URL here, but I'll show you what we need to know here by focusing back on favorites.py. 

So what I'm going to do here is follows is this. Let me delete everything from favorites.py except for let's say this. From CS50 import SQL in all caps. So that's importing a SQL feature from CS50's library that's going to allow me to open a DB file in code. 

How do I do that? Well, let me create a variable called DB for database, though I could call it anything I want. Let me call this SQL function and pass in using special syntax that's not CS50 specific. It's an industry thing. sqlite:///. Unlike every other URL you type, this one literally has three in this context here. And then the name of the database, which in this case is favorites.db. So this is just a way of telling this SQL library that we wrote but that works exactly like third party alternatives open favorites.db using the SQLite technology, if you will. 

All right. Let's just ask the user a question. Give me your favorite problem. So we're going to use input instead of get string, but we could use get string, but they're pretty much the same for our purposes. Let's ask the user for their favorite. And now in Python code, let us select from favorites.db all of the rows where students specify that problem as their favorite. 

So in SQL alone, it would be this. Select star from favorites where problem equals and I'll do, well, whatever my favorite's going to be. Like problem equals Mario, for instance. So if I were just using SQL, I would literally write something like that. But I'm in a .py file now. I have to use Python syntax. 

But Python supports strings. SQL is just text. It's just a string. So I could certainly just put my SQL code in a string perhaps and then pass it to a Python function. And here's the bridge between the two. If you just treat SQL as any old text, we can put it in a string and execute it. 

So let me actually do this. Let me go ahead and create a variable called rows, which is eventually going to contain all the rows from the database. Let me go ahead and select db.execute. This is the one function you need to know about inside of CS50's library, and it literally executes a SQL statement. And then in quotes, you pass it literally what you want to execute. And let me go ahead and close the parenthesis at the end there. 

And now let me just try this. So for row in rows, let's iterate over all of the rows, let me go ahead and print out how about row, quote unquote. And what do I want here? Let's print out the timestamp of that person for kicks. All right, let me open my terminal window. Python of favorites.py. Crossing my fingers here for sure. Enter. There we go. Favorites. I'll type in Mario. 

OK. So I got back-- it's not very interesting, but I got back all of the timestamps of students who typed in Mario that we imported into this database. Well, what I really care about is how popular Mario is. So let me change this a little bit. Let me change this to count the number of rows. And let me keep it simple. Let me give an alias like I proposed earlier like as n, where n is a number. So that now down here, I can actually just do this. Print out the value of n. 

All right. Let me go back to my terminal window. Run Python to favorites.py. Let me type in Mario. Enter. OK, 39. Now, technically I'm cheating. Honestly if I'm executing select count, we've seen before it only ever returns one row, not multiple. So there's really nothing to iterate over, but it's working fine. It's just iterating once, but I'm getting lucky. 

So technically what I should probably just do is this. I should probably give myself a variable called row, set it equal to the very first row and only row that came back, and now print out that rows and column. Let me rerun the program. I'll type in Mario again. Enter. And I still see 39. So of course, I don't strictly need to do this. I don't really need a variable. I can do rows bracket 0 instead. But let me focus on what this library is now doing. 

So per the documentation, what the CS50 execute function always does for you is it returns a list of dictionaries. So if your query returns nothing, like no matches, you get back an empty list. Like open bracket, closed bracket, nothing in it. Any loop is not going to execute anything useful, because there's nothing in it. 

If, though, you get back one row, you're going to get back a list of size one inside of which is a single dictionary. That dictionary is going to have keys that correspond to whatever you selected, be it the columns or the count. So when I selected star before, I would have gotten all of the columns. 

That's how I was able to access timestamp. Here I'm just selecting count and I don't want to have to type this down here. That would just look kind of atrocious. It would work, but it would look weird to just keep retyping count paren star close paren. So I just created an alias called n just to make my life easier or cleaner down here. 

So to be clear, the CS50 execute function returns a list of dictionaries when you're using select. And that is how I can now get back the first and only row and then print out that row's end value. It is identical to-- let me do this. Let me highlight this whole line of text. Let me in my terminal window run SQLite3 of favorites.db like we did before break. Let me just copy paste this query. Enter. 

That's the table I got back earlier when we played with SQL manually. And so when I get back this table, here's the key, here's the value, and I only have one row, which is why I'm just blindly indexing into rows bracket 0, because I know there's always going to be an answer there. It's going to be 0 or 1 or more. But I know now it's going to be called n because of this here. 

So what have I just done? Well, this is SQL down here. And this is just me being like a data scientist asking questions about my data just using black and white SQL queries. This is me now being a Python programmer who wants to talk to a SQL database using Python. And the bridge we're using happens to be the CS50 library. But again, there's third party free libraries you can also use as well. Ours is just very simple. 

And indeed, the documentation will explain how execute behaves a little differently for inserts, updates, and deletes. You don't get back a list because you're not selecting anything, but you do get back some return values. Questions on this? That's the last of our Python code. That ties everything together in spirit. Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: This one here? Yes. So db.execute by definition returns a list of rows. And each of those rows happens to be a dictionary because its convenient. Key value pairs. If I'm selecting the count of rows, I just know from having learned SQL an hour ago that this is always going to give me a single row whose column in this case is called n. So if I know it's a single row, I can just blindly, just like in C, go into that list or an array in C and go to the first location and then treat that as the single row. 

What you don't want to do is this. Even if you the human know the query returns one row, you can't just magically change the variable name to be singular and expect to have only one value. You will always have a list. So even if there is only one value in it, it's up to you to do something like this to get at it. Or if you prefer more succinctness, you can do rows bracket I bracket n. That'll achieve the same thing without a variable. Yeah? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Good. So I have been misleading this whole time and cheating because this is only ever going to return Mario. I'm ignoring the favorite that the human typed in here on line five. So let me fix that. And that's going to lead us to some of the problems that arise ultimately with SQL. The right way to solve that problem-- let me get rid of my terminal window here. 

The right way to solve this problem is not to use an fstring like we did in Python generally, because SQL queries, as we'll see in a moment, can be dangerous. When you want to plug in users' data into a query that you've written most of in advance, you should, you must, you had better use a placeholder, namely a question mark in this case. This is somewhat specific to CS50's library, but we just borrowed the convention that every other library uses too. In the world of SQL, single question marks are used as placeholders. 

And the way you do this is as follows. If you want to plug-in a value for that question mark, just like in printf in C, you specify as a second or a third or fourth argument all of the values you want plugged into this. So in C weeks ago, we were using %s. Same exact idea. In SQL it's a question mark that you use instead. 

This now, if I open back my terminal window and I run Python of favorites.py, type in Mario, I should still get 39. But now I can also type in Scratch perhaps and get 44 for that very first piece at 0. And that one is even more popular here. So this now is correct. 

It would work to use an fstring here and then plug in a value like favorite here. But you'll see in just a moment don't do that. You will expose yourself to potential hack or attacks by trusting the user's input. 

And so in fact, let's transition from that to exactly some of these kinds of challenges, namely two before we wrap up. So in the world of SQL, especially when it's used at scale with the Twitters and the Googles of the world, a lot of data is probably coming into the database all at once because multiple people are opening their phones at the same time around the world. They're clicking on the same links roughly at the same time around the world. When you have thousands of people all using your site at once, order of operations is going to be important. 

But unfortunately in SQL and in other contexts of computing, there's this risk of what's known as a race condition. So for instance, has anyone ever seen or liked this? This is the world record egg. Or it's this thing that was very popular a while back. It's still kind of going strong. But if you go to the Instagram profile for World Record Egg, the goal was to make the most liked Instagram post ever. And they did pretty well. It's just this. It's just a picture of an egg. 

Now, at the height of the popularity, like there might have been hundreds, thousands, tens of thousands of people clicking pretty much at the same time on this egg. So it actually creates a potential problem with the integrity of Instagram's data. Why? Well, if you have all these requests coming in at once, how do you possibly keep track of all of them and update your counter in a way that can keep up with all of that traffic? Why? 

Well, let's just hypothesize what Meta, formerly Facebook, was doing underneath the hood with Instagram if this were their code. So suppose for the sake of discussion that Instagram servers are using a mix of Python and SQL. Probably not using the CS50 library, but they could absolutely be using those two languages or two others together. 

Suppose they do this in order to update the number of likes for that post. They first execute a SQL query like select the current number of likes from a table called posts where the idea of the post equals whatever the unique identifier is for that specific egg in the table. And then they store the result in this rows variable, just like I did. And then they do this. They create a variable called likes. 

They set it equal to rows bracket 0. So the very first row in the result set. And they get the likes key. So this is literally what I just did with the count. Let me hypothesize that Instagram does something similar with the total number of likes. 

Why are they doing this? Because they then want to execute a third line of code that executes update the posts table. Set the new number of likes equal to something where the idea of the post equals this other thing. Now, notice just like in printf there's the comma separated list of values. They want to update the current number of likes from the current value to the current value plus 1. So it's likes plus 1. And then we plug in the ID for this. So suppose this is what Instagram is doing. 

Unfortunately, whenever you execute multiple lines of code independently and you're so popular like Instagram that you have thousands, hundreds of thousands of servers potentially, it is quite possible that if you and I and everyone else in the room clicks that egg at the same time, it's not going to be the case statistically that three lines of code are executed for me and then three lines for you and then three lines for you. They're probably going to get interspersed. 

This gets executed for me and then this gets executed for you and then they get back to doing work for me and so forth just to kind of multitask, just like a human might, but at a super speed here. 

The problem, though, is if these lines of code get interrupted, what could go wrong? Well, suppose that Carter and I both click the egg at the same time and suppose the current number of likes back in the day is 100. That stores in this variable the value 100. But if we click so close in time, we might get back the same answer to this select query. As of that moment in time when David and Carter clicked, it had 100 likes. But then this last line of code is executed for me and then maybe Carter. 

Because that answer, the state of the database, was stored in this variable, then both Carter and I will result in this line of code being executed with the same value. Update the post table setting the likes equal to 101 for that post's ID. Why? Because again, if each of these lines of code running on different servers are checking the value of the current number of likes but then getting interrupted because Carter clicked the darn thing too and then resuming their work on my behalf, we might have a race condition where the code is sort of racing to finish but getting interrupted by other users' clicks. 

And the problem with that is that if you are inspecting the value of some variable, or in this case a database cell, and making a decision based on it, like how to update it, you might now lose data. And Instagram is probably not good for advertising if they're losing likes. And so that's probably a problem not to retain the value 102 and instead insert the number 101 twice. 

It's actually similar in spirit to a story that was told in a databases course I took myself years ago whereby-- it's somewhat analogous to kind of a contrived scenario involving a refrigerator. And this is the closest thing to a refrigerator we could get on stage. But imagine you've got one of these little dorm fridges in your dorm too and your roommate. 

And maybe both of you, as the story was told to me, really like milk. And one of you is at class, but the other of you comes home and you open your dorm fridge and you're like, oh darn it, we're out of milk. And so you close the fridge. You walk across the street to CVS or some other store and you get in line to buy some milk. 

Meanwhile, your roommate gets out of class. They come back to your dorm room. They're really thirsty for some milk. They open up the fridge. They say, oh, we're out of milk. And then they take a different route perhaps to CVS or some other store nearby, get in line to buy some milk. 

Fast forward some amount of time in this very contrived story and what happens? Oh damn it, we now ended up with two gallons of milk and there's no way we can fit gallons of milk in there, let alone two of them. So that's a problem. But what's the relationship to this here? Well both of us, yeah, did what? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Exactly. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Exactly. So to summarize, both of us had a very similar thought process, made a similar decision based on the same information, not realizing that the information, the fridge, was in the process of being updated. And of course, in the Instagram world, it happens like this. In the fridge world, it might take a few minutes. But the problem is ultimately the result of our having made a decision about the state of the world and the state of the world was in the middle of being updated. The queries got comingled with others. Or, in this case, someone was already on their way to the store. 

So what's the solution in the real world? Well, you could very simply take a post it note and put like gone for milk so as to communicate to your roommate that they should not inspect the value of that variable and make a decision on it. Why? Because it's not yet consistent with the outcome that's about to happen. You could be more dramatic and you could actually lock the fridge somehow, put a padlock around it or the like so they can't even get in there. And that would achieve the same effect too. 

And that is actually pretty much the solution to this problem in code too. It's not safe. It's not sufficient to only execute three lines of code like this. Rather, what you probably want to do is use additional SQL keywords that we won't spend much time on in the class itself, but these. There are solutions to this problem. 

You can begin what's called a transaction and you can more explicitly commit to making a decision, like updating the database to 101 or 102. Or if you realize, wait a minute, Carter's query is interrupting mine. Let me roll back to the previous state and just rewind. Let me undo. Control Z, if you will. 

There's also another keyword that's not so much used anymore in SQL which is locking. You could literally back in the day. Lock the entire database table, preventing anyone from updating it or making changes or even reading it while someone else was accessing it. That was a very heavy handed solution because it slowed everything down. 

But in short, transactions are now a feature of SQL that you won't necessarily need to use yourselves that do solve this problem by doing the equivalent of saying while David's like counter is in the process of being updated, keep Carter at bay, ideally briefly, and then let his data go through too. It's equivalent too to putting a note or a lock on the fridge. And indeed, I mean lock literally. They were once upon a time called and still are in some contexts called locks on databases too. 

And the code for which you might do this is almost the same. You simply wrap the three queries with a transaction statement and a commit. And the term of art here is that this makes your statements atomic. So atomic means they're either all executed or not at all. That is they're all very tightly coupled together without interruption. Transactions solves that problem and avoid having two gallons of milk. 

And the last problem that arises that is tragically so darn common in the real world today is what's called a SQL injection attack. And it's what I alluded to earlier with the question mark. So suppose you're in the habit of logging into Yale websites with your net ID or password or at Harvard, your Harvard key and password as well. 

Suppose for the sake of discussion that the people that implemented Harvard key log in allow you to type in your email address, of course, and your password. But suppose that they are using SQL underneath the hood to check your username and password to make sure that you are David Malan or Carter Zenke or whoever you claim to be. 

I haven't shown you the syntax yet, but it turns out that in SQL, -- is a special way of indicating a comment. It means ignore everything to the right. So it's just like // in C or the hash symbol in Python. -- just means ignore everything to the right. And we've, of course, seen single quotes. So one way to wage a SQL injection attack is to try to inject malicious SQL code into someone else's database without them realizing it. How do you do this? 

Well, suppose I log in as malan@harvard.edu single quote dash, dash. I'm not double quoting anything clearly and there's nothing to the right of the -- anyway. But this imbalance is going to be useful. Why? Because if I'm a hacker and I'm presuming someone at Harvard probably is using single quotes to wrap the user's email address and wrap the user's password, what if I try to complete their thought for them and close one of those quotes for them? What might happen? 

Well, we could do this. Here for instance, let me hypothesize is the code that Harvard wrote, hopefully not, underneath the hood. So they're using CS50's library in Python and they're using SQL inside. Suppose that they have a query like this. Select star from users where username equals question mark and password equals question mark. And then suppose they just plug in whatever username and password was typed in. And then if they get back some number of rows dot dot dot, they assume I am David. They assume Carter is Carter if both the username and password are in the database. Just end of story there. 

This is good. This has the question mark placeholder, as we discussed earlier. But what if you don't quite remember that? You don't quite take that to heart and you use your more familiar last week fstrings whereby we use these curly braces to plug in values. What if you do this instead? So it's almost the same idea. It's still db execute but now it's select star from users where username equals. And now notice I'm doing the single quotes, which is required by SQL, but I'm using fstrings with the curly braces. And the password equals single quote password and then close single quote. 

The problem is if you're just blindly pasting effectively the user's input into that web form into the username field and the password field, there's nothing stopping a malicious user, student, faculty, staff from including a single quote in their name. Or maybe even benevolently if their name happens to have a single quote, as some last names in particular do. 

So this is very fragile. Why? Well, suppose that if we plug in my malicious, malan@harvard.edu single quote -- notice what happens to username here. The username variable inside of the curly quotes will get replaced with this. And notice single quote, which the Harvard programmer wrote, malan@harvard.edu single quote which I wrote -- which I wrote single quote which Harvard wrote and whatever else they want after that. 

What's the implication, though, of the dash, dash? Everything to the right is going to be ignored. So the password is never even checked in this scenario. I'm tricking the server into ignoring everything after the -- but I have constructed very cleverly, very maliciously a syntactically valid query. Why? Because I provided the single quote that's going to finish the thought of that first single quote. 

And now I would only know how to do this if I saw the code or if I just randomly try putting apostrophes into web forms and see if things break. That's often how adversaries attack systems. They type in potentially dangerous characters, hit Enter. If something breaks, they're not necessarily into the system, but they know that there might be a vulnerability. And then they start trying more methodically things like this. 

So this then is going to be bad, because it effectively grays out the rest of the query. And this query is surely going to return some rows without even knowing my password. And so this logic here dot dot dot means, well, if a data came back from this query, Harvard is presumably going to assume that Malan logged in. Show him his account or whatever is being protected here. 

So in short, using fstrings bad. Using any equivalent like %s in C, bad. When it comes to SQL, using question marks or whatever a third party library like CS50 prescribes is the way to solve this. Why? Because libraries like ours are designed to at least be smart and be paranoid. And what we will do is this. 

When you use the question marks and the values are plugged in, we will escape any potentially dangerous characters inside of those placeholders. And so effectively, the single quote will no longer be considered a grammatical single quote. It will just be literally a character in the username or password. So the library takes care of this for you because you're plugging in the username and password as separate arguments. And then we or the third party you're using actually sanitize. That is clean up the data and prevent those bad characters. 

Now, this is kind of an internet meme that went around for a while. If you've ever driven a car or been in a car where there's the automatic readers for tolls. This person thought it might be funny to try doing something like this. What are they presumably doing? The presumption here is, whether or not it worked is unclear, is that here's the end of actual license plate number, but here's an interesting single quote and a semicolon. That's especially bad because it means you can maybe execute a second query on the database. This is someone having fun trying to drop the entire database table for whatever municipality is scanning through cameras their license plate code. 

And I would be remiss if we didn't end on this note. At least in computer science circles, there is someone named, no relation to the TF name we put in the database earlier, little Bobby Tables, which ends with this XKCD comic. And if you chuckle, if you laugh, you're now legit SQL programmers. 

Nice, nice. Every CS student out there knows about little Bobby Table. So if you name drop little Bobby Tables now, you're in. All right, that's it though for today. We will see you next time. 

[MUSIC PLAYING] 
