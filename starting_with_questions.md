Answer the following questions and provide the SQL queries used to find the answer.

**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**

SQL Queries:

```sql select "country", "city", max("totalTransactionRevenue") as Highest_Transaction_Revenue
from all_sessions_cpy where "totalTransactionRevenue" != 0
group by "country", "city"
order by Highest_Transaction_Revenue desc limit 15```

Answer:
"country"	"city"	"highest_transaction_revenue"
"United States"	"not available in demo dataset"	1015
"United States"	"Atlanta"	742
"United States"	"Sunnyvale"	649
"Israel"	"Tel Aviv-Yafo"	602
"United States"	"Los Angeles"	363
"United States"	"Seattle"	358
"Australia"	"Sydney"	358
"United States"	"Chicago"	306
"United States"	"Palo Alto"	305
"United States"	"San Francisco"	301
"United States"	"Nashville"	157
"United States"	"Mountain View"	156
"United States"	"San Jose"	154
"United States"	"New York"	152
"United States"	"Austin"	122


**Question 2: What is the average number of products ordered from visitors in each city and country?**

SQL Queries: 
```select "country", "city", cast(avg("productQuantity") as integer) as Avg_Num_of_Products
from all_sessions_cpy where "productQuantity" !=0
group by "country", "city"
order by Avg_Num_of_Products desc limit 15```

Answer:
"country"	"city"	"avg_num_of_products"
"United States"	"not available in demo dataset"	11
"Spain"	"Madrid"	10
"United States"	"Salem"	8
"United States"	"Atlanta"	4
"United States"	"Houston"	2
"India"	"Bengaluru"	1
"Ireland"	"Dublin"	1
"Mexico"	"not available in demo dataset"	1
"United States"	"(not set)"	1
"United States"	"Ann Arbor"	1
"United States"	"Chicago"	1
"Argentina"	"not available in demo dataset"	1
"United States"	"Dallas"	1
"United States"	"Detroit"	1
"United States"	"Los Angeles"	1


**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**

SQL Queries:
```select "v2ProductCategory", "country", "city", count (*) as Num_of_Products
from all_sessions_cpy where "productQuantity" != 0
group by "v2ProductCategory", "country", "city"
order by Num_of_Products desc limit 20```

Answer:
"v2ProductCategory"	"country"	"city"	"num_of_products"
"Home/Nest/Nest-USA/"	"United States"	"Mountain View"	3
"Home/Nest/Nest-USA/"	"United States"	"not available in demo dataset"	3
"Electronics"	"United States"	"not available in demo dataset"	2
"${escCatTitle}"	"Spain"	"Madrid"	1
"${escCatTitle}"	"United States"	"Mountain View"	1
"${escCatTitle}"	"United States"	"New York"	1
"${escCatTitle}"	"United States"	"Houston"	1
"(not set)"	"Mexico"	"not available in demo dataset"	1
"(not set)"	"United States"	"Columbus"	1
"(not set)"	"United States"	"New York"	1
"(not set)"	"United States"	"Salem"	1
"Apparel"	"India"	"Bengaluru"	1
"Apparel"	"United States"	"Mountain View"	1
"Bags"	"United States"	"Atlanta"	1
"Drinkware"	"United States"	"Detroit"	1
"Bags"	"United States"	"not available in demo dataset"	1
"${escCatTitle}"	"United States"	"not available in demo dataset"	1
"Headgear"	"France"	"not available in demo dataset"	1
"Home/Apparel/Headgear/"	"United States"	"not available in demo dataset"	1
"${escCatTitle}"	"United States"	"(not set)"	1


**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**

SQL Queries:
```select "v2ProductName", "country", "city", sum ("productQuantity") as Num_of_Products_Sold
from all_sessions_cpy where "productQuantity" != 0
group by "v2ProductName", "country", "city"
order by Num_of_Products_Sold desc```

Answer:
"v2ProductName"	"country"	"city"	"num_of_products_sold"
"Leatherette Journal"	"United States"	"not available in demo dataset"	65
"Reusable Shopping Bag"	"United States"	"not available in demo dataset"	50
"Waze Dress Socks"	"Spain"	"Madrid"	10
"Red Spiral Google Notebook"	"United States"	"Salem"	8
"Nest® Cam Outdoor Security Camera - USA"	"United States"	"not available in demo dataset"	4
"Reusable Shopping Bag"	"United States"	"Atlanta"	4
"Nest® Protect Smoke + CO White Wired Alarm-USA"	"United States"	"New York"	2
"Google Sunglasses"	"United States"	"Houston"	2
"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	"United States"	"Mountain View"	2
"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"United States"	"New York"	2
"Google Men's Bike Short Sleeve Tee Charcoal"	"United States"	"Mountain View"	1
"Google Men's Long Sleeve Raglan Ocean Blue"	"United States"	"not available in demo dataset"	1
"Google Men's Pullover Hoodie Grey"	"United States"	"Los Angeles"	1
"Google Men's Short Sleeve Badge Tee Charcoal"	"United States"	"Columbus"	1
"Google Men's Vintage Badge Tee Black"	"India"	"Bengaluru"	1
"Google Men's Vintage Badge Tee Black"	"United States"	"Ann Arbor"	1
"Google Sunglasses"	"United States"	"Chicago"	1
"Google Twill Cap"	"United States"	"not available in demo dataset"	1
"Google Women's Convertible Vest-Jacket Black"	"United States"	"Mountain View"	1
"Google Women's Quilted Insulated Vest Black"	"United States"	"Mountain View"	1
"Google Youth Short Sleeve T-shirt Green"	"Canada"	"not available in demo dataset"	1
"Leather and Metal Ballpoint Pen"	"Canada"	"not available in demo dataset"	1
"Nest® Cam Indoor Security Camera - USA"	"United States"	"San Jose"	1
"Nest® Cam Indoor Security Camera - USA"	"United States"	"Seattle"	1
"Nest® Cam Indoor Security Camera - USA"	"United States"	"Sunnyvale"	1
"Nest® Cam Indoor Security Camera - USA"	"United States"	"not available in demo dataset"	1
"Nest® Cam Outdoor Security Camera - USA"	"United States"	"San Francisco"	1
"Nest® Cam Outdoor Security Camera - USA"	"United States"	"Sunnyvale"	1
"Nest® Learning Thermostat 3rd Gen-USA"	"United States"	"San Francisco"	1
"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	"United States"	"New York"	1
"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	"United States"	"Palo Alto"	1
"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	"United States"	"not available in demo dataset"	1
"Nest® Protect Smoke + CO Black Wired Alarm-USA"	"United States"	"Mountain View"	1
"Nest® Protect Smoke + CO White Battery Alarm-USA"	"United States"	"Mountain View"	1
"Nest® Protect Smoke + CO White Wired Alarm-USA"	"United States"	"not available in demo dataset"	1
"YouTube Leatherette Notebook Combo"	"United States"	"Dallas"	1
"YouTube Men's Short Sleeve Hero Tee Black"	"Colombia"	"not available in demo dataset"	1
"YouTube Men's Short Sleeve Hero Tee White"	"United States"	"New York"	1
"YouTube Men's Vintage Tee"	"Mexico"	"not available in demo dataset"	1
"Android Wool Heather Cap Heather/Black"	"France"	"not available in demo dataset"	1
"YouTube Twill Cap"	"Canada"	"not available in demo dataset"	1
"Android Wool Heather Cap Heather/Black"	"United States"	"(not set)"	1
"Compact Bluetooth Speaker"	"United States"	"not available in demo dataset"	1
"Four Color Retractable Pen"	"United States"	"not available in demo dataset"	1
"Google 22 oz Water Bottle"	"United States"	"Detroit"	1
"Google Alpine Style Backpack"	"Argentina"	"not available in demo dataset"	1
"Google Bongo Cupholder Bluetooth Speaker"	"United States"	"not available in demo dataset"	1
"Google Laptop Backpack"	"Ireland"	"Dublin"	1
"Google Laptop and Cell Phone Stickers"	"Finland"	"not available in demo dataset"	1
"Google Men's  Zip Hoodie"	"United States"	"New York"	1

**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries: 
```select "country", "city", sum ("totalTransactionRevenue") as total_Transaction_Revenue
from all_sessions_cpy where "totalTransactionRevenue" != 0
group by "country", "city"
order by total_Transaction_Revenue desc```

Answer:
"country"	"city"	"total_transaction_revenue"
"United States"	"not available in demo dataset"	6082
"United States"	"San Francisco"	1561
"United States"	"Sunnyvale"	991
"United States"	"Atlanta"	853
"United States"	"Palo Alto"	608
"Israel"	"Tel Aviv-Yafo"	602
"United States"	"New York"	526
"United States"	"Los Angeles"	479
"United States"	"Mountain View"	479
"United States"	"Chicago"	448
"Australia"	"Sydney"	358
"United States"	"Seattle"	358
"United States"	"San Jose"	262
"United States"	"Nashville"	157
"United States"	"Austin"	157
"United States"	"San Bruno"	103
"Canada"	"Toronto"	82
"Canada"	"New York"	67
"United States"	"Houston"	38
"United States"	"Columbus"	21
"Switzerland"	"Zurich"	16