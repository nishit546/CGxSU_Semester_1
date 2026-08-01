# College Management System - SQL Practice Dataset

## Objective

Practice SQL using a simple College Management database.

## Create Database

``` sql
CREATE DATABASE CollegeDB;
USE CollegeDB;
```

## Create Tables and Insert Data

### Departments

``` sql
CREATE TABLE Departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(50),
    hod_name VARCHAR(50)
);

INSERT INTO Departments VALUES
(1,'Computer Science','Dr. Sharma'),
(2,'Information Technology','Dr. Patel'),
(3,'Mechanical','Dr. Singh'),
(4,'Civil','Dr. Mehta'),
(5,'Electrical','Dr. Gupta'),
(6,'Electronics','Dr. Verma'),
(7,'Artificial Intelligence','Dr. Khan'),
(8,'Data Science','Dr. Shah'),
(9,'Commerce','Dr. Jain'),
(10,'Mathematics','Dr. Joshi'),
(11,'Physics','Dr. Roy'),
(12,'Chemistry','Dr. Das'),
(13,'Biotechnology','Dr. Thomas'),
(14,'MBA','Dr. Nair'),
(15,'English','Dr. Fernandes'),
(16,'History','Dr. Kulkarni'),
(17,'Economics','Dr. Rao'),
(18,'Architecture','Dr. Iyer'),
(19,'Law','Dr. Mishra'),
(20,'Pharmacy','Dr. Kapoor');
```

### Students

``` sql
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    gender VARCHAR(10),
    age INT,
    city VARCHAR(50),
    marks DECIMAL(5,2),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES Departments(department_id)
);

INSERT INTO Students VALUES
(101,'ankit','Male',21,'Ahmedabad',88,1),
(102,'Rahul','Male',20,'Delhi',75,2),
(103,'Priya','Female',21,'Mumbai',92,1),
(104,'Aman','Male',22,'Jaipur',68,3),
(105,'Sneha','Female',20,'Pune',84,4),
(106,'Riya','Female',19,'Surat',91,5),
(107,'Karan','Male',22,'Indore',66,6),
(108,'Neha','Female',21,'Bhopal',78,7),
(109,'Vikas','Male',23,'Lucknow',81,8),
(110,'Anjali','Female',20,'Ahmedabad',87,9),
(111,'Rohit','Male',21,'Delhi',59,10),
(112,'Pooja','Female',22,'Mumbai',73,11),
(113,'Arjun','Male',20,'Pune',95,12),
(114,'Kavya','Female',19,'Jaipur',82,13),
(115,'Harsh','Male',22,'Ahmedabad',69,14),
(116,'Meera','Female',20,'Surat',90,15),
(117,'Yash','Male',21,'Indore',77,16),
(118,'Nisha','Female',22,'Lucknow',80,17),
(119,'Dev','Male',20,'Delhi',86,18),
(120,'Simran','Female',21,'Mumbai',93,19);
```

### Courses

``` sql
CREATE TABLE Courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(50),
    credits INT,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES Students(student_id)
);

INSERT INTO Courses VALUES
(1,'Database Systems',4,101),
(2,'Operating Systems',4,102),
(3,'Computer Networks',3,103),
(4,'Data Structures',4,104),
(5,'Java Programming',4,105),
(6,'Python Programming',3,106),
(7,'Machine Learning',4,107),
(8,'Artificial Intelligence',4,108),
(9,'Cloud Computing',3,109),
(10,'Web Development',3,110),
(11,'Cyber Security',4,111),
(12,'Software Engineering',3,112),
(13,'DBMS Lab',2,113),
(14,'Linux',2,114),
(15,'Data Analytics',4,115),
(16,'Mobile App Development',3,116),
(17,'Computer Graphics',3,117),
(18,'Big Data',4,118),
(19,'IoT',3,119),
(20,'Compiler Design',4,120);
```

## Verify

``` sql
SHOW TABLES;
DESC Departments;
DESC Students;
DESC Courses;

SELECT * FROM Departments;
SELECT * FROM Students;
SELECT * FROM Courses;
```

## Relationship

-   One Department → Many Students
-   One Student → One Course (for this dataset)

## Topics

-   SELECT
-   WHERE
-   ORDER BY
-   GROUP BY
-   HAVING
-   COUNT, SUM, AVG, MIN, MAX
-   INNER JOIN
-   LEFT JOIN

## Practice Questions

### Basic

1.  Display all students.
2.  Display all departments.
3.  Display all courses.
4.  Show only student names.
5.  Show distinct cities.
6.  Students with marks \> 80.
7.  Students from Ahmedabad.
8.  Female students.
9.  Sort students by marks descending.
10. Show top 5 students by marks.

### Aggregation

11. Count students.
12. Average marks.
13. Highest marks.
14. Lowest marks.
15. Total marks.
16. Students per department.
17. Students per city.
18. Average marks by department.
19. Departments having average marks \> 80.
20. Cities having more than one student.

###  ORDER BY Practice

21. Display students sorted by marks ascending.
22. Display students sorted by marks descending.
23. Sort students by age.
24. Sort students by city alphabetically.
25. Sort students by city and then marks descending.
26. Display top 5 students by marks.
27. Display lowest 5 students by marks.
28. Sort departments by name.
29. Sort courses by credits descending.
30. Sort students by department and marks.

###  Alias (AS)
31. Display student_name as Name.
32. Display marks as Score.
33. Display department_name as Department. 
34. Display hod_name as Head Of Department.
35. Display course_name as Subject.
36. Display student_name and marks with aliases.
37. Display city as Location.
38. Display age as Student Age.
39. Display credits as Course Credits.
40. Display department_id as Dept ID.

###  GROUP BY
41. Count students in each department.
42. Count students in each city.
43. Average marks by city.
44. Average marks by department.
45. Maximum marks in each department.
46. Minimum marks in each department.
47. Total marks by city.
48. Average age by gender.
49. Count male and female students.
50. Count courses based on credits.

### HAVING
51. Departments having more than one student.
52. Cities having more than one student.
53. Departments with average marks above 80.
54. Cities where average marks are above 75.
55. Departments where maximum marks exceed 90.
56. Cities where minimum marks are below 70.
57. Departments having total marks greater than 150.
58. Departments with exactly one student.
59. Genders having average age above 20.
60. Credits having more than two courses.

###  LIKE Operator
61. Student names starting with A.
62. Student names starting with P.
63. Student names ending with a.
64. Student names ending with t.
65. Student names containing "ri".
66. Student names where second letter is 'a'.
67. Student names having exactly five letters.
68. Cities starting with A.
69. Department names ending with "Science".
70. Course names containing "Data".


## Interview Preparation
Database Schema

### Student

            Student(
            student_id INT PRIMARY KEY,
            student_name VARCHAR(50),
            age INT,
            gender VARCHAR(10),
            city VARCHAR(50),
            department_id INT,
            marks INT
            )

### Department

            Department(
            department_id INT PRIMARY KEY,
            department_name VARCHAR(50),
            hod VARCHAR(50)
            )

### Course

            Course(
                course_id INT PRIMARY KEY,
                course_name VARCHAR(50),
                department_id INT,
                credits INT
                )

### Enrollment

            Enrollment(
            enrollment_id INT PRIMARY KEY,
            student_id INT,
            course_id INT,
            semester INT
        )


# SQL Interview Preparation Questions

---

## Part A – Basic SQL

1. Display all students.
2. Display all departments.
3. Display all courses.
4. Display all enrollments.
5. Display only student names.
6. Display students from Ahmedabad.
7. Display students older than 20 years.
8. Display students scoring more than 80 marks.
9. Display students scoring between 60 and 80 marks.
10. Display students whose city is Surat.
11. Display distinct cities.
12. Display distinct department IDs.
13. Sort students by marks.
14. Sort students by city and marks.
15. Display the first 10 students.
16. Count total students.
17. Find highest marks.
18. Find lowest marks.
19. Find average marks.
20. Find total marks.

---

## Part B – GROUP BY & HAVING

1. Count students department-wise.
2. Count students city-wise.
3. Average marks department-wise.
4. Highest marks department-wise.
5. Lowest marks department-wise.
6. Total marks department-wise.
7. Average age department-wise.
8. Count students gender-wise.
9. Departments having more than 5 students.
10. Cities having more than 3 students.
11. Departments having average marks above 70.
12. Cities having highest marks above 90.
13. Departments having lowest marks below 40.
14. Departments having exactly 4 students.
15. Cities having exactly 2 students.
16. Departments whose total marks exceed 500.
17. Cities whose average marks exceed 75.

---

## Part C – JOINS

1. Display student name and department name.
2. Display student name and HOD.
3. Display all students with department details.
4. Display all departments with their students.
5. Display department name and number of students.
6. Display department name and average marks.
7. Display department name and highest marks.
8. Display department name and lowest marks.
9. Display course name and department name.
10. Display all courses with HOD names.
11. Display department name and total courses.
12. Display all departments even if they have no students.
13. Display departments having no students.
14. Display all departments even if they have no courses.
15. Display departments having no courses.

---

## Part D – SELF JOIN

1. Find students from the same city.
2. Find students with the same marks.
3. Find students with the same age.
4. Find students from the same department.
5. Find pairs of students from Ahmedabad.
6. Find pairs of students having equal marks.
7. Find pairs of students in the same course.
8. Find students enrolled in the same semester.
9. Find duplicate student names.
10. Find duplicate cities.

---

## Part E – SUBQUERIES

1. Find students scoring above average.
2. Find students scoring below average.
3. Find students with the highest marks.
4. Find students with the lowest marks.
5. Find second highest marks.
6. Find third highest marks.
7. Find Nth highest marks.
8. Find departments having maximum average marks.
9. Find departments having minimum average marks.
10. Find students scoring above department average.

---

## Part F – UNION

1. Display all student names and HOD names using `UNION`.
2. Display all department names and course names using `UNION`.
3. Display all IDs from Student and Course using `UNION`.
4. Display all names using `UNION ALL`.
5. Display all department IDs using `UNION`.
6. Display all names from Student and Department.
7. Display all course IDs and department IDs.
8. Display all primary keys from all tables using `UNION`.

---

## Part G – Company-Level SQL

1. Department with the highest average marks.
2. Department with the maximum students.
3. Department with the minimum students.
4. Student with the highest marks in each department.
5. Student with the lowest marks in each department.
6. Top 3 departments by average marks.
7. Department-wise student count and course count.
8. Courses with no enrollment.
9. Students enrolled in the maximum number of courses.
10. Departments where every student scored above 60.
11. Departments where at least one student scored 100.
12. Departments with no female students.
13. Cities where average marks exceed department average.
14. HOD supervising the maximum students.
15. Department having both maximum students and maximum courses.
16. Student enrolled in the highest-credit course.
17. Courses with highest credits.
18. Departments offering maximum credits.
19. Students enrolled in all department courses.
20. Find students sharing both city and marks.
21. Find duplicate enrollments.
22. Find students enrolled in more than three courses.
23. Department with the highest enrollment.
24. Find courses having exactly five students.
25. Find departments where no course exists.
26. Find HODs with no students.
27. Find students who have not enrolled in any course.
28. Display department performance report.
