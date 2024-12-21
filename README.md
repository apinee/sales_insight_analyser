# sales_insight_analyser

# Problem Statement

ABC Hardware is a company that supplies computer hardware and peripherals to various clients. They have their head office in Delhi, India, and many regional offices throughout the country. Apoorva Jha, the sales director, struggles to obtain accurate sales insights due to regional managers' biased reporting and excessive data. He seeks a simplified, visual representation of the data for better decision-making.

The reliance on verbal reports from regional managers leads to a distorted view of the sales performance. This affects Apoorva’s ability to make informed decisions based on accurate data. The overwhelming amount of Excel files complicates the analysis process. Apoorva desires a more straightforward way to understand key sales metrics without sifting through numerous spreadsheets.

Implementing a dashboard solution like Power BI allows Apoorva to visualize data effectively. This enables him to track sales trends and make data-driven decisions to enhance company performance.

## Project Planning

The second part of this project includes project planning. Project planning for data analytics at AtliQ Hardware involves using the AIMS grid to clarify purpose, stakeholders, end results, and success criteria effectively. This structured approach facilitates better project outcomes and resource management.

### AIMS Grid Components

1. **Identifying Pain Points**
   - The first component emphasizes identifying the key pain points in the project, ensuring focused efforts on addressing specific challenges. This clarity helps streamline the project direction.

2. **Stakeholder Involvement**
   - Stakeholder involvement is crucial, including teams from marketing, sales, IT, and data analytics. This ensures comprehensive insights and collaboration throughout the project's lifecycle. This inclusive approach enhances project effectiveness.

3. **Defining Success Criteria**
   - Defining success criteria is essential to measure project success accurately, such as reducing costs by 10% and improving information delivery methods. This quantifiable goal supports accountability and progress tracking.

The AIMS grid is a powerful project management tool that helps define success criteria and monitor project progress efficiently, significantly enhancing project outcomes.

## Data Cleaning and Analyzing with MySQL

 Show all customer records
```sql
SELECT * FROM customers;```



![image](https://github.com/user-attachments/assets/97cafb1a-a73f-41b7-8200-17cbf0e0e65a)





Show total number of customers
```sql
SELECT count(*) FROM customers;```

![image](https://github.com/user-attachments/assets/bb0c45a4-a342-4e16-b5eb-33449631d476)




Show transactions for Chennai market (market code for chennai is Mark001
```sql
SELECT * FROM transactions WHERE market_code='Mark001';```

![image](https://github.com/user-attachments/assets/077072e2-6922-4307-b8d4-41f98fed5120)


Show transaction where currancy is USD

```sql
SELECT * FROM transactions WHERE currency="USD";```

![image](https://github.com/user-attachments/assets/e7a08298-a79b-44c9-a781-cb5c8ed30436)


Show transactions in 2020 join by date table


```sql
SELECT transactions.*, date.* 
FROM transactions 
INNER JOIN date ON transactions.order_date=date.date 
WHERE date.year=2020;```

![image](https://github.com/user-attachments/assets/a5bb29ce-0b0d-4efc-b5d9-0a4d93b09669)


Show total revenue in year 2020, January Month,
```sql
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 
  AND date.month_name = 'January' 
  AND (transactions.currency = 'INR' OR transactions.currency = 'USD');```

![image](https://github.com/user-attachments/assets/40a19a97-fd78-46cb-a96b-8ac6ec25696f)



Show total revenue in year 2020 in Chennai


```sql
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date=date.date 
WHERE date.year=2020 
  AND transactions.market_code="Mark001";```

![image](https://github.com/user-attachments/assets/1ede5aaa-1472-4da8-bd59-66813a13f642)


By using these MySQL operations, we obtained insights into the sum of the data and transactions. We identified which rows and columns have missing values, which we will clean later on using Power BI.

# ETL with Power BI


![schema diagram](https://github.com/user-attachments/assets/fb5c28d1-d816-413c-a112-a111c35dd0c2)




 



