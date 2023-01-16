What are your risk areas? Identify and describe them.

It has been observed that key unifying identifiers like product sku numbers are not consistently populated inside the tables. e.g, it was observed that the master product table is missing many SKU numbers which are present in sales and sessions tables. This is consistency issue which will affect the quality of analysis. 

QA Process:
Describe your QA process and include the SQL queries used to execute it.

QUALLITY CHECK OF DATA:

A) VERIFYING WHETHER PRODUCT SKUs ARE PRESENT IN ALL TABLES:

select * from sales_by_sku where "productSKU" is null -> 0 rows returned.

select * from sales_report where "productSKU" is null -> 0 rows returned.

select * from products where "SKU" is null -> 0 rows returned.

select * from all_sessions where "productSKU" is null -> 0 rows returned

This implies that SKUs are present in both master and transaction tables and hence may be used as one of the identifiers to join tables and gather new insights.

A) VERIFYING WHETHER PRODUCT SKUs ARE CONSISTENT ACROSS ALL TABLES:

select count("SKU" from products -> 1092 itemss counted.

select count(distinct "productSKU") from sales_by_sku -> 462 items counted.

select count("SKU") from products a inner join sales_by_sku b on a."SKU" = b."productSKU" -> only 454 items counted. This means some SKU items missing from master products tabble which creates a gap for the products information.

select count(distinct "productSKU") from all_sessions -> 536 items counted.

select count(distinct "SKU") from products a inner join all_sessions b on a."SKU" = b."productSKU" -> 389 items counted. This means that transactions table all_sessions has SKUs which are not present in the master products table which creates further gap for the product information.

CONCLUSION: THE PRODUCT INFORMATION WHICH IS A KEY IDENTIFIER TO GENERATE INSIGHTS IS LOW ON QUALITY AND HENCE MAY LIMIT THE QUALITY OF ANALYSIS.




