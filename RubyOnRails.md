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
**Install JSON**
```
gem install json --platform=ruby
```
**Check JSON installed correctly**
```
ruby -rubygems -e "require 'json';puts JSON.load('[42]').inspect"
```
**Install GEMs**
```
bundle install
```
**Migrate Database**
```
rake db:migrate
```

###Create New Application
```
cd C:\rails
rails new blog
cd blog
```
**Start Server**
```
rails server
```

Create controller
Create route

rails generate model <model name>  creates:
- db/migrate/
- app/views/<model name>


**Rail Types**
Here's a good set of definitions (from http://stackoverflow.com/a/15316528/2128691)

- binary - is for storing data such as images, audio, or movies.
- boolean - is for storing true or false values.
- date - store only the date
- datetime - store the date and time into a column.
- decimal - is for decimals.
- float - is for decimals. (What's the difference between decimal and float?)
- integer - is for whole numbers.
- primary_key - unique key that can uniquely identify each row in a table
- string - is for small data types such as a title. (Should you choose string or text?)
- text - is for longer pieces of textual data, such as a paragraph of information.
- time - is for time only
- timestamp - for storing date and time into a column.
- 

#Rails Commands

Generate Model vs Scaffolding
http://stackoverflow.com/questions/17734378/difference-between-scaffold-and-model-in-rails
```
rails generate model <modelname>
rails generate scaffold <name> <field:prop> <field:prop>
```


