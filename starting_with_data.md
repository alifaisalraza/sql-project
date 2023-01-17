Question 1:

Find out visitors who generated maximum revenue to the company site and explore their visit behavior on the site.

SQL Queries:  
```sql select "fullvisitorId", sum("revenue") as total_revenue, max("visitNumber") as TotalSitevisits,
sum("pageviews") as TotalPageViews, sum("timeonsite") as TotalTimeonSite from analytics_cpy
where "revenue" != 0
group by "fullvisitorId"
Order by total_revenue desc limit 20```

Answer:
"fullvisitorId" "total_revenue" "totalsitevisits" "totalpageviews" "totaltimeonsite"
"9681060687378784629" 27740 19 3070 88517
"3052828106337222847" 14054 1 3924 139680
"1957458976293878100" 9097 315 1510 58090
"9026840718082010040" 9019 36 1459 62762
"79204932396995037" 7055 6 37 1753
"5469079519715865124" 5603 5 676 24674
"4604965471651937146" 4282 1 494 15184
"5039450677611598907" 4009 1 637 52039
"7113011772090059658" 3451 4 2298 147908
"1729388992500827205" 3312 4 86 3606
"9947542428111966715" 2931 8 275 7860
"0291002892578472269" 2772 2 153 2610
"566055411938639598" 2694 4 880 29380
"9927137011932170896" 2655 104 146 10758
"0069486905584188344" 2597 3 696 44412
"037324303090551054" 2407 1 240 14460
"0095747507496204221" 2369 3 36 5242
"3704081881488905199" 2331 2 990 21024
"6750341726655002083" 2218 10 362 24441
"9661775944684760384" 2201 3 204 10974

Question 2:
Find out social channels capable of generating maximum revenue including relevance, if any, of social media engagement of visitors for company revenue.

SQL Queries:
```select "channelGrouping", "socialEngagementType", sum("revenue") as total_revenue from analytics_cpy
where "revenue" != 0
group by "channelGrouping", "socialEngagementType"
Order by total_revenue desc limit 20```

Answer:
"channelGrouping" "socialEngagementType" "total_revenue"
"Referral" "Not Socially Engaged" 830356
"Direct" "Not Socially Engaged" 180407
"Organic Search" "Not Socially Engaged" 112089
"Paid Search" "Not Socially Engaged" 19840
"Display" "Not Socially Engaged" 14508
"Social" "Not Socially Engaged" 2854
"Affiliates" "Not Socially Engaged" 518

Question 3:
Explore company's revenue pattern over year and month time scale.

SQL Queries:
```select substr("date", 1, 4) as "year", substr("date", 5, 2) as "month", sum ("revenue") as total_revenue, sum("units_sold") as TotalUnitsSold from analytics_cpy
where substr("date", 5, 2) in (select distinct substr("date", 5, 2) as "month" from analytics_cpy)
group by "year", "month"
order by total_revenue desc```

Answer:
"year" "month" "total_revenue" "totalunitssold"
"2017" "07" 411000 156729
"2017" "06" 372856 138539
"2017" "05" 357152 113900
"2017" "08" 19564 5524

Question 4:
Correlate page views and time spent on site to the prospect of revenue generation for each product category.

SQL Queries:
```select "v2ProductCategory", sum("totalTransactionRevenue") as TotalTransactionRevenue, sum("transactionRevenue")
as TransactionRevenue, sum("timeonsite") as totalTimeonSite, sum("pageviews") as totalPageViews
from all_sessions_cpy
group by "v2ProductCategory"
order by TotalTransactionRevenue Desc, TransactionRevenue Desc, totalTimeonSite Desc, totalPageViews Desc
limit 15```

Answer:
"v2ProductCategory" "totaltransactionrevenue" "transactionrevenue" "totaltimeonsite" "totalpageviews"
"Home/Nest/Nest-USA/" 4355 0 75185 2168
"Nest-USA" 2043 200 4919 126
"Bags" 1757 1015 1123 29
"Electronics" 1174 1174 925 35
"Home/Office/Notebooks & Journals/" 849 0 34506 694
"Home/Accessories/Pet/" 747 0 5832 205
"Housewares" 649 0 800 6
"Apparel" 347 0 8840 158
"Home/Apparel/Men's/Men's-T-Shirts/" 233 0 258293 7165
"${escCatTitle}" 213 0 6194 138
"Lifestyle" 183 0 939 26
"Home/Apparel/Women's/Women's-T-Shirts/" 178 0 74515 1981
"Home/Shop by Brand/Android/" 157 0 49880 1398
"Home/Shop by Brand/Google/" 149 0 147160 3877
"Home/Accessories/Drinkware/" 139 0 19642 404

Question 5:

SQL Queries:

Answer:
