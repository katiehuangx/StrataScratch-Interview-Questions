# ♾ StrataScratch Interview Questions

[StrataScratch](https://www.stratascratch.com) is a data science platform with real interview questions from top companies, including FAANG companies.

I'll be solving SQL questions and sharing my answers.

### Table of Contents

## Level: Easy

<img width="657" alt="image" src="https://user-images.githubusercontent.com/81607668/172357989-cd618ae1-3fe9-4944-b720-39e8413f752f.png">

Result: salary_diff

```sql
SELECT 
  MAX(CASE WHEN d.department = 'marketing' THEN salary END) -
  MAX(CASE WHEN d.department = 'engineering' THEN salary END) as salary_diff
FROM db_employee e
INNER JOIN db_dept d
  on e.department_id = d.id
```

<img width="609" alt="image" src="https://user-images.githubusercontent.com/81607668/172358481-c6259889-4bc6-4c0a-8b41-3567d58fd4b7.png">

***
