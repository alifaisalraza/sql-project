Answer the following questions and provide the SQL queries used to find the answer.

**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**

SQL Queries:

select "country", "city", max("totalTransactionRevenue") as Highest_Transaction_Revenue
from all_sessions where "totalTransactionRevenue" is not null
group by "country", "city"
order by Highest_Transaction_Revenue desc

Answer:

country	city	highest_transaction_revenue
United States	not available in demo dataset	1015480000
United States	Atlanta	742480000
United States	Sunnyvale	649240000
Israel	Tel Aviv-Yafo	602000000
United States	Los Angeles	363000000
United States	Seattle	358000000
Australia	Sydney	358000000
United States	Chicago	306000000
United States	Palo Alto	305000000
United States	San Francisco	301000000
United States	Nashville	157000000
United States	Mountain View	156000000
United States	San Jose	154000000
United States	New York	152000000
United States	Austin	122000000
United States	San Bruno	103770000
Canada	Toronto	82160000
Canada	New York	67990000
United States	Houston	38980000
United States	Columbus	21990000
Switzerland	Zurich	16990000


**Question 2: What is the average number of products ordered from visitors in each city and country?**

SQL Queries:

Answer:

**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**

SQL Queries:

Answer:

**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**

SQL Queries:

Answer:

**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

Answer:
