---
title: Lab 8 - Trivia
tags: programação, cs50
use: Documentation
languages: HTML, CSS, JavaScript
dependences: CS50
---

> This material is distributed by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my understanding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Trivia](#trivia)
  - [Getting Started #](#getting-started-)
  - [Implementation Details](#implementation-details)
    - [Hints](#hints)
    - [Testing](#testing)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Submitted](#submitted)

</details>

---

# Trivia

> You are welcome to collaborate with one or two classmates on this lab, though it is expected that every student in any such group contribute equally to the lab.

Write a webpage that lets users answer trivia questions.

![screenshot of trivia questions](https://cs50.harvard.edu/x/2023/labs/8/questions.png)

## Getting Started [#](https://cs50.harvard.edu/x/2023/labs/8/#getting-started)

Started CS50x in 2021 or prior and need to migrate your work from CS50 IDE to the new VS Code codespace? Be sure to check out our instructions on how to [migrate](https://cs50.harvard.edu/x/2023/labs/8/../../new/) your files!

Open [VS Code](https://code.cs50.io/).

Start by clicking inside your terminal window, then execute `cd` by itself. You should find that its “prompt” resembles the below.

```bash
$
```

Click inside of that terminal window and then execute

```bash
wget https://cdn.cs50.net/2022/fall/labs/8/trivia.zip
```

followed by Enter in order to download a ZIP called `trivia.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!

Now execute

```bash
unzip trivia.zip
```

to create a folder called `trivia`. You no longer need the ZIP file, so you can execute

```bash
rm trivia.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd trivia
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
trivia/ $
```

If all was successful, you should execute

```bash
ls
```

and you should see an `index.html` file and a `styles.css` file.

If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Implementation Details

Design a webpage using HTML, CSS, and JavaScript to let users answer trivia questions.

1.   In `index.html`, add beneath “Part 1” a multiple-choice trivia question of your choosing with HTML.
    -   You should use an `h3` heading for the text of your question.
    -   You should have one `button` for each of the possible answer choices. There should be at least three answer choices, of which exactly one should be correct.

2.   Using JavaScript, add logic so that the buttons change colors when a user clicks on them.
    -   If a user clicks on a button with an incorrect answer, the button should turn red and text should appear beneath the question that says “Incorrect”.
    -   If a user clicks on a button with the correct answer, the button should turn green and text should appear beneath the question that says “Correct!”.

3.   In `index.html`, add beneath “Part 2” a text-based free response question of your choosing with HTML.
    -   You should use an `h3` heading for the text of your question.
    -   You should use an `input` field to let the user type a response.
    -   You should use a `button` to let the user confirm their answer.

4.   Using JavaScript, add logic so that the text field changes color when a user confirms their answer.
    -   If the user types an incorrect answer and presses the confirmation button, the text field should turn red and text should appear beneath the question that says “Incorrect”.
    -   If the user types the correct answer and presses the confirmation button, the input field should turn green and text should appear beneath the question that says “Correct!”.

5. Optionally, you may also:
    -   Edit `styles.css` to change the CSS of your webpage!
    -   Add additional trivia questions to your trivia quiz if you would like!

<details> <summary>In other words:</summary>

Part 1
> 1.1. Add a multiple choice question to the HTML page
> 1.2. Use an h3 heading for the question text
> 1.3. Use one button for each possible answer choice
> 1.4. With JavaScript, add logic so that..
>   1.4.1. When an incorrect answer choice is clicked, the button should turn red and text should appear beneath the question that says "Incorrect".
>   1.4.2. When the correct answer choice is clicked, the button should turn green and text should appear beneath the question that says "Correct!"
Part 2
> 2.1. Add a free response question to the HTML page
> 2.2. Use an h3 heading for the question text
> 2.3. Use one input for the response and a button to confirm answer 
> 2.4. With JavaScript, add logic so that..
>   2.4.1. When an incorrect answer choice is provided, the text field should turn red and text should appear beneath the question that says "Incorrect"
>   2.4.2. When the correct answer choice is provided, the text field should turn green and text should appear beneath the question that says "Correct!"

</details>

### Hints

-   Use [`document.querySelector()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) to query for a single HTML element.
-   Use [`document.querySelectorAll()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll) to query for multiple HTML elements that match a query. The function returns an array of all matching elements.
-   Use [`addEventListener()`](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener) method of the EventTarget interface sets up a function that will be called whenever the specified event is delivered to the target.


### Testing

No `check50` for this lab, as implementations will vary based on your questions! But be sure to test both incorrect and correct responses for each of your questions to ensure that your webpage responds appropriately.

Run `http-server` in your terminal while in your `lab8` directory to start a web server that serves your webpage.

## How to Submit

In your terminal, execute the below to submit your work.

```
submit50 cs50/labs/2023/x/trivia
```

---

# Walkthrough
> Full code [here](./src/trivia/index.html)

First the easy part, the HTML, I've added some classes to avoid passing the event itself with the arguments within the element. This approach is similar to the one described by Brian.

```html
<h3>Question 1: Which animal is known for "crashing" many pictures since 2009?</h3>
<button class="answer-button">elephant</button>
<button class="answer-button">bird</button>
<button class="answer-button">squirrel</button>
<button class="answer-button">cat</button>
<p id="feedback1"></p>

<!-- ... -->

<h3>Question 2: How functions break up?</h3>
<input type="text">
<button>Check Response</button>
<p id="feedback2"></p>
```
> The second one is actually a joke.

For JS though, the code ended a bit more complicated, first I've defined the two functions and then the caller based on the `DOMContentLoaded` event.

The Multiple Choice Question, selects by the `.multiple-choice` and `.answer-button` fetching all the options and creating a loop that runs *for each* element. The `isCorrect` argument is a conditional validation of `button.textContent === 'squirrel'` this avoids the need off a "correct" or "incorrect" html class.

Lastly the function changes the attribute color, so no need to alter the CSS file, and get the element (`id="feedback..."`) and change the `innerHTML` value.

```js
// TODO: Add code to check answers to questions
// Multiple Choice Question Logic
function checkMultipleChoiceAnswer(selectedButton, isCorrect) {
    let buttons = document.querySelectorAll('.multiple-choice .answer-button');
    let fb1 = document.getElementById("feedback1");

    buttons.forEach(function(button) {
        if (button === selectedButton) {
            if (isCorrect) {
                button.style.backgroundColor = 'green';
                document.querySelector('#feedback1').innerHTML = 'Correct!';
                // button.parentElement.nextElementSibling.textContent = '...';
            } else {
                button.style.backgroundColor = 'red';
                document.querySelector('#feedback1').innerHTML = 'Incorrect!';
            }
        } else {
            // Opitional: Disable a second try
            button.disabled = false;
        }
    });
}
```

> There's a possibility to fetch the html using `.getElementById('id')` but for that would require to create new variables.

For the Free Response Question, is quite the same described above but with a few additional variables, that catches the *Input*, the *Button* and the *Response*.

```js
// Free Response Question Logic
function checkFreeResponseAnswer() {
    let responseInput = document.querySelector('.free-response input');
    let responseButton = document.querySelector('.free-response button');
    let responseText = responseInput.value.trim().toLowerCase();

    if (responseText === 'because they stop calling each other') {
        responseInput.style.backgroundColor = 'green';
        document.querySelector('#feedback2').innerHTML = 'Correct!';
    } else {
        responseInput.style.backgroundColor = 'red';
        document.querySelector('#feedback2').innerHTML = 'Incorrect!';
    }

    // Opitional: Disable a second try
    //responseInput.disabled = true;
    //responseButton.disabled = true;
}
```

> **Info**
> Optionally you could disable the elements after a trial, but Brian doesn't do this so I've left it commented.

To call all of above only after the DOM load completion we need to add a *event listener* and then call the functions with the actual arguments. 

```js
document.addEventListener('DOMContentLoaded', function() {
    const multipleChoiceButtons = document.querySelectorAll('.multiple-choice .answer-button');
    multipleChoiceButtons.forEach(function(button) {
        button.addEventListener('click', function() {
            checkMultipleChoiceAnswer(this, button.textContent === 'squirrel');
        });
    });

    const freeResponseButton = document.querySelector('.free-response button');
    freeResponseButton.addEventListener('click', checkFreeResponseAnswer);
});
```

> Hope that you found the joke answer :D

## Submitted

```bash
trivia/ $ submit50 cs50/labs/2023/x/trivia
Connecting.......
Authenticating...
Verifying........
Preparing.....
Files that will be submitted:
./styles.css
./index.html
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading.......
Go to https://submit.cs50.io/users/see7e/cs50/labs/2023/x/trivia to see your results.
```

> Yes, there's no test, strange isn't it?