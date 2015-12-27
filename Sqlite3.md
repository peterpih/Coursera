###Sqlite3 installed in C:/Windows
**Useful links:**

http://zetcode.com/db/sqlite/datamanipulation/

To get the version:
```
$ sqlite3 -version
```

- history file: **.sql_history**
- resource file: **.sqliterc**

###Sqlite3 command summary below
useful link: http://zetcode.com/db/sqlite/tool/

```
# show tables
.tables

# delete table
drop table <tablename>

# show schema for a table
.schema <table>

# show records in a table
SELECT * from <table>
```

###Sqlite3 commands
**All command lines end in ";"**
```
SELECT <*|field,field> from <table>;
DROP TABLE <table>
```
**Meta Commands *(settings)* begin with "."**
- .show *(shows settings)*
- .mode column
- .headers \<on|off\>
- .separator \<delimiter\>

###From the command line
```

$ sqlite3 -html test.db
```

