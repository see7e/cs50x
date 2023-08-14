---
title: LECTURE10 - TRANSCRIPT
tags: programação, cs50
use: Transcript
languages: NULL
dependences: CS50
---

SPEAKER 1: Good afternoon. My name is Sarah. 

SPEAKER 2: And my name is Grant. 

SPEAKER 1: And we are The Harvard Crocodilians and the Radcliffe Pitches. 

SPEAKER 2: Now, Sarah and I understand that today is the final lecture of CS50. 

SPEAKER 1: It's been a tough semester. We made it through P sets 4, 5, and even finance. 

SPEAKER 2: Now, I know this is an unpopular opinion, but I particularly enjoyed finance. I spent a lot of time with my flask. 

SPEAKER 1: The P set? 

SPEAKER 2: There was a P set? 

SPEAKER 1: Well, at least things are looking up. Today is our last lecture. And look how far we've come. If I were an emoji right now, I'd be the face with tears of joy. 

SPEAKER 2: Sorry about that we're just trying to work some CS50 references into the intro. I mean, boy I sure hope this Tide man doesn't run off my Mario filter. 

SPEAKER 1: You could say that. For loop x equals open bracket 1 comma 2 close bracket. Boy, I sure wish we had Check 50 see if these jokes were funny when we wrote them. 

SPEAKER 2: Any who. We hope that you'll enjoy this brief serenade. 

[SCATTING] 

SPEAKER 1: (SINGING) Well, you lace up your boats and you walk on down to an knocked down shack edge of town. There's a landing [INAUDIBLE] that just won't quit. 

[INTERPOSING VOICES] 

SPEAKER 1: Well, there's fryers. 

SPEAKER 2: Broilers. 

SPEAKER 1: And [INAUDIBLE]. 

SPEAKER 2: Barbeque ribs. 

SPEAKER 1: But the trick of the train is what they're serving at those fine [INAUDIBLE]. You're going to spend the rest of your [? brights ?] down at the house of blue lights. 

[ALL SCATTING] 

Down at the house, the house of blue lights. Well, you lace up your boots and you walk on down to a knock down shack on the edge of town. There's a landing [INAUDIBLE] there that won't just quit. You walk until you see a blue light [INAUDIBLE] fall in there. Can you dig them sights down at the house, the house of blue lights? 

[ALL SCATTING] 

You lace up your boots and you walk on down to a knocked down shack on the edge of town. There's a lot of people coming there that just won't quit. You walk until you see a blue light [INAUDIBLE] fall in there. Can you dig them sights down at the house, the house of blue lights? 

[ALL SCATTING] 

ALL: (SINGING) Be sure to spend your brights down at the house of blue lights. 

[APPLAUSE] 

SPEAKER 3: Good afternoon, everyone. We are the Harvard Krokodiloes. And it is such an honor to be here with the Radcliffe Pitches performing for CS50's final lecture. Congratulations to everyone. And we hope you'll enjoy this our tribute to CS50. 

SPEAKER 1: 1 2, a, 1, 2, 3, 4. 

ALL: [VOCALIZING] 

SPEAKER 2: (SINGING) C is for the language I once knew. O is for O notation, I must do. D is for dynamic, flask run and finance it. E is even more than David Malan can adore. So code is all that I can give to you. 

ALL: (SINGING) He can give to you. 

SPEAKER 2: Code debugging it since, P set 2. 

ALL: (SINGING) Bugs in P set 2. 

SPEAKER 2: (SINGING) Soon deadlines, I'll make it. Hit Compile and please don't break it. Code was made by me for you. 

ALL: [VOCALIZING] (SINGING) C is for the language I once knew. O is for O notation I must do. D is for dynamic, flask run and finance it. E Is even more than David Malan can adore. So code is all that I can give to you. Code debugging, it says P set 2. Soon deadlines, I'll make it. Hit Compile, but please don't break it. Code was made by me for you. 

SPEAKER 2: (SINGING) C is for the language. 

SPEAKER 3: 0,1,0,0, 0.1,0, 0. 

SPEAKER 2: (SINGING) O is for O notation. 

SPEAKER 3: 0, 1, 0, 0, 1, 0 

SPEAKER 2: (SINGING) D is for dynamic. Flask run and finance it. E Is even more than David Malan can adore. So code is all that I can give to you. Code debugging it, sends P set 2. Soon deadlines, I'll make it. Hit Compile and please don't break it. Code was made by me for. Code was made by me for. Code was made by me for you. 

ALL: [VOCALIZING] 

SPEAKER 2: (SINGING) Code. 

DAVID J. MALAN: All right. 

[APPLAUSE] 

All Right. This is CS50. And CS50, this was the Harvard Krokodiloes and the Radcliffe Pitches. If one more time we can thank them for joining us today. 

[APPLAUSE] 

So this is already week 10, our last, and indeed among the goals for today are to hopefully give you all the more of appreciation of truly just how far you've come. Recall that in week 0, we began with this visual here whereby it was described this class as a bit of a fire hose, whereby drinking from that fire hose or really a fire hose from a water fountain is not unlike getting an education down the road too. 

And so this is to say, that if you're feeling like you didn't quite get it all down, like that's actually OK. And that's to be expected. And even if you felt that with each passing week, 0, 1, 2 all the way up now till 10, it never really ever got easier, perhaps just consider that what was once hard like Mario and getting "Hello, world" to compile is indeed the right measure of the delta between week 0 and now in week 10. 

In fact, you might recall that again in week 0, 2/3 of your classmates had never taken a CS course before. Now, of course, you all have. And indeed, if you think back to this final sentiment from week 0, that indeed "what ultimately matters in this course is not where you end up relative to your classmates, but where you end up relative to where you yourself began." 

So I would take some pride, take some satisfaction, take some relief, even though, a little bit more work does remain at really just how far you've come since that week 0. And recall that in week 0, we literally started with just 0s and 1s. 

And by now, many of you might have gleaned that these 64 0s and 1s have been spelling something week by week. In fact, today is our very last message here in binary encoded on stage. But then quickly, we introduced scratch and we started to assemble some building blocks of programming, loops, conditions, loops, conditions, functions and the like, but without all the distractions of semicolons and curly braces and all of that which admittedly we introduced the next week when we introduced you to C. 

But even now that we've transitioned to Python, hopefully even those kinds of curiosities or confusions are hopefully starting to just get more familiar. And so you finally start to see the missing semicolon as opposed to spending time on that kind of struggle. 

Recall too, that in week 2, we started talking already about memory and how you can manage things in arrays that later became, of course, in Python, lists. The week after we talked not only about debugging bugs in code but how to debug those same programs. 

Thereafter, we started talking about algorithms, and we took a step back from code and looked at the bubble sorts and the selection sorts and the merge sorts and all of the searches as well that go hand in hand with that. And indeed, this ultimately is what a lot of problem solving moving forward is going to be about, just solving problems with some form of algorithm. 

And you have so many different languages in your toolkit now with which to approach problems like those. We talked thereafter about pointers, which are not likely to come back in any modern languages that you now use but hopefully you have an all the better of a sense underneath the hood of like what's going on inside of the computer so that when you're designing something, you're using something, something crashes, you at least have a mental model for what's going on and it's no longer that week 0 Black box as it once was. 

I mean, you built things like this. Think back to week 5 when you built your own hash table. And those things are everywhere, key value pairs, whether it's in Python or in C or if it's now in CSS and JavaScript and even HTML, like that principle of key value pairs is really everywhere. 

And so, of course, now code doesn't necessarily have to look like this. It now wonderfully looks a little something more like this. But eventually, you're probably not, I'm not going to use Python anymore. Something new and better is going to come along. 

But odds are, like a lot of the building blocks from these past 11 weeks are still going to be useful for wrapping your mind around those new worlds. And indeed SQL, we introduced to you a little bit too. And even if you don't feel yourself yet an expert, hopefully you have a sense of what you can do with it and what problems you can solve. 

It's of course a better alternative to something simple like a spreadsheet. And now of course, web stuff is everywhere, whether it's on your laptop or desktop or even a lot of the mobile apps that you use on your phone, even though they're native applications, like you install them from Google Play or the Apple App Store. 

They're implemented increasingly with HTML, CSS, and JavaScript, but they're put in a little rectangular window so you don't even notice that that's actually really just an embedded browser. And then of course, you can build things, as you might for your final project, that too might very well be web based if you go that route. 

I mean, I'm still clinging to like the very first like web app I ever made years ago. But honestly, I do that in part because I was just so darn proud that like I taught myself how to do something and it actually worked and was used by other people. 

So whether it's just used by you or your classmates or your roommates or your family or your company down the line, there's a great sense of satisfaction that comes despite all of the pain that might be along the way when you just can't see or fix that bug. 

Now, of course we'll transition as you'll see in the coming days to empowering you to code client side as well. Up until now, you've been using our own VS Code installation in the cloud, which is nice because you've got up and running super fast in week 1, focusing only on code challenges not on technical difficulties. 

But among the goals now, if you so choose and want to program after this class, even if you never take another CS course before, you can use these same real world de facto standard tools on your own Mac or PC. And so pictured here is screenshot of like VS Code on the Mac. And even though, yes, you're going to have to jump through a couple of more hoops to just get Python or some other language working on your own Mac or PC, like that's what programming is ultimately going to be about. 

And we deliberately transition you to this at term's end so that now you have 11 weeks of more comfort under your belt with which to solve sort of silly technical support headaches that might have been deal breakers so many weeks ago. So there's still more to be done in the coming weeks. 

And indeed a support structure therefore, the CS50 hackathon, of course, will be this 7:00 PM till 7:00 AM opportunity to dive into your final project-- well, really continue diving into your final project ideally at that point alongside classmates, perhaps your project partners if you're working collaboratively. 

And awaiting you will be such memories and excitement hopefully as these, even as you then turn your attention back to your final project. There of course, will be several meals during the day culminating with 5:00 AM shuttles to IHOP, the local pancake place, if you are so awake at that point or even if you get there. 

This is not an uncommon sight as you might recall from week 0. And then lastly is the CS50 fair, which is finally back after a couple of years now of it not being on campus. And this will be an opportunity for everyone to present their final projects to passers by, classmates, faculty and staff and really just delight in what it is you created on your Mac, your PC, your phone, in the cloud or anywhere else. 

And indeed, it's just going to be an opportunity to bring your laptop to a shared space or your phone and introduce your project to passers by such as might appear and ultimately celebrate what you all accomplished. And indeed will you be handed at the CS50 fair, your very own I took CS50 t-shirt, which I daresay, I'm still wearing all of these years later. 

And so you too-- 

[APPLAUSE] 

--will have that ahead of you as well. So for what's on the agenda today, we thought we would not only look back but look forward. But first, we wanted to thank so many of the team members that have been helping both on stage and off who've made this course and these sections and so much more about CS50 possible. 

Of course, the building that we are now in, there's a whole team downstairs in Memorial Hall who helps us get set up and organized each day. Our thanks to them. There's the education support services team who makes everything look and sound so well down here, especially when we have all of them more microphones as well. 

Our friends, the Harvard Krokodiloes and the Radcliffe Pitches most recently and then of course CS50's own team, that [INAUDIBLE] CS50's own favorite restaurant, Chang Chau, down the road. Indeed if you find yourself in Cambridge for the next 1, 2, 3, 4 years or visiting from out of town, do pay a visit to our friends just down the road. 

And in fact, we'll have our very last CS50 lunch this Friday if you're able locally to partake. And then there are CS50's own team, both on stage and off. And my thanks, truly. Because not only do they make everything run so smoothly, they capture it for students here who might not be physically present here. For our friends down in New Haven at Yale and certainly for anyone online who might be tuning in as well. 

And then lastly, wanted to thank, of course, the huge team of your classmates, your peers that make CS50 possible in sections and office hours, tutorials, and more. Allow me to share with you the outtakes, so that even we, the teaching staff sometimes struggle with computer science, here are some of the clips that we captured when just passing packets via TCPIP a while back. 

You saw the finally-- the nicely polished version, but here are, if I may, if we could dim the lights, are some of the outtakes. 

[MUSIC PLAYING] 

Buffering. OK. Josh, nice. Helen, Oh. [CHUCKLES] Yet, Moni, No, oh, wait. That was amazing, Josh. But. Um, Sophie. 

Amazing. That was perfect. Moni. [CHUCKLES] I think I-- 

SPEAKER 4: Hey, un-mute. 

DAVID J. MALAN: Over to Yoel. 

SPEAKER 4: [INAUDIBLE] 

DAVID J. MALAN: Guy. That was amazing. Thank you all. 

SPEAKER 4: So good. 

DAVID J. MALAN: Indeed, in that moment, if we could, just one round of applause for everyone who's helped out this semester. 

[APPLAUSE] 

So back in week 0, we introduced you, of course, to this idea of computational thinking, which is to think a little more methodically, a little more algorithmically. And by way of these various languages, hopefully, that is something you notice, maybe not in the moment, but in the months and the years to come that you do find that your thoughts are indeed a little more cleaned up and you're just able to express yourself a little more precisely and even spot illogic in someone else's document or statements as well. 

But at the end of the day, really a course like this is also about critical thinking. And indeed, rewind again to week 0 when we frame the entirety of computer science as really just this, problem solving. And any problem in the world, be it CS or otherwise, has some input, and we decided how to represent those inputs. 

It needs some output, the solution there too. And then all of what you focused on doing and learning and applying these past several weeks is in that proverbial black box, which hopefully is not such an abstraction anymore but is indeed something that you know how to harness and know what could be going on underneath the hood, even if it's in some technology or some language that maybe we ourselves didn't cover, because a lot of those first principles remain the same. 

Now, along the way, we talked about the quality of solutions to those problems. We happen to focus on correctness, just does it work? Design, which is a bit more qualitative and subjective. And then style, the aesthetics of it all. And these two are characteristic, maybe not with these same words, of just how you might write or evaluate other creations in life, be it physical or written or the like. 

So think about too, as you solve problems, just how you can frame for yourself, like am I doing a good job or not by quantizing it, along these or perhaps other axises as well. And we thought we'd highlight just two topics from that week 0 that have really been manifest for the past several weeks, namely abstraction, like taking complicated things and ideas and trying to simplify them so that we can operate at this level and solve problems we care about without getting into the weeds of implementation details so to speak. 

But there's this tension because, you know now, from all of these different languages, that code is fairly unforgiving. I mean, even omitting a stupid semicolon sometimes breaks everything. And so precision is sort of at odds sometimes with this idea of leveraging abstraction. 

And so we thought we would try to tease this apart, especially all these weeks later here, but with a bit of a live demonstration. So on the way in, you probably all received a sheet of paper. If not, but someone near you did just tear theirs in half and borrow half a sheet if you can or any piece of loose leaf paper or the like will suffice as long as you have a pen or pencil. 

And for this, allow me to propose that we invite up maybe two final CS50 volunteers this semester, and like a lot of hands are going up in this. A lot of hands. How about, I saw the first hand there. Yes, who's pointing at herself now. Come on down. 

We just need the one hand for now but, oh, wait. You'll be our number two. Well, OK, we have way too many volunteers now. No, no please. Please come down. Yes, in the black shirt. And if you guys, we will, we'll do pair programming in just a bit. 

If you want to hang out in the wings here, we'll have our second demonstration as well. So OK, now maybe round of applause for our three volunteers. 

[APPLAUSE] 

Oh. Come on up, first. Oh, no. Second and third. OK, you come first. We'll do it order No. This is a queue. Queue here. What's your name? 

DANI: I'm Dani. 

DAVID J. MALAN: Dani. OK, take this mic. OK, so we will de-queue you momentarily. All right, so Dani, come on over to the middle here. And in a moment, I'm going to hand to Dani a sheet of paper that has a picture on it. And this picture is going to be something that I'd like you to verbally program the audience to draw. 

You can use any words, any abstractions, any level of precision that you want, but you just can't make hand gestures or sort of show them what to draw. But first, you want to tell us a little something about yourself, including everyone here. 

DANI: I'm Dani, and I took CS50. 

DAVID J. MALAN: OK. Wonderful. Wonderful. So I'm going to reveal the picture only to Dani. And if each of you would like to take out that sheet of paper and just make sure that no one else can see this, if you want to hold it up this way. 

Everyone here is now holding their pen or pencil, and in some number of steps, give them a verbal algorithm for drawing what you see. And you can say anything you want, but no hand gestures. 

DANI: OK, so you're going to want to draw a square in the center of the paper with the diagonal pointing to the center of the edge. Wait. No actually, scratch that. Draw a rhombus in the center of your paper. 

DAVID J. MALAN: And for those who forget what a rhombus is? 

DANI: A diamond. A square that's on its side. And then from the bottom vertex, draw a straight line down, but not all the way to the edge of the paper. OK. And then keep your pencil or pen at that point, and you're going to want to draw a line that's parallel to the line of the original rhombus to the right. 

And then keep your pencil or pen at that point, and draw a line straight up, connecting to the side vertex. Yes. And then go back to the line that you drew from the bottom vertex to the bottom of the paper, and then draw a line parallel to the left edge of the rhombus. 

And then keep your pencil at that point and draw a line up to the vertex of the rhombus again. 

DAVID J. MALAN: The end. 

DANI: The end. 

DAVID J. MALAN: All right. Well, thank you to Dani. Hang on to your paper. Thank you so much. And if you want to step off to the stage there, we will reveal. Thank you. A round of applause if we could for Dani. 

[APPLAUSE] 

That is not an easy task, I'm sure. And if Carter wouldn't mind just grabbing a few samples here, let's actually take a look on the overhead if we could. I'm going to pop down over here real fast. We don't need to collect them all, but if you're feeling either good or bad with what you drew, happy to collect a few of them. 

OK. Thank you. Thank you. I hope you won't mind if I can't reach everyone. Just a couple more, over here. OK. All right, that's-- OK. 

AUDIENCE: This one's really [INAUDIBLE] 

DAVID J. MALAN: This one's really funny. I'm going to go with this one if I may. And Carter has some too. Thank you so much. OK. So just a random assortment here. Let me turn on a camera so I can show you what I see. 

Here, for instance, is one classmate's drawing which might resemble perhaps what you Drew here. Here is the beginnings of a house, it seems. Nice. This one, this one is larger. And how about a couple of others that were getting closer, I think. So more edges and vertices there. 

This one seems a little similar in spirit, if not proportional. This is Zac's the best one. But it turns out if I may, Zac, you're not all that far off. Here, Dani, is what you were reciting to everyone algorithmically. Indeed, it was this here cube. 

And so Dani, can you come on back up for a moment. So if you'd like to share for just a moment like what were some of the thoughts going through your head and why did you choose the words that you did? 

DANI: OK. So what was going through my head when I saw the cube. I didn't know if I could say, draw a cube. So I decided to start with the top and so draw a rhombus in the center of your paper, and then draw a line down and just do the first part. 

Then the second part, then the third part. And then you would get a cube like Zac. 

DAVID J. MALAN: Yeah, and so had you said, and you could have said, draw a cube, which would be more of an abstraction. Even that's not necessarily sufficiently precise, right, because you don't necessarily know what the orientation of that cube is, the size of it, the positioning on the paper. 

So you instead took a lower level approach, which is not unlike Scratch. If you think about Scratch, being able to move up, down, left, right, turn 90 degrees, turn 15 degrees and the like. I mean, that is ultimately how a lot of graphical programs and games even might be implemented by really focusing at the level you do. 

But of course, there's this tension with us humans whereby we prefer often to think at this level, but even that might not be sufficient. Which is to say, here in week 10, these are still going to be in our hard problems, but a hand, if we could, one more time for Dani for getting us that far along. Thank you so much. Let me give you a stress ball here. 

[APPLAUSE] 

All right. And if we could have both of our volunteers come up here. We're going to have-- yes, come on up. Come on up. And let me have you guys introduce yourselves in the middle here. 

EVAN: Hi, I'm Evan. 

SADDIQ: Hi there. I'm Saddiq from Turkey. Nice to meet you all. 

DAVID J. MALAN: Wonderful. Welcome. And this time we're going to flip it around so as to have the audience do what Dani just did for us. The only catch here is that the only means we have for showing the audience what they need to tell you to draw is like literally right above the chalkboard. 

So on our system here, that your eyes must stay on the chalkboard and not look up. And in just a moment, if you guys want to both stand in front of the chalkboard, back to the audience. And as you're talking with each other, verbalize it through the microphone if you will. 

I'm going to show everyone else in the room a second and final drawing, and we'll just go rapid fire around the room, give us one step at a time collectively, and we'll see if these guys can't draw exactly that same outcome. 

AUDIENCE: Is there another chalk? 

DAVID J. MALAN: What's that? 

SADDIQ: Is there another chalk? 

DAVID J. MALAN: Just the one, so you'll have to collaborate and let's give you a clean slate here, literally. All right. So no looking up. That's the only rule for you guys. Here we go. For the audience, here is what we'd like them, ironically, to draw. Step one, from anyone in the audience? Yes. 

AUDIENCE: Draw a circle. 

DAVID J. MALAN: Draw a circle. Anywhere. 

AUDIENCE: Not anywhere. 

[INTERPOSING VOICES] 

DAVID J. MALAN: OK. That's step one. Step two. Someone else? Yeah, in the middle. 

AUDIENCE: Draw a line down from the bottom of the stairs, about halfway down to the-- half way down. 

DAVID J. MALAN: Draw a line down from the bottom of the circle about halfway down. I think there was a hand in front of you too. Number three? 

AUDIENCE: From the point on the bottom, draw a diagonal line to the left. OK. [INAUDIBLE] 

[LAUGHTER] 

DAVID J. MALAN: OK. 

AUDIENCE: The overarching goal here is you're trying to draw a person. 

DAVID J. MALAN: The overarching goal here, for those unable to hear, is to draw a person. 

EVAN: Oh, it's a stick figure. 

SADDIQ: OK. It may be a stick figure. 

AUDIENCE: Draw the left leg of the person. 

DAVID J. MALAN: Draw the left leg of the person, of this person. OK. Good job. All right. OK. Next, step four. Yeah? 

AUDIENCE: Go to the vertice of the line going up and the circle and to the left, I'm sorry, to the right, draw a V. 

DAVID J. MALAN: To the right of the vertex at the bottom of the circle, draw a V. 

AUDIENCE: Yeah, draw a V. 

SADDIQ: A V. 

EVAN: Like what V? 

DAVID J. MALAN: Nope, not interactive. Draw a V. 

EVAN: Well-- Yeah, it seems really weird. 

DAVID J. MALAN: Get ready for-- 

EVAN: Maybe something like this? 

DAVID J. MALAN: Step five. OK, we'll go with that. Step five. Someone else? Step five, someone else? Someone else? Yeah? 

AUDIENCE: Draw the right side of the leg. 

DAVID J. MALAN: Draw the right side of the leg. Nice. Step six. Step six. 

SADDIQ: Happy face? 

DAVID J. MALAN: Six. Six. Yes? 

AUDIENCE: Erase the line you have on the left. 

DAVID J. MALAN: Erase the line that you have on the left. 

AUDIENCE: On the left. 

DAVID J. MALAN: Step seven. Yes? 

AUDIENCE: Instead of that line that was before going up, make it go down. 

DAVID J. MALAN: Instead of that line before going up, make it go down. Step eight. Step eight? Step eight? Yes? 

AUDIENCE: Connect that line to the hip. 

DAVID J. MALAN: Connect that line to the hip, 

AUDIENCE: Not like, not touching. 

DAVID J. MALAN: Not touching. 

EVAN: Something like this, maybe? 

DAVID J. MALAN: Compromise. 

EVAN: Not touching. 

SADDIQ: Not touching. 

DAVID J. MALAN: OK. All right. Step nine. Almost there, I think. Step nine? Step nine? Step nine? Yes, in back. 

AUDIENCE: [INAUDIBLE] write the word "hi" on the top left of the circle. 

DAVID J. MALAN: Right the word "hi" on the top left of the circle. 

EVAN: Put this right here. 

DAVID J. MALAN: OK. And step 10. Almost there. 

AUDIENCE: Draw a line pointing to "hi". 

DAVID J. MALAN: Draw a line pointing to "hi". 

EVAN: This is like a speech bubble, basically. 

DAVID J. MALAN: And step 10, 11? Yeah? 

AUDIENCE: Erase the exclamation point. 

DAVID J. MALAN: Erase the exclamation point. Nice. 12. Do we want to give them one more? 12? Or are we good? Yeah, last one. 

AUDIENCE: Erase the right arm. 

DAVID J. MALAN: Erase the right arm. I think we're going to need a 13 then. And then? Yeah? 

AUDIENCE: Repeat the left arm, but rotate it 90 degrees. 

DAVID J. MALAN: Repeat the left arm, but rotate it by 90 degrees. 

SADDIQ: That feels wrong. How would you like-- as an organic human being, how would you use your arms? 

DAVID J. MALAN: No. No. No. 

AUDIENCE: [INAUDIBLE] 

SADDIQ: Would you ever stretch your arm like that? 

DAVID J. MALAN: That would not be a stick figure. 

SADDIQ: Would you do this or would you do that? 

DAVID J. MALAN: All right, little hint, maybe. Give me a step 14. Step 14 and final? Step 14? I think we just got to tell him what to do. Step 14? Yes? 

AUDIENCE: Think of a walking man. The right hand [INAUDIBLE] normal [INAUDIBLE], but just rotate the edge of it a little to a left. 

DAVID J. MALAN: Think of a walking man, and have the left, the right hand walking to your right. 

SADDIQ: It's like-- 

DAVID J. MALAN: Where could the hand go? Where should the hand go on that arm? But Yeah. OK. Yes. No. I mean, look right here. Look right here. Look right. Yes, sorry. Thank you. 14 is done. 

[APPLAUSE] 

That's pretty close, so congratulations to you guys. And thank you as well. All right, so I mean, these things too are not-- yes, round of applause then, sure. 

[APPLAUSE] 

So this is to say these ideas of abstraction and precision and really every other term of art that we explored this term are sort of omnipresent and can be easier or harder to implement depending on exactly what the problem is. But what we thought we'd do now in our final day is try to now similarly prepare you for life after CS50. 

And this is really going to be a list of really potential to-do, so that you can stand on your own after the class, after the classes' infrastructure, write actual code. And then we'll come full circle one final time with our friend Jennifer 8 Lee to look at the world of emojis and how they relate to all forms of representation that we've talked about up until now. 

So one, how can you go about programming after CS50? So one, you can actually install command line tools on your own Mac or PC. Perhaps unbeknownst to you, Windows has what's generally called a command prompt. Mac OS literally comes with a terminal program in your applications utilities folder. 

And so even if you've never run those programs, you've actually had a sort of blinking cursor, black and white prompt available to you. Might not have all of the same software installed as your code space in the cloud, but you have that command line interface even within today's graphical tools. 

And among the tools you can install within that command line interface would be something called Xcode on the Mac which comes not only with a GUI IDE, integrated development environment, but also those command line tools and Microsoft for Windows has something similar as well. 

Learning Git, so we've used Git, only unbeknownst to you underneath the hood for the most part. But Git is a very, very popular tool, if challenging to pick up for the first time, that makes it easy to push code to a website called GitHub or any equivalent and then collaborate more effectively with classmates. 

There's definitely a bit of a learning curve, but thanks to CS50's own Brian Yu, you can start, for instance with a video like this. And this indeed is going to be one of these de facto standards in the real world, at least for the next several years that you'll probably encounter if you work in tech or really any company where you're doing some programming. 

VS code itself, we'll walk you through this process in the coming days, but you can indeed install it on your own Mac or PC. And what can you do when you write code? Well, you can certainly write software for your Mac, for your PC, for your phone, or of course per week 9, you can host your own website be it static as in week 8, hosting it at websites like these, which generally have free or student-friendly accounts via which you can put something statically on the web at a real domain name that you might choose. 

Or you can host a full fledged web app, and using student tiers on Amazon and Microsoft and Google's Cloud Services or others, you can sign up for, being a student certainly, a whole lot of free software, free hosting so as to if nothing else experiment and perhaps maximally get your own app or website up and running. So know that those are resources available to you. 

And this is by certainly a non-exhaustive list. If you'd like to geek out in the coming months, in the coming years, these are just some of the places that people who take computer science classes, who write code, might tend to hang out and ask and answer questions of each other. So keep an eye for instance on these here. 

And then CS50 has its own communities as you'll see. If you go to this URL here via the OpenCourseWare version of CS50 which is open to the world, there a vibrant community, thanks to time zones, that's pretty much active 24/7, 365. Talking about not only CS50 goings on and problem sets and projects, but really technology more generally, as well. 

So certainly feel welcome to partake, either asking or answering questions. Now, speaking of asking and answering questions, a couple of weeks ago, you kindly gave us a whole bunch of review questions which we culled through and picked out our favorite 20 of them. These, of course, were multiple choice questions. 

And in preparation for this week, in preparation for life ahead, we thought we would choreograph a bit of a quiz show here. And indeed, as you came in at the start of class, you might recall being invited to go to this URL here, CS50/ly, either here in person or if you're watching live from home at this URL here. You can use a phone or a laptop. 

And if it's easier on the phone, you can point your camera at this 2D barcode here, we'll give folks a moment to pull that up. And again that, URL was CS50.ly/poll, and once it looks like most folks have it up and running, our friend Carter here will help us dive into this review session, if you will, with a bit of fun along the way. 

All right, Carter, if you'd like to take it away. What do we have as our first question? You should see on your phone or laptop, this same question being asked. The first question is, "How do you print quote, unquote "hello, world" in Python?" So among the possible answers are these here. 

Buzz in on your phone or your laptop. We've got a few hundred responses already. Seven seconds to make your decision. This is question 1 of 20, going into it with some confidence. I think we're down to 0 on the clock and Carter it looks like 98% of you indeed said, "hello, world." And Carter, per the check mark, that's indeed the correct answer here. 

Now, to make things interesting, know that you'll see some number of points. And we've deliberately anonymized it so only what number you are. So a whole lot of guests have a perfect score of 1,000 at the moment. Hopefully we'll see over the next several questions, things start to bridge out. 

But know that the speed with which you buzz in will also factor into how many points you now get. So the faster you move, the more points you get. Question 2, if we could, "What does DNS stand for?" from just a couple of weeks back. "Domain Number System. Domain Name System. Data Numbering Structure" and "There's no such thing as DNS." 

Few hundred responses are in, 8 seconds remain. Fewer points now, but still a chance to buzz in. And now as we hit zero, the responses are these, "Domain Name System" which is indeed correct, and 84% of you got that one correctly, and indeed exists, we talked about it a couple of weeks ago. 

So we're still seeing a whole lot of ties at 2,000. We'll see if someone starts to pull away before long. Question three, "What is the upper bound of Merge Sort's run time?" So that escalated quickly. "Big O of n log n. Big O of log n. Omega of log n." or "Big O of 1." "What is the upper bound of Merge Sort's runtime?" 

That was the last of the algorithms we saw for sorting, and in one second, we'll see that the correct answer is just edging out everyone else, indeed, 46% it is, n-- I know. It's n log n. Now, if I may, as the teacher, it can't be log n, because log n is strictly less than n. And you can't possibly sort n elements unless you minimally look at or touch each of them. So it's got to be at least greater than n intuitively. 

We still have a whole bunch of ties. Let's move on to number 4. "What is stored in argc?" Back to the language, C. Is it "An array of arguments. The maximum size of an array. The count of arguments given to a program when first run." or "how much memory is allocated to a function?" 

Again, you wrote all of these questions. And we have 5 seconds, for the reveal. Argc is indeed "The count of arguments given to a program when first run." Think back to C when we did command line arguments, there was argc and argv. Argv was the array, but argc was indeed the count. The a and argc. 

All right, we still have a whole bunch of ties at the top here, but let's move on then to number 5. "What is the duck debugger's favorite hobby?" According to one of your classmates, "Dressing up like Dracula. Swimming across the stage. Filling up the entire bathroom of a guy's house. Sitting quietly on stage." 

The third of course, is a reference to a YouTube video that was on the course's website that week. But according to your classmates, number 2, seconds remaining, sitting quietly on stage is its favorite pastime. So a little harder perhaps than the others. 

5,000, now we're starting to see some spread. So we only have six guests in contention for first place. And the next question now is 6, "What is the function used to open a file in C?" "fopen. open. fileopen. file." "What is the function used to open a file in C?" 

7 seconds. There's some differences between C and Python here, and the reveal, it is indeed fopen at 77% correct too. All right, let's see the rankings now. If you are Guest1590, 715, 6171, 3753 or 3273, you're now in the lead as we move on to question 7. 

"How does strlen compute the avg-- sorry, how does strlen compute the length of a string in C?" "It looks at how much memory the string uses. It counts the number of characters until it reaches backslash zero. It counts the number of bits in the string. It creates pointers for each character and counts them." 

10 seconds, strlen in C. Recall that we implemented this ourselves in class, but then we use the library thereafter. And indeed, with 85%, it simply counts the number of characters until it reaches that sentinel, backslash zero, a.k.a. Null. And in this case, we have 544 of you tied now for first. 

All right, question 8, "Where does malloc allocate memory from?" The "Stack." The "Heap" The "Pointers" or the "Temp" "Where does malloc allocate memory from?" Responses are coming in, 8 seconds. A good review question at that. In 2 seconds we'll see that malloc allocates memory from, close one, the Heap is correct. The Heap is correct. 

The stack recall is where functions store their local variables and their arguments and that just happens automatically. The Heap represented in our pictures up top is where malloc draws from. Now we have guest 15 has made its way to the top here, but others can catch up if they don't buzz in fast enough. 

So number 9, "How many people flew from Fiftyville to New York on the day of the crime?" "16. 29. 8." or "3." Anyone with a laptop perhaps has an advantage here. 5 seconds, and the answers are-- but the answer is 16. 

Let's see if Guest15 got this. They did not. Goodbye to Guest15 at the top. All right, question 10. We're about halfway there. "What are meta tags used for in HTML? " "To describe a web page. To define parameters for an element. To group elements together. To translate content into machine-readable format." "What are meta tags used for in HTML?" 

We saw a few of them for different use cases. And with 1 second, we see that indeed the number one answer was to describe the webpage, be it for a mobile device, be it for screen scrapers like Facebook and Twitter and other such apps that grab images and descriptions thereof. 

All right. We're in the second half now, Guest4669 edged ahead. Guest15 is now in sixth place. All right. Number 11 is "How do you find the address of a variable in C?" Think back a few weeks. Star, dollar sign, ampersand Ask. 

From one of your own classmates, "How do you find the address of a variable in C?" And the number one answer is ampersand which is indeed the address of operator at 62%. Nicely done. Let's see who's the top of the list now. 

Guest4669 has retained their lead, so we move on to 12. "What does the arrow operator mean in C?" A hyphen and a greater than sign. "Nothing. Starts a comment. Replaces a star in dot operator. Declares a pointer." "What does this arrow operator mean in C?" 

Again from a few weeks back. 3 seconds, harder assortment perhaps. And it's oh, "Replaces a star in dot operator." The number two answer was indeed correct. This was just a cleaner way, syntactic sugar for collapsing what would be a star and then some parentheses and then a dot into quite simply something that looks like an arrow itself. 

All right, Carter, who's in the lead now? Still that same guest, and let's see what 13 has for us. "Which of these is not a data type in SQLite?" "BLOB. STRING, INTEGER. TEXT." We used a few of these more commonly than others but not all of these are for real. 5 seconds to make your decision. 

And the results are BLOG is a thing, STRING is not in SQLite. It's of course called TEXT, as we've seen it. BLOB, as goofy as it sounds, is just binary large object. But indeed, it's how you might store a binary file in your database. All right. 

The rankings now, oh, Guest8444 has eked ahead. So we move on to 14. "Which of the following is a valid way to print exclamation, point exclamation, point exclamation point, exclamation point, in Python?" And I'll let you read these yourselves. Which is a valid way? 

OK, everyone got quiet and is thinking. All right. 6 seconds, a few hundred responses in so far. All right, and yes, nicely done. 78% is correct. You can use the star operator to essentially multiply the character at left. 

All right, who's in the lead, Carter? We now have still Guest8444. And so we move on now to 15. "What does the free function do?" Deallocated memory from a primitive. Deallocated memory at the given pointer. Terminates a loop." or "Returns a value from the function." "What does the free function do?" 

All right, 5 seconds. "What does the free function do?" Call to the opposite essentially of malloc. And it "Deallocates the memory at the given pointer." as well. And in C, that's on you. In Python, you don't need to worry about allocating or freeing alike. 

All right. We now have at the top, still Guest8444 and seeing more and more spread. 16, "Which is not a step of compiling? Think back now to week 2. "Compiling. Preprocessing. Linking." or "Threading." "Which is not a step of compiling?" 

We use it as a catchall, but it technically means a few different things collectively. All right. And threading is indeed not on the list. That is a technical thing, generally meaning a program can do multiple things at once, but that is not related here to compiling. 

All right Guest8444 still at the top. We have just a few questions left. And so, 17 "What was the surprise at the beginning of the Halloween lecture?" According to your classmates, someone scared me, "Someone hid candy under every chair." Someone dressed up as me. "The entire staff dressed up as Carter." 

Oh, interesting litmus test of who came to or watched lecture perhaps. Let's see which guests got this correct. Someones really dressed up as indeed me at 64%. So I think we have attendance here essentially from that lecture. 

So let's move on now to the final few questions after seeing that Guest8444 is still doing well. Can anyone dethrone them? "Why is it incorrect to use the equals equals operator in C to compare strings?" "It is computationally inefficient. You're comparing the locations of the strings. Strings don't exist. Using equal equals will lead to buffer overflow." 

"Why is it incorrect to use equal equals in C to compare strings?" 3 seconds. We saw this live, and it motivated like an entire week because you're comparing the locations, that is the addresses in memory of those same strings. 

All right. Let's see if this leaves the rankings the same. Guest8444 is still at the top and pulling ahead. Two final questions, 19. "What is the difference between NUL" one L, "and NULL." Two Ls. NUL and NULL mean the same thing. NUL refers to backslash 0, whereas NULL" 2 L's "is the 0 address. NUL is the zero address whereas NULL" two L's "refers to backslash zero. NUL is NULL but lazier." 

5 seconds. Subtle. Not the best design perhaps to have in technical terms, but indeed 62% of you got that and N-U-L is the first thing we talked about when we talked about backslash zero, and N-U-L-L is a pointer. It's the zero pointer. Same number, but different context. 

All right, Carter. Guest8444 is the person to beat with our final 20th questions. "What do the binary bulbs on stage spell today?" And these are your four choices, different from usual. We usually use 8-bit Ascii. Today we are using UTF8 which is a form of Unicode, which is the larger subset that uses 1, or 2, or 3, or even 4 bytes to spell a single character. 

And the answer, wow, close, is indeed a cupcake. Indeed, a cupcake. Well done. And let's see the final results. 8444 is the winner. Are they here in person, perhaps? 8444. You're 8444. Come on down. 

[APPLAUSE] 

Thank you. There you go. Congratulations. 

GUEST8444: Thank you. 

DAVID J. MALAN: Thank you. All your. All right. Today if we may, give me just one moment. All right. All right. So today we are so pleased to be joined by Jennifer 8 Lee who's an alumna of the college, a dear friend, and is actually really the reason why there's evidence of Muppets in CS50. 

In fact, some years ago, I was visiting her and she had on her shelf like this custom Muppet. It wasn't one that appears on TV, but she had somehow gone on a website, a former toy store called FAO Schwartz at the time, and you're allowed to configure your own Muppet whatnot. Choose the eyes, the nose, the face and the torso. 

And I just thought this was the coolest thing. And so in the taxi on the way home, I was like going on the website trying to purchase our very first Muppet. I then sort of woke up the next morning thinking, why did I just buy a puppet in the back of a taxi? And so it sat on the shelf for really two years. 

And then a colleague of mine within CS50's team decided, after I brought it into the office to sit on a shelf there, to actually bring it to life. And indeed if you Google around and CS50 Muppetry and puppetry online, you'll see in fact these as characters, not only over the past couple of years in COVID times, when really there was next to no one actually here, and so they were instead. 

But indeed she's brought not only this educational element, this pedagogical element, this playful element to CS50. And we have her here today to speak to exactly the sorts of encodings that are here on stage. 

Jenny is the former Vice Chair of the Unicode subcommittee on emoji, which is to say that she and her colleagues have been influential in taking emoji from what was a very limited character set early on and by far unrepresentative of much human emotion in speech into really an initiative now to capture digitally all of the world's languages, past, present and future, as well as the range of emotions that we might see here in the form of that pillow or even in the cake that await. So allow me to introduce, Jennifer 8 Lee. 

JENNIFER 8. LEE: Thank you. I much drink. Clicker. Hi. All right. Hold on. I have to hide my drinks. I might need more water. All right. I'm really excited to speak. So speak your last time. Last year I was here. One, I was wearing a mask, which is like a real bummer if you're lecturing. And then the entire front part was all Muppets. So I'm really happy to see humans actually. And it's always an honor to speak at Sanders. 

And then Dave and I were actually classmates way back when. So I do remember him when he was an undergrad much like you. So I am going to give a talk on the world of emoji and how I kind of became an emoji activist. So it kind of all starts with my friend, Yiying Lu, who is a designer who's well known for doing the Twitter fail whale, which was kind of laid to rest. Except now, this week it seems like it may be necessary again. 

So she and I one day were texting. This is back in 2015. We're texting about dumplings because we are Chinese-ish women and we like to text about food. And so I sent her this picture of dumplings. She was like yum, yum, yum, yum, yum, yum, yum, yum. 

And then she was like, oh, Apple doesn't have a dumpling emoji. And I was like, well, that's kind of interesting. I didn't really think anything about it because people point things out to you all the time, and then you just like forget, and you just like move on. 

But then half an hour later, on my phone appears this dumpling with heart eyes. And you don't see it because this is a still shot, but it actually had blinking eyes. So she liked to call it like bling, bling, dumpling. So she as a designer had decided to go in and make her own dumpling emoji because she was like, I'm a designer, I can fix it. 

But that actually got me thinking. I was like, where do emoji come from? And how is there not a dumpling emoji. Because from my perspective, dumplings are this kind of universal food. Right. So and there are a lot of Japanese foods on the emoji keyboard. And I was not, this was like back in 2015. I was like not a big emoji user like at all. 

So I mean, you have things like ramen. You have Bento boxes. You have curry. You have tempura. You even have kind of obscure kind of foods like this thing, things on a stick, turns out to be fish things on a stick. Then this pink and white swirly thing is also a fish thing. And there's even like that triangle rice ball that looks like it's had a bikini wax, all well represented on the emoji keyboard, but no dumplings. 

And it's very strange, because like all cultures kind of have their dumpling, whether or not it's khinkali or ravioli or empanadas, like essentially everyone sort of like discovered the idea of yummy goodness inside a carbohydrate shell, whether or not baked or fried or steamed. 

So I was like, OK, I literally Google was like who controls emoji. And you discover that they're actually regulated by a nonprofit called the Unicode Consortium. And it is, and I just went on their website and I discovered that they had 12 full voting members as of 2015. 

So this is 2015, and they were like mostly US multinational tech companies. It was Oracle. It was IBM, Microsoft, Adobe, Google, Apple, Facebook, and Yahoo. And of the three that were not multinational US tech companies, there were, let's see a German company called SAP. A Chinese telecom company called Huawei, and then like the government of Oman. 

Those were basically the 12 full voting members of the US multinational tech companies. So they at that point paid $18,000 a year to have full voting power on the Unicode committee. And I was like, oh, that's a lot of money. And I kind of felt indignant about this. 

But then if you kind of keep on digging on their website, you found there was this kind of interesting loophole, which is could join as an individual for $75. You don't get voting power, but it gave you the right to put yourself on the email list and also to attend the quarterly Unicode meeting. So I was like, I'll do that. 

I had no idea what I was doing. But I'm like, I'm going to go fight for this dumpling emoji, because from my perspective, dumplings are universal. Emoji are kind of universal. So the fact that there was no dumpling emoji meant like something was wrong in the universe and I was determined to fix this. 

You know I was on this email list. And then a couple of maybe, even like a couple of weeks later, I got-- they kind of sent out this note that's like, hey, who's coming to the quarterly meeting. And I was like, I looked at the calendar. I looked at my schedule. I was like, oh, I'll be in Silicon Valley at that time. So I basically like RSVP and I was like, I will be there and took Caltrain to an Apple building. 

It's a legal building in I think it was Sunnyvale. So I just like show up. And I don't know what I was sort of expecting like with like the Unicode. I think I maybe that was going to be like a baby Congress, like with a little very formal seats, people with gavels. That is not what I found. 

Basically it is, it was a conference room full of people who skewed wider, skewed older, skewed male, skewed engineers. And this is basically the room where it happens. So this is 2015. These were the people who decided your emoji, all very nice and. 

There was one, even had a daughter who had a sense of humor and made him a shirt that said "Shadowy Emoji Overlord." So I just kind of listened to them debate things like milk emoji and beans emoji. And it just seemed like not quite right to me that it would be this global visual language that were basically decided by like a small group of people inside a conference room in Silicon Valley. 

So I decided to form a group called Emojination, whose motto is like "Emoji by the People, for the People." And it basically advocates for more kind of representative inclusive emoji. We start with a Kickstarter campaign, dumpling emoji process trying to right the wrong in this world and made this little cute video sort of advocating-- 

NARRATOR: Dumpling are one of the most universal, cross-cultural foods in the world. Georgia has khinkali Japan has gyoza, Korea has mandu, Italy has ravioli, Poland has pierogi, Russia has pelmani, Argentina has empanadas, Jewish people have kreplach, China has potstickers, Nepal and Tibet have momos. 

Yet somehow, despite their popularity, there is no dumpling emoji in the standard set. Why is that? Emoji exist for pizza, tempura, sushi, spaghetti, hot dog and now tacos, which Taco Bell takes credit for. We need to right this disparity. Dumplings are global. Emoji are global. Isn't it time we brought them together? Oh, yeah, while we're at it, how about an emoji for Chinese takeout? 

JENNIFER 8. LEE: So I did put together a dumpling emoji proposal. I wrote this, I remember Thanksgiving Day 2015 on a plane. And actually, and we got it passed, basically dumpling, takeout box, chopsticks and fortune cookie. 

I have to say, I don't think fortune cookie would have made it on its own merits, but it kind of like slid in on the coattails of the other ones. And so these were the proposals as we submitted them. And then these are the ones that kind of exist now on the Apple keyboard. And I have to say, the dumpling looks really, really realistic, oddly realistic. 

And whereas, like the fortune cookie I think is like a big fail, because first of all, there's like, it has no-- it has no gap. It looks like a dead 3D Pac-Man. So I'm very disappointed in the manifestation of that. But that's OK. That's OK. 

And so it's kind of interesting, like what is the process of getting an emoji passed? And I will walk you through it. So first of all, you come up with your idea. And then you write this proposal and then you submit it to the Unicode emoji subcommittee who then gives you comments and then sends it back to you. And you kind go around and around the circle. 

So these are things that we consider. So somewhere in there, I also fought my way onto the emoji committee and then also became a Vice Chair, became a Vice Chair. Sort of an extracurricular just like completely run amok in my life. 

So things that matter popular demand, is it a frequently requested emoji. Multiple usages and meanings, so that's actually kind of very important for something like certain animals have meaning. So we did sloth a while ago, and that also has not only the literal meaning but sort of like connotations. 

There are visually distinctiveness, it can be recognized. So this was a blocker for one of the emoji that I have worked on before which is cave, which is kind of hard to do. I think, meaning wise, is pretty good, but it's really hard to get a cave down in emoji sizes. And then it filling a gap, completeness. 

So a good example for that is like for some reason, for many years, we had red heart, yellow heart, green heart, blue heart, purple heart, and no orange heart. So somewhat, so you would do the rainbow, but people would substitute the pumpkin in. So you would like have a rainbow heart thing with a little pumpkin stuck in the middle. So orange heart obviously should be added and give a sense of completeness. 

And then something else is existing vendor compatibility. And so a good example for that was many years ago WhatsApp decided to add the gender non-binary emoji. And then once it did that, then all of the other kind of vendors jumped on. 

So what kind of knocks out an emoji. So too specific or narrow. So we'll often see that with very specific animals or a very specific group. It's redundant so one year, oh my God, who makes a Butterball? Butterball makes the turkeys. Butterball submitted an emoji proposal that was like a cooked turkey. But we already had a live turkey so it seemed kind of redundant to have both, like a cooked turkey for Thanksgiving and a live turkey. 

So not visually discernible. This is a struggle for things like, I know my friends have kind of proposed kimchi. Kimchi is really hard on emoji sizes for many reasons and part of that tension is because it's not visually discernible. 

Then there are no logos brands, deities, or celebrities. So no Nike swoosh, no McDonald's M. And then this is one that we decide in the last year or so which is no more flags. Flags are a very complicated thing. And as a result Unicode does not want to be in a business of deciding what is a country or not a country. 

So like when you get a proposal from like Kurdistan, you're like-- so right now, the way that the emoji flags are decided is they kind of depend on what the UN recognizes and then those get passed down to the International Standards Organization and then Unicode just does that. It does not want to be in the business of the geopolitical affairs. 

So once it comes out of the subcommittee, it goes to the full Unicode Technical Committee, UTC. Those were the people that were in the room that I showed you. And they vote once a year basically to pass all the emoji. And it takes a while. There's a lot of coordinating with the International Standards Organization and a lot of working with the companies. 

And eventually, it takes a long time, but it ends up on your devices. And that historically has taken about 18 to 24 months from when you put it in a proposal to when you get it in. It's going to be a little bit longer going forward probably is my sense as we're organized-- Unicode is designed to space out some of the Unicode releases. 

So Emojination kind of has done its thing. So one of the weird things is like how did Unicode, this kind of non-profit organization based in Mountain View, California end up controlling this global visual language? So a lot of it has to start, has it has to do with the fact that emoji started in Japan back in the late 1990s. 

The set from Docomo in 1999 is considered, is widely considered sort of like the first like color emoji set. It has been collected by the Museum of Modern Art. And so the Japanese telecom companies would use basically, would have their own sets of emoji. And then there were different companies, so they would have different sets. 

So you could basically only send these like visual characters with someone who is on your same carrier. So it's like basically equivalent of if you were on like Verizon, you could only text people on Verizon with like emoji. Or if you were on T-Mobile, you could only do that. 

So at a certain point, they decided they the Apple and Google came into Japan. They wanted to start selling smartphones. And they realized that it was a hodgepodge of systems and they wanted to unify it. And so in 2007, they went to Unicode and they're like OK, help us unify the emoji, kind of basically all the emojis so that we have one standard system. 

And part of the reason is why Unicode. Because Unicode basically has this mission is to enable everyone speaking every language on Earth to be able to use your languages on computer and smartphone, so it basic unifies all written languages into one ginormous set. 

And that was not the case actually when I was growing up. There was a point where like if you were Japanese on Apple that would be different than Japanese on DOS or Chinese or Arabic. So it drove everyone crazy and they basically decided around the late '80s or early 1990s that they were going to come up with one standardized system that sort of encoded all characters in one ginormous set. 

So there's three main projects for Unicode if you care. So one is encoding characters including emoji. Now there are about 100,000 characters aside assigned, so that includes Chinese, Japanese, Korean, Arabic, Cyrillic, actually all the hieroglyphics, all of the emoji, a lot of things like the Bitcoin symbol or like copyleft or whatever. Those all assigned were about 100,000 characters, even those languages that are basically out of use. 

So the other thing it does, it creates localization resources so things so that you know, oh, if you're in this country this is you're using a euro or you're using the pesos or something. So there's a lot of localization data that is needed depending on which geography you're using your device from, or that you know that the time is used this way or dates are shown that way. So that is called the common local data repository or CLDR as they call it. 

And the other thing they do is they kind of maintain libraries for developers in order to do all-- so they are not building everything from scratch, and that is called ICU. So it's very funny, because it's called CLDR, and then one day, one of our friend's girlfriends made him this thing which she called a sealdeer, because whenever he talked about CLDR, she thought he was talking about sealdeers. So now this is his little like mascot for like Unicode related things. 

So how does Unicode do this? So basically it assigns code points. And each code point is a unique number assigned to each Unicode character, so face with tears of joy, it can be written like this with a code point, or it can be written like this in terms of decimal numbers. And it can also written in this in binary numbers. So these are all basically the same. 

And the key thing to know, at least about emoji, is that when your device, if you're talking on your iPhone with someone who's on a laptop or an iPad or like an Android device, it's not sending the images back and forth. It's sending just a number of back and forth. And then locally, your phone, or like your laptop decides like, oh this number correlates with which image in terms of our emoji font and then pulls it up. 

So this is really key to know why different emoji look different on different platforms. So 2007 to 2010, it took about three years, but Unicode 6.0 came out with our first little baby set of emoji. And it just kind of hung out there for a year. Like no one, it wasn't doing anything. 

So 2011 though, Apple starts adding the emoji keyboard and it just like explodes, like I feel like in some ways, emoji are were not invented. They were discovered. They like obviously touch something very, very primal to like our human desire to communicate in like little colorful glyphs on electronic devices. 

And you kind of have what's kind of really interesting is like the ambiguity that comes with what emoji kind of mean. And so one this is one of my favorite emoji. It's sort of like an upside down smiley face, very, very ambiguous. Clearly very ambiguous, because if you start typing into Google, like the top hits are like what does it mean from a guy. What does it mean from a girl. 

It's clearly something that a lot of people are using in like complex situation ships between each other. So one of the fun things is who can propose emoji. Technically anyone can. Anyone here can. Normal humans can. We have basically Google Doc or Google Form that we throw up historically between August, sorry April and August in the last two years. 

And so this is one of our favorite examples. This is Rayouf Alhumedhl. She was a 15-year-old Saudi Arabian girl who was living in Vienna at the time that she proposed the hijab emoji. And then she was like Time Magazine like coolest teens she got like a whole bunch of different things. She got into Harvard and Stanford. And she went to Stanford. So this is a proposal we got. 

Then there was a group of folks from Argentina who got the mate emoji, kind of the symbol of their national drink. Then we worked with, there was a nonprofit that really wanted to get a menstruation emoji and so what they proposed to begin with was like bloody underwear. 

And I was just like no, no, no. So many different reasons why this is a terrible emoji. So we did get blood drops and you can do moon and blood drop or underwear and blood drops. There's a lot of different ways. Actually it's really funny, because I was polling my friends beforehand what they would use to indicate menstruation before there was a blood drop. 

So there was like red wine. There was kind of that rose with the like falling petal. And then my favorite is actually my friend who used a Japanese flag as a way to indicate that she was having her period. So one of the biggest contributors, this skin tone emoji appeared, I think in 2015. It was amazing. 

It is. And it was proposed by a mom, Katrina Parrott. She is an entrepreneur and a mom who is just like at home one day and her daughter comes home and is like I wish there were emoji that looked like me. And her mom was like, that's great, honey. What's an emoji? 

And so she, like me, I guess googled and just figure it out that Unicode controlled emoji. And she just came up with a proposal saying we should not only have the yellow skin tones. At that time, everything was sort of Simpson's yellow. 

It's really interesting to see how race and nationality are depicted in different parts of the world. So originally in Japan, everyone was yellow, but these were the non-- by default, everyone was just like human or Japanese. But they had like a couple of things that were like not. 

One was, you had a blonde person. So there's an emoji called like blonde woman or whatever that represents all Westerners. So that was one. And then they have one that's like an Indian guy with a turban. So that's supposed to represent Indian people. And then there's like a guy with a little like little hat that's supposed to represent like Chinese people. So that was like that the Japanese view of race which was like default, then you were then you were like blonde Western, Chinese or Indian. And that is all there was. 

And obviously in the United States, we care a lot about race. And then so she came up with a system with five skin tones like just like normal people. Some guy in Germany decided that he wanted to do a face with one eyebrow raised, or as we call it the [? cobara ?] emoji. 

Oh, this one's fun. So woman's flat shoe. I have to say, not highly used statistically at this point. But I really kind of appreciate it because it was a mom who was very offended that all women shoes had heels, even the sandals. 

So this is her, she had like three kids at the time. She now has four. She was very fertile. And she also did the women's flat-- she also did one piece bathing suit because she was also offended by the fact that the only kind of bathing suit you had was like this little itsy bitsy polka dot bikini thing, which is not great if you're like taking your six-year-old. 

So I would say that got passed, but like it didn't go over super well with everyone. So you know Unicode, because it's very public, submits things for comments. And we got this comment back, so one piece bathing suit, why? A person wanting to indicate the use of swimwear can't use existing bikini. Is this really necessary? What about a Victorian bathing costume or wetsuit or [INAUDIBLE]. 

This is like literally in like the records, and like do not encode. And so the person who did this, actually very impressive. He's actually the person who created the middle finger emoji. And actually if you've ever seen the Vulcan emoji, the Vulcan hand emoji, he's actually very active. And I have to say this is actually I think one of the more impressive emoji. 

So obviously, obviously we have a lot of active debate. Sometimes you get like whole countries submitting. So literally the government of Finland, as in like their equivalent of the State Department, their diplomacy kind of thing, submitted a proposal for sauna. And these were so creepy and so weird. So much is wrong with this. 

But I felt where they were coming from, for like they're naked. They have no-- they're club feet. And so we decided to help them. We're like OK, we see where you're going with this. Let's see if we can help you like come up, you know like we had this spoon. Like should there be like steam around them. Like should they be naked or wearing a towel was like super dicey. 

But we wanted to help them because it was literally a foreign government coming in front of Unicode advocating for the sauna emoji on behalf of their entire country. So then this-- it's evolved into this basically person in steamy room which is the most sort of like the PG version of sauna. And there's no spoon. They're all dressed. It's very odd. 

But so you can see the evolution of what it started out. What we submitted and what it ended up so. There's a lot of evolution throughout the entire process. And like companies can submit emoji proposals too. So Google actually worked on this one. I love this one. 

So just to give you some context, as of 2015, there are many ways you could be or have an occupation as a male on the emoji keyboard. Like for example, you could be a police officer. You could be a detective. You could be Buckingham Palace guard. You could even be Santa Claus. Like these are so many jobs that you could have. 

But if you were a woman as of 2015, there were four things that you could be. You could be a princess. You could be a bride. You could be a dancer, or you could be a Playboy bunny. These were the sum total of all the occupations that we could have. 

So there was sort of this movement at that time, there was like this video on YouTube that like went viral. There was like a New York Times op-ed that was like, where are the women with professions? So basically they came up with a set of emoji for professions. 

And what's nice is not did women have these professions, now men have them too. So of an Emojination emoji, these are some of the ones that we've worked on. I think about 130 of the emoji on your keyboard probably came through, touched our system in some way, including, I have to say microbe or virus. I think, I have the opinion that every emoji has its day. 

It might not be like today. It might not be next year, but I have to say, virus was not doing anything. Then came 2020, and that was like such a good moment for it, along with soap. We had also done soap. So among the other emoji that we have worked on are, sorry, mooncake, llama, teddy bear. There were no toys. I felt really sad for toys. We have giraffe. There was hut. 

Bubble tea. Bubble tea was very controversial, actually. I have to say, we try to slide it in originally with the takeout box and the dumplings and people were not having it. And I understand that. Because there's not a lot. Like compared to beer or wine, like bubble tea is not long, does not have a long history on this planet. 

But I will say that they submit it again, actually kind of originally proposing that it was not just bubble tea, but like a black ball and milk and tea. It was kind of cool. And I have to say there was definitely a generational divide between the Asian women who sit in that room and are like this absolutely is a thing that we consume like almost like every week of our life, and people who are a little bit older who are like, that looks like a parfait. How do you not know that's not a parfait? 

We're like, we absolutely know it is not a parfait. And so it got in, eventually. So it does sort of influence. It kind of shows who is in the room influences the decisions that get made or sometimes in the room, now sometimes more likely in the Zoom. 

I actually had to say Beaver emoji, if you see Beaver emoji, that's one of the ones I'm most proud of. So that is actually co-authored by a professor here at Harvard who is both lesbian and was married to a woman from Canada. So it was very important to her to get the Beaver emoji passed. And she promised me it would always be the first line of her bio. 

And indeed, if you go to her Twitter handle. It's like Joan Donovan, creator of the Beaver emoji, comma, is Head of Research at the Shorenstein Center at the Harvard Kennedy School. It's pretty impressive. And then we did greens. Actually greens was really interesting because people, this was also like a generational, cultural thing. 

People were like, why do we need greens? We have salad. And I was like, we're Chinese. We don't eat raw greens because like you don't know where it's been or if it's clean. So we cook our greens so salad is not something that we have. So eventually I got my greens and so that was kind of fun. 

And then so these were some of the people who sort of have contributed to our little Emojination things, including a number of Native Americans who help get feather. So why do I care? So part of it is because I'm Chinese. I grew up speaking Chinese and English at the same time. And it's really interesting to see like Chinese and English characters in terms of emoji and Chinese together, right. 

So this is fire. You have fire characters and now you have the emoji things. And it kind of shows that there is a longevity in the human experience of something that was designed for 4,000 years ago has the same visual cues in the human experiences as now. So mouth, tree, moon, sun. They can mix and match them, which is super fun. 

So two trees kind of make a forest, oops, sorry. Oh well. And then the moon and sun together means bright, which I like. I like this one. So if you stop and you think about this, so this is basically a pig under a roof. 

And what does that mean? It does not mean farm as you might think. It actually means home or family. So in the Chinese kind of structure and outlook on the view, it's like where you keep your pigs is actually where your home is and what your farm is. So it gets kind of weird in all kinds of ways. 

So one of my favorite radicals, so this character means woman, me. And as I was learning Chinese, you kind of notice like how it shows up. So this is a woman underneath a roof and you're like oh it means mom or wife or whatever like home. 

It does not. It means peace, because things are at home when the woman is or things are at peace when the woman is at home underneath a roof, which I always thought was little bit odd. Then there is also woman plus child. So you're like oh, and actually specifically boy child. The connotation there is a little bit unclear. 

So you're like a woman plus child, family, mom, whatever. It is not. It means good. So the standard for goodness in ancient China was a woman who had a male child. So that kind of just like kind of irked me growing up. And then three women together means evil which is very Macbeth. 

This character means greed. This character means slave. This marriage, let's see I think this one is jealousy and this means adultery or betrayal. So like definitely not loving the way women were portrayed on the emoji keyboard. 

So in case you're wondering, we just came out with a kids book called "Hanmoji" that kind of compares emoji and Chinese. And I think they sent a whole bunch of books so that you guys can do some kind of contests like later on with CS50. 

So but the mixing and matching is really interesting. For example, the skin tones are actually the same yellow character plus a layer of skin tone on top of that. So I kind of took my lessons from Chinese in terms of seeing how things can combine. 

So there's something that you should know about, which is ZWJ. This is also an invisible emoji character. It stands for zero with joiner. And it was actually originally created for I think Arabic where you would basically kind of force something to have be in the beginning of a word or an end of the word by kind of having this invisible character. 

So the rainbow flag for example is actually a rainbow plus the white flag. And we could have all kinds of fun combinations. If you look at polar bear, it actually is, if you have an older device where it breaks apart, it is bear plus snow which is really cute. 

It was originally, I had bear plus white, and then we decided that bear plus snow made a lot more sense. So another one, this is new, I think you guys should have it if you've updated your phones in the last year or so. So mending heart is heart plus band-aid. 

What is this one? Oh, this is interesting. There was a breastfeeding woman for a long time and people felt like there was not gender parity. It was actually really interesting, all the people who wrote in and were like I want to be a dad showing that I'm holding my baby. Why is there only a woman holding my baby? 

So we kind of created a whole set. So this is man plus bottle. Ta-dah. And so this is an-- all of these occupations are actually oftentimes a woman plus, like the fried egg or like a school or a tractor and that's how you got the occupations. 

If you send an emoji over into an older system, sometimes it'll break apart. So one of my kind of favorite kind of contributions in this world is interracial couple emoji which we did with Tinder which is super fun because then you could have different couples that are, and like so many [INAUDIBLE]. 

This is a fun, if you guys ever have to do a [? combinatoric ?] test. This is really fun because you have to genders plus a third like neutral gender plus two people plus five skin tones plus yellow, like how many emoji couples can you come up with when you introduce this factor. So this is-- and underneath it, it's just a ZWJ sequence, it's like two people standing together that are like glued together. 

Now this actually gets interesting from a CS50 perspective because in many cases, even though you only see one character underneath the hood depending on how your system works, they're counting each one of these as an individual character. So your string length actually might be five instead of one. And this kind of became a problem with things like Twitter where things had a hard skin length. 

So gender inclusivity is actually one of the things that we've been dealing most with in the last couple of years. So it's kind of interesting if you think about both what a pictorial language looks like versus the abstractness of a spoken language. So because we had boy and we had girl. But there was no way to say generic child. 

Like if you were, you want to say child, you had to pick a boy or a girl, but not a way to say just some little person. And that's really key because in English at least there is no gender implied by child. So how do we mimic that? And also is key for something like doctor, right, doctor and teacher. Those don't have gender implied, but when we have them on the emoji keyboard, you'd pick a male teacher or a female doctor or whatnot. 

So there was actually a guy at Adobe who considers himself non-gender binary also the man behind the orange heart. He fought and got basically the first three non-gender, the non-gender binary emoji. So child, adult, and the older adults. So those are creative. And then we started having to propagate them through actually all the occupations. So these are the gender neutral versions of many of those. 

But then we got into this whole thing where every emoji that had a gender originally had to be mirrored. So originally we had bearded man, and then we're like, OK, well we actually have to get bearded woman. So that is on your keyboard. There is pregnant woman. There is now pregnant man, which is interesting. 

There is woman in a bridal gown. There is now man in a bridal gown. And then there were ones that actually had to be created that were neither man or woman. So this is a merperson. So there was merman, there's mermaid and there was merperson. It was really interesting to figure out, how do you draw a gender neutral merperson. Like a bunch of them in the beginning actually had the arms crossed around the chest. 

Monarch, so there was prince and princess, and now there is monarch. And one of my favorite actually is there was Santa Claus and there was Mrs. Claus and now there's Mx. Claus. Like the name of this character literally in Unicode is Mx Claus so I feel like it's sort of like a very official enshrining of gender non-binaryness in like the world. Not everyone loved it. New York Post did not love this, like we're cutting of into like emoji woke wars. 

So some emoji stats for you. This is very fascinating. This is sort of like the general distribution. By far, the single emoji that you use more than anything else is the face with tears of joy, about 10% of all emoji sent is that one character. And the number two is heart, red heart, and then it kind of goes down. 

So there's a frequency of emoji use. This is sort of done by order of magnitude. So 1 is 1/2 of 2. 2 is 1/2 of 1 so duh, duh. It's really interesting. It's a very, very steep drop off after the first couple in case you ever want to go on to the emoji kind of Unicode website, you too can see all the frequency things. 

So I think it's really funny. So basically if it's green going this way, it increased in usage between 2019 and 2021. And it's red going this way, it drop. And so pleading face, which is a relatively new emoji, just sort of shot up on the charts. And whereas actually like smiley face with heart eyes actually kind of slipt which is interesting. 

So we just closed our emoji proposal around for 2022. These were the breakdowns. People love submitting smileys and food and beverages, animals and nature. I mean, these are very googly colors. So what is the future of emoji? I will tell you because we just had a meeting two weeks ago so I can now publicly talk about it. 

So historically, there was this whole idea like Unicode doesn't want to be in the world of like encoding glyphs for like devices everywhere. There was very controversial when I started doing that, because mostly what Unicode used to do was you take an existing language. It could be done, you know and then it would just take it and digitize. 

It took languages that existed and just digitized them. And then when it kind of wandered into emoji world, suddenly it's like deciding what deserves to be like an emoji decides to be digitized. So trying to get out of it and they have proposals over time or it's like, oh, maybe we should like come up with a way to send pictures back and forth where you it's a fixed picture and you like use a hash so that we would look at the picture and then go do a lookup somewhere. 

That did not go over well. Then there was actually a really interesting proposal I kind of like, didn't go over well, which is using something called a queue ID which is in the Wikipedia world. So in Wikipedia world, items all have numbers across the different language Wikipedia. 

So Obama, human, Earth, they will have an ID number, so that the page in English and the page in German the page in Chinese all know that they're pointing to the same thing. So the question, so one idea came up, like why don't we use the numbering system so we can use like Eiffel tower and see the number and then like, oh, people know like oh you're, trying to say Eiffel tower. 

That did not go over well. So both of those proposals seem dead as of yet. And it's too bad because you'll see what's happening. So what's coming in 2022? So these are the emoji that I actually sort of thought they would be on your phones by now because we're in mid-November and they usually update early November. 

So three more hearts. People love hearts. Wing, blackbird, goose, birds also, purple flowers, jellyfish, moose face donkey, donkey was a bit late for the kind of elections, ginger, peapod, wireless, khanda, shaking face, folding hand fans. 

That one was interesting because when people first proposed it, they proposed it as like an electric fan and that didn't-- who knows what electric fans will look like in 100 years? Because the thing is, once an emoji, always an emoji. They never retire. So they're always looking for things that have a long visual longevity, floppy disk, do not actually do that. So there's always like, we don't want another floppy disk. 

And then hair pick is interesting. So there was a whole debate about how to convey like Afro African hair, like the curly hair that they introduced a couple of years ago is supposed to do that. And most of the vendors actually have it in a sort of Afro way except for Apple. So there's a lot of complaints. But hair pick was sort of an interesting way. It means both comb but also has sort of an interesting historic connotation, and it's been around for about 2,00 years. 

A couple of music things, maracas and flute. Beyond 2022, one of the things that's going to die, oops, can I go back? No, I can't. Oh well, we're going to retire the family emoji. They didn't go over so well. There were so many of them. It's combinatorically if you had all the everything in all the races all, the races, all because you wanted to have skin tones, because you didn't want imply that families can only be one race. 

It was such a ordeal. Essentially, we're all like, no one uses them, and there are so many. And it's like the fonts like in terms of the load is like too large so they're just going to make them all into like basically little like bathroom symbol type folks. So I think that is, those will disappear. 

What's actually really interesting about the family emoji is they had gay fam. When they introduced the family emoji, they had gay family emoji, and the Russian government went berserk. And actually you can Google this in 2015, you'll see a bunch of articles about the Russian government considering it homosexual propaganda to use. 

And there was a big debate about whether or not they were going to ban Apple devices. And so you can see a lot of the media coverage from that time. But I thought it was really interesting how upset a national government can get about little pictures on your phone. 

Another thing that's on the agenda as of a couple of weeks ago is directionality in terms of emoji. So as you know, most emoji kind of just flip one way or another. And the reason why it matters is because not all languages run in the same direction. 

So for example, Arabic. So we're used to left to right, but a lot of languages go right to left. So and kind of changes the meaning of emoji. For example, right to left, I send this a lot to my friends when I'm going flying from the Bay Area to New York. 

If you do it from left to right, however, that is what it looks like. So it looks like you're in a Bay Area but the plane is still going that kind of up and to the right. And then now it looks like you're going from New York to the Bay Area. 

The other place is like, oh, it's a girl, and she's running really fast. Right. That is right to left in our world, wait left to right, sorry. Sorry, that was supposed to be left to right. And in here it would be she's like behind like pollution or something like that. So sorry about-- 

So an example, this is actually in the proposal. Like in one case, if it's left or right, you're running away from a line of cars. And the other one, it's a warning to not run behind car fumes. So they are trying to figure out, how do we mirror a bunch of the emoji. 

But the main thing that I think sort of, I don't know when it's going to happen, I'm really hopeful it's going to happen is trying to come up with a system that supports little stickers in line that don't need Unicode. So this is like Slack or on Twitch, you can embed little pictures in line, and all the vendors have to get together and agree to come up with a standard way to do that. 

They'd have not yet come up with that, but that is sort of one of the ways that Unicode is like it wants to back away from actually being like a global regulator for like little colorful glyphs. 

And so if you ever need to reach me in my emoji world, you can find me jenny@emojination.org. There will be-- it will be actually a while I think before we see a next generation of emoji showing up. It used to be like every year, they would get new code points. It might be a little bit less than every year now as they work on things like directionality over time. 

If anyone has questions, you can ask questions. You can find me afterwards. I think I feel like there's supposed to be some hubbub right now about maybe microphones but maybe not. But maybe I'm just done. And if there are questions or if David is around, I'm happy. I'm happy to have to answer any questions that folks have. Yes? 

AUDIENCE: Hi. Yes. I was wondering what were your thoughts on The Emoji Movie. 

JENNIFER 8. LEE: So the question is, what are my thoughts on The Emoji Movie. You're talking about the Sony animated one? Yes. My thought on that is it is better than a 6% rating on Rotten Tomatoes would lead you to believe. So that's my one thought. And my next thought is that was a rush job from an animation perspective. That was about 18 months, whereas a typical animated movie takes four years. 

So in my spare time, I also produce movies and documentaries. So one thing that is key to know about movies and animated movies, and this is very important. They take a very long time, but you can always fix it, because you haven't shot anything. 

And a very good example of that is I assume you guys have seen Frozen. If you haven't seen-- you seem of the age that you would have seen Frozen. I do not understand how huge and a phenomenon or why was such a huge phenomenon. But they actually did an original cut of Frozen and it-- 

So I don't know if you guys know the Snow Queen thing, but she's like super dark and not fun and kind of evil and not someone you want to get behind as a character. So they actually did sort of a rough cut of that of Frozen. And they came out of that with, it is just storyboarding. 

They're like, that is not good. And they killed it. So they were like, we can't go with this and then started from scratch more or less again, starting with a song. "Let it Go," which is actually written by a kid from my elementary school, Bobby Lopez, or co-written by Bobby Lopez. 

I also-- actually fun fact, I also went, I would take the school bus with a Lin-Manuel Miranda. So I was a fourth grader when he was like a kindergartener. So we had a very musical elementary school in New York City. But the thing is, they could fix it because they had enough time and have enough money, not like movies where you shoot humans, much harder to fix. 

You have the footage that you have, and you can do little pickups, but you can't fix it. So essentially what happened in that case, I think it's 18 months, and it could have gotten better. And a lot of the movies that you see with Pixar, like it's very-- it's actually sort of emotionally similar to the movie called Inside Out. . They just had more time, and so it's better, so as opposed to 18 months which is not long enough to make an animated movie. 

But the other fun thing is, it was so weird because they sold sponsorships. It was like, oh my God, here comes the bots and the malware. Let's go into Dropbox and protect ourselves. And so I think that it got a lot of bad kind of vibes from the press for doing things like that. But from a kid's perspective, it's fine. I think if-- I don't know that I would put it on my top 10 of animated pictures, but it's better than 6% on Rotten Tomatoes. 

And then actually if you guys ever care, we have done-- I did a documentary about emoji so and all the people that helped create emoji. And we did a CS50x movie night, I think during the pandemic? Was it during the pandemic? Everything is sort of like blurred together, but it was during the pandemic. Yeah. More questions? Yes? 

AUDIENCE: Hi. I wanted to know that you mentioned that one of the criteria for having an emoji accepted is that it's popular. How do determine whether-- 

JENNIFER 8. LEE: Where there's demand, yeah. 

AUDIENCE: Whether there's demand. How do you determine demand? Is it based on whether or not [INAUDIBLE]? 

JENNIFER 8. LEE: Yeah, that's a very good question. Yeah, so the question is one of the proposals-- One of our criteria is of getting an emoji accepted is to try to demonstrate demand and how do we demonstrate demand? And I would say in a pretty clumsy way actually at this point. 

So the main thing that you have in our current proposal process is we have a median emoji, which is elephant. So elephant is like, you stack ranked all the emoji for popularity, elephant is like [CLICKS] right there in the middle. And it's also a concept that's universally understood across all languages. 

So elephant shows up somewhere between 500 million and 700 million in Google search results, like if you type it into a laptop, you'll see elephant, 500 million search results. And generally, you're trying to-- when you're comparing your term to elephant, you want to see very roughly how many Google search results, Bing search results, sometimes Instagram. 

So actually something that was really surprising to me was someone proposed hummingbird. I think hummingbird is a good proposal. But if you look at hummingbird, it's only like 21 million in terms of the stats, so which I thought was like very surprisingly low. So that's one of the main ways that we kind of see like, is it also visually used and all of that. Yeah. Any other questions? Are we good? 

I didn't even need my water or anything. Oh, can-- I'm going to take a picture. I'm going to take a picture for because now you guys are actually human and not Muppets, so I'm very, very excited about this. So I will send this to my block mates and be like, I just lectured at CS50 in Sanders Theatre. 

DAVID J. MALAN: My thanks to Jenny Lee. 

[APPLAUSE] 

Thank you. Yeah, you can stay up here if you want. Give me one second. So if up until now, thought it would be appropriate to toss this up on the board. If up until now, you've not yet gotten CS50 stress ball on the way out, please do grab one. We got some extras as well off to the side. 

But I would also keep in mind, back in week 0, where again we began, we asked you to categorize yourselves as to whether you are among those less comfortable, those more comfortable, or those somewhere in between. Please know now that you are officially all some-- 

Please know now that you were all officially among those more comfortable and indeed even though a couple of more milestones await, we cannot wait to see what you accomplish with your final projects. In the meantime, as always this is and now this was CS50. 

[APPLAUSE] 

[HARMONICA] 

ALL: (SINGING) Bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum. Mr. Sandman, when I enrolled in CS50. I'll say, truth be told, I thought I'd be a real coding hero, because I did so well on p-set 07. 

It picked up so fast. Turns out the C is harder than scratch. Hello, world and goodbye sleep because this is CS50. Bum, bum, bum, bum, bum, bum, bum, bum, bum bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum. 

Mr. Sandman, I was on the [? fall grind, ?] trying so hard to not fall behind, attending section and wanting a tutor, stuck in the entry point of my computer. Sandman, finally getting ahead. They would switch us to Python instead. 

Why we spend five weeks on C because this is CS50. Bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, bum. Mr. Sandman, we completed each task. JavaScript SQL, CSS and Flask. 

With every language, our minds had to reset. Don't get us started on that finance p-set. Sandman, now I return. My friends asked if I would do it again. I replied, obviously, because this was CS, no more p-sets because this was CS-fif bum, bum, bum, bum, bum, bum, bum, bum, bum, bum, T. 

[APPLAUSE] 

[MUSIC PLAYING] 
