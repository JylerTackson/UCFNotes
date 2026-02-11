List **all columns** for employees who work in the department with dept id = 10. Order
the results by name in ascending order.
```sql
SELECT *
FROM Employees
WHERE dept_id = 10
ORDER BY name
```

Ensure that if you see **all columns** you use the `*` to select all.
`ORDER BY` is **default** to `ASC`.

---
Retrieve the distinct department names from the Departments table, ordered alphabetically by dept name.
```sql
SELECT DISTINCT dept_name
FROM Departments
ORDER BY dept_name
```

---
For each department, return the department name and the number of employees in that
department. Only include departments that have at least one employee. Sort the output
by the number of employees in descending order.
```sql
SELECT d.dept_name, COUNT(e.emp_id) AS num_employees
FROM Departments d
JOIN Employees e	
  ON e.dept_id = d.dept_id
GROUP BY d.dept_id, d.dept_name
HAVING COUNT(e.emp_id) > 0
ORDER BY num_employees DESC
```

The `WHERE` clause does not support aggregate functions and come BEFORE grouping. The `HAVING` clause comes after grouping and supports aggregate functions.

---
Compute the overall minimum salary, maximum salary, and average salary across all
employees. Return these three values in a single row, using clear column aliases for each
aggregate.
```sql
SELECT MIN(salary) AS min_salary, 
	MAX(salary) AS max_salary, 
	AVG(salary) AS avg_salary
FROM Employees
```
