# Class Database

## Submission

Below you will find a set of tasks for you to complete to set up a databases of students and mentors.

To submit this homework write the correct commands for each question here:

```sql
create database cyf_classes owner postgres;

CREATE TABLE mentors(
id SERIAL PRIMARY KEY,
name VARCHAR(50) NOT NULL,
yearsInGlasgow int,
address VARCHAR(120),
favProgramLanguage VARCHAR(100)
);

INSERT INTO mentors (name, yearsinglasgow, address, favprogramlanguage) VALUES ('Jesús C.', 1, 'Barcelona', 'php');
INSERT INTO mentors (name, yearsinglasgow, address, favprogramlanguage) VALUES ('Pedro A.', 2, 'Francia', 'java');
INSERT INTO mentors (name, yearsinglasgow, address, favprogramlanguage) VALUES ('Juan B.', 3, 'Suiza', 'JavaScript');
INSERT INTO mentors (name, yearsinglasgow, address, favprogramlanguage) VALUES ('Arturo D', 4, 'Portugal', 'C');
INSERT INTO mentors (name, yearsinglasgow, address, favprogramlanguage) VALUES ('Ronaldo E.', 5, 'Brasil', 'C++');

CREATE TABLE students(
id SERIAL PRIMARY KEY,
name VARCHAR(50) NOT NULL,
address VARCHAR(120),
graduated BOOL
);

INSERT INTO students (name, address, graduated) VALUES ('Ronald M', 'Sevilla', 'true');
INSERT INTO students (name, address, graduated) VALUES ('Ramon M', 'Portugal', 'true');
INSERT INTO students (name, address, graduated) VALUES ('Carlos M', 'Francia', 'true');
INSERT INTO students (name, address, graduated) VALUES ('Maria M', 'Rusia', 'true');
INSERT INTO students (name, address, graduated) VALUES ('Wendy M', 'Alemania', 'false');
INSERT INTO students (name, address, graduated) VALUES ('Eduard M', 'Inglaterra', 'false');
INSERT INTO students (name, address, graduated) VALUES ('Emma M', 'Canarias', 'false');
INSERT INTO students (name, address, graduated) VALUES ('Jose M', 'Suiza', 'false');
INSERT INTO students (name, address, graduated) VALUES ('Marcos M', 'Noruega', 'false');
INSERT INTO students (name, address, graduated) VALUES ('Cristian M', 'Moldavia', 'false');

SELECT * FROM mentors;
SELECT * FROM students;

CREATE TABLE classes(
id SERIAL PRIMARY KEY,
leadingmentor VARCHAR(50) NOT NULL,
topic VARCHAR(120) NOT NULL,
date DATE NOT NULL,
location VARCHAR(30) NOT NULL
);

INSERT INTO classes (leadingmentor, topic, date, location) VALUES ('Bernardo A.', 'JavaScript', '2019/06/22', 'Alemania');
INSERT INTO classes (leadingmentor, topic, date, location) VALUES ('Ramon B.', 'C++', '2020/01/15', 'Barcelona');
INSERT INTO classes (leadingmentor, topic, date, location) VALUES ('Echenique P.', 'Python', '2021/07/01', 'Madrid');

ALTER TABLE students ADD COLUMN class_id int;
ALTER TABLE students add foreign key(class_id) references classes (id);


SELECT * FROM mentors WHERE yearsinglasgow > 5;
SELECT * FROM mentors WHERE favprogramlanguage = 'JavaScript';
SELECT * FROM students WHERE graduated = 'true';



```

When you have finished all of the questions - open a pull request with your answers to the `Databases-Homework` repository.

## Task

1. Create a new database called `cyf_classes` (hint: use `createdb` in the terminal)
2. Create a new table `mentors`, for each mentor we want to save their name, how many years they lived in Glasgow, their address and their favourite programming language.
3. Insert 5 mentors in the `mentors` table (you can make up the data, it doesn't need to be accurate ;-)).
4. Create a new table `students`, for each student we want to save their name, address and if they have graduated from Code Your Future.
5. Insert 10 students in the `students` table.
6. Verify that the data you created for mentors and students are correctly stored in their respective tables (hint: use a `select` SQL statement).
7. Create a new `classes` table to record the following information:

   - A class has a leading mentor
   - A class has a topic (such as Javascript, NodeJS)
   - A class is taught at a specific date and at a specific location

8. Insert a few classes in the `classes` table
9. We now want to store who among the students attends a specific class. How would you store that? Come up with a solution and insert some data if you model this as a new table.
10. Answer the following questions using a `select` SQL statement:
    - Retrieve all the mentors who lived more than 5 years in Glasgow
    - Retrieve all the mentors whose favourite language is Javascript
    - Retrieve all the students who are CYF graduates
    - Retrieve all the classes taught before June this year
    - Retrieve all the students (retrieving student ids only is fine) who attended the Javascript class (or any other class that you have in the `classes` table).
