# ♾ StrataScratch Interview Questions

[StrataScratch](https://www.stratascratch.com) is a data science platform with real interview questions from top companies, including FAANG companies.

I'll be solving SQL questions and sharing my answers.

### Table of Contents

- [Level: Easy](##level-easy)
- [Intermediate](##level-intermediate)
- [Hard](##level-hard)

***

## Level: Easy

### 📌 Salaries Differences
[Question: ](https://platform.stratascratch.com/coding/10308-salaries-differences?code_type=1) Write a query that calculates the difference between the highest salaries found in the marketing and engineering departments. Output just the absolute difference in salaries.

```sql
SELECT 
  MAX(CASE WHEN d.department = 'marketing' THEN salary END) - 
    MAX(CASE WHEN d.department = 'engineering' THEN salary END) as salary_diff
FROM db_employee e
INNER JOIN db_dept d
  ON e.department_id = d.id
```

<img width="597" alt="image" src="https://user-images.githubusercontent.com/81607668/172528878-b77567f6-9890-40c5-9040-23caf7a70204.png">

### 📌 Popularity of Hack
[Question: ](https://platform.stratascratch.com/coding/10061-popularity-of-hack?code_type=1) Meta/Facebook has developed a new programing language called Hack.To measure the popularity of Hack they ran a survey with their employees. The survey included data on previous programing familiarity as well as the number of years of experience, age, gender and most importantly satisfaction with Hack. Due to an error location data was not collected, but your supervisor demands a report showing average popularity of Hack by office location. Luckily the user IDs of employees completing the surveys were stored.

Based on the above, find the average popularity of the Hack per office location. Output the location along with the average popularity.

```sql
SELECT 
  e.location, 
  AVG(popularity) AS avg_popularity
FROM facebook_employees e
INNER JOIN facebook_hack_survey s
  ON e.id = s.employee_id
GROUP BY e.location;
```

<img width="600" alt="image" src="https://user-images.githubusercontent.com/81607668/172529617-19b1c2a3-a99a-4f09-a433-c056675c6622.png">

### 📌 Finding Updated Records
[Question: ](https://platform.stratascratch.com/coding/10299-finding-updated-records?code_type=1) We have a table with employees and their salaries, however, some of the records are old and contain outdated salary information. Find the current salary of each employee assuming that salaries increase each year. Output their id, first name, last name, department ID, and current salary. Order your list by employee ID in ascending order.

```sql
-- Rank each employee's salary by descending order so that the higher salary which is the latest salary is ranked as 1st
WITH current_salary_cte AS (
  SELECT 
    id, first_name, last_name, department_id, salary,
    ROW_NUMBER() OVER (PARTITION BY id ORDER BY salary DESC) AS ranking
  FROM ms_employee_salary)

SELECT *
FROM current_salary_cte
WHERE ranking = 1;
```

<img width="587" alt="image" src="https://user-images.githubusercontent.com/81607668/172530857-ff2076e8-a423-4954-8ade-f5755198ea4e.png">

### 📌 Average Salaries
[Question: ](https://platform.stratascratch.com/coding/9917-average-salaries?code_type=1) Compare each employee's salary with the average salary of the corresponding department. Output the department, first name, and salary of employees along with the average salary of that department.

```sql
WITH avg_salary_cte AS (
  SELECT 
    department, AVG(salary) AS avg_salary
  FROM employee
  GROUP BY department)

SELECT e.department, e.first_name, e.salary, s.avg_salary
FROM employee e
INNER JOIN avg_salary_cte s
  ON e.department = s.department
ORDER BY e.department, e.first_name;
```

<img width="588" alt="image" src="https://user-images.githubusercontent.com/81607668/172532281-b01099f2-1792-4269-84b7-ca302f967eec.png">

### 📌 Count the number of user events performed by MacBookPro users

[Question: ](https://platform.stratascratch.com/coding/9653-count-the-number-of-user-events-performed-by-macbookpro-users?code_type=1) Count the number of user events performed by MacBookPro users. Output the result along with the event name. Sort the result based on the event count in the descending order.

```sql
SELECT event_name, COUNT(user_id) AS user_count
FROM playbook_events
WHERE device = 'macbook pro'
GROUP BY event_name
ORDER BY user_count DESC;
```

<img width="594" alt="image" src="https://user-images.githubusercontent.com/81607668/172532882-15b20a1c-f749-4306-bd1f-f474bee06ae5.png">

### 📌 Churro Activity Date
[Question: ](https://platform.stratascratch.com/coding/9688-churro-activity-date?code_type=1) Find the activity date and the pe_description of facilities with the name 'STREET CHURROS' and with a score of less than 95 points.

```sql
SELECT activity_date, pe_description
FROM los_angeles_restaurant_health_inspections
WHERE facility_name = 'STREET CHURROS'
  AND score < 95;
```

<img width="541" alt="image" src="https://user-images.githubusercontent.com/81607668/172535133-fca767b5-f69c-44fc-899c-10ec97196f6c.png">

### 📌 Find libraries who haven't provided the email address in circulation year 2016 but their notice preference definition is set to email
[Question: ](https://platform.stratascratch.com/coding/9924-find-libraries-who-havent-provided-the-email-address-in-2016-but-their-notice-preference-definition-is-set-to-email?code_type=1) Find libraries who haven't provided the email address in circulation year 2016 but their notice preference definition is set to email. Output the library code.

```sql
SELECT DISTINCT home_library_code
FROM library_usage
WHERE provided_email_address IS FALSE
  AND circulation_active_year = 2016
  AND notice_preference_definition = 'email';
```

<img width="477" alt="image" src="https://user-images.githubusercontent.com/81607668/172536587-2e83197d-9eab-4640-a7a9-dc9fc7d6c23d.png">

### 📌 Find the base pay for Police Captains
[Question: ](https://platform.stratascratch.com/coding/9972-find-the-base-pay-for-police-captains?code_type=1) Find the base pay for Police Captains. Output the employee name along with the corresponding base pay.

```sql
SELECT employeename, basepay
FROM sf_public_salaries
WHERE jobtitle LIKE '%CAPTAIN%';
```

<img width="539" alt="image" src="https://user-images.githubusercontent.com/81607668/172537372-2921e6bb-59f3-442a-a301-62f7a69b6b09.png">

### 📌 Find the most profitable company in the financial sector of the entire world along with its continent
[Question: ](https://platform.stratascratch.com/coding/9663-find-the-most-profitable-company-in-the-financial-sector-of-the-entire-world-along-with-its-continent?code_type=1) Find the most profitable company from the financial sector. Output the result along with the continent.

```sql
SELECT company, continent
FROM forbes_global_2010_2014
WHERE sector = 'Financials'
ORDER BY profits DESC
LIMIT 1;
```

<img width="568" alt="image" src="https://user-images.githubusercontent.com/81607668/172537717-28380217-aab4-4fa1-9a22-a1a0c42ed737.png">

### 📌 Bikes Last Used
[Question: ](https://platform.stratascratch.com/coding/10176-bikes-last-used?code_type=1) Find the last time each bike was in use. Output both the bike number and the date-timestamp of the bike's last use (i.e., the date-time the bike was returned). Order the results by bikes that were most recently used.

```sql
WITH ranked_by_recency AS (
  SELECT 
    bike_number, 
    end_time, 
    ROW_NUMBER() OVER (PARTITION BY bike_number ORDER BY end_time DESC) AS ranking
  FROM dc_bikeshare_q1_2012)

SELECT bike_number, end_time
FROM ranked_by_recency
WHERE ranking = 1;
```

<img width="590" alt="image" src="https://user-images.githubusercontent.com/81607668/172539547-ae00bdd5-c04d-4801-bc9e-e829dc60d3d3.png">

### 📌 Lyft Driver Wages
[Question: ](https://platform.stratascratch.com/coding/10003-lyft-driver-wages?code_type=1) Find all Lyft drivers who earn either equal to or less than 30k USD or equal to or more than 70k USD. Output all details related to retrieved records.

```sql
SELECT *
FROM lyft_drivers
where yearly_salary <= 30000 OR yearly_salary >= 70000;
```

<img width="583" alt="image" src="https://user-images.githubusercontent.com/81607668/172540424-571d9957-db0a-4322-9394-cdb578ca4d58.png">

### 📌 Find all posts which were reacted to with a heart
[Question: ](https://platform.stratascratch.com/coding/10087-find-all-posts-which-were-reacted-to-with-a-heart?code_type=1) Find all posts which were reacted to with a heart.

```sql
SELECT DISTINCT p.*
FROM facebook_posts p
INNER JOIN facebook_reactions r
    ON p.poster = r.poster
WHERE r.reaction = 'heart'
LIMIT 1; -- Note
```

Note: _The official solution has only 1 retrieved record, however the question did not specifically request for the solution to be limited to one. Upon browsing the Solution Discussion, other users also found the official solution to be incorrect and it should be without `LIMIT 1`. For the sake of solving the question, I'm limiting my retrieved records to 1 record._

<img width="592" alt="image" src="https://user-images.githubusercontent.com/81607668/172541703-bad2f432-9463-4976-b274-b942b242f74e.png">

### 📌 Count the number of movies that Abigail Breslin nominated for oscar
[Question: ](https://platform.stratascratch.com/coding/10128-count-the-number-of-movies-that-abigail-breslin-nominated-for-oscar?code_type=1) Count the number of movies that Abigail Breslin was nominated for an oscar.

```sql
SELECT COUNT(DISTINCT movie) AS movie_count
FROM oscar_nominees
WHERE nominee = 'Abigail Breslin';
```

<img width="215" alt="image" src="https://user-images.githubusercontent.com/81607668/172542574-f557cfac-b3bc-4201-aefa-953700d04d02.png">

***

## Level: Medium

### 📌 Workers With The Highest Salaries
[Question: ](https://platform.stratascratch.com/coding/10353-workers-with-the-highest-salaries?code_type=1) Find the titles of workers that earn the highest salary. Output the highest-paid title or multiple titles that share the highest salary.

```sql
-- Ranked salary using DENSE_RANK() whereby records with the same salaries are assigned with same ranking
WITH grouped_salary AS (
  SELECT 
    t.worker_title, w.salary, 
    DENSE_RANK() OVER (ORDER BY w.salary DESC) AS ranking
  FROM worker w
  INNER JOIN title t
    ON w.worker_id = t.worker_ref_id)
    
SELECT worker_title
FROM grouped_salary
WHERE ranking = 1;
```

<img width="314" alt="image" src="https://user-images.githubusercontent.com/81607668/172554310-647f9db6-d4a0-4c73-a8ce-780db82194c3.png">





