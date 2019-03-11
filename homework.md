# SQL Homework

The local cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'

```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:

```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions. Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1.  Return ALL the data in the 'movies' table.

Answer: SELECT * FROM movies;
Result: 
id |                title                | year | show_time 
----+-------------------------------------+------+-----------
1 | Iron Man                            | 2008 | 23:40
2 | The Incredible Hulk                 | 2008 | 17:30
3 | Iron Man 2                          | 2010 | 20:40
4 | Thor                                | 2011 | 16:30
5 | Captain America: The First Avenger  | 2011 | 13:10
6 | Avengers Assemble                   | 2012 | 20:30
7 | Iron Man 3                          | 2013 | 23:05
8 | Thor: The Dark World                | 2013 | 23:10
9 | Batman Begins                       | 2005 | 18:00
10 | Captain America: The Winter Soldier | 2014 | 16:10
11 | Guardians of the Galaxy             | 2014 | 17:15
12 | Avengers: Age of Ultron             | 2015 | 23:35
13 | Ant-Man                             | 2015 | 15:00
14 | Captain America: Civil War          | 2016 | 21:35
15 | Doctor Strange                      | 2016 | 20:40
16 | Guardians of the Galaxy 2           | 2017 | 22:45
17 | Spider-Man: Homecoming              | 2017 | 22:40
18 | Thor: Ragnarok                      | 2017 | 17:40
19 | Black Panther                       | 2018 | 22:00

2.  Return ONLY the name column from the 'people' table

Answer: SELECT name FROM people;
Result: 
name          
------------------------
Jennifer Archibald
Katharina Bitzan
Myriam Boran
David Boyle
Alasdair Carstairs
Eric Cross
Amy Edwardson
Jordan Davidson
Stephen Gibson
Mark King
Rory MacGregor
Robert Marshall
Becky Nielsen
Grant Rutherford
Kanokwan Sritawan
Montgomery Stanczak
Lidia Stopinska-Cherek
Ben Svajko/ Barker
Maria Toscano
Annabel Treshansky
Charlie Walker


3.  Oops! Someone at CodeClan got Mateusz's name wrong! Change it to reflect Mateusz' proper name ('Montgomery' should be 'Mateusz').

Answer: UPDATE people SET name = 'Mateusz Stanczak' WHERE name = 'Montgomery Stanczak';
Result:
Mateusz Stanczak

4.  Return ONLY your name from the 'people' table.

Answer: SELECT 'Jon Zarecki' FROM people;
Result:  Jon Zarecki

5.  The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

Answer: DELETE FROM movies WHERE title = 'Batman Begins';
Result:
id |                title                | year | show_time 
----+-------------------------------------+------+-----------
1 | Iron Man                            | 2008 | 23:40
2 | The Incredible Hulk                 | 2008 | 17:30
3 | Iron Man 2                          | 2010 | 20:40
4 | Thor                                | 2011 | 16:30
5 | Captain America: The First Avenger  | 2011 | 13:10
6 | Avengers Assemble                   | 2012 | 20:30
7 | Iron Man 3                          | 2013 | 23:05
8 | Thor: The Dark World                | 2013 | 23:10
10 | Captain America: The Winter Soldier | 2014 | 16:10
11 | Guardians of the Galaxy             | 2014 | 17:15
12 | Avengers: Age of Ultron             | 2015 | 23:35
13 | Ant-Man                             | 2015 | 15:00
14 | Captain America: Civil War          | 2016 | 21:35
15 | Doctor Strange                      | 2016 | 20:40
16 | Guardians of the Galaxy 2           | 2017 | 22:45
17 | Spider-Man: Homecoming              | 2017 | 22:40
18 | Thor: Ragnarok                      | 2017 | 17:40
19 | Black Panther                       | 2018 | 22:00
(18 rows)

6.  Create a new entry in the 'people' table with the name of one of the instructors.

Answer:
INSERT INTO people (
name
) VALUES (
'Pawel Orzechowski'
);

Result:
(...) Pawel Orzechowski
(23 rows)

7.  Jordan Davidson has abandoned us. Remove him from the table of people.

Answer: DELETE FROM people WHERE name = 'Jordan Davidson';

Result:
Jon Zarecki
Mateusz Stanczak
Pawel Orzechowski
(22 rows)

8.  The cinema has just heard that they will be holding an exclusive midnight showing of 'Avengers: Infinity War'!! Create a new entry in the 'movies' table to reflect this.

Answer:
INSERT INTO movies (
title,
year,
show_time
) VALUES (
'Avengers: Infinity War',
2018,
'00:00'
);

Result:
id |                title                | year | show_time 
----+-------------------------------------+------+-----------
1 | Iron Man                            | 2008 | 23:40
2 | The Incredible Hulk                 | 2008 | 17:30
3 | Iron Man 2                          | 2010 | 20:40
4 | Thor                                | 2011 | 16:30
5 | Captain America: The First Avenger  | 2011 | 13:10
6 | Avengers Assemble                   | 2012 | 20:30
7 | Iron Man 3                          | 2013 | 23:05
8 | Thor: The Dark World                | 2013 | 23:10
10 | Captain America: The Winter Soldier | 2014 | 16:10
11 | Guardians of the Galaxy             | 2014 | 17:15
12 | Avengers: Age of Ultron             | 2015 | 23:35
13 | Ant-Man                             | 2015 | 15:00
14 | Captain America: Civil War          | 2016 | 21:35
15 | Doctor Strange                      | 2016 | 20:40
16 | Guardians of the Galaxy 2           | 2017 | 22:45
17 | Spider-Man: Homecoming              | 2017 | 22:40
18 | Thor: Ragnarok                      | 2017 | 17:40
19 | Black Panther                       | 2018 | 22:00
20 | Avengers: Infinity War              | 2018 | 00:00
(19 rows)


9.  The cinema would also like to make the Guardians movies a back to back feature. Find out the show time of "Guardians of the Galaxy" and set the show time of "Guardians of the Galaxy 2" to start two hours later.

Answer for finding showtime:
SELECT show_time FROM movies WHERE title = 'Guardians of the Galaxy';
Result:  show_time 
-----------
17:15
(1 row)

Answer for changing showtime: UPDATE movies SET show_time = '19:15' WHERE title = 'Guardians of the Galaxy 2';

Result:
16 | Guardians of the Galaxy 2           | 2017 | 19:15
(19 rows)

## Extension

1.  Research how to delete multiple entries from your table in a single command.

Answer: DELETE FROM movies WHERE id = 10 OR id = 14;

Result: (...) 20 | Avengers: Infinity War             | 2018 | 00:00
16 | Guardians of the Galaxy 2          | 2017 | 19:15
(17 rows)
