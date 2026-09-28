# MongoDB Design: Student Success Hub

## Collections

I only used one collection called `students`. Each student has two arrays inside it:
- `advisingNotes` (date, advisor, category, text)
- `supportVisits` (date, serviceType, description)

## Sample Document

{
  "studentId": "S1001",
  "name": "Amina Warsame",
  "email": "amina.warsame@concordia.com",
  "major": "Information Technology Infrastructure",
  "advisingNotes": [
    { "date": ISODate("2026-09-02"), "advisor": "Dr. Reyes", "category": "academic plan", "text": "Reviewed fall schedule, on track for spring graduation." },
    { "date": ISODate("2026-09-18"), "advisor": "Dr. Reyes", "category": "well-being", "text": "Feeling stressed with work hours, talked about time management." }
  ],
  "supportVisits": [
    { "date": ISODate("2026-09-05"), "serviceType": "tutoring", "description": "Database normalization help" },
    { "date": ISODate("2026-09-15"), "serviceType": "writing center", "description": "Reviewed reflection paper" }
  ]
}

## Why I embedded

I embedded the notes and visits because advisors are usually looking up one student at a time. This way I get everything about that student in one query and I don't have to connect different collections. A student isn't going to have hundreds of notes or visits so the documents won't get too big. It also made the 3 or more visits question easier because I could just count how many items are in the array. If the school wanted a report of every tutoring visit across all students though, I think having visits in their own collection would work better.