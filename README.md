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

Explanation:

SELECT DISTINCT salary: Ensures duplicate salaries are not considered.
ORDER BY salary DESC: Sorts salaries from highest to lowest.
LIMIT 1 OFFSET 1: Skips the highest salary (OFFSET 1) and returns the next one (LIMIT 1).

--------------------------------------------------------------------------------------------------