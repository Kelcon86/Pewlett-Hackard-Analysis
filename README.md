# Pewlett-Hackard-Analysis

## Overview
Pewlett-Hackard is a reputable company with thousands of employees. Along with an HR analyst, I have been tasked with analyzing 6 CSV files with employee information in order to determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. 

## Results
- For deliverable 1 we were tasked with finding the number of retiring employees by job title. The Retirement_titles table was created by retrieving the emp_no, first_name and last_name columns from the Employees table and the title, from_date and to_date columns from the Titles table. The INTO clause was used to create the new table and both tables were joined on the primary key. The data was filtered on the birth_date column to retrieve the employees who were born between 1952 and 1955. Lastly, the table was ordered by the employee number.
 
<img width="623" alt="retirement_titles_screenshot" src="https://user-images.githubusercontent.com/60076980/153776293-f191e25f-7496-448b-af63-b8eb6b2c096c.png">

- The second table created was Unique_titles in order to remove the duplicate entries for employees that had switched titles over the years and to keep only the most recent title of each employee. First we retrieved the employee number, first and last name, and title columns from the Retirement Titles table. Then the DISTINCT ON statement was used to retrieve the first occurrence of the employee number for each set of rows defined by the ON () clause. We then filtered on the to_date column to exclude the employees that have already left the company and to keep only those daes that are equal to '9999-01-01'. The Unique_titles table was created by using the INTO clause and the table was sorted in ascending order by the employee number and descending order by the last date (to_date) of the most recent title.

<img width="478" alt="Unique_titles" src="https://user-images.githubusercontent.com/60076980/153772321-157cf030-6fa7-4f6f-bea5-26acd135bea9.png">

- The third table created was Retiring_titles in order to retrieve the number of employees by their most recent job title who are about to retire. We first retrieved the number of titles from the Unique_titles table and then grouped the table by title and sorted the count column in descending order.

<img width="492" alt="Retirement_titles" src="https://user-images.githubusercontent.com/60076980/153776213-ac51f058-9ec4-4c6d-b0b8-50e93b8199cf.png">

- Lastly we created a Mentorship_eligibility table. For deliverable 2 we were tasked with finding the employees that are eligible for the mentorship program (employees born between January 1, 1965 and December 31, 1965). In order to do this we first retrieved the emp_no, first_name, last_name and birth_date columns from the Employees table, the from_date and to_date columns from the Departments Employee table and the title column from the Titles table. Then we used the DISTINCT ON statement to retrieve the first occurrence of the employee number for each set of rows defined by the ON () clause. The new table was created using the INTO clause. We then joined the Employees and Department Employee table on the primary key and the Employees and Titles tables on the primary key. The data was filtered on the to_date column to all the current employees, then filtered on the birth_date columns to get all the employees whose birth dates were between January 1, 1965 and December 31, 1965. The table was ordered by the employee number.

<img width="660" alt="Mentorship_eligibility" src="https://user-images.githubusercontent.com/60076980/153772378-077afb7f-a1ca-41de-a7be-7e04f0e4300d.png">

## Summary
### How many roles will need to be filled as the "silver tsunami" begins to make an impact?

From the Retirement_titles table we can see the breakdown of roles that have employees retiring soon:
- 25,916 Senior Engineers
- 24,926 Senior Staff
- 9,285 Engineers
- 7,636 Staff
- 3,603 Technique Leaders
- 1,090 Assistant Engineers
- 2 Managers

We can see that 50,842 of the 72,458 (70%) retiring employees are in senior roles and that 36,291 of the 72,458 (50%) retiring employees are in engineer positions.

### Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett-Hackard employees?
There are 1549 employees eligible for the mentorship program. Considering the size of the company and the number of retiring employees, this is not enough mentors.

<img width="466" alt="Mentorship_eligibility_count" src="https://user-images.githubusercontent.com/60076980/153775998-e2755a24-9551-42cb-8350-8fe694f34334.png">

By getting a count of the titles in the mentorship_eligibility table we can see the viable mentorship candidates.
<img width="294" alt="Mentorship_eligibility_titles" src="https://user-images.githubusercontent.com/60076980/153777473-19bab9e8-4b73-442c-b51a-ed5c9e4b0797.png">
