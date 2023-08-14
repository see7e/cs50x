---
title: LECTURE_PLUS - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] DAVID J. MALAN: All right. So this is CS50. My name is David Malan, and this is Harvard University's introduction to the intellectual enterprises of computer science and the art of programming. And this, of course, is our special family weekend, wherein not only our CS50's own students here in the audience, but also some family members as well. 

Now, you're showing up in the semester a little bit late. We've just tackled week eight, which is really our ninth week since computer scientists start counting from zero. So we've done a whole lot of work over the past few weeks, as you might have heard via emails or text messages home, including a language known here as binary. 

So on the screen here, of course, is a lot of zeros and ones. And suffice it to say, let me sum up the past nine weeks with this is what's going on underneath the hood. But of course, today, we thought we'd make things a little more accessible, a little more broadly applicable. 

And indeed, our focus today will not be on what these patterns of zeros and ones represent, which in astute, I might notice are replicated visually with these light bulbs being in a pattern on and off. And as your child might have hinted before class, or perhaps, now, this might very well spell a word up to eight characters long because you can encode, even in the real world, things digital too. But today, we'll focus on things much more high level, this notion of cybersecurity, like the security of our data, our privacy of our systems, particularly, on the internet nowadays because presumably, all of us are carrying technologies around in our pocket using laptops and desktops every day. 

And so the goal today is to stipulate that this is what's going on underneath the hood. But let's solve some problems at a higher level, so that your homework, when you go back to wherever you're visiting from, can actually be to apply some of today's lessons learned. So with that said, perhaps, the most common familiar defense of one's systems, and data, phone, and laptops, and desktops would just be these simple passwords. 

Unfortunately, you and I are-- frankly, as humans, not all that good at choosing passwords. And this is in itself a relatively weak form of defense, even though each of us has dozens, hundreds, of passwords nowadays or at least dozens or hundreds of accounts, maybe fives or tens of dozens of passwords. Indeed, if you're in the habit of reusing passwords, we'll see today, probably among our first lessons learned. 

So for instance, if we look back at the past year, 2021, thanks to security researchers who take a look at data that has been hacked or leaked online by way of public databases, we have a sense as computer scientists of what the most popular, or equivalently, what some of the worst passwords are that you and I are choosing for our system. So as of this past year, according to one measure, the most commonly used password in systems everywhere was 123456. All right? The number two password in our top 10 here list was only slightly longer, 123456789. 

After that, we took a turn in the other direction, 12345 alone. After that, it got a little more interesting, qwerty, which might sound pretty cryptic, but not if you look down at your US keyboard. And it's the top left hand row of the keys on an American keyboard, so also, not all that hard. 

Perhaps, not surprisingly a little disconcertingly, number five was password. Meanwhile, number six returns us to digits, 12345678. After that, really, less effort, 111111. 

After that, a little more variation, but not all that much 123123. After that, it's getting even less interesting, 1234567890. And then lastly topping the list is just 1234567. 

So this is not a good top 10 list to be on. So among today's first takeaways is if you see your password on the screen, you didn't make the list in a good way. This means hundreds, thousands, millions of other people probably have that password of yours. 

Now, in and of itself, that's not necessarily worrisome because I don't know who has these passwords in a room as large as this. But just intuitively, why is this a bad thing? Either parent or child is welcome to raise a hand here. Why might this be-- intuitively, yeah? 

AUDIENCE: Access to it. 

DAVID J. MALAN: So access to it. I mean, we literally, as computer scientists, now have a database of really common passwords. And your thoughts? 

AUDIENCE: [INAUDIBLE] find it out quickly. 

DAVID J. MALAN: Yeah, you can just find it out quickly. I mean, you could imagine trying to guess someone's password by just typing in random letters, random numbers, random words, but not if you have a top 10 list. The adversaries in the world might as well just start with this list. 

Now, you'll notice that even absent from this are slight variance. Some of you might be thinking, I'm not on the list because I do something clever like I use an exclamation point for the number one, or a three for an E, or a 5 for an S. And based on the smiles in the room right now, you're not all that clever, it turns out, because other people are smiling too, which is to say that an adversary can take those same heuristics that you might think are making things more secure by just tweaking some letters to numbers or vise versa. But if you're doing it and other people are doing it, the bad guys, so to speak, are going to be doing it as well. 

So unfortunately, when it comes to passwords, better is longer, and random, and really unguessable. But that's not what most of us have. In fact, case in point on our phones, whether you have an Android device or an iPhone nowadays, odds are you have something relatively simplistic protecting it, if you have anything at all. But at least, Apple and Google are pretty good at at least nudging us to choose these kinds of passcodes now. 

And a four-digit passcode is quite common nowadays. And so here's where we have an opportunity, thanks to the URL that you saw on the screen earlier, to conjecture as a group just how long might it take an adversary, someone out there who's out to get us or get one of us-- how long might it take an adversary to figure out your phone's four-digit passcode? This is CS50's own Carter. 

Carter, if you could switch over and pull the audience here-- if you take out your phone or laptop, whatever device you might have used a few minutes ago, to scan that QR code or to visit that same URL, you can see these questions on your browser. And if you can't, that's fine. We'll share some aggregate data, nonetheless. 

But you should have an opportunity to tap one of your answers. And we'll give folks a few more seconds if you'd like to play along at home. And here in just a moment-- probably have many people reporting. 

But why don't we go ahead and take a look at some percentages? It looks like most of you-- 60% to 70%-- are proposing just a few seconds, so that's not all that good news if it's a four-digit passcode. Some of you are hoping it's a few minutes. 8% are hoping a few hours. More than 4% of you are really hoping, perhaps, it's a few days. 

Well, let's actually consider how we can answer this question and make today not just conceptual, but a little quantitative too and see if we can't slap some numbers on questions like these, so ultimately, you can make more informed decisions with your system's security. So for instance, when it comes to four-digit pass codes, rather than just consider how secure it is, well, let's make it a more precise question like, what are the forms of attack? Well, the simplest attack might be just someone grabbing your phone, be it, in your family, or maybe at Starbucks, or the airport, or the like and just starting all possible combinations, maybe 0000, then 0001, and 0002. 

We could maybe automate this a little bit. So for instance, I might potentially be able to do something like robotosize this here. Let me go ahead and full screen a quick video here that's just going to paint a picture in just a moment on the screen of how, if we're a really clever adversary and know how to build things, well, at least, maybe we could automate some of that process. So here's an Android phone sitting on a counter. Here's a very simple tripod and a little touch device robotically doing all of that hacking for you starting at 0000 probably all the way up to 9999. 

Now, that too wasn't necessarily all that fast, but at least, the adversary can step away and doesn't actually have to be bothered with the time involved, the cost involved, in actually hacking that particular device. Well, let's go one level deeper, a little more interestingly, and consider here how much time really this so-called brute force attack would take. And that's actually a term of art, much like in yesteryear when maybe there was a battering ram trying to brute force their way into a castle or something like that. A brute force attack digitally is just someone trying manually all possible codes or maybe robotically trying all possible codes, but generally automating the process in some way to go through all possibilities. 

Well, if you've got, for instance, a four-digit passcode-- let's ask maybe a follow-up question here, not how long it will take, but how many possible four-digit passcodes are there? Because then maybe, we can do some quick math. And if every passcode takes me a second, or a few milliseconds, or the like, then I think we can try to extrapolate from that whether the first answer was seconds, or minutes, or days, or hours, or something else. 

So how many four-digit passcodes are possible? If you take out your same device, it should have just changed automatically if it doesn't seem to have maybe reload your browser with some menu option. And then tap in here, how many four-digit passcodes are possible? Four total, 40, 9,999, 10,000. Or unsure is OK too. 

So let's see. We'll give you a few more moments. How many four-digit passcodes are possible? And shall we reveal the results? 

So now, it looks like a few of you-- 2% of you are saying just for passcodes, 40, 9,999. There's definitely some contention here. And 6% are unsure. 

Well, how do we wrap our minds around this? Well, let's just do this real simple here. Let me switch back over to doing a bit of math. 

And if we have here 10 possibilities for each digit, if there's four digits, each digit can be zero, one, two, three, four, five, six, seven, eight, nine. So that's 10 possibilities. So if you think about the number of permutations, that's 10 possibilities for the first digit times 10 for the next, times 10 for the next, times 10 for the next. And so if we do that out, 10 times, 10 times, 10 times, 10 or 10 to the fourth, there are, indeed-- and 66% of you found 10,000 possibilities. 

And so now we can kind of work backwards and decide, how long is it going to take for an adversary to hack into this phone? Because if it's one attack, one guess per second, well, that's going to map out to 10,000 seconds, but maybe not if the adversary isn't a roboticist or a human. What if they're a software programmer or someone who has taken even a class introductory, like CS50 and learned a little bit of programming? 

Well, a little bit frighteningly, it's not all that hard to hack into systems if you just know how to code, too, and really have the computer do your work for you. So in fact, let me go ahead and change over to another screen on my computer here. This is different for students in the group from VS Code. This is just a black and white version of it that we've used briefly in the past. 

And I'm just going to go ahead and create a program called crack.py. To crack something just technically means to figure out what it is, figure out a password in this case. And .py means I'm going to use a programming language that we here in CS50 have been dabbling in the past couple of weeks with more to come next week as well. 

So it turns out, and you need not understand each of these lines of code, if I want to try, maybe, generating all 10,000 possible codes, I'm not going to bother with a robot. I've got all these cables coming out of my computer. And odds are one of them is a USB cable or a lightning cable. 

Surely, we could figure out how to connect laptop or desktop to phone and just automate the process nowadays by just sending all of the numbers into the phone until one unlocks the trick just like in the movies or TV. Well, in Python, I could write a program that does this as follows. I can import, so to speak, all of the decimal digits, zero through nine. 

And this, for students in the room, is just a slightly better version of typing out 10 different numbers manually. I can also import from a library, so to speak, called itertools for iteration tools, which means to do something again and again. I can import a function called product, which means the cross product. Combine this with this some number of times. 

And then it's just two more lines of code. I can use what's called a loop in programming. So for every pass code in the cross product of all 10 of those digits repeated, a total of four times-- let me go ahead and-- rather than bother connecting my phone and hacking my own phone, let me just print out every one of those 10,000 codes on the screen, and we'll see how fast the hacker could do this. 

Let me go ahead. And print and with an asterisk, which is a little trick to format it nicely, I'm going to print out each of those pass codes. And that's it, four lines of code, maybe 40 seconds of talking, but maybe really four seconds of coding if I actually did this without the audience. 

And now let me go ahead and save the file. And I'm going to run, as we do every day in class of late. Python of crack.py. And when I hit Enter, I should see on the screen all 10,000 possibilities from 0000 9999. So let's see. Is it a few seconds, minutes, hours, or days? 

Done. So barely even seconds plural if that. So that should be a little disconcerting because all that adversary needs to do is grab your phone off the counter, plug in a cable, and boom. They're done. There's no ticking clock or worries as in the movies or TV that maybe you're going to come into the room. You don't need that much of a window of time. 

So what would be better than this? Well, let's consider what our options might be if we don't want to just use four-digit pass code. Some of you, indeed, might have better passcodes than that. And maybe, you use four-letter passcodes instead, so A through Z, maybe uppercase and lowercase. That starts to make things a little more interesting. 

So should we poll this question too? If we upgrade from four digits to just four letters, English letters, A through Z, uppercase and lowercase-- why don't we go ahead and pol the group here and ask how many four-letter passcodes are there instead? 

So this time, the range starts at four. Still not the right answer, though, this time. How many four-letter pass codes are possible? 

[INAUDIBLE]. Take a couple more seconds. All right. Almost a couple hundred responses in already. A few more seconds. And why don't we go ahead and reveal now the answers, which are-- 

OK, so we solved a couple of problems at least. OK, someone's just messing with us now. All right. So it looks like most of you-- 76% of you have claimed it's seven million plus possibilities. 

So that's encouraging because that's a whole order of magnitude more than before. Well, let's figure out how we might do this mathematically. So if we've got 26 lowercase, 26 uppercase, that's 52 possibilities now for each of those four digits. 

So that's 52 times itself four times, which, indeed, either off the top of your head a good guess, a calculator on the same device you're using right now, indeed, gives us seven million instead. Well, what might be slightly better than that? Well, maybe four characters. 

And this, indeed, is what your Macs, PCs, and phones are urging us to do nowadays, not just numbers, not just letters, but really annoying punctuation, so it really looks cryptic not just to the adversary, but also to you and me, unfortunately. And that's the downside. But here now, we have a mental model, and really, a computational framework via which we can evaluate the security of these. 

And I'll go ahead and spoil some of the math here. If we've got 52 letters of the alphabet, uppercase and lowercase, 10 digits, and if I count them out on my keyboard, about 32 punctuation symbols in typical English grammar, that actually gives us 94 possibilities now, which is up from 52, which is up from 10. So now, we're really moving. And now that would give us 78 million possibilities, so another order of magnitude. 

Now, it's still going to be relatively fast because you know what? I can actually do this. Let me go back into my code here. Let me reopen this same program. And I can point out just how easy it is to make these changes. 

Instead of importing digits as before, I can import, as your child might know, ascii letters, which are A through Z, uppercase, lowercase. And I can just change this here, ascii letters. And so this was that first version where we just changed to letters. 

Let me now rerun the code. And instead of seeing numbers, we'll see letters flying across the screen. And if I walk over here to the screen, we'll see that. By the time I get here, we're halfway through the entire alphabet lowercase. If I now start walking away, I think, yeah, we're already done now with uppercase as well. 

If I upgrade this slightly further-- let's go ahead and take it one more level and, perhaps, do, let's say, ascii letters, and digits, and punctuation. And this would be the Pythonic way to say that. And I'm going to add to those letters those same digits, those same punctuation symbols. Let me shrink my font just so the code still fits on the screen. 

And what we now have is with a two seconds of changes, a program that if I run this version-- whoops-- without the typographical error-- this is what we call in CS50 a bug. So now, we run the same-- this is what we call in CS50 a second bug-- punctuation. This is where I cross my fingers. 

OK. So now it's going to be a little hard to see as flies across the screen. But you probably are seeing glimpses of some weird punctuation characters as well. And I won't waste our time trying to talk through this because this is going to take longer. We're still in the lowercase. I'm still over here already. We've not even gotten to N, now O, then P. 

So this is going to run longer. But let's end with one final question on the security of all these systems. I'm going to cancel that by hitting Control C on my keyboard. And let's ask the question instead, if we use eight-character passwords, so twice as many characters. But even that is not terribly long. 

This is eight characters alone on the stage, eight characters. Using letters, numbers, and punctuation might be better. Let's do one final vote here, if we could. 

On your same device, how many eight-character possibilities are there now for these passcodes? And now four didn't even make the list this time. All right, a few more seconds, about 100 responses so far. 

How about we go ahead-- and, Carter, if you wouldn't mind, let's reveal the results based on the vote, a pretty decent spread here. Although the quadrillions are quickly buzzing in. And they're contending with the others here. Looks like 44% of you said quintillion. 34% said quadrillion. 

And this time, for the first time, you overbid. So indeed, if we go back to the math here, at least, the majority over bid. If we have eight-character passcodes that gives us 94 times itself eight times or 94 to the eighth power. And in fact, that gives us roughly 6,095,689,385,410,816 possible passcodes. 

Now, what does that mean? Well, the adversary's algorithm, the step-by-step code that they write to try to hack into your phone, is no different. And honestly, if your passcode is eight characters long, but they're are 00000000, you're no more secure fundamentally. You really want to be somewhere in the sweet spot of that massive range of values, so that if the adversary tries this brute force attack just running through all possibilities, they will eventually reach your passcode just mathematically. It will be there. 

Hopefully, though-- well, maybe not hopefully-- you and I and they will be gone from this world because that much time will have passed. And if we do out the math here, this number of seconds, for instance, is long past when we will no longer be here. So that's the sort of measures. 

We don't sort of fundamentally change the equation for the adversary. It's still the same risk. It's still the same attack. But you significantly drive down the probability of success on their part. Or conceptually, you drive up the cost to the adversary. 

And indeed, even in the physical world, this is true. You just want your passcode in the digital world really to be better than someone else's because you want someone else's passcode to be the one that the adversary does something with. Just like in the physical world, even though it's a bit uncomfortable to consider, your house doesn't need to be 100% secure. And indeed, it's difficult to make it such. 

There's always going to be a point of weakness. Maybe it's that window, the door, or something like that. But if your home is more secure than the next door home, just probabilistically, you are more secure. 

You're not secure. And indeed, any website you see down the road that says, we are secure because we do X, Y, or Z, that's nonsense. Security is really about comparisons and evaluating things if quantitatively relative to some other system, relative to some other code. 

So what's the takeaway here? Well, hopefully, a non-trivial number of you will go home this weekend on Monday and change at least one passcode. But there's going to be a tradeoff here. 

We talk about this all the time in CS50. Any time we improve something, we pay some price in time, in performance, in cost, somewhere else. So what's the downside then of this advice that you should use minimally eight-character passcodes? Why might you want to say nay and not do this? 

AUDIENCE: You have to remember it. 

DAVID J. MALAN: Say again? 

AUDIENCE: You have to remember it. 

DAVID J. MALAN: You have to remember it, right? And so here, there is some sociology. There's some human behavior. Some of you might have colleagues, if you're working in the real world, at least, back in healthier times when you had colleagues with desks in cubicles. And there's probably one person in the office with a post-it note on their monitor with their passcode. 

It's a bit of a cybersecurity offense, but it's also a real world side effect, maybe of corporate policies, that aren't really calibrated for human behavior. So we'll see if there's some other defenses. And indeed, let me propose that we talk briefly about one that actually tends to kick in automatically. 

Even if your passcode is not as strong as we've just seen, one of these six quadrillion possibilities, well, what could we do instead? Well, has anyone-- and I'll zoom in on this here-- accidentally locked themselves out of their own phone before? When does that happen? Yeah, when you try the password-- 

AUDIENCE: Too many times. 

DAVID J. MALAN: Yeah, so too many times. Maybe your finger is slightly off. Maybe you're slightly off, and you just don't input the same passcode correctly after five times, 10 times. There's some reasonable threshold. 

And why does that happen? Well, Apple and Google equivalently figure just probabilistically if after 10 guesses, you still haven't typed in the right passcode, probably, you're not you. You're someone else who's picked up your phone, so we're just going to go ahead and lock you out. 

Now, what's the effect of this? Well, this means now that each of those possible passcodes no longer takes roughly one second. Now it takes roughly one minute. 

So the attack is still the same. But if it's now one passcode or 10 guesses per minute, we have significantly by a factor of 60 in this story slowed things down. And unfortunately, does anyone know what happens if you screw up again after a minute? 

AUDIENCE: It goes longer. 

DAVID J. MALAN: Yeah, it goes longer. It's like five minutes and then 10 minutes. And Google is kind of obnoxious about it. They don't even give you a time frame. They just say, try again later. 

And so that keeps not only the adversary out, but also potentially you. So therein lies that tradeoff. If you've forgotten your code, if-- nowadays, your finger is slightly wet, so the screen isn't responding correctly. These could be usability downsides too. So security is really just about finding the sweet spot among these various tradeoffs here. 

But there's other mechanisms too. And some of you might recognize this screen from Gmail via which, of course, you log in. But after you log into Gmail or similar websites, or apps, or systems at work nowadays, especially, you might be presented with what's called two-factor authentication. And what is this in a nutshell in layperson's terms? Many of you, if you do anything digitally at work, might have to do this now. Yeah? 

AUDIENCE: It sends a text to your phone. 

DAVID J. MALAN: Exactly. You get texted at your phone, an additional code that's not your same password. It's typically a numeric code, maybe six digits long. It expires after a minute or 10 minutes. 

But why is this a good thing? Well, one, it's no longer just a piece of information that you know or that you might have written down. It's information that changes every time you try to log in. But more importantly, it's a fundamentally second factor, which means it's not just something you know. Now it's something you have. 

So you, for instance, are the only one theoretically that should be receiving that code. And so now the adversary, if they want to get into your account, not only have to guess, or brute force, or maybe read off of a post-it note your password. They also have to physically have access now to that phone. 

So there's still a threat, absolutely, but it's not everyone on the internet with an internet connection. Now it's only the people in Starbucks. Now it's only the people at work. Now it's only the people in your home who might have access to that second factor. 

So there too, it just raises the bar to the adversary making it harder, more time consuming, more geographically impossible for them to attack you. But what's the downside of two-factor authentication, whether it's a device-- or even nowadays, it's in software, whether it's on your keychain or on your phone where you're prompted for this code. What's a downside that some of us have probably experienced too? 

AUDIENCE: You forget your phone. 

DAVID J. MALAN: You forget your cell phone, absolutely. Right, the factor that you have, you don't have with you. Or maybe, you're in a basement somewhere, don't have reception. You're on a plane. You can't get the code. 

And so there too are these tradeoffs. And even IT departments need to keep that in mind because what does that mean for them? Well, if you don't have your phone with you and you are in the habit of calling IT to help you fix this, now there's a cost, a human cost, maybe even a financial cost. 

And so IT policy nowadays is really just about finding the right balance and where we want to spend our resources, but at least raise the bar to the adversary. But of course, there's other ways too. And this is going to be one of our homework assignments if you will after today. 

There's this software called password managers. And no need to buzz in on your phone, but maybe with a physical hand. How many folks here use a password manager? OK, let me ballpark this at 10%, 20%, perhaps. So we've got 80% upside here and a lesson learned potentially. 

So a password manager is just a piece of software on your Mac, your PC, or your phone nowadays that manages your passwords. Well, what does that mean? When you go to a website for the first time or you download an app for the first time and you have to create an account, you can still use your email address, or David as your username, or whatever your name might be. So you don't have to change that methodology. 

But instead of typing in 123456 as your same password for that website or app as well as for every other, now you use the password manager software to generate something difficult to guess for you. That is you tell the password manager, give me an eight-character random passcode, not 0000, but something with punctuation, with numbers, with letters. And better yet, the password manager, as the name suggests, remembers that password for you. 

And the next time you go to another website, you do it again with a completely different password, maybe same username, maybe two-factor authentication, but different password, different password, different password. And it doesn't have to be eight. I mean, I'm in the habit of using a dozen, two dozen characters in total. And at that point, I can't even pronounce the number of possibilities because it goes well beyond the quadrillions. 

So the probability that someone's going to get into one of those accounts for me now is very, very, very low. And they're going to take less interest in me and maybe more interest in someone else that's not using as good of a password. Now, what does this mean in real terms? 

Well, when you go to log into that managed site, you don't manually type your password anymore. In fact, you don't generally even need to know it. Nowadays, I probably don't 90-plus, 99% of my passwords. I entrust them to this password manager. 

Now, of course, you'd like to think that the password manager itself is secure. So what might that mean? Well, those of you who do use a password manager, how do you access that software itself? What's protecting your data in your understanding? 

AUDIENCE: Biometrics. 

DAVID J. MALAN: So maybe biometrics, like your face ID, or maybe your fingerprint, or maybe more simply, what else? 

AUDIENCE: A password. 

DAVID J. MALAN: Maybe just a password. And hopefully, that password that primary password, that gatekeeper, is not itself 123456. Otherwise, it doesn't matter how secure all of the others are. 

But if you're willing to put in the effort and pick one pretty long somewhat random very unguessable password that you just promise to commit to memory-- and maybe for backup, you literally print it out and put it in a safe deposit box or a safe, or just hide it somewhere physically that there's very low probability someone's going to find the backup copy, that might be alone. But of course, the flip side is now if you forget that primary password, you've now lost all of the eggs in the basket. If someone gets that primary password, now they have access to everything. So that's rather the tradeoff. 

But I dare say you're probably less threatened, depending on your family, by the people immediately around you than the billions of other people on the internet that have access, potentially, to those same systems. So there, too, it's a tradeoff. But it's up to you to decide whether or not to manage your passwords in this way. 

But if you were on that top 10 list, or even if you're not, but you can think of several accounts that all have the same password, you're probably going to benefit from something like this. And why is it bad, to be clear, to use the same password on multiple sites in case that's never sort of dawned in thought? Why is that a bad thing, to reuse a password on different websites, different apps? Any intuition? Yeah, in the back? 

AUDIENCE: Once attacked, it's easy to get to. 

DAVID J. MALAN: Exactly. Once it's attacked, you can-- the adversary, presumably, by transitivity, can see, oh, well, if this user's username is malan@harvard.edu on this website, and their password is foolishly 123456 or even something way more complicated, they can probably just assume with high probability that if I'm being a little reckless, let's try accessing malan@harvard.edu's use other accounts, other apps using that exact same password. And so by transitivity, essentially, you're putting your other accounts at risk. 

So what's maybe a takeaway? Minimally here, I would start to reconsider your passcodes on your most important data. Maybe it's medical. Maybe it's financial. Maybe it's email. Anything remotely personal that you really wouldn't want to have access. 

Do you necessarily need the same level of security on e-commerce sites or sites that you don't really care about or that you signed up for once and after that, that's it? Probably not. So you can decide for yourself, but again, software, like a password manager. 

And these are just some of the possibilities out there are probably to be your friend. A couple of these are free. They come with Windows or Mac OS. A couple are commercial. Harvard has a site license for students for one of these as well. So there are options out there. 

But what else do people use? What else can people use to keep their systems secure? So most of us nowadays have probably heard of encryption, this technique for just scrambling information. 

So when you want to send a message, an email, or upload a photograph, or use your credit card, hopefully, it's not just being sent out for all to see, but there's some kind of scrambling going on. And some fancy mathematics ensure that encryption ensures that only you, the sender, and someone else, the receiver, can theoretically see what that credit card number is, what that message is what that photograph is instead. So encryption is sort of commonplace nowadays, both in websites, and apps, and ATMs, and other such devices. But how does it work? 

Well, back in week two of CS50, your child learned a little something about encryption, otherwise, known as cryptography. And one of the algorithms we talked about was quite simply something like this. This is what we might call, not only CS50, but plain text, so very plain text that, in this case, is English and obviously, everyone in the room can read it. 

But what if I wanted to send this message out to someone in this room, or out on the internet, or maybe equivalently back in the day, maybe write a message down on a scrap of paper in grade school and pass a secret note, a secret love note to someone in class with hopes that the teacher or any other students in the class can't intercept it and read it? Well, you probably don't want to say, this is CS50, or I love you, or anything remotely sensitive. But rather, maybe you want to encrypt it. And let's change the T to a U. 

Maybe change the H to an I, the I to a J, the S to a T, the I to a J, the S to a T again, the C to a D, the S to a T. And we'll just leave the numbers, alone even though I worry someone could probably guess what this now does say, nonetheless. But what was the algorithm as I rattled those changes off, whether a student from week two or parents from week now? Yeah? 

AUDIENCE: It's a one-letter shift. 

DAVID J. MALAN: Just a one-letter shift. And this is more sophisticated called a rotational cipher or a Caesar cipher after Caesar back in the day. It's relatively simplistic. 

But back in the day, it's not so simplistic if you're the first person in the world to ever use it or think of it. But nowadays, this is not actually what we use. But it's similarly mathematical in nature. 

It's not quite as simple as just adding one or subtracting one to go from now what we call ciphertext to plain text. But it's similarly math that's involved. And let me just stipulate that the way the math works is that the sender and the receiver just have to have in mind some kind of secret. And the secret in this case would very trivially be one, but it could be a much bigger, much more unguessable number, or maybe some other secret we share, the presumption being that my classmates, my teacher in that grade school classroom, if they don't know what that secret is that number is, yeah, they could try to brute force it and try all possible mathematics, plus one, plus two, plus three. 

But that's going to take them some time. And they probably don't care enough. And so my data might be, therefore, relatively secure. 

But we use encryption all the time nowadays. And so for instance, this is at the start of most URLs nowadays, even if you don't type it yourself. With that said, Safari and even Chrome now are kind of simplifying, if not, dumbing down user interfaces to just hide details that you and I, as normal users, don't need to see 24/7. But it is there. 

And if in fact, on your phone or laptop, you click on the URL, even if it's super short initially, you'll probably see the whole thing starting with this. And the S means secure. The S means that encryption is being used. 

But there's other forms of this, not just when you visit websites. There's this, end-to-end encryption, which is being talked about more nowadays, especially during COVID times with so many more of us on video and talking about more sensitive things, telemedicine, talking to doctors, things that you also wouldn't want to verbally or visually get out into the wild just like text. What's different about end-to-end encryption versus HTTPS and the type of encryption that most of us use every day on websites alone? 

End-to-end encryption is sort of a better feature that you want to increasingly seek when using services like Zoom, or Microsoft Teams, or WhatsApp, or the like. Any instincts here? Yeah, over on the right. 

AUDIENCE: The encryption happens in the source and destination. 

DAVID J. MALAN: Good. So the encryption, the scrambling of information, happens in the source the sender, and the destination, the receiver, without a so-called middleman in between. And this is actually very different from most contexts nowadays that use just HTTPS because when you're using HTTPS to buy something on Amazon securely with your credit card, well, of course, Amazon needs to be able to decrypt the message at the end of the day. And so that's fine. 

But even when you're using services like video conferencing or maybe text messaging nowadays-- well, if you're using WhatsApp, that's owned by Meta. And if you're using Instagram, that's owned by Meta. There's a lot of middlemen in these apps that we're using. 

And if they were only using encryption period or only using something like HTTPS, yes, your connection from you to WhatsApp, and in turn, to the recipient might very well be secure on each end of that channel. But Meta in between the company and any other company in between could theoretically, for better or for worse, be looking at that data, whether it's to mine it for advertising purposes, whether it's to snoop on data that you're sending. That is not end-to-end encryption if the middleman, a company, typically, has technically access to that data. 

Now, Zoom, and Microsoft Teams, and WhatsApp, and iMessage, and other services with which you're familiar increasingly are offering stronger guarantees of encryption, whereby, it's indeed between parties A and B and not the one in the middle. Now, there's downsides here. And you can actually see this kind of functionality manifest in certain settings. For instance, besides iMessage, which just does this for you on iPhones or Macs, besides Zoom, you can actually fine tune these settings, indeed, within Zoom itself. 

So here's a screenshot that I took last night of just what the user interface looks like today to create a new Zoom meeting with the latest version of Zoom software. And maybe unbeknownst to you, there is a choice of buttons down here. And most likely, yours is, by default, enhanced encryption, which is brilliant marketing speak because it's just encryption. 

It's not enhanced. It actually ironically means worse than this. But they want you using it most likely, why? Well, it's a little easier to implement. It's a little less expensive for them computationally. 

And to be fair, enhanced encryption does scramble the data, but not in a way that Zoom can't see it. Zoom can, indeed, see it. But that's actually a plus in some context because if you want to do cloud recordings and you want a meeting recorded not on your Mac or PC, but let Zoom deal with that. 

If you want automatic transcription nowadays, so the words to appear, whether it's English or something else on the screen, well, you can't really lock Zoom or any other middleman out of that because someone needs to save it to the cloud. Someone needs to translate the voice to those English or some other language words. So enhanced encryption enables those features, but they also allow a bad actor, malicious employees, someone who's just nosey at Zoom or the equivalent middle man to just poke around your video conference and hear what you've said or see what you've typed as well unless you instead check this box as well. 

So increasingly look for mentions of end-to-end encryption. Or give that some thought when you choose a technology via which to communicate with someone, whether it's within your family or without as well. Now, last, but not least, there's other applications of encryption too. And this, too, might be a lesson learned as well, full disk encryption. 

So a disk is where your data is stored in your Mac, or PC, or even your phone. And full disk encryption just means ideally that all of your data is encrypted that is somehow scrambled. Now, hopefully, your password for your computer or phone is good enough so that even though the device is encrypted with that password, at least, you'll remember it. And your phone or your Mac or PC will automatically decrypt it for you. 

Of course, you can't scramble the information and hide it from ourselves. One of us, at least, for these devices needs to have access. But full disk encryption typically means that at least when you close the laptop lid or power down for the night, that even if someone else steals that device, opens the lid, unless they have your passcode, they can't even plug in fancy cables to the device and just rip the zeros and ones off of the device and see what's actually there. Full disk encryption means they could do that, but they would just see seemingly random zeros and ones. 

Now, there's a downside here too. This might slow things down potentially. But it is a feature increasingly that's offered and is absolutely something you should consider enabling in general, especially if your laptop or phone travels with you. And certainly, your phone does. 

Or if you plan to donate, or sell, or give away a device, you don't want to leave all of the zeros and ones, the remnants of your own sensitive data, passed on there. So Windows has a feature called BitLocker. Mac OS has a feature called FileVault. There's commercial options as well. 

But generally, we're at the point now in 2022 where clicking a button is sufficient to enable these features. With that said, don't rush into all of these decisions. I would make backups of your data. And don't maybe email CS50 if something goes wrong with that process. But I would do your own due diligence. But this, too, would be a menu of possibilities. 

And now, the bad side, the downside, of what seems to be great, this notion of full disk encryption. Unfortunately, just as we can encrypt our data to protect it from the adversaries, so can the adversaries if they get into our devices, encrypt our data and do what? Not tell us that secret key. 

And so this is generally applied in the context of ransomware, which tragically, you increasingly hear about in hospital systems, school systems, municipalities where systems are getting attacked. And the data is not just getting stolen because what is the adversary typically need with local municipal or even hospital data? The value to the adversary is encrypting all of the hospital, all of the municipality's data preventing them from accessing it if they have no backups or the like. 

And so ransomware is literally about trying to convince someone to pay you money or pay you Bitcoin or something like that to give you that secret key. And the key, in this case, is surely more sophisticated than the number one. But it's really the same idea. 

So here too, yet again, a tradeoff just as we sort of invent something for good, it can also be used for evil in so to speak as well. But it's really the same underlying principles, even though we keep seeing it and hearing about it, in these different forms. And lastly, if only because folks are generally familiar, but don't necessarily know what it is that it's doing for them, browsers nowadays have what's often called incognito mode or private mode, which has nothing to do with encryption, but does have to do with cybersecurity, or really, cyber privacy, keeping your data from prying eyes. 

Incognito mode, if you open it in Chrome, for instance, looks a little something like this. And we use it in CS50 when introducing students, as we did last week, to web programming because it, in effect, lets you start with a clean slate like a brand new browser that has never visited any websites before, which is good for just diagnosing problems. But it's often commonly used if you want to log into maybe your Gmail account on someone else's computer and you don't want your password being saved or you want to visit some website where you don't want the URL or the search terms ending up in your autocomplete history. So there's multiple uses for incognito mode. 

But what does it really do? Well, it doesn't stop your company, it doesn't stop your university, your internet service provider, be it, Comcast, Verizon, or the like from knowing what websites you go to because-- ask your students. A couple of weeks ago we talked about-- actually, a week ago, we talked about how the internet works. 

And unfortunately, every computer has an IP address, which is a unique identifier, which goes out any time you go anywhere incognito mode or not. So this isn't really covering your tracks outside of your office, or outside of your home, or outside of your company. But it is, at least, throwing away local information. 

And so we'll talk, in fact, in CS50's week nine this coming Monday about cookies, which you might generally know about and what are called sessions. And so long story short, what incognito mode does is it throws away, when you close the window, any locally stored information, so these things called cookies, which are sort of virtual hand stamps that just remember what you've logged in as or what's in your shopping cart or the like. 

But it doesn't hide any information from anyone outside of your own Mac or PC. It only prevents those local prying eyes. So there, too, even though we have tools that many of you are probably in the habit of using or thinking you should use to be more private, be more secure on the internet, what we do really in CS50, both weeks past and future, is talk about how these technologies work, so that ultimately, we have all the more of an educated citizenry here among undergrads and here as well as online, so that you can apply these same lessons learned to problems you'll encounter in the future. 

So as promised, the homework. One, you should probably use a password manager. It doesn't have to be one of those ones on the list, but at least starting that conversation maybe with someone who does, maybe the-- it's often the students in your family, perhaps, who can advise you on some of these technologies. Consider using a password manager too, using two-factor authentication, whether it's your phone or some key fob or the like, but at least seeking out that feature at least for accounts that you really care about, your email, social media, financial, medical, anything where you'd be embarrassed, at best, or really violated, at worst, if that kind of information got out and then increasingly using not just encryption, which you get automatically for most technologies today, but increasingly choosing technologies that offer stronger guarantees that keep those middlemen, those companies out of the way if only so that you can trust with higher probability that only party B knows what party A has said or sent. 

Now, this, of course, was a whirlwind tour. There's so much more that you can do online. Indeed, this course, CS50, can be taken for free online via platforms like edX at edx.org/cs50. 

I thought it might be appropriate to end on this note. If anyone would like to conjecture before we start playing music and adjourn for lunch, what our final message here is. If we reverse the plus one and maybe start minus one here, minus one here-- and indeed, thank you so much for coming. This was CS50. 

[MUSIC PLAYING] 
