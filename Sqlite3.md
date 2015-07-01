###Sqlite3 installed in C:/Windows

###Sqlite3 command summary below
useful link: http://zetcode.com/db/sqlite/tool/

```
# show tables
.tables

# show schema for a table
.schema <table>

# show records in a table
SELECT * from <table>
```

###Sqlite3 commands
**All command lines end in ";"**
```
SELECT <*|field,field> from <table>
```
**Settings begin with "."**
- .show *(shows settings)*
- .mode column
- .headers \<on|off\>
- .separator \<delimiter\>

