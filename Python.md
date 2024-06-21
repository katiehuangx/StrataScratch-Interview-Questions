
### 📌 [Microsoft | Finding Updated Records](https://platform.stratascratch.com/coding/10299-finding-updated-records?code_type=2)

We have a table with employees and their salaries, however, some of the records are old and contain outdated salary information. Find the current salary of each employee assuming that salaries increase each year. Output their id, first name, last name, department ID, and current salary. Order your list by employee ID in ascending order.

```python
# Import your libraries
import pandas as pd

# Start writing code
ms_employee_salary.head()

# Group data by id, first name, last name, and department id.
# Find the maximum salary which represents the current salary.
ms_employee_salary.groupby(['id', 'first_name', 'last_name', 'department_id'])['salary']
  .max()
  .reset_index()

```

<img width="686" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/538b10e8-e31d-45c1-8dbb-18a5bcd4d810">

### 📌 [Lyft/DoorDash | Bikes Last Used](https://platform.stratascratch.com/coding/10176-bikes-last-used?code_type=2)

Find the last time each bike was in use. Output both the bike number and the date-timestamp of the bike's last use (i.e., the date-time the bike was returned). Order the results by bikes that were most recently used.

```python
# Import your libraries
import pandas as pd

# Start writing code
dc_bikeshare_q1_2012.head()

# Group by bike number and find by maximum end time for each bike.
# Then, sort end time values in descending order.
dc_bikeshare_q1_2012.groupby('bike_number')['end_time'] # Group by bike number
  .max() # Find the maximum end time
  .reset_index()
  .sort_values(by='end_time', ascending=False) # Sort end time in descending order
```

<img width="540" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/05d3069a-7b53-4031-91b8-b6e750357b12">

### 📌 [Airbnb/Expedia | Reviews of Hotel Arena](https://platform.stratascratch.com/coding/10166-reviews-of-hotel-arena?code_type=2)

Find the number of rows for each review score earned by 'Hotel Arena'. Output the hotel name (which should be 'Hotel Arena'), review score along with the corresponding number of rows with that score for the specified hotel.

```python
# Import your libraries
import pandas as pd

# Start writing code
hotel_reviews.head()

# Find number of rows for each review score, meaning to group the review score.
# Filter for hotel name == 'Hotel Arena'
# Output hotel name, review score, and number of rows
hotel_reviews[hotel_reviews['hotel_name'] == 'Hotel Arena'] # Filter for 'Hotel Arena' hotels
  .groupby(['reviewer_score', 'hotel_name'])
  .size() # Count number of rows
  .reset_index(name='n_reviews') # Name the new column as 'n_reviews'
```

<img width="673" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/66c31397-2a76-4f6e-b3cc-eca69d8efbf4">
