# PostgreSQL Questions

### Variant 1: Basic Understanding and Recall

1.  What is PostgreSQL and why is it used?
2.  Define DDL and give two examples of DDL commands.
3.  What does DML stand for and what is its purpose?
4.  Name three data types available in PostgreSQL.
5.  What is the primary key constraint in PostgreSQL?
6.  Describe the foreign key constraint and its importance.
7.  Explain the difference between the `VARCHAR` and `TEXT` data types.
8.  What is the purpose of the `NOT NULL` constraint?
9.  How would you retrieve all rows from a table named `employees`?
10.  What SQL command is used to create a new table in PostgreSQL?
11.  Describe the `CHECK` constraint in PostgreSQL.
12.  How can you insert data into a table in PostgreSQL?
13.  Explain the use of the `SELECT` statement.
14.  What is the role of the `UPDATE` command?
15.  How do you delete data from a PostgreSQL table?
16.  What is the difference between `INNER JOIN` and `LEFT JOIN`?
17.  Define the term "aggregate function" in the context of PostgreSQL.
18.  How can you rollback a transaction in PostgreSQL?
19.  What is the purpose of the `GROUP BY` clause?
20.  Give an example of a simple `SELECT` query using the `WHERE` clause.

### Variant 2: Intermediate Application and Understanding

21.  How can you ensure the uniqueness of data in a column using PostgreSQL constraints?
22.  What is the difference between `SERIAL` and `BIGSERIAL` data types?
23.  How do you update the value of a column for all rows in a table?
24.  Demonstrate how to use the `COUNT()` aggregate function in a query.
25.  How would you join three tables using the `INNER JOIN` clause?
26.  Explain the significance of transaction control language in PostgreSQL.
27.  How can you create a composite primary key in PostgreSQL?
28.  Describe how to use the `HAVING` clause in a query.
29.  What is a transaction in PostgreSQL, and how is it managed?
30.  Provide an example of using the `BETWEEN` operator in a query.
31.  How can you alter the structure of an existing table to add a new column?
32.  Explain the purpose of the `EXPLAIN` command in PostgreSQL.
33.  How do you create an index on a table, and why would you do so?
34.  Describe the process of normalizing a database and its benefits.
35.  Show how to use subqueries in PostgreSQL.

### Variant 3: Advanced Analysis and Problem Solving with Example Data

36. Write a SQL query to find the title of the book with the highest price using the `Books` table.
37. Using the `Authors` and `Books` tables, create a query to display a list of authors sorted by the number of books they have published in descending order.
38. Construct a query to display the month with the highest total number of books sold, based on the `Sales` table.
39. Develop a SQL statement to add a `Rating` column to the `Books` table and then update this new column with a default rating of 5 for all existing books.
40. Using the dataset, write a query to find the average price of all books.
41. From the `Sales` table, demonstrate how to find the sale with the highest quantity sold.
42. Using the `Sales` table, write a query to count the number of sales made in January 2024.
43. Design a query to find all books that were sold more than once on the same day
44. Show how to insert a new sale record into the `Sales` table for `BookID` 2 with a quantity of 2 on `2024-02-10`
45. Show how to modify the `Sales` table structure to include a `CustomerID` column, and then write a mock query to insert hypothetical data into this new structure.
46. Write a query to join the `Books` and `Authors` tables to list each book along with its author's name.
47. Demonstrate how to find the total sales revenue (quantity * price) per book.
48. Write a query to list authors who have more than one book in the `Books` table.
49. From the `Sales` table, demonstrate how to calculate the total quantity of books sold for `BookID` 1.
50. Show how to delete sales records from the `Sales` table for sales that occurred before `2024-02-01`.



## Example Dataset

### Books Table

| BookID | Title                         | AuthorID | Price |
|--------|-------------------------------|----------|-------|
| 1      | PostgreSQL Essentials         | 1        | 40    |
| 2      | Advanced SQL Techniques       | 2        | 50    |
| 3      | Understanding Databases       | 3        | 30    |
| 4      | The Art of Database Design    | 2        | 60    |
| 5      | SQL for Data Science          | 4        | 45    |
| 6      | PostgreSQL Performance Tuning | 1        | 55    |

### Authors Table

| AuthorID | Name            |
|----------|-----------------|
| 1        | Alex Thompson   |
| 2        | Maria Garcia    |
| 3        | John Smith      |
| 4        | Linda Johnson   |

### Sales Table 

| SaleID | BookID | Quantity | SaleDate   |
|--------|--------|----------|------------|
| 1      | 1      | 2        | 2024-01-10 |
| 2      | 2      | 1        | 2024-01-15 |
| 3      | 3      | 3        | 2024-02-01 |
| 4      | 1      | 1        | 2024-02-05 |
| 5      | 4      | 2        | 2024-02-10 |
| 6      | 5      | 1        | 2024-02-12 |
| 7      | 2      | 2        | 2024-02-15 |
| 8      | 6      | 1        | 2024-02-20 |

## SQL Code for Example Dataset

### SQL Table Creation

```sql
CREATE TABLE Authors (
    AuthorID INT PRIMARY KEY,
    Name VARCHAR(255) NOT NULL
);

CREATE TABLE Books (
    BookID INT PRIMARY KEY,
    Title VARCHAR(255) NOT NULL,
    AuthorID INT,
    Price DECIMAL(10, 2),
    FOREIGN KEY (AuthorID) REFERENCES Authors(AuthorID)
);

CREATE TABLE Sales (
    SaleID INT PRIMARY KEY,
    BookID INT,
    Quantity INT,
    SaleDate DATE,
    FOREIGN KEY (BookID) REFERENCES Books(BookID)
);
```

### SQL Data Insertion

#### Authors Table

```sql
INSERT INTO Authors (AuthorID, Name) VALUES
(1, 'Alex Thompson'),
(2, 'Maria Garcia'),
(3, 'John Smith'),
(4, 'Linda Johnson');
```

#### Books Table

```sql
INSERT INTO Books (BookID, Title, AuthorID, Price) VALUES
(1, 'PostgreSQL Essentials', 1, 40),
(2, 'Advanced SQL Techniques', 2, 50),
(3, 'Understanding Databases', 3, 30),
(4, 'The Art of Database Design', 2, 60),
(5, 'SQL for Data Science', 4, 45),
(6, 'PostgreSQL Performance Tuning', 1, 55);
```

#### Sales Table

```sql
INSERT INTO Sales (SaleID, BookID, Quantity, SaleDate) VALUES
(1, 1, 2, '2024-01-10'),
(2, 2, 1, '2024-01-15'),
(3, 3, 3, '2024-02-01'),
(4, 1, 1, '2024-02-05'),
(5, 4, 2, '2024-02-10'),
(6, 5, 1, '2024-02-12'),
(7, 2, 2, '2024-02-15'),
(8, 6, 1, '2024-02-20');
```
