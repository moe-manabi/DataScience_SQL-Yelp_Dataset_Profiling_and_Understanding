# DataScience_SQL-Yelp_Dataset_Profiling_and_Understanding
Profiling and Understanding a Dataset 
Part 1: Yelp Dataset Profiling and Understanding

1. Profile the data by finding the total number of records for each of the tables below:

Sample Query>>

select count (*) as total_rows /* returns the number of records in a table */
from Attribute; /* Place each table name here */ 
	
i. Attribute table = 10000
ii. Business table = 10000
iii. Category table = 10000
iv. Checkin table = 10000
v. elite_years table = 10000
vi. friend table = 10000
vii. hours table = 10000
viii. photo table = 10000
ix. review table = 10000
x. tip table = 10000
xi. user table = 10000
	


2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

i. Business = 10000 
select count(distinct id) as Total_distinct_Record /* Primary key was used */
from business;

ii. Hours = 1562 
select count(distinct business_id) as Total_distinct_Record /* foreign key used > business_id */
from hours;

iii. Category = 2643 
select count(distinct business_id) as Total_distinct_Record /* foreign key used > business_id */
from Category;

iv. Attribute = 1115 
select count(distinct business_id) as Total_distinct_Record /* foreign key used > business_id */
from Attribute;

v. Review = 10000
select count(distinct id) as Total_distinct_Record /* Primary key was used */
from Review;

vi. Checkin = 493
select count(distinct business_id) as Total_distinct_Record /* foreign key used > business_id */
from Checkin;

vii. Photo = 10000
select count(distinct id) as Total_distinct_Record /* Primary key was used */
from photo;

viii. Tip = 537
select count(distinct user_id) as Total_distinct_Record /* foreign key used > user_id */
from tip;

ix. User = 10000
select count(distinct id) as Total_distinct_Record /* Primary key was used */
from user;

x. Friend = 11
select count(distinct user_id) as Total_distinct_Record /* foreign key used > user_id */
from friend;

xi. Elite_years = 2780 
select count(distinct user_id) as Total_distinct_Record /* foreign key used > user_id */
from Elite_years;

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.	



3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

	Answer: "NO".
	
	
	SQL code used to arrive at answer:
select 
sum(case when id is null then 1 else 0 end) as Total_NULL,
sum(case when name is null then 1 else 0 end) as Total_NULL,
sum(case when review_count is null then 1 else 0 end) as Total_NULL,
sum(case when yelping_since is null then 1 else 0 end) as Total_NULL,
sum(case when useful is null then 1 else 0 end) as Total_NULL,
sum(case when funny is null then 1 else 0 end) as Total_NULL,
sum(case when cool is null then 1 else 0 end) as Total_NULL,
sum(case when fans is null then 1 else 0 end) as Total_NULL,
sum(case when average_stars is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_hot is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_more is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_profile is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_cute is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_list is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_note is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_plain is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_cool is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_funny is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_writer is null then 1 else 0 end) as Total_NULL,
sum(case when compliment_photos is null then 1 else 0 end) as Total_NULL
from user;


	


	
4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:


Sample query >>

select 
min(stars) as minmum_Stars,
max(stars) as maximum_Stars,
avg(stars) as average_stars
from review;



	i. Table: Review, Column: Stars
	
		min:1	max:5	avg:3.7082
		
	
	ii. Table: Business, Column: Stars
	
		min:1.0	max:5.0	avg:3.6549
		
	
	iii. Table: Tip, Column: Likes
	
		min:0	max:2	avg:0.0144
		
	
	iv. Table: Checkin, Column: Count
	
		min:1	max:53	 avg:1.9414
		
	
	v. Table: User, Column: Review_count
	
		min:0	max:2000	  avg:24.2995
		


5. List the cities with the most reviews in descending order:

SQL code used to arrive at answer:

select  city,count(review_count) as total
from business
group by city
order by total desc;
	
Copy and Paste the Result Below:
	
+-----------------+-------+
| city            | total |
+-----------------+-------+
| Las Vegas       |  1561 |
| Phoenix         |  1001 |
| Toronto         |   985 |
| Scottsdale      |   497 |
| Charlotte       |   468 |
| Pittsburgh      |   353 |
| MontrÃ©al        |   337 |
| Mesa            |   304 |
| Henderson       |   274 |
| Tempe           |   261 |
| Edinburgh       |   239 |
| Chandler        |   232 |
| Cleveland       |   189 |
| Gilbert         |   188 |
| Glendale        |   188 |
| Madison         |   176 |
| Mississauga     |   150 |
| Stuttgart       |   141 |
| Peoria          |   105 |
| Markham         |    80 |
| Champaign       |    71 |
| North Las Vegas |    70 |
| North York      |    64 |
| Surprise        |    60 |
| Richmond Hill   |    54 |
+-----------------+-------+
	
6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:

select 
name,
stars,
count(stars)
from business
where city='Avon'
group by stars;

Copy and Paste the Resulting Table Below (2 columns Ã¢â‚¬â€œ star rating and count):
+-----------------------------------------------+-------+--------------+
| name                                          | stars | count(stars) |
+-----------------------------------------------+-------+--------------+
| Portrait Innovations                          |   1.5 |            1 |
| Mr. Handyman of Cleveland's Northwest Suburbs |   2.5 |            2 |
| Mulligans Pub and Grill                       |   3.5 |            3 |
| Cambria hotel & suites Avon - Cleveland       |   4.0 |            2 |
| Dervish Mediterranean & Turkish Grill         |   4.5 |            1 |
| Hoban Pest Control                            |   5.0 |            1 |
+-----------------------------------------------+-------+--------------+

ii. Beachwood

SQL code used to arrive at answer:

select 
name,
stars,
count(stars)
from business
where city='Beachwood'
group by stars;

Copy and Paste the Resulting Table Below (2 columns Ã¢â‚¬â€œ star rating and count):
		
+----------------------------+-------+--------------+
| name                       | stars | count(stars) |
+----------------------------+-------+--------------+
| College Planning Network   |   2.0 |            1 |
| Avis Rent A Car            |   2.5 |            1 |
| Charley's Grilled Subs     |   3.0 |            2 |
| American Eagle Outfitters  |   3.5 |            2 |
| Hyde Park Prime Steakhouse |   4.0 |            1 |
| Origins                    |   4.5 |            2 |
| Studio Mz                  |   5.0 |            5 |
+----------------------------+-------+--------------+

7. Find the top 3 users based on their total number of reviews:
		
	SQL code used to arrive at answer:
	
select 
name,
review_count                 /* returns the user names and number of reviews */
from user                
order by review_count desc   /* this will ensure number of reviews is in descending order (largest to smallest) */
limit 3;                     /* limits the number of record to 3 */
		
	Copy and Paste the Result Below:
		
+--------+--------------+
| name   | review_count |
+--------+--------------+
| Gerald |         2000 |
| Sara   |         1629 |
| Yuri   |         1339 |
+--------+--------------+

8. Does posing more reviews correlate with more fans?

	Please explain your findings and interpretation of the results:
         >> No, user "Amy" has the highest number of fans with less reviews while user "Harald" having higher number of reviews with less fans

select
name,
fans,
review_count
from user
order by fans desc
limit 10;

+-----------+------+--------------+
| name      | fans | review_count |
+-----------+------+--------------+
| Amy       |  503 |          609 |
| Mimi      |  497 |          968 |
| Harald    |  311 |         1153 |
| Gerald    |  253 |         2000 |
| Christine |  173 |          930 |
| Lisa      |  159 |          813 |
| Cat       |  133 |          377 |
| William   |  126 |         1215 |
| Fran      |  124 |          862 |
| Lissa     |  120 |          834 |
+-----------+------+--------------+

	
9. Are there more reviews with the word "love" or with the word "hate" in them?

	Answer: Per below results there are more reviews with the word "love" in them comparing to the reviews with word "hate".

	
	SQL code used to arrive at answer:

select count (*)
from review
where text like '%love%'

+-----------+
| count (*) |
+-----------+
|      1780 |
+-----------+

select count (*)
from review
where text like '%hate%'

+-----------+
| count (*) |
+-----------+
|       232 |
+-----------+
	
	
10. Find the top 10 users with the most fans:

	SQL code used to arrive at answer:
select 
name,
fans
from user
order by fans desc
limit 10;
	
	
	Copy and Paste the Result Below:
+-----------+------+
| name      | fans |
+-----------+------+
| Amy       |  503 |
| Mimi      |  497 |
| Harald    |  311 |
| Gerald    |  253 |
| Christine |  173 |
| Lisa      |  159 |
| Cat       |  133 |
| William   |  126 |
| Fran      |  124 |
| Lissa     |  120 |
+-----------+------+

	
		

Part 2: Inferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. 
Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.

City >> phoenix
Category >> Restaurants
	
i. Do the two groups you chose to analyze have a different distribution of hours? 

Yes


ii. Do the two groups you chose to analyze have a different number of reviews?
Yes
         
         
iii. Are you able to infer anything from the location data provided between these two groups? Explain.

It appears that businesses with similar rating also share a postal code to some degree. Additionally, businesses with longer hours of operation have higher ratings comparing to those with limited hours of operation 

SQL code used for analysis:

select 
b.name as Business_Name,
c.category as Business_Category,
b.city,
b.stars,
h.hours,
b.postal_code,
b.review_count
from business b inner join category c
on b.id=c.business_id 
inner join hours h 
on h.business_id=c.business_id
where 
b.city='Phoenix'
and c.category='Restaurants'
group by b.stars;

+----------------------------------------+-------------------+---------+-------+----------------------+-------------+--------------+
| Business_Name                          | Business_Category | city    | stars | hours                | postal_code | review_count |
+----------------------------------------+-------------------+---------+-------+----------------------+-------------+--------------+
| McDonald's                             | Restaurants       | Phoenix |   2.0 | Saturday|5:00-0:00   | 85004       |            8 |
| Gallagher's                            | Restaurants       | Phoenix |   3.0 | Saturday|9:00-2:00   | 85024       |           60 |
| Five Guys                              | Restaurants       | Phoenix |   3.5 | Saturday|10:00-22:00 | 85008       |           63 |
| Bootleggers Modern American Smokehouse | Restaurants       | Phoenix |   4.0 | Saturday|11:00-22:00 | 85028       |          431 |
| Charlie D's Catfish & Chicken          | Restaurants       | Phoenix |   4.5 | Saturday|11:00-18:00 | 85034       |            7 |
+----------------------------------------+-------------------+---------+-------+----------------------+-------------+--------------+
		
		
2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.
		
i. Difference 1:
The business that is open have higher number of reviews         
         
ii. Difference 2:
The business that is open have longer hours of operation         
         
         
SQL code used for analysis:

select 
b.name as Business_Name,
c.category as Business_Category,
b.city,
b.stars,
h.hours,
b.postal_code,
b.review_count,
b.is_open
from business b inner join category c
on b.id=c.business_id 
inner join hours h 
on h.business_id=c.business_id
where 
b.city='Phoenix'
and c.category='Restaurants'
group by b.is_open;

+----------------------------------------+-------------------+---------+-------+----------------------+-------------+--------------+---------+
| Business_Name                          | Business_Category | city    | stars | hours                | postal_code | review_count | is_open |
+----------------------------------------+-------------------+---------+-------+----------------------+-------------+--------------+---------+
| Charlie D's Catfish & Chicken          | Restaurants       | Phoenix |   4.5 | Saturday|11:00-18:00 | 85034       |            7 |       0 |
| Bootleggers Modern American Smokehouse | Restaurants       | Phoenix |   4.0 | Saturday|11:00-22:00 | 85028       |          431 |       1 |
+----------------------------------------+-------------------+---------+-------+----------------------+-------------+--------------+---------+
	
	
3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
i. Indicate the type of analysis you chose to do:
         I want to help investors understand what businesses are going to be more likely to fail. 
         
ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:
         The results will provide categories of business that ended in failure and provide some statistical information on where and what kind of business they were.
	   We can draw insight from what business are more likely to fail in specific location. not having certain attributes led a business to fail or having certain ones did not help a business thrive. 
                  
iii. Output of your finished dataset:
         
         
iv. Provide the SQL code you used to create your final dataset:
select
c.category,
b.name,
t.name as attribute,
t.value,
b.city,
b.state,
b.postal_code,
b.stars,
b.neighborhood,
b.review_count,
b.is_open
from business b inner join category c
on c.business_id=b.id
inner join attribute t on t.business_id=b.id
where b.is_open='0'
and c.category='Food';
