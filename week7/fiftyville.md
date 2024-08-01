---
title: Problem Set 7 - Fiftyville
tags: programming, cs50
use: Documentation
languages: Python, SQL
dependences: CS50
---

> This material is distributed by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my undersantding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Fiftyville](#fiftyville)
  - [A Mystery in Fiftyville](#a-mystery-in-fiftyville)
  - [Getting Started #](#getting-started-)
  - [Specification](#specification)
  - [Hints](#hints)
  - [Testing](#testing)
  - [How to Submit](#how-to-submit)
  - [Acknowledgements](#acknowledgements)
- [Walkthrough](#walkthrough)
  - [Result](#result)
  - [Log Trace](#log-trace)
  - [Submitted](#submitted)

</details>

---

# Fiftyville

Write SQL queries to solve a mystery.

## A Mystery in Fiftyville

The CS50 Duck has been stolen! The town of Fiftyville has called upon you to solve the mystery of the stolen duck. Authorities believe that the thief stole the duck and then, shortly afterwards, took a flight out of town with the help of an accomplice. Your goal is to identify:

-   Who the thief is,
-   What city the thief escaped to, and
-   Who the thief’s accomplice is who helped them escape

All you know is that the theft **took place on July 28, 2021** and that it **took place on Humphrey Street**.

How will you go about solving this mystery? The Fiftyville authorities have taken some of the town’s records from around the time of the theft and prepared a SQLite database for you, `fiftyville.db`, which contains tables of data from around the town. You can query that table using SQL `SELECT` queries to access the data of interest to you. Using just the information in the database, your task is to solve the mystery.

## Getting Started [#](https://cs50.harvard.edu/x/2023/psets/7/fiftyville//#getting-started)

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/7/fiftyville.zip
```

in order to download a ZIP called `fiftyville.zip` into your codespace.

Then execute

```bash
unzip fiftyville.zip
```

to create a folder called `fiftyville`. You no longer need the ZIP file, so you can execute

```bash
rm fiftyville.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd fiftyville
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
fiftyville/ $
```

Execute `ls` by itself, and you should see a few files:

```bash
answers.txt  fiftyville.db  log.sql
```

If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Specification

For this problem, equally as important as solving the mystery itself is the process that you use to solve the mystery. In `log.sql`, keep a log of all SQL queries that you run on the database. Above each query, label each with a comment (in SQL, comments are any lines that begin with `--`) describing why you’re running the query and/or what information you’re hoping to get out of that particular query. You can use comments in the log file to add additional notes about your thought process as you solve the mystery: ultimately, this file should serve as evidence of the process you used to identify the thief!

As you write your queries, you may notice that some of them can become quite complex. To help keep your queries readable, see principles of good style at [sqlstyle.guide](https://www.sqlstyle.guide). The [indentation](https://www.sqlstyle.guide/#indentation) section may be particularly helpful!

Once you solve the mystery, complete each of the lines in `answers.txt` by filling in the name of the thief, the city that the thief escaped to, and the name of the thief’s accomplice who helped them escape town. (Be sure not to change any of the existing text in the file or to add any other lines to the file!)

Ultimately, you should submit both your `log.sql` and `answers.txt` files.


## Hints

-   Execute `sqlite3 fiftyville.db` to begin running queries on the database.
    -   While running `sqlite3`, executing `.tables` will list all of the tables in the database.
    -   While running `sqlite3`, executing `.schema TABLE_NAME`, where `TABLE_NAME` is the name of a table in the database, will show you the `CREATE TABLE` command used to create the table. This can be helpful for knowing which columns to query!
-   You may find it helpful to start with the `crime_scene_reports` table. Start by looking for a crime scene report that matches the date and the location of the crime.
-   See [this SQL keywords reference](https://www.w3schools.com/sql/sql_ref_keywords.asp) for some SQL syntax that may be helpful!

## Testing

Execute the below to evaluate the correctness of your code using `check50`.

```bash
check50 cs50/problems/2023/x/fiftyville
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/fiftyville
```

## Acknowledgements

Inspired by another case over at [SQL City](https://mystery.knightlab.com/).

---

# Walkthrough
> Full code [here](./src/fiftyville/log.sql)

Using sqlite to access fiftyville.db, and using `.schema` to reveal the tables structure:

```sql
-- sqlite> .schema
CREATE TABLE crime_scene_reports (
    id INTEGER,
    year INTEGER,
    month INTEGER,
    day INTEGER,
    street TEXT,
    description TEXT,
    PRIMARY KEY(id)
);
CREATE TABLE interviews (
    id INTEGER,
    name TEXT,
    year INTEGER,
    month INTEGER,
    day INTEGER,
    transcript TEXT,
    PRIMARY KEY(id)
);
CREATE TABLE atm_transactions (
    id INTEGER,
    account_number INTEGER,
    year INTEGER,
    month INTEGER,
    day INTEGER,
    atm_location TEXT,
    transaction_type TEXT,
    amount INTEGER,
    PRIMARY KEY(id)
);
CREATE TABLE bank_accounts (
    account_number INTEGER,
    person_id INTEGER,
    creation_year INTEGER,
    FOREIGN KEY(person_id) REFERENCES people(id)
);
CREATE TABLE airports (
    id INTEGER,
    abbreviation TEXT,
    full_name TEXT,
    city TEXT,
    PRIMARY KEY(id)
);
CREATE TABLE flights (
    id INTEGER,
    origin_airport_id INTEGER,
    destination_airport_id INTEGER,
    year INTEGER,
    month INTEGER,
    day INTEGER,
    hour INTEGER,
    minute INTEGER,
    PRIMARY KEY(id),
    FOREIGN KEY(origin_airport_id) REFERENCES airports(id),
    FOREIGN KEY(destination_airport_id) REFERENCES airports(id)
);
CREATE TABLE passengers (
    flight_id INTEGER,
    passport_number INTEGER,
    seat TEXT,
    FOREIGN KEY(flight_id) REFERENCES flights(id)
);
CREATE TABLE phone_calls (
    id INTEGER,
    caller TEXT,
    receiver TEXT,
    year INTEGER,
    month INTEGER,
    day INTEGER,
    duration INTEGER,
    PRIMARY KEY(id)
);
CREATE TABLE people (
    id INTEGER,
    name TEXT,
    phone_number TEXT,
    passport_number INTEGER,
    license_plate TEXT,
    PRIMARY KEY(id)
);
CREATE TABLE bakery_security_logs (
    id INTEGER,
    year INTEGER,
    month INTEGER,
    day INTEGER,
    hour INTEGER,
    minute INTEGER,
    activity TEXT,
    license_plate TEXT,
    PRIMARY KEY(id)
);
```

Steps

1. view the size of the reports
2. view the entire reports
3. view reports on July 28, 2021 and on Humphrey Street
4. find the bakery
  LEADS
  - bakery parking lot
  - ATM on Leggett Street
  - earliest flight out of Fiftyville tomorrow */
5. bakery  check plate owners*/
6. ATM  check acc_nbr owners*/
7. cross acc_nbr owners w/ plate owners
8. phonecalls
9. SUSPECTS

| id     | name  | phone_number   | passport_number | license_plate |
| ------ | ----- | -------------- | --------------- | ------------- |
| 686048 | Bruce | (367) 555-5533 | 5773159633      | 94KL13X       |
| 514354 | Diana | (770) 555-1861 | 3592750733      | 322W7JE       |

10. Fiftyville airport info
11. Find flights from CSF on 29-07-21
12. find passgengers in flights - THIEF
13. match the numbers of the past calls - ACCOMPLICE
14. find the city


## Result

```txt
The THIEF is: Bruce
The city the thief ESCAPED TO: New York City
The ACCOMPLICE is: Robin
```

## Log Trace 

```bash
Connecting.......
Authenticating...
Verifying........
Preparing.....
Uploading.......
Waiting for results........................
Results for cs50/problems/2023/x/fiftyville generated by check50 v3.3.7
:) log.sql and answers.txt exist
:) log file contains SELECT queries
:) mystery solved
To see the results in your browser go to https://submit.cs50.io/check50/
```

## Submitted

```bash
Connecting......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
./log.sql
./answers.txt
Files that won't be submitted:
./fiftyville.db
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? YES
Uploading......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/fiftyville to see your results.
```