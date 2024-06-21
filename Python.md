
### 📌 [Microsoft | Finding Updated Records](https://platform.stratascratch.com/coding/10299-finding-updated-records?code_type=2)

We have a table with employees and their salaries, however, some of the records are old and contain outdated salary information. Find the current salary of each employee assuming that salaries increase each year. Output their id, first name, last name, department ID, and current salary. Order your list by employee ID in ascending order.

```python
# Import your libraries
import pandas as pd

# Start writing code
ms_employee_salary.head()

# Group data by id, first name, last name, and department id and find the maximum salary which represents the current salary
ms_employee_salary.groupby(['id', 'first_name', 'last_name', 'department_id'])['salary']
  .max()
  .reset_index()

```

<img width="686" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/538b10e8-e31d-45c1-8dbb-18a5bcd4d810">

### 📌 [DoorDash | Bikes Last Used](https://platform.stratascratch.com/coding/10176-bikes-last-used?code_type=2)

```python
# Import your libraries
import pandas as pd

# Start writing code
dc_bikeshare_q1_2012.head()

# Group by bike number and find by maximum end time for each bike. Then, sort end time values in descending order
dc_bikeshare_q1_2012.groupby('bike_number')['end_time']
  .max()
  .reset_index()
  .sort_values(by='end_time', ascending=False)
```

<img width="540" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/05d3069a-7b53-4031-91b8-b6e750357b12">
