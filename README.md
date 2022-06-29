## Sales Insights Data Analysis Project

### Power BI dashboard

1. To use the dashboard, download Power BI app from microsoft store and then download the .pbix file attached in this repository.
2. After the .pbix file is opened Power BI app, you can access 3 dashboards by the name Dashboard 1, Dashboard 2, Dashboard 3.
3. In the dashboard, you can choose to toggle the financial year or month and the data would change accordingly.   

### Power BI app
1. To open the dashboard on mobile , you nedd to publish this power bi file in your power bi workspace.
2. Once you do that, you can download the Power BI mobile app, login with your workspace account and access the dashboard

### Instructions to setup mysql on your local computer

1. Follow step in this video to install mysql on your local computer - 
https://www.youtube.com/watch?v=OM4aZJW_Ojs

1. SQL database dump is in Data_dump.sql file above. Download `Data_dump.sql` file to your local computer and import it as per instructions given in the tutorial video

### Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`

