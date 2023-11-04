# Show schema

## Microsoft SQL, PostgreSQL, MySQL and such...

### Tables in database

Databases use this syntax to show content

```sql
SELECT * FROM information_schema.tables
```

This are the most common column names:

- TABLE_CATALOG
- TABLE_SCHEMA
- TABLE_NAME
- TABLE_TYPE

Here are the column names in the `information_schema.TABLES` table:

| Column Name | Description |
|---|---|
| TABLE_CATALOG | The catalog name. |
| TABLE_SCHEMA | The schema name. |
| TABLE_NAME | The table name. |
| COLUMN_NAME | The column name. |
| DATA_TYPE | The data type of the column. |
| IS_NULLABLE | Whether the column can be null. |
| COLUMN_DEFAULT | The default value for the column. |
| ORDINAL_POSITION | The ordinal position of the column. |
| COLUMN_TYPE | The type of the column. |
| COLUMN_SIZE | The size of the column. |
| BUFFER_LENGTH | The buffer length of the column. |
| DECIMAL_DIGITS | The number of decimal digits for the column. |
| PSEUDO_COLUMN | Whether the column is a pseudo-column. |
| REMARKS | The comments for the column. |

The `information_schema.TABLES` table is a read-only view that provides information about all of the tables in the database. This information can be useful for troubleshooting problems with the tables or for identifying security vulnerabilities.

To query the `information_schema.TABLES` view, you can use the following SQL statement:

```sql
SELECT * FROM information_schema.TABLES;
```

This will return all of the columns in the `information_schema.TABLES` view.

### Columns in tables

On the other hand, this SQL request will display columns in particular table:

```sql
SELECT * FROM information_schema.columns WHERE table_name = 'Users'
```

And this are the returned column names:

- TABLE_CATALOG
- TABLE_SCHEMA
- TABLE_NAME
- COLUMN_NAME
- DATA_TYPE

Here are the column names in the `information_schema.COLUMNS` table:

| Column Name | Description |
|---|---|
| TABLE_CATALOG | The catalog name. |
| TABLE_SCHEMA | The schema name. |
| TABLE_NAME | The table name. |
| COLUMN_NAME | The column name. |
| DATA_TYPE | The data type of the column. |
| TYPE_NAME | The name of the data type. |
| COLUMN_SIZE | The size of the column. |
| BUFFER_LENGTH | The buffer length of the column. |
| DECIMAL_DIGITS | The number of decimal digits for the column. |
| NUMERIC_PRECISION | The precision of the column. |
| NUMERIC_SCALE | The scale of the column. |
| NULLABLE | Whether the column can be null. |
| IS_NULLABLE | The type of the nullability. |
| COLUMN_DEFAULT | The default value for the column. |
| COLLATION_NAME | The collation name for the column. |
| ORDINAL_POSITION | The ordinal position of the column. |
| COLUMN_PRIVILEGES | The privileges on the column. |
| REFERENCED_TABLE_NAME | The name of the table that the column references, if applicable. |
| REFERENCED_COLUMN_NAME | The name of the column that the column references, if applicable. |

The `information_schema.COLUMNS` table is a read-only view that provides information about all of the columns in the database. This information can be useful for troubleshooting problems with the columns or for identifying security vulnerabilities.

To query the `information_schema.COLUMNS` view, you can use the following SQL statement:

```sql
SELECT * FROM information_schema.COLUMNS;
```

This will return all of the columns in the `information_schema.COLUMNS` view.

### Example

<a href="https://asciinema.org/a/7ntfiUmnKGtRJktKMHmGnFk3d" target="_blank"><img src="https://asciinema.org/a/7ntfiUmnKGtRJktKMHmGnFk3d.svg" /></a>

Sure. The SQL injection attack, listing the database contents on non-Oracle tutorial example in PortSwigger Academy demonstrates how an attacker can use a SQL injection attack to list the contents of a database on a non-Oracle server.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website is vulnerable to SQL injection because it does not properly sanitize user input. This means that an attacker can inject malicious SQL code into the website's database.

The attacker can use this vulnerability to list the contents of the database by using a SQL injection attack. A SQL injection attack is a technique that allows an attacker to execute arbitrary SQL commands on a database server.

To exploit this vulnerability, the attacker would first need to identify a database table that contains the data they want to retrieve. They can do this by submitting a variety of malicious SQL queries and observing the results. Once the attacker has identified a table, they can then use a SQL injection attack to list the contents of the table.

For example, the attacker could submit the following malicious query:

```sql
SELECT * FROM users WHERE username = 'admin' AND password = '' --
```

This query will select all of the rows from the `users` table where the `username` column is equal to `admin` and the `password` column is equal to the empty string.

If the query is successful, the attacker will be able to see all of the usernames and passwords in the `users` table.

The attacker could then use this information to launch further attacks, such as phishing attacks or password guessing attacks.

The SQL injection attack, listing the database contents on non-Oracle tutorial example is a good demonstration of how an attacker can use a SQL injection attack to list the contents of a database on a non-Oracle server. It is important to be aware of this vulnerability and to take steps to protect yourself.

Here are some tips for protecting yourself from SQL injection attacks:

* Use a strong username and password for your online accounts.
* Change your passwords regularly.
* Be suspicious of emails or text messages that ask for your personal information.
* Install antivirus software and keep it up to date.
* Be careful about what websites you visit and what links you click on.
* Train yourself and your employees on how to identify and avoid phishing attacks.

By following these tips, you can help to protect yourself from SQL injection attacks and keep your accounts safe.

In addition to the tips above, there are a few things that the website can do to protect itself from SQL injection attacks:

* Use a rate limiting mechanism to prevent users from submitting too many requests in a short period of time.
* Use a honeypot account to lure attackers into entering malicious SQL queries.
* Implement a CAPTCHA challenge to verify that the user is human.
* Use a prepared statement mechanism to prevent attackers from injecting malicious SQL code into the database.
* Use a database auditing mechanism to detect and log suspicious SQL queries.

By implementing these measures, the website can help to protect itself from SQL injection attacks.

## Oracle

### Tables in database

Here are the column names in the `ALL_TABLES` table in Oracle Database:

| Column Name | Description |
|---|---|
| OWNER | The owner of the table. |
| TABLE_NAME | The name of the table. |
| TABLESPACE_NAME | The tablespace where the table is stored. |
| CLUSTER_NAME | The cluster name, if applicable. |
| CREATED | The date and time the table was created. |
| LAST_DDL_TIME | The date and time the table was last modified. |
| SEGMENT_TYPE | The type of segment that the table is stored in. |
| STATUS | The status of the table. |
| TEMPORARY | Whether the table is a temporary table. |
| PCTFREE | The percentage of free space in each data block. |
| PCTUSED | The percentage of used space in each data block. |
| INITRANS | The number of initial transactions for the table. |
| MAXTRANS | The maximum number of transactions for the table. |
| STORAGE | The storage parameters for the table. |
| INITIAL_EXTENT | The size of the initial extent for the table. |
| NEXT_EXTENT | The size of the next extent for the table. |
| MINEXTENTS | The minimum number of extents for the table. |
| MAXEXTENTS | The maximum number of extents for the table. |
| PCTINCREASE | The percentage by which the size of the table will increase when it needs to be resized. |
| LOGGING | Whether the table is logged. |
| COMPRESS | Whether the table is compressed. |
| ENCRYPT | Whether the table is encrypted. |

The `ALL_TABLES` table is a read-only view that provides information about all of the tables in the database. This information can be useful for troubleshooting problems with the tables or for identifying security vulnerabilities.

To query the `ALL_TABLES` view, you can use the following SQL statement:

```sql
SELECT * FROM ALL_TABLES;
```

This will return all of the columns in the `ALL_TABLES` view.

### Columns in tables

```sql
SELECT * FROM all_tab_columns WHERE table_name = 'USERS'
```

Here are the column names in the `ALL_TAB_COLUMNS` table in Oracle Database:

| Column Name | Description |
|---|---|
| OWNER | The owner of the table. |
| TABLE_NAME | The name of the table. |
| COLUMN_NAME | The name of the column. |
| DATA_TYPE | The data type of the column. |
| DATA_LENGTH | The length of the column. |
| DATA_PRECISION | The precision of the column. |
| DATA_SCALE | The scale of the column. |
| NULLABLE | Whether the column can be null. |
| IDENTITY | Whether the column is an identity column. |
| VIRTUAL | Whether the column is a virtual column. |
| SEQUENCE_OWNER | The owner of the sequence that generates the values for the identity column, if applicable. |
| SEQUENCE_NAME | The name of the sequence that generates the values for the identity column, if applicable. |
| DEFAULT_VALUE | The default value for the column. |
| CONSTRAINT_NAME | The name of the constraint that enforces the default value for the column, if applicable. |
| COMMENTS | The comments for the column. |

The `ALL_TAB_COLUMNS` table is a read-only view that provides information about all of the columns in the database. This information can be useful for troubleshooting problems with the columns or for identifying security vulnerabilities.

To query the `ALL_TAB_COLUMNS` view, you can use the following SQL statement:

```sql
SELECT * FROM ALL_TAB_COLUMNS;
```

This will return all of the columns in the `ALL_TAB_COLUMNS` view.

> Remember to use `FROM dual` if you use `SELECT`

### Example

<a href="https://asciinema.org/a/lqu1jOLvj49NAUwN6Q0hQmIOq" target="_blank"><img src="https://asciinema.org/a/lqu1jOLvj49NAUwN6Q0hQmIOq.svg" /></a>

