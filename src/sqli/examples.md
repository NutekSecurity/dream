# Simple examples

## SQLi that show hidden data

Append `' -- ` or `' OR 1=1 -- ` to the url to show what the website is hiding from you

<a href="https://asciinema.org/a/ZZcn5kbcJqUOh5uFEs9v0EHPU" target="_blank"><img src="https://asciinema.org/a/ZZcn5kbcJqUOh5uFEs9v0EHPU.svg" /></a>

The goal here is to generate SQL statement like this one:

```sql
SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1
```

_Portswigger_ warns about using this type of SQLi - 

> Take care when injecting the condition OR 1=1 into a SQL query. Although this may be harmless in the initial context you're injecting into, it's common for applications to use data from a single request in multiple different queries. If your condition reaches an UPDATE or DELETE statement, for example, this can result in an accidental loss of data.

## SQLi that uses login form

We want to get into application as an `administrator` user. To accomplish that
we need to execute this SQL query.

```sql
SELECT * FROM users WHERE username = 'administrator'--' AND password = ''
```

<a href="https://asciinema.org/a/uLlC06h13BsD3Tp0owMxFO2I2" target="_blank"><img src="https://asciinema.org/a/uLlC06h13BsD3Tp0owMxFO2I2.svg" /></a>

To do this we input in login form

```sql
administrator'--
```

and some password (it's irrelevant, but might be neccessairly).

For this to work we use `mitmproxy` and intercept `login` flow, where we alter
the input data and resume it by pressing `a` (I needed to press it twice).

For this example it might even work using just the browser.