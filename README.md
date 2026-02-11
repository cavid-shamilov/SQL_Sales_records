# **PROJECT PORTFOLIO – Sales Records SQL Data Analysis**
## Project Overview

This project demonstrates practical SQL skills applied to a structured sales transactions dataset. The analysis includes database creation, table design, data cleaning, exploratory data analysis (EDA), and solving business-driven SQL questions.

The project was completed by solving tasks provided in a YouTube SQL tutorial series. While the business questions were inspired by the tutorial, all queries were written, structured, and executed independently to strengthen my understanding of SQL and analytical thinking.
Objectives

Create and manage a SQL database
Design and build a structured sales table
Perform data validation and cleaning (handling NULL values)
Explore transactional data using SQL
Solve business-related analytical questions
Apply aggregation, filtering, grouping, sorting, and ranking techniques

Dataset Description
The dataset contains retail-style transactional data including:
Transaction ID
Sale date and time
Customer ID
Gender and age
Product category
Quantity sold
Price per unit
Cost of goods sold (COGS)
Total sale amount
Each row represents a single sales transaction.

Database Setup and Table Creation
```sql
Create database
CREATE DATABASE sql_project_1;

-- Table creation
CREATE TABLE Salesrecords 
(
    transactions_id INT PRIMARY KEY,
    sale_date DATE,
    sale_time TIME,
    customer_id INT,
    gender VARCHAR(10),
    age INT,
    category VARCHAR(15),
    quantity INT, 
    price_per_unit DECIMAL(10,2),
    cogs DECIMAL(10,2),
    total_sale DECIMAL(10,2)
);
```
## Data Exploration and Cleaning
```sql-- View first 10 rows to understand the structure
SELECT TOP 10 * FROM Salesrecords;

-- Count total rows
SELECT COUNT(*) FROM Salesrecords;

-- See all rows where any column is NULL
SELECT * FROM Salesrecords
WHERE transactions_id IS NULL
   OR sale_date IS NULL
   OR sale_time IS NULL
   OR customer_id IS NULL
   OR gender IS NULL
   OR age IS NULL
   OR category IS NULL
   OR quantity IS NULL
   OR price_per_unit IS NULL
   OR cogs IS NULL
   OR total_sale IS NULL;

-- Delete rows with any NULL values
DELETE FROM Salesrecords
WHERE transactions_id IS NULL
   OR sale_date IS NULL
   OR sale_time IS NULL
   OR customer_id IS NULL
   OR gender IS NULL
   OR age IS NULL
   OR category IS NULL
   OR quantity IS NULL
   OR price_per_unit IS NULL
   OR cogs IS NULL
   OR total_sale IS NULL;

-- Count unique customers
SELECT COUNT(DISTINCT customer_id) FROM Salesrecords;

-- Count total sales
SELECT COUNT(total_sale) FROM Salesrecords;

-- View all distinct categories
SELECT DISTINCT category FROM Salesrecords;
-- Data Analysis & Business Key Problems & Answers
```

## My Analysis & Findings
Q.1 Retrieve all sales made on '2022-09-19
Q.2 Transactions where category is 'Electronics' and quantity > 2 in Feb 2023:
Q.3 Total sales for each category
Q.4 Average age of customers who purchased from 'Beauty' category
Q.5 Transactions where total_sale > 1000
Q.6 Total number of transactions by gender in each category
Q.7 Write a SQL query to calculate the average sale for each month
Q.8 Write a SQL query to find the top 5 customers based on the highest total sales
Q.9 Write a SQL query to find the number of unique customers who purchased items from each category.



## Q.1 Retrieve all sales made on '2022-09-19
```sql SELECT * 
FROM Salesrecords 
WHERE sale_date = '2022-09-19';
```



## Q.2 Transactions where category is 'Electronics' and quantity > 2 in Feb 2023:
```sqlSELECT *
FROM Salesrecords
WHERE YEAR(sale_date) = 2023
  AND MONTH(sale_date) = 2
  AND category = 'Electronics'
  AND quantity > 2;
```



## Q.3 Total sales for each category
  ```sqlSELECT category, SUM(total_sale) 
FROM Salesrecords 
GROUP BY category;
```


## Q.4 Average age of customers who purchased from 'Beauty' category
```sqlSELECT category, AVG(age) 
FROM Salesrecords 
WHERE category = 'Beauty';
```



## Q.5Transactions where total_sale > 1000
```sqlSELECT * 
FROM Salesrecords 
WHERE total_sale > 1000;
```


## Q.6 Total number of transactions by gender in each category
```sqlSELECT category, gender, COUNT(transactions_id) 
FROM Salesrecords
GROUP BY category, gender;
```



## Q.7 Write a SQL query to calculate the average sale for each month
```sqlselect year(sale_date),datename(month,sale_date),avg(total_sale)
from Salesrecords
group by year(sale_date),month(sale_date),datename(month,sale_date)
ORDER BY year(sale_date), MONTH(sale_date);
```



## Q.8 Write a SQL query to find the top 5 customers based on the highest total sales
```sqlSelect top 5  customer_id,sum(total_sale) 
from salesrecords 
group by customer_id 
order by total_sales desc;
```



## Q.9 Write a SQL query to find the number of unique customers who purchased items from each category.
```sqlselect category,count(distinct(customer_id)) 
from salesrecords 
group by category;


-- End of project
```
## Key SQL Concepts Used

Database & Table creation: CREATE DATABASE, CREATE TABLE
Data Cleaning: DELETE, IS NULL
Aggregation: COUNT(), SUM(), AVG()
Grouping and Filtering: GROUP BY, WHERE
Sorting: ORDER BY
Working with unique values: DISTINCT
Top rows: TOP
Date functions: YEAR(), MONTH(), DATENAME()
## Acknowledgment
This project is based on tasks provided in the following YouTube SQL tutorial series:
🔗 YouTube SQL Tutorial Series
All query implementations, structure, and documentation were completed independently as part of my SQL learning journey.
## Conclusion

This project strengthened my SQL fundamentals, improved my data cleaning skills, and developed analytical thinking by solving real-world styled business questions using structured sales data.
