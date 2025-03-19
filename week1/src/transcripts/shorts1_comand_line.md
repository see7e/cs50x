---
title: SHORST1 - SHELL - TRANSCRIPT
tags: programming, cs50
use: Transcript
languages: NULL
dependences: CS50
---

[MUSIC PLAYING] 

DOUG LLOYD: OK. So let's talk about how to use the Linux command line. Now, the CS50 IDE, or in fact, even a CS50 appliance, if you're familiar with that, or you're taking an older version of CS50, is a cloud-based machine which runs Ubuntu, which is one of the many flavors of the Linux operating system. Linux operating system is favored by programmers, because it's just cooler, right? 

Many modern Linux distributions have graphical user interfaces, which we also call GUIs, G-U-I, to allow easy mouse-based navigation, which you're probably familiar with, if you're a Windows or Mac user, moving around your mouse, double-clicking on icons, and so on. Still though, as a programmer, and even though the IDE contains the ability to do some graphical user stuff, clicking, and dragging, and all that, you'll still be using your terminal window pretty frequently. And you can do many of the same tasks that you can do with a mouse with keyboard commands. And we're going to talk a little bit about what some of those commands are right now. 

Now, these commands can be used on any Unix-based operating system, which includes Linux, but also includes Mac OS. If you open up Terminal on your Mac, you can use these exact commands. Windows also has Command Prompt, but some of the commands are slightly different, so it doesn't actually work, because Windows is not a Unix-based system. 

So let's take a look at some of these Linux commands. The first one that you'll probably use quite a lot is ls. That's a lowercase l, followed by a lowercase s, which is short for list. And what the list command does is it gives you a readout of all the files and folders in your current directory. So you can see everything you can get to from where you currently are. 

So I've opened up here the CS50 IDE. And I'm going to zoom-in in a second to give you a closer look, but here's the broad picture of what the IDE looks like. On the left, you can see we have a file tree, which you're probably familiar with, double-clicking, and files and folders, and all that stuff. So that's still there in the CS50 appliance. At the center in the top is where you're going to be writing your code, once you click on a file. And at the bottom, we have a terminal window, which is where we can execute these terminal commands. 

I'm going to zoom-in and head over here, just to show you that, in fact, I can click on these files and folders. So clearly, where I currently am, I have two folders, called pset0 and pset1, and three files, one called hello, one called hello.c, and one called hello.txt. 

So let's move down to the terminal window and get a closer look. So we just talked, again, about the fact that we have three files and two folders in the current directory. If I type ls, which again is the command to list the contents of the current directory, and then I hit Enter, look what I see, hello, hello.c, hello.txt, pset0 and pset1. 

pset0 and pset1 are colored blue, to indicate to you that those are directories that we could navigate into. And we'll learn a little bit about how to navigate into directories in a minute. And every other thing is colored black, if it's a text file or a source code file, and green, if it's an executable file. So clearly, that means that I could run a program called, hello. That's what the green one there means. But basically, typing the ls command has allowed me to look at everything that exists in my current directory, which matches what we see here, in the graphical display of the same. The next command you'll probably use quite a bit is cd, lowercase c, lowercase d, which is short for change directory. This allows us to do what I was talking about a second ago, which is to navigate between directories at the command line, as opposed to double-clicking on folders. So if we type cd and then the name of a directory, we can get into that directory. 

As an aside, know that the name of the current directory is always dot, and the name of the directory one level above where we are now, that is the name of the folder in which our folder is, dot, dot-- or in which our folder is, is dot, dot. And if you're ever curious about the name of your directory, you can type pwd, which stands for present working directory. We'll take a look at all of these now, by heading back to the CS50 IDE. So I'm back in my workspace now. And I'll zoom-in again on the terminal, so we can take a look at moving around within the IDE. So I'm going to list the contents of my directory again, just to reground us in where we are. So if I type ls, which is for list again, I see that I can get to pset0 and pset1. Those are the directories I can get to from here. I know that, because the IDE gives me a clue by coloring them blue. 

Let's say that I want to get into my pset1 directory, because I'm working on problem set 1. I can type cd-- again, short for change directory-- space, pset1. And if I hit Enter, notice what happens. It doesn't look like a lot has happened. But if you look at the prompt, it now tells me that I'm in ~/workspace/pset1. I've navigated into the pset1 folder that was within my workspace. 

And if I type ls, I see some different stuff here, right? This isn't the same list that I saw before. I've navigated into pset1. And so now, when I type ls, I'm getting the context of what can I see from within the pset1 folder. 

Now, I'm going to type control l, which just clears the screen. And I'm going to list the contents of the directory again, just so you can see. I just wanted to do that to clear out some of the stuff that you saw down below and to prevent this from going too far down out of range. 

Now, I said earlier that, if I want to navigate to the current directory, I can type cd space dot. Hit Enter. It doesn't do anything, right? I'm changing directories to the current directory. You're not always going to find a need for a single dot, but you will occasionally. 

Let's say that I want to move up one level. I want to get back to my workspace directory. I can't type cd workspace, there's no such file or directory. And the reason for that-- if I type ls one more time-- is that there is no directory called workspace inside of my pset1 directory. I'm going to clear my screen again with control l. Remember what I said earlier, though, that we can navigate back with dot, dot. That's the name of the parent directory. So if I type cd, space, dot, dot, and then hit Enter, now look at what happened. My command prompt tells me that I'm back in my ~/workspace directory. I moved up one level, thanks to dot, dot. 

Now, let's say that I'm using an operating system that is Linux-based, but doesn't necessarily tell me where I am. This one happens to tell us that I'm in ~/workspace right now, right at the prompt. But I could be completely lost in a mess of folders, and I have no idea where I am and no idea where I want to get back to. There's two things that I can do. 

First of all, I can figure out where I am, by typing pwd. That's my present working directory. And if I hit Enter, it tells me exactly where I am. Now /home/ubuntu is the long way of saying, tilde, which is your home directory. But it tells me that I'm in home/ubuntu/workspace, or ~/workspace. 

I'm going to navigate to my pset1 directory again, and I'm going to list the contents. And I see that I have another directory there, called extras. So I'm going to cd into extras, and then I'm going to clear my screen. 

So now, I'm pretty far in, right? What if I want to back to workspace immediately? There's a couple things I could do. I could type cd, dot, dot, slash, dot, dot, to move up one level and then another level. But that's kind of annoying. 

So if I ever want to get back to just my home directory, tilde, I can type cd with nothing after it. Cd, Enter. And now, I'm in tilde. And if I want to get to workspace, I can just type cd workspace. And that's how you work changing directories within the CS50 IDE or any Linux operating system at the command line. All right. The next one that might come in handy is mkdir, which is short for make a directory, if I need to create a new folder. If you're familiar with the GUI operating system, you might right-click. And then, when the context menu pops up, choose New Folder. That's probably how you've done it before. But we can also create directories at the command line. So we're back in the IDE. I'll zoom-in on the terminal and list the contents of my directory again, just to give us a frame of reference. Let's say that, now, I've finished working on problem set 0 and problem set 1. So I want to create a new directory to work on for problem set 2. How do I do that? 

Well, again, I could right-click in the left side there and choose New Folder and create a pset2 directory. That would work too. But then I also do it at the command line pretty quickly, by typing mkdir, space-- I typed in n, but-- space pset2. If I hit Enter and then I list the contents of my directory again, I see that, look, now I have a pset2 folder. And I can navigate into that using cd and do all the work I need to do for pset2. Incidentally, I'll just pop over here really quickly to the file tree. And you can see that, also, in the graphical File Explorer, we can see that the pset2 directory has also been created there. And I can navigate to it, using the GUI as well. The next time and that's probably going to come in handy is cp, which is short for copy. Copy, unlike all the other commands we've seen before, takes two arguments, a source, the name of the file that you want to copy, and a destination, where you want to copy the file to. It's pretty easy to copy a file, so let's do that. 

So we're back in the IDE. I'm going to list the contents of my current directory with ls. Now, let's say that I want to make a copy of hello.txt. Again, from the file tree on the left, the graphical interface, I could right-click on hello.txt, make a copy, paste the copy. But I can do it pretty quickly at the command line too. 

Let's say I want to copy hello.txt to hi.txt. I can cp, space, hello.txt. That's my source file, so that's why I'm going to choose that one first. And then I need to name the destination file, hi.txt. I hit Enter. And if I list the contents of my directory again, there's hi.txt. I made a copy of it. And in fact, if I went into hi.txt, I could see that it would be an exact duplicate of everything that existed in my hello.txt file. 

So that's how you copy a file. But what if you want to copy an entire directory? So for a second, let's take a look at what's in my pset0 directory. If I cd pset0 and list the contents, I have a directory called, sample, and a scratch file, scratch.sb2. So that's good to know. So let's clear the screen, and I'm going to go back to my workspace directory for a second. 

Let's say that, now, I want to make a copy of my pset0 directory. I can't just say cp pset0 pset3, for instance. You get this weird message, omitting directory pset0. Why do you get that message? Well, it turns out that, when you have a directory that has other stuff inside of it, the cp command doesn't really necessarily know what to do with it. 

We need to explicitly tell Linux, the terminal, I want you to copy the pset0 directory and copy every folder that exists inside of it and every file that exists inside of it. In other words, I need you to recursively dive down into pset0 and make a copy of everything in there. 

If I want to do that, what I can do is cp-r, for recursive, pset0 pset3. Hit Enter. Now, if I list the contents of my directory, I see there's the pset3 directory that I can work with. And if I cd into pset3 now and then list the contents, look, there's sample and scratch.sb2 again. So that's pretty cool. So that's how you can copy an entire directory, and not just a single file. So if you want to copy a directory, just remember to use the -r flag when you're working with the cp command. All right. So I've copied a file, but I've done it by mistake. And now, I want to get rid of it. How do I do that? Again, if you're familiar with a GUI interface, you can right-click and just choose Delete. And it'll send it to the trash or the Recycle Bin. But at the command line, we can just type rm, for remove, and then the name of the file we want to get rid of. 

Now, rm is very careful. It does a lot of double-checking, to make sure that you actually want to delete the file. It doesn't want to make any mistakes, because there's no Recycle Bin here. Once we delete a file, it's gone. And there's really no way to recover it. So we need to be pretty careful, and so rm is going to be really careful for us. 

So let's go back to the IDE and get rid of that hi.txt file that I created a minute ago with copy. So we're in the IDE. And I list the contents of my directory again, just to give us some context. I mean, you can see that there's hi.txt, which I created a little while ago. Now, I want to get rid of it. How do I do it? 

Again, just rm. So I can type rm hi.txt and hit Enter. And there's rm being really careful for us and making sure we actually want to delete this file. Do you really want to remove regular empty file hi.txt? That's just like an operating system, like Windows or Mac, that you might be familiar with popping up that box says are you really sure you want to do this. 

I'm pretty sure I want to this, so I'm going to type, yes-- or I could also just type y-- and hit Enter. And if I list the contents of my directory again, hi.txt is gone. Not bad, right? Let's press Control L, just to get rid of all this stuff and get us back at the top of the screen. 

Now, there is a way to short circuit rm, so that it doesn't ask us that question. We really know we want to get rid of that file, and we don't even want to be asked the question. How do we do that? Well, we can specify an extra flag, just like we did with cp where we could add the -r flag, to recursively copy into a directory. There's another flag for rm, which is -f, which is to force rm to do exactly what we're telling it to do. 

So let's say that, now, I want to get rid of my hello.txt file. I don't want that one either. What can I do? Well, I can rm -f hello.txt. What do you think is going to happen here? It's gone. Didn't even ask me the question. And in fact, if I list the contents of my directory again, it's gone. There's no undo here. hello.txt is gone, and I wasn't even asked if I wanted to delete it. What if I want to get rid of an entire directory? The way you do that is very similar to copy. If you want to delete a directory, you don't just want to delete the directory, you want to delete everything inside of it. And so you use -r, to recursively delete a directory. 

So let's rm -r pset2. I'm not actually working on pset2, so I can get rid of that directory. I hit Enter. Do I want to remove the directory, pset2? Yes, I do. And if I list the contents of my directory again, it's gone. All right? 

One more variation on this theme. So I'll clear the screen again, to put everything at the top. Hit ls. Now, I want to get rid of my pset3 directory, and I really know I want to get rid of my pset3 directory. I can recursively and forcibly remove my pset3 directory. 

Now, you're going to be really careful when you're using rm -rf. As you program more, it'll be something you just do really quickly. And in fact, I do it all the time. But it can lead to some disastrous consequences, if you accidentally delete the wrong thing. So I want you to be aware that this is an option available to you, but use it sparingly, and use it with caution. 

I know for a fact I'm not working on my problem set 3 anymore, so I'm going to get rid of all of those files. And I know I don't want to be asked every single time if I want to delete a file, so I'm going to rm -rf pset3. Didn't even ask me if I wanted to get rid of it. I hit ls. pset3 is gone. So that's all the variations that you can use to get rid of files with rm. 

The last command line command that's going to pretty useful for you is mv, which is short for move. Move Is basically equivalent to rename. It moves a file from one location to another, the source to the destination. Let's see where using a move might be handy at the terminal window. 

So I'm in my pset1 directory, and I've noticed something has gone a little wrong. I was working on my greedy problem, but I accidentally named it greddy. So when I try and run it through check50, it doesn't really work. I do have a couple of options. We could do what we've done before, which is to make a copy of the file. I could copy greddy.c to greedy.c, right? Hit Enter. I see that both files are there. And then I could rm, to remove, greddy.c. That gets rid of it. So that would work, after I confirm that I want to get rid of it. And I effectively have renamed greddy.c to greedy.c. I copied it, and then removed the original. 

But that's a multi-step process. And certainly, there's a better way. In fact, there is. So let's hit Control L, just to bring this back up, and list the contents of my directory again. 

So let's say, oh, I made a mistake. I actually really did want to call that file greddy.c. In one fell swoop, I can type move greedy.c to greddy.c. Hit Enter. And now, I didn't have to copy and remove it, I just was able to rename it. One-stop shopping. 

Now, there are a lot of other basic command line utilities that you can use with the Linux command line. And we'll be discussing a lot of them in the future in CS50. But for now, just getting your feet wet with working with this terminal environment, these five commands should get you pretty far in navigating around and working with files in your IDE or in whatever Linux-based operating system you're using. 

If you're curious and you want to look ahead a little bit at some of the command line commands we'll be using in the future, here's a list of a couple of the more common ones. I'm Doug Lloyd. This is CS50. 