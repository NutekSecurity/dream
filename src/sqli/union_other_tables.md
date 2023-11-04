# Get other tables

A SQL injection UNION attack is a type of SQL injection attack where the attacker injects a UNION statement into a database query. This allows the attacker to combine the results of two or more queries, which can be used to extract sensitive data from the database.

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

To retrieve interesting data using a UNION attack, the attacker would need to know the structure of the database and the data types of the columns. Once the attacker knows this information, they can inject a UNION statement that will return the data they are interested in.

For example, if the attacker is interested in the names and email addresses of all users in the database, they would need to inject a UNION statement that returns the `name` and `email` columns from the `users` table.

The attacker would also need to know the number of columns in the `users` table. This is because the UNION statement must have the same number of columns as the original query.

Once the attacker has injected the UNION statement, they can submit it to the web application. The database will then return the results of both queries, which will include the data that the attacker is interested in.

It is important to note that UNION attacks can be very difficult to detect. This is because the attacker can use the UNION statement to return data that is similar to the data that is returned by the original query. This makes it difficult for the web application to detect that an attack has occurred.

Here are some ways to detect UNION attacks:

* **Use a web application firewall (WAF):** A WAF can be used to detect UNION attacks by looking for patterns in the traffic that is sent to the web application.
* **Use anomaly detection:** Anomaly detection can be used to detect UNION attacks by looking for patterns that are not normally seen in the traffic that is sent to the web application.
* **Use manual auditing:** Manual auditing can be used to detect UNION attacks by looking for patterns in the data that is returned by the web application.

I hope this helps! Let me know if you have any other questions.

In a SQL injection UNION attack, the UNION operator is used to combine the results of a malicious query with the results of a legitimate query. This technique allows an attacker to retrieve interesting or sensitive data from the database that they are not authorized to access directly.

Here's how a SQL injection UNION attack can be used to retrieve interesting data:

1. **Identify a Vulnerable Parameter:** Find a parameter in the application that is vulnerable to SQL injection. This parameter should be used in an SQL query without proper validation and sanitization.

2. **Determine the Number of Columns:** Use a trial-and-error approach to determine the number of columns required in the injected query. This involves injecting `UNION SELECT` statements with different numbers of columns until you get a valid response.

3. **Find Columns with Useful Data Types:** Once you know the correct number of columns, identify columns in the database that contain interesting or sensitive data. Common targets include usernames, passwords, email addresses, credit card numbers, or other confidential information.

4. **Fine-Tune the Data Types:** Adjust the data types of the `UNION SELECT` statement to match the data types of the columns in the original query. This may involve using functions like `CAST` or `CONVERT` to ensure compatibility.

5. **Retrieve Interesting Data:** Execute the SQL injection UNION attack with the modified `UNION SELECT` statement to retrieve the interesting data. The results of the injected query will be combined with the results of the original query, and the interesting data will be presented in the application's response.

For example, consider a vulnerable application with the following SQL query to fetch user information based on the provided username:

```sql
SELECT username, email, address FROM users WHERE username = 'input';
```

An attacker discovers that the "username" parameter is vulnerable to SQL injection. They can use a UNION attack to retrieve the email addresses of all users in the database. Suppose the injected query looks like this:

```
' UNION SELECT null, email, null FROM users --
```

The modified query will be:

```sql
SELECT username, email, address FROM users WHERE username = '' UNION SELECT null, email, null FROM users --';
```

The injected query adds a `UNION SELECT` statement to fetch the "email" column from the "users" table. The application will execute this injected query alongside the original query and return the concatenated results.

With the successful execution of the SQL injection UNION attack, the attacker can extract email addresses from the database and access sensitive user information.

It is crucial to note that SQL injection attacks are illegal and unethical unless you have explicit permission to test the security of an application. Always follow responsible disclosure practices and obtain proper authorization before attempting any security testing.

Try this: 

```sql
' UNION SELECT username, password FROM users--
```

<a href="https://asciinema.org/a/ygM5Lv9pQkvVOnzUc0nDbwxG8" target="_blank"><img src="https://asciinema.org/a/ygM5Lv9pQkvVOnzUc0nDbwxG8.svg" /></a>

Sure. The SQL injection UNION attack, retrieving data from other tables tutorial example in PortSwigger Academy demonstrates how an attacker can use a UNION attack to retrieve data from other tables in a database.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website is vulnerable to SQL injection because it does not properly sanitize user input. This means that an attacker can inject malicious SQL code into the website's database.

The attacker can use this vulnerability to retrieve data from other tables by using a UNION attack. A UNION attack is a technique that allows an attacker to combine the results of two or more SQL queries into a single result set.

To exploit this vulnerability, the attacker would first need to identify a database table that contains the data they want to retrieve. They can do this by submitting a variety of malicious SQL queries and observing the results. Once the attacker has identified a table, they can then use a UNION attack to retrieve the data.

For example, the attacker could submit the following malicious query:

```sql
SELECT name FROM users UNION SELECT email FROM users;
```

This query will combine the results of the `SELECT name FROM users` query with the results of the `SELECT email FROM users` query. The result set will contain all of the names and emails of the users in the database.

The attacker could then use this information to launch further attacks, such as phishing attacks or password guessing attacks.

The SQL injection UNION attack, retrieving data from other tables tutorial example is a good demonstration of how an attacker can use a UNION attack to retrieve data from other tables in a database. It is important to be aware of this vulnerability and to take steps to protect yourself.

Here are some tips for protecting yourself from UNION attacks:

* Use a strong username and password for your online accounts.
* Change your passwords regularly.
* Be suspicious of emails or text messages that ask for your personal information.
* Install antivirus software and keep it up to date.
* Be careful about what websites you visit and what links you click on.
* Train yourself and your employees on how to identify and avoid phishing attacks.

By following these tips, you can help to protect yourself from UNION attacks and keep your accounts safe.

In addition to the tips above, there are a few things that the website can do to protect itself from UNION attacks:

* Use a rate limiting mechanism to prevent users from submitting too many requests in a short period of time.
* Use a honeypot account to lure attackers into entering malicious SQL queries.
* Implement a CAPTCHA challenge to verify that the user is human.
* Use a prepared statement mechanism to prevent attackers from injecting malicious SQL code into the database.
* Use a database auditing mechanism to detect and log suspicious SQL queries.

By implementing these measures, the website can help to protect itself from UNION attacks.