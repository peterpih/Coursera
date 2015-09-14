```
rails console
```
Should give `irb` prompt

**Find Tables In Database**  
(from: http://stackoverflow.com/questions/24880956/rails-console-database-schema-checking)  
```
# list the tables in the database
ActiveRecord::Base.connection.tables
```
can also check the tables in db/schema.rb, to **recreate** db/schema.rb:
```
bundle exec rake db:schema:dump
```
***table_print**
- add **table_print** to Gemfile
- bundle install

In `rails console` type "tp" to see it's installed, or
```
show data_directory;
```

###Postgres
**start server**  
http://www.postgresql.org/docs/9.1/static/server-start.html  
```
postgres -D /usr/local/pgsql/data
```

**dump restore**  
http://www.postgresql.org/docs/9.4/static/backup-dump.html  
```
pg_dump <databasename> > <txtdumpfile>

psql <databasename> < <txtdumpfile>
```
psql will not create a data base, to **create** a database:
```
createdb -T template0 <databasename>
```
To **DELETE** a database:
```
rails dbconsole
\c <adifferent database>    # connect to a diferent database
DROP DATABASE <databasename>
```
