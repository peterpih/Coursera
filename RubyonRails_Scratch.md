```
rails console
```
Should give `irb` prompt
```
**Find Tables In Database**
(from: http://stackoverflow.com/questions/24880956/rails-console-database-schema-checking)  
# list the tables in the database
ActiveRecord::Base.connection.tables
```
can also check the tables in db/schema.rb, to **recreate** db/schema.rb:
```
bundle exec rake db:schema:dump
```
