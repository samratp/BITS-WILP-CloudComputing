Below are some sample queries using Neo4j's Cypher query language on a hypothetical employee graph dataset. The dataset includes nodes representing employees and departments, and relationships indicating the manager-subordinate relationships and department assignments.

### Sample Cypher Queries:

1. **Create Employees and Departments:**
   ```cypher
   CREATE (emp1:Employee {name: 'John', empId: 101}),
          (emp2:Employee {name: 'Alice', empId: 102}),
          (dept1:Department {deptId: 'D001', name: 'Engineering'}),
          (dept2:Department {deptId: 'D002', name: 'Marketing'})
   ```

2. **Create Relationships:**
   ```cypher
   MATCH (emp:Employee), (dept:Department)
   WHERE emp.name = 'John' AND dept.name = 'Engineering'
   CREATE (emp)-[:WORKS_IN]->(dept),
          (emp)-[:REPORTS_TO]->(emp2)
   ```

3. **Find Employees in a Department:**
   ```cypher
   MATCH (emp:Employee)-[:WORKS_IN]->(dept:Department)
   WHERE dept.name = 'Engineering'
   RETURN emp.name
   ```

4. **Get Employees and Their Managers:**
   ```cypher
   MATCH (emp:Employee)-[:REPORTS_TO]->(manager:Employee)
   RETURN emp.name, manager.name AS manager
   ```

5. **Find Subordinates of a Manager:**
   ```cypher
   MATCH (manager:Employee)-[:REPORTS_TO]->(subordinate:Employee)
   WHERE manager.name = 'John'
   RETURN subordinate.name
   ```

6. **Find Employees with No Subordinates:**
   ```cypher
   MATCH (emp:Employee)
   WHERE NOT (emp)-[:REPORTS_TO]->()
   RETURN emp.name
   ```

7. **Count Employees in Each Department:**
   ```cypher
   MATCH (emp:Employee)-[:WORKS_IN]->(dept:Department)
   RETURN dept.name, COUNT(emp) AS employeeCount
   ```

8. **Find Common Managers of Employees:**
   ```cypher
   MATCH (emp1:Employee)-[:REPORTS_TO]->(manager:Employee)<-[:REPORTS_TO]-(emp2:Employee)
   RETURN emp1.name, emp2.name, manager.name AS commonManager
   ```

9. **Get Employees and Their Department:**
   ```cypher
   MATCH (emp:Employee)-[:WORKS_IN]->(dept:Department)
   RETURN emp.name, dept.name AS department
   ```

10. **Find Shortest Path Between Employees:**
    ```cypher
    MATCH path = shortestPath((emp1:Employee)-[*]-(emp2:Employee))
    WHERE emp1.name = 'John' AND emp2.name = 'Alice'
    RETURN path
    ```

11. **Get Employees and Their Direct Reports:**
    ```cypher
    MATCH (manager:Employee)-[:REPORTS_TO]->(subordinate:Employee)
    RETURN manager.name, COLLECT(subordinate.name) AS directReports
    ```

12. **Find Employees Who Are Also Managers:**
    ```cypher
    MATCH (emp:Employee)-[:REPORTS_TO]->(subordinate:Employee)
    RETURN emp.name, COLLECT(subordinate.name) AS directReports
    ```

13. **Find Employees with a Specific Skill:**
    ```cypher
    MATCH (emp:Employee)-[:HAS_SKILL]->(skill:Skill {name: 'Java'})
    RETURN emp.name
    ```

14. **Update Employee Details:**
    ```cypher
    MATCH (emp:Employee {name: 'John'})
    SET emp.salary = 80000, emp.title = 'Senior Developer'
    RETURN emp
    ```

15. **Delete Employee and Relationships:**
    ```cypher
    MATCH (emp:Employee {name: 'Alice'})-[r]-()
    DELETE emp, r
    ```

These queries assume a simple graph model.
