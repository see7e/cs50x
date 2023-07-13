---
title: Problem Set 8 - Homepage
tags: programação, cs50
use: Documentation
languages: HTML, CSS, JavaScript
dependences: CS50
---

> This material is distributed by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my understanding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Homepage](#homepage)
  - [Getting Started #](#getting-started-)
  - [Background](#background)
  - [Specification](#specification)
  - [Testing](#testing)
  - [Assessment](#assessment)
  - [Hints](#hints)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Submitted](#submitted)

</details>

---

# Homepage

Build a simple homepage using HTML, CSS, and JavaScript.

## Getting Started [#](https://cs50.harvard.edu/x/2023/psets/8/homepage/#getting-started)

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/8/homepage.zip
```

in order to download a ZIP called `homepage.zip` into your codespace.

Then execute

```bash
unzip homepage.zip
```

to create a folder called `homepage`. You no longer need the ZIP file, so you can execute

```bash
rm homepage.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd homepage
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
homepage/ $
```

Execute `ls` by itself, and you should see a few files:

```bash
index.html  styles.css
```

If you run into any trouble, follow these same steps again and see if you can determine where you went wrong! You can immediately start a server to view your site by running

```bash
http-server
```

in the terminal window. Then, command-click (if on Mac) or control-click (if on PC) on the first link that appears:

```bash
http-server running on LINK
```

Where LINK is the address of your server.

## Background

The internet has enabled incredible things: we can use a search engine to research anything imaginable, communicate with friends and family members around the globe, play games, take courses, and so much more. But it turns out that nearly all pages we may visit are built on three core languages, each of which serves a slightly different purpose:

1.  HTML, or _HyperText Markup Language_, which is used to describe the content of websites;
2.  CSS, _Cascading Style Sheets_, which is used to describe the aesthetics of websites; and
3.  JavaScript, which is used to make websites interactive and dynamic.

Create a simple homepage that introduces yourself, your favorite hobby or extracurricular, or anything else of interest to you.

## Specification

Implement in your `homepage` directory a website that must:

- [x]  Contain at least four different `.html` pages, at least one of which is `index.html` (the main page of your website), and it should be possible to get from any page on your website to any other page by following one or more hyperlinks.
- [x]  Use at least ten (10) distinct HTML tags besides `<html>`, `<head>`, `<body>`, and `<title>`. Using some tag (e.g., `<p>`) multiple times still counts as just one (1) of those ten!
- [x]  Integrate one or more features from Bootstrap into your site. Bootstrap is a popular library (that comes with lots of CSS classes and more) via which you can beautify your site. See [Bootstrap’s documentation](https://getbootstrap.com/docs/5.2/) to get started. In particular, you might find some of [Bootstrap’s components](https://getbootstrap.com/docs/5.2/components/) of interest. To add Bootstrap to your site, it suffices to include
    
    ```html
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css" integrity="sha384-TX8t27EcRE3e/ihU7zmQxVncDAy5uIKz4rEkgIXeMed4M0jlfIDPvg6uqKI2xXr2" crossorigin="anonymous">
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ho+j7jyWK8fNQe+A12Hb8AhRq26LrZ/JpcUGGOn+Y7RsweNrtN/tE3MoK7ZeZDyx" crossorigin="anonymous"></script>
    ```
    
    in your pages’ `<head>`, below which you can also include
    
    ```html
    <link href="styles.css" rel="stylesheet">
    ```
    
    to link your own CSS.
    
- [x]  Have at least one stylesheet file of your own creation, `styles.css`, which uses at least five (5) different CSS selectors (e.g. tag (`example`), class (`.example`), or ID (`#example`)), and within which you use a total of at least five (5) different CSS properties, such as `font-size`, or `margin`; and
- [x]  Integrate one or more features of JavaScript into your site to make your site more interactive. For example, you can use JavaScript to add alerts, to have an effect at a recurring interval, or to add interactivity to buttons, dropdowns, or forms. Feel free to be creative!
- [x]  Ensure that your site looks nice on browsers both on mobile devices as well as laptops and desktops.

## Testing

If you want to see how your site looks while you work on it, you can run `http-server`. Command- or control-click on the first link presented by http-server, which should open your webpage in a new tab. You should then be able to refresh the tab containing your webpage to see your latest changes.

Recall also that by opening Developer Tools in Google Chrome, you can _simulate_ visiting your page on a mobile device by clicking the phone-shaped icon to the left of **Elements** in the developer tools window, or, once the Developer Tools tab has already been opened, by typing `Ctrl`+`Shift`+`M` on a PC or `Cmd`+`Shift`+`M` on a Mac, rather than needing to visit your site on a mobile device separately!

## Assessment

No `check50` for this assignment! Instead, your site’s correctness will be assessed based on whether you meet the requirements of the specification as outlined above, and whether your HTML is well-formed and valid. To ensure that your pages are, you can use this [Markup Validation Service](https://validator.w3.org/#validate_by_input), copying and pasting your HTML directly into the provided text box. Take care to eliminate any warnings or errors suggested by the validator before submitting!

Consider also:

-   whether the aesthetics of your site are such that it is intuitive and straightforward for a user to navigate;
-   whether your CSS has been factored out into a separate CSS file(s); and
-   whether you have avoided repetition and redundancy by “cascading” style properties from parent tags.

Afraid `style50` does not support HTML files, and so it is incumbent upon you to indent and align your HTML tags cleanly. Know also that you can create an HTML comment with:

```html
<!-- Comment goes here -->
```

but commenting your HTML code is not as imperative as it is when commenting code in, say, C or Python. You can also comment your CSS, in CSS files, with:

```css
/* Comment goes here */
```

## Hints

For fairly comprehensive guides on the languages introduced in this problem, check out these tutorials:

-   [HTML](https://www.w3schools.com/html/)
-   [CSS](https://www.w3schools.com/css/)
-   [JavaScript](https://www.w3schools.com/js/)

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/homepage
```

---

# Walkthrough
> HomePage Index [here](./src/homepage/index.html)

As you know, I'm a bit lasy, so the sites reflect the exercises of this week.

- HomePage index
- RadioShack Redo
- Trivia!

I've used some concepts of the Lecture and the Lab, to build the same Navbar Header, to keep a pattern style that links all of the pages as requested.
## Result

```bash
Index of /
(drwxr-xr-x)	13-jul.-2023 14:53		radio1996/
(drwxr-xr-x)	13-jul.-2023 14:53		radio1997/
(drwxr-xr-x)	13-jul.-2023 14:53		radiotoday/
(-rw-r--r--)	13-jul.-2023 14:53	7.3k	index.html
(-rw-r--r--)	13-jul.-2023 14:53	2.6k	styles.css
(-rw-r--r--)	13-jul.-2023 14:53	6.9k	trivia.html

Node.js v20.3.1/ http-server server running @ localhost
```

## Submitted

```bash
homepage/ $ submit50 cs50/problems/2023/x/homepage
Connecting.........
Authenticating...
Verifying........
Preparing.....
Files that will be submitted:
./index.html
./radio1997/src/steve_logo.gif
./radio1997/src/wall.gif
./radio1997/src/storelocator_logo.gif
./radio1997/src/2_dots.gif
./radio1997/src/family_radio.gif
./radio1997/src/srevices_logo.gif
./radio1997/src/dth_sat.gif
./radio1997/src/anmclr.gif
./radio1997/src/cellular.gif
./radio1997/src/img_40f7b7a4.gif
./radio1997/src/75.gif
./radio1996/src/big_rgrey1.gif
./styles.css
./radio1997/src/dot_clear.gif
./radio1997/index.html
./radio1997/src/about_logo.gif
./radio1997/src/computer.gif
./radio1996/src/mclogo.gif
./trivia.html
./radiotoday/src/radioshack-logo.png
./radio1996/src/rsfetur2.gif
./radio1997/src/you_got.gif
./radiotoday/index.html
./radio1997/src/1_dots.gif
./radio1997/src/repair_logo.gif
./radio1996/index.html
./radio1997/src/support_logo.gif
./radio1997/src/red_ball_2.gif
./radio1997/src/sun.jpeg
./radio1997/src/radioshack.gif
./radio1996/src/longall.gif
./radio1997/src/new_Sizz.gif
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading.......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/homepage to see your results.
```