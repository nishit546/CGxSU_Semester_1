#  SQL Practice — Students, Courses & Enrollments

## 1. Database Schema

### Students

| Column | Type | Description |
|---|---|---|
| student_id | INT | Primary key |
| name | VARCHAR(50) | Student name |
| department | VARCHAR(50) | Student department |
| city | VARCHAR(50) | Student city |
| admission_year | INT | Year of admission |

### Courses

| Column | Type | Description |
|---|---|---|
| course_id | INT | Primary key |
| course_name | VARCHAR(100) | Course name |
| credits | INT | Course credits |

### Enrollments

| Column | Type | Description |
|---|---|---|
| enrollment_id | INT | Primary key |
| student_id | INT | Foreign key referencing Students |
| course_id | INT | Foreign key referencing Courses |
| marks | INT | Marks obtained |
| enrollment_date | DATE | Date of enrollment |

---

## 2. Create Database Tables

    CREATE TABLE Students(
        student_id INT PRIMARY KEY,
        name VARCHAR(50),
        department VARCHAR(50),
        city VARCHAR(50),
        admission_year INT
    );

    CREATE TABLE Courses (
        course_id INT PRIMARY KEY,
        course_name VARCHAR(100),
        credits INT
    );

    CREATE TABLE Enrollments (
        enrollment_id INT PRIMARY KEY,
        student_id INT,
        course_id INT,
        marks INT,
        enrollment_date DATE,
        FOREIGN KEY (student_id) REFERENCES Students(student_id),
        FOREIGN KEY (course_id) REFERENCES Courses(course_id)
    );

---

# SQL Practice Questions

## Level 1 — Aggregation & Subqueries

### Question 1
Find the **second-highest marks** obtained by any student.

---

### Question 2
Find the students who scored **more than the average marks of all students**.

---

### Question 3
Find the students whose marks are **greater than the average marks of their own course**.

---

### Question 4
Find the **course with the highest average marks**.

---

### Question 5
Find the student who has obtained the **highest marks in each course**.

---

### Question 6
Find students who are enrolled in **more courses than the average number of courses taken by a student**.

---

### Question 7
Find students who are enrolled in **every course** available in the `Courses` table.

---

### Question 8
Find courses in which **no student has scored below 40**.

---

### Question 9
Find students who have **never scored below 50** in any course.

---

### Question 10
Find students who have scored **above 80 in at least two different courses**.

---

### Question 11
Find the **department having the highest average student marks**.

---

### Question 12
Find the **top 3 students from each department** based on their average marks.

---

### Question 13
Find students whose **average marks are higher than the average marks of their department**.

---

### Question 14
Find the course with the **largest difference between highest and lowest marks**.

---

### Question 15
Find students who have taken **more courses than every student from the Computer Science department**.

---

### Question 16
Find students who have taken **at least one course but have never scored below 60**.

---

### Question 17
Find the **most popular course**, i.e. the course having the maximum number of enrolled students.

---

### Question 18
Find the **second-most popular course** based on enrollment count.

---

### Question 19
Find students who are enrolled in **exactly the same courses as another student**.

---

### Question 20
Find pairs of students who have taken **at least two courses together**.

---

### Question 21
Find the student(s) who have the **highest total marks** across all their enrolled courses.

---

### Question 22
Find the student who has the **highest average marks without using `LIMIT` or `TOP`**.

---

### Question 23
Find courses where the **average marks are higher than the overall average marks of all enrollments**.

---

### Question 24
Find the department where students have the **highest average marks**, considering only students who are enrolled in at least 2 courses.

---

### Question 25
Find students who scored **higher than every student from at least one other department**.

---

