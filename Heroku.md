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
<b>heroku local</b> run the app locally from heroku

add <b>--app <em>APP</em></b> to specify non default Heroku <em>APP</em>  
<pre>
<b>heroku open</b> open a link to the app website in local browser
<b>heroku ps</b> dynos running on Heroku
<b>heroku config</b> show configuration vars and the database url
<b>heroku addons</b> show additional services

<b>heroku pg:psql</b> for [postgres on Heroku](#'accessing-database-remotely')

<b>heroku maintenance:on</b> take site down for maintenance
<b>heroku maintenance:off</b>

<b>heroku logs --app <em>APP</em></b> show log file for Heroku <em>APP</em>
<b>heroku restart --app <em>APP</em></b> restart <em>APP</em>

<b>heroku run console</b>
<b>heroku run bash --app <em>APP</em></b> remote Unix command line
</pre>
  

###Example Heroku website
<pre>
<b>git clone https://github.com/heroku/ruby-getting-started.git</b> get the example app
<b>heroku create</b> link to Heroku
<b>git push heroku master</b> <em>branch</em><b>:master</b> deploy app to Heroku git
<b>heroku open</b> open the website in a local browser
</pre>

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
NOTE: **DATABASE_URL** and **DATABASE** are the literal strings not env variables  
<pre>
<b>heroku pg:info</b>                      # show some info about the database

<b>heroku pg:reset DATABASE_URL</b>        # empties the database (DO NOT DELETE THE DATABASE, empty it using this)

<b>heroku pg:credentials DATABASE</b>      # shows the database credentials (username, password)

<b>git push heroku test:master</b>         # push 'test' branch to 'master' on heroku

<b>heroku pg:push</b> <em>mylocaldb</em> <b>DATABASE_URL</b>
heroku pg:push mylocaldb HEROKU_POSTGRESQL_MAGENTA --app sushi
</pre>

###To pull down a database:
<pre>
<b>heroku pg:pull</b>
<b>heroku pg:pull AMBER fff_development --app forever-family-foundation</b>
</pre>

<id='accessing-database-remotely'>
###Accessing database remotely
Need to be made a Collaborator on the database, then:  
<pre>
<b>heroku pg:psql --app</b> <em>\<appname\></em>  
heroku pg:psql --app aqueous-spire-6633
</pre>
**Records created since 1 month ago**  
<pre>
<b>SELECT * FROM</b> <em>table_name</em> <b>WHERE</b> <em>column_name</em> > <b>CURRENT_DATE - INTERVAL '1 month';</b>
</pre>
###Production Check  
On the **Heroku  Dashboard**, click on hamburger in upper right-hand corner, then click **Production Check**
