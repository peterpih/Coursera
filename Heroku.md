Useful **setup** link: http://sourabhbajaj.com/mac-setup/Heroku/README.html  
Useful **posgres** link: https://devcenter.heroku.com/articles/heroku-postgresql#pg-push-and-pg-pull  

###Install Heroku
On OSX, use Homebrew:  
```
brew install heroku-toolbelt
heroku update
```

###Heroku Commands
  1. `heroku open` open a link to the app website
  2. `heroku ps` dynos running on Heroku
  3. `heroku logs` log file for Heroku
  4. `heroku addons`
  5. `heroku config` show configuration and the database url
  6. `heroku pg` for postgres commands
  

**Example Heroku website**
  11. `git clone https://github.com/heroku/ruby-getting-started.git` this example app
  2. `heroku create`
  3. `git push heroku master` deploy app to Heroku git
  4. `heroku open` open the website in browser

