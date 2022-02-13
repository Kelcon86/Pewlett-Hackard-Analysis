# Pewlett-Hackard-Analysis

## Overview
Pewlett-Hackard is a reputable company with thousands of employees. Along with an HR analyst, I have been tasked with analyzing 6 CSV files with employee information in order to determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. 

## Results: Provide a bulleted list with four major points from the two analysis deliverables. Use images as support where needed.
For deliverable 1 we were tasked with finding the number of retiring employees by job title. The Retirement_titles table below was created 

- First the Retirement_titles table was created by retrieving the emp_no, first_name and last_name columns from the Employees table and the title, from_date and to_date columns from the Titles table. The INTO clause was used to create the new table and both tables were joined on the primary key. The data was filtered on the birth_date column to retrieve the employees who were born between 1952 and 1955. Lastly, the table was ordered by the employee number.
 
<img width="665" alt="Retirement_titles" src="https://user-images.githubusercontent.com/60076980/153772319-6dde9948-c39b-4ae7-b2f8-5f1d73f38aca.png">

- The second table created was Unique_titles in order to remove the duplicate entries for employees that had switched titles over the years and to keep only the most recent title of each employee. First we retrieved the employee number, first and last name, and title columns from the Retirement Titles table. Then the DISTINCT ON statement was used to retrieve the first occurrence of the employee number for each set of rows defined by the ON () clause. We then filtered on the to_date column to exclude the employees that have already left the company and to keep only those daes that are equal to '9999-01-01'. The Unique_titles table was created by using the INTO clause and the table was sorted in ascending order by the employee number and descending order by the last date (to_date) of the most recent title.

<img width="478" alt="Unique_titles" src="https://user-images.githubusercontent.com/60076980/153772321-157cf030-6fa7-4f6f-bea5-26acd135bea9.png">

- The third table created was Retiring_titles in order to retrieve the number of employees by their most recent job title who are about to retire. We first retrieved the number of titles from the Unique_titles table and then grouped the table by title and sorted the count column in descending order.

<img width="200" alt="Retiring_titles" src="https://user-images.githubusercontent.com/60076980/153772515-fccacd69-85ed-4005-82c7-d7c787ee92dc.png">

- Lastly we created a Mentorship_eligibility table. For deliverable 2 we were tasked with finding the employees that are eligible for the mentorship program (employees born between January 1, 1965 and December 31, 1965). In order to do this we first retrieved the emp_no, first_name, last_name and birth_date columns from the Employees table, the from_date and to_date columns from the Departments Employee table and the title column from the Titles table. Then we used the DISTINCT ON statement to retrieve the first occurrence of the employee number for each set of rows defined by the ON () clause. The new table was created using the INTO clause. We then joined the Employees and Department Employee table on the primary key and the Employees and Titles tables on the primary key. The data was filtered on the to_date column to all the current employees, then filtered on the birth_date columns to get all the employees whose birth dates were between January 1, 1965 and December 31, 1965. The table was ordered by the employee number.

<img width="660" alt="Mentorship_eligibility" src="https://user-images.githubusercontent.com/60076980/153772378-077afb7f-a1ca-41de-a7be-7e04f0e4300d.png">

## Summary: Provide high-level responses to the following questions, then provide two additional queries or tables that may provide more insight into the upcoming "silver tsunami."
How many roles will need to be filled as the "silver tsunami" begins to make an impact?

Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
