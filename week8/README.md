---
title: CS50 - Week 8
tags: programming, cs50
use: Documentation
languages: HTML, CSS, JS
dependences: CS50
---

> This material is distribured by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my undersantding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Lecture 8](#lecture-8)
	- [Welcome! #](#welcome-)
	- [Routers](#routers)
	- [DNS](#dns)
	- [HTTP](#http)
	- [HTML](#html)
		- [Structure](#structure)
		- [Paragraphs](#paragraphs)
		- [Headers](#headers)
		- [Lists / Tables](#lists--tables)
		- [Images / Videos](#images--videos)
		- [Links](#links)
		- [The Head - Meta](#the-head---meta)
	- [CSS](#css)
	- [Frameworks](#frameworks)
	- [JavaScript](#javascript)
	- [Summing Up](#summing-up)
- [Section](#section)
- [Shorts](#shorts)
	- [Internet Primer](#internet-primer)
	- [IP](#ip)
	- [TCP](#tcp)
	- [HTTP](#http-1)
	- [HTML](#html-1)
	- [CSS](#css-1)
	- [JavaScript](#javascript-1)
	- [DOM](#dom)
- [Exercises](#exercises)
	- [Practice Problems](#practice-problems)
	- [Lab 8: Trivia](#lab-8-trivia)
	- [Problem Set 8](#problem-set-8)
	- [What to Do](#what-to-do)

</details>

---

# Lecture 8

<details>
<summary>Keywords, lookup in <a href="./src/transcripts/lecture8.md">transcript</a></summary>

- IP, address
- envelope
- http/s
- reassemble
- protocols
- dns
- domain
- top level domain
- local cache
- application level protocol
- path
- tld
- network > headers
- status code
- curl
- user input
- server, request, response
- tag
- attribute, content
- hierarchy
- embed
- viewport
- responsive
- elements (console)
- selector
- entities
- semantic tags
- classes
- frameworks
- bootstrap
- client-side, server-side
- events, listener
- factoring
- camelcase

</details>

## Welcome! [#](https://cs50.harvard.edu/x/2023/notes/8/#welcome)

In previous weeks, we introduced you to Python, a high-level programming language that utilized the same building blocks we learned in C. Today, we will extend those building blocks further in HTML, CSS, and JavaScript.

The internet is a technology that we all use. The _ARPANET_ connected the first points on the internet to one another.

Using our skills from previous weeks, we can build our own web pages and applications.


## Routers

To route data from one place to another, we need to make _routing decisions_. That is, someone needs to program how data is transfered from point A to point B.

You can imagine how data could take multiple paths from point A and point B, such that when a router is congested, data can flow through another path.

_TCP/IP_ are two protocols that allow computers to transfer data between them over the internet.

_IP_ or _internet protocol_ is a way by which computers can identify one another across the internet. Every computer has a unique address in the world. Addresses are in this form:

```
  #.#.#.#
```

Numbers range from `0` to `255`. IP addresses are 32-bits, meaning that these addresses could accommodate over 4 billion addresses. Newer versions of IP addresses can accommodate far more computers!

In the real world, servers do a lot of work for us.

_TCP_, or transmission control protocol, is used to distinguish web services from one another. For example, `80` is used to denote HTTP and `443` is used to denote HTTPS. These numbers are _port numbers_.

When information is sent from one location to another, an IP address and TCP port number are sent.

These protocols are also used to fragment large files into multiple parts called _packets_. For example, a large photo of a cat can be sent in multiple packets. When a packet is lost, TCP/IP can request missing packets again from the origin server.

TCP will acknowledge when all the data has been transmitted and received.

## DNS

It would be very tedious if you needed to remember an address number to visit a website.

_DNS_, or _domain name systems_, is a collection of servers on the internet that are used to route website addresses like "`harvard.edu`" to a specific IP address.

DNS simply hold a table or database that links specific, fully qualified domain names to specific IP addresses.

## HTTP

*HTTP* or _hypertext transfer protocol_ is an application-level protocol that developers use to build powerful and useful things.

When you see an address such as `https://www.example.com` you are actually implicitly visiting that address with a `/` at the end of it.

The _path_ is what exists after that slash. For example, `https://www.example.com/folder/file.html` visits `example.com` and browses to the `folder` folder and then visits the file named `file.html`.

`https` in this address is the protocol that is used to connect to that web address. By protocol, we mean that HTTP utilizes `GET` or `POST` _requests_ to ask for information from a server. For example, you can launch Google Chrome, right-click, and click `inspect`. When you open the `developer tools` and visit `Network`, selecting `Preserve log`, you will see `Request Headers`. You’ll see mentions of `GET`. This is possible in other browsers as well, using slightly different methods.

Generally, after making a request a server, you will receive the following in `Response Headers`:

```
  HTTP/1.1 200 OK
  Content-Type: text/html
```

This approach to inspecting these logs may be a bit more complicated than need be. You can analyze the work of HTTP protocols at [code.cs50.io](https://code.cs50.io). For example, type the following in your terminal window:

```
  curl -I https://www.harvard.edu
```

The output of this command returns all the header values of the **responses of the server** alongside the `200` status code.

-   Similarly, execute the following in your terminal window:
    
    ```
      curl -I http://www.harvard.edu
    ```

Notice that the `s` in `https` has been removed. The server response will show that the response is `301` instead of `200`, meaning that the website has permanently moved. The browser "knows" that with this code (`301`), it should redirect to the next page by the **Location header** info. 

-   Further, execute the following command in your terminal window:
    
    ```
      curl -I https://harvard.edu
    ```
    
    Notice that you will see the same `301` response, providing a hint to a browser of where it can find the correct website.
    

Similar to `301`, a code of `404` means that a specified URL has not been found. There are numerous other response codes, such as:

```
  200 OK
  301 Moved Permanently
  302 Found
  304 Not Modified
  304 Temporary Redirect
  401 Unauthorized
  403 Forbidden
  404 Not Found
  418 I'm a Teapot
  500 Internal Server Error
  503 Service Unavailable
```

-   It’s worth mentioning that `500` errors are always your fault as the developer. This will be especially important for next week’s pset, and potentially for your final project!

We can send more complicated commands to the server. For example, we can attempt the following:

```
  GET /search?q=cats HTTP/1.1
  Host: www.google.com
```

Notice that not only are we specifying a path but also user input using the `?` mark. `q` is used to denote _query_, passing `cats` to it.

If you manually type `google.com/search?=cats` into your web browser address bar, it will manually query Google for results related to `cats`.

## HTML

_HTML_ or _hypertext markup language_ is made up of _tags_, each of which may have some _attributes_ that describe it.

### Structure

In your terminal, type `code hello.html` and write code as follows:

```html
<!DOCTYPE html>

<!-- Demonstrates HTML -->

<html lang="en">
	<head>
		<title>hello, title</title>
	</head>
	<body>
		hello, body
	</body>
</html>
```

Notice that:
- the `html` tag both opens and closes this file
- the `lang` attribute, which modifies the behaviour of the `html` tag
- there are both `head` tags and `body` tags. 

Indentation is not required but does suggest a hierarchy. The html source code of a page can be then condensed, usually called minimal, for size purposes.

You can serve your code by typing `http-server`. This serve is now available on a very long URL. If you click it, you can visit the website with your own code.

When you visit this URL, notice that the file name `hello.html` appears at the end of this URL.

The hierarchy of tags can be represented as follows:

![html code next to a heirarchy showing parent and child nodes](https://cs50.harvard.edu/x/2023/notes/8/cs50Week8Slide065.png "DOM")

The browser will read your HTML file top to bottom and left to right.

### Paragraphs 

Because whitespace is effectively ignored in HTML, you will need to use `<p>` paragraph tags to open and close a paragraph. Consider the following:

```html
<!DOCTYPE html>

<!-- Demonstrates paragraphs -->

<html lang="en">
	<head>
		<title>paragraphs</title>
	</head>
	<body>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus convallis scelerisque quam, vel hendrerit lectus viverra eu. Praesent posuere eget lectus ut faucibus. Etiam eu velit laoreet, gravida lorem in, viverra est. Cras ut purus neque. In porttitor non lorem id lobortis. Mauris gravida metus libero, quis maximus dui porta at. Donec lacinia felis consectetur venenatis scelerisque. Nulla eu nisl sollicitudin, varius velit sit amet, vehicula erat. Curabitur sollicitudin felis sit amet orci mattis, a tempus nulla pulvinar. Aliquam erat volutpat.
		</p>
		<p>
			Mauris ut dui in eros semper hendrerit. Morbi vel elit mi. Sed sit amet ex non quam dignissim dignissim et vel arcu. Pellentesque eget elementum orci. Morbi ac cursus ex. Pellentesque quis turpis blandit orci dapibus semper sed non nunc. Nulla et dolor nec lacus finibus volutpat. Sed non lorem diam. Donec feugiat interdum interdum. Vivamus et justo in enim blandit fermentum vel at elit. Phasellus eu ante vitae ligula varius aliquet. Etiam id posuere nibh.
		</p>
		<p>
			Aenean venenatis convallis ante a rhoncus. Nullam in metus vel diam vehicula tincidunt. Donec lacinia metus sem, sit amet egestas elit blandit sit amet. Nunc egestas sem quis nisl mattis semper. Pellentesque ut magna congue lorem eleifend sodales. Donec tortor tortor, aliquam vitae mollis sed, interdum ut lectus. Mauris non purus quis ipsum lacinia tincidunt.
		</p>
		<p>
			Integer at justo lacinia libero blandit aliquam ut ut dui. Quisque tincidunt facilisis venenatis. Nullam dictum odio quis lorem luctus, vel malesuada dolor luctus. Aenean placerat faucibus enim a facilisis. Maecenas eleifend quis massa sed eleifend. Ut ultricies, dui ac vulputate hendrerit, ex metus iaculis diam, vitae fermentum libero dui et ante. Phasellus suscipit, arcu ut consequat sagittis, massa urna accumsan massa, eu aliquet nulla lorem vitae arcu. Pellentesque rutrum felis et metus porta semper. Nam ac consectetur mauris.
		</p>
		<p>
			Suspendisse rutrum vestibulum odio, sed venenatis purus condimentum sed. Morbi ornare tincidunt augue eu auctor. Vivamus sagittis ac lectus at aliquet. Nulla urna mauris, interdum non nibh in, vehicula porta enim. Donec et posuere sapien. Pellentesque ultrices scelerisque ipsum, vel fermentum nibh tincidunt et. Proin gravida porta ipsum nec scelerisque. Vestibulum fringilla erat at turpis laoreet, nec hendrerit nisi scelerisque.
		</p>
		<p>
			Sed quis malesuada mi. Nam id purus quis augue sagittis pharetra. Nulla facilisi. Maecenas vel fringilla ante. Cras tristique, arcu sit amet blandit auctor, urna elit ultricies lacus, a malesuada eros dui id massa. Aliquam sem odio, pretium vel cursus eget, scelerisque at urna. Vestibulum posuere a turpis consectetur consectetur. Cras consequat, risus quis tempor egestas, nulla ipsum ornare erat, nec accumsan nibh lorem nec risus. Integer at iaculis lacus. Integer congue nunc massa, quis molestie felis pellentesque vestibulum. Nulla odio tortor, aliquam nec quam in, ornare aliquet sapien.
		</p>
	</body>
</html>
```

Notice that paragraphs start with a `<p>` tag and end with a `</p>` tag.

### Headers

HTML allows for the representation of headings:

```html
<!DOCTYPE html>

<!-- Demonstrates headings (for chapters, sections, subsections, etc.) -->

<html lang="en">
	
	<head>
		<title>headings</title>
	</head>
		
	<body>
		
		<h1>One</h1>
		<p>
			Lorem ipsum dolor [...].
		</p>
		
		<h2>Two</h2>
		<p>
			Mauris ut dui in eros semper hendrerit [...].
		</p>
		
		<h3>Three</h3>
		<p>
			Aenean venenatis convallis ante a rhoncus [...].
		</p>
		
		<h4>Four</h4>
		<p>
			Integer at justo lacinia libero blandit aliquam [...].
		</p>
		
		<h5>Five</h5>
		<p>
			Suspendisse rutrum vestibulum odio, sed venenatis purus condimentum sed. Morbi ornare tincidunt augue eu auctor [...].
		</p>
		
		<h6>Six</h6>
		<p>
			Sed quis malesuada mi [...].
		</p>

	</body>

</html>
```

Notice that `<h1>`, `<h2>`, and `<h3>` denote different levels of headings.
> I've compressed the paragraph texts to simplify (I don't like repetitive things), but you can maintain to see the hole block.

### Lists / Tables

We can also create lists within HTML:

```html
<!DOCTYPE html>

<!-- Demonstrates (ordered) lists -->

<html lang="en">
	<head>
		<title>list</title>
	</head>
	<body>
		<ol>
			<li>foo</li>
			<li>bar</li>
			<li>baz</li>
		</ol>
	</body>
</html>
```

Notice that the `<ol>` tag creates an ordered list containing three items.

We can also create a table in HTML:

```html
<!DOCTYPE html>

<!-- Demonstrates table -->

<html lang="en">
	<head>
		<title>table</title>
	</head>
	<body>
		<table>
			<tr>
				<td>1</td>
				<td>2</td>
				<td>3</td>
			</tr>
			<tr>
				<td>4</td>
				<td>5</td>
				<td>6</td>
			</tr>
			<tr>
				<td>7</td>
				<td>8</td>
				<td>9</td>
			</tr>
			<tr>
				<td>*</td>
				<td>0</td>
				<td>#</td>
			</tr>
		</table>
	</body>
</html>
```

Tables also have tags that open and close each element within.

### Images / Videos

Images can also be utilized within HTML:

```html
<!DOCTYPE html>

<!-- Demonstrates image -->

<html lang="en">
	<head>
		<title>image</title>
	</head>
	<body>
		<!-- https://www.harvard.edu/ -->
		<img alt="Harvard University" src="harvard.jpg">
	</body>
</html>
```

Notice that `src="harvard.jpg"` indicates the path where the image file can be located. The `alt=""` is used for many Text to Speech applications, and even if the browser can't load the file for any specific reason the text will be displayed in place.

Videos can also be included in HTML:

```html
<!DOCTYPE html>

<!-- Demonstrates video -->

<html lang="en">
	<head>
		<title>video</title>
	</head>
	<body>
		<!-- https://www.harvard.edu/ -->
		<video autoplay loop muted playsinline width="1280">
			<source src="halloween.mp4" type="video/mp4">
		</video>
	</body>
</html>
```

Notice that the `width` attribute defines the width of the video.

### Links 

You can also link between various web pages:

```HTML
<!DOCTYPE html>

<!-- Demonstrates link -->

<html lang="en">
	<head>
		<title>link</title>
	</head>
	<body>
	   Visit <a href="image.html">Harvard</a>.
	</body>
</html>
```

Notice that the `<a>` or _anchor_ tag is used to make `Harvard` a linkable text.

### The Head - Meta

Meta tags are used to hold information about the data within the HTML file. Consider the following:

```html
<!DOCTYPE html>

<!-- Demonstrates responsive design -->

<html lang="en">
	<head>
		<meta name="viewport" content="initial-scale=1, width=device-width">
		<title>meta</title>
	</head>
	<body>
		Lorem ipsum dolor sit amet, consectetur adipiscing elit [...].
	</body>
</html>
```

Notice this set of `meta` attributes makes this page mobile-friendly.

There are numerous `meta` key-value pairs that you can use:

```html
<!DOCTYPE html>

<!-- Demonstrates Open Graph tags -->

<html lang="en">
	<head>
		<meta property="og:title" content="CS50">
		<meta property="og:description" content="Introduction to the intellectual enterprises of computer science and the art of programming.">
		<meta property="og:image" content="cat.jpg">
		<title>meta</title>
	</head>
	<body>
		...
	</body>
</html>
```

Notice that these key value pairs relate to the `title` and `description` of the web page.

You can also create forms reminiscent of Google’s search:

```html
<!DOCTYPE html>

<!-- Demonstrates form -->

<html lang="en">
	<head>
		<title>search</title>
	</head>
	<body>
		<form action="https://www.google.com/search" method="get">
			<input name="q" type="search">
			<input type="submit" value="Google Search">
		</form>
	</body>
</html>
```

Notice that a `form` tag opens and provides the attribute of what `action` it will take. The `input` field is included, passing the name `q` and the type as `search`.

We can make this search better as follows:

```html
<!DOCTYPE html>

<!-- Demonstrates additional form attributes -->

<html lang="en">
	<head>
		<title>search</title>
	</head>
	<body>
		<form action="https://www.google.com/search" method="get">
			<input autocomplete="off" autofocus name="q" placeholder="Query" type="search">
			<button>Google Search</button>
		</form>
	</body>
</html>
```

Notice that `autocomplete` is turned `off`. `autofocus` is enabled.

-   We’ve seen just a few of many HTML elements you can add to your site. If you have an idea for something to add to your site that we haven’t seen yet (a button, an audio file, etc.) try Googling “X in HTML” to find the right syntax!

## CSS

`CSS`, or _cascading style sheet_, is a markup language that allows you to fine-tune the aesthetics of your HTML files.
In your terminal, type `code home.html` and write code as follows:

```html
<!DOCTYPE html>

<!-- Demonstrates inline CSS with P tags -->

<html lang="en">
	<head>
		<title>css</title>
	</head>
	<body>
		<!-- Header -->
		<p style="font-size: large; text-align: center;">
			John Harvard
		</p>
		<!-- Main -->
		<p style="font-size: medium; text-align: center;">
			Welcome to my home page!
		</p>
		<!-- Footer -->
		<p style="font-size: small; text-align: center;">
			Copyright &#169; John Harvard
		</p>
	</body>
</html>
```

Notice that some `style` attributes are provided to the `<p>` tags. The `font-size` is set to `large`, `medium`, or `small`. Then `text-align` is set to center.

While correct, the above is not well-designed. We can remove **redundancy** by modifying our code as follows:

```html
<!DOCTYPE html>

<!-- Create DIVs -->

<html lang="en">
	<head>
		<title>css</title>
	</head>
	<body style="text-align: center">
		<div style="font-size: large">
			John Harvard
		</div>
		<div style="font-size: medium">
			Welcome to my home page!
		</div>
		<div style="font-size: small">
			Copyright &#169; John Harvard
		</div>
	</body>
</html>
```

> Always remember, a repetitive and hard code element is difficult to give maintenance.   

Notice that `<div>` tags are used to divide up this HTML file into specific regions. `text-align: center` is invoked on the entire body of the HTML file. **CSS uses the principle of inheritance**, a child will receive the attributes of their parent (if it wasn't overwritten).

It turns out that there is newer **semantic text** that is included in HTML. We can modify our code as follows:

```html
<!DOCTYPE html>

<!-- Uses semantic tags instead of DIVs -->

<html lang="en">
	<head>
		<title>css</title>
	</head>
	<body style="text-align: center">
		<header style="font-size: large">
			John Harvard
		</header>
		<main style="font-size: medium">
			Welcome to my home page!
		</main>
		<footer style="font-size: small">
			Copyright &#169; John Harvard
		</footer>
	</body>
</html>
```

Notice that the `header` and `footer` both have different styles assigned to them.

This practice of placing the style and information all in the same location is not good practice. We could move the elements of style to the top of the file as follows:

```html
<!-- Demonstrates class selectors -->

<html lang="en">
	<head>
		<style>
			
			.centered
			{
				text-align: center;
			}
			
			.large
			{
				font-size: large;
			}
			
			.medium
			{
				font-size: medium;
			}
			
			.small
			{
				font-size: small;
			}
		
		</style>
		<title>css</title>
	</head>
	<body class="centered">
		<header class="large">
			John Harvard
		</header>
		<main class="medium">
			Welcome to my home page!
		</main>
		<footer class="small">
			Copyright &#169; John Harvard
		</footer>
	</body>
</html>
```

Notice all the style tags are placed up in the `head` in the `style` tag wrapper. Also notice that we’ve assigned _classes_, called `centered`, `large`, `medium`, and `small` to our elements, and that we select those classes by placing a dot before the name, as in `.centered`

It turns out that we can move all our style code into a special file called a _CSS_ file. We can create a file called `style.css` and paste our classes there:

```css
.centered
{
	text-align: center;
}

.large
{
	font-size: large;
}

.medium
{
	font-size: medium;
}

.small
{
	font-size: small;
}
```

Notice that this is verbatim what appeared in our HTML file.

We then can tell the browser where to locate the CSS for this HTML file:

```html
<!DOCTYPE html>

<!-- Demonstrates external stylesheets -->

<html lang="en">
	<head>
		<link href="style.css" rel="stylesheet">
		<title>css</title>
	</head>
	<body class="centered">
		<header class="large">
			John Harvard
		</header>
		<main class="medium">
			Welcome to my home page!
		</main>
		<footer class="small">
			Copyright &#169; John Harvard
		</footer>
	</body>
</html>
```

Notice that `style.css` is linked to this HTML file as a stylesheet, telling the browser where to locate the styles we created.


## Frameworks

Similar to third-party libraries we can leverage in Python, there are third-party libraries called _frameworks_ that we can utilize with our HTML files.

_Bootstrap_ is one of these frameworks that we can use to beautify our HTML and easily perfect design elements such that our pages are more readable. Can be utilized by adding the following link tag in the head of your html file:

```html
<head>
	<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-Zenh87qX5JnK2Jl0vWa8Ck2rdkQ2Bzep5IDxbcnCeuOxjzrPF/et3URy9Bv1WTRi" crossorigin="anonymous">
	<title>favorites</title>
</head>
```
> This is the minimal version, so if you decide to lookup the code, it will be condensed entirely, to save space and processing.

The `integrity=""` and `crossorigin=""` refers to the connection type to the server where the file is stored, in this case [cdn.jsdelivr.net](cdn.jsdelivr.net).

-   You can learn more about this in the [Bootstrap Documentation](https://getbootstrap.com/docs/4.1/getting-started/introduction/).

## JavaScript

> [!IMPORTANT]  
> This course utilizes Bootstrap and some [JQuery](https://jquery.com/) functions. Is important to know that since `v5.0` of Bootstrap, [JQuery dependencies were dropped](https://getbootstrap.com/docs/5.3/migration/#javascript).

JavaScript is another programming language that allows for interactivity within web pages.
-   supports conditionals:
    
    ```js
    if (x < y)
    {
    
    }
    else
    {
    
    }
    ```
    
-   Variables are also supported:
    
    ```js
    let counter = 0;
    ```
    
-   You can also increment:
    
    ```js
    counter++
    ```
    
-   Loops are very similar to what you have seen before in C:
    
    ```js
    for (let i = 0; i < 3; i++)
    {
    
    }
    ```
    

JavaScript allows you to dynamically read and modify the html document loaded into memory such that the user need not reload to see changes.

The selectors belong to a JS library called **JQuery**.
> It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript.

-   Consider the following HTML:
    
    ```html
    <!DOCTYPE html>
    
    <!-- Demonstrates programmatic changes to style -->
    
    <html lang="en">
        <head>
            <title>background</title>
        </head>
        <body>
            <button id="red">R</button>
            <button id="green">G</button>
            <button id="blue">B</button>
            <script>
            
                let body = document.querySelector('body');
                document.querySelector('#red').addEventListener('click', function() {
                    body.style.backgroundColor = 'red';
                });
                document.querySelector('#green').addEventListener('click', function() {
                    body.style.backgroundColor = 'green';
                });
                document.querySelector('#blue').addEventListener('click', function() {
                    body.style.backgroundColor = 'blue';
                });
    
            </script>
        </body>
    </html>
    ```

Notice that JavaScript listens for when a specific button is clicked. Upon such a click, certain style attributes on the page are changed. `body` is defined as the body of the page. Then, an event listener waits for the clicking of one of the buttons. Then, the `body.style.backgroundColor` is changed.

-   Similarly, consider the following:
    
    ```html
    <!DOCTYPE html>
    
    <html lang="en">
        <head>
            <script>
    
                // Toggles visibility of greeting
                function blink()
                {
                    let body = document.querySelector('body');
                    if (body.style.visibility == 'hidden')
                    {
                        body.style.visibility = 'visible';
                    }
                    else
                    {
                        body.style.visibility = 'hidden';
                    }
                }
    
                // Blink every 500ms
                window.setInterval(blink, 500);
    
            </script>
            <title>blink</title>
        </head>
        <body>
            hello, world
        </body>
    </html>
    ```
    
    This example blinks a text at a set interval. Notice that `window.setInterval` takes in two arguments: 1) A function to be called and 2) a wait period (in milliseconds) between function calls.
    
-   Consider the following:
    
    ```html
    <!DOCTYPE html>
    
    <html lang="en">
    
        <head>
            <title>autocomplete</title>
        </head>
    
        <body>
    
            <input autocomplete="off" autofocus placeholder="Query" type="text">
    
            <ul></ul>
    
            <script src="large.js"></script>
            <script>
    
                let input = document.querySelector('input');
                input.addEventListener('keyup', function(event) {
                    let html = '';
                    if (input.value) {
                        for (word of WORDS) {
                            if (word.startsWith(input.value)) {
                                html += `<li>${word}</li>`;
                            }
                        }
                    }
                    document.querySelector('ul').innerHTML = html;
                });
    
            </script>
    
        </body>
    </html>
    ```
    
    This is a JavaScript implementation of autocomplete.
    
-   Interestingly, we can also geolocate using JavaScript:
    
    ```html
    <!DOCTYPE html>
    
    <html lang="en">
        <head>
            <title>geolocation</title>
        </head>
        <body>
            <script>
    
                navigator.geolocation.getCurrentPosition(function(position) {
                    document.write(position.coords.latitude + ", " + position.coords.longitude);
                });
    
            </script>
        </body>
    </html>
    ```
    
    Notice that `navigator.geolocation` is used to `getCurrentPosition`. This will not work if your computer or browser does not allow for location tracking.
    
-   The capabilities of JavaScript are many and can be found in the [JavaScript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript).

## Summing Up

In this lesson, you learned how to create your own HTML files, style them, leverage third-party frameworks, and utilize JavaScript. Specifically, we discussed…

-   TCP/IP
-   DNS
-   HTML
-   CSS
-   Frameworks
-   JavaScript

See you next time!

---
# Section 
> [Transcript](./src/transcripts/section8.md)

- HTTP
	Are the rules that define how the computers should interact within the internet. 

- HTML
	Is the structure that translates to the type of the page itself, is constructed as a Tree (DOM), where the document have the different elements. 

- CSS
	Represents the styles that could be applied to each element of the document. Works with a cascade principle, using inheritance as the tree of the DOM.

- JavaScript
	Actual programming language, that manipulates the DOM tree and do some fun stuff.

---

# Shorts

## Internet Primer 
> [Transc](./src/transcripts/shorts8_internet.md)

## IP
> [Transc](./src/transcripts/shorts8_ip.md)


## TCP
> [Transc](./src/transcripts/shorts8_tcp.md)


## HTTP 
> [Transc](./src/transcripts/shorts8_http.md)


## HTML
> [Transc](./src/transcripts/shorts8_html.md)


## CSS
> [Transc](./src/transcripts/shorts8_css.md)


## JavaScript
> [Transc](./src/transcripts/shorts8_js.md)

## DOM
> [Transc](./src/transcripts/shorts8_dom.md)


---

# Exercises

## Practice Problems

In addition to this week’s lab and problem set, you’re welcome to try any of these (optional!) practice problems:

-   Radio Shack [Redo](./redo.md) [#](https://cs50.harvard.edu/x/2023/problems/8/redo/), for practice with Bootstrap (and some web development history!)

## [Lab 8: Trivia](./lab8.md)
> Full code [here](./src/trivia/index.html)

## Problem Set 8

> Collaboration on problem sets is not permitted except to the extent that you may ask classmates and others for help so long as that help does not reduce to another doing your work for you, per the course’s policy on [academic honesty](https://cs50.harvard.edu/x/2023/psets/8/../../syllabus/#academic-honesty).
>
> The staff conducts random audits of submissions to CS50x. Students found to be in violation of this policy will be removed from the course. Students who have already completed CS50x, if found to be in violation, will have their CS50 Certificate permanently revoked.

## What to Do

Be sure you have completed [Lab 8](./lab8.md) [#](https://cs50.harvard.edu/x/2023/psets/8/../../labs/8/) before beginning this problem set.

1.  Log into [code.cs50.io](https://code.cs50.io) using your GitHub account
2.  Run `update50` in your codespace’s terminal window to ensure your codespace is up-to-date and, when prompted, click **Rebuild now**
3.  Submit [Homepage](./homepage.md) [#](https://cs50.harvard.edu/x/2023/psets/8/homepage/)