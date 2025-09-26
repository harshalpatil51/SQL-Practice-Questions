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

---------------------------------------------------------------------------------------------------
