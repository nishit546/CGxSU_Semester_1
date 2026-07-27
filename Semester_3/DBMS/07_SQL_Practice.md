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
