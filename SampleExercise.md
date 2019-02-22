Sample Exercise
===============

Context
-------

You're working with a database that holds the academic records of high school
students for a local school district. Student demographic data is in the
`students` table, the list of courses is in the `courses` table, and every time
a student is enrolled in a course, a new entry is added to the
`student_courses` table to show that the student has enrolled in that
course, and is later updated to show whether or not the student is currently
active in that course, whether or not they passed, and what grades they
received.

Instructions
------------

William Cross is a student in the school. Perform a query that counts the
number of courses he has passed (the `passed` column in `student_courses` will
be `true`).

Copy and paste the result into the answer box below.

Example Solution
----------------

Note: there are, in practice, many queries that would work for this; the
following is merely one of the simpler ones.

~~~~
SELECT COUNT(*) AS courses_passed
FROM students
INNER JOIN student_courses
        ON student_courses.student_id = students.id
INNER JOIN courses
        ON student_courses.course_id = courses.id
WHERE students.last_name = "Cross"
  AND students.first_name = "William"
  AND student_courses.passed = true
~~~~
