# Know what and where

Examining the database in SQL injection attacks is a process of identifying and exploiting vulnerabilities in a database to gain unauthorized access to sensitive data. This can be done by injecting malicious code into a web application that interacts with the database.

Once the attacker has gained access to the database, they can use it to steal data, modify data, or even delete data. They can also use the database to gain access to other systems or networks.

There are a number of ways to examine the database in SQL injection attacks. One way is to use a tool like SQLMap. SQLMap is a free and open-source tool that can be used to automate the process of identifying and exploiting SQL injection vulnerabilities.

Another way to examine the database is to use a web application firewall (WAF). A WAF can be used to detect and block SQL injection attacks. However, WAFs are not always effective, and they can sometimes be bypassed by attackers.

Finally, it is also possible to examine the database manually. This can be done by looking for patterns in the data that is returned by the web application. For example, if the attacker is able to retrieve the names and email addresses of all users in the database, this is a sign that an SQL injection attack has occurred.

Here are some ways to protect against SQL injection attacks:

* **Use prepared statements:** Prepared statements are a way of preventing SQL injection attacks by binding the input parameters to the query before it is executed.
* **Sanitize user input:** This involves removing any special characters that could be used to inject malicious code.
* **Use a web application firewall (WAF):** A WAF is a software application that can help to protect web applications from a variety of attacks, including SQL injection attacks.
* **Use a database firewall:** A database firewall is a hardware or software appliance that can be used to protect databases from a variety of attacks, including SQL injection attacks.
* **Use a vulnerability scanner:** A vulnerability scanner is a tool that can be used to scan web applications for known vulnerabilities, including SQL injection vulnerabilities.

In SQL injection attacks, examining the database involves extracting information or manipulating data within the database to gain unauthorized access to sensitive information or perform malicious actions. The goal is to exploit vulnerabilities in the application's input validation and interact with the underlying database in unintended ways.

Here are some common techniques attackers use to examine the database in SQL injection attacks:

1. **Data Extraction:** Attackers can use SQL injection to extract data from the database that they are not authorized to access. They may retrieve sensitive information such as usernames, passwords, email addresses, credit card numbers, or other valuable data.

2. **UNION-Based Attacks:** As explained earlier, attackers can use the UNION operator to combine the results of a malicious query with the results of a legitimate query, allowing them to retrieve data from additional tables or columns.

3. **Error-Based Attacks:** Attackers can exploit error messages returned by the database to gather information about the database schema, table names, or column names. This information aids in further attacks.

4. **Time-Based Attacks:** Time-based attacks involve using conditional SQL statements that cause delays in the application's response. The attacker can infer information about the database based on the delay in the response.

5. **Out-of-Band (OOB) Attacks:** OOB attacks leverage the application to interact with external systems to retrieve data or exfiltrate information from the database.

6. **Blind SQL Injection:** In situations where the application does not return specific error messages or information, attackers may use blind SQL injection techniques to infer data through true/false statements or numerical responses.

7. **Modifying Data:** In some cases, attackers may use SQL injection to manipulate or modify data in the database. For example, they could modify records, insert malicious data, or delete data from the database.

It is essential to remember that SQL injection attacks are illegal and unethical unless you have explicit permission to test the security of an application. Unauthorized access to or manipulation of databases is a serious security violation and may lead to legal consequences.

For responsible disclosure and security testing, always seek permission from the application owner or security team before attempting any form of security assessment. Ethical hacking, or penetration testing, should only be performed with proper authorization and within a controlled testing environment.

Sure, here are some SQL examples of examining the database in SQL injection attacks:

* **Finding the names of all tables in the database:**

```sql
SELECT name FROM INFORMATION_SCHEMA.TABLES;
```

* **Finding the columns in a specific table:**

```sql
SELECT COLUMN_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = 'table_name';
```

* **Finding the data in a specific column:**

```sql
SELECT data FROM table_name WHERE column_name = 'column_value';
```

* **Retrieving the results of a query:**

```sql
SELECT * FROM table_name;
```

* **Combining the results of two queries:**

```sql
SELECT * FROM table_name UNION SELECT * FROM table_name2;
```

These are just a few examples of how to examine the database in SQL injection attacks. The specific queries that you can use will depend on the structure of the database and the data that you are interested in.

It is important to note that UNION attacks can be very dangerous. If an attacker is able to inject a UNION statement into a web application, they could potentially extract sensitive data from the database. It is important to protect your web applications from SQL injection attacks by using prepared statements and other security measures.

Here are some ways to protect against UNION attacks:

* **Use prepared statements:** Prepared statements are a way of preventing SQL injection attacks by binding the input parameters to the query before it is executed.
* **Sanitize user input:** This involves removing any special characters that could be used to inject malicious code.
* **Use a web application firewall (WAF):** A WAF is a software application that can help to protect web applications from a variety of attacks, including SQL injection attacks.

Here are some SQL examples demonstrating how attackers can examine the database using SQL injection:

1. **Extracting Usernames and Password Hashes:**
   Suppose the application has a login form with the following SQL query:
   ```sql
   SELECT * FROM users WHERE username = '<input_username>' AND password = '<input_password>';
   ```

   An attacker can use SQL injection to extract usernames and password hashes:
   ```
   ' OR 1=1; --   (input_username)
   ```

   The modified query will be:
   ```sql
   SELECT * FROM users WHERE username = '' OR 1=1; -- ' AND password = '<input_password>';
   ```

   Since `1=1` is always true, the attacker will get results for all users, including their usernames and password hashes.

2. **Enumerating Table Names:**
   Suppose the application uses the following SQL query to retrieve data:
   ```sql
   SELECT * FROM information_schema.tables WHERE table_schema = 'public';
   ```

   An attacker can use SQL injection to enumerate table names:
   ```
   ' UNION SELECT table_name, null, null FROM information_schema.tables WHERE table_schema = 'public'; -- 
   ```

   The injected query will return the names of all tables in the `public` schema.

3. **Extracting Sensitive Data from Specific Columns:**
   Let's assume the application uses the following query to display user profiles:
   ```sql
   SELECT full_name, email, credit_card FROM user_profiles WHERE user_id = '<input_user_id>';
   ```

   An attacker can use SQL injection to extract sensitive data:
   ```
   ' UNION SELECT password, null, null FROM users WHERE user_id = '1'; -- 
   ```

   The attacker retrieves the hashed passwords of user accounts by injecting the UNION statement to fetch data from the `users` table.

4. **Error-Based Enumeration:**
   An attacker may exploit errors in SQL queries to gather information about the database structure. For example:
   ```
   ' AND 1=CONVERT(int, (SELECT @@version)); --
   ```
   The attacker will receive an error message containing the database version.

5. **Time-Based Attacks:**
   Attackers can use time-based SQL injection to infer data from the database based on conditional SQL statements. For instance:
   ```
   ' OR IF(1=1, SLEEP(5), 0); --
   ```
   The query will introduce a delay if the condition `1=1` is true, helping the attacker infer information.

These examples demonstrate how SQL injection can be exploited to examine and extract data from a vulnerable database. Remember that these examples are for educational purposes only, and unauthorized SQL injection attacks are illegal and unethical. Always ensure you have explicit permission to conduct security testing on any application or database.