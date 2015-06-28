#Installing Ruby On Rails on Windows 8.1

###Install Ruby
```
http://rubyinstaller.org/downloads/
```
Be sure to check the comments and install the most recent **stable** version
**NB: currently not using 64-bit**
This video was also generally helpful: https://www.youtube.com/watch?v=j8UsSmSgVt8

**Check Ruby has been installed correctly**
```
Ruby -v
```

> At this point I tried to run **rails server** but got an error message to install DevKit


###Install DevKit
for downloads: http://rubyinstaller.org/downloads/

**read instructions thuroughly**
instructions: https://github.com/oneclick/rubyinstaller/wiki/Development-Kit
```
mkdir C:\RubyDevKit   # install to a permanent directory
cd C:\RubyDevKit
ruby dk.rb install
```
**Install JSON***
```
gem install json --platform=ruby
```
**Check JSON installed correctly
```
ruby -rubygems -e "require 'json';puts JSON.load('[42]').inspect"
```
**Install GEMs**
```
bundle install
```
**Create New Application**
```
cd C:\rails
rails new blog
cd blog
```
**Start Server**
```
rails server
```
