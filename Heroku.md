Useful links:  
**setup**: http://sourabhbajaj.com/mac-setup/Heroku/README.html  
**posgres**: https://devcenter.heroku.com/articles/heroku-postgresql#pg-push-and-pg-pull  
**git deploy**: https://dashboard.heroku.com/apps/aqueous-spire-6633/deploy/heroku-git   
**pulling down database**: 


###Install Heroku
On OSX, use Homebrew:  
```
brew install heroku-toolbelt
heroku update
```

###Heroku Commands
  1. `heroku open` open a link to the app website in local browser
  2. `heroku ps` dynos running on Heroku
  3. `heroku logs` show log file for Heroku
  4. `heroku addons`
  5. `heroku local` run the app locally from heroku
  5. `heroku config` show configuration and the database url
  6. `heroku pg` for postgres commands
  

**Example Heroku website**
  11. `git clone https://github.com/heroku/ruby-getting-started.git` this example app
  2. `heroku create`
  3. `git push heroku master` deploy app to Heroku git
  4. `heroku open` open the website in browser

###Papertrail
```
heroku addons                   # show addons
heroku addons:doc papertrail    # documentation for papertrail
heroku addons:open papertrail   # open a dashboard for papertrail

heroku run bash                 # runs a remote shell
heroku run <command>            # runs a comandline command
heroku run bundle install
heroku run rake db:migrate

heroku config                   # show config settings
                                # database url is shown here
heroku config:set TIMES=10      # set TIMES env var to 10
```
###Postgres on Heroku  
NOTE: `DATABASE_URL` and `DATABASE` are the literal strings not sibstitutions  
```
heroku pg:info                      # show some info about the database

heroku pg:reset DATABASE_URL        # empties the database (DO NOT DELETE THE DATABASE, empty it using this)

heroku pg:credentials DATABASE      # shows the database credentials (username, password)

git push heroku test:master         # push 'test' branch to 'master' on heroku

heroku pg:push mylocaldb DATABASE_URL
heroku pg:push mylocaldb HEROKU_POSTGRESQL_MAGENTA --app sushi
 ```
###Accessing database remotely
Need to be made a Collaborator on the database, then:  
```
heroku pg:psql --app aqueous-spire-6633
```
