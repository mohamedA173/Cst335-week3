# CST335 Week 3: Student Success Hub

## Scenario
The school wants a hub where advisors can look up a student and see their support history. This includes the student's info, advising notes, and visits to tutoring, the writing center, or workshops. For this assignment I set up the same data two ways, once with relational tables and once with MongoDB.

## Relational Design
I made three tables: Student, AdvisingNote, and SupportVisit. AdvisingNote and SupportVisit both have a StudentID foreign key that connects back to Student. I also used NOT NULL, UNIQUE, and CHECK so the data stays clean.

## MongoDB Design
I used one collection called `students`. Each student has their advising notes and support visits saved inside their document as arrays. I did it this way because advisors usually look up one student at a time. I also added validation rules and unique indexes so bad data can't get added.

## Comparison
Relational is better when you need the data to stay correct and when you want to look at info across a lot of students, like pulling all tutoring visits for a report. The foreign keys and constraints do a lot of the work for you.

MongoDB is better for what this hub is mostly for, which is pulling up one student and seeing everything at once. It's also easier to add new fields later. The downside is you have to set up the integrity rules yourself.

## How to Run
1. Install MongoDB Community Edition and start it with `brew services start mongodb/brew/mongodb-community`
2. Open a terminal in this folder
3. Run `mongosh < week3_mongo_commands.txt` to create the database and add the data. The last command is supposed to fail since it's testing the validation.
4. Run `mongosh < week3_mongo_queries.txt` to see the query results
