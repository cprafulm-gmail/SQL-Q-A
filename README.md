# SQL-Q-A

1. Question: What is SQL?
   Answer: SQL (Structured Query Language) is a programming language used for managing and manipulating relational databases.

2. Question: What are the different types of SQL statements?
   Answer: There are mainly three types of SQL statements:
   - Data Definition Language (DDL): Used for creating, modifying, and deleting database objects (e.g., CREATE TABLE, ALTER TABLE, DROP TABLE).
   - Data Manipulation Language (DML): Used for retrieving, inserting, updating, and deleting data (e.g., SELECT, INSERT, UPDATE, DELETE).
   - Data Control Language (DCL): Used for managing user access and permissions (e.g., GRANT, REVOKE).

3. Question: Write a SQL query to retrieve all records from a table named "customers".
   Answer:
   ```sql
   SELECT * FROM customers;
   ```

4. Question: Write a SQL query to retrieve the names of customers who have placed orders.
   Answer:
   ```sql
   SELECT name FROM customers
   WHERE customer_id IN (SELECT customer_id FROM orders);
   ```

5. Question: Write a SQL query to calculate the average salary of employees in a table named "employees".
   Answer:
   ```sql
   SELECT AVG(salary) FROM employees;
   ```

6. Question: Write a SQL query to join two tables, "orders" and "customers", based on the customer_id column.
   Answer:
   ```sql
   SELECT * FROM orders
   INNER JOIN customers ON orders.customer_id = customers.customer_id;
   ```

7. Question: Write a SQL query to retrieve the top 5 highest-paid employees from a table named "employees".
   Answer:
   ```sql
   SELECT * FROM employees
   ORDER BY salary DESC
   LIMIT 5;
   ```

8. Question: Write a SQL query to insert a new record into a table named "products".
   Answer:
   ```sql
   INSERT INTO products (product_id, name, price)
   VALUES (1, 'Product A', 10.99);
   ```

9. Question: Write a SQL query to update the price of a product with a specific product_id in a table named "products".
   Answer:
   ```sql
   UPDATE products
   SET price = 14.99
   WHERE product_id = 1;
   ```

10. Question: Write a SQL query to delete all records from a table named "customers" where the country is 'USA'.
    Answer:
    ```sql
    DELETE FROM customers
    WHERE country = 'USA';
    ```
Certainly! Here are a few more SQL technical interview questions with answers and sample code:

11. Question: Write a SQL query to calculate the total sales amount for each product in a table named "sales".
    Answer:
    ```sql
    SELECT product_id, SUM(amount) AS total_sales
    FROM sales
    GROUP BY product_id;
    ```

12. Question: Write a SQL query to retrieve the names of customers who have not placed any orders.
    Answer:
    ```sql
    SELECT name
    FROM customers
    WHERE customer_id NOT IN (SELECT customer_id FROM orders);
    ```

13. Question: Write a SQL query to find the highest sales amount among all products.
    Answer:
    ```sql
    SELECT MAX(amount) AS highest_sales_amount
    FROM sales;
    ```

14. Question: Write a SQL query to calculate the average salary of employees for each department in a table named "employees".
    Answer:
    ```sql
    SELECT department, AVG(salary) AS average_salary
    FROM employees
    GROUP BY department;
    ```

15. Question: Write a SQL query to retrieve the top 3 products with the highest sales amount from a table named "products".
    Answer:
    ```sql
    SELECT *
    FROM products
    ORDER BY sales_amount DESC
    LIMIT 3;
    ```

16. Question: Write a SQL query to update the email addresses of all customers from a table named "customers" by adding a prefix 'new_' to their existing email addresses.
    Answer:
    ```sql
    UPDATE customers
    SET email = CONCAT('new_', email);
    ```

17. Question: Write a SQL query to find the number of customers who have placed at least 3 orders.
    Answer:
    ```sql
    SELECT COUNT(DISTINCT customer_id) AS num_customers
    FROM orders
    GROUP BY customer_id
    HAVING COUNT(order_id) >= 3;
    ```

18. Question: Write a SQL query to delete all duplicate records from a table named "employees" based on the "email" column.
    Answer:
    ```sql
    DELETE FROM employees
    WHERE employee_id NOT IN (
        SELECT MIN(employee_id)
        FROM employees
        GROUP BY email
    );
    ```

19. Question: Write a SQL query to calculate the total revenue for each month in a table named "sales" where the sales_date column is of type DATE.
    Answer:
    ```sql
    SELECT EXTRACT(MONTH FROM sales_date) AS month, SUM(amount) AS total_revenue
    FROM sales
    GROUP BY EXTRACT(MONTH FROM sales_date);
    ```

20. Question: Write a SQL query to find the second-highest salary in a table named "employees".
    Answer:
    ```sql
    SELECT MAX(salary) AS second_highest_salary
    FROM employees
    WHERE salary < (SELECT MAX(salary) FROM employees);
    ```

21. Question: Write a SQL query to retrieve the names of customers who have made a purchase in the last 30 days.
    Answer:
    ```sql
    SELECT name
    FROM customers
    WHERE customer_id IN (
        SELECT customer_id
        FROM orders
        WHERE order_date >= CURRENT_DATE - INTERVAL '30 days'
    );
    ```

22. Question: Write a SQL query to find the total number of orders placed by each customer in a table named "orders".
    Answer:
    ```sql
    SELECT customer_id, COUNT(*) AS order_count
    FROM orders
    GROUP BY customer_id;
    ```

23. Question: Write a SQL query to calculate the average age of employees in a table named "employees" based on their birthdates.
    Answer:
    ```sql
    SELECT AVG(DATEDIFF(CURRENT_DATE, birthdate)) AS average_age
    FROM employees;
    ```

24. Question: Write a SQL query to retrieve the top 5 most recent orders from a table named "orders" ordered by the order date.
    Answer:
    ```sql
    SELECT *
    FROM orders
    ORDER BY order_date DESC
    LIMIT 5;
    ```

25. Question: Write a SQL query to find the customers who have placed orders for all available products in a table named "products".
    Answer:
    ```sql
    SELECT customer_id
    FROM orders
    GROUP BY customer_id
    HAVING COUNT(DISTINCT product_id) = (SELECT COUNT(*) FROM products);
    ```

26. Question: Write a SQL query to update the quantity of a specific product in a table named "products".
    Answer:
    ```sql
    UPDATE products
    SET quantity = 10
    WHERE product_id = 1;
    ```

27. Question: Write a SQL query to calculate the total revenue for each category in a table named "products" by joining it with a table named "categories".
    Answer:
    ```sql
    SELECT c.category_name, SUM(p.price * p.quantity) AS total_revenue
    FROM products p
    JOIN categories c ON p.category_id = c.category_id
    GROUP BY c.category_name;
    ```

28. Question: Write a SQL query to retrieve the names of customers who have placed orders for at least two different products in a table named "orders".
    Answer:
    ```sql
    SELECT c.name
    FROM customers c
    JOIN orders o ON c.customer_id = o.customer_id
    GROUP BY c.name
    HAVING COUNT(DISTINCT o.product_id) >= 2;
    ```

29. Question: Write a SQL query to find the products that have never been ordered in a table named "products".
    Answer:
    ```sql
    SELECT p.product_id, p.product_name
    FROM products p
    LEFT JOIN orders o ON p.product_id = o.product_id
    WHERE o.order_id IS NULL;
    ```

30. Question: Write a SQL query to delete all records from a table named "employees" whose hire date is more than 5 years ago.
    Answer:
    ```sql
    DELETE FROM employees
    WHERE hire_date <= CURRENT_DATE - INTERVAL '5 years';
    ```

31. Question: How can you improve the performance of a slow SQL query?
    Answer: There are several approaches to improve query performance, such as:
    - Adding indexes to relevant columns used in the query.
    - Restructuring the query or using more efficient JOIN conditions.
    - Breaking down complex queries into smaller subqueries.
    - Using proper data types to reduce storage and memory usage.
    - Analyzing and optimizing the database schema for better performance.
    - Caching frequently accessed data using tools like Redis or Memcached.

32. Question: Write a SQL query to optimize a slow-performing query that involves joining multiple large tables.
    Answer:
    ```sql
    -- Create temporary tables for subsets of large tables
    CREATE TEMPORARY TABLE temp1 AS SELECT * FROM table1 WHERE condition;
    CREATE TEMPORARY TABLE temp2 AS SELECT * FROM table2 WHERE condition;

    -- Create indexes on temporary tables
    CREATE INDEX temp1_index ON temp1 (column1);
    CREATE INDEX temp2_index ON temp2 (column2);

    -- Perform optimized join using temporary tables
    SELECT *
    FROM temp1
    JOIN temp2 ON temp1.id = temp2.id
    WHERE condition;

    -- Clean up temporary tables
    DROP TABLE temp1;
    DROP TABLE temp2;
    ```

33. Question: How can you optimize a query that retrieves a large amount of data?
    Answer: To optimize a query that retrieves a large amount of data, you can:
    - Use pagination or limit the number of rows returned.
    - Filter the data using appropriate WHERE conditions to reduce the result set.
    - Optimize the query by adding indexes, optimizing joins, or rewriting the query structure.
    - Consider denormalizing the data or using summary tables for frequently accessed information.
    - Utilize database caching mechanisms to store and retrieve frequently accessed data.
    - Evaluate and optimize the hardware and infrastructure supporting the database system.

34. Question: Write a SQL query to optimize the performance of a slow query involving string pattern matching.
    Answer:
    ```sql
    -- Add an index on the column used for string pattern matching
    CREATE INDEX pattern_index ON table_name (column_name);

    -- Use a more efficient pattern matching function or operator
    SELECT *
    FROM table_name
    WHERE column_name LIKE 'prefix%';

    -- Alternatively, use regular expressions for more complex pattern matching
    SELECT *
    FROM table_name
    WHERE column_name ~ '^pattern';
    ```

35. Question: How can you improve the performance of SQL queries in a heavily used database?
    Answer: To improve performance in a heavily used database, you can:
    - Optimize database indexes to reduce the time required for data retrieval.
    - Analyze and optimize the database schema to minimize redundant or inefficient structures.
    - Consider database partitioning or sharding to distribute the load across multiple servers.
    - Implement caching mechanisms at the application or database level.
    - Tune the database server configuration parameters, such as memory allocation and query cache size.
    - Regularly monitor and analyze query execution plans to identify and resolve performance bottlenecks.

36. Question: Write a SQL query to optimize the performance of a slow query involving aggregation functions.
    Answer:
    ```sql
    -- Add indexes on columns used for grouping or filtering
    CREATE INDEX group_index ON table_name (group_column);
    CREATE INDEX filter_index ON table_name (filter_column);

    -- Use a subquery or common table expression (CTE) to filter data before aggregation
    WITH filtered_data AS (
        SELECT *
        FROM table_name
        WHERE filter_column = 'value'
    )
    SELECT group_column, COUNT(*)
    FROM filtered_data
    GROUP BY group_column;
    ```

37. Question: How can you improve the performance of a slow query that involves sorting large result sets?
    Answer: To improve the performance of a query involving sorting large result sets, you can:
    - Add an index on the columns used for sorting.
    - Limit the number of rows returned using pagination.
    - Use a more efficient sorting algorithm, such as an index-based sort.
    - Consider caching or pre-sorting data if the sorting requirement is frequent and stable.

38. Question: Write a SQL query to optimize the performance of a slow query that involves multiple nested subqueries.
    Answer:
    ```sql
    -- Rewrite the nested subqueries as join operations
    SELECT *
    FROM table1 t1
    JOIN (
        SELECT column2
        FROM table2
        WHERE condition
    ) t2 ON t1.column1 = t2.column2
    WHERE t1.condition;
    ```

39. Question: How can you optimize the performance of a query that involves joining multiple tables with complex conditions?
    Answer: To optimize a query with complex join conditions, you can:
    - Ensure relevant columns used for joining are indexed.
    - Break down the query into smaller subqueries or views to simplify the join conditions.
    - Use appropriate join types (e.g., INNER JOIN, LEFT JOIN) based on the desired result set.
    - Evaluate the order of table joins to minimize the intermediate result set size.
    - Consider denormalizing or restructuring the database schema to eliminate complex joins.

40. Question: Write a SQL query to improve the performance of a slow query that involves a large number of OR conditions.
    Answer:
    ```sql
    -- Use UNION instead of OR conditions
    SELECT *
    FROM table_name
    WHERE column_name = value1
    UNION
    SELECT *
    FROM table_name
    WHERE column_name = value2;
    ```

41. Question: How can you optimize the performance of a query that involves aggregate functions over large datasets?
    Answer: To optimize queries involving aggregate functions over large datasets, you can:
    - Add indexes on the columns used in the GROUP BY clause.
    - Use summary tables or materialized views to pre-aggregate data for faster retrieval.
    - Optimize the query by rewriting it to eliminate unnecessary joins or calculations.
    - Partition the data based on the grouping criteria to distribute the load across multiple partitions.
    - Consider using specialized analytics tools or frameworks for handling large-scale aggregations.

42. Question: Write a SQL query to optimize the performance of a slow query that involves a self-join on a large table.
    Answer:
    ```sql
    -- Create an index on the columns used for self-join
    CREATE INDEX self_join_index ON table_name (column1, column2);

    -- Use table aliases to optimize self-join
    SELECT *
    FROM table_name t1
    JOIN table_name t2 ON t1.column1 = t2.column2
    WHERE condition;
    ```

43. Question: How can you improve the performance of a query that involves multiple OR conditions?
    Answer: To improve the performance of queries involving multiple OR conditions, you can:
    - Rewrite the query using UNION or UNION ALL instead of OR conditions.
    - Ensure relevant columns used in OR conditions are indexed.
    - Break down the query into smaller subqueries with simpler conditions.
    - Evaluate the necessity of each OR condition and consider optimizing the query structure.

44. Question: Write a SQL query to optimize the performance of a slow query that involves a LIKE operator with a leading wildcard.
    Answer:
    ```sql
    -- Consider using a full

-text search solution instead of LIKE operator
    SELECT *
    FROM table_name
    WHERE column_name LIKE 'prefix%';

    -- Alternatively, use a search engine or indexing tool for efficient wildcard searches
    ```

45. Question: How can you optimize the performance of a query that involves a table with a large number of rows?
    Answer: To optimize queries on large tables, you can:
    - Add appropriate indexes on columns used for filtering and joining.
    - Partition the table based on specific criteria to improve query performance.
    - Analyze and optimize the database schema to eliminate redundant or inefficient structures.
    - Use proper data types and limit the amount of unnecessary data retrieval.
    - Consider database denormalization or using summary tables for frequently accessed information.

