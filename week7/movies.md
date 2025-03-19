---
title: Problem Set 7 -  Movies
tags: programming, cs50
use: Documentation
languages: Python, SQL
dependences: CS50
---

> This material is distributed by `Harvard © 2023 edX LLC`. It was copied during the execution of the Course, and have been modified due to my undersantding and integrated to the previous Data Structure of `Programing Studies`.

<details> <summary>Table of Contents</summary>

- [Movies](#movies)
  - [Getting Started #](#getting-started-)
  - [Understanding](#understanding)
  - [Specification](#specification)
  - [Usage](#usage)
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

# Movies

Write SQL queries to answer questions about a database of movies.

## Getting Started [#](https://cs50.harvard.edu/x/2023/psets/7/movies//#getting-started)

Log into [code.cs50.io](https://code.cs50.io/), click on your terminal window, and execute `cd` by itself. You should find that your terminal window’s prompt resembles the below:

```bash
$
```

Next execute

```bash
wget https://cdn.cs50.net/2022/fall/psets/7/movies.zip
```

in order to download a ZIP called `movies.zip` into your codespace.

Then execute

```bash
unzip movies.zip
```

to create a folder called `movies`. You no longer need the ZIP file, so you can execute

```bash
rm movies.zip
```

and respond with “y” followed by Enter at the prompt to remove the ZIP file you downloaded.

Now type

```bash
cd movies
```

followed by Enter to move yourself into (i.e., open) that directory. Your prompt should now resemble the below.

```bash
movies/ $
```

Execute `ls` by itself, and you should see 13 .sql files, as well as `movies.db`.

If you run into any trouble, follow these same steps again and see if you can determine where you went wrong!

## Understanding

Provided to you is a file called `movies.db`, a SQLite database that stores data from [IMDb](https://www.imdb.com/) about movies, the people who directed and starred in them, and their ratings. In a terminal window, run `sqlite3 movies.db` so that you can begin executing queries on the database.

First, when `sqlite3` prompts you to provide a query, type `.schema` and press enter. This will output the `CREATE TABLE` statements that were used to generate each of the tables in the database. By examining those statements, you can identify the columns present in each table.

Notice that the `movies` table has an `id` column that uniquely identifies each movie, as well as columns for the `title` of a movie and the `year` in which the movie was released. The `people` table also has an `id` column, and also has columns for each person’s `name` and `birth` year.

Movie ratings, meanwhile, are stored in the `ratings` table. The first column in the table is `movie_id`: a foreign key that references the `id` of the `movies` table. The rest of the row contains data about the `rating` for each movie and the number of `votes` the movie has received on IMDb.

Finally, the `stars` and `directors` tables match people to the movies in which they acted or directed. (Only [principal](https://www.imdb.com/interfaces/) stars and directors are included.) Each table has just two columns: `movie_id` and `person_id`, which reference a specific movie and person, respectively.

The challenge ahead of you is to write SQL queries to answer a variety of different questions by selecting data from one or more of these tables.

## Specification

For each of the following problems, you should write a single SQL query that outputs the results specified by each problem. Your response must take the form of a single SQL query, though you may nest other queries inside of your query. You **should not** assume anything about the `id`s of any particular movies or people: your queries should be accurate even if the `id` of any particular movie or person were different. Finally, each query should return only the data necessary to answer the question: if the problem only asks you to output the names of movies, for example, then your query should not also output each movie’s release year.

You’re welcome to check your queries’ results against [IMDb](https://www.imdb.com/) itself, but realize that ratings on the website might differ from those in `movies.db`, as more votes might have been cast since we downloaded the data!

1.  In `1.sql`, write a SQL query to list the titles of all movies released in 2008.
>   Your query should output a table with a single column for the title of each movie.

2.  In `2.sql`, write a SQL query to determine the birth year of Emma Stone.
>   Your query should output a table with a single column and a single row (not counting the header) containing Emma Stone’s birth year.
>   You may assume that there is only one person in the database with the name Emma Stone.

3.  In `3.sql`, write a SQL query to list the titles of all movies with a release date on or after 2018, in alphabetical order.
>   Your query should output a table with a single column for the title of each movie.
>   Movies released in 2018 should be included, as should movies with release dates in the future.

4.  In `4.sql`, write a SQL query to determine the number of movies with an IMDb rating of 10.0.
>   Your query should output a table with a single column and a single row (not counting the header) containing the number of movies with a 10.0 rating.

5.  In `5.sql`, write a SQL query to list the titles and release years of all Harry Potter movies, in chronological order.
>   Your query should output a table with two columns, one for the title of each movie and one for the release year of each movie.
>   You may assume that the title of all Harry Potter movies will begin with the words “Harry Potter”, and that if a movie title begins with the words “Harry Potter”, it is a Harry Potter movie.

6.  In `6.sql`, write a SQL query to determine the average rating of all movies released in 2012.
>   Your query should output a table with a single column and a single row (not counting the header) containing the average rating.

7.  In `7.sql`, write a SQL query to list all movies released in 2010 and their ratings, in descending order by rating. For movies with the same rating, order them alphabetically by title.
>   Your query should output a table with two columns, one for the title of each movie and one for the rating of each movie.
>   Movies that do not have ratings should not be included in the result.

8.  In `8.sql`, write a SQL query to list the names of all people who starred in Toy Story.
>   Your query should output a table with a single column for the name of each person.
>   You may assume that there is only one movie in the database with the title Toy Story.

9.  In `9.sql`, write a SQL query to list the names of all people who starred in a movie released in 2004, ordered by birth year.
>   Your query should output a table with a single column for the name of each person.
>   People with the same birth year may be listed in any order.
>   No need to worry about people who have no birth year listed, so long as those who do have a birth year are listed in order.
>   If a person appeared in more than one movie in 2004, they should only appear in your results once.

10.  In `10.sql`, write a SQL query to list the names of all people who have directed a movie that received a rating of at least 9.0.
>   Your query should output a table with a single column for the name of each person.
>   If a person directed more than one movie that received a rating of at least 9.0, they should only appear in your results once.

11.  In `11.sql`, write a SQL query to list the titles of the five highest rated movies (in order) that Chadwick Boseman starred in, starting with the highest rated.
>   Your query should output a table with a single column for the title of each movie.
>   You may assume that there is only one person in the database with the name Chadwick Boseman.

12.  In `12.sql`, write a SQL query to list the titles of all movies in which both Johnny Depp and Helena Bonham Carter starred.
>   Your query should output a table with a single column for the title of each movie.
>   You may assume that there is only one person in the database with the name Johnny Depp.
>   You may assume that there is only one person in the database with the name Helena Bonham Carter.

13.  In `13.sql`, write a SQL query to list the names of all people who starred in a movie in which Kevin Bacon also starred.
>   Your query should output a table with a single column for the name of each person.
>   There may be multiple people named Kevin Bacon in the database. Be sure to only select the Kevin Bacon born in 1958.
>   Kevin Bacon himself should not be included in the resulting list.


## Usage

To test your queries in VS Code, you can query the database by running

```bash
$ cat filename.sql | sqlite3 movies.db
```

where `filename.sql` is the file containing your SQL query.

You can also run

```bash
$ cat filename.sql | sqlite3 movies.db > output.txt
```

to redirect the output of the query to a text file called `output.txt`. (This can be useful for checking how many rows are returned by your query!)

## Hints

-   See [this SQL keywords reference](https://www.w3schools.com/sql/sql_ref_keywords.asp) for some SQL syntax that may be helpful!
-   See [sqlstyle.guide](https://www.sqlstyle.guide/) for pointers on good style in SQL, especially as your queries get more complex!

## Testing

While `check50` is available for this problem, you’re encouraged to instead test your code on your own for each of the following. You can run `sqlite3 movies.db` to run additional queries on the database to ensure that your result is correct.

If you’re using the `movies.db` database provided in this problem set’s distribution, you should find that

> -   Executing `1.sql` results in a table with 1 column and 10,050 rows.
> -   Executing `2.sql` results in a table with 1 column and 1 row.
> -   Executing `3.sql` results in a table with 1 column and 88,918 rows.
> -   Executing `4.sql` results in a table with 1 column and 1 row.
> -   Executing `5.sql` results in a table with 2 columns and 12 rows.
> -   Executing `6.sql` results in a table with 1 column and 1 row.
> -   Executing `7.sql` results in a table with 2 columns and 7,085 rows.
> -   Executing `8.sql` results in a table with 1 column and 4 rows.
> -   Executing `9.sql` results in a table with 1 column and 18,946 rows.
> -   Executing `10.sql` results in a table with 1 column and 3,392 rows.
> -   Executing `11.sql` results in a table with 1 column and 5 rows.
> -   Executing `12.sql` results in a table with 1 column and 7 rows.
> -   Executing `13.sql` results in a table with 1 column and 182 rows.

Note that row counts do not include header rows that only show column names.

If your query returns a number of rows that is slightly different from the expected output, be sure that you’re properly handling duplicates! For queries that ask for a list of names, no one person should be listed twice, but two different people who have the same name should each be listed.

Execute the below to evaluate the correctness of your code using `check50`.

```bash
check50 cs50/problems/2023/x/movies
```

## How to Submit

In your terminal, execute the below to submit your work.

```bash
submit50 cs50/problems/2023/x/movies
```

## Acknowledgements

Information courtesy of IMDb ([imdb.com](https://www.imdb.com)). Used with permission.

---

# Walkthrough
> Full code [here](./src/)

Executing `.schema` gives:

```sql
sqlite> .schema
CREATE TABLE movies (
                    id INTEGER,
                    title TEXT NOT NULL,
                    year NUMERIC,
                    PRIMARY KEY(id)
                );
CREATE TABLE stars (
                movie_id INTEGER NOT NULL,
                person_id INTEGER NOT NULL,
                FOREIGN KEY(movie_id) REFERENCES movies(id),
                FOREIGN KEY(person_id) REFERENCES people(id)
            );
CREATE TABLE directors (
                movie_id INTEGER NOT NULL,
                person_id INTEGER NOT NULL,
                FOREIGN KEY(movie_id) REFERENCES movies(id),
                FOREIGN KEY(person_id) REFERENCES people(id)
            );
CREATE TABLE ratings (
                movie_id INTEGER NOT NULL,
                rating REAL NOT NULL,
                votes INTEGER NOT NULL,
                FOREIGN KEY(movie_id) REFERENCES movies(id)
            );
CREATE TABLE people (
                id INTEGER,
                name TEXT NOT NULL,
                birth NUMERIC,
                PRIMARY KEY(id)
            );
```

Same as Lab 7 here are the queries:

1. `SELECT title FROM movies WHERE year LIKE 2008;`
	```sql
	sqlite> SELECT COUNT(title) FROM movies WHERE year LIKE 2008;
    /*
    +--------------+
    | COUNT(title) |
    +--------------+
    | 10050        |
    +--------------+*/
    ```
2. `SELECT birth FROM people WHERE name LIKE 'Emma Stone';`
3. `SELECT title FROM movies WHERE year >= 2018 ORDER BY title  ASC;`
4. `SELECT COUNT(movie_id) FROM ratings WHERE rating = 10;`
5. `SELECT title, year FROM movies WHERE title LIKE 'Harry Potter%' ORDER BY year ASC;`
6. `SELECT AVG(rating) FROM ratings WHERE movie_id IN (SELECT id FROM movies WHERE year = 2012);`
7. 
    ```sql
    sqlite> SELECT title, rating FROM movies
    ...> JOIN ratings ON movies.id = ratings.movie_id
    ...> WHERE movies.year = 2010
    ...> ORDER BY rating DESC, title;
    /*
    +--------------------------------------------------------+--------+
    |                         title                          | rating |
    +--------------------------------------------------------+--------+
    | Amaren ideia                                           | 9.8    |
    | The American Buffalo                                   | 9.8    |
    | The Great Mystery                                      | 9.8    |
    | ...                                                    | ...    |
    +--------------------------------------------------------+--------+*/
    ```

8. 
    ```sql
    sqlite> SELECT name FROM people
    ...> WHERE id IN (
    ...>     SELECT person_id FROM stars
    ...>     WHERE movie_id IN (
    ...>         SELECT id FROM movies
    ...>         WHERE title LIKE 'Toy Story'
    ...>     )
    ...> );
    /*
    +-------------+
    |    name     |
    +-------------+
    | Tom Hanks   |
    | Tim Allen   |
    | Jim Varney  |
    | Don Rickles |
    +-------------+*/
    ```

9. 
    ```sql
    SELECT  name FROM people
    WHERE id IN (
        SELECT person_id FROM stars
        WHERE movie_id IN (
            SELECT id FROM movies
            WHERE year = 2004
        )
    )
    ORDER BY birth;
    ```

10. It gets timed out.
    ```sql
    SELECT name FROM people
    WHERE id IN (
        SELECT person_id FROM directors
        WHERE movie_id IN (
            SELECT id FROM ratings
            WHERE rating >= 9.0
        )
    );
    ```

11. 
    ```sql
    sqlite> SELECT title FROM movies
    ...> JOIN ratings ON movies.id = ratings.movie_id
    ...> JOIN stars ON movies.id = stars.movie_id
    ...> JOIN people ON stars.person_id = people.id
    ...> WHERE people.name = 'Chadwick Boseman'
    ...> ORDER BY ratings.rating DESC
    ...> LIMIT 5;
    /*
    +--------------------------+
    |          title           |
    +--------------------------+
    | 42                       |
    | Black Panther            |
    | Marshall                 |
    | Ma Rainey's Black Bottom |
    | Get on Up                |
    +--------------------------+*/
    ```

12. 
    ```sql
    sqlite> SELECT title FROM movies
    ...> JOIN stars AS s1 ON movies.id = s1.movie_id
    ...> JOIN stars AS s2 ON movies.id = s2.movie_id
    ...> JOIN people AS p1 ON s1.person_id = p1.id
    ...> JOIN people AS p2 ON s2.person_id = p2.id
    ...> WHERE p1.name = 'Johnny Depp' AND p2.name = 'Helena Bonham Carter';
    /*
    +------------------------------------------------+
    |                     title                      |
    +------------------------------------------------+
    | Corpse Bride                                   |
    | Charlie and the Chocolate Factory              |
    | Sweeney Todd: The Demon Barber of Fleet Street |
    | Alice in Wonderland                            |
    | Dark Shadows                                   |
    | Johnny's Inferno                               |
    | Alice Through the Looking Glass                |
    +------------------------------------------------+*/
    ```

13. Not good, don't kwon why returned 'Kevin Bacon'
    ```sql
    SELECT DISTINCT p.name FROM people AS p
    JOIN stars AS s1 ON p.id = s1.person_id
    JOIN movies AS m1 ON s1.movie_id = m1.id
    JOIN stars AS s2 ON m1.id = s2.movie_id
    JOIN people AS p2 ON s2.person_id = p2.id
    WHERE p2.name = 'Kevin Bacon';
    ```

## Result

```bash

```

## Log Trace 

```bash
movies/ $ check50 cs50/problems/2023/x/movies
Connecting......
Authenticating...
Verifying......
Preparing.....
Uploading......
Waiting for results.......................
Results for cs50/problems/2023/x/movies generated by check50 v3.3.7
:) SQL files exists
:) 1.sql produces correct result
:) 2.sql produces correct result
:) 3.sql produces correct result
:) 4.sql produces correct result
:) 5.sql produces correct result
:) 6.sql produces correct result
:) 7.sql produces correct result
:) 8.sql produces correct result
:) 9.sql produces correct result
:( 10.sql produces correct result
    Query did not return results
:) 11.sql produces correct result
:) 12.sql produces correct result
:( 13.sql produces correct result
    expected "Tom Hanks\nBil...", not "Kevin Bacon\nT..."
To see the results in your browser go to https://submit.cs50.io/check50/
```

## Submitted

```bash
movies/ $ submit50 cs50/problems/2023/x/movies
Connecting......
Authenticating...
Verifying......
Preparing.....
Files that will be submitted:
./3.sql
./10.sql
./11.sql
./7.sql
./1.sql
./8.sql
./2.sql
./5.sql
./9.sql
./4.sql
./12.sql
./6.sql
./13.sql
Files that won't be submitted:
./LICENSE
./movies.db
Keeping in mind the course's policy on academic honesty, are you sure you want to submit these files (yes/no)? yes
Uploading......
Go to https://submit.cs50.io/users/see7e/cs50/problems/2023/x/movies to see your results.
```