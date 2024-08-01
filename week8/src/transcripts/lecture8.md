---
title: LECTURE8 - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] [VIDEO PLAYBACK] 

- All the way to the top and then you pass it down. 

- This is for you, Yale. We love you, Yale. 

- We're here to cheer for Harvard. 

- Yeah. Go Harvard. 

- Take one and pass it down. 

- Pass them down. 

- It's not gonna say something like Yale sucks is it? 

- It says go Harvard. 

- We're nice. 

- You see that [BLEEP]? Look at them. They passed the paper. It's gonna happen. It's actually gonna happen. I can't [BLEEP] believe it. 

- What do you think of Yale? 

- They don't think good. 

- It may be a complete mess, I don't know. 

- You can't really fix it now. 

- Does everyone have it? Does anyone have their stuff? Does everyone have their stuff? 

- The probability that it's going to be legible is very small. 

- I agree. 

- It's too complicated. 

- Look at all the signs. 

- I know, but it's too complicated. 

- What houses are you guys in? That's not a real house. 

- How many extra are there? 

- Ho-fo? 

- Yeah. 

- You guys aren't from Harvard are you? 

- No, Pfoho. Pforzheimer. 

- Yeah, but she said ho-fo. 

- Well, she's probably drunk. 

- Does everyone have their stuff? 

- Are all the cards distributed? 

- All right, let's do it now. 

[CHEERING] 

- Yeah, look. 

- Oh my God. It's gonna work. 

[CHEERING] 

- Hold up your signs. 

[BLEEP] 

- You suck, you suck, you suck, you suck, you suck, you suck. 

- We [BLEEP] did it. [BLEEP] 

- You suck, you suck, you suck, you suck, you suck, you suck. 

- What do you think of Yale, sir? 

- They suck. 

[LAUGHS] 

- They suck? 

- One more time. One more time. 

[CHEERING] 

- Oh, there it goes again. 

- Harvard sucks, Harvard sucks, Harvard sucks, Harvard sucks, Harvard sucks, Harvard sucks, Harvard sucks. 

[END PLAYBACK] 

ADAM: All right. This is CS50. Welcome to week eight. Last week we learned how to create, read, update, and delete databases using SQL. But this week-- 

- Adam, everyone. Happy Halloween. 

[LAUGHS] 

[APPLAUSE] 

DAVID MALAN: All right. So this is the CS50 and this is week eight already. My thanks to Adam on today, this Happy Halloween. In the coming moments, we're going to learn all about how the internet itself works, which of course, is a technology that we all use every day, probably using in some form right now. But we'll see that if you start to understand some of the underlying building blocks that power the internet itself, we can actually start to build interesting things on top of it. 

And a lot of the apps, the websites that you all use every day should become all the more familiar, things that you yourselves can create. And honestly when things go wrong, you'll have all the more of a mental model for how things work or are not, in fact, working so that you can ultimately diagnose all the more issues yourselves. 

So if we take a look at the internet in the early days, it pretty much was just this. This happens to be, of course, the geography of the United States. And just some of the first points on the internet were these here. This was so called ARPANET back in 1969. And indeed, the internet had its origins here in the United States with just a few computers interconnected somehow initially. That, of course, began to grow over time such that we eventually had the West Coast connected to the East Coast. 

And nowadays what you can think of these dots on the screen as representing are these things called routers, sort of computers or really servers that somehow have wires or maybe wireless connections between them that allow data to flow from point A to B to C. And then this, of course, has been now magnified across the entire globe and even above ground as well so that we can connect all the more readily to systems anywhere. 

Now, in order to route the data from one router to another, we need to somehow make routing decisions. And this is the kind of thing that the internet service providers, the ISPs of the world just handle for us. You and I plug our Macs, our PCs into the network here at Harvard or equivalently at Yale or we somehow get online via WiFi or cellular technology. 

And then some of these larger entities, these bigger companies or countries, handle most of the data getting from point A to point B. And if you think about what these routers represent, they're indeed just servers somehow interconnected, not unlike this grid of tiles here, for instance, back in the Zoom days. And in fact here we have, I claim, a grid of routers implemented here by the course's teaching fellows and course assistants and TAs. 

And if the goal at hand, for instance, is for Phyllis to route some piece of information, maybe it's an email, maybe it's a request for a web page in the bottom right hand corner, all the way up to, say, Brian here in the top left hand corner. Suffice it to say if each of these tiles represents a router, a server that can move the data back, forth, left, and right, that packet of information, so to speak, from Phyllis to Brian could take any number of different possible routes. Up, down, left, right to go from the one corner to another. So let me go ahead and hit Play on this video here wherein the teaching fellows play this same role. 

[VIDEO PLAYBACK] 

[MUSIC PLAYING] 

[END PLAYBACK] 

DAVID MALAN: All right, so in this particular case, the data was routed pretty straightforwardly up and then to the left. But suppose that one or more of the staff were a bit busy. Maybe one of the routers is congested. That is to say, just get way more envelopes at a moment in time that it can handle. 

Thankfully the design of the internet is such that there's often multiple ways the data can get from point A to point B, maybe going through point C or point D instead. And so there's a resilience there even as some of the servers themselves might go down. So allow me to propose that we use the same grid of routers now to route the data in a slightly different way this time. 

[VIDEO PLAYBACK] 

[MUSIC PLAYING] 

[END PLAYBACK] 

DAVID MALAN: So success. You'll see perhaps later just how many takes it took us to actually get that routing right. But it does in fact manifest that you can travel different paths in order to get the data from point A to point B. So as we talk about routers, as you think of the internet, I mean, think of those humans as just representing these routers. Points A to P and everywhere in between. 

Now, how do the teaching staff know to route that packet up and then down or left and right in order to get to the destination? Well, all of them were programmed, so to speak, to understand protocols. It's called TCP and IP otherwise known together typically as TCP/IP. And you've probably seen these acronyms at some point in the real world, on the internet, on some kind of documentation, a text even if you haven't really thought hard about it. But IP is certainly the more common of the two perhaps in common culture. 

So what does TCP and IP do for us? Well, really two primary things. Any computer or any teaching staff member who understands TCP/IP knows how to get data from point A to point B. But how? Well, let's break down what that problem to be solved is. IP, otherwise known as Internet Protocol, is a protocol that computers speak that allow them to know how to address computers on the internet. 

And a protocol is just a set of conventions that computers adhere to. So someone wrote code that probably has a whole lot of conditionals that tells the computer what to do if something happens. Like if I receive a packet, then send it to the next server or something like that. 

In the human world, we have protocols too. In healthier times, it was quite common to extend your hand to another human in order to greet them. And if they're following human protocol, they would presumably grab your hand and shake it, at least in a culture like this one here on campus. And now that is a human protocol in that someone initiates it, someone responds to it, and you both sort of know what to do. Your programmed to know what to do. So same idea with internet protocol. Computers just know what to do when they've been programmed to do so. 

So what does this mean? If IP decides that every computer in the world will have a unique address, just like the Science Center around the corner might have a unique address of 1 Oxford Street, Cambridge, Massachusetts, 02138, USA. IP dictates that every computer on the internet have a unique address of this form. And this too is probably something you've seen in the real world even if you haven't thought too hard about it. 

It's a number and what's called dotted decimal notation, which means it's a decimal number dot something dot something dot something. So four digits separated by convention by decimal point, although there are newer and bigger versions of the same. And these so called IP addresses that might be as simple as 1.2.3.4 uniquely identify a computer on the internet. 

The numbers have to range from 0 to 255 each. And that's a bit of a hint just as you start to think more computationally. If each of these is a number from 0 to 255, how many bits does that suggest each number is using? Feel free to shout it out. How many bits gives us 255? 256 total possibilities. So eight bits. 

That should just be sort of a heuristic in your mind. Anytime you hear something that's in the range of 0 to 255 or 256 values total, think back to week 0, which gives us eight bits plus another eight bits another eight bits and another eight bits, which is to say an IP address typically is 32 bits in total. 

Now, if we do another bit of quick mental math or think back to week 0, if every IP address is 32 bits, how many computers can we have on the internet at once? Give or take. Roughly 4 billion is the ballpark. And we don't need to be super precise for discussion's sake. But roughly 4 billion is how high you can count, assuming no negative numbers, if you have 32 bits in total. 

Now, that's not terribly many numbers of addresses, especially considering the number of humans in the world, the number of us that do have laptops or desktops or devices more generally, phones in our pockets and the like. 

So let me just stipulate for today's purposes that there's even a newer and improved version of IP otherwise known as version 6. This is version 4 but still super popular. Version 6 uses 128 bits, which is a huge number of possible permutations. I daresay I can't even pronounce that number it's so big. So there are ways around even this limitation already. 

So every computer has an address like this. What does that really mean? Well, suppose that I was Phyllis in the story told visually earlier and I want to send a message to Brian. Well, both Phyllis and Brian have IP addresses. And suppose that Brian's IP address happens to be 1.2.3.4 in that top left hand corner. Well, Phyllis's Mac or PC or phone would essentially do the equivalent on this human envelope by writing the two address in the middle of the envelope, as is our human convention, like this. 

So this is an envelope, a piece of information, an email, a text message, whatever destined for Brian. And so she would have her computer put Brian's IP address in the middle. Her IP address is maybe 5.6.7.8. So just like our human convention, I might write 5.6.7.8 at the top of the envelope. Five, six, seven, eight. Thereby indicating what the return address is. And this is helpful, because if Brian's computer needs to acknowledge receipt, if he needs to reply in some form, this way the envelope has all the information we need. 

But in the real world, servers do a lot of things nowadays. Not just email but maybe chat, maybe video conferencing, maybe any number of other services as well. And so it turns out that an address alone might not be sufficient, because how does Brian's computer know when he opens the envelope, so to speak, that this should be interpreted as an email or interpreted as a chat message or interpreted as a video attachment that Phyllis has sent? Well, we need some other mechanism, some other hint on this envelope to distinguish one type of internet service from another. 

And so that's where the other acronym in TCP/IP comes in, which is TCP. So this stands for Transmission Control Protocol, which is just a different set of conventions that computers adhere to in order to solve a couple of different problems. One is this problem of distinguishing one type of service from another. Now, what does that mean? 

Well, humans decades ago decided as they started inventing all of these various internet services, the web being the first one, how they might-- or the web now being the most popular ones. They decided to assign different services that can be used on the internet unique numbers. And so two of the most common are these. 80 is the number that a bunch of humans decided years ago will represent what you and I know as HTTP. 

And we'll talk more technically in a bit about what HTTP is. But obviously it's the thing that's in the beginning of every URL nowadays. Or HTTPS, which, of course, has the S added to it. And that has its own unique number. And for now, the S just means Secure. One is encrypted or scrambled somehow for privacy's sake and the other is unencrypted. It's a little more vulnerable to interception. So these two numbers are what the world decided when implementing TCP shall uniquely identify those services. 

So what does this mean? Well, this means that if Brian's computer in the story from before is hosting not like an email server but maybe he has a website and Phyllis is requesting Brian's home page or something like that. She would have her Mac or PC or phone not only write Brian's IP address in the middle of the envelope but also the number, otherwise known as a port number that she wants this envelope to be routed to. Now, 80 would be insecure nowadays. HTTP:// is sort of passe and we almost always see HTTPS:// now. 

So I'm just going to go with best practice and I'm going to add a colon and then the number 443 at the end of Brian's IP address. So now I have an IP address for Brian, the port number for the service that this is relevant to, and I'm not going to bother writing it, but it turns out that Phyllis's computer would also choose a port number, maybe a random port number, so that Brian can conversely reply. 

And then the computer can know which response is coming back for which request. But the most important one is this one in the two field whereby this distinguishes this from an email, a chat message, a video conference session or a Zoom or whatnot from anything else happening on Brian's computer at the same time. 

So all this time if you've seen these terms TCP and IP, those are really two of the most important things that they do. But TCP does one other thing that's super useful too. It turns out that it's super common nowadays especially to transmit a lot of media on the internet, whether it's an image or maybe it's a movie file, and it would be a little obnoxious, to say the least, if your downloading a really big file meant that no one else in your dorm room or your household could actually download anything until you're actually done. So of course, multiple people nowadays can be on the internet at once even if all of the connections are a little slower. But one person's usage does not block someone else's. 

Now, how does this work? Well, TCP/IP in conjunction with IP can also allow you to take a really big image of a cat, which the internet of course is filled with, and take a big image of a cat or a big video file of a cat and fragment it into multiple pieces. So I'm just going to roughly tear it down the middle and then maybe tear it down the middle again. So now it's four different fragments. And I'm sorry, but the computer will be reassembling these for us. 

And what Phyllis's computer could do now if she's uploading this picture of a cat to Brian's web server, well, she could put one fragment in this envelope and then have three separate envelopes for the other three fragments. And what she could then do on the outside of this envelope is just kind of number them somehow. And in fact, this is something else that TCP and IP together would do for us. This first envelope now might say something like one out of four in the memo field, so to speak, of the metaphorical envelope here. 

Now, this should be enough information. Because now if Brian gets all four of these envelopes, he presumably knows how to reassemble the picture of the cat in order top to bottom, left to right. But more importantly, suppose that one of the routers, one of the TFs in the video is sort of distracted and they sort of drop one of the packets. And that's a metaphor actually in practice for when a router gets really busy. It's got way too much data coming in. It might metaphorically drop packets. 

What does that mean in practice? I mean, it literally just ignores the zeros and ones. It doesn't save them to its memory, because there's just no room left. So it's equivalent to dropping the packet. 

So suppose now that Brian gets one of four, three of four, and four of four. What can his computer infer now after receiving those three packets? One of four, three of four, and four of four. What's the use there? Yeah, I think you're signaling with your fingers which one-- can I call on you? 

Yeah, so he's missing two out of four, the second of the packets. And this is useful now because you could imagine he can send some message back to Phyllis saying, hey, please retransmit number two of four without having to redownload the entirety of the cat. So there's an efficiency there as well. 

So TCP/IP allows data really to go from point A to point B while solving a bunch of these problems along the way. So nowadays if you ever see mentioned on your Mac or PC of your so called IP address, that is the sort of problem that's being solved. 

Questions now on these protocols, these conventions called TCP and IP? That's the extent to which we'll need to understand them. Won't have to implement them, per se. We'll just take them hereafter for granted. Any questions that you've ever been wondering about your home network? Yeah. 

AUDIENCE: What happens when TCP-- like, when you try to send a message? Does it know if that user got the message or not? 

DAVID MALAN: A really good question. How does TCP know that a user got a message? Another aspect, another feature of TCP is that Brian's computer by design of this protocol will also acknowledge the packets that he's received. And it will do it efficiently. 

If Brian receives all four packets in a pretty narrow window of time, his computer will send to Phyllis's computer a quick message saying essentially received all four. Otherwise he'll say the opposite, which is that I'm missing for instance two out of four. And that just ensures ultimately that all of the data is indeed arrived so that you're not missing like a quadrant of the cat in question. 

All right, but that's not the only problem that needs to be solved ultimately. We also need to make the internet user friendly, if you will. And it would be really tedious if you had to visit websites, for instance, by way of their IP addresses. 1.2.3.4 is pretty memorable, but there's like 4 billion other possible addresses available. 

And it would be super tedious to remember those. It would be bad marketing to advertise those. In fact, most of you probably don't even know the phone numbers of your closest friends and family members anymore because you instead store them in your contacts or in your address book associating with numbers that are completely opaque with actual names or strings, if you will. 

The same goes for the internet too, even though every computer does have and must have a unique IP address numerically. Why? Won't routers or computers, computers just crunch numbers very readily, but we humans work better with strings of text. We need some system for converting user friendly strings like harvard.edu or yale.edu or google.com to the underlying IP addresses. 

And that's where the next acronym comes in today, which is DNS, Domain Name System. So this is just another technology that's been in use for some time now. And it's a collection of servers on the internet whose purpose in life is to convert domain names to IP addresses and maybe vice versa as well. 

So let me stipulate for today's purposes, there are some root DNS servers in the world that, long story short, know about all of the dot coms, all of the dot edus, all of the dot, dot, dot, all of the other top level domains around the world, as well as in the US. And then there are some smaller DNS servers owned by companies, owned by universities, and even in your apartments or homes most likely. Indeed, if you have a home router plugged into the wall somewhere, that's not only routing your data in and out of your apartment or home or dorm room. It's also typically serving as a local therefore faster DNS server, a cache if you will. It's sort of locally saving your most frequently accessed websites in their IP addresses just to avoid bothering the bigger, more expensive, busier servers all day long. 

So there's DNS servers all over. If you poke around your settings in Windows or Mac OS or Android or iOS, you'll see mention of DNS, and you'll probably see the IP addresses of the servers whose purpose in life is to do this conversion for you. But this is a requisite feature if we just want the internet to be user friendly and allow us to use words instead of numbers alone. 

What's inside of these DNS servers? It's essentially a spreadsheet. Or if we can say it more geekily, it's essentially like a hash table of some sort, which it has keys and values. The key is the domain name. Harvard.edu, yale.edu, google.com. And the value is the corresponding IP address, or in many cases IP addresses plural, of the corresponding servers. 

So here already even though I've drawn it fairly abstractly like you would on a chalkboard, it's really probably implemented as some kind of table. Maybe a hash table, maybe a database table, maybe SQL or something like that. Or maybe it's even just a linked list or an array. We just have to somehow enable this computer to convert one to the other. 

Now, just to be super precise, DNS servers actually convert what are called fully qualified domain names, which is generally not just harvard.edu but more verbose www.harvard.edu and www.google.com. So the whole thing that you would see as a substring of the URL. So that's what DNS does. And that's what your university, your company, your home router are doing for you. 

Let me pause here to see if there are any questions. This too is just a technology now we'll take for granted. It just works. Questions at all? No? All right. 

So let's now transition among our protocols really to the last for today, which will set the stage for actually solving problems with these and writing some code ultimately. HTTP. This is something that you see or hear all day long even though you rarely have to bother typing it anymore. 

Odds are if you go to harvard.edu, yale.edu, google.com, you don't bother typing HTTP, let alone HTTPS, manually anymore. Why? Because your browser auto completes that kind of thing just to make life easier. But it is officially at the beginning of every URL you visit, either HTTP or the more secure HTTPS, whenever you're using your browser to access some website. 

So HTTP stands for Hypertext Transfer Protocol. And it's easily one of the most popular, daresay one of the most powerful features of the internet nowadays. But the mental model to have here is that HTTP or the web more generally is kind of a service that runs on top of the internet. And maybe Zoom or Microsoft Teams is another service that runs on top of the internet. And iMessage and technologies like it is another service that runs on top of the internet. 

So the internet is really the lower level plumbing, the TCP/IP stuff, the DNS stuff, that just gets data from point A to point B. But now, and we're in a software development class ultimately here in CS50, HTTP is the application level protocol. It's sort of what programmers use, what companies use, what developers use ultimately to use the underlying plumbing to build interesting and powerful things. 

So what does this mean when it comes to accessing services via HTTP or the more secure HTTPS? Well, here is a representative URL. Even though you might not type the whole thing, if you poke around your address bar, this is what's up there. With that said, a lot of browsers nowadays are kind of simplifying if not dumbing down what you see with your human eyes just to shorten the strings, especially on mobile devices. But almost always, if you click the URL or highlight it, then you see the whole thing. But on many browsers, you might only ever see example.com. But all of this information is there. It's just getting more and more hidden just for user interfaces sake. 

Well, it turns out when you visit a URL, by default, especially if you type nothing after the dot com in this case, you're technically implicitly adding a single slash. So a single denotes the root of the server. That is the default page or folder in the server. And the slash, whether or not you type it or not, is implicitly going to be there. And that just means give me the default. Whatever is at www.example.com, give me that page or that folder. 

But URLs can be longer than this. And more generally, there can be a path, so to speak. And this is a term of art. A path is some sequence of folder and/or file names after a URL like this. And so you might see more specifically that a URL contains a very specific file. This isn't as common nowadays anymore, though we will begin today by using this technique. But if there is a file called literally file.html or something else on the server, that file is going to be what this URL pulls up on the computer. 

Meanwhile, you might have /folder/, which just means show me whatever's inside of this folder. Or you might have more verbosely /folder/file.html, which will show you that file in that folder. And meanwhile, just to give some other terms of art, this is the so called fully qualified domain name. And again, these vocab words don't matter all that much, but you'll hear or see them over time. 

We generally colloquially just refer to this as the domain name, which is a little less precise but gets the job done certainly in conversation. And this part here I described briefly earlier. What's the name for this suffix at the very end of the fully qualified domain name? The? Yeah. 

AUDIENCE: Top Level Domain. 

DAVID MALAN: Yeah. Top Level Domain or TLD. And this is just some form of categorization of the URLs. Now, the internet got its start within the United States and a lot of the first websites, of course, came from the US. And so for better or for worse, the sort of stake was planted in the ground. So generally .com indicated at least early on that it was some kind of commercial enterprise, a business that owned a domain name. .edu is an educational institution. .net was some kind of network. .gov was the US government. 

Now, there are also country code TLDs. CCTLDs like .uk or .jp. Every country in the world has its own two letter TLD that might very well be restricted to only servers or companies or people in that country. Many of them can be used by anyone. You've used a lot of URLs in this class ending in cs50.io. That doesn't mean input output. It actually is a TLD from another country that lets anyone on the internet pay for and on an annual basis using that domain. 

.tv for instance you might see in some cases, like twitch.tv and the like. That too is owned by another country that allows others in the English speaking world in this case to use it as though it connotes TV. But those are just different types of TLDs that roughly categorize where the domain lives. But it doesn't necessarily mean it's commercial anymore. It doesn't necessarily mean it's a network anymore. For the most part, there are hundreds of TLDs now, for better or for worse, most of which are less common than these big ones. But most anyone can buy most of them with just some restrictions on things like .edu and .gov that are still very much regulated. 

This, meanwhile, is what we might call the host name. www, It's obviously a super common convention. Almost every website uses www as its host name. But that's a human convention. It's not a requirement. And indeed, some websites don't even bother having a host name. They just use their domain to advertise their websites. 

This now is going to be the scheme or the protocol and this is just going to indicate via what protocol the computer, your Mac, your PC, your phone should use when accessing content at that address. Because indeed, there are other protocols you can use. But for the most part, we'll only focus on HTTP or equivalently HTTPS. All right. Any questions now on those just definitions, building blocks of URLs, just so we all sort of share a common vocabulary? Any questions at all? Yeah. 

AUDIENCE: What is the local post IP? 

DAVID MALAN: Sure. We'll come back to this actually later today. There's a technical term known as local host, which is a generic name for your computer, your Mac, your PC, your phone, especially when you're doing software development. And by convention, your own computer has not only whatever IP address you get from your university or your internet service provider. 

It also has a reflexive IP address, one that just always refers to itself, which is 127.0.0.1. And that's just a human convention. Humans decided that shall refer always to your computer. And it's actually going to be useful today and onward, because we can use that when doing development on our own computers ultimately. Other questions on URLs, IP, DNS, or any of these building blocks? 

All right. So what do we mean by HTTP being a protocol? When I extended my hand earlier as a human handshake, a typical human in healthy times would know to respond in turn. Well, how does Brian's computer to respond to Phyllis's envelope, whatever message is therein? 

Well, assuming that Brian is indeed still a web server in the story and Phyllis was trying to upload a cat or maybe download a cat from Brian's web server, inside of Phyllis's envelope would have been a message literally in text. And it's English for the most part. And it would contain at the beginning of that message literally one of these English verbs. 

Either get, which means just that. Get me the home page. Get me a picture of a cat. Get me a picture of a dog or a video or anything else. Or post, which often means post. That is put, that is upload a picture of a cat or a dog or something else to the server instead. That's not strictly the only use cases for these, but you can generally think them as one is just getting information and the other is posting from the client, from Phyllis to the server, in this case, Brian. 

So those are the two keywords that we might see. And why is this useful? Well, it turns out we can start to see in our own Mac or PC some of these very same messages. For instance, if Phyllis were visiting not Brian's but example.com, that web server, inside of her metaphorical envelope, there would be a textual message that literally starts with get slash then the word HTTP then the version she's using. 1.1 is very common. Two and three are becoming more common. But HTTP generally looks like this. 

The next line of text in her envelope would probably say host: then literally the fully qualified domain name of the server she's accessing, just in case. And this happens super commonly, especially on small websites. If one server is hosting multiple domain names, multiple websites, this just distinguishes which one she actually wants. And then there's usually a whole bunch of other lines of text as well. 

So where can you actually see this? Well, let me actually go ahead and do this. Give me just a moment, and I'm going to open up on my computer here an empty Chrome window in incognito mode. Generally speaking, incognito mode or private mode is used when you don't want there to be left remnants of what websites you visited. 

And it has the effect for software developers of just forgetting any things you might have tried already within your browser, including things called cookies. More on those another time. Your autocomplete history and the like. So for development purposes, incognito mode is especially helpful because it's sort of like starting with a clean slate every time you open a new private or incognito mode. So there's not going to be any remnants of previous testing or code that you've been playing with. 

And I'm going to go ahead and do this. I'm going to go ahead and right click or Control click on Chrome. I'm going to choose Inspect. And it's going to pull up this window, sometimes on the side sometimes on the bottom. I'm going to move it to the bottom just so we can see it a little more readily. And I'm going to zoom in. And it's going to look a little arcane at first. 

And I'm going to just highlight a few of these tabs. We'll see here along the top that there's elements, console, sources, network, and a whole bunch of other things as well. This is the advanced mode in Chrome. And Safari and Firefox and Edge have their own equivalents of these features. They've always been there, even if you've never clicked the right button to enable these features. 

And I'm going to focus for a moment on network like this. This is a feature of the browser that's going to allow me, the programmer in this case, so the engineer, to just kind of look at what messages my browser is actually sending to a server. So let me go ahead and do something like this. Let me go ahead and visit for instance in my browser here, and I'm going to shrink the window just a little bit so we can see it exactly, I'm going to visit https://www.harvard.edu. And now I'm going to hit Enter. 

And a whole bunch of stuff just happened along the bottom of my screen. And I'm going to try to pull my window up just a little bit. So we can focus on a subset of this. Let me pull this up, covering up really the content of the page, focusing on these lower level details down here. And what I want to see first is-- let me-- oh, sorry. Let me go ahead and reload this page here after retaining the log so that we can see absolutely everything on the screen. And to be clear, I just checked because I forgot earlier preserve log because I wanted to preserve everything on the screen. I want to see everything all at once. 

And we'll see this. The very first line of output is completely overwhelming with detail at first glance. But what you'll see here, if I start to scroll down and down and down and down, are the so called request headers. And let me zoom in here. And what you're seeing inside of Chrome, inside of its Network tab in its so called developer tools. Again, this is just for engineering types. 

You'll see all of the headers, all of the lines of text that magically were sent by my Mac to harvard.edu, much like from Phyllis to Brian's server in that story. So I can see exactly what messages are being sent. And a lot of this we haven't talked about yet, but we do see some mention of get and we see some mention of slash and a bunch of other arcane details. But notice they're all sort of key value pairs with the colon here indicating what the corresponding value is. 

Now, most of this is not going to be interesting, and we're not going to focus too much on the weeds of all of this. But it indeed gives us a sense of what's inside of that virtual envelope. Now, harvard.edu is one thing. But there's other websites we might visit as well. And no matter what they are, we're going to expect ultimately an HTTP response. 

So in addition to a computer, like my Mac or Phyllis's computer, sending a request containing gets and host and those details too, you'll see here in my slide form just representative response from the server. And notice that key here is that the server is responding in the same version of HTTP in this example. It's sending back this so called status code. Just a numeric code that indicates, in this case, that everything's OK. And it includes this header, this HTTP header, which again, is just a key value pair saying that the type of this content that's coming back from the server is text/html. More on HTML in just a little bit. 

But for our purposes now, this just means that harvard.edu is sending me back a web page. And indeed, if we hide all of this technical stuff, that's the web page that we saw up here with all of the usual imagery and the like. And in fact, I can see this if I scroll back up not to request headers but response headers. You'll see up here that we get back responses, including the date that the server responded and a whole bunch of other details as well. 

And honestly, this has always been under your fingertips and it will soon be useful as we start making web based applications ultimately. But this very quickly gets overwhelming quickly. And so better than this might actually be a tool that we can use within our code space itself. 

So let me go back to VS Code here. I didn't open any code tabs. I'm just going to use my terminal window for a moment. And I'm going to run a couple of commands that are going to allow me to actually see what is going on when I request one website. Let me go ahead and use a command called curl for connect URL. 

And this is like a command line black and white program that's going to pretend to be a browser. And it's going to connect to the URL, show me the headers, but it's not going to show me the images of the graphics, which might very well be useful to the humans but not to me right now as the developer. 

So I'm going to do curl. I'm going to do -i. And then I'm going to do https://www.harvard.edu/ as though I'm pretending to be a browser requesting the home page. And what's nice about curl is, albeit overwhelming too, you'll get back a whole response from the server containing only those header values, the key value pairs inside of the envelope. And we'll ignore almost all of these. 

But here is the response from the server. It responded using a new and improved version of HTTP. In this case, version two, and it gave me back a 200. There's my content type, text/html. And then this char set happens to do with the encoding, if it's Unicode or ASCII or something else. And then there's all this other overwhelming detail for now. 

But this is the beginnings of my ability to just kind of poke around and see how the server works. And it turns out too that we'll be able to see other potential responses as well. So for instance, HTTP might not only return 100. What if I do this instead? Let me go ahead and visit curl -i http://www.harvard.edu. 

So notice I deliberately used the insecure version of the URL, which maybe Harvard's system administration doesn't like anymore. Well, how can they ensure that I, the end user, the student, nonetheless use HTTPS even if I didn't type it myself? Well, let me run just that command with just HTTP, not HTTPS, and you'll see that everything is not OK. It didn't come back with a 200. It came back with 301 and this message saying Harvard moved permanently. 

But here's where you can look for another clue. Among all of these lines, most of which I don't care about, there's a location patient header colon that's a little hint to me that says where Harvard University has apparently moved to on the web. And what's different about this URL, just to be clear? It has the S included. 

And what your browser will do by default, because Google and Microsoft and Mozilla programmed it this way, whenever it sees a 301 response instead of 200, it won't show you any web page. It will look for a location header, find that URL, and then automatically quote unquote "redirect" you there too. So this is why it doesn't matter what we type in the browser. Harvard can have its servers send these semi secret messages to our browsers, and then it will just visit a second URL all automatically. 

And you can do this with hostnames as well. Suppose that Harvard does not want to standardize on harvard.edu. Why? They just want it to always be www. Maybe it's a branding thing. Maybe it's a technical thing. We can see the exact same response here. This first tells me when I visit HTTP harvard.edu with no www, Harvard minimally wants me to be using a secure connection. 

If I then, OK fine, cooperate, let me go ahead and clear my screen. Let me add the S but not the www. You can see here that it again responded with 301 up here. And the location now adds the www. So it's just a way of bouncing users from one place to another. And this is all thanks to HTTP boiling down to relatively simple messages inside of the envelope that tell the computer, the browser in this case, how to respond. 

Now, odds are you've seen others besides 301 even though you've probably never seen that actual number unless you've done this kind of thing before. But there probably is a number that everyone in this room has seen even if you never really wondered why is it that number. I think you're smiling. What number are you thinking of? 

Yeah, so 404. Why is 404? Well, 404 indicates by convention not found. And now why the world decided years ago to show us normal humans on the internet 404 is anything significant is unclear. That's sort of bad design. What do I care if the status code is 404? But it's common enough on the internet that probably all of us have seen it. 

But that just means that some server when you visit a URL that's incorrect, maybe it's outdated, the URL has been changed, if you see a 404, it just means that the virtual envelope that came from the server back to your Mac or PC or phone contains not 200 OK, not 301 moved permanently, but 404 not found instead. And it's usually accompanied by a technical message, maybe a cute picture of a cat sort of hiding because it means not found or something like that. The aesthetics are entirely up to the server. But that's what the 404 means. 

And there's other codes too, a few of which you'll use in the coming weeks as we transition from command line programs in C in Python to web based ones. We've seen a few of these already. And several of them are kind of variants of the same thing, like these 300 ones here. But we'll see others. 

Like 403 forbidden means you probably forgot to log in or you need to log in or something like that. Internal server error. Right now know in the coming weeks you will absolutely encounter 500 errors and they're always your fault. It's going to be the equivalent of a segmentation fault in C. A 500 error means you or I screwed up when writing some code. So we're going to see that. But it's just going to be an opportunity for us to fix it. 

If a server is overloaded, you often see 503, like something's unavailable because something's too popular or is, maybe worse, getting attacked. This is an old April Fool's joke. 418 is not actually used in practice, but someone took the time to write up an entire formal technical proposal so that servers can respond saying I'm a teapot. So it's kind of part of internet lore. And there's other ones of these status codes as well. 

But this is useful, because eventually we'll see in code you can use this understanding, high level as it might be, of HTTP to do some interesting and powerful things. So for instance, we can even send fancier URLs to servers. It turns out, as we'll soon see, if you send a message like this, get/search?q=cats and then HTTP 1.1 or whatever version and you send that message to Google server, www.google.com, this is how you can specify not just the path of a web page that you want, /search in this case. 

The question mark it turns out is going to be a convention in the internet, in the web specifically, for passing human user input to the server as well. In fact, you've probably never paid close attention to URLs, but they very often have question marks. They very often have equal signs. And indeed, even google.com supports a certain key, q in this case for query, and you can put anything you want after that in order to search for actual cats. 

So if I actually go back to Chrome itself here for a moment, let me pull back open my Chrome browser here, previously I was using incognito mode for harvard.edu. I've gone ahead and closed that window and opened a new one so we can start fresh by visiting Google. Normally you and I are in the habit of going to google.com and searching via the form. Or nowadays you just type your search query in the browser itself and it brings you automatically to Google or Bing or something else. But I can really be pedantic here. 

Let me go ahead and zoom in and I'll manually go to https://www.google.com/search?q= maybe cats. Now, this would not be a very user friendly experience if all of us had to manually type out something crazy like that. But that's what the form is redirecting you to when you type in more user friendly cats into a text box. 

If I hit Enter here, we'll get back indeed a whole bunch of search results about cats. If I zoom back in and maybe I change it from cats to dogs, that too is going to change. And notice it's prepopulating the text box because Google has written its code in order to do so as well. 

Now, apropos of the video with which we began today from yesteryear, one of the better Yale pranks over the years, has anyone actually ever been to safetyschool.org? And to our friends at Yale watching live, hi. Safetyschool.org. So it's kind of fun if you actually visit it depending on who you are. So if I open up a new window here. And I go to http://safetyschool.org, zooming in, Enter, my oh my. Look at where it goes. Now, how does that-- 

[APPLAUSE] 

This is not a CS50 thing. Someone out there who I don't know who they are for 20 years has been paying annually for that domain, safetyschool.org, for just this joke. But if I now go back into VS Code here in my terminal window and a little more sophisticatedly let me do curl -i http://safetyschool.org, the browser of course immediately redirected me to the website. But what's going on underneath the hood? Well, 20 some years ago, someone bought the domain, configured the server quite simply to spit this out. Safetyschool.org for years has moved permanently to www.yale.edu. 

So just a little demonstration of what you can do with just a little bit of understanding of HTTP. That's been a lot already. We've laid the foundation for understanding how the internet works. Now we're going to use it with a language called HTML, Hypertext Markup Language, CSS, Cascading Style Sheets, and JavaScript, a proper programming language. But first it feels opportune to take a 10 minute break. We have some wonderful Halloween candy in the transept, and we'll be back and 10 with those languages. 

[VIDEO PLAYBACK] 

- We're headed up to Boston, checking out the stadium for the prank. 

A few years ago, I was at a math conference and I was sitting around the table at dinner with a few other mathematicians. And one of them went to Harvard and started telling the story of this amazing prank that was against Harvard. And at that point, I felt I had to interrupt and said, well, actually I can tell you a lot more about that. OK. 

- The idea was perfected in a dorm room. 

- We came up with the idea actually to prank them with signs of the football game. We threw some ideas out there as far as what the signs would say. We eventually settled on we suck. 

- And my immediate reaction was, no, this will never work. However, the problem solver in me started thinking, well, maybe we can make this work. 

- The problem? They had to infiltrate Harvard stadium without getting caught, sneaking 1,800 placards, distribute them to unsuspecting Harvard fans, and then convince those fans to prank themselves. 

- It's great. 

We thought about basically every possible thing that could go wrong and tried to come up with a solution for it. 

- And then you put two reds on top of it. 

- They made fake Harvard IDs and fake backstories, fake placard designs, and a 28 member fake pep squad. On November 20, 2004, the fake Harvard students smuggled the placards into the game. 

- What do you think of Yale, sir? 

- They suck. 

- It's not going to say something like Yale sucks, is it? 

- It says go Harvard. 

- But then trouble. 

- What houses are you guys in? That's not a real house. 

- Ho-fo? 

- Yeah. You guys aren't from Harvard, are you? Can I see your Harvard ID, because I really think you guys are from Yale. 

- I just showed him the front of this ID and all of a sudden, he just ran away and he felt so embarrassed. 

- Having escaped one confrontation, they couldn't risk another. It was time. 

- This just looks like a total mess. We have absolutely no idea if this is going to work. 

- Look at them. They have the paper. It's gonna happen. It's actually gonna happen. I can't [BLEEP] believe this. 

- What was once a prank became a legend. 

- We [BLEEP] did it. [BLEEP] 

- And immediately we started hearing chants from the other side. You suck. 

- You suck, you suck, you suck. 

- And I think it was at that point in time that we knew we had pulled it off. 

- One more time. Come on, Harvard. 

- There it comes again. 

[CHEERING] 

- I really think it didn't matter that Harvard won because of the prank. For a lot of Yale students and alumni, we definitely won that year. 

[END PLAYBACK] 

ALL: All right. This is CS50. Happy Halloween. 

[LAUGHS] 

[APPLAUSE] 

DAVID MALAN: Thank you all. OK, thank you. Oh, here. Oh, all right. A little Halloween candy. All right. Thank you all. So glad I wore the same thing today. So in just a moment-- thank you. OK. 

So in just a moment, we'll transition to understanding all the more now what we can do with this underlying infrastructure. So again, HTTP and below it TCP/IP is all about just getting the data from point A to point B in some standardized way. 

But now let's talk about HTML. This is the language in which web pages themselves are written. Hypertext Markup Language. Now, some of you might have used this before to make personal home pages. Some of you might have dabbled even if using some website to create your own home page. But understanding this language is useful certainly for creating the aesthetics of a web page, conveying data that's of interest. 

But at the end of the day, it and the language we look at next, CSS, are not programming languages. There's going to be no functions, no loops, no programming logic. But we will end today with a teaser of a proper programming language called JavaScript via which you can manipulate all of these various other languages as well. 

So ultimately HTML has two features. And this is a language that we spend very brief amount of time on because it really boils down to just a couple of basic ideas and then vocabulary that you'll build out over time just by Googling, looking up references, looking at other pages' source code. But tags and attributes are what characterize HTML. 

Now, what do I mean by that? Here, for instance, is the HTML code via which you can make probably the simplest of all web pages, one that quite simply says in the browser window, hello title and hello body, for instance. 

Now, what does this actually mean? If you imagine opening up this code in a browser, be it on a Mac or PC or phone, you'll see typically some kind of rectangular window. And there's usually a tab that has the title of that page. And then most of the rectangular region is the web page itself. What you're looking at then is the code that's going to put hello title in the title bar, in the tab at the very top. And down at the bottom, hello body is going to be all that's in the big black and white box that composes the rest of the browser window itself. 

Now, what are the salient characteristics here that we'll now start to take for granted? Well, first, whoops, first let's go ahead and, give me just a moment here, and actually do something with this code. So I'm going to go ahead and do this. Back in VS Code here, I'm going to first create a file called, say, hello.html. And in this tab, I'm going to go ahead and really repeat exactly that same code. 

Now, I had this line first, doc type HTML. Then I had this line, HTML lang equals quote unquote en close quote. Then I had inside of that head, then I had inside of that title, then inside of that I had hello title. And I'm doing this quickly because we'll tease apart in a moment what it actually all means. And then down here below that so called head, I had just the text hello body. 

So at the moment, that I claim is the entirety of a web page. But it currently lives in my code space, so to speak, in a file called hello.html. That's fine if I want to create it. But how do I, how do you, how does anyone on the internet actually view it? Well, to serve a web page, you indeed need a web server. 

And it turns out that Codespaces comes with one of these pre-installed because we CS50 staff did so for you. And what you can do in a terminal window once you have an HTML file ready to go that you want the world to see, you can literally run in your terminal window http-server. Single command. And what that's going to do for you is start a web server. That is to say, a program whose purpose in life is just to serve web pages. 

And even though probably up until now for years you probably, if you're like me, equate "server" quote unquote with a physical device. Server is really a piece of software. It just tends to run on big fancy devices. So when we say server, we often all think of in our minds eye big, expensive devices, perhaps. But a server is just a program whose purpose in life is to respond to requests with responses. And that's the vernacular there. 

Now, once you run HTTP server, and I'm going to do a bit of magic because I set this up before class just to make sure it goes smoothly, you'll see some output like this whereby your server is now available on a very long URL. Mine here is a very long URL that will be different from yours. But what this is is a unique identifier that your Codespace has temporarily generated so that you can now access and ideally only you can access that file using your browser. 

Now, if I flip the URL or you flip the URL to public by right clicking or control clicking the right features of VS Code, you can enable anyone in the world to visit it. But we're not going to ultimately host our websites in your Codespace, because as soon as you log off for the night and the thing shuts down, the website will go down. But at the end of the semester, particularly for final projects, we'll show you ways that you can put your own website, your own code on the actual internet 24/7, 365 even with your own domain name if you want to get one so that it lives independent of your own sleep schedule and usage schedule a VS Code here. 

So I'm going to go ahead now and visit this URL in another tab of my browser. And what I'll see here is this. This is the output of that program called HTTP server. And essentially what it is doing is it's using TCP and IP in conjunction with HTTP to just run your very own web server on GitHub's own servers as well. And that's because of different ports. Again, we won't go too much into the weeds of the TCP, the IP, and all of that stuff. But recall that different port numbers can allow you to distinguish one service from another. 

Now, one of the services is, of course, your Codespace, VS Code in the cloud that we've been using for weeks. But if you want to use the same physical server that GitHub controls but actually visit your own web server that I just ran in my terminal window in another tab, that's fine. They're just going to be using different TCP ports. And you and I don't have to care what they are but just that this is a feature that TCP supports. 

So what you see here is somewhat arcane. This is not a thing that most people on the internet should ever see. I'm just doing this for development purposes. But this is the index. That is the directory, the folder contents of my Codespace, and because I deleted everything from prior weeks already, all we see right now is hello.html, which I just created. 

So if I click on hello.html within this folder listing, you'll be a little underwhelmed. And I'll zoom in just so there's something more interesting there. But now you see hello comma body. But what's interesting, perhaps, is that after this long, very cryptic and uninteresting URL, notice at the very end of it, and I'll zoom in in a moment, what do you see? /hello.html. 

Which follows the convention I claimed before break is how a browser would allow you to access a specific file on a server by doing slash and then the name of the file name. Everything before it is very cryptic. It would be better if I buy a domain name that's a little more easy to remember and set that up some other time. But for now, let's just focus on only the file names that I'm actually creating. 

All right. So the code is up and running, underwhelming though it might be with the body in the middle of the page. And let me zoom in up here too. Hello comma title is indeed in the tab, just as promised. So what's actually going on with code like this that we just created? 

Well, let's go back to the slide version of the same. And let me just highlight a few of these lines. The very first line is what's called your document type declaration. Doesn't really matter to remember that by phrasing. And this is just something you copy paste or do from memory at the top of any .html file that you create when making your own web page. It's a implicit indicator to the browser that you're using the very latest version of HTML, which is version 5. 

You don't mention the number 5. Just browsers nowadays are programmed look for this to know that you're using the very latest version of the language. Languages, just like human languages, evolve over time. We're up to version 5 of HTML, but new features get added every few years. So indeed, this lecture, this class has been evolving over time too. 

So let's now focus on the next line as well as the bottom line. And you'll notice some deliberate symmetry here. This here is what we're going to call a tag. And it's technically different from this. This is a document type declaration. It's got the weird exclamation point. That's the only anomaly. Everything else follows a pattern. 

This is a tag in HTML and it's the HTML tag. And a tag generally both starts and stops or opens and closes at some point. So this is the so called start tag or open tag. And this just means essentially to the browser, hey, browser, here comes some HTML, the language in which web pages are written. 

This here with the forward slash after the angled bracket means hey, browser, that's it for the HTML of this page. So that's what I mean by symmetry. I started a thought here, finished it down here. 

What's in between those two thoughts? Well, here browser, or rather let me clarify one thing. This thing here is that other keyword, an attribute. An attribute is something that modifies the behavior of a tag. So it's similar to an argument in C or in Python like a parameter to a function. These aren't functions, but it's the same idea. Just modifies the default behavior of something instead. 

Lang equals en. You can probably guess just means that hey, browser, assume that everything hereafter is in English. And that might be useful for Google Translate or just search engine optimization so that just the server, the browser know what human language you have actual content in. Like hello title, hello body, even though a good computer can probably infer from context often. 

All right, so that's an attribute. That's a tag. And the whole thing here, everything in between the start tag and end tag, we would also call an HTML element. That just means everything related to that open and close tag. 

All right. Now notice indented inside of, so to speak, the HTML open and close tag are another pair of tags, the head tag and the body tag or the head element collectively and the body element collectively. And same idea. Hey browser, here comes the head of my page. Hey browser, that's it for the head. Hey browser, here comes the body of my page. Hey browser, that's it for the body. 

The head is essentially the tiny little strip at the very top, including the tab itself. The body is like 95% of everything else, the big rectangular region. What's inside of your title, of your head of the web page? At the moment, just the title. So this indicates, hey browser, here comes my title. Hey browser, that's it for the title. The title of course, is literally quote unquote "hello comma title." 

Meanwhile if we bounce back out here is the second element inside of the HTML tag. This says, hey browser, here comes the body. Hey browser, that's it for the body. And hey browser, this is the contents, these are the contents of the body itself. 

Now, the indentation is a stylistic thing. I did it just to be sort of neat and tidy because it suggests what is inside of what. But it also suggests a sort of hierarchy. And in fact, we'll use terminology from the world of family trees. If this is a parent, so to speak, head and body would be the child elements of the HTML tag. 

Meanwhile title is a child of the head tag. Or equivalently, title is a grandchild of HTML. So you can use the same sort of vernacular as in the human world when it comes to familial relationships too. And that just hints at, again, this same hierarchy. So we have tags and they include HTML head, title, body. And that's it for now. 

We have attributes. We've seen one example of them, lang. But we'll see many other examples of the same idea. But these building blocks are exactly the same. Generally, you start a thought, you finish a thought, and you might do something in between. Questions on this basic structure of any web page? Any questions at all? No? 

All right. So let's now allow things to ramp up a little more interestingly and do something with these building blocks. But so that you have a mental model for everything that's going on here on after, think of this same HTML being related in spirit to week five when we talked all about data structures. If I really wanted to, I could take to heart this idea of children and parents and grandparents and really depict this thing graphically. 

And in fact, this tree here, if you will, and it's not a binary tree, it's not a binary search tree, it's just a tree. Using week five's terminology, if this special node here represents the whole document, well the root element, as I called it, is HTML. HTML has two children, head and body. The head tag has in turn a title child and in turn has some text, just as the body has some text. And so this is what your browser is doing. 

You and I, the programmers, write this stuff. The browser reads this code top to bottom, left to right whenever you visit a website. And inside of the computer's memory, Chrome, Edge Firefox, Safari, whatnot, they build this data structure in the computer's memory so as to know what it is you have told them to do. And we'll see over time at the end of today, you can write code in an actual programming language, JavaScript, to maybe dynamically add or remove things from this tree. 

And this is how things like Gmail work. When you open up your email inbox, if you're a Gmail user, if you just stay there long enough, you'll probably get more and more mail. And what happens? You don't have to reload the page or rebuild the tree, per se. It just all of a sudden it appears at the top, at the top, at the top. What's happening there is that Google wrote some code that just keeps adding more nodes to this tree every time they realize you've got a new message again and again. So that's the relationship now even with this world of HTML, with all of the programmatic ideas we looked at in the past. 

All right. So let's go ahead and do something with this that's a little more interesting than just hello itself. I'm going to go ahead and hide my terminal window because the server is now running and all I want to do now is experiment with hello and other examples as well. 

Let me go ahead and actually before I do that, let me go ahead and run code of paragraphs.html just so I can keep my code separate. And now I'll hide the terminal window again. Paragraphs.html. I'm going to do almost exactly the same. Let me go ahead and start with something familiar. And eventually I'll start copying and pasting just to save time. So doc type HTML is always there. Open the HTML tag. 

And now notice I didn't type the rest of that. Just like with C, just like with Python, we try to save you some keystrokes by closing parentheses, adding quotes. The HTML support in VS Code is pretty good too and it tries to finish your thought when it comes to tags as well. It can screw things up if it does something you don't want it to do. So sometimes you have to delete. But it's just autocomplete, as we've seen before. 

Let's go ahead and let me add lang equals en as all of my examples today will be. Let's add the head tag. Let's go and proactively add the body tag. And now let's go ahead and give this a title tag, which has a-- I'll just call this paragraphs just so I remember which example is what. 

Now notice all of this white space and all of this neat and tidy indentation the browser ultimately is not going to care about. This is just for us humans to kind of keep ourselves sane when we look at the code. It's just easier to read. But strictly speaking, I could minimally delete all of this white space and I could just move all of this tag up to the same line. Both I think are fine. I'll just kind of follow a certain convention. But this too would have the exact same meaning. But we'll see where that detail about white space could potentially get us into trouble later. 

In my paragraphs tag, let's do this. In advance I've written up some Latin-like text, a really long paragraph of Latin-like text like this. It's actually random nonsense. It's not real Latin even though a couple of the words might look familiar. And so here we have three paragraphs of text. And I've deliberately hit Enter in between them so that just like an essay in Google Docs or Microsoft Word, hopefully I'll see three separate paragraphs. 

Let me now change tabs and I'll close hello.html from before. I'm going to go back to my other tab here. I'm going to click Back to go back to that index of all of my files which I started at earlier. And you'll see now that I have two files because I obviously just created a second file called paragraphs.html. So let's click on this to see our three paragraphs of Latin-like text. And voila. I'll zoom out. 

All right. First bug, if you will. This just looks like one massive blob of text, not three blobs of text. And why might that be? Borrowing the hint I offered a moment ago. Why are we not seeing break? 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, so we need some kind of line breaks here. Because the browser turns out is only going to take us literally. And if you just give it text, text, text, it's just going to show you text. And any time there's more than a single white space, whether it's two or 20 or 200, it's going to just assume that you did that just to be neat and tidy and it's going to collapse them into just one space visually like this. 

So there are, in fact, a couple of solutions. One is this here. I could add some explicit line breaks. And it turns out that there's a VR tag like this. And just for visibility's sake, let me do two of them. So hitting Enter, Enter on my keyboard. I'll do it here too. BR for break, break. 

And now let me go back to my other tab. Nothing's changed yet, but that's because I have to reload. I've changed it on the server, but now I need to change it in the browser by reloading. And now it looks a little better, albeit nonsensical. 

But you'll notice a curiosity. Per this BR tag, this is kind of poorly designed. It's a little hackish to just say Enter, Enter and make the browser do this. Breaks, line breaks, don't actually require close tags or end tags. So not all tags need to be closed, at least those that it just makes no semantic sense to close them. Like the break is there or it's not. You can't imagine starting to move to the next line and then eventually getting around to finishing. It's either there or it's not. So some tags do not have close tags as necessary. 

But there's a more elegant way here, I daresay, not just sort of hackishly putting in these line breaks. Let me do this instead. I'll delete those. And let me go ahead and, as the name of this file suggests, let me add a paragraph tag. Now, here I need to fight with VS Code's autocomplete, because I don't want to finish the thought there. 

Let me go ahead and open the paragraph tag and close a paragraph tag. And just to keep things tidy, I'll go ahead and indent too, even though the indentation itself doesn't matter. Let me go ahead and create another tag for opening this paragraph. And I'll close this one here. And now let me see. Sometimes it's fighting with my autocomplete, but that's fine, because I did this the wrong way at first. And now let me go ahead and finish this thought by closing this paragraph tag here. And I've manually fixed all of my indentation. 

So now on line 10, I have the equivalent of hey browser, start a paragraph. And then it does the Latin-like text. Then on line 12, hey browser, that's it for this paragraph. And repeat, repeat. If I now go back to my other tab and reload again, shouldn't be all that different. But semantically, it's a little bit better. Why? Because you saying break, break doesn't really mean anything. But by saying paragraph, paragraph, paragraph, now there's some more semantic information there. 

Now if Google is analyzing your page or if the programmer is trying to understand what it is you did in the past when writing this code, you just know semantically, oh, this is a paragraph, this is a paragraph, this is a paragraph, just like in a book or an essay. So it's a little more clear focusing more on what it is, not how you want to display it. Any questions then on these paragraphs? 

All right. So a few more tags. And indeed, these first few examples will really just be sort of bang, bang, bang. Just a bunch of different vocabulary words in the form of these new tags. But we won't go through the entire laundry list of tags. This is indeed the thing for which web references and books and the like are ultimately helpful, just like a dictionary in the real world. 

So I'm going to go ahead and do this. Let me go ahead and copy this. Let me create a new file called headings.html just so we have a new file for this. To save time, I'm just going to paste that exact same code just to get me started. I'm going to change the title of it for clarity for the code online to headings. 

And now just like a book or an essay or a thesis, let me actually put some actual headings here. Now, if my first heading like chapter one, I could do something like this up here. I could have a paragraph like I just learned and I could say something like chapter one here. But that's not really a paragraph. And so it's sort of better design to tell the browser and really tell the world what it is. 

So it turns out there's another tag I can use like h1 for heading and most important heading. And in here, I'm just going to keep it simple and I'm going to say something like one. And in fact, this is so short. Here's a good candidate for just keeping this all in the same line. But this has no functional difference, but it'll just make it a little more terse on the screen. 

Now let me go ahead down here. And I could have multiple headings so H1 two. And down here I could have another one, H1 three. And if I go back to my other tab, I reload it. Now we should see, just like a book or an essay, now we have some proper-- now we have some-- oops. I have to go to the right file. Sorry. If I go back to the index, now we see the new third file called headings.html. And now we indeed see some fairly pretty, if simple, headings as well. 

Now, if these aren't three chapters, one, two, three, but maybe it's a chapter, then a section, then a subsection such that just visually you want things to get smaller and smaller, well those exist too. And in fact, you can do H1 through H6. H1, a little paradoxically, is the biggest and boldest. H6 is the smallest but still bold. 

So it might make sense to make this H2, both open and close, and maybe this H3, open and close, if again, this is a section or a subsection inside of that chapter. If I reload now, notice just gets a little smaller. So it's more similar to what you'd see on the printed page. But this now is just another three tags that I might use in my own code. 

All right, well how about lists of things? I have three paragraphs here, but let's do this. Let me go back to VS Code. I'm going to copy this code so I have a starting point. I'm going to create a new file called, say, list.html. Here I'm going to copy paste. I'm going to change my title to be list just for clarity. 

And in here I'm going to go ahead and get rid of this whole body, because let's move away from these massive paragraphs and keep it simpler for now. If I want to have a list of things, for instance, if you haven't seen these already, a computer scientist when they're fishing for just some arbitrary meaningless words, they often use foo, bar, and baz just as their go to, just like a mathematician might use x, y, z for variables. 

So foo, bar, and baz are on three separate lines. And maybe this is my to do list or my shopping list. But you can probably imagine, if I go back to my other tab, go back to the index, I now see my new file list.html. But it's probably going to look wrong. I think I'm just going to say yeah, foo, bar, baz all in one breath, if you will, not on new lines. And you can try to fight this. You can be like really want to put some line breaks. There go back and reload. It's still not going to make any change. 

How do I want to fix this? Well, I can do this in a few ways. I can make them paragraphs, but they're not really paragraphs. They're a list. So I'm going to use a different tag instead. I'm going to create, for instance, an unordered list using the UL tag. Open and close. 

Inside of that, I'm going to use the list item tag, LI, and I'm going to say foo. Inside of another tag I'm going to say bar. Inside of a third tag open and close, I'm going to say baz. So it's getting a little verbose, but it's still relatively succinct. LI is all you need type for list item. UL is all you need type for unordered list. So there's some shorthand syntax here that's adopted. 

If I now reload, you're going to see a so-called unordered, list like not sorted, which means by convention to show it as bullets. Though it could be displayed in different ways visually as well. If you actually change your mind and you realize, oh, I'd really like to number this, well, you could obviously like just add one and two and three, but that's going to get annoying, especially if the list grows. You want to change something, insert something in the middle. Then you have to reorder it. I mean, we're using computers here. They can do this for us. 

So we can change the UL to any guesses? OL, maybe, for ordered list, which is the opposite here. So let's try changing that to OL. Let me go back to my browser. And I'm just hitting Command R or Control R to reload the page instead of clicking the button every time. Now I automatically get one, two, and three. And you can even override the aesthetics using different numerals or symbology instead, but that would be perhaps the most common there as well. All right. It's a lot of tags quickly. But any questions on lists, paragraphs, headings, or the like? No? 

All right. So let me go ahead and propose this here. Let's go ahead and create what we'll call a table. So let me copy and paste this into a new file. Code of table.html. And in table.html, let me again rename the title to table. Let me get rid of that ordered list from before. And let me now use a table tag open and close. This one one's a little weird. But inside of a table, you typically have a head of the table. 

So I'll say, well, let's say the first row. We'll keep this one simple. A table row or TR. Inside of a table row, you would ideally have columns, but that's not the nomenclature. Instead you have data. So TD for Table Data. And let me go ahead and just have the first datum be one. I'm just going to arbitrarily do one, two, three just so we have something to play with. 

And you know what? Just for demonstration sake, I am going to deliberately copy paste this twice and I'm just going to manually change the numbers just so we can see what I'm creating. Seven, eight, nine. And then maybe just for good measure if you're seeing where this is going, let me copy this one more time and give myself a final row with an asterisk, a 0, and a pound sign if maybe you see where this is going. 

Let me go back to my other tab. Let me go back to the index. There is my new file, table.html. I'll click that. And while it's not very pretty, I'll zoom in. It's indeed a table of data. I happen to mimic a telephone keypad. But you can imagine this being much juicier, much more interesting scientific or financial data or the like laid out into these rows, TRs, and these columns, a.k.a. table data as well. So we have that ability as well for structured data. 

Now of course, the internet has lots of images on it. And in fact, this is all just text. How can we introduce images? Well, let me go ahead and do this. Let me first sort of semi secretly copy an image file that I brought from earlier just so we have something to play with. And I have in my account here now an image called harvard.jpeg. And I uploaded this semi secretly a second ago into my account so that I can reference a second file. 

Let me go ahead and copy this HTML just to save myself some keystrokes. Let me go ahead and do code of image.html. And let me paste that code and hide my terminal window. I'm going to get rid of all of this table as just uninteresting now. We're going to make this even simpler by changing my title to image to keep all these demonstrations separate. 

And now if I want to make a web page that when visited shows us a picture of Harvard, well, there's an image tag abbreviated IMG for short. I can specify what the source of that image is. And if my file, a JPEG in this case, is literally in the same folder, I can just say quote unquote "harvard.jpeg." If it's in a folder, I should mention the folder name and a slash or something like that. If the image is on the internet somewhere with a URL, I could also have a whole URL, https:// and then the URL of the image. But I uploaded it in advance. 

Now, this is just going to visually display on the screen. But not everyone, of course, can see images. Screen readers might need a bit of assistance. And even search engines might want to analyze the page and know what this is an image of. Now, machine learning and artificial intelligence are maybe getting better, to be fair, at figuring out just by analyzing images what they are, but they're certainly imperfect. I am a human. I know pretty well what I took a photo of, for instance. 

So maybe what I should do proactively, which would be good for accessibility, is have this alt tag for alternative text. And then literally say Harvard University so that someone who can't see or so that a server can actually with higher probability what it is they're looking at. And I could be even more detailed than just a phrase. I could describe the image as well. 

All right. Let me go back to my index in the second tab. Let me go back and zoom back out. There's my new file and there's my new JPEG that I quickly uploaded before. I can click now on image.html and, albeit a little overwhelming, that is a really big image of Harvard. 

Now, apparently it's too big to fit on the screen. So this isn't the best user experience to have to scroll up. OK, so there's the image. Horrible, horrible design, if you will, at least in terms of my code. But there's going to be ways where I can rein that in and affect the height or the width as well. But for now it's just deliberately a little overwhelming instead. 

Now we can do something a little more fun and topical today, which might be to use a video instead. So let me go ahead here and very quickly grab another file today, which I brought in advance and you might have seen briefly earlier, which is an MP4, an actual video file. And what I'm going to do here by revealing VS Code again is I'm going to code a file called video.html. Yet another demonstration here. I'm going to change my title to video just to keep these things straight. 

And instead of the image tag, you might imagine using now indeed a video tag. And this is a relatively newer tag that has increasing support among browsers. So it's good now to use. And inside of this, the syntax is a little different. You specify, and this is weirdly annoyingly inconsistent, not SRC for source. You literally say source. And then in source, you use a source attribute. 

Horrible design semantically, but this is what we're stuck with. Halloween.mp4 is the name of the video. We uploaded in advance made by some of Harvard's digital artists. And the type of this video so that the browser knows for sure is video/mp4. That's a so called content type that you just know or you look up to figure it out. 

And just so that this is as animated as possible, I'm going to tell the video tag with a few attributes to autoplay. And it turns out that attributes often have key value pairs whereby it's the key, the attribute name equals quote unquote some value, just like lang equals quote unquote en for English. But not all attributes need values. In fact, if you read the documentation for HTML's video tag, there's an autoplay attribute where you can literally just say the key and it needs no value. It's just going to mean autoplay. And if you don't want autoplay, you just omit it altogether. So you don't necessarily need a value on or off. 

I want the thing to loop just so it keeps going. I want it to be muted so that we don't hear any sound. In fact, there is no sound, but browsers nowadays for anti-spam and advertising reasons often will not play a video if it has sound because it's just kind of obnoxious if you visit a page and all of a sudden your speakers start blaring. So I know this from having read up on this that I should mute it if I want it to actually autoplay for real. 

And then I'll set the width manually for now to be like 128 pixels across just from some trial and error earlier. And that width attribute does have a value. Now, I'm being a little uptight here by alphabetizing all of my attributes. Not at all necessary. I do it just so I can skim things faster and know if something is there or not. So for me it's just a matter of style. 

Let me go back to my other tab. Go back to my index. And you'll see two new files, again, the MP4 file and video.html. I'll click on the latter. And if I did this well, here we have thanks to our friends in Harvard, our artistic friends at Harvard, very-- like an ooh would help with the drama here. But we have a very dramatic, nice Halloween type view here as well. So we have videos embedded as well. And suffice it to say there's ways to embed YouTube videos or Vimeo or other services as well using yet more tags too. 

But the web is, of course, all about hyperlink, hypertext markup language, where you click on something and you end up somewhere else. And this is how the web is so powerfully interconnected. So how do we start creating links from one website or web page to another? Either that I made or someone else. 

Well, let me go ahead and open back up my terminal window. And let's create a file called link.html just to demonstrate what you and I know as a link. I'll hide my terminal window now. Let me copy paste just to save myself some keystrokes. And let me get rid of the video tag so we can focus now on links. 

Suppose that I want you to visit Harvard virtually. Well, I could say something like visit Harvard, period. This is uninteresting because it's just going to be text. I probably want you to actually visit harvard.edu instead more specifically. And I'll lowercase it just to be consistent with what browsers do in the address bar. 

All right, let me go now back to this video tab and go back where we now see my index. I'll zoom back in and there's link.html. Unfortunately when I click this, and I'll zoom in, you literally just see the text that I wrote. And yet on every social media platform nowadays, except like Instagram, when you type a URL or what looks like a URL, even if you didn't bother with the HTTP or HTTPS, it usually automatically links it for you on Facebook, on Twitter, and other sites as well. That's just a convenience. Discord and Slack do that too. But they're just doing it to make things more user friendly. But they have to generate HTML with the proper tags and attributes. 

So to get this to actually work, it's not even good enough to say https://www.harvard.edu. Because if I go back now and reload now, you'll literally just see all of that as text. If you want the browser to treat this as a link, you need to use the anchor tag. It'd be great if it were called the link tag, but it's not. It's called the anchor tag or A for short. 

And the way you reference the URL to which you want to lead the user is via href for Hyper Reference. This is one of the earliest tags, perhaps among the most arcane now. But if I then put that whole URL in quotes and close my tag, I now have an opportunity to finish my thought in between the start tag and the end tag for this anchor. And what I put in between the start and end tag is whatever the human's going to see. 

So here I can say Harvard. I can go back to my other tab. I can reload the page and now you see the familiar blue underline. This now is an actual link. And if I click it, I'll be whisked away to the actual Harvard website. 

But there's a risk here. Can anyone imagine pretty simply after, what, 60 seconds of the anchor tag, how could someone, an adversary misuse this tag alone? How could a website run by an adversary, how could a spammer misuse this tag do you think? Yeah. 

AUDIENCE: Could you have it say, like, Visit Yale? 

DAVID MALAN: Yeah, absolutely. You could have it say one thing but lead elsewhere. So I could say Yale in here. Nothing's stopping me as the developer. Go back to the page. Reload. Now it says visit Yale. You click on Yale, and voila, you end up applying to the wrong place instead. 

Now, there's some hints of this. I could hover over this. And super small. Like this isn't very good for your anti-hacking techniques. But way down here, you can actually see the URL that it's going to go to. And most browsers indeed do this, at least on desktops and laptops. So it's a little bit of a hint. 

But what you're seeing here, even though this is kind of a silly playful example, this is exactly how phishing attacks work, P-H-I-S-H-I-N-G work, whereby an adversarially tells you to log into your PayPal account. But it doesn't go to paypal.com. It goes to some other random website that they bought and built that then tries to collect your username and password and store it in their database. So now they can log into your PayPal account as you. And it boils down to that simple primitive. 

And you can be even more manipulative too. You can even say the whole URL for Yale, like yale.edu or worse, https://www.yale.edu and reload that. And now, I mean, who among you and people in your lives are necessarily going to be so paranoid as to not just blindly click on that URL? 

This is why just being a defensive real world person nowadays digitally is just ever more so important. So these same things that can be used for good or benign use cases can also be used for ill purposes too. And it is literally that simple. Questions now on any of these tags thus far? Just a few more to offer up. Any questions on this here? No? 

Well, let me open up a couple that I brought in advance just so we don't have to type all of them here. If you, for instance, have a web page that's got quite a bit of code, let me go ahead grab from the website a couple of examples real fast here. Namely one that will call how about meta.html. And in this example here, give me just a moment to full screen it, we're going to have a file. So code meta.html. I'll open this up next. No relationship to what we now know as Meta the company. 

But rather this is going to be a page that I copied and pasted the same chunk of Latin-like text from earlier. So it's going to be a really big paragraph of text. And this is an example where if you were to open this web page, not on my own Mac or your PC but on your phone, the font might actually be really annoying and difficult to read. Why? Because your phone is going to try to squeeze all of the content onto the tiny viewport, the rectangular region of your phone instead. 

So it turns out there are ways, pretty easy ways, to make your website mobile friendly as well, otherwise known technically as responsive. And the easiest way to do this is to include this tag here, a meta tag. Again, no relationship to Facebook. This has been here much longer. And in this case here, this meta tag on line five has its own sort of approach to key value pairs. This is a good example of where it'd be nice if it looked just like everything else, but this is what we have historically. 

You can have a meta tag with an attribute called name that refers to the name of some feature of the browser. In this case, viewport is the technical term for the big rectangular region to which I keep referring. The body, really, of your page. The content for the viewport, you can say some esoteric details like this. The initial scale should be one. That is no matter who visits your site, it shouldn't start zoomed in. It shouldn't start zoomed out. It should start at just the default sizing. 

And then this here, width equals device width, is a very arcane way of saying if the user has a small screen, show the text proportional to that size. Don't just try to cram it all into a tiny little window. So it's super simple. But if for the next problem set or future projects as well you find that just things look really bad on mobile, this kind of tag is the place to start, meta. 

There aren't terribly many of these that you'll use, but they're useful for other mechanisms as well. In fact, let me go ahead and semi secretly pull up one other example as well whereby I'm going to grab another example that uses more of these tags. And in just a moment, I'll reveal it here. Give me just one second here. I'll propose that in this example of meta, we now add these properties instead. So I copy pasted this from an existing file just so as to not waste time typing all of these out. 

If you've ever shared a URL on Facebook or Twitter or Slack or Discord or any number of websites nowadays that automatically show a nice preview where you suddenly see the default image of the page, maybe a few sentences or words of text or something like that. Sometimes those applications, those websites, will just choose the first image it finds on the website or the first sentence it sees and show that. But that might not be very user friendly or search engine friendly. And so a developer might want to control what it is that Slack, Discord, Facebook, Twitter, and other such sites show by default. 

For that you can use nowadays what are called open graph tags, which is to say there's other uses of the meta tag. And you just look these things up. Even I had to look this up to remember what the key value pairs are. The meta tag can also have a property attribute that can be these very specific strings. OG title, OG description, OG image, which denotes Open Graph, which again, is this standard that's evolved in recent years. And what you can do here is tell browsers and in turn servers what you want them to show as the default title of the page, the description of the page, and even the default image just so you can exercise more control when sharing things socially nowadays as well. 

Again, it just boils down to these key value pairs. This is absolutely the kind of thing you look up as needed to cross check. But those capabilities are there. And so literally the next time you paste a link into Slack or Discord or any online site that then displays it in embedded fashion, just know that all this time a little bit of textual code like this in HTML has been there by whoever authored the site. 

All right. Let's do one final example in HTML alone before we transition to just cleaning up the aesthetics and improving the visuals of everything we've been creating. Let me go ahead here and close meta.html. Let me code up a new file called how about search.html and see if we can't draw some inspiration from our cursory understanding earlier of how URLs work to see if we can't reinvent google.com itself. 

So recall that a canonical URL might look like this here. And in particular, if you want to pass in user input to that URL, again, you can potentially have a question mark and then a key equals value pair. Or for that matter, you can even have multiple key value pairs that by convention are separated by ampersands. These things are everywhere. Later today when you pull up almost any website in your browser, look at the URL and you'll just see a lot of this. A lot of noise too and distractions. But there's going to be some equal signs most likely and/or some ampersands as well. And those are just separating key value pairs. 

Now, what can I do here? Well, if you think back to how we manually searched for cats earlier, let me quickly do this. I'll do this one manually. Doc type HTML as my very first line. HTML tag with how about my lang attribute for English up here. And then inside of this, I'll have a head tag. Inside of this, I'll have a title. I'll call this example search. And then down here I'll have my beginning of the body tag. 

And now let me introduce you to really a final tag for now, a form tag, which will create a web form, the thing with text boxes and buttons that you and I use every day on any number of websites. Inside of this form, I'm going to have an input like a text box whose name is going to be q for query, because I'm trying to reimplement Google here. The type of that I want to be a text box. 

Or if I know I'm using this for search, I can actually change this to a search box. And it's going to let me-- it's going to generally put a little x there so you can clear it quickly. That's a nice little enhancement as well. And then I'm going to give myself a Submit button by doing input-- whoops. I'm going to give myself a Submit button by doing input type equals submit. And then I'll leave that as such here. 

All right. Now I need to do a little bit more. But let's see how this looks. Let me go over to my other tab. Let me go back to my index. And if I zoom out, there is search.html. I'll click it and there's not much going on here, even if I zoom in. But I do indeed have a really big text box and a Submit button. 

But I haven't in my HTML told anyone anywhere that I want this input, whether I type cat or dog, to go to google.com. So for that, I need a couple of more attributes. And I know this from having done this before. And any online reference will say the same. You can add an action attribute. Like what do you want the action of this form to be? And you can put the URL to which you want this form to be submitted. And I know from tinkering that it should be https://www.google.com/search. I don't need to put any question marks here myself. But I do want the browser to do that for me. 

So let me go back to my other tab. Let me reload. And nothing visually has happened. But watch this. When I now type in cats but before I hit Enter, notice that I'm currently at some long crazy URL slash search.html as expected. If I now go down to the Submit button and click Submit, watch what happens to the URL and the page itself. I'm whisked away to the actual google.com. And indeed, there are those same cats. And if I zoom in here, you'll see that my URL has changed to be indeed /search?q=cats. 

So this is just how web forms work. When you submit any form on the web in this way, the browser automatically goes to that action URL, adds a question mark, puts any key value pairs that you manually typed into the text boxes, and lets the server do its thing. Now here's where Chrome is starting to simplify things. Safari does this too. If you double click on your URL, now you see the full URL. But if any parts are missing, that's just a UI thing to eliminate visual distractions nowadays. 

Meanwhile, if I go back to my own form, if I search this time for dogs and hit Enter, now again, the URL changes to be q=dogs. And it all reduces to this basic building block of using a form tag. 

Now I can be more explicit. If I know I want to use get, which is actually the default, I can literally say quote unquote "get" in all lowercase, even though the verb earlier was by design in uppercase. But here now, I'm just being ever more explicit. If I don't want the label of this button to be very generically Submit, maybe I want it to be "Google Search," quote unquote. Well, if you read the documentation for forms, you can actually change the value of the button to be quote unquote "Google Search." And if I now go back here and reload, I get a fresh form. And now I get a button that literally says Google Search. 

And if I tinker with this further, because this isn't very user friendly, there's even more attributes I can do. I can add on my search input a autocomplete equals off if I don't want to see my own history for whatever reason. I don't want people knowing I'm searching for cats and dogs on this page. I can auto focus on the text box so that it shows the cursor blinking in that box by default. And I can even do something like this. I can have a placeholder attribute that says something like query or some other documentation for the user. 

And if I now go back and reload, you'll see notice it says query and it's subtle, but my cursor is already positioned there. It gave it focus. And I can type cats now without having to click in the box manually, which is just marginally better for the user's experience. Any questions now on all of this here? Any questions? 

All right. That too was a lot. Why don't we take a casual five minute break? And when we resume, we'll take a look at CSS, add in some JavaScript, and then wrap up. So five minutes only for now. 

All right. We are back. So that's technically it for HTML. Here on out, it'll be up to online resources and references we point you to just to fill in your vocabulary for more tags and attributes. But conceptually, that's it. There's attributes, there are tags, and there are attributes, and the rest of it really is just kind of a laundry list of possible features. 

But it turns out too you'll see over time that you can even see the HTML for websites. So for instance, if I go over to harvard.edu in my browser, which I'll go ahead in just a moment here and do here, and do https://www.harvard.edu/ Enter, it again will pull up today's version of Harvard's website. And if I right click or Control click on it again and go to Inspect, you'll see those so called developer tools. 

And earlier we focused on the Network tab just so we could see the HTTP stuff going on. But what I glossed over earlier was the so called Elements tab, which actually shows you the HTML underlying any web page on the internet. And so for instance, here is the underlying HTML for Harvard's homepage as of right now. And aesthetically, some of it's been collapsed. So if I click on these various triangles, I'll see what's actually inside of. That is the children of some of these HTML tags. 

But here on out if you're ever curious as to how a web page made some feature visually, you can just literally use these developer tools built into your own browser just to see what the web developer actually did. And you can do things too like this. 

Like if you really like maybe, let's see, if you really like this menu in the top right hand corner of Harvard's website, you can even right click that or Control click that specifically, choose Inspect, and what browsers will do is jump to the HTML corresponding to that visual element on the page. And here you can see that we've not talked about this tag before. There's a button tag, there's an ID attribute, and there's some other attributes as well that define that button. 

You can do other things too in the web page. Let me scroll down, for instance, here. And actually, let's go to another one, like yale.edu here in today's theme. And suppose we want to do something like change the aesthetics of this website. Well, how about this? Over here, Life At Yale. Let's right click on this. Choose Inspect. That's going to jump to that part of the page. 

And notice what you can do here in this Elements tab. We can be a little playful in return today. Life At Harvard. And voila, we've now changed Yale's website, it would seem. So have we really? Hopefully hacking is not actually this easy. What did we actually do based on today's mental model? I have changed the page, but. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: Yeah, I've just changed how it is for me. Because my browser, just like with Phyllis and Brian from the get go, requested Yale's web page. I got back a virtual envelope containing that HTML, as we've now called it. My browser has a local copy. It's got its own tree, otherwise known as a DOM, Document Object Model, built up in its memory. And yeah, I went to town and changed my copy of it. But of course, hopefully, I've not changed the actual server. And in fact, if I reload Yale's website now, hopefully it will revert back to, indeed, what it should be instead. Life At Yale. 

But this ability in your own browser, be it Chrome or Firefox or Edge or Safari, to have these built in developer tools are very powerful, because it's going to enable you to not only diagnose problems that will invariably arise in the coming weeks with your own code, but it's also going to allow you to learn from other sites how you can do things and tinker as well. 

But up until now, we've focused only on tags and attributes and on the structure of a web page. Let's now focus more on the aesthetics and fine tuning that. It turns out that HTML has very limited support for anything aesthetic like font sizes and colors and so forth. And in recent years, people have used necessarily a second language called CSS. Not a programming language. Again, a markup language, if you will, to just fine tune the aesthetics of a page. Font sizes, colors, margins, and all of that. 

So CSS is going to allow us to define a whole bunch of properties, which is just another group of people's terminology for key value pairs. Indeed, ever since week five, key value pairs are everywhere in the world, not just at Sweetgreen and restaurants, but indeed under inline code and languages and technologies like these. So properties is the new word in CSS for what a moment ago we called attributes in HTML. But it's the same idea, just different vocabulary that you get used to over time. 

A few phrases I might use now and you'll hear in the coming days would be these. Type selector, class selector, ID selector, attribute selector, which just refer to different techniques we're about to see that are going to allow you to control more precisely the aesthetics of specific things on the page. 

And the way we're going to do this is we're going to take our basic HTML, like we saw earlier, and we're going to introduce in the next few minutes just a couple of more tags and/or attributes. One, we're going to introduce you to a tag called style, which nicely named allows you to control the style, the aesthetics, the visuals of the web page. 

Or we're going to introduce you to a link tag, which very confusingly does not give you a link that you can click on. It just links to another file that then gets automatically included or imported, to borrow our language from C or in Python. But same idea. This will allow us to include secondary files. 

And we're going to ultimately show you how you can leverage third party frameworks, libraries that other people wrote, so as to not get stuck in the weeds of all the fine tuning of aesthetics and just make pretty things fast so you can focus really on the intellectually interesting part, if that's your choice, of building the content, the site out, the application out yourself. 

All right, so with that said, let me go back to VS Code here. And let me go ahead and create a simple example called home.html. A very simple home page for John Harvard, for instance. Let me give myself three paragraphs initially, the first of which is just going to have the person's name. The second paragraph is going to say something like welcome to my home page to greet visitors. And the third is going to be a little footer like copyright how about John Harvard 1636 or something like that. 

All right, let me go back to my other tab as before. Reload my index. There's my new file. Home.html and I'll click that. And you'll see, OK, I mean, this is sort of 1636 style web page. Super simple, all text, nothing really interesting going on there. 

But we can start to style it a little differently. If the title of the page is John Harvard and then it's welcome to my home page and then this less important footer, why don't we have the text be large, then medium, then small? So something arbitrary but a little more nuanced. 

So let me go back to VS Code here. And in my home.html file, let me introduce not yet the style tag but what I'm going to call temporarily the style attribute. Both indeed exist. This one's simpler and it's going to be correct, but we'll see in a moment not as well designed, arguably, as is often our narrative. 

So inside of the style tag, you can put this language called CSS. Key value pairs, otherwise known as properties. The only way you know what properties exist, what keys exist, is by taking a class, reading a book, looking at an online reference. And we're going to give you just a sampling of what's out there. 

So suppose I want to control the font size of this first paragraph. I can literally say font-size in all lowercase, colon, and then a word like large. Or I can specify 12 point or 18 point or something more precise like from Google Docs or Microsoft Word. 

And suppose I want to make this text down here medium. Well, I'll do quote unquote font size colon medium. And down here or I'll do style equals font-size small. So I'm going to start with just these three key value pairs. Same key but different values. 

I'll go back to my page and in a moment I'll reload, and it's going to be somewhat subtle. But watch how the font size do change when I reload now. All right. So I've got a little bigger. Middle one is about the same, and the last one is a little smaller. 

What if I want to center it? Just like many web pages have the text like this centered. Well, I can separate these key value pairs with semicolons. And I'm sorry, semicolons are kind of sort of back with CSS. But I can do text-align:center. Strictly speaking, I don't need the last semicolon if there's no more key value pairs, but I'll just do it to be consistent. Text-align:center. And then down here after another semicolon, text-align:center. 

All right, let's go back, reload. Now it's going to be much more obvious the change. And we now have the beginnings of a homepage. Still pretty basic, but at least it's a little more interesting. 

Turns out we can do a little better with the copyright symbol. Like most computers actually have support for a circle with a C in it. But you can't just do that with text like this. There's different ways to do this. You could copy paste it from a website that already has it so you don't have to figure out the magical keystroke on your Mac or PC. But there's also in HTML what are called entities. 

And you can actually specify using hexadecimal or decimal codes numbers like this, hash 169 semicolon after an ampersand. And this is a special symbol that you can look up in any online reference for special characters that are hard or impossible to type manually at your keyboard. 

And this, let me zoom in just so it's obvious, if I reload now instead of being two parentheses and a C character, now it's a proper copyright symbol. So you'll see these out there. They're not necessarily that frequently used nowadays, but it's good to know that they exist. 

But let me go back now to my code and propose that while correct, this is arguably not very well designed. And even if you've never seen HTML, never seen CSS before, what instinct might you have for why this is poorly designed? Yeah. 

AUDIENCE: [INAUDIBLE] 

DAVID MALAN: There's repetition. In general in the past several weeks, C, Python, SQL, repetition generally bad and sloppy and it's not going to scale well. So the repetition I think you're probably alluding to is text align center, text align center, text align center. Well, we can factor that out in CSS. The C in CSS means Cascading. And this means that if you move some properties to a parent or a grandparent, the children or grandchildren will inherit those properties. That is, they will cascade down the family tree, so to speak. 

And so let me go ahead and remove all of these, since I claim they're indeed redundant. And let me preserve just one of them by, well, let me do this. It's not quite right to put a paragraph inside of a paragraph. That's just not a thing in English writing or in writing more generally. So I'm going to do one thing first. It turns out that these two are arguably not paragraphs. This is like a header, the body, the essence of the page, and then the footer. 

So if a paragraph isn't quite the right English semantics, you can actually use more generically a tag that's all over the internet called div for division of the page. And this is just a very generic term for a big rectangular region that divides the page again and again, just so that you can think about different regions. 

Now that I have div, which really has no more meaning than that. It's a division of the page. Interpret as you will. Now I can have multiple ones of these. And let me go ahead and open a div tag here. Let me close a new div tag here. And then just to keep everything tidy, I'm going to highlight everything in between and hit Tab. And that just automatically indents everything for me. 

Now I have three divs inside of another div, and that's totally fine. This is very commonly done. Now I'm going to do this. Style equals quote unquote text align colon center semicolon or not. And now I have some cascading capabilities. Now the parent of those three children, John harvard, welcome to my home page, and the copyright will now all inherit that property. 

So when I hit reload, nothing aesthetically has changed. Whoops, sorry. I should have done reload slightly earlier. When you use a div instead of a paragraph, it actually gets rid of the space between those paragraphs. It just sandwiches them a little closer together. I can fix this in another way. But that aside, everything is still centered and the text is still large, medium, and small. But I should have called out that change in the paragraph spacing. But we could bring that back before long if we wanted. 

Now, what more could I do to maybe improve this? Well, strictly speaking, I don't really need that parent div because these three divs inside already had a parent. So let me actually get rid of that new div just to undo what I did. I'll highlight this. And if you haven't seen this trick, Shift Tab will unindent nicely, which is perhaps helpful. I could just put that text align center on the body tag. So text align colon center quote unquote. This too would work as well so long as you go up the family tree, so to speak, reload, and now indeed there's nothing aesthetically that has changed this time. 

But it turns out nowadays the web is getting a little more sophisticated. And even though you will see so many examples online, in tutorials, in books using div, div, div all over the place, there are newer semantic tags. Semantic just means they have more meaning than this generic notion of a division. And if you look up a documentation for HTML, you'll see that if you want to have a header on a page, not a heading like H1, H2 but a header, there's literally nowadays a header tag. 

And this is marginally better because it now says what it is. Search engines like Google and Bing can detect, oh, that's the header of the page. Maybe we should use this and give it more prominence in the search results. You can then have a main part of the page. So literally a tag called main nowadays. You can literally have a footer of the page. And again, these are often useful for screen readers to help recite things verbally for folks who might otherwise not be able to read them. 

And probably the screen readers might highlight the header and the main part but maybe might not spend time for the user on the footer, which is arguably a little less important semantically usually. Or search engines, again, now know what's the header, what's the footer, what's the main part of the page. So they know what to search and analyze. So this would arguably be a better design nowadays as well. 

But what else remains as a problem? Well, this is now getting a little bit more subtle and takes some experience. But this practice of putting HTML and CSS all in the same file, it's a little sloppy. Why? Because it means I'm comingling my data with the presentation thereof. The juicy stuff I care about, like John Harvard and the phrase welcome to my home page, and all of the aesthetics that I might want to change over time. 

And honestly, because everything is currently in one big file, it's going to make it really hard for me to collaborate with a classmate or a colleague at work. So that maybe I do the HTML, they do the CSS. Uh-uh, not if you're all working in the same file. It would be a nightmare. Even if you use a VS Code sharing feature like Google Docs and both are typing at the same time, you're going to mess up somehow. It'd be nice if we could separate these two languages. 

Well, one way to do that would be as follows. Let me get rid of all of the style tags. Sorry, style attributes that I've added up until now on all four now of these tags. And let me introduce the style tag that we saw on the slide earlier instead. I'm going to go up here into the head of the page, which is where technically these style tags must go so that they're already loaded into memory before the body is even analyzed by the browser. 

And inside of the style tag, I'm actually going to select the HTML elements that I want to stylize, if you will. So if I want to change the body's aesthetics, I'm going to literally type the name of that tag body. And then, I'm sorry, curly braces are back also from C. Inside of these curly braces, I'm going to put text align center. So the key value pairs are the same. The only new thing I've done is I've moved some of the syntax up to this new style tag in the head. 

If I want to now control the header tag as well, I can use the same curly braces. This is convention to put the open curly brace on the same line, the closed curly brace on another. The browser doesn't really care, but this is a common CSS style convention. I'm going to do font size large semicolon. Then for the main tag, I'm going to do font size medium. And then for the footer tag, I'm going to do font size small. 

So same exact thing. And it's admittedly a little bit more verbose. It's taking up more lines of code. It doesn't all quite fit on the screen. But if you scroll back down now, and you'll acquire an eye for this, this is just better. It's just more compact. It's more readable. The content, the data jumps out, and there's no visual distractions like the CSS properties as before. 

Upside here too is that we don't actually need to-- this doesn't actually change the aesthetics. If I reload the same page, it still looks the same. But I've taken a step toward some slightly better design. 

But let me propose that there's other ways to do this too. We just selected things by way of their type. So that was a so called type selector when I literally just specified the type of tag. Body, header, main, footer. But there's other ways that now we can lay the foundation for making reusable CSS that you and colleagues and classmates can use and reuse in multiple files and even in multiple projects. 

So let me actually go ahead and do this. Instead of just very explicitly saying I want the body to be centered, let me invent an adjective, if you will, and let me change this to .centered. And this new vocabulary word, centered, will literally mean text align center. 

Let me go ahead here and I'm just going to create a new adjective called large, a new adjective called medium, and a new adjective called small. They are deliberately consistent with what the properties do. But these are now my own vocabulary words. And they are called classes. So a class is just a collection of key value pairs, a collection of properties that you get to invent for yourself. 

And what it lets you do now is this. Now if I want the whole body to be centered, I can add this tag, which we actually saw briefly in Yale's HTML, class=center. Down here in the header if I want this to be large, I can say class="large". Down here on main, I can say class="medium". And down here I can have class="small". 

Now, I have taken one step backward by re-adding some of the aesthetics to the page. But it's not the actual properties. It's not the key value pairs. It's now more semantically nice, because now I just know from reading the HTML what these things are going to look like, whereas the implementation details for all four of those adjectives is now relegated up above. And these are literally my words. I could change it to .foo and use class="foo" but obviously that would not be the best choice of words in this case. 

All right. Any questions on this? This now is what we would call a class selector by using literally the dot, even though the dot does not appear elsewhere, but dot means this is a class. These are not always the best syntactic design decisions that the world makes. 

All right. Well, one last trick then. Notice that this is a little annoying that I'm still working in the same file. And if my classmate wants to clean up my aesthetics, make my homepage look way better, if my colleague wants to do the same, wouldn't it be nice if we could actually move all of this code to a different file like a Python library or a C header file? Well, you can. 

Let me go ahead and delete that whole style tag. Let me add a confusingly named link tag, the href of which let's call a new file styles.css. And let's say that the relationship of that file is that of stylesheet. So this is a term of art in the world of web development. A stylesheet is a text file that contains lots of styles, lots of CSS properties. 

Let me open my terminal real fast. And let me do code of styles.css. Enter. And in this file, I'm going to paste all of those same lines as earlier. But now they're in a separate file. And indeed, if I hide my terminal window and I give this file to a colleague, they can now work on the aesthetics of the page and make things a lot prettier than this, maybe use specific font sizes, maybe add colors and the like. 

Whereas I can focus entirely on the HTML, because this file now will reference that other. And if I go back to my other tab and reload, the content's going to be exactly the same, but now I'm using some separate file instead. Any questions now about these techniques here? No? 

All right, so with that said, let me show just one example now of what I called a moment ago frameworks. And this is where web development gets kind of fun, at least if you like this, especially if you like the sort of logical design, the presentation of information you care about, but you really don't want to struggle with font sizes and colors and getting everything pixel perfect, so to speak. 

Let me propose that I open up here an example in just a moment in VS Code that I prepared in advance. And this one is going to be an opportunity to consider how you might take some of the data from last week, wherein we collected everyone's favorites, and lay it out in a really big HTML table. So I wrote this out in advance because it was a huge amount of data, but it's the same data from the Google Form from last week. 

And you'll see already the hints of a table tag and these TRs. And I added a few other tags for aesthetics. It turns out when you have a more visually interesting header for your table, there's another tag called thead. There's another tag called tbody. These are not all that intellectually interesting. I just read the documentation and realized, oh, to make things prettier I need a thead, a tbody, and so forth. 

But what's interesting here is that if I go to my index here and open this file called favorites.html, here's all of the data from last week's Google spreadsheet, which we exported as CSV and I manually before class converted to just HTML. It's indeed a table, but it's really not pretty. The columns are really close together. It's kind of hard to distinguish one row from another. But this is just raw HTML written by me. 

Now, I could use CSS and some of the tricks we just saw to maybe change font size. There's ways to change color, background color, and a lot of things like that. But honestly, surely other people in the world have presented tabular data in pretty ways. I've been to many websites that have prettier tables than mine. Can I maybe use someone else's framework, someone else's CSS included in my page but don't stand on their shoulders and just make my stuff look prettier? 

Well, I dare say I can. Let me go ahead here and semi secretly open up VS Code again. And let me grab a slightly different version of favorites.html that I also opened in advance wherein I add this line of code instead. Give me just a moment to foreground this version. And the data is all the same as before, but I've added one of these link tags. And I'm not linking to my own styles.css. 

I'm using a popular library called bootstrap. And bootstrap is just one of many popular libraries out there, free at that, that has a whole bunch of CSS files and soon JavaScript files that you can just use for free in your own projects, personally or professionally, that just make things look and behave better without you having to reinvent wheels. 

Now, to access their CSS, I had to read their documentation and grab this very long URL here. But it's the same idea. Link href equals quote unquote something. And I read their documentation and they told me to add this. They told me that if I want my tables to be prettier, I have to add a class attribute to my own table tag and specify, a little weirdly but this is what bootstrap told me to do, a class called table. And that will make it a prettier bootstrap table. 

And if I want to stripe it, like every other row is gray instead of white just to make it pop a little more visually, I can also add a second class separated by a space called table striped. That's all I did. I added line five and I changed line nine and that is it. The rest of the hundreds of lines in favorites.html are the same. 

But if I go back here now and reload the browser, now thanks to bootstrap, voila. It's much prettier. Now I can zoom out and that changes the font size just locally for me. And even if you don't love their aesthetics, I mean, this is easily better than my own there. And it turns out we can do even better by adding interactivity to this too. But to do that, we're going to need one final language for today. And this one is an actual programming language. 

And we won't use it all that much in CS50, but we introduce it here as we begin web stuff because there's just so many free libraries and professional libraries that you can use just to make your web applications fancier and more interactive. Mobile applications as well increasingly use HTML, CSS, and JavaScript to power our iPhones and Android devices as well. 

So a quick tour of some syntax and then we'll conclude with just some hopefully inspiring examples to give you a taste of what JavaScript can do. So JavaScript supports conditionals, just like C and Python before it. If we rewind to our Scratch days, here of course is a conditional. Here is the corresponding JavaScript code as of today. It's pretty much identical to C with this syntax here. If we had an if else, in Scratch it looked like this. In JavaScript, it's going to look like this instead. 

So it's a bit of a regression vis a vis Python. The parentheses are back. The curly braces are back. The semicolons I mentioned in CSS are also back in JavaScript potentially. But it's familiar is the point here. And it's a different language that's frequently used for the web, whereas you can't use Python in the way we're about to use JavaScript. It just wasn't designed for that purpose. 

Meanwhile, if you have an if else if else in Scratch, well in JavaScript just like in C, it's going to look like this instead. Variables in JavaScript, of course, are a thing too. And in Scratch, we might have initialized a counter variable to 0. In JavaScript a few different ways to do this. And just for now, the keyword is let's. It's sort of a polite way of asking for a variable. Let counter equals 0 semicolon. So you don't mention the type, but you do use a keyword here in this case called let. 

If you want to increment counter by one, few different ways in JavaScript you can do this. Just like in C, in JavaScript you can do this. Just like in C and in Python, in JavaScript you can also get this. So plus plus is back. So maybe that counterbalances the other syntax as well. That was not the case in Python. 

Loops are back, of course, in JavaScript. Whereas in Scratch you could repeat three times like this, in JavaScript it's pretty much just like C. The only difference here is that you say let instead of int for an example like this. Meanwhile, if you want to do something forever in Scratch, in JavaScript just like in C, you say while true in this case. 

So this is to say we're sort of comfortable spending relatively little time on JavaScript, at least for today's purposes, because syntactically it's really the same as we've seen before with maybe a slight variance here or there. But what's interesting today arguably is just what kinds of things you can do with it. 

So with that said, what kinds of things can we do? It all comes back to this picture. If this is a simple web page on the left and this is the corresponding tree or DOM, Document Object Model on the right, that is the tree the browser automatically creates in memory or RAM for you, JavaScript is now a proper programming language that lets us dynamically manipulate, like read data from this, change this. 

And this is how Google, for instance, implements your inbox. They might have in your inbox it's like a table. So TR, TR, TR, TR, probably something like that. Or heck, maybe div, div, div. Using JavaScript, any time they realize someone sent you new mail, they can create a new node, a new rectangle in memory and you, the human, see a new div or a new TR again and again and again. So with JavaScript, you just have the ability to control the user's experience instead of, like I've been doing, constantly hitting reload in the page to see some new content, to see some new content. JavaScript can be running 24/7 so that you can actually see all of these changes live. 

All right. So let's go about writing some JavaScript code now. Instead of writing it on the server and executing it on the server, we're going to actually use a very common paradigm whereas JavaScript is actually executed in the browser client side. That is to say we can actually start writing some JavaScript code inside of our own .html file so that when a user visits that web page with their browser, not only is the HTML and any CSS downloaded to the user's browser, so is that JavaScript code so that it's executed indeed client side on the browser rather than server side, as has been the case with Python in previous weeks. 

Well, where do we go about writing some JavaScript code? Let's go ahead and revisit hello.html, which previously was a completely static example that literally just said hello title, hello body. Indeed, if I open this up using HTTP server and view it now in a separate tab, all it said was exactly that. Hello title in the tab and hello body in the main part of the viewport, so to speak. 

Well, let's make this example a little more dynamic so it doesn't just say hello body but maybe says hello to an actual person. So let's go ahead and do this. Let's go ahead and remove the hardcoded hello body. And let's actually go ahead here and use a form tag. But we're not going to use this form in the usual way whereby the data gets sent all the way back to the server. We're going to leverage control over this form client side instead. 

So I'm going to go ahead and create this open form tag, close form tag. Inside of that, let me give myself a text input that's going to have autocomplete="off" just to ensure that what I previously type in my examples doesn't reappear accidentally. We're going to auto focus it so that the cursor is blinking right there in that text box. And this time I'm going to go ahead and give it how about a placeholder of quote unquote name to make clear that I'm prompting the user for their name. And then the type of this text box will be the default or more explicitly here text. 

And then I'm going to have, as we've seen before, a button, the type of which is submit. Also our typically default. And then inside of this button is going to be the label. How about something like how about we'll call this greet. So that's what the button will actually say. 

Well, let me actually go back into my browser tab. Let me reload this page. And we should now see a relatively simple form whereby I have the cursor blinking on a text input prompting the user for their name and then a greet button that I can click. But if I click this button now, it's not going to do anything useful because I haven't written any code to tell the browser what to do when I click that button. But it turns out there's all sorts of events in the world of JavaScript that you can listen for, so to speak. 

In fact, here's just a list of some of them. Any time something changes in a form field, any time the user clicks or drags on something, any time the user presses a key and maybe lifts their finger up, anytime the mouse goes down or over or up on top of something, or any time a form is submitted, those are events in the same way that we talked about events back in week 0 in Scratch. And in JavaScript, just like in Scratch where you can do something when green flag clicked, in JavaScript you can write code that actually listens for any of these events or more. 

So with that said, let's go back to VS Code here and let's make a couple of changes instead. Let's go ahead and add to this form a new attribute. That's not the best way to do it, but it's perhaps the simplest for version one here. And let's say on submit, do the following. So on submit is an HTML attribute. And curiously, its value inside of the quotes there can actually be some JavaScript code. And let's go ahead now and let's assume there exists a function in the world called greet. And what I want to do is call that function right then and there. 

Well, now in JavaScript, how do I go about making that function exist? It doesn't come out of the box just like print might or say might in Python or scratch respectively. But I can do this. Let me go up into the head of this page. Inside of a script tag here, both open and close, let me actually write some JavaScript code. And just so it stands out, I'm going to give myself a couple of blank lines, though not strictly necessary. 

And let me define a new function in JavaScript called greet. And this is the syntax in JavaScript for creating your own function. Similar in Python instead of saying def, in JavaScript you just say function, then the name of the function, and any arguments within the parentheses thereafter. But I'm not going to pass in any here. 

Then inside of curly braces, what I'm going to do is use a built in JavaScript function that comes with any browser called alert. It's not the best or prettiest user interface, but for now it's going to get the job done. What do I want to say to the user? Well, let's first just say something simple like hello comma world close quote semicolon, thereby alerting the user with precisely that message. 

Now what I'm going to do down here is make one other change. I don't want this form to actually get submitted to the server. Just like we've seen in the past when you submit a form, it often goes to something like google.com/search. I actually want my JavaScript code to take control over the entire user experience of this form so that I'm just using the form as a user input mechanism, not to actually send via get or post this data to some other server, including my own. 

So this is going to look a little ugly. But after calling greet, I'm actually going to do this, which I've read the documentation about and I know that if you actually hard code return false here, that just tells the browser, please don't actually submit the form. Only call the greet function. 

All right. Well, let me go back to my browser here. Let me reload this, because I need to download the latest version of the JavaScript code. And I'm just going to go ahead without even typing my name, I'm going to click on the Greet button. And you'll see that, albeit a little cryptically at the top, we see an alert that says hello world. There's my ugly URL of my code space there at the moment, but we do indeed see that string. 

But what I haven't, of course, done is taken any actual name from the user. So how can we go about doing that? Well, ideally I want to alert the user with hello comma David or hello comma Carter, whatever name I type into that box. So how can I go about doing that? 

Well, let me create a variable called name. And let me set it equal to this function call. Document.queryselector. That comes with JavaScript itself. Let me then in parentheses pass in an argument that is going to be, huh, the ID. I need a unique identifier for the thing I want to select. So let me actually go back to my HTML code here. 

And instead of giving this form field a name like q for query, let me actually use another HTML attribute called ID where now I can call this anything I want. And for clarity, I'm just going to call this input element uniquely name. Now up here in query selector, just like in CSS where you can use hashes and dots and other symbology in order to select certain nodes in your DOM, that is rectangles in that memory tree, well, I can go ahead and select hash name, which, again, is just the syntax for uniquely selecting the element whose ID is in this case name. So you have the hash up here. You don't need the hash as the value of the attribute down here on line 20. 

And now if I want to actually get the value of that text box, I literally just say .value. So document refers to the whole web page itself. Query selector is a function that's built into that object, so to speak. And the value accessible via .value just like a C struct or even a Python class allows me to go inside of that text field and get whatever the value the user has typed in. 

Now, as I've been able to do in languages like Python fairly readily, I can concatenate this name onto the string hello comma space so as to form a complete phrase. And you'll notice here that I'm actually using single quotes in my JavaScript, double quotes in my HTML. This is perhaps a common convention. In JavaScript, the language does not care if you use double quotes or single quotes, but I dare say single quotes are just more common. And so that's what I've done here. 

All right. Now as always, I'm going to cross my fingers. Go back to this page. I'm going to reload, because I've changed the JavaScript and I need my browser to download it. And now I'm going to type in my name for instance, D-A-V-I-D. Click Greet with fingers crossed. And voila, now I see hello comma David. 

All right, so it turns out that while functional, this isn't the best design. And comingling your HTML with your JavaScript code as with this on submit attribute isn't particularly clean. It's better, as with CSS, to keep your HTML over here, your CSS over here, and your JavaScript now over here, so to speak. And better still perhaps even in some separate files. 

So how can I go about changing this a little bit? Well, let me go ahead and actually let's go ahead and delete all of this code for just a moment. And let me go and get rid of this on submit handler down here and really just distill my HTML only into the HTML and the attributes therefore. And what I'm instead going to do now is do this. I can use JavaScript to achieve the listening for that submit event or that on submit event. I don't need to actually use HTML for that. I can use JavaScript entirely. 

So it turns out I can access some other member of this document by doing document.queryselector again. But this time, let's select the actual form tag. And it doesn't have an ID because it has no ID in its HTML. But it does have a tag name. So just like in CSS when you can target elements by way of their name, I'm just going to select the one and only form on this page by using that same query selector function. 

And now I'm going to use another function that just comes with JavaScript in the context of browsers whereby once you select an element like that form, I can call add event listener, which is similar in spirit to Scratch's when green flag clicked or any block like that. You can then tell the browser what event you want to listen for. I want to listen for the submit event. So you don't say on submit here. Now that we're in pure JavaScript, you just say submit. 

And now I can do something like this. I can go ahead and say call the following function. And I'm not even going to bother giving this function a name. And that is allowed to in JavaScript, as we saw briefly in Python. And what I'm going to do now inside of curly braces after that keyword function is the same kind of code as before. I'm going to do let name equals document.queryselector. I'm going to select that same name ID as before and get its value. And then I'm going to do alert and then pass in hello comma, a single quote again after that. Concatenate with that the name and then semicolon. 

But I need to do one other thing. It turns out that this function, and if you read the documentation for this technique, actually takes automatically a special argument called by convention event. And this is just a variable, if you will, that refers to whatever event just happened. In this case, it's of course, going to be submit. But in other contexts, it might be a click event, a mouse down event, or something else entirely. 

So this allows me now to do this, which is a little cryptic, but you get used to these conventions. I can use that event, whatever it is, and then prevent whatever the default behavior is by calling a special function called prevent Default with a capital D. This is the alternative to that messier return false semicolon that I had inside of my HTML before. 

So all I've done here now is I've left all of my HTML as pure HTML down here and I've put all of my JavaScript code as pure JavaScript up here. This sort of separation of concern similar to what we started doing with CSS just a bit ago in order to keep those two languages separate too. 

Well, let me go back to my browser here. Reload the page. And unfortunately, there's a subtle mistake I've made here. Let me go ahead and type in D-A-V-I-D and click Greet. And unfortunately, nothing actually seems to happen. Well, maybe it's just my name. Carter. Greet. And nothing seems to happen. That alert does not come up. Well, why is that? 

Well, let me go back to VS Code here and point out that order of operations in JavaScript matters similar in spirit to C. Because on line seven I'm selecting the form and trying to add an event listener for submitting that form, unfortunately the form had better exist at that moment in time, but it doesn't. Because just like in C and in some cases Python where the compiler or the interpreter reads the code top to bottom, notice that the form doesn't actually exist and therefore get loaded into the computer's memory until line 19. So we've got to kind of reorder these somehow. 

Now, maybe the simplest way to do this would just be to perhaps do something like this. Let me scroll back up to my script tag and perhaps a little more explicitly move it into the order in which I want it to be executed. So I'm going to go below my form and inside of my body, which is actually OK for JavaScript here, and just use that same code. 

And assuming I didn't make any typos, let's go back to the browser. Click reload again to get the latest. Type in my name again using that purely JavaScript solution. And the only change I made was I moved the code from up here to down here. Clicking Greet now. And wow, it's now back. We get the alert with hello comma David. So those kinds of things, those kinds of principles matter at least when we're back in this world. But there's other solutions too. 

And just so that you've seen it, because it's a common convention in libraries as well, let me undo that change and put that script tag back in the head or really anywhere else in the page where it might be. And let me propose that there's one other way to solve this problem to postpone that code on lines 7 through 11 getting executed until really the whole DOM, the tree, is ready to go. 

And the syntax for this might be as follows. I can do document and I can add to the document an event listener that's going to listen for something a little special. And I always have to look this up myself to remember the spelling and the capitalization. But it turns out that the browser itself, once it's done loading all of your HTML top to bottom, left to right, it will raise an event called DOM content loaded, capitalized exactly as such. 

And if you want to call some function, and I don't even need an event argument in this case, you can open curly braces just as before and put inside of those curly braces the code that you want to execute only once the DOM's content has been loaded top to bottom. And now let me just finish my thought with a closed curly brace, close parentheses, and semicolon. It gets a little annoying to visually line all of this up, but I think I'm still good. And now even though this code is at the top of my file or really above the form tag itself, I think we're OK. 

So let's go back to the browser here. Reload the page. Type in D-A-V-I-D and click Greet and we still get the same correct behavior. And so this is just a very common paradigm to use these kinds of events to listen and listen and listen for something to happen and then only do something once that thing has transpired. 

All right, well let's take one more step with JavaScript code before we take a look at what's really fun about this language and what you can do with browsers in particular by just cleaning things up a little bit further. I'm going to go back into the code here and I'm actually going to remove or cut all of this code out of the hello.html file itself. And I'm going to change my script tag to have nothing in between the open and closed tag, but I am going to give it a source attribute. 

And let's go ahead and call this, for instance, hello.js. So .js would be the convention for the file extension for a JavaScript file. And even though this is a little weird that we have the script tag and a source attribute then nothing in between the open and close tag, this is indeed the convention when you want to put all of your code in a separate file. 

And let me go ahead and do that. Let me go ahead and open my terminal window. Create a new file called hello.js. And then in that file, I'm just going to paste the very code that I just cut from the previous file. So no changes to the code. All I'm doing is factoring it out. 

And now I'm doing something just like our CSS factorization before, which confusingly used the link tag. This uses the script tag. This just now allows me to collaborate with someone like Carter or someone else so that they can do the JavaScript code, I can do the HTML, maybe a third person can do the CSS. And indeed, maybe we can build even grander things by designing things in this way. 

All right. Well, let me go back to my browser again. Reload the page. I shouldn't see any visual changes, but if I type in my name again, David, and click Greet, this still now works. And what my browser has just done underneath the hood is not only download the hello.html file as always, because there's now this script tag that's referencing the source of another file, just like an image tag might reference the source of an image, the browser is automatically helping me out by loading that into its memory as well. 

And now how about one final example? And for this one, I'm going to go ahead and not write it live but open it up as prepared in advance just to show you what you can do by listening for some of these other events as well, like the key up, the finger going down, the finger going up, and listening for exactly that so as the user is typing something you can do something interesting as well. 

I'm going to go back into my directory listing here. And I click on this source, a directory which has all of the examples that I wrote here in advance. And I'm going to scroll down to one called hello5.html. And in hello5 now we've gotten rid of the button and we just have this text box. But notice now what happens if I start typing my name as D-A-V-I-D. 

I'm not typing Enter at all. And in fact, if I start deleting and I change my mind and start typing Carter's name, notice now that the web page, the DOM inside of the computer's memory, is now automatically updating itself. So it's not even listening, it would seem, for a submit event anymore but maybe for a key up event instead. 

So let me go back to VS Code here. Open my terminal window. And in my source directory, let me open up hello5.html. Inside of the script tag, you'll see some code that's similar in spirit to before whereby I'm adding an event listener to the document waiting for the whole DOM's content to be loaded. But then inside of that function, I'm now doing this. 

I'm creating a variable called input and selecting from the document the one and only input tag that we saw just a moment ago. I'm then adding on line 11 in event listener for key up, which is exactly that gesture so that I can execute some additional code any time the human lifts their finger from the keyboard after typing a key. 

What do I then do? Well, I'm going to go ahead, it seems, and declare another variable called name. And I'm just going to select some p tag on the page. And now we didn't really see a p tag, so I think it's time to look at the HTML. If I scroll down to the bottom of the page where my actual HTML is, you'll see that there's just a form tag and no on submit handler anymore, as before. There's just an input tag and no button at all, but there is on line 29 here an open and close p tag just so I have an empty placeholder in which to put something like hello David or hello Carter. 

So that's why now on line 12 I can define a variable called name and I can select that p tag so that what do I want to do? Well, if inside of the input there's a value, so this is essentially checking for null or the absence of a string. So if input.value does not equal nothing, that is there is a value in that text box, well, this syntax here on line 14 is a very clever way of doing the following. 

Go into that name tag. That is to say, the empty paragraph. Change the inner HTML of it, the HTML inside of it, to be literally this. Hello comma. And then just so you've seen an additional piece of syntax, this is similar to Python's f strings, the syntax is a little weird in JavaScript. You actually use not single quotes, not double quotes, but back ticks, which on a US English keyboard are typically the top left hand key of your keyboard or thereabouts. And using dollar sign curly braces just like the curly braces alone in Python allows us to plug in whatever the value is of that input. 

However, if there's no value there, it looks like I'm just going to say hello whoever you are. And in fact, we can see that behavior now as I delete, delete, delete, delete, delete, delete, delete and nothing's there. Now that if condition is no longer true and so we see this default value instead. 

So this is only to say that by harnessing these various events that are constantly happening on most any web page, we can now register code just like we did way back in Scratch to actually listen for those events and do something with them. 

Now, it turns out we can do some interesting things even using third party code. And just as we used bootstrap a bit ago to make our table prettier, allow me to propose that we also take a look at this version of favorites as well. Let me go back into my source 8 directory and open up favorites2, which I made in advance, which looks almost the same, though I've zoomed in here a bit. 

But you'll notice somewhat subtly over the leftmost column in this table, you'll see now this arrow in gray pointing up and pointing down. Previously those were not there. All I had was a static HTML table with all of this data sorted in whatever order it was inputted the other day in that form. But now notice what I can do. If I want to sort in one order, I can click this arrow or the other order, I can sort in this arrow. So essentially doing it chronologically forward or backward. 

Now, how is that sorting happening? It's presumably based on all of the timestamps that were registered when we submitted that Google Form just a bit ago when it was live. But now using JavaScript, it turns out that we can use some logic somehow and sort this data by the same. And you don't get that automatically just by using HTML alone. 

Now, how did I achieve that? Well, it turns out if I go ahead and close these hello files. And in VS Code let's open up favorites2.html. You'll see that all of the HTML is actually the same if I scroll down and down through this file. But I added a little something interesting at top. I copied and pasted the appropriate URLs and HTML tags from bootstrap's documentation. 

And you'll see here that I have a file called not only bootstrap.min.css but also bootstrap.bundle.min.js as well as a couple of other things as well that allows me ultimately using third party libraries to add some special HTML attributes that those libraries told me to add. And then as soon as those libraries detect the presence of these attributes now on my own raw data, they do their thing and JavaScriptify, not a technical term, the entire table and now make it interactive and not static. 

So you'll see here that the aesthetics of the table are as before, table and table striped. But I'm adding now another HTML attribute called data toggle whose value is table. And I know that only from the documentation of these libraries indicating that that's how I can now enable this table to be interactive as I can too by adding data sortabls="true" on specifically the timestamp column. And the only thing unfamiliar here perhaps is I'm using TH for Table Heading as opposed to TD as I do elsewhere. But that's all that it takes to now focus on the raw data you want to present and let someone else do the heavy lifting of actually implementing the logic. 

Well, let's end with just a look at what more you can do with JavaScript and just how powerful it is when you combine a language like this with the data and the user interface you want to convey. Let's go ahead and open up within source 8 directory something called background.html. 

Now this interface here is quite simple. It just has three buttons, R, G, and B. And the background of course, notice by default, is just white. But when I click on the R, the background turns red. When I click on the G, it turns green. And the blue, it turns blue. And again and again. So how is this working? 

Well, if you think back again to the available events, perhaps I'm just listening for a click on those buttons and then doing something with maybe the CSS of the page to allow me to see those different colors. So in fact, let's go back to VS Code here and let's open up background.html. And in here, you'll see some simple HTML at the top. Just three buttons. But I've given each a unique ID so that I can reference it in code. 

And then inside of a script tag here below, because I didn't bother with the DOM content loaded event here, notice that I'm doing the following. I'm creating a variable called body that lets me select the body tag. I then have in these three lines some code that handles red. What am I doing? Well, I'm selecting from the document whatever HTML tag has unique ID of red. 

And then I'm adding an event listener for any click on that button. And any time someone clicks on that red button, I call this function anonymously. It doesn't even have or need a name. And this syntax here is powerful, because now in JavaScript I can alter the CSS of my page by doing body, which is the tag that I selected two lines ago, accessing its style, accessing its background color property, and setting it equal to quote unquote red. And I do the same down below for green. I do the same down below for blue. 

And the only thing worth noting here is that in CSS, it turns out it's the case that the CSS property for the background color of a page is actually background-color in all lowercase with a hyphen in between. Unfortunately in the world of JavaScript, a hyphen would be mistaken for subtraction, like background minus color, which would be wrong. So the convention in JavaScript is when you're trying to manipulate CSS, you take whatever the property name is, font size, background color, and you change it into so called camel case here. You get rid of the hyphen and you capitalize the subsequent words like color in this case here. 

All right. How about another? Well, it turns out back in the day, back in my day, there was a HTML tag that would actually allow you to do this. Create blinking text on a screen. It's rather unpleasant at this rate certainly. But how might this work? Well, it turns out in JavaScript if we take a look at the blink.html file here, we'll see that you can in your HTML do something literally as simple as hello world in the body. But then you can call this function here. 

It turns out just like document, there's another global special variable you can use in JavaScript and browsers called window, which refers to all things related to the window itself. The window comes with a set interval function, which lets you do exactly that. Set an interval in milliseconds. And after every expiration of that interval, some function will be called for you. So in this case, it's saying every 50 milliseconds. But let's actually slow that down now to 500 milliseconds or one half a second. Call a function called blink. 

Notice I do not have parentheses after the blink name because I don't want to call blink now. I want to tell the JavaScript to call the function called blink every 500 milliseconds. Now we'll see in a moment what that code looks like, but let's go back to the page and reload. And you'll see now that it's a more pleasant blinking, if that's even the case, every half second because I'm now firing that event, that is I'm calling that function now, every 500 milliseconds instead. 

How am I doing that? Well, in this same script tag, I've invented my own blink function. This has the distinction back in the day of actually being an HTML tag and among the few tags that the world removed and got rid of so that it's no longer used because it's not all that user friendly. 

But down here what am I doing? I'm getting the body of the document itself with this variable and then I'm checking two CSS properties that we didn't talk about before, but it turns out that you can check and set the visibility of an element in JavaScript by going into that tag, checking its style, and getting its visibility at a property. And if it happens to equal hidden, the next line of code here, 13, sets it equal to visible instead. Else if it's not hidden, it must already be visible. And so line 17 flips it the other way and changes it to hidden. 

Here left hand, right hand clearly not talking. No idea why the opposite of visible is not invisible. It's indeed visible and hidden. But this just allows you every time this function is called to change the property from one value to another, achieving that blinking effect. 

You can do even more powerful things that you and I take for granted every day. Let's go into source 8 and go to autocomplete.html, which I wrote in advance. And this is a page that also loads into memory a really big dictionary that you might recall from problem set five. And if I go ahead and type in something like C-A-T, you'll notice dynamically an unordered bulleted list appearing below the text box that shows you all of the words in that dictionary from p set five that start with C and then C-A and then T just like the autocomplete you see every day on your phone and Google or websites like it. 

How is that working? Well, probably I'm listening for the key press going up. As soon as that key is pressed, I'm probably searching through a big array really of all of those words, maybe using linear search, maybe binary search if faster than that. And then looking for any string in that array that starts with C or C-A or C-A-T. And then I'm generating automatically the HTML therefore. 

But perhaps most familiar nowadays is just how much your phone and your laptop know about you. And let me go into a final example here in source 8 called geolocation.html, which is a term of art that just refers to figuring out your geography. For instance, your GPS coordinates. 

Now here we have a third and final global variable that your browser provides you with called navigator. And in navigator, there's a special object called geolocation that comes with a function called get current position. So if you call navigator.geolocation.getCurrentPosition and then pass in a function of your own that doesn't need a name but does take an argument, in this case I called it position, as soon as the browser or as soon as the phone has figured out where in the world that user is with that browser at some latitude and longitude, the browser will automatically call that function for you. 

And you can do anything you want with the position that comes back, the latitude and longitude respectively. So I'm going to use a function that's not often that helpful, but for our purposes today it's just going to write to the document itself to my big rectangular region whatever the latitude is, then a comma, and then the longitude as well. 

So if we go back with this final flourish into source 8, open up geolocation.html, you'll see that my browser first wants my permission to let this website my own know my location. I'm going to go ahead and click Allow. Crossing my fingers, because it might take a moment for the phone or the laptop to figure it out. And it looks like according to Google, I am right this moment with my Mac at latitude longitude 42.375 comma negative 71.11. 

Let's go ahead and highlight and copy that. Let's go to a website like googlemaps.com. Crossing our fingers. If you've never done this, you can search for GPS coordinates too. Let's hit Enter. And amazing. We are indeed in Sanders Theater, roughly there, standing on this stage on Halloween. And that then is week eight. We will see you next time. Happy Halloween. 

[APPLAUSE] 

[VIDEO PLAYBACK] 

- Off you go. Buffering. OK. Josh, nice. Helen. Oh. 

[LAUGHS] 

Moni. Oh no, wait. That was amazing, Josh. Sophie. 

[LAUGHS] 

Amazing. That was perfect. Moni. 

[LAUGHS] 

I think I-- over to Yoel. Guy. That was amazing. Thank you all. 

- So good. 

[END PLAYBACK] 

[MUSIC PLAYING] 
