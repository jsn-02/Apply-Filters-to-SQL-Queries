# Apply Filters to SQL Queries

## Scenario

You are a security professional at a large organization. Part of your job is to investigate security issues to help keep the system secure. You recently discovered some potential security issues that involve login attempts and employee machines.

Your task is to examine the organization’s data in their `employees` and `log_in_attempts` tables. You’ll need to use SQL filters to retrieve records from different datasets and investigate the potential security issues.

## Objective

To utilize SQL queries in MariaDB to investigate and mitigate potential security risks by filtering data in the `employees` and `log_in_attempts tables`. This exercise aims to demonstrate the ability to use SQL for data retrieval and analysis in a security context, providing actionable insights for improving system security.

### Skills Learned

- Creating and executing SQL queries
- Using SQL operators (AND, OR, NOT, LIKE) for data filtering
- Investigating security issues through data analysis

### Tools Used

<img src="https://img.shields.io/badge/-MariaDB-003545?&style=for-the-badge&logo=mariadb&logoColor=white" />

## Steps

### Step 1: Review "*Table Formats*" Document

This document describes how the organization's tables are organized.

[Table Formats](https://docs.google.com/viewer?url=https://github.com/user-attachments/files/16322580/Table.Formats.pdf)

### Step 2: Retrieve After Hours Failed Login Attempts

I used this query to identify failed login attempts that occurred after business hours, specifically after 6 PM. By filtering the `log_in_attempts` table where the `login_time` was greater than '18:00' and the `success` was 0 (false), I was able to focus on potentially suspicious activities that took place when the office was likely closed.

![image2](https://github.com/user-attachments/assets/e4e79da1-ec87-42c8-8bcc-a4cd98a46064)

> The WHERE clause filters the records to only include those where the login attempt time is after 18:00 and the attempt failed (success = 0).

### Step 3: Retrieve Login Attempts on Specific Dates

This query helped me investigate a suspicious event that occurred on May 9, 2022. I wanted to review login attempts on both May 8 and May 9 to get a complete picture. By filtering the `login_date` for these two specific dates using the `OR` operator, I captured all relevant login attempts during this period.

![image6](https://github.com/user-attachments/assets/52894e68-bce5-47eb-a51f-d17675b7b2bc)

> The OR operator is used in the WHERE clause to filter records that match either of the specified dates.

### Step 4: Retrieve Login Attempts Outside of Mexico

To investigate login attempts that did not originate in Mexico, I used this query. Since the country column could contain either 'MEX' or 'MEXICO', I used the `NOT LIKE` operator with `%MEX%` to exclude any records associated with Mexico. This helped me focus on login attempts from other countries, which was crucial for narrowing down the investigation.

![image4](https://github.com/user-attachments/assets/6a32faf4-a7d3-4f1b-a00c-c770cc2fb5c4)

> The NOT LIKE operator with %MEX% ensures that both 'MEX' and 'MEXICO' are excluded from the results.

### Step 5: Retrieve Employees in Marketing

I needed to gather information on employees in the Marketing department located in the East building. By filtering the `department` column for values containing 'Marketing' and the `office` column for values starting with 'East-', I was able to pinpoint the exact employees relevant to this query. This was essential for targeting specific machines for security updates.

![image1](https://github.com/user-attachments/assets/f41cb337-640b-4f3e-9229-b5c2720970c8)

> The LIKE operator is used to filter records that contain 'Marketing' in the department and those located in the East building (office LIKE 'East-%').

### Step 6: Retrieve Employees in Finance or Sales

For this query, I aimed to find employees in either the Sales or Finance departments. By using the `OR` operator to filter the `department` column for these two specific values, I identified all relevant employees. This information was necessary for performing targeted security updates on their machines.

![image3](https://github.com/user-attachments/assets/8b516cdb-aaeb-49dc-83d7-5ce7cce08056)

> The OR operator is used in the WHERE clause to filter records that match either 'Sales' or 'Finance' in the department.

### Step 7: Retrieve All Employees Not in IT

Finally, I needed to find employees who were not part of the Information Technology (IT) department. Using the `!=` operator to exclude the 'Information Technology' department from the `department` column, I was able to identify all employees outside of IT. This was important for ensuring that necessary updates were applied to machines not already covered by IT-specific updates.

![image5](https://github.com/user-attachments/assets/e395bcbd-133f-46ae-a876-e051cfd5838b)

> The != operator is used in the WHERE clause to exclude records where the department is 'Information Technology'.

<!--
### Step 8: Write the Document

> [!IMPORTANT]
> [Apply Filters to SQL Queries](https://docs.google.com/viewer?url=)
-->
