---
title: CS50 - Week 10
tags: programming, cs50
use: Documentation
languages: Flask
dependences: CS50
---

> This material is distribured by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my undersantding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Welcome!](#welcome)
- [Computational and Critical Thinking](#computational-and-critical-thinking)
- [Abstraction and Precision](#abstraction-and-precision)
- [Life After CS50](#life-after-cs50)
- [Quiz Show](#quiz-show)
- [Emoji](#emoji)
- [Summing Up](#summing-up)

</details>

> [Transcript](./src/transcripts/lecture10.md)

---

> what ultimately matters in this course is not so much where you end up relative to your classmates but where you end up relative to yourself when you began

## [Welcome!](https://cs50.harvard.edu/x/2023/notes/10//#welcome)

-   This is CS50!
-   This is our final week in the course!
-   Indeed, we have come a long way! You have drunk from the firehose! If you have not _got it all down_, that’s okay! Consider what was once _hard_, like getting `hello` to compile, is now less challenging.
-   What ultimately matters in this course is not so much where you end up relative to your classmates but where you end up relative to yourself when you began.
-   Recall that in Week 0, we began with zeros and ones. We assembled in Scratch, learning the essential building blocks of programming.
-   By Week 2, we learned about memory.
-   Then, we learned about debugging.
-   By Weeks 3 and 4, we were learning more about time complexity and efficiency of your code, discussing bubble sort and merge sort.
-   We discussed pointers, giving you a sense of what is happening inside your computer.
-   In Week 5, you built your own hash table! The principle of key-value pairs was visible in Python, SQL, and on!
-   In Week 6, you learned about the ideas of columns, rows, and tables.
-   Finally, we learned about building web applications.
-   This week, we will be focusing on how to code-client side. Up until this point, you have been programming in the cloud. If you so choose, you can use these tools on your own Mac or PC.

## Computational and Critical Thinking

-   Way back in Week 0, we introduced you to the idea of _computational_ or _algorithmic_ thinking. You will likely find, through this course, you will be able to sort your thoughts more clearly in the future!
-   Additionally, we exercised our _critical thinking_ in that you will likely be able to better understand what is happening behind the scenes in other people’s programs. You will be able to better evaluate your own work and the work of others.

## Abstraction and Precision

-   In this course, you learned about how to take big problems and separate them into smaller and smaller ones.
-   Indeed, you learned how you could write pseudocode to break a problem down to manageable steps.
-   Further, you learned how the language you use is of particular importance! Your language has to be precise.
-   As you transition out of CS50, you will likely be able to better assess what is required of you in assignments for other classes, at work, and at large: You will be able to understand how to break down a large problem and ask the questions necessary to yourself and others to have a better outcome.

## Life After CS50

-   There are a number of ways you can engage in programming-related work outside this course.
-   First, you can install command-line tools, like [Xcode](https://developer.apple.com/xcode/) and [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/about).
-   Second, you can also [learn GIT](https://youtu.be/MJUJ4wbFm_A).
-   Third, you can [download VS Code](https://code.visualstudio.com/).
-   Next, you can host a website using [GitHub Pages](https://pages.github.com/) or [Netlify](https://www.netlify.com/).
-   Fifth, you could host a web application via [Amazon AWS](https://aws.amazon.com/education/awseducate/), [Microsoft Azure](https://azure.microsoft.com/en-us/free/students/), [Google Cloud Services](https://cloud.google.com/edu/students), or [GitHub’s Education Pack](https://education.github.com/pack).
-   Further, you can keep reading:
    
    -   [https://www.reddit.com/r/learnprogramming/](https://www.reddit.com/r/learnprogramming/)
    -   [https://www.reddit.com/r/programming/](https://www.reddit.com/r/programming/)
    -   [https://stackoverflow.com/](https://stackoverflow.com/)
    -   [https://serverfault.com/](https://serverfault.com/)
    -   [https://techcrunch.com/](https://techcrunch.com/)
    -   [https://news.ycombinator.com/](https://news.ycombinator.com/)
-   The above resources are not an exhaustive list. _Geek out_ as much as you please!
-   Further, we hope you will join one of our many [communities](https://cs50.harvard.edu/x/communities).

## Quiz Show

-   We hosted our own quiz show! The following questions were covered:
    
    -   How do you print “hello, world” in Python?
        
        -   `print("hello, world")`
    -   What does DNS stand for?
        
        -   Domain Name System
    -   What is the upper bound of Merge Sort’s runtime?
        
        -   O(nlog⁡n)
    -   What is the duck debugger’s favorite hobby?
        
        -   Sitting quietly on stage
    -   What is the function used to open a file in C?
        
        -   `fopen`
    -   How does strlen compute the length of a string in C?
        
        -   It counts the number of characters until it reaches `\O`
    -   Where does malloc allocate memory from?
        
        -   Heap
    -   How many people flew from Fiftyville to New York on the day of the crime?
        
        -   16
    -   What are `meta` tags used for in HTML?
        
        -   To describe a web page
    -   How do you find the address in a variable in C?
        
        -   `&`
    -   What does `->` mean in C?
        
        -   Replaces a star and dot operator
    -   Which of these is not a data type in SQLite?
        
        -   String
    -   Which of the following is a valid way to print “!!!!” in Python?
        
        -   `print("!" * 4)`
    -   What does the free function do?
        
        -   Deallocates memory at a given address
    -   Which is not a step of compiling?
        
        -   Threading
    -   What was the surprise at the surprise of the Halloween lecture?
        
        -   Someone dressed up as David Malan
    -   Why is it incorrect to use the `==` operator in C to compare strings?
        
        -   You are comparing the locations of the strings
    -   What is the difference between NUL and NULL?
        
        -   NUL refers to `\0`, whereas NULL is the zero address
    -   What do the binary bulbs spell on stage today?
        
        -   ![🧁](https://twemoji.maxcdn.com/v/14.0.2/72x72/1f9c1.png)

## Emoji

-   We were joined by Jennifer 8. Lee, ‘99, CS50 alum.
-   A number of years ago, Jennifer was texting her friend, Yiying Lu, when they both realized that a dumpling emoji did not exist. So her friend, who is a designer, came up with her own image of a dumpling, and Jennifer was inspired to investigate who controls emoji.
-   Jennifer researched the Unicode Consortium, a non-profit organization, with technology companies and other organizations as voting members.
-   Jennifer founded [Emojination](http://www.emojination.org), which “wants to make emoji approval an inclusive, representative process.”
-   There are numerous factors that influence whether or not an emoji is added, including:
    
    -   Popular demand or frequent requests
    -   Multiple usages or meanings
    -   Visual distinctiveness, or easily recognizable at small sizes
    -   Whether they complete some gap, such as an orange heart among red, yellow, green, and blue hearts
    -   Existing vendor compatibility, such as if one company already unofficially supports it
-   There are also factors that are considered against an emoji’s inclusion, including:
    
    -   Too specific or narrow
    -   Redundant or too similar to an existing emoji
    -   Not visually discernible, like a cave
    -   No logos, brands, deities, celebrities
    -   No more flags
-   Unicode Consortium votes once per year about adding new emojis.
-   Historically, the Unicode standard emerged from many different technology companies having their own systems for special characters.
-   Unicode assigns a unique number to each of the 100,000 special characters.
-   While emoji existed prior, their popularity exploded in 2011.
-   Though anyone can propose an emoji, [Emojination](http://www.emojination.org) helps organizations and individuals create proposals. Many of these have been accepted by Unicode.
-   Jennifer shared that Chinese characters have similarities in representing objects or being combined to represent another concept.
-   Similarly, emoji can be combined to make statements of various meanings.
-   You can learn more about the similarities between emoji and Chinese in [The Hanmoji Handbook](https://hanmoji.org/).
-   Considering an emoji consisting of a couple, you can imagine almost endless possibilities of the characteristics of each partner. Accordingly, under the hood, emoji often considered a single emoji have many underlying possibilities, including skin color.
-   Next year, there will be emoji for hearts in light blue, gray, and pink. Further, there will be a wing, blackbird, and goose. There will be a flower called a Hyacinth, a jellyfish, a moose face, a donkey, ginger, a pea pod, a hair pick, and many others.

## Summing Up

In this lesson, you took a tour through the past many weeks of the course. You hypothesized how what you learned may be used inside and outside the computer sciences in the future. Further, you learned how you could continue your work in computer science beyond this class. Specifically, we discussed…

-   Computational and critical thinking
-   Abstraction and precision
-   Life after CS50
-   Testing your knowledge
-   Emoji

This was CS50!