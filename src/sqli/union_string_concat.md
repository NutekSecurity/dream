# String concatenetaion

You can concatenate together multiple strings to make a single string.

| Database | Concatenetaion |
| --- | --- |
| MySQL |'foo' 'bar' [Here is the space] |
| MySQL | CONCAT('foo','bar') |
| PostgreSQL | 'foo'\|\|'bar' |
| Oracle | 'foo'\|\|'bar' |
| Microsoft | 'foo'+'bar' |

Here is a table of the standard way to concatenate strings in every popular SQL database:

| Database | Standard way to concatenate strings |
|---|---|
| MySQL | `CONCAT()` |
| PostgreSQL | &#124;&#124; |
| Microsoft SQL Server | `+` |
| Oracle | \|\| |
| DB2 | \|\| |

Here are some examples of how to concatenate strings in each database:

```sql
-- MySQL
SELECT CONCAT('Hello', ' ', 'world!');

-- PostgreSQL
SELECT 'Hello' || ' ' || 'world!';

-- Microsoft SQL Server
SELECT 'Hello' + ' ' + 'world!';

-- Oracle
SELECT 'Hello' || ' ' || 'world!';

-- DB2
SELECT 'Hello' || ' ' || 'world!';
```

## Example

<a href="https://asciinema.org/a/2Oet12DxnrQXuWf0f22gXldVL" target="_blank"><img src="https://asciinema.org/a/2Oet12DxnrQXuWf0f22gXldVL.svg" /></a>

Sure. The SQL injection UNION attack, retrieving multiple values in a single column tutorial example in PortSwigger Academy demonstrates how an attacker can use a UNION attack to retrieve multiple values from a single column in a database.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website is vulnerable to SQL injection because it does not properly sanitize user input. This means that an attacker can inject malicious SQL code into the website's database.

The attacker can use this vulnerability to retrieve multiple values from a single column by using a UNION attack. A UNION attack is a technique that allows an attacker to combine the results of two or more SQL queries into a single result set.

To exploit this vulnerability, the attacker would first need to identify a database table that contains the values they want to retrieve. They can do this by submitting a variety of malicious SQL queries and observing the results. Once the attacker has identified a table, they can then use a UNION attack to retrieve the values.

For example, the attacker could submit the following malicious query:

```sql
SELECT name FROM users UNION SELECT id FROM users;
```

This query will combine the results of the `SELECT name FROM users` query with the results of the `SELECT id FROM users` query. The result set will contain all of the names and IDs of the users in the database.

The SQL injection UNION attack, retrieving multiple values in a single column tutorial example is a good demonstration of how an attacker can use a UNION attack to retrieve multiple values from a single column in a database. It is important to be aware of this vulnerability and to take steps to protect yourself.

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