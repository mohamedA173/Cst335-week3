# Relational Design: Student Success Hub

## Tables

Student
- StudentID (PK)
- FirstName (NOT NULL)
- LastName (NOT NULL)
- Email (NOT NULL, UNIQUE)
- Major

AdvisingNote
- NoteID (PK)
- StudentID (FK, NOT NULL)
- NoteDate (NOT NULL)
- AdvisorName (NOT NULL)
- Category (NOT NULL, CHECK in 'academic plan', 'well-being', 'career')
- NoteText (NOT NULL)

SupportVisit
- VisitID (PK)
- StudentID (FK, NOT NULL)
- VisitDate (NOT NULL)
- ServiceType (NOT NULL, CHECK in 'tutoring', 'writing center', 'workshop')
- Description

## Relationships

- AdvisingNote.StudentID references Student.StudentID. A student can have a lot of notes but each note is only for one student.
- SupportVisit.StudentID references Student.StudentID. Same thing here, a student can have a lot of visits but each visit is for one student.

I made the StudentID foreign keys NOT NULL so you can't have a note or visit that isn't tied to a student. I also made Email UNIQUE so the same person can't get added twice. For Category and ServiceType I added CHECK constraints so people have to pick from a set list instead of typing whatever they want.

I thought about making an Advisor table but I just kept AdvisorName as a column to keep it simple. If the hub got bigger I would probably split it out.