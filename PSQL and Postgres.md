#PSQL commands
**Show databases***
```
\l                  # list databases letter el
\c <database>       # connect to a database
\d+ <table>         # list columns of a table
```

###SQL commands
```
SELECT * FROM <table>;                                  # select all rows

UPDATE <table> SET <column>=<value> WHERE id=<userid>;

DELETE FROM <table>;                                    # clear all rows from a table

SELECT * FROM users WHERE email ILIKE 'ppih@panix%';    # '%' is the wildcard
```
