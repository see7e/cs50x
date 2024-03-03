---
title: SHORTS8 - INTERNET PRIMER - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

DOUG LLOYD: If you've been watching these videos in the order which we recommend, we're about to undergo bit of a culture shift. Because now, we're going to start talking about the internet and web technologies. So up until now, we've really been doing a lot of C. And when we've been running our programs, we have been running them from the command line. That's pretty much how the users have been interacting with the programs that we write. They pick something to prompt, something happens in the terminal window, and then it's done. 

Sometimes you might have persistent data that remains afterwards. But that's pretty much it. It's at the command line. It's the only way the user can interact. From this point forward, we're going to start transitioning so that the users can interact with our websites. So we're going to be writing websites, which aren't written in C, but are written in a variety of other programming languages, including PHP, and it's sort of helper languages, HTML, CSS, and the like. So we're going to start talking about those things. 

Before we get into web programming itself, I think it's probably a good idea to take a step back and talk about how computers and humans interact over the web. So this video is really a primer, a basic guide, to the internet. Now, the caveat here is the CS50 is not a networking class. So what we're going to be talking about here is pretty high level. We're not going to get into any low level details of how all this stuff works. If you're interested in that, I'd strongly recommend taking a class on computer networking. And we might even tell white lie or two just for the purposes of making the general understanding clear. 

So with that said, let's talk about how we interact with the internet. So here we are. Here's us. We're pretty looking forward to getting onto the internet, which as we all know, is chock full of cats. 

Now do we just connect to the internet like this? Well, probably not. Intuitively, you know that, say for example, when you change your WiFi network on your computer, you don't see one called internet unless that just so happens to be the name of your local WiFi. Right? 

It's usually something like home. Or if you're at work, it might be the name of your company. There's not just one option called internet. And so something or some things exist in between when we want to connect to the internet. What are some of those things? Well, we're going to talk about that. We're also going to talk about some of the important things we need in order to be able to connect to the internet. And the first of these things is an IP address. So you've probably heard the term IP address before. What does it mean? Well, an IP address is basically a unique identifier of your computer on a network. Just like every home or office has a unique address to which one could send a mail. 

Similarly, every computer if it wants to receive data or send data, needs to have a unique address. So that when information is sent or received, it's being sent from or received to the correct location. This addressing scheme, as I said, is called IP addressing. IP is stands for Internet Protocol, which we'll talk about again shortly. 

Now, what does IP addressing look like? Well, the scheme basically was, when it was first implemented, to give every computer a unique 32-bit address. That's a lot of bits. That's 4 billion addresses. 

And generally, instead of using hexadecimal notation, which we've used previously in the context of pointers in C to talk about addresses, we usually represent IP addresses in a little bit more of a human friendly way, representing them as four clusters of 8 bits represented as decimal numbers. Because humans don't frequently speak hexadecimal, unless you're programming. But people who use the internet aren't necessarily programmers. 

And so making it easy and accessible for them to be able to talk about what their IP address is in case they maybe need to call up somebody to troubleshoot something, it's better to make it in the more common conventional decimal number format. And so an IP address just looks pretty much like this, w.x.y.z, where each one of those letters represents a non-negative value in the range of 0 to 255. Recall that an 8-bit number can hold 256 distinct values. 

And so that's why our range is 0 to 255. And we have four clusters of 8 bits for a grand total of 32 bits. And so an IP address might look something like this. This is sort of a generic default IP address, 123.45.67.89. All of them are in the range of 0 to 255, so that's a valid IP address. 

Here at Harvard University, all of our IP addresses start with 140.247. That's just the way that the IP addresses in this geographic area have been assigned. And so this might be an IP address that might exist here at Harvard. 

So as I said, if every IP address is 32 bits, we have about 4 billion to give out, a little more than 4 billion. But we can kind of see a problem, right? What's the world population right now? 

Well, it's somewhere north of 7 billion people. And in the Western world at least, most people have more than one device capable of internet connectivity. I have one right here. And I have another one in my pocket. And I have one back in my office. 

And so that's three. And that doesn't even count the ones that I have at home, too. And so that's kind of a problem, right? We have at least 7 billion people and only 4 billion addresses. 

And every device is supposed to be uniquely identified. We have developed some workarounds to deal with this problem, something called a private IP address, which we're not going to get into in this video. But basically, it allows further the web, the internet, to kind of fake out a little bit that you have a unique address by having private addresses and then funneling them through one single address, which is shared by many different computers. 

But that's really not a long term fix. Even that fixed isn't going to last forever. And so we need to have a different way of dealing with this. 

So as I said, we had about 4 billion. But that's not going to be good enough, right? And so the way that it has been decided there we're going to deal with this is to make longer IP addresses. Instead of 32-bit addresses, we're going to have 128-bit addresses. So instead of 4 billion addresses, we're going to have that huge number of addresses, which is 340 billion billion billion billion, so a lot of IP addresses. 

And this new scheme is called IPv6 is commonly how it's referred. The old scheme being IPv4. It's a bit of a problem in that this problem has been known about for a really long time. 

And you'll see this a lot in the context of computers and computing. We're good at anticipating problems. But we're bad at dealing with them even though we know about them. So IPv6 has been around for a while. And only in the last couple years have we actually started phasing in these IPv6 addresses to phase out the IPv4 addresses. But some places do have them. And they look similar to a regular IP address. But they are a lot longer. 

So instead of now having four clusters of 8 bytes for your address, we now have eight clusters of 16 bytes. And 8 times 16 is 128. And we represent these in the less conventional hexadecimal form. Because having 16-bit numbers means that instead of being a range of 0 to 255, We'd have a range of 0 to 65,535. 

And so having a bunch of those stuck together would be very difficult to read. And so we usually use hex just out of convenience. And so a typical IPv6 address might look something like this. 

It's certainly a lot longer than the IPv4 address we've seen before. But this would be a valid IPv6 address. This one is also about IPv6 address. 

This one happens to belong to Google. And notice there's a bunch of zeros there. Sometimes these addresses can get so long. And since we're still pretty early in IPv6, sometimes there can be big chunks of zeros in there that we don't need. 

If you're reading this out loud, it's 2001.4860.4860.0.0.0.0.8844. It's kind of a lot, right? So if you see a bunch of zeros, you might sometimes see an IPv6 address like this, where they omit the zeros and use a double colon instead. This is OK, though. Because we know that there are supposed to be eight distinct chunks. And so by implication, we see four. So we know that there must be four sets of zeros like this, that fill it in. 

So sometimes, you might see an IPv6 address not having eight separated chunks like we do here. You might see it looking like this. And that just means that everything you don't see in between where that double colon is is just zero separated. 

So, OK. We know a little bit more about IP addresses now. But how do we get them? We can't just pick the one we want. If we did that, we might end up fighting somebody for the same IP address. Or somebody might have chosen it previously. If we try and take it, we're going to run into a bit of a problem. And so we can't just pick the IP address that we want. 

So the way that we get an IP address is somewhere between our computer and the internet, that big internet out there, there's something called a DHCP server, a Dynamic Host Configuration Protocol server. It's a big mouthful of text. But really all it does is it assigns you an IP address. 

Your DHCP server has a list of addresses that it can validly assign. And it gives you one. That's pretty much all there is to it. Now before DHCP, this task of assigning addresses fell to a system administrator. So an actual person would have to manually assign your computer and address when you connected to a network. So DHCP just sort of automates this process of giving you an IP address. But that's how you get it. It's just a program running somewhere between you and the internet that has a bank of IP addresses that it can give out. And when you connect to the network, it gives you one. So let's revisit this diagram. Somewhere between you and the internet, there's a DHCP server. OK. So that's good. Now, let's talk about DNS. So we've talked although these IP addresses. And we know that if we're going to uniquely identify a device on the internet, it has to have a unique address. 

And we could visit that address if we wanted to. But you've probably never typed in something like 192.168.1.0 into your browser, right? You don't type in numbers into your browser. You usually type in human readable names like google.com or cs50.harvard.edu, right? 

Those aren't IP addresses, though. So exists this service called the Domain Name System, DNS, that translates IP addresses to human comprehensible words or phrases that are much more memorable than remembering a set of four numbers or, soon, a set of eight hexadecimal numbers. That would be really challenging, right? 

Think about before the days of cell phones. You had your memorize your friend's phone numbers. It might have gotten tough after a little while. And similarly, if you want to visit a bunch of websites, you probably don't want to remember a bunch of numbers. You'd rather remember a bunch of words. 

So this mapping, this translating, of sets of numbers to human readable names kind of makes DNS the yellow pages of the web. And you can think about it as if it's just a huge list running from 0.0.0.0 all the way down to 255.255.255.255, which would be the highest possible-- that's the full range from 0s to 255s of all 4 billion-ish IPv4 addresses. I made up the ones on the top and the bottom. But the one in the middle there is actually an IP address. So if we visited 74.125.202.138, apparently that translates to that site there, io-- what the heck is that? Well, not every name that maps is actually clear what it is, right? 

So sometimes somebody who owns an IP address might name their host something that they're actually not. For example, that IP address if you went there, is actually just google.com. But Google has a lot of different servers. 

And they can't call them all google.com. So they have their own internal system for translating google.com to whatever server actually is connected to that IP address. And then there's another system that exists between to translate that gobbledygook here to google.com. But we won't get into that. 

And similarly for IPv6s, we're also going to have a yellow pages that'll be a lot bigger. And similarly, in the middle there-- it was tough to find an IPv6 address that was legitimate. But I found one for Google. 

But it's Google's Irish website. But if you went to that IPv6 address, if your browser was IPv6 capable, that would bring you to Google's Irish homepage. So there you go. 

But this isn't entirely true, right? This the system seems cumbersome, right? If there's a huge list of 4 billion things to have to look up, that's pretty big. There's no yellow pages of the world, right? If you still get the yellow pages delivered to you-- I got mine the other day, and I just recycled it. But if you do get the yellow pages delivered to you, you don't get a book that's every phone number that exists on the planet, right? You get a list of the local phone numbers, the ones you're most likely to call. 

And that's actually what DNS is. If you think about it, DNS is really the local yellow pages. And large DNS servers like google.coms, they are actually just more like libraries that have a copy of all of the local yellow pages or all of the local DNS records. So there's really no one repository of the full DNS of the internet, just like there's no one yellow pages of the world. 

There are all these local small scale DNSs that exist out there. And there are services that aggregate them together. But they depend on those smaller DNS systems updating their information, so that they have the most accurate information. 

So again, this analogy is large aggregating DNS systems are like libraries that have a copy of every yellow pages of the world. They don't themselves update those books. They depend on the books coming in, so they can update the information if they need it. 

So the DNS system is not a giant block. It's decentralized across many, many servers. So now we know that somewhere between us and the internet there exists a DNS server as well as a DHCP server. 

Now, access points, what our access points? Well, access points you're probably pretty familiar with from actually connecting to the internet. That's the network that you choose, the home or your work network or what have you. 

And I'm generalizing the concept of an access point here for purposes of this video. But there are actually a lot of things that can be rolled up into access points. There are concepts of routers, which is sort of a general term that we use. 

But there are also switches and things actually called access points that are separate from this general concept of an access point. But basically what happens is with IPv4, I said we have this concept of private addresses, right? And instead of every machine having a unique IP address, which we have run out of, because we're over 4 billion devices trying to connect to the internet, what we do is instead assign an IP address to a router. That router or access point just in your home, for example. 

And the router's job as to sort of act as a traffic cop, allowing everybody who's connected to that router to use the same IP address to get out. Does that make sense? So everybody at your home has a private IP address. They can't connect to the internet, or the internet rather can't speak to them, through that private address. They can only speak to them through the address in the router. And it's the router's job to take information that you're sending the router and direct it to the correct place and for information that's coming into the router for the router to send it to you. 

So the routers are really the devices here-- particularly a router in your home, the most common sort of usage case for most people-- that has the public IP address. That's the device that's connected to the internet. And you connect to the router to have information flow through it on your behalf. 

As I said, a modern home network, the router and switch and access point are all kind of bundled up into a single device. Sometimes a modem is bundled in there as well. That's usually just called a router. But it's really all of those things together. 

Large scale business networks or so-called Wide Area Networks, WANS, actually keep these devices separate. They have a switch. They have routers. They have multiple access points. 

For example, at a university you'll see things that look like so-called routers mounted are all around campus. Those are all access points that flow into routers, switches, et cetera, to pass information along. Because these networks are so big that one single access point can't cover its large area. 

And so these large networks, business networks, et cetera, split these into separate devices, so the network and scale and grow if needed. So again, somewhere between us and the internet, we have an access point. And that's what we connect to. And through there, we can get to the internet. As I said at the beginning of this video, this is not a course on networking. So this is not the entire story. And I've kind of glossed over it. And maybe I've left you even a little bit confused as to what some of these things are. But that's OK. 

We don't need the whole story. It's enough for us to know moving forward just basically a little bit about how the internet works. So what we know is we have these private networks at our house. 

And we connect to a router. And that router is connected to the internet at large. But what is the internet at large? I keep saying this, but what is it? 

Well, it's really just all these individual networks at my house, and at your house, and at every other house, that are connected together. It's an interconnected network, an inter-net. So instead of thinking about the internet as this giant cloud, this ethereal thing that exists out there, it's really just a connection among all of these networks. 

So here we go. We have our local network. And we're not the only person probably on our local network trying to use the internet. There's probably several of us trying to get in. 

And we're not the only network that exists in the world, right? There are other networks, too, that are trying to connect to the internet. But the internet is not, again, a separate entity. 

It's just a set of rules that allow these networks, these small networks, the blue, the purple, and the red network here, to communicate with each other. So there's no thing they're all connecting to. They're all just connected to each other, right? 

And so somewhere on these networks exists the services that we actually want. So maybe in the blue network is where Google lives. And in the purple network is where Facebook lives. And in the red network, well, maybe that's where all those cats are. 

And so if we want to get information about cats, we just traverse this chain of networks to get the information we want. And here, I've represented the network as all being able to talk to each other. And we can only talk to the network. But the network can't talk back to us. 

But that's not true either, right? This is all a two-way street. Information can flow through networks back and forth. 

How does it do that? Well, the internet's really a system of protocols. And we're going to start talking about what those protocols are in future videos. 

But again, the internet is not a separate thing. It's a set of rules that defines how networks communicate, these small networks, these local network that we're used to, the people in our house, the people at our school, the people at our job, all sharing a network. And how these networks interconnect and talk to each other, that's actually what the internet's all about. So let's, in a future video, talk about some of the protocols that comprise the internet to hopefully give you a bit more of a well-rounded understanding. I'm Doug Lloyd. This is CS50. 