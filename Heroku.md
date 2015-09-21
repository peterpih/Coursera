**Useful setup link**: http://sourabhbajaj.com/mac-setup/Heroku/README.html  

###Install Heroku
On OSX, use Homebrew:  
```
brew install heroku-toolbelt
heroku update
```

###Heroku Commands
1) `heroku open` open a link to the app website
2) `heroku ps` dynos running on Heroku
3) `heroku logs` log file for Heroku

**Example Heroku website**
1) `git clone https://github.com/heroku/ruby-getting-started.git` this example app
2) `heroku create`
3) `git push heroku master` deploy app to Heroku git
4) `heroku open` open the website in browser

