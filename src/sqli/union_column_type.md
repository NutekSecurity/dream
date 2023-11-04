# Column type check

Injcet this statements to find out the column with string type

```sql
' UNION SELECT 'a',NULL,NULL,NULL--
' UNION SELECT NULL,'a',NULL,NULL--
' UNION SELECT NULL,NULL,'a',NULL--
' UNION SELECT NULL,NULL,NULL,'a'--
```

Try this until you get no error.

<a href="https://asciinema.org/a/L0w0gUaCxlErLyjBIvNBt5O0M" target="_blank"><img src="https://asciinema.org/a/L0w0gUaCxlErLyjBIvNBt5O0M.svg" /></a>

When performing a SQL injection UNION attack, it is important to find columns with a useful data type. This is because the attacker can only extract data from columns with a data type that can be returned by the database.

For example, if the attacker is trying to extract the names of all users in the database, they would need to find a column with a data type that can store text. If the only column with a text data type is the `email` column, the attacker would only be able to extract the email addresses of all users in the database.

Here are some of the most common data types that can be returned by the database:

* **CHAR:** This data type stores a fixed-length string of characters.
* **VARCHAR:** This data type stores a variable-length string of characters.
* **TEXT:** This data type stores a large string of characters.
* **INT:** This data type stores an integer value.
* **FLOAT:** This data type stores a floating-point value.

The attacker can use the `SELECT` statement to find columns with a useful data type. For example, the following statement would return all columns in the `users` table that have a data type of `VARCHAR`:

```sql
SELECT COLUMN_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = 'users' AND DATA_TYPE = 'VARCHAR';
```

Once the attacker has found a column with a useful data type, they can use it to extract data from the database.

Here are some ways to protect against UNION attacks:

* **Use prepared statements:** Prepared statements are a way of preventing SQL injection attacks by binding the input parameters to the query before it is executed.
* **Sanitize user input:** This involves removing any special characters that could be used to inject malicious code.
* **Use a web application firewall (WAF):** A WAF is a software application that can help to protect web applications from a variety of attacks, including SQL injection attacks.

In a SQL injection UNION attack, once you've determined the number of columns required in the injected query (as explained in the previous response), the next step is to identify columns with useful data types that can reveal valuable information. Typically, you want to find columns containing sensitive data such as usernames, passwords, or other valuable information.

Here's a step-by-step approach to finding columns with useful data types in a SQL injection UNION attack:

1. **Identify Potential Columns:** Inject the `UNION SELECT` statement into the vulnerable parameter as explained before, and make sure the injected query returns the same number of columns as the original query. For example:
   ```sql
   injected_parameter' UNION SELECT 1, 2, 3 --
   ```

2. **Observe the Response:** Examine the application's response after the injection. The injected data will likely appear somewhere on the page. If it doesn't appear directly, it might still influence the page layout or structure.

3. **Identify Data Type Mismatch:** If the data types in the injected query do not match the data types in the original query, you may receive an error or unexpected output. In this case, you need to identify the correct data types for each column.

4. **Fine-Tune Data Types:** To find columns with useful data types, you can use various SQL functions like `CAST`, `CONVERT`, or string concatenation (`||`) to manipulate the data types in the `UNION SELECT` statement. For example:
   ```sql
   injected_parameter' UNION SELECT CAST('admin' AS TEXT), username, password FROM users --
   ```

   In this example, we cast the string `'admin'` as the data type `TEXT` to match the data type of the `username` column in the original query.

5. **Check for Valuable Data:** Observe the response again after fine-tuning the data types. Look for information that appears as a result of the injected query. You may find sensitive data like usernames or passwords in the application's response.

6. **Explore Different Tables:** Depending on the application's database schema, you may want to explore different tables by changing the table names in the `FROM` clause of the injected query. For example:
   ```sql
   injected_parameter' UNION SELECT username, email, credit_card_number FROM customers --
   ```

   In this example, we assume there is a table named `customers` that contains columns like `username`, `email`, and `credit_card_number`.

7. **Retrieve Sensitive Data:** Once you identify columns with useful data types, you can retrieve sensitive information from the database through the SQL injection UNION attack. For example, you might extract usernames and hashed passwords to attempt password cracking.

It's essential to be cautious and ethical when conducting SQL injection attacks. Always seek permission from the application's owner before performing any security testing, and ensure you are not violating any laws or regulations during your testing process.

Sure. The SQL injection UNION attack, finding a column containing text tutorial example in PortSwigger Academy demonstrates how an attacker can use a UNION attack to find a column containing text in a database.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website is vulnerable to SQL injection because it does not properly sanitize user input. This means that an attacker can inject malicious SQL code into the website's database.

The attacker can use this vulnerability to find a column containing text by using a UNION attack. A UNION attack is a technique that allows an attacker to combine the results of two or more SQL queries into a single result set.

To exploit this vulnerability, the attacker would first need to identify a database table that contains the data they want to retrieve. They can do this by submitting a variety of malicious SQL queries and observing the results. Once the attacker has identified a table, they can then use a UNION attack to find a column containing text.

For example, the attacker could submit the following malicious query:

```sql
SELECT name, 'a' FROM users UNION SELECT email, 'a' FROM users;
```

This query will combine the results of the `SELECT name, 'a' FROM users` query with the results of the `SELECT email, 'a' FROM users` query. The result set will contain all of the names and emails of the users in the database, along with the string "a".

The attacker can then search the result set for the string "a". If they find it in a column, they know that the column contains text.

The attacker could then use this information to launch further attacks, such as phishing attacks or password guessing attacks.

The SQL injection UNION attack, finding a column containing text tutorial example is a good demonstration of how an attacker can use a UNION attack to find a column containing text in a database. It is important to be aware of this vulnerability and to take steps to protect yourself.

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