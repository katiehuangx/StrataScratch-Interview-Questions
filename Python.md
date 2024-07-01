
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

### 📌 [Spotify | Easy | Find how many times each artist appeared on the Spotify ranking list](https://platform.stratascratch.com/coding/9992-find-artists-that-have-been-on-spotify-the-most-number-of-times?code_type=2)

Find how many times each artist appeared on the Spotify ranking list. Output the artist name along with the corresponding number of occurrences. Order records by the number of occurrences in descending order.

```python
# Import your libraries
import pandas as pd

# Start writing code
spotify_worldwide_daily_song_ranking.head()

spotify_worldwide_daily_song_ranking
  .groupby('artist') # Group results by artist
  .size() # Count number of rows
  .reset_index(name='n_occurences') # Re-name number of rows as 'n_occurences'
  .sort_values(by='n_occurences', ascending=False) # Sort results in descending order
```

### 📌 [City of San Francisco | Easy | Find the base pay for Police Captains](https://platform.stratascratch.com/coding/9972-find-the-base-pay-for-police-captains?code_type=2)

Find the base pay for Police Captains. Output the employee name along with the corresponding base pay.

```python
# Import your libraries
import pandas as pd

# Start writing code
sf_public_salaries.head()

# Filter results for job title containing 'Captain' in a case-insensitive manner
captain_salaries = sf_public_salaries[sf_public_salaries['jobtitle'].str.contains('Captain', case=False)]

# Output results showing employee name and base pay
captain_salaries[['employeename', 'basepay']]
```

### 📌 [City of San Francisco | Easy | Find libraries who haven't provided the email address in circulation year 2016 but their notice preference definition is set to email](https://platform.stratascratch.com/coding/9924-find-libraries-who-havent-provided-the-email-address-in-2016-but-their-notice-preference-definition-is-set-to-email?code_type=2)

Find libraries who haven't provided the email address in circulation year 2016 but their notice preference definition is set to email. Output the library code.

```python
# Import your libraries
import pandas as pd

# Start writing code
library_usage.head()

# Filter rows based on specified conditions
filtered_libraries = library_usage[(library_usage['circulation_active_year'] == 2016 # Filter circulation year 2016
  & (library_usage['notice_preference_definition'] == 'email') # Filter notice preference as email
  & (library_usage['provided_email_address'] == False)] # Filter libraries who did not provide email

# Get unique values of 'home_library_code' column  
filtered_libraries['home_library_code'].unique()
```

<img width="282" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/160c3b60-a818-4549-aa44-6bd01e6c50ad">

### 📌 [Amazon/Shopify | Easy | Order Details](https://platform.stratascratch.com/coding/9913-order-details?code_type=2)

Find order details made by Jill and Eva. Consider the Jill and Eva as first names of customers. Output the order date, details and cost along with the first name. Order records based on the customer id in ascending order.

```python
# Import your libraries
import pandas as pd

# Start writing code
customers.head()

# Filter rows where 'first_name' is either 'Jill' or 'Eva'
filtered_customers = customers.loc[(customers['first_name'] == 'Jill') | (customers['first_name'] == 'Eva')]

# Select 'id' and 'first_name' columns from filtered_customers
selected_customers = filtered_customers[['id', 'first_name']]

# Merge 'selected_customers' with 'orders' on 'cust_id'
merged_orders = pd.merge(
    selected_customers,
    orders[['cust_id', 'order_date', 'order_details', 'total_order_cost']],
    left_on='id',
    right_on='cust_id',
    how='inner'
    ).sort_values(by='cust_id', ascending=True) # Sort result by 'cust_id' in ascending order

# Select and reorder columns for the final output
merged_orders[['order_date', 'order_details', 'total_order_cost', 'first_name']]
```

<img width="646" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/15b53443-53ac-4d7e-92b6-2c5813bce40e">

### 📌 [Apple/Amazon | Easy | Customer Details](https://platform.stratascratch.com/coding/9891-customer-details?code_type=2)

Find the details of each customer regardless of whether the customer made an order. Output the customer's first name, last name, and the city along with the order details. Sort records based on the customer's first name and the order details in ascending order.

```python
# Import your libraries
import pandas as pd

# Start writing code
customers.head()

# Merge customers and orders on 'id' and 'cust_id'
merged_data = pd.merge(
    customers[['id', 'first_name', 'last_name', 'city']],
    orders[['cust_id', 'order_details']],
    left_on='id',
    right_on='cust_id',
    how='left'
    )

# Drop 'id' and 'cust_id' columns from the merged_data
# Sort output by 'first_name' and 'order_details' in ascending order   
merged_data.drop(columns=['id', 'cust_id']).sort_values(by=['first_name', 'order_details'], ascending=True)
```

<img width="633" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/e56b51d4-0023-4734-a9d5-94619c471940">

### 📌 [Amazon | Easy | Number of Workers by Department Starting in April or Later](https://platform.stratascratch.com/coding/9847-find-the-number-of-workers-by-department?code_type=2)

Find the number of workers by department who joined in or after April. Output the department name along with the corresponding number of workers. Sort records based on the number of workers in descending order.

```python
# Import your libraries
import pandas as pd

# Start writing code
worker.head()

# Convert 'joining_date' to datetime type
worker['joining_date'] = pd.to_datetime(worker['joining_date'])

# Filter workers who joined on or after April 1st, 2014 at midnight
filtered_workers = worker[worker['joining_date'] >= '2014-04-01 00:00:00']

# Group workers by department and count number of rows
# Sort output by number of rows in descending order
filtered_workers.groupby('department').size().reset_index(name='num_workers').sort_values(by='num_workers', ascending=False)
```

<img width="480" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/025b51ef-ed1f-41b5-a8e6-44b7b8d7547f">

### 📌 [Microsoft/Amazon | Easy | Admin Department Employees Beginning in April or Later](https://platform.stratascratch.com/coding/9845-find-the-number-of-employees-working-in-the-admin-department?code_type=2)

Find the number of employees working in the Admin department that joined in April or later.

```python
# Import your libraries
import pandas as pd

# Start writing code
worker.head()

# Convert 'joining_date' to datetime type
worker['joining_date'] = pd.to_datetime(worker['joining_date'])

# Filter workers who joined on or after January 1st, 2014 and belong to 'Admin' department
filtered_workers = worker[(worker['joining_date'] >= '2014-04-01 00:00:00') & (worker['department'] == 'Admin')]

# Get number of rows using shape
filtered_workers.shape[0]
```

<img width="243" alt="image" src="https://github.com/katiehuangx/StrataScratch-Interview-Questions/assets/81607668/c9a7a427-62d2-49e0-830a-0fa7a7b70734">


