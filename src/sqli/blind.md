# Blind SQLi

Blind SQL injection is a type of SQL injection attack where the attacker cannot see the results of the injected query. This means that the attacker cannot use traditional techniques such as UNION attacks to extract data from the database.

Instead, blind SQL injection attacks rely on the database to behave differently depending on the value of the injected query. For example, the attacker might inject a query that causes the database to sleep for a certain amount of time if the value of the query is true, and to return immediately if the value of the query is false.

The attacker can then use this behavior to infer the value of the injected query by observing the response time of the database. For example, if the database takes a long time to respond when the attacker injects the value "1", then the attacker can infer that the value of the query is true.

Here is an example of a blind SQL injection attack:

The attacker wants to know the name of the database. They know that the database name is stored in the `database` table, and that the `database` table has a column called `name`.

The attacker injects the following query into the application:

```sql
' OR SLEEP(5)
```


If the value of the `database` column is "test", then the database will sleep for 5 seconds before returning the results. If the value of the `database` column is not "test", then the database will return the results immediately.

The attacker can then use the response time of the database to infer the value of the `database` column. If the database takes a long time to respond, then the attacker can infer that the value of the `database` column is "test".

Blind SQL injection attacks can be very difficult to defend against. This is because the attacker does not need to see the results of the injected query in order to extract data from the database.

However, there are a number of things that can be done to reduce the risk of blind SQL injection attacks. These include:

* Using prepared statements to prevent SQL injection attacks.
* Validating user input carefully.
* Using a web application firewall to block malicious traffic.

By following these steps, you can help to reduce the risk of blind SQL injection attacks on your web application.

Blind SQL injection is a type of SQL injection attack where an attacker can exploit a vulnerability in a web application to retrieve information from the database without directly seeing the results. In blind SQL injection, the application does not display the results of the injected query, making it harder for the attacker to extract data. However, the attacker can infer information based on the application's behavior or responses.

There are two main types of blind SQL injection attacks:

1. **Boolean-Based Blind SQL Injection:**
   In a boolean-based blind SQL injection, the attacker crafts SQL queries with conditional statements that result in a true or false response. The application's behavior or response will indicate whether the condition is true or false, allowing the attacker to infer information.

   Example:
   Suppose a vulnerable login form uses the following SQL query to check the credentials:
   ```sql
   SELECT * FROM users WHERE username = '<input_username>' AND password = '<input_password>';
   ```

   The attacker could inject the following payload:
   ```
   ' OR 1=1; -- (input_username)
   ```

   The modified query will be:
   ```sql
   SELECT * FROM users WHERE username = '' OR 1=1; -- ' AND password = '<input_password>';
   ```

   If the application's response indicates a successful login, it means the injected condition `1=1` is true, and the attacker knows the username is valid.

2. **Time-Based Blind SQL Injection:**
   In time-based blind SQL injection, the attacker crafts SQL queries that introduce delays in the application's response. The attacker can infer information based on whether the response is delayed or not.

   Example:
   Suppose the application uses the following query to retrieve data:
   ```sql
   SELECT * FROM products WHERE product_id = '<input_product_id>';
   ```

   The attacker could inject the following payload:
   ```
   ' OR IF(1=1, SLEEP(5), 0); -- (input_product_id)
   ```

   The modified query will introduce a delay of 5 seconds if the condition `1=1` is true. The attacker can then observe the application's response time to infer whether the condition is true or false.

Blind SQL injection attacks can be more challenging to exploit than standard SQL injection because the attacker does not directly see the results of the injected query. However, they can be successful by carefully crafting payloads and analyzing the application's behavior or responses. It's essential for developers to follow secure coding practices, input validation, and parameterized queries to prevent SQL injection vulnerabilities.