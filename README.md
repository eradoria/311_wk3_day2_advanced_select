# Advanced SELECT

## Setup

You should have already created a Google Cloud account, created an instance and built a database (yesterday), as well as installed MySQL Workbench and made a connection to the database you've created.. In this lesson we will practice querying data.

* Open MySQL Workbench

## Part 1 - Initialize data

We'll use the same database as we did yesterday but this new initialization will delete or `DROP` our existing table of `users` and replace it with three new tables: `usersAddress`, `users`, & `usersContact`. To do this:

* Make sure you've selected the "admin" database in MySQL Workbench

* Create a new query tab
  * Click the button on the top left that has a SQL file with a "plus" icon on it

* Click the folder icon in your query tab to open a new file

* Select the "initialize.sql" script that lives in this repo (you've hopefully cloned it into your 311-JSDev folder or somewhere else)

* Click the lightning bolt icon to run the query

* If you refresh your schemas you should see a "users", "usersContact" and "usersAddress" table

## Part 2 - Query data

We are going to run a couple SQL queries and put the answers in the "Query Responses" section of this README. The query instructions are intentionally written in plain english. It's up to you to translate that into a SELECT statement.

1. Get a sum of all the user_ids from the `usersAddress` table grouped by state. Enter the values for the specific states below.
  SELECT state, SUM(user_id) as users; FROM usersAddress; GROUP BY state; Order by users desc
  
  # state, users
'CA', '17324'
'NY', '13581'
'NJ', '13560'
'TX', '7908'
 

2. Find the most popular area code in the `usersContact` table. 
  * Hint: SUBSTR, GROUP BY
   select COUNT(*) as sum, substring(phone1,1,3) as area_code; from usersContact ; group by area_code; order by sum desc
  
  sum, area_code
  '18', '973'

3. Find the MIN first_name, the county, and a count of all users in that county for counties with more than 10 users. There will be four results. List the last one. 
  * Hint: MIN, COUNT, JOIN, GROUP BY, HAVING
  select   MIN(first_name), usersAddress.county, COUNT(user_id) as users; from users; INNER JOIN usersAddress ON users.id = usersAddress.user_id; group by county; having users > 10

# MIN(first_name), county, users
'Alaine', 'Orange', '11'


## Query Responses

1. Sums
  * AK:
  * CT
  * TX:
  * WY:

2.
  * Area code:

3.
  * first_name:
  * county:
  * county total:


## Summary

We're starting to get pretty advanced with our SQL queries. Keep researching other advanced SELECT statements and get ready to foray into [INSERTs and UPDATEs and DELETEs, oh CRUD](https://www.youtube.com/watch?v=-HrfbV16-FQ)!.
