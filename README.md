# SQL-for-DevOps-Engineers

![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

![](SQL.png)

## SQL Self Assessment

<details>
<summary><b><i>1.What is SQL?</i></b></summary>

$\color{green}{\text{Answer}}$

SQL (Structured Query Language) is a standard language for relational databases (like MySQL, MariaDB, ...).
It's used for reading, updating, removing and creating data in a relational database.

</details>

<details>
<summary><b><i>2.How is SQL Different from NoSQL?</i></b></summary>

$\color{green}{\text{Answer}}$

The main difference is that SQL databases are structured (data is stored in the form of tables with rows and columns - like an excel spreadsheet table) while NoSQL is unstructured, and the data storage can vary depending on how the NoSQL DB is set up, such as key-value pair, document-oriented, etc.

</details>

<details>
<summary><b><i>3.When is it best to use SQL? NoSQL?</i></b></summary>

$\color{green}{\text{Answer}}$

- SQL: Best used when data integrity is crucial. SQL is typically implemented with many businesses and areas within the finance field due to it's ACID compliance.

- NoSQL: Great if you need to scale things quickly. NoSQL was designed with web applications in mind, so it works great if you need to quickly spread the same information around to multiple servers

Additionally, since NoSQL does not adhere to the strict table with columns and rows structure that Relational Databases require, you can store different data types together.

</details>

## Practical SQL - Basics

<b><i>For these questions, we will be using the Customers and Orders tables shown below:</i></b>

<b><i>Customers</i></b>

|  Customer_ID  | Customer_Name | Items_in_Cart | Cash_spent_to_Date |
|     :---:     |     :---:     |     :---:     |        :---:       |
|     100204    |   John Smith  |       0       |        20.00       |
|     100205    |   Jane Smith  |       3       |        40.00       |
|     100206    |   Bobby Frank |       1       |        100.20      |

<b><i>Orders</i></b>

|  Customer_ID	 | Order_ID	|          Item             |   Price  |  Date_sold  |
|     :---:      |   :---:  |          :---:            |  :---:   |    :---:    |
|     100206	   |   A123	  |      Rubber Ducky	        |   2.20	 |  2019-09-18 |
|     100206	   |   A123	  |       Bubble Bath	        |   8.00	 |  2019-09-18 |
|     100206	   |   Q987	  |       80-Pack TP	        |  90.00   |	2019-09-20 |
|     100205	   |   Z001	  |   Cat Food - Tuna Fish	  |  10.00   |	2019-08-05 |
|     100205	   |   Z001	  |     Cat Food - Chicken	  |  10.00   |	2019-08-05 |
|     100205	   |   Z001	  |     Cat Food - Beef 	    |  10.00	 |  2019-08-05 |
|     100205	   |   Z001	  |Cat Food - Kitty quesadilla|	 10.00	 |  2019-08-05 |
|     100204	   |   X202	  |         Coffee	          |  20.00	 |  2019-04-29 |

<details>
<summary><b><i>4.How would I select all fields from this table?</i></b></summary>

$\color{green}{\text{Answer}}$

```SQL
SELECT * FROM Customers;
```

</details>

<details>
<summary><b><i>5.How many items are in John's cart?</i></b></summary>

$\color{green}{\text{Answer}}$

```SQL
SELECT Items_in_Cart FROM Customers WHERE Customer_Name = "John Smith";
```

</details>

<details>
<summary><b><i>6.What is the sum of all the cash spent across all customers?</i></b></summary>

$\color{green}{\text{Answer}}$

```SQL
SELECT SUM(Cash_spent_to_Date) as SUM_CASH FROM Customers;
```

</details>

<details>
<summary><b><i>7.How many people have items in their cart?</i></b></summary>

$\color{green}{\text{Answer}}$

```SQL
SELECT COUNT(1) FROM Customers WHERE Items_in_cart > 0;
```

</details>

<details>
<summary><b><i>8.How would you join the customer table to the order table?</i></b></summary>

$\color{green}{\text{Answer}}$

You would join them on the unique key. In this case, the unique key is Customer_ID in both the Customers table and Orders table.

</details>

<details>
<summary><b><i>9.How would you show which customer ordered which items?</i></b></summary>

$\color{green}{\text{Answer}}$

```SQL
SELECT Customers.Customer_Name, Orders.Item FROM Customers JOIN Orders ON Customers.Customer_ID = Orders.Customer_ID ;
```

</details>

<details>
<summary><b><i>10.Using a with statement, how would you show who ordered cat food, and the total amount of money spent?</i></b></summary>

$\color{green}{\text{Answer}}$

```SQL
WITH CatFoodOrders AS (
    SELECT 
        Customers.Customer_Name, 
        Orders.Item, 
        Orders.Price
    FROM Customers
    JOIN Orders ON Customers.Customer_ID = Orders.Customer_ID
    WHERE Orders.Item LIKE '%Cat Food%'
)
SELECT 
    Customer_Name, 
    SUM(Price) AS Total_Spent
FROM CatFoodOrders
GROUP BY Customer_Name;
```

</details>

<details>
<summary><b><i>11.Which of the following queries would you use?
  
A.
```SQL
SELECT COUNT(*) FROM shawarma_purchases WHERE YEAR(purchased_at) = '2017';
```

B.
```SQL
SELECT COUNT(*) FROM shawarma_purchases WHERE purchased_at >= '2017-01-01' AND purchased_at <= '2017-12-31';
```
                                    
</i></b></summary>

$\color{green}{\text{Answer}}$

Option B. It allows the database to use an index on the date column, making it much faster than Option A on large datasets.

</details>
