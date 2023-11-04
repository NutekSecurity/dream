# UNION attacks

A UNION attack is a type of SQL injection attack where the attacker injects a UNION statement into a database query. This allows the attacker to combine the results of two or more queries, which can be used to extract sensitive data from the database.

For example, let's say there is a web application that allows users to search for products. The application uses a SQL query to retrieve the results of the search. The query might look something like this:

```sql
SELECT * FROM products WHERE product_name LIKE '%search_term%';
```

An attacker could inject a UNION statement into the query like this:

```sql
SELECT * FROM products WHERE product_name LIKE '%search_term%' UNION SELECT * FROM users;
```

This would cause the database to return the results of both queries, which would include the names and email addresses of all users in the database.

Here is another example. Let's say there is a web application that allows users to log in. The application uses a SQL query to check the username and password of the user. The query might look something like this:

```sql
SELECT * FROM users WHERE username = 'username' AND password = 'password';
```

An attacker could inject a UNION statement into the query like this:

```sql
SELECT * FROM users WHERE username = 'username' AND password = 'password' UNION SELECT 1, 2, 3;
```

This would cause the database to return the results of both queries, which would include the first three rows in the `users` table.

UNION attacks can be very powerful, and they can be used to extract sensitive data from a database. It is important to protect your web applications from SQL injection attacks by using prepared statements and other security measures.

Here are some ways to protect against UNION attacks:

* **Use prepared statements:** Prepared statements are a way of preventing SQL injection attacks by binding the input parameters to the query before it is executed.
* **Sanitize user input:** This involves removing any special characters that could be used to inject malicious code.
* **Use a web application firewall (WAF):** A WAF is a software application that can help to protect web applications from a variety of attacks, including SQL injection attacks.

SQL injection UNION attacks are a type of SQL injection attack that involves using the UNION operator to combine the results of a malicious query with the results of a legitimate query. This allows an attacker to retrieve data from tables they are not authorized to access, gain sensitive information, or even perform further attacks on the database.

Here's a brief explanation of SQL injection UNION attacks with examples:

Consider a vulnerable web application that constructs an SQL query using user-supplied input without proper validation and sanitization.

1. Initial Vulnerable Query:
   For example, let's say the application's code builds an SQL query like this:
   ```sql
   $username = $_POST['username'];
   $sql = "SELECT * FROM users WHERE username = '$username'";
   ```

   An attacker notices that the application is vulnerable to SQL injection and decides to exploit it. They submit the following malicious input as the `username` parameter:
   ```
   ' UNION SELECT null, null, null, null, password FROM users WHERE '1'='1
   ```

   The SQL query executed by the application will become:
   ```sql
   SELECT * FROM users WHERE username = '' UNION SELECT null, null, null, null, password FROM users WHERE '1'='1'
   ```

2. Exploiting the UNION Operator:
   The attacker's input causes the application to execute two queries: the original query and the attacker's injected query. The UNION operator combines the results of both queries. The injected query selects the `password` field from the `users` table. As a result, the attacker can retrieve the hashed passwords of all users in the database.

SQL injection UNION attacks can be more potent when the attacker can infer the number and data types of columns in the query. By using functions like `UNION SELECT`, `ORDER BY`, and `LIMIT`, the attacker can fine-tune the results to extract specific information.

Preventing SQL injection UNION attacks (and all SQL injection attacks) involves using parameterized queries or prepared statements, which ensure that user input is treated as data rather than executable SQL code. Additionally, input validation and escaping should be employed to handle user input safely.