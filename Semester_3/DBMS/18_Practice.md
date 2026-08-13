# SQL + Normalization — EST Practice Questions

## Q1

Consider:

`STUDENT(SID, SName, Age, Dept, Marks)`

Write SQL queries to:

1. Display all students.
2. Display students having marks greater than 80.
3. Display students belonging to CSE.
4. Display students sorted by marks in descending order.
5. Find the average marks.
6. Find the highest marks department-wise.

---

## Q2

Consider:

`EMPLOYEE(EID, EName, Salary, DeptID)`

`DEPARTMENT(DeptID, DeptName)`

Write SQL queries to:

1. Display employee name with department name.
2. Display employees earning more than 50,000.
3. Find average salary department-wise.
4. Display departments whose average salary is greater than 60,000.

---

## Q3

Given:

`R(A, B, C, D, E)`

Functional Dependencies:

* A → B
* B → C
* C → D
* D → E

Answer:

1. Find the candidate key.
2. Identify prime and non-prime attributes.
3. Check whether R is in 2NF.
4. Check whether R is in 3NF.
5. Check whether R is in BCNF.
6. Decompose R into 3NF.

---

## Q4

Consider:

`ENROLLMENT(SID, SName, CID, CName, InstructorID, InstructorName, Marks)`

Functional Dependencies:

* SID → SName
* CID → CName, InstructorID
* InstructorID → InstructorName
* (SID, CID) → Marks

Answer:

1. Find the candidate key.
2. Identify partial dependencies.
3. Identify transitive dependencies.
4. Check 2NF.
5. Check 3NF.
6. Check BCNF.
7. Decompose into 3NF.

---

## Q5

Consider:

| SID | SName | CID | CName | IID | IName  | Marks |
| --- | ----- | --- | ----- | --- | ------ | ----- |
| S1  | Ali   | C01 | DBMS  | I01 | Rao    | 85    |
| S1  | Ali   | C02 | OS    | I02 | Sharma | 72    |
| S2  | Ahmed | C01 | DBMS  | I01 | Rao    | 91    |
| S3  | John  | C03 | CN    | I03 | Khan   | 78    |

Assume:

* SID → SName
* CID → CName, IID
* IID → IName
* (SID, CID) → Marks

Questions:

1. Find the candidate key.
2. Find all partial dependencies.
3. Find all transitive dependencies.
4. Normalize up to 3NF.
5. Determine whether the original relation is in BCNF.

---

## Q6

Consider:

`COURSE(CID, CName, InstructorID, InstructorName, DeptID, DeptName)`

Functional Dependencies:

* CID → CName, InstructorID, DeptID
* InstructorID → InstructorName
* DeptID → DeptName

Answer:

1. Find the candidate key.
2. Identify prime and non-prime attributes.
3. Check 2NF.
4. Check 3NF.
5. Check BCNF.
6. Decompose into BCNF.

---

## Q7

After normalization, you have:

* STUDENT(SID, SName, DeptID)
* COURSE(CID, CName, InstructorID)
* INSTRUCTOR(InstructorID, InstructorName)
* DEPARTMENT(DeptID, DeptName)
* ENROLLMENT(SID, CID, Marks)

Write SQL queries to:

1. Display student name and department name.
2. Display student name, course name and marks.
3. Display course name and instructor name.
4. Find students scoring more than 80.
5. Find average marks for each course.
6. Find the highest marks in each course.
7. Find departments having more than 5 students.
8. Find students who are not enrolled in any course.

---

## Q8 🔥

Consider:

`R(StudentID, StudentName, CourseID, CourseName, InstructorID, InstructorName, DeptID, DeptName, Marks)`

Functional Dependencies:

* StudentID → StudentName
* CourseID → CourseName, InstructorID, DeptID
* InstructorID → InstructorName
* DeptID → DeptName
* (StudentID, CourseID) → Marks

Answer:

1. Find the candidate key.
2. Find all partial dependencies.
3. Find all transitive dependencies.
4. Check 2NF.
5. Check 3NF.
6. Check BCNF.
7. Decompose into 3NF.
8. Decompose into BCNF.
9. Compare the 3NF and BCNF decompositions.

---

## Q9

Given:

`ORDERS(OrderID, CustomerID, CustomerName, ProductID, ProductName, Price, Quantity)`

Assume:

* (OrderID, ProductID) → Quantity
* CustomerID → CustomerName
* ProductID → ProductName, Price

Questions:

1. Find the candidate key.
2. Find partial dependencies.
3. Find transitive dependencies.
4. Check 2NF.
5. Check 3NF.
6. Normalize the relation into 3NF.

---

## Q10 🔥 SQL + Normalization

Consider:

`STUDENT_COURSE(SID, SName, Dept, CID, CName, IID, IName, Marks)`

Assume:

* SID → SName, Dept
* CID → CName, IID
* IID → IName
* (SID, CID) → Marks

Answer:

1. Find the candidate key.
2. Identify partial dependencies.
3. Identify transitive dependencies.
4. Check whether the relation is in 2NF.
5. Check whether the relation is in 3NF.
6. Decompose the relation into 3NF.
7. Create the final tables using SQL.
8. Add primary and foreign key constraints.
9. Insert sample records.
10. Display student name, course name and marks.
11. Find average marks course-wise.
12. Find students scoring above the course average.
