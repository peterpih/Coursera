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

###Installing Rails

downloads: http://rubyinstaller.org/downloads  

- Download Ruby2.2.exe  
- Run as Administrator to install  

**ERROR MSG: Could not find railties**  
Means the installation is faulty: http://stackoverflow.com/questions/9212116/rails-could-not-find-railties  
```
gem list              # list avaiable gems
get install rails     # will install other gems
```
cd C:\RubyDevKit
```
downloads: http://rubyinstaller.org/downloads  
instructions: http://github.com/oneclick/rubyinstaller/wiki/Development-Kit  

###Instant Gratification
Create a new directory **demo**
```
cd work
rails new demo  # creates all necessary directories
```
Examin the installation:  
```
rake about
```

