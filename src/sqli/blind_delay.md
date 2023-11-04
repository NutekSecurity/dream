# Time delays

Blind SQL injection with time delays is a technique used by attackers to exploit web applications that are vulnerable to SQL injection but do not provide direct feedback to the attacker about the success or failure of the injected SQL query. In such cases, the attacker cannot see the actual results of the injected query directly, but they can infer the information indirectly by inducing time delays in the server's response.

Here's how Blind SQL injection with time delays works:

1. **Identifying a Vulnerable Parameter**: The attacker identifies a user-input parameter in a web application that is susceptible to SQL injection. This could be a URL parameter, a form field, or any other input that is used to construct an SQL query.

2. **Injecting Malicious SQL**: The attacker then injects malicious SQL code into the vulnerable parameter to manipulate the original SQL query. The goal is usually to extract sensitive information from the application's database.

3. **Time Delay Payload**: In a regular Blind SQL injection, the attacker cannot directly see the results of the injected query. However, by introducing time delays in the server's response, they can determine whether a specific condition is true or false. For example, they may inject a query that causes the server to delay its response for a certain amount of time if a particular condition is met.

4. **Inference of Information**: Based on the server's response time, the attacker can infer whether the condition they injected is true or false. By repeatedly injecting queries with different conditions and observing the response times, the attacker can gradually reconstruct the information they seek.

**Example**:

Suppose we have a vulnerable web application with a search feature that accepts a parameter called `product_id` and uses it to construct an SQL query to fetch product information from the database. The application displays product details if a valid `product_id` is provided.

Here's an example of a Blind SQL injection with time delays:

Original URL: `https://example.com/products?product_id=123`

Suppose the attacker wants to know if there's a product with `product_id` equal to `456`. They can inject the following SQL code:

```
https://example.com/products?product_id=123' AND (SELECT CASE WHEN (SELECT COUNT(*) FROM products WHERE product_id = 456) = 1 THEN pg_sleep(10) ELSE pg_sleep(10) END)-- 
```

In this example, the injected SQL code checks if there's a product with `product_id` equal to `456`. If the condition is true, the database will introduce a 10-second delay in the server's response due to the `pg_sleep(10)` function. If the condition is false, there will be no delay.

By observing the response time of the web application, the attacker can determine whether the product with `product_id` equal to `456` exists or not.

It's crucial to note that Blind SQL injection attacks can be time-consuming because the attacker needs to carefully construct and test different queries to infer the desired information. Web application developers should take measures to prevent SQL injection vulnerabilities, such as using parameterized queries or prepared statements, to avoid such attacks.

Here is a table showing the time delays in different databases:

| Database | Function | Notes |
|---|---|---|
| MySQL | SLEEP(time) | Only available since MySQL 5. It takes a number of seconds to wait in parameter. |
| MySQL | BENCHMARK(count, expr) | Executes the specified expression multiple times. By using a large number as first parameter, you will be able to generate a delay. |
| SQL Server | WAIT FOR DELAY 'hh:mm:ss' | Suspends the execution for the specified amount of time. |
| SQL Server | WAIT FOR TIME 'hh:mm:ss' | Suspends the execution of the query and continues it when system time is equal to parameter. |
| Oracle | DBMS_LOCK.SLEEP(time) | Suspends the execution for the specified amount of time. |
| Oracle | DBMS_LOCK.SPIN(time) | Spins for the specified amount of time. |
| Oracle | dbms_pipe.receive_message(('a'),10) | Sleep for 10 seconds |
| PostgreSQL | SELECT pg_sleep(10) | Sleep for 10 seconds |

Please note that these are just a few examples of time delays that can be used in different databases. There may be other functions or procedures available that can be used to achieve the same effect.

Here is an example of how to use the SLEEP() function in MySQL to create a 2-minute delay:

```sql
SELECT SLEEP(120);
```

This query will sleep for 120 seconds, which is equal to 2 minutes.

## Example of time delay in SQL injection:

<a href="https://asciinema.org/a/XDktRWnI6XruE1ZeL06PH7CyK" target="_blank"><img src="https://asciinema.org/a/XDktRWnI6XruE1ZeL06PH7CyK.svg" /></a>

Sure. The Blind SQL injection with time delays tutorial example in PortSwigger Academy demonstrates how a website can be vulnerable to blind SQL injection attacks by using time delays.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website is vulnerable to blind SQL injection because it does not properly sanitize user input. This means that an attacker can inject malicious SQL code into the website's database.

The attacker can use this vulnerability to enumerate the database contents by using time delays. Specifically, the attacker can submit a malicious SQL query to the website and measure the response time. If the response time is longer than a certain threshold, the attacker can infer that the query has returned a result set.

To exploit this vulnerability, the attacker would first need to identify a database table that they want to enumerate. They can do this by submitting a variety of malicious SQL queries and observing the response times. Once the attacker has identified a table, they can then use time delays to enumerate the table contents.

The Blind SQL injection with time delays tutorial example is a good demonstration of how a website can be vulnerable to blind SQL injection attacks by using time delays. It is important to be aware of these vulnerabilities and to take steps to protect yourself.

Here are some tips for protecting yourself from blind SQL injection attacks:

* Use a strong username and password for your online accounts.
* Change your passwords regularly.
* Be suspicious of emails or text messages that ask for your personal information.
* Install antivirus software and keep it up to date.
* Be careful about what websites you visit and what links you click on.
* Train yourself and your employees on how to identify and avoid phishing attacks.

By following these tips, you can help to protect yourself from blind SQL injection attacks and keep your accounts safe.

In addition to the tips above, there are a few things that the website can do to protect itself from blind SQL injection attacks:

* Use a rate limiting mechanism to prevent users from submitting too many requests in a short period of time.
* Use a honeypot account to lure attackers into entering malicious SQL queries.
* Implement a CAPTCHA challenge to verify that the user is human.
* Use a random query time mechanism to prevent attackers from identifying results sets from response times.

By implementing these measures, the website can help to protect itself from blind SQL injection attacks.