This is SQL Practice Questions Repository

---------------------------------------------------------------------------------------------------
Problem 1          Topic - Left Join              27-SEP-2025 

SELECT 
    Person.firstName,
    Person.lastName,
    Address.city,
    Address.state
FROM Person
LEFT JOIN 
    Address ON Person.personId = Address.personId;

--------------------------------------------------------------------------------------------------

Problem 2         Topic - Second Highest Salary          28-SEP-2025

Note : To solve this question there are two approach using subquery and Using ORDER BY with LIMIT and OFFSET:


// Subquery Approach

SELECT MAX(salary) as SecondHighestSalary
FROM Employee
WHERE salary < (SELECT MAX(salary) FROM Employee LIMIT 1)


// Using ORDER BY with LIMIT and OFFSET:

SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;

✅ Explanation:

SELECT DISTINCT salary: Ensures duplicate salaries are not considered.
ORDER BY salary DESC: Sorts salaries from highest to lowest.
LIMIT 1 OFFSET 1: Skips the highest salary (OFFSET 1) and returns the next one (LIMIT 1).

--------------------------------------------------------------------------------------------------

Problem 3         Topic - Conditional           29-SEP-2025


SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >= 25000000;

--------------------------------------------------------------------------------------------------

Problem 4         Topic - Department Highest Salary            29-SEP-2025


WITH DepartmentHighestSalary AS (
    SELECT
        departmentId,
        MAX(salary) AS max_salary
    FROM
        Employee
    GROUP BY
        departmentId
)
SELECT
    D.name AS Department,
    E.name AS Employee,
    E.salary AS Salary
FROM
    Employee AS E
JOIN
    Department AS D ON E.departmentId = D.id
JOIN
    DepartmentHighestSalary AS DHS ON E.departmentId = DHS.departmentId AND E.salary = DHS.max_salary;


✅ Explanation: 
CTE //

This part creates a temporary result set called DepartmentHighestSalary.

It groups the Employee table by departmentId and finds the maximum salary in each department.

So, for each department, you get:

departmentId
max_salary (the highest salary in that department)


Main Query //
This part fetches:

The department name from the Department table (D.name)
The employee name from the Employee table (E.name)
The salary of the employee (E.salary)

It joins:

Employee with Department to get department names.
Employee with DepartmentHighestSalary to filter only those employees whose salary matches the maximum salary in their department.

✅ Explanation:

Jim and Max both work in IT and earn the highest salary in that department (90000).
Henry earns the highest salary in Sales (80000).
Joe and Sam are not included because their salaries are not the highest in their departments.

--------------------------------------------------------------------------------------------------

Problem 5             Topic : Conditional               29-SEP-2025

SELECT name
FROM Customer
WHERE id NOT IN (
    SELECT id
    FROM Customer
    WHERE referee_id = 2
) OR referee_id IS NULL;


SELECT name
FROM Customer
WHERE referee_id != 2 OR referee_id IS NULL;

