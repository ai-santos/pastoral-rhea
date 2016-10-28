#Table of Contents
[Main Page](https://github.com/lumodon/pastoral-rhea/blob/master/README.md)<br><br>
[Problem 1](#problem-1)<br>
[Problem 2](#problem-2)<br>
[Problem 3](#problem-3)<br>
[Problem 4](#problem-4)<br>
[Problem 5](#problem-5)<br>
[Problem 6](#problem-6)<br>
[Problem 7](#problem-7)<br>
[Problem 8](#problem-8)<br>
[Problem 9](#problem-9)<br>
[Problem 10](#problem-10)<br>

#Problem 1: 
[Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/duplicate-emails/
Answer:
```
CREATE TABLE Person(
	Id INTEGER,
	Email VARCHAR(20)
);

INSERT INTO namedTable (Id, Email) 
	VALUES (1, 'a@b.com'), (2, 'c@d.com'), (3, 'a@b.com');
	
SELECT * FROM namedTable;

SELECT DISTINCT Email FROM namedTable x 
	WHERE Email = ANY(
		SELECT Email FROM namedTable y WHERE x.Id != y.Id
	);
```

#Problem 2: 
[Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/employees-earning-more-than-their-managers/
Answer:
```
CREATE TABLE Employee (
	Id INTEGER PRIMARY KEY,
	Name VARCHAR(20),
	Salary INTEGER,
	ManagerId INTEGER
);

INSERT INTO Employee (Id, Name, Salary, ManagerId) 
	VALUES 	(1, 'Joe', 70000, 3), 
			(2, 'Henry', 80000, 4), 
			(3, 'Sam', 60000, NULL), 
			(4, 'Max', 90000, NULL);
	
SELECT * FROM Employee;

SELECT Name AS Employee FROM Employee x 
	WHERE Salary > ANY(
		SELECT Salary FROM Employee y 
			WHERE x.ManagerId = y.Id
	)
```

#Problem 3:
[Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/combine-two-tables/ :
ANSWER:
```
SELECT firstName AS FirstName, lastName AS LastName, City, State FROM Person 
    LEFT JOIN Address ON Person.PersonId = Address.PersonId; 
```

#Problem 4:
[Table of Contents](#table-of-contents)

https://leetcode.com/problems/second-highest-salary/
ANSWER:
```
SELECT MAX(Salary) AS SecondHighestSalary FROM Employee 
	WHERE Salary < ALL(SELECT MAX(Salary) FROM Employee);
```

#Problem 5:
[Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/delete-duplicate-emails/
ANSWER:
```
DELETE p1
FROM Person p1, Person p2
WHERE p1.Email = p2.Email AND
p1.Id > p2.Id
```

#Problem 6: 
[Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/customers-who-never-order/
Answer:
```
DROP TABLE IF EXISTS Customers;
DROP TABLE IF EXISTS Orders;

CREATE TABLE Customers (
	Id INTEGER PRIMARY KEY,
	Name VARCHAR(20)
	);
	
CREATE TABLE Orders (
	Id INTEGER PRIMARY KEY,
	CustomerId INTEGER
	);

INSERT INTO Customers (Id, Name) 
	VALUES 	(1, 'Joe'),
			(2, 'Henry'),
			(3, 'Sam'),
			(4, 'Max');
			
INSERT INTO Orders (Id, CustomerId) 
	VALUES 	(1, 3),
			(2, 1);
			
SELECT Customers.Name AS Customers FROM Customers 
	WHERE Customers.Id NOT IN (
		SELECT Customers.Id FROM Customers JOIN Orders ON Orders.CustomerId = Customers.Id
	)

```

#Problem 7:
[Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/rising-temperature/
ANSWER:
```
SELECT w1.Id 
FROM Weather w1, Weather w2 
WHERE DATEDIFF(w1.DATE, w2.DATE) = 1 
AND w1.Temperature > w2.Temperature;
```

#Problem 8:
[Table of Contents](#table-of-contents)<br>
Question: https://leetcode.com/problems/nth-highest-salary/
Answer:
```
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
  SET N = N-1;
  RETURN (
      SELECT DISTINCT Salary FROM Employee
      ORDER BY Salary DESC
      LIMIT 1 OFFSET N
  );
END
```


#Problem 9: 
[Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/department-highest-salary/
Answer: 
```
DROP TABLE IF EXISTS Employee;
DROP TABLE IF EXISTS Department;

CREATE TABLE Employee (
	Id SERIAL PRIMARY KEY,
	Name VARCHAR(20),
	Salary INTEGER,
	DepartmentId INTEGER
	);
	
CREATE TABLE Department (
	Id SERIAL PRIMARY KEY,
	Name VARCHAR(20)
	);

INSERT INTO Employee (Id, Name, Salary, DepartmentId) 
	VALUES 	(DEFAULT, 'Joe', 700000, 1),
			(DEFAULT, 'Henry', 800000, 2),
			(DEFAULT, 'Sam', 600000, 2),
			(DEFAULT, 'Max', 900000, 1),
			(DEFAULT, 'Jene', 1000000, 1);
			
INSERT INTO Department (Id, Name) 
	VALUES 	(1, 'IT'),
			(2, 'Sales');

SELECT d1.Name AS Department, e1.Name AS Employee, e1.Salary FROM Employee e1
JOIN Department d1 ON e1.DepartmentId = d1.Id
WHERE (DepartmentId, Salary) IN (
	SELECT e2.DepartmentId, MAX(e2.Salary) FROM Employee e2 
	GROUP BY e2.DepartmentId
);
```

#Problem 10:
[Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/rank-scores/
ANSWER:
```
SELECT Score , 
(SELECT COUNT(DISTINCT Score)+1 
FROM Scores as s2 
WHERE s1.Score < s2.Score) AS Rank 
FROM Scores as s1 
ORDER BY Rank ASC;
```
