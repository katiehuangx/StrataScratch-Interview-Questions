
### 📌 [Microsoft | Easy | Finding Updated Records](https://platform.stratascratch.com/coding/10299-finding-updated-records?code_type=2)

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

### 📌 [Lyft/DoorDash | Easy | Bikes Last Used](https://platform.stratascratch.com/coding/10176-bikes-last-used?code_type=2)

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

### 📌 [Airbnb/Expedia | Easy | Reviews of Hotel Arena](https://platform.stratascratch.com/coding/10166-reviews-of-hotel-arena?code_type=2)

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
  .groupby(['reviewer_score', 'hotel_name']) # Group by 'reviewer_score' and 'hotel_name'
  .size() # Count number of rows
  .reset_index(name='n_reviews') # Name the new column as 'n_reviews'
```

<img width="673" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/66c31397-2a76-4f6e-b3cc-eca69d8efbf4">

### 📌 [Google/Netflix | Easy | Count the number of movies that Abigail Breslin nominated for oscar](https://platform.stratascratch.com/coding/10128-count-the-number-of-movies-that-abigail-breslin-nominated-for-oscar?code_type=2)

Count the number of movies that Abigail Breslin was nominated for an oscar.

```python
# Import your libraries
import pandas as pd

# Start writing code
oscar_nominees.head()

# Filter for actor Abigail Breslin and count number of rows
len(oscar_nominees[oscar_nominees['nominee'] == 'Abigail Breslin'])
```

<img width="251" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/d7304f29-beac-4ba1-9a61-08c43dcd0382">

### 📌 [Meta | Easy | Find all posts which were reacted to with a heart](https://platform.stratascratch.com/coding/10087-find-all-posts-which-were-reacted-to-with-a-heart?code_type=2)

Find all posts which were reacted to with a heart. For such posts output all columns from facebook_posts table.

```python
# Import your libraries
import pandas as pd

# Start writing code
facebook_reactions.head()

# Filter for heart reactions and get unique post IDs
# .loc is used to access a group of rows and columns by labels.
heart_post_id = facebook_reactions.loc[facebook_reactions['reaction'] == 'heart', 'post_id'].unique()

# Filter facebook_posts for posts with IDs in heart_post_ids
facebook_posts[facebook_posts['post_id'].isin(heart_post_id)]
```

<img width="896" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/0cb45116-ed85-4313-af23-9334c75c5d55">

### 📌 [Meta | Easy | Popularity of Hack](https://platform.stratascratch.com/coding/10061-popularity-of-hack/solutions?code_type=2)

Find the average popularity of the Hack per office location. Output the location along with the average popularity.

```python
# Import your libraries
import pandas as pd

# Start writing code
facebook_employees.head() # id, location
facebook_hack_survey.head() # employee_id, popularity

# Merge facebook_employees and facebook_hack_survey
average_popularity_by_location = pd.merge(
    facebook_employees[['id', 'location']], 
    facebook_hack_survey[['employee_id', 'popularity']], 
    left_on='id', 
    right_on='employee_id', 
    how='left')

# Calculate average popularity by location
average_popularity_by_location.groupby('location')['popularity'].mean().reset_index()
```

<img width="609" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/da3a538a-0280-49c8-a983-fe800fa0b86b">

### 📌 [Lyft | Easy | Lyft Driver Wages](https://platform.stratascratch.com/coding/10003-lyft-driver-wages?code_type=2)

Find all Lyft drivers who earn either equal to or less than 30k USD or equal to or more than 70k USD. Output all details related to retrieved records.

```python
# Import your libraries
import pandas as pd

# Start writing code
lyft_drivers.head()

lyft_drivers[(lyft_drivers['yearly_salary'] <= 30000) | (lyft_drivers['yearly_salary'] >= 70000)]
```

<img width="643" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/eafa7555-37ac-4865-b2cc-31b2fa0b6db4">


