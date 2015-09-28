###Class names in Rails must be Capitalized  

#TOC
[Installing PostGrSQL on Mac](#postgres-section)

Useful link: http://guides.rubyonrails.org/getting_started.html  

<div id="postgres-section">
###Installing PostGreSQL on Mac
Has instruction on starting server:  
http://www.gotealeaf.com/blog/how-to-install-postgresql-on-a-mac  

Generic database.yml
```
# SQLite version 3.x
#   gem install sqlite3
#
#   Ensure the SQLite 3 gem is defined in your Gemfile
#   gem 'sqlite3'
#
# Changed to PostGreSQL for FFF
#
default: &default
  adapter: postgresql
  host: localhost
  pool: 5
  timeout: 5000

development:
  <<: *default
  database: fff_development

# Warning: The database defined as "test" will be erased and
# re-generated from your development database when you run "rake".
# Do not set this db to the same as development or production.
test:
  <<: *default
  database: fff_test

production:
  <<: *default
  database: fff_production
```
And then `rake db:create db:migrate`

