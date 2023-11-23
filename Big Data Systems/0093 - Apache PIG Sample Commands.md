Let's assume a data file named `employee_data.txt` with the following sample rows:

```plaintext
1,John,Male,60000,IT
2,Jane,Female,70000,HR
3,Bob,Male,80000,Finance
4,Alice,Female,75000,IT
5,Charlie,Male,90000,Finance
6,Eva,Female,65000,HR
```

Here are 30 Apache Pig commands with explanations and sample output:

### 1. **Load Data:**
```pig
-- Load data from file into a relation named 'employees'
employees = LOAD 'employee_data.txt' USING PigStorage(',') AS (id:int, name:chararray, gender:chararray, salary:int, department:chararray);
```

### 2. **Show Schema:**
```pig
-- Display the schema of the 'employees' relation
DESCRIBE employees;
```
**Output:**
```plaintext
employees: {id: int, name: chararray, gender: chararray, salary: int, department: chararray}
```

### 3. **Display Data:**
```pig
-- Display the first few rows of the 'employees' relation
DUMP employees;
```
**Output:**
```plaintext
(1,John,Male,60000,IT)
(2,Jane,Female,70000,HR)
(3,Bob,Male,80000,Finance)
(4,Alice,Female,75000,IT)
(5,Charlie,Male,90000,Finance)
(6,Eva,Female,65000,HR)
```

### 4. **Filter Data - Male Employees:**
```pig
-- Filter only male employees
male_employees = FILTER employees BY gender == 'Male';
DUMP male_employees;
```
**Output:**
```plaintext
(1,John,Male,60000,IT)
(3,Bob,Male,80000,Finance)
(5,Charlie,Male,90000,Finance)
```

### 5. **Group by Department:**
```pig
-- Group employees by department
department_group = GROUP employees BY department;
DUMP department_group;
```
**Output:**
```plaintext
(Finance,{(3,Bob,Male,80000,Finance),(5,Charlie,Male,90000,Finance)})
(HR,{(2,Jane,Female,70000,HR),(6,Eva,Female,65000,HR)})
(IT,{(1,John,Male,60000,IT),(4,Alice,Female,75000,IT)})
```

### 6. **Count Employees by Department:**
```pig
-- Count employees in each department
employee_count = FOREACH department_group GENERATE group AS department, COUNT(employees) AS count;
DUMP employee_count;
```
**Output:**
```plaintext
(Finance,2)
(HR,2)
(IT,2)
```

### 7. **Average Salary by Gender:**
```pig
-- Calculate average salary by gender
average_salary = FOREACH (GROUP employees BY gender) GENERATE group AS gender, AVG(employees.salary) AS avg_salary;
DUMP average_salary;
```
**Output:**
```plaintext
(Female,70000.0)
(Male,76666.66666666667)
```

### 8. **Top 3 Highest Salaries:**
```pig
-- Find the top 3 highest salaries
top_salaries = ORDER employees BY salary DESC;
top_3_salaries = LIMIT top_salaries 3;
DUMP top_3_salaries;
```
**Output:**
```plaintext
(5,Charlie,Male,90000,Finance)
(3,Bob,Male,80000,Finance)
(2,Jane,Female,70000,HR)
```

### 9. **Join Data with Another Relation:**
Assuming another relation named `department_info` with department details.

```pig
-- Join employee data with department_info
department_info = LOAD 'department_info.txt' USING PigStorage(',') AS (department:chararray, location:chararray);
joined_data = JOIN employees BY department, department_info BY department;
DUMP joined_data;
```
**Output:**
```plaintext
(1,John,Male,60000,IT,IT,San Francisco)
(2,Jane,Female,70000,HR,HR,New York)
(3,Bob,Male,80000,Finance,Finance,Chicago)
(4,Alice,Female,75000,IT,IT,San Francisco)
(5,Charlie,Male,90000,Finance,Finance,Chicago)
(6,Eva,Female,65000,HR,HR,New York)
```

### 10. **Window Function - Rank by Salary:**
```pig
-- Rank employees based on salary
ranked_data = RANK employees BY salary DESC;
DUMP ranked_data;
```
**Output:**
```plaintext
(1,John,Male,60000,IT,5)
(2,Jane,Female,70000,HR,3)
(3,Bob,Male,80000,Finance,1)
(4,Alice,Female,75000,IT,4)
(5,Charlie,Male,90000,Finance,2)
(6,Eva,Female,65000,HR,6)
```
