# Pewlett-Hackard-Analysis
## Overview of the Analysis
The purpose of this project was to complete an analysis on the Dataset provided by Pewlett Hackard to determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. This analysis will be useful to help prepare for a lot of transitions due to the high number of employees reaching retirement.

## Results
* To begin my analysis I created an ERD or Entity Relationship Diagram to effeciently visualize the releathips between the various categorgies given from the datasets. 

![EmployeesDB Updated](https://user-images.githubusercontent.com/93167609/148492671-056db6fb-9be5-49a0-a574-9613e4821d04.png)

* I created the table below to show the employees who are retiring soon. This table was used as as stepping stone for further analysis to quantify the amount of upcoming job vanacies. I cleaned the date from the original table because some employees had duplicate entiries due to a change in job title. I believe this shows growth within the company.

![image](https://user-images.githubusercontent.com/93167609/148494606-898dd127-c2ca-47f7-951a-db80170772e1.png)

* I created the table below which quantifies the job title count. This table makes it easier to see which areas will see the most vacancies. Senior Engineer, Senior Staff and Engineer will see the most retiring employees. Senior Engineer holds the highest at 32.5% of the retiring employees. Senior Staff follow up at 31.3% and Engineer at 15.7%

![image](https://user-images.githubusercontent.com/93167609/148494975-1eaaa2b4-cf0b-4a0a-b3a7-0a08bab031d5.png)

* The table below shows the employees who are of retirement age and their titles. This will be useful when organizing the transition because it will allow the company to identify its senior employees and pair them with their replacements.

![image](https://user-images.githubusercontent.com/93167609/148496880-d3d34b3f-f8ae-4b79-b817-935550109ad2.png)


## Summary
How many roles will need to be filled as the "silver tsunami" begins to make an impact?
- 90,398 roles will need to be filled.

Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
- No, there is not enough qualified, retirement-ready employees to mentor the next genereation. There should be alot of hiring and promoting during this transistion. The earlier table encouraged that growth was possible in this company.  

- I altered my code to yield a table showing only employees who had been hiring in the year 2002. I chose this year because it was the latest hire date amongst the dataset. These employees can be paired with more experienced employees amongst the mentorship candidates. 

`code()` SELECT DISTINCT ON (e.emp_no) e.emp_no,
e.first_name,
e.last_name,
e.birth_date,
de.from_date,
de.to_date,
t.title
INTO new_employees
FROM employees as e
INNER JOIN department_employees as de
ON (e.emp_no =de.emp_no)
INNER JOIN titles as t
ON (e.emp_no=t.emp_no)
WHERE (de.from_date BETWEEN '2002-01-01' AND '2002-12-31')
AND (de.to_date= '9999-01-01')	
ORDER BY emp_no;

![image](https://user-images.githubusercontent.com/93167609/148501885-4c115983-3d31-4fe5-9d9c-6c13ac2ad33c.png)

- As I previously explained, Senior Engineers will have the hardest impact because 32% of the retiring employees are Senior Engineers. I created a table to show only employees with the title Senior Engineer. This will allow the company to identify exactly which Senior Engineer positions need to be filled.

`code()`SELECT DISTINCT ON (e.emp_no) e.emp_no,
e.first_name,
e.last_name,
e.birth_date,
de.from_date,
de.to_date,
t.title
INTO senior_emp
FROM employees as e
INNER JOIN department_employees as de
ON (e.emp_no =de.emp_no)
INNER JOIN titles as t
ON (e.emp_no=t.emp_no)
WHERE (t.title= 'Senior Engineer')
AND (de.to_date= '9999-01-01')	
ORDER BY emp_no;

![image](https://user-images.githubusercontent.com/93167609/148503560-ccf834d7-5afb-400b-a011-a0948a1d2443.png)

