# Second-order SQLi

**Second-order SQL injection** is a type of SQL injection attack where the attacker injects malicious code into a database query that is stored in a web application. The malicious code is then executed when the query is run, which can allow the attacker to gain access to sensitive data or take control of the application.

The difference between first-order and second-order SQL injection is that in first-order injection, the malicious code is executed immediately. In second-order injection, the malicious code is stored in the database and is not executed until the query is run. This makes second-order injection more difficult to detect, because the malicious code is not executed immediately.

Here is an example of a second-order SQL injection attack:

The attacker visits a web application that allows users to search for products. The attacker enters the following search query:

```
' OR 1=1; --
```

The `'` character is a single quote, which is used to escape special characters in SQL queries. The `OR 1=1` statement is a Boolean expression that always evaluates to true. The `; --` statement is a comment that tells the SQL parser to ignore the rest of the query.

When the user submits the search query, the web application will store the query in the database. The next time a user searches for products, the web application will run the query and return the results. However, the malicious code that was injected by the attacker will also be executed. This will allow the attacker to gain access to sensitive data or take control of the application.

Here are some ways to protect against second-order SQL injection attacks:

* **Sanitize user input:** This involves removing any special characters that could be used to inject malicious code.
* **Use prepared statements:** Prepared statements are a way of preventing SQL injection attacks by binding the input parameters to the query before it is executed.
* **Use a web application firewall (WAF):** A WAF is a software application that can help to protect web applications from a variety of attacks, including SQL injection attacks.

Second-order SQL injection is a type of SQL injection attack that occurs when the malicious input is stored in the database and later used in a subsequent query, leading to SQL injection vulnerabilities in different parts of the application.

Let's explain it with an example:

Suppose we have a simple web application that allows users to post comments on a website. The application takes the user's input and stores it in the database without proper input validation and sanitization.

1. Initial SQL Injection Vulnerability:
   The application has a comment submission form where users can post their comments. The user input is directly used in an SQL query without proper validation and escaping. For example:
   ```sql
   $comment = $_POST['comment'];
   $sql = "INSERT INTO comments (content) VALUES ('$comment')";
   ```

   A user decides to post a comment with malicious input:
   ```
   acorn'; DROP TABLE users; --
   ```

   The SQL query executed will become:
   ```sql
   INSERT INTO comments (content) VALUES ('acorn'; DROP TABLE users; --')
   ```

   The attacker successfully executes an SQL injection attack, attempting to drop the "users" table.

2. Second-Order SQL Injection Vulnerability:
   The application stores the comment in the database without any immediate issues. However, later in the application's lifecycle, the comments are retrieved and displayed on another page, such as a comment history page or the main website. The application uses the stored comment content directly in another SQL query without proper validation. For example:
   ```sql
   $comment_id = $_GET['id'];
   $sql = "SELECT * FROM comments WHERE id = $comment_id";
   ```

   The malicious comment containing the payload from the initial SQL injection is retrieved from the database and used in the new query:
   ```
   $comment_id = 1; -- (malicious comment with payload)
   ```

   The SQL query executed will become:
   ```sql
   SELECT * FROM comments WHERE id = 1; --'
   ```

   The attacker successfully executes a second-order SQL injection attack, potentially manipulating or extracting data from the database.

Second-order SQL injection can be more challenging to detect and mitigate compared to traditional SQL injection attacks because the attack occurs in a different part of the application flow and not directly in the initial user input. Proper input validation, parameterized queries, and escaping of user inputs can help prevent both first-order and second-order SQL injection vulnerabilities.