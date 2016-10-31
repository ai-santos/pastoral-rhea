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
[Back to Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/duplicate-emails/
<br>Setup:
```
CREATE TABLE Person(
	Id INTEGER,
	Email VARCHAR(20)
);

INSERT INTO namedTable (Id, Email) 
	VALUES (1, 'a@b.com'), (2, 'c@d.com'), (3, 'a@b.com');
```

#Problem 2: 
[Back to Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/employees-earning-more-than-their-managers/
<br>Setup:
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
```

#Problem 3:
[Back to Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/combine-two-tables/ :
<br>Setup:
```
#No setup provided
```

#Problem 4:
[Back to Table of Contents](#table-of-contents)

https://leetcode.com/problems/second-highest-salary/
<br>Setup:
```
#No setup provided
```

#Problem 5:
[Back to Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/delete-duplicate-emails/
<br>Setup:
```
#No prep needed
```

#Problem 6: 
[Back to Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/customers-who-never-order/
<br>Setup:
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
```

#Problem 7:
[Back to Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/rising-temperature/
<br>Setup:
```
#No prep work provided
```

#Problem 8:
[Back to Table of Contents](#table-of-contents)<br>
Question: https://leetcode.com/problems/nth-highest-salary/
<br>Setup:
```
#Function based answer
```


#Problem 9: 
[Back to Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/department-highest-salary/
<br>Setup: 
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
```

#Problem 10:
[Back to Table of Contents](#table-of-contents)<br>
https://leetcode.com/problems/rank-scores/
<br>Setup:
```
#No setup provided
```
