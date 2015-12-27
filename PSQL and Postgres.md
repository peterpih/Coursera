Useful graph of SQL joins:  
http://stackoverflow.com/questions/565620/difference-between-join-and-inner-join  
#PSQL commands
**Show databases***
<pre>
<b>\l</b>                  # list databases letter el
<b>\c</b> <em>database</em>         # connect to a database
<b>\d+</b> <em>table</em>           # list columns of a table
</pre>

###SQL commands
<pre>
<b>SELECT</b> * <b>FROM</b> <em>table</em><b>;</b>                                    # select all rows

<b>UPDATE</b> <em>table</em> <b>SET</b> <em>column=value</em> <b>WHERE</b> <em>id=userid</em><b>;</b>

<b>DELETE</b> <b>FROM</b> <em>table</em> <b>WHERE</b> <em>=userid</em><b>;</b>                        # clear all rows from a table

<b>SELECT</b> * <b>FROM</b> <em>users</em> <b>WHERE</b> <em>email</em> <b>LIKE</b> <em>'ppih@panix%'</em><b>;</b>     # '%' is the wildcard
<b>SELECT</b> * <b>FROM</b> <em>users</em> <b>WHERE</b> <em>email='ppih@panix%'</em><b>;</b>  
</pre>
