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

|  Customer_ID  | Customer_Name | Items_in_Cart | Cash_spent_to_Date |
|     :---:     |     :---:     |     :---:     |        :---:       |
|     100204    |   John Smith  |       0       |        20.00       |
|     100205    |   Jane Smith  |       3       |        40.00       |
|     100206    |   Bobby Frank |       1       |        100.20      |
