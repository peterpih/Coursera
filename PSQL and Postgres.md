For **rake db:migrate** commands to **up** or **down** a database look  
[RubyOnRails Rake](https://github.com/peterpih/Miscellaneous/blob/master/RubyOnRails%20Rake.md)

[PostgreSQL](http://www.postgresql.org/docs/9.1/static/sql-altertable.html) documentation

Useful graph of SQL joins: [difference between join and inner join](http://stackoverflow.com/questions/565620/difference-between-join-and-inner-join  )
#PSQL commands
**Show databases***
<pre>
<b>\l</b>                        # list databases letter el

<b>\c</b> <em>database</em>               # connect to a database
<b>\c</b> fff_development

<b>\d</b>                        # list tables
<b>\d+</b> <em>table-name</em>            # list columns of a table
</pre>

###SQL commands
<pre>
<b>SELECT</b> * <b>FROM</b> <em>table</em><b>;</b>                                    # select all rows

<b>UPDATE</b> <em>table</em> <b>SET</b> <em>column=value</em> <b>WHERE</b> <em>id=userid</em><b>;</b>

<b>DELETE</b> <b>FROM</b> <em>table</em> <b>WHERE</b> <em>=userid</em><b>;</b>                        # clear all rows from a table

<b>SELECT</b> * <b>FROM</b> <em>users</em> <b>WHERE</b> <em>email</em> <b>LIKE</b> <em>'ppih@panix%'</em><b>;</b>     # '%' is the wildcard
<b>SELECT</b> * <b>FROM</b> <em>users</em> <b>WHERE</b> <em>email='ppih@panix%'</em><b>;</b>  

<b>ALTER TABLE</b> <em>table-name</em> <b>RENAME TO</b> <em>new-table-name</em>;  <em>( rename a table )</em>
<b>ALTER TABLE</b> <em>table-name</em> <b>RENAME</b> <em>column-name</em> <b>TO</b> <em>new-column-name<em>;
</pre>
