# SQL Security Investigation - Login & Employee Data Analysis

**Author:** Taaha Idrees  
**Project Type:** Simulated cybersecurity training investigation  
**Focus:** SQL filtering, login analysis, employee system analysis

## Project Description

In this project, I used SQL queries to investigate potential security issues involving login activity and employee systems. I applied filters to identify events such as failed login attempts outside normal working hours, suspicious activity on specific dates, and login attempts originating outside a specified location. I also queried employee records to identify systems that required security updates.

## Investigation

### 1. After-Hours Failed Login Attempts

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00'
  AND success = 0;
```

**Analysis:** This query retrieves failed login attempts that occurred after 18:00. The WHERE clause filters records based on the login_time and success columns. The AND operator requires both conditions to be true, so the results contain only login attempts that occurred after business hours and were unsuccessful.

### 2. Login Attempts on Suspicious Dates

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09'
   OR login_date = '2022-05-08';
```

**Analysis:** This query retrieves all login attempts that occurred on May 8 or May 9, 2022. The WHERE clause filters the login_date column, while the OR operator returns records that satisfy either date condition. Reviewing activity across both dates allows the security team to examine login behavior surrounding the suspicious event.

### 3. Login Attempts Outside Mexico

```sql
SELECT *
FROM log_in_attempts
WHERE country NOT LIKE 'MEX%';
```

**Analysis:** This query retrieves login attempts that originated outside of Mexico. The LIKE 'MEX%' pattern matches country values beginning with MEX, including both MEX and MEXICO. The NOT operator excludes these records, allowing the security team to focus its investigation on login attempts originating from other countries.

### 4. Marketing Employees in the East Building

```sql
SELECT *
FROM employees
WHERE department = 'Marketing'
  AND office LIKE 'East%';
```

**Analysis:** This query retrieves employees in the Marketing department who work in the East building. The department = 'Marketing' condition filters employees by department, while office LIKE 'East%' matches office values that begin with East. The AND operator ensures that both conditions must be satisfied, allowing the security team to identify the employee machines that require the security update.

### 5. Employees in Sales or Finance

```sql
SELECT *
FROM employees
WHERE department = 'Sales'
   OR department = 'Finance';
```

**Analysis:** This query retrieves employees who work in either the Sales or Finance department. The WHERE clause filters records using the department column, while the OR operator allows either condition to be satisfied. This provides the security team with the employee records needed to identify machines requiring the security update.

### 6. Employees Outside Information Technology

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

**Analysis:** This query retrieves employees who are not part of the Information Technology department. The WHERE clause filters records based on the department column, while the NOT operator excludes employees in Information Technology. This allows the security team to identify employees whose machines still require the security update.

## Summary

This investigation demonstrated how SQL can help security professionals efficiently analyze large datasets and isolate information relevant to a security investigation. I used AND, OR, NOT, LIKE, and the % wildcard to filter login and employee records based on multiple security conditions. These techniques can help identify suspicious login activity and determine which employee systems require security-related action.

## Skills Demonstrated

- SQL filtering with `WHERE`
- Combining conditions with `AND` and `OR`
- Excluding records with `NOT` and `NOT LIKE`
- Pattern matching with `LIKE` and the `%` wildcard
- Date and time filtering
- Security-focused analysis of login and employee data

## Portfolio Note

This project is based on a simulated training scenario completed as part of cybersecurity coursework. It demonstrates practical SQL filtering and security-analysis skills rather than production or employment experience.
