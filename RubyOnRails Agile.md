Notes from **Agile Web Development with Rails 4**  

**MVC** - Model-View-Controller architecture  
**DRY** - Don't Repeat Yourself  

Rails is **Agile**:
- Individuals and interactions over processes and tools
- Working software over comprehensive documentation
- Customer collaboration over contract negoatiation
- Respnding to change over following  plan
http://agilemanifesto.org  

Useful links:  
http://formus.pragprog.com/forums/148  
http://www.praprog.com/titles/rails4/errata  
http://eee.pragprog.com/wikis.RailsPlayTime  

###Install Ruby

YouTube video: https://www.youtube.com/watch?v=sWP3Nit8kEg

downloads: http://rubyinstaller.org/downloads  

- Download Ruby2.2.exe  
- Run as Administrator to install  

To test Ruby installation:  
```
ruby -e puts 1+1  # command line run as ruby
```

Ruby also deploys with **IRB**, interactive Ruby

```
irb
```

**ERROR MSG: Could not find railties**  
Means the installation is faulty: http://stackoverflow.com/questions/9212116/rails-could-not-find-railties  
```
gem list              # list avaiable gems
gem install rails     # will install other gems
```

**pessimistic lock**: https://robots.thoughtbot.com/rubys-pessimistic-operator  
**bundler** best practices: https://github.com/thoughtbot/guides/tree/master/best-practices#bundler  


###Install DevKit  

GitHub info: https://github.com/oneclick/rubyinstaller/wiki/development-kit  
Install into C:/DevKit  
Useful info: http://rubyinstaller.org/add-ons/devkit/  
```
cd C:\DevKit                        # directory where Dev Kit is installed
ruby dk.rb init
ruby dk.rb install
gem install json --platform=ruby    # JSON should install correctly and you should see with native extensions
                                    # in the screen messages
                                    
ruby -rubygems -e "require 'json'; puts JSON.load('[42]').inspect"  #  to confirm that the json gem is working.
```
Now test installation from GitHub documentation  


cd C:\RubyDevKit

downloads: http://rubyinstaller.org/downloads  
instructions: http://github.com/oneclick/rubyinstaller/wiki/Development-Kit  

###Install RubyGems

Main website: www.rubygems.org  
```
gem -v                    # checks installed version
gem update --system       # check for updates
gem --help                # for help
gem list                  # list of gems currently installed
```


##Install Rails
Rails is a Gem  
Find the latest version of Rails on www.rubygems.org  
To install:  
```
gem install rails --version=4.2.4 --no-ri --no-rdoc
```
--no-ri and --no-rdoc means do not install documentation (which can still be found on-line)  
```
rails -v                   # show version number of rails
```

###Install MySQL
3 Steps to install MySQL:
1) Download and install MySQL
  - developer website: http://dev.mysql.com
2) Default MySQL password
3) Install MySQL RubyGem

**Download MySQL*** 
On the dev.mysql.com websote, find the Community Server download page  
Find the MSI Installer download  
Find the "No thanks, just install" choice at the bottom  
The installer will check for any necessary updates  
Choose the **Developer Default** since only developing on local machine  

After installation, you can find the MySQL command line under Programs|MySQL  
**It is not necessary to add MySQL to PATH**  

**Add MySQL RubyGem**

###Text Editor
- Color coding, syntax highlighting
  - Ruby, Rails, HTML, CSS, JavaScript
- Easily navigate a while project
  - Project widowws, open tabs, etc
- Good search and replace
- Auto-paring of parenthesis, brackets, and quotes
- Auto-indent
- Code completion
- Customize document and code coloring (themes)


###Instant Gratification
Create a new directory **demo**
```
cd work
rails new demo  # creates all necessary directories
```
Examine the installation:  
```
rake about
```


