---
title: SHORTS8 - HTML - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

DOUG LLOYD: So we spent about-- if my math is right, and I think looking back-- I think we spent about 35 videos talking about various aspects of C, maybe a little more, maybe a little less. And we didn't cover everything in C, but we covered a big chunk of the language, the vast majority of it, certainly for common uses. Now we're going to talk about another language, HTML. And we're going to cover it in just one video. 

But that's going to be OK. That's going to actually become something you're going to get used to. Now that you have the fundamentals of one language, it's actually pretty easy to start learning others. So we're going to start to step a little back and gloss over the basic differences between these languages and sort of leave you to it. There's a lot of really great resources on the internet, which we're going to start directing you towards because the internet is a vast repository of information. And so it's not like you'll be losing out necessarily by not having the information covered in a video. You'll still be able to get everything you need and use the knowledge you've already built up by understanding C to make the learning curve for these other languages actually a lot flatter. I promise. 

But let's talk about one language that's really fundamental for every web page, which is HTML. HTML is the Hyper Text Markup Language. HTML is a language but it is not a programming language. 

HTML doesn't have variables. It doesn't have logic or functions or anything like that. We can't do any programming per se in HTML. Sometimes you'll hear people describe themselves as HTML programmers, which isn't entirely accurate. We can't write HTML programs. 

HTML is just used to mark up text. It's called a markup language. And what this does-- this markup-- we use tags in HTML and these tags-- this markup-- semantically defines the structure of a page and causes the plain text that exists between tags to be interpreted by browsers in different ways. And perhaps it's best to explain this by way of an illustration. 

Here's a very simple HTML page, not an HTML program, again, an HTML page. And we know it's an HTML page because we've bounded everything with HTML tags. So this is what an HTML tag looks like. It's between angle brackets. And notice at the top we have HTML and at the very bottom, after we've done what is apparently a lot of other HTML, we have angle bracket slash HTML. So that sort of is the boundary between what is HTML and what is not. And of course, conventionally, just as you wrote all of your C programs with dot C extensions, all of your HTML files will end with dot HTML extensions. But there's more going on here. We don't just have these HTML tags. We apparently have this thing called a head tag. Well, OK, what's that? 

Well maybe it's best to distinguish by way of a body, body being the content of the web page. So maybe the head tag defines stuff that isn't in the browser window proper, but is somehow important to our web page being rendered correctly. For example, inside of the head tag we have title tags. 

So title being hello world, that's actually going to be what shows up in the tab in Chrome or in safari or Firefox-- whatever browser you prefer-- that's what's going to show up in the title. And before tabs it would show up in your entire browser window and you can only have one page open in a browser window at a time. So that's going to be the title of my page up in the tab or the browser window bar, hello world. And then the content of my web page will be world, hello. So let's take a look at what some thing like this might look like. This is a pretty simple HTML page. So I'm here in my CS50 IDE and I've zoomed in a little bit. And I'm just going to open up hello dot HTML and show you that this is pretty much the page content that we saw before. My simple HTML, head tags, title tags, body, and so on. I've indented to be clean. 

And then what I can do in my IDE is just preview the page. And there we go. The content of my page is world, hello, and I don't see anything in from the head tags there. It's just the content of the body. World, hello. And again the body just said, world, hello. The other part is missing. 

So that's really all it is. This is a very simple basic HTML page. Now I've indented my HTML to be really nice and organized, but I don't actually have to. I could make it look pretty ugly. And this would still work. This would be the exact same web page. I've just gotten rid of all of the white space. 

As it turns out, white space is data. And so when we're sending data from sender to receiver, from server to client, data costs money. And so getting rid of whitespace is actually a good idea if you're somebody who serves up a lot of web content. It's a bad idea if you're somebody who's learning this stuff and you want to have it nicely organized. This is a lot easier to parse than this. But it's functionally identical. 

The indentation and stuff like that doesn't actually matter in HTML. All that matters is opening tags and closing tags in the correct order. Notice what happened here, though. The markup gives us a way to communicate extra information about what we've written. The Hello, World part was interpreted as the title. And the world, hello part was interpreted as the content or what should be visible on my web page. 

There are over 100 of these different tags and lots of great resources online to find them. We're going to talk about a few of them in this video, some of the really fundamental stuff. But we're not going talk about it all because it would be exhaustive to do so. 

Another thing you can do, though, is open up developer tools. And if you recall from our video on HTTP, I explained how to open up developer tools. In Chrome it's usually the F12 key to open up the developer toolbar. Then instead of choosing the Network tab, you can choose the Elements tab. And if you load a web page, you'll actually see the HTML that creates that web page. And so you can learn a lot about HTML by looking at your favorite websites and seeing how they build the various pieces of them that you like. So maybe there's this cool pattern or something like that. How do they make it with HTML? Well you can just open up your developer tools and hover over that element and see exactly what HTML makes it. So that's a really good way to learn HTML, and I strongly recommend that you do it both to learn HTML and also to learn a little bit about some of the options available to you in developer tools, which will certainly come in handy as you begin doing more intensive web programming. 

So let's take a look at a couple of common HTML tags. And we'll jump and take a look at what these tags will also render as by looking at some files in my IDE. So here are three very basic tags for tweaking the visual appearance of text. There's B tags, I tags, and U tags. And respectively what they do is render the text between them in bold, italics, and underlining. So let's see what that would look like on an actual web page in my IDE. 

So here in my IDE I have a file called BIU dot HTML. BIU dot HTML just being bold, italics, underlining. I'll open it up. 

And we'll see that here I have this text is B tags bold. This text is I tags italic. And this text is U tags underlined. What is this going to look like? Well again, all I have to do is go over here to my browser, my file browser, click Preview, and this is what comes up. 

The text in between the B tags is indeed now bold. The text in between the I tags is indeed now italic. And the text in between the U tags is indeed now underlined. So that's pretty good. We now know how to make text look a little more fancy or draw emphasis to certain things. Another couple of common tags here are paragraph tags, P, and header tags, which I've rendered here as HX. 

These P tags, these paragraph tags, break your text up into paragraphs. It's not enough to just hit Enter and leave spaces, because a computer is only going to do what you tell it to do and it ignores white space for the most part. So we can't just hit Enter and expect our computer to interpret that we want to start a new paragraph. We have to very explicitly say this is one paragraph-- this is another-- by enclosing each in a set of P tags. 

And we also have these options for H tags, these header tags. We have six different levels of headers, one, two, three, four, five, and six, which are progressively larger and larger headers. And they get smaller and smaller and smaller and smaller. So we have a top level header, a second level header, and so on, and so on. 

Let's take a look at maybe some P tags and some header tags in action on a web page. So here in my IDE I have a file called PH dot HTML, PH being paragraphs and header tags. Open that up. There's a lot going on here because I've put some lorem ipsum, some just random text in here. So I'll zoom out a little bit because there's so much going on. But notice that I have at the very top here I have an H1, a level one, header tag. Then I have a paragraph, which is just a bunch of random text-- lorem ipsum-- just default standard filling in text. So I have two paragraphs inside of that level one header and then down below I have a level two header here on line 24, a second level header, and another two paragraphs. Well what does this look like if I view it in my preview? Let's see. 

So notice that the first level header here is actually quite a bit bigger than the second level header. So we used H1 tags. And notice that the P tags allow us to break things out into paragraphs. If we had gotten rid of those P tags and actually just put Enters or Returns in between what we hoped would be the different paragraphs, they would all just slam together and it wouldn't have this nice paragraph separation with space above and below. And so that's what paragraph tags and header tags are commonly used to do to draw attention to portions of our web page in that way. 

Next up are some tags that we use to build lists on our web page. So we have unordered lists-- ULs-- which are just bulleted lists, ordered list which are numbered-- OLs-- and inside of either one of those we need to have sets of how to indicate list items, LI. And so we have open UL tag and we put items inside of it. And then when we're done with that, we can close the UL tag. 

And similarly we can have an ordered or numbered list and put list items inside of that. So let's take a look at a couple of lists and what they would render as on CS50 IDE. So I have here in my IDE a file called lists dot HTML. Let's take a look. 

And notice here I have an unordered list with five things in it. And then I have an ordered list, and I've changed the tag a little bit, right? I've said start equals six. It turns out with an ordered list I can set the starting point wherever I want-- by default it will be one-- by just adding this so-called attribute to my OL tag. And so this list will start counting at six. So the elements of that numbered list should be six, seven, eight, nine, ten, because there are five elements in the list, as opposed to one, two, three, four, five, which would be the case if I had said OL without specifying the start attribute. 

So we'll just preview this so you can get a sense for what's going on here. And there we go. There's my list. The first five elements are unordered or bulleted lists. And the next five elements are a separate ordered list starting from six. So that's how we can build lists using HTML. Another thing you might want to do with HTML is build a table of information of rows and columns to present information in a particularly organized way. To do this with HTML we can have a table definition beginning open bracket table. And then inside of that table we might have a set of rows, TR tags to indicate each row. And then TD tags go inside of TR tags to specify a column within a row. 

Why is it called TD and not TC? Well, TD stands for table data. Usually you're putting your information there. So that's why it's TD and not TC. It's a little bit confusing. 

So you have table tags and inside of your table tags you have a number of rows, TRs. And inside each row you have TDs for the number of columns that you want to have in that particular row. Let's take a look at a very simple table over in CS50 IDE. 

So I have here a file called table dot HTML. Let's have a look at what that looks like. There's a lot going on here but if you notice I have a table open. I'm starting the definition with table. And then in my first row I apparently have four columns, one, two, three, four. And then I'm done with that row. 

Then I start another row and do two, four, six, eight. Finish that row. Do another row, three, six, nine, 12. And then a last row, four, eight, 12, and though it's a little cut off here, 16. 

I finished that row. I finished the table. And then I'm done with my HTML. What does this look like? Well, it's not really much to see. I've clearly organized my information in a somewhat more organized way. But it's not super pretty here. And we're going to deal with that when we talk about CSS. We'll revisit this idea of what we do to make a table-- maybe format it a little bit better? But I do still have four rows, each of which has four columns, and really what this amounts to is a very simple four by four multiplication table. 

Just a few more tags we'll talk about. Let's talk about the concept of an HTML form. So you may have seen this in the context of logging into a web page. Usually you type in your user name. You type in your password, and you're good to go. That would be the beginning of a form. 

Skipping over div a second. We also have inputs which kind of fit inside of forms. These are the elements that you're actually typing into, or the radio buttons you're ticking, or the check boxes that you're ticking off. So these go inside of forms. And they comprise basically each row of the form if your form is formatted well. Then there's this concept of a div, which doesn't really fit in any particular category of tags like the ones I've been doing previously. It just sort of demarcates the beginning of some arbitrary division-- div-- of the page. There's no visual break. There's no line. It's not set off as a separate chunk automatically. You'd have to style it that way to do that. 

It just sort of says I want a piece of space on my web page, and I'm just going to call it this division of my page. We can put stuff inside of divs, and in fact, when we head over to IDE in a second, we'll see that I'm putting my form inside of a div. 

So I have here in my IDE a file called div form dot HTML. Let's open it up. Notice that like I said, div is kind of arbitrary. Right? It doesn't really mean anything. So I have an arbitrary first division of my page. And then instead of another div later on, starting on line eight, I have this form. And inside of the form I have a number of inputs, fields of the form. So I have a field whose name is A-- which doesn't really mean anything right now-- that apparently takes text, another one that takes a password, another that's a Radio button, another that's a check box, and another that's a Submit button. Well, what does this all actually look like? Well, let's take a look. We'll open it up in our preview window. Notice that this arbitrary first division-- there's no visual separation here. It didn't really do anything, right? 

And then I have my form. And I didn't do any special formatting. So the form is just one big row of information. If I had formatted my form differently, I might have it line by line by line. But I didn't do any styling. Again, we're not talking about CSS here. We're just talking about HTML. 

Well in my text form I can type-- remember that forms of type text so I can put my name. And in my password I can type my password. And because that field is of type password, you don't know what my password is. It's all dots. 

I can also choose to tick off a radio button or tick off a check box. Or I could submit my form. And I didn't do anything, so when I submit my form, the page just refreshes. But I could perhaps configure my Submit button to do something else. And we'll see what we can do with that in a future video on PHP. But this builds a very simple form that we can use to have users interact and submit information to our website. 

One last comment before we move on to some other tags are to take a look at this input tag one more time. Notice that I've highlighted the ends of the tag in red. Every other tag we've seen so far has had a beginning and an end, an opening tag and a closing tag. 

But an input tag doesn't. There's no text that goes in between input tags. All of the information we're intending to convey is bound up as part of the attributes of that input. Notice we have input name equals x. Type equals y. That's really all the information we need. 

This is called a self closing tag. It doesn't require an opening and a close because all of the information is contained inside the tag and its attributes. So sometimes you'll see this, too. So just be aware that if you have a tag that is entirely self-contained, it opens and closes itself with the open angle bracket on the left and the slash angle bracket on the right. We'll see another one of those right now with image tags as well. 

Before we talk about images, we need to talk about hyperlinks. If we want our web page to be interactive and move us around, it would be nice be able to click on one of those what has typically been a blue link. This is actually how we build a hyperlink in our web page. And interestingly enough there's another HTML tag called link, which is not a hyperlink. A here stands for anchor, and that's how we indicate a hyperlink. 

A href equals x means go to web page X. And everything between the open A tag and the close A tag is what's going to be that underlined blue text that looks like a link that we're familiar with. Below that we have an image tag, which is a self closing tag for displaying an image located at X. And you might be able to change that image by specifying width and height and other attributes in that dot dot dot there. 

At the very bottom here we have a very interesting looking tag that doesn't have a closing tag. It's exclamation point doctype HTML. So HTML has been around since the early 1990s for building web pages, and it's gone undergone several revisions since then. Most recently in 2014 it underwent a revision called HTML5 which is now the current sort of de facto HTML standard. 

To indicate that our web pages are written using HTML5, this is how we start off. It can be omitted but what that basically means is you can't use any of the tags that are HTML5 tags, those new tags. So we always start off if we're using HTML5. And all the tags we've talked about previously are not HTML5 tags. But this would indicate that HTML5 tags will be present. And so we have exclamation doctype HTML, which is at the very beginning of our HTML file, and then after that point we actually have our HTML open tag and proceed from there. 

The last one is a comment tag, which looks slightly different, too. It starts off with angle bracket exclamation dash dash but no closing bracket. In between those two elements there is where you write your comments. And let's take a look at images and comments and links in CS50 IDE. 

So I have here a file called image link dot HTML which I'm going to open up. And notice I've got a couple of comments here in my HTML comments. So just like in C and other programming languages, HTML just by being a markup language does have the ability to have comments. And so I'm apparently going to place a picture of Rick Astley somewhere between this div tag, this arbitrary division. Apparently that file is located at Rick dot JPEG, which if we head back over to my file tree for a second, is a file that exists in the current directory. So that's OK. I can reference it. 

Then I can have internal links. So notice on line 11 here my href is hello dot HTML. So that just refers to hello dot HTML which exists in the current directory. And I can also have external links by just specifying HTTPS to indicate that I'm not talking about a file in my current directory. I'm talking about a file that exists somewhere on the internet, which I have to request using the HTTP protocol. 

So let's take a look at what this page might look like and get ready for a picture of Rick Astley to show up on your screen. So I'll preview this. There's Rick Astley at the very top in this arbitrary division I put it at the top. And then down below I have my links, right? 

I have a link to hello dot HTML. And if I click that, I get moved over to this page that we're very familiar with from the very beginning of our program. If I pop that page open again, if I pop image link open one more time, I can also go externally to CS50's website. And there we see-- I'll zoom out a little bit here-- we'll see CS50's website sort of embedded in the middle of our page. So I was able to make an internal link as well as an external link. 

The last rule with HTML that we're going to talk about here is that your HTML should be well formed. In C we talked a lot about the various syntax of things. In HTML the syntax really revolves around tags. Every tag you open needs to be closed. And in fact, every tag you open should be closed in reverse order. 

So if you open a bold tag, an italic tag, and then an underline tag to do all three to a particular set of text, you should close them in reverse order. So if you opened bold, italic, underline, you want to close underline, italic, bold. This sort of encapsulation is what keeps HTML nice and organized. 

Unlike C, though, syntax errors won't actually cripple your HTML possibly. Your HTML may be not well formed but would still work. And so these errors can sort of slide by. It's up to you to really be vigilant. Sometimes they will fail but sometimes you can get away with it. 

It can be a really difficult task, though, to keep track of when you opened a tag, when you closed it, especially as your HTML files get bigger and bigger. You'll want some help. And there are online validator tools that you can use to have a look at your web page and see if it's well formed HTML. And you should definitely take a look at those and start to use them as you begin doing some work with HTML, writing HTML, just so you get some good habits about organizing your HTML in a good way and good style and making sure that you're not doing anything that could create a syntax error that would cause you a bit of a problem down the road. 

I'm Doug Lloyd. This is CS50. 