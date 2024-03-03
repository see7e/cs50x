---
title: Lab 9 - Birthdays
tags: programação, cs50
use: Documentation
languages: Flask
dependences: CS50
---

> This material is distributed by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my understanding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Lab 9: Birthdays](#lab-9-birthdays)
  - [Getting Started #](#getting-started-)
  - [Understanding](#understanding)
  - [Implementation Details](#implementation-details)
    - [Hints](#hints)
    - [Testing](#testing)
  - [How to Submit](#how-to-submit)
- [Walkthrough](#walkthrough)
  - [Log Trace](#log-trace)
  - [Submitted](#submitted)

</details>

---

# Lab 9: Birthdays

You are welcome to collaborate with one or two classmates on this lab, though it is expected that every student in any such group contribute equally to the lab.

Create a web application to keep track of friends’ birthdays.

![screenshot of birthdays website](https://cs50.harvard.edu/x/2023/labs/9//birthdays.png)

## Getting Started [#](https://cs50.harvard.edu/x/2023/labs/9/#lab-9-birthdays#getting-started)

Started CS50x in 2021 or prior and need to migrate your work from CS50 IDE to the new VS Code codespace? Be sure to check out our instructions on how to [migrate](https://cs50.harvard.edu/x/2023/labs/9/#lab-9-birthdays../../new/) your files!

Open [VS Code](https://code.cs50.io/).

Start by clicking inside your terminal window, then execute `cd` by itself. You should find that its “prompt” resembles the below.

```bash
$
```

Click inside of that terminal window and then execute

```bash
wget https://cdn.cs50.net/2022/fall/labs/9/birthdays.zip
```

followed by Enter in order to download a ZIP called `birthdays.zip` in your codespace. Take care not to overlook the space between `wget` and the following URL, or any other character for that matter!

Now execute

```bash
unzip birthdays.zip
```

to create a folder called `birthdays`. You no longer need the ZIP file, so you can execute

```bash
rm birthdays.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd birthdays
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
birthdays/ $
```

If all was successful, you should execute

```bash
ls
```

and you should see the following files and folders:

```bash
app.py  birthdays.db  static/  templates/
```

If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!


## Understanding

In `app.py`, you’ll find the start of a Flask web application. The application has one route (`/`) that accepts both `POST` requests (after the `if`) and `GET` requests (after the `else`). Currently, when the `/` route is requested via `GET`, the `index.html` template is rendered. When the `/` route is requested via `POST`, the user is redirected back to `/` via `GET`.

`birthdays.db` is a SQLite database with one table, `birthdays`, that has four columns: `id`, `name`, `month`, and `day`. There are a few rows already in this table, though ultimately your web application will support the ability to insert rows into this table!

In the `static` directory is a `styles.css` file containing the CSS code for this web application. No need to edit this file, though you’re welcome to if you’d like!

In the `templates` directory is an `index.html` file that will be rendered when the user views your web application.

## Implementation Details

Complete the implementation of a web application to let users store and keep track of birthdays.

-   When the `/` route is requested via `GET`, your web application should display, in a table, all of the people in your database along with their birthdays.
    -   First, in `app.py`, add logic in your `GET` request handling to query the `birthdays.db` database for all birthdays. Pass all of that data to your `index.html` template.
    -   Then, in `index.html`, add logic to render each birthday as a row in the table. Each row should have two columns: one column for the person’s name and another column for the person’s birthday.
-   When the `/` route is requested via `POST`, your web application should add a new birthday to your database and then re-render the index page.
    -   First, in `index.html`, add an HTML form. The form should let users type in a name, a birthday month, and a birthday day. Be sure the form submits to `/` (its “action”) with a method of `post`.
    -   Then, in `app.py`, add logic in your `POST` request handling to `INSERT` a new row into the `birthdays` table based on the data supplied by the user.

Optionally, you may also:

-   Add the ability to delete and/or edit birthday entries.
-   Add any additional features of your choosing!

### Hints

-   Recall that you can call `db.execute` to execute SQL queries within `app.py`.
    -   If you call `db.execute` to run a `SELECT` query, recall that the function will return to you a list of dictionaries, where each dictionary represents one row returned by your query.
-   You’ll likely find it helpful to pass in additional data to `render_template()` in your `index` function so that access birthday data inside of your `index.html` template.
-   Recall that the `tr` tag can be used to create a table row and the `td` tag can be used to create a table data cell.
-   Recall that, with Jinja, you can create a [`for` loop](https://jinja.palletsprojects.com/en/2.11.x/templates/#for) inside your `index.html` file.
-   In `app.py`, you can obtain the data `POST`ed by the user’s form submission via `request.form.get(field)` where `field` is a string representing the `name` attribute of an `input` from your form.
    -   For example, if in `index.html`, you had an `<input name="foo" type="text">`, you could use `request.form.get("foo")` in `app.py` to extract the user’s input.

### Testing

No `check50` for this lab! But be sure to test your web application by adding some birthdays and ensuring that the data appears in your table as expected.

Run `flask run` in your terminal while in your `birthdays` directory to start a web server that serves your Flask application.

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/labs/2023/x/birthdays
```

---

# Walkthrough
> HTML code [here](./src/birthdays/templates/index.html)
> Python code [here](./src/birthdays/app.py)

In `index.html`, tree simple inputs for the Name, Month and Day, and another one for the form submission. Could have used Jinja for construction but isn't effective for only three elements.

```html
<h2>Add a Birthday</h2>
<!-- TODO: Create a form for users to submit a name, a month, and a day -->
<form action="/" method="post">
    <input type="text" id="name" name="name" placeholder="Name" required>
    <input type="text" id="month" name="month" placeholder="Month" required>
    <input type="text" id="day" name="day" placeholder="Day" required>
    <input type="submit" value="Add Birthday">
</form>
```

Contrary to the previous situation, for the presentation of the information in the Database file, I've used a loop to add in each row the values returned by the query.

```html
<tbody>
    <!-- Loop through the database entries to display them in this table -->
    {% for birthday in birthdays %}
    <tr>
        <td>{{ birthday.name }}</td>
        <td>{{ birthday.month }}/{{ birthday.day }}</td>
    </tr>
    {% endfor %}
</tbody>
```

Behind the scenes, in `app.py`. To add the user's entry into the database, used `execute("query...")` with the values retrieved using `form.get(...)` of the requisition.

Further, if the request is the default `GET`, just send the `birthday` dictionary to the Jinja.

```python
@app.route("/", methods=["GET", "POST"])
def index():
    if request.method == "POST":
        # Get the user's entry from the form
        name = request.form.get("name")
        month = request.form.get("month")
        day = request.form.get("day")

        # TODO: Add the user's entry into the database
        db.execute("INSERT INTO birthdays (name, month, day) VALUES (?, ?, ?)", name, month, day)

        return redirect("/")

    else:
        # TODO: Display the entries in the database on index.html
        birthdays = db.execute("SELECT * FROM birthdays")
        return render_template("index.html", birthdays=birthdays)
```


## Log Trace 

Returned the expected HTTP request values, **200 OK** for `GET` and **302 Found** for `POST` redirecting back to `index.html`.

```bash
birthdays/ $ flask run
 * Debug mode: off
INFO: WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on https://see7e-glowing-broccoli-q76xqwx64xwhx7rq-5000.preview.app.github.dev
INFO: Press CTRL+C to quit
INFO:  * Restarting with stat
INFO: SELECT * FROM birthdays
INFO: 127.0.0.1 - - [21/Jul/2023 14:45:59] "GET / HTTP/1.1" 200 -
INFO: 127.0.0.1 - - [21/Jul/2023 14:45:59] "GET /static/styles.css HTTP/1.1" 200 -
INFO: INSERT INTO birthdays (name, month, day) VALUES ('Keeper', '9', '1')
INFO: 127.0.0.1 - - [21/Jul/2023 14:49:09] "POST / HTTP/1.1" 302 -
INFO: SELECT * FROM birthdays
INFO: 127.0.0.1 - - [21/Jul/2023 14:49:09] "GET / HTTP/1.1" 200 -
INFO: 127.0.0.1 - - [21/Jul/2023 14:49:09] "GET /static/styles.css HTTP/1.1" 200 -
```


## Submitted

	# check50
	## cs50/labs/2023/x/birthdays
	---
	### :) Birthdays

```bash
birthdays/ $ submit50 cs50/labs/2023/x/birthdays
Connecting.......
Authenticating...
Verifying........
Preparing.....
Files that will be submitted:
./static/styles.css
./app.py
./birthdays.db
./templates/index.html
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading.......
Go to https://submit.cs50.io/users/see7e/cs50/labs/2023/x/birthdays to see your results.
birthdays/ $ 
```