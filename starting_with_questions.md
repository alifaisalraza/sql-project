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

select "country", "city", avg ("productQuantity") as Avg_Num_of_Products
from all_sessions where "productQuantity" is not null
group by "country", "city"
order by Avg_Num_of_Products desc

Answer:

"country"	"city"	"avg_num_of_products"
"United States"	"not available in demo dataset"	10.583333333333334
"Spain"	"Madrid"	10
"United States"	"Salem"	8
"United States"	"Atlanta"	4
"United States"	"Houston"	2
"United States"	"New York"	1.1666666666666667
"Ireland"	"Dublin"	1
"Mexico"	"not available in demo dataset"	1
"United States"	"(not set)"	1
"United States"	"Ann Arbor"	1
"United States"	"Chicago"	1
"Argentina"	"not available in demo dataset"	1
"United States"	"Dallas"	1
"United States"	"Detroit"	1
"United States"	"Los Angeles"	1
"United States"	"Mountain View"	1
"United States"	"Palo Alto"	1
"United States"	"San Francisco"	1
"United States"	"San Jose"	1
"United States"	"Seattle"	1
"United States"	"Sunnyvale"	1
"United States"	"Columbus"	1
"Canada"	"not available in demo dataset"	1
"Colombia"	"not available in demo dataset"	1
"Finland"	"not available in demo dataset"	1
"France"	"not available in demo dataset"	1
"India"	"Bengaluru"	1

**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**

SQL Queries:
select "v2ProductCategory", "country", "city", count (*) as Num_of_Products
from all_sessions where "productQuantity" is not null
group by "v2ProductCategory", "country", "city"
order by Num_of_Products desc

Answer:
"v2ProductCategory"	"country"	"city"	"num_of_products"
"Home/Nest/Nest-USA/"	"United States"	"Mountain View"	3
"Home/Nest/Nest-USA/"	"United States"	"not available in demo dataset"	3
"Electronics"	"United States"	"not available in demo dataset"	2
"${escCatTitle}"	"United States"	"(not set)"	1
"${escCatTitle}"	"United States"	"Houston"	1
"${escCatTitle}"	"United States"	"Mountain View"	1
"${escCatTitle}"	"United States"	"New York"	1
"${escCatTitle}"	"United States"	"not available in demo dataset"	1
"(not set)"	"Mexico"	"not available in demo dataset"	1
"(not set)"	"United States"	"Columbus"	1
"(not set)"	"United States"	"New York"	1
"(not set)"	"United States"	"Salem"	1
"Apparel"	"India"	"Bengaluru"	1
"Apparel"	"United States"	"Mountain View"	1
"Bags"	"United States"	"Atlanta"	1
"Bags"	"United States"	"not available in demo dataset"	1
"Drinkware"	"United States"	"Detroit"	1
"Headgear"	"France"	"not available in demo dataset"	1
"Home/Apparel/Headgear/"	"United States"	"not available in demo dataset"	1
"Home/Apparel/Kid's/Kids-Youth/"	"Canada"	"not available in demo dataset"	1
"Home/Apparel/Men's/"	"United States"	"New York"	1
"Home/Apparel/Men's/"	"United States"	"not available in demo dataset"	1
"Home/Apparel/Men's/Men's-Outerwear/"	"United States"	"Los Angeles"	1
"Home/Apparel/Men's/Men's-T-Shirts/"	"Colombia"	"not available in demo dataset"	1
"Home/Apparel/Men's/Men's-T-Shirts/"	"United States"	"Ann Arbor"	1
"Home/Apparel/Men's/Men's-T-Shirts/"	"United States"	"New York"	1
"Home/Apparel/Women's/Women's-Outerwear/"	"United States"	"Mountain View"	1
"Home/Bags/"	"Ireland"	"Dublin"	1
"Home/Bags/Backpacks/"	"Argentina"	"not available in demo dataset"	1
"Home/Nest/Nest-USA/"	"United States"	"New York"	1
"Home/Nest/Nest-USA/"	"United States"	"Palo Alto"	1
"Home/Nest/Nest-USA/"	"United States"	"San Francisco"	1
"Home/Nest/Nest-USA/"	"United States"	"San Jose"	1
"Home/Nest/Nest-USA/"	"United States"	"Seattle"	1
"Home/Nest/Nest-USA/"	"United States"	"Sunnyvale"	1
"Home/Office/Notebooks & Journals/"	"United States"	"not available in demo dataset"	1
"Home/Shop by Brand/YouTube/"	"Canada"	"not available in demo dataset"	1
"Home/Shop by Brand/YouTube/"	"United States"	"Dallas"	1
"Home/Shop by Brand/YouTube/"	"United States"	"New York"	1
"Lifestyle"	"United States"	"Chicago"	1
"Nest-USA"	"United States"	"Mountain View"	1
"Nest-USA"	"United States"	"San Francisco"	1
"Nest-USA"	"United States"	"Sunnyvale"	1
"Nest-USA"	"United States"	"not available in demo dataset"	1
"${escCatTitle}"	"Canada"	"not available in demo dataset"	1
"Office"	"United States"	"not available in demo dataset"	1
"${escCatTitle}"	"Finland"	"not available in demo dataset"	1
"${escCatTitle}"	"Spain"	"Madrid"	1


**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**

SQL Queries:
select "v2ProductName", "country", "city", max ("productQuantity") as Max_Num_of_Products
from all_sessions where "productQuantity" is not null
group by "v2ProductName", "country", "city"
order by Max_Num_of_Products desc

Answer:
"v2ProductName"	"country"	"city"	"max_num_of_products"
"Leatherette Journal"	"United States"	"not available in demo dataset"	65
"Reusable Shopping Bag"	"United States"	"not available in demo dataset"	50
"Waze Dress Socks"	"Spain"	"Madrid"	10
"Red Spiral Google Notebook"	"United States"	"Salem"	8
"Reusable Shopping Bag"	"United States"	"Atlanta"	4
"Nest® Cam Outdoor Security Camera - USA"	"United States"	"not available in demo dataset"	3
"Nest® Protect Smoke + CO White Wired Alarm-USA"	"United States"	"New York"	2
"Google Sunglasses"	"United States"	"Houston"	2
"Google Laptop and Cell Phone Stickers"	"Finland"	"not available in demo dataset"	1
"Google Men's  Zip Hoodie"	"United States"	"New York"	1
"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"United States"	"New York"	1
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
"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	"United States"	"Mountain View"	1
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

**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries: 
select "country", "city", sum ("totalTransactionRevenue") as total_Transaction_Revenue
from all_sessions where "totalTransactionRevenue" is not null
group by "country", "city"
order by total_Transaction_Revenue desc

Answer:
"country"	"city"	"total_transaction_revenue"
"United States"	"not available in demo dataset"	6092560000
"United States"	"San Francisco"	1564320000
"United States"	"Sunnyvale"	992230000
"United States"	"Atlanta"	854440000
"United States"	"Palo Alto"	608000000
"Israel"	"Tel Aviv-Yafo"	602000000
"United States"	"New York"	530360000
"United States"	"Mountain View"	483360000
"United States"	"Los Angeles"	479480000
"United States"	"Chicago"	449520000
"Australia"	"Sydney"	358000000
"United States"	"Seattle"	358000000
"United States"	"San Jose"	262380000
"United States"	"Austin"	157780000
"United States"	"Nashville"	157000000
"United States"	"San Bruno"	103770000
"Canada"	"Toronto"	82160000
"Canada"	"New York"	67990000
"United States"	"Houston"	38980000
"United States"	"Columbus"	21990000
"Switzerland"	"Zurich"	16990000