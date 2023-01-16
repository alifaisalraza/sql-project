What issues will you address by cleaning the data?

Ans: The purpose is to remove or fix corrupted data. Following observation was made:
a) Products table was not complete. The list of products were incomplete and transaction tables like sales_by_sku and all_sessions were referring to products not mentioned inside the products. This created gap in bringing together all the information to make a meaningful insight. Owing to limited knowledge of context behind the data, a limited set of data cleaning practices may be possible.
b) sales_report was found to be a derivtive table created out of join of products table and sales_by_sku tables hence was dropped from further investigation.

Queries:
Below, provide the SQL queries you used to clean your data.

----------------------------------------------------------------------------------
FURST, MAKE A COPY OF ALL TABLES (WITH DATA) EXCEPT SALES_REPORT:

Table sales_report not copied as it is just a join of sales_sku and products tables and hence is derivative. 

CREATE TABLE products_cpy AS 
TABLE products;

CREATE TABLE sales_by_sku_cpy AS 
TABLE sales_by_sku;

CREATE TABLE all_sessions_cpy AS 
TABLE all_sessions;

CREATE TABLE analytics_cpy AS 
TABLE analytics;

----------------------------------------------------------------------------------
SET ALL CURRENCY CODE TO USD:

select * from all_sessions where "currencyCode" != 'USD' -> 0 rows returned.

select * from all_sessions where "currencyCode" is null -> 272 out of 15000 rows returned.

So, the currency code updated to 'USD' for all rows.

update all_sessions_cpy
set "currencyCode" = 'USD' where "currencyCode" is null

----------------------------------------------------------------------------------
ALTER TABLE; DROP COLUMNS WHICH HAVE NO VALUE AT ALL:

select * from all_sessions_cpy
where "searchKeyword" is not null
or "productRefundAmount" is not null 
or "itemQuantity" is not null
or "itemRevenue" is not null

-> 0 rows returned.

select * from analytics_copy where userid is not null

-> 0 rows returned.

alter table all_sessions_cpy
drop column "searchKeyword"

alter table all_sessions_cpy
drop column "productRefundAmount"

alter table all_sessions_cpy
drop column "itemQuantity"

alter table all_sessions_cpy
drop column "itemRevenue"

alter table analytics_cpy
drop column "userid"

----------------------------------------------------------------------------------

CONVERT VALUES AND PRICES IN UNDERSTANDABLE FORMAT (DIVIDE BY MILLION):

update all_sessions_cpy
set "totalTransactionRevenue" = "totalTransactionRevenue"/1000000 

update all_sessions_cpy
set "transactionRevenue" = "transactionRevenue"/1000000 

update all_sessions_cpy
set "productPrice" = "productPrice"/1000000 

update all_sessions_cpy
set "productRevenue" = "productRevenue"/1000000 

update analytics_cpy
set "revenue" = "revenue"/1000000

update analytics_cpy
set "unit_price" = "unit_price"/1000000

----------------------------------------------------------------------------------

UPDATE THOSE FIELDS WITH 0 VALUE WHEN THEY ARE NULL AS LONG AS IT DOESN'T INTERFERE WITH BUSINESS LOGIC:

update all_sessions_cpy set "totalTransactionRevenue" = 0 where "totalTransactionRevenue" is null

update all_sessions_cpy set "transactions" = 0 where "transactions" is null

update all_sessions_cpy set "timeonsite" = 0 where "timeonsite" is null

update all_sessions_cpy set "sessionQualityDim" = 0 where "sessionQualityDim" is null

update all_sessions_cpy set "productQuantity" = 0 where "productQuantity" is null

update all_sessions_cpy set "productRevenue" = 0 where "productRevenue" is null

update all_sessions_cpy set "transactionRevenue" = 0 where "transactionRevenue" is null
