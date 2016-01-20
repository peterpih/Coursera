###Gemfile.lock

Great explaination of Gemfile.lock: 
http://stackoverflow.com/questions/6927442/what-is-the-difference-between-gemfile-and-gemfile-lock-in-ruby-on-rails

<b>Gemfile.lock</b> records the **exact** version used  
Gemfile records preferences ie "~>"  

###Always version control Gemfile.lock

###Bundler
<pre>
<b>bundle install</b>                # install a gem in this scope
<b>bundle install</b> <em>gem</em>
<br>
<b>bundle update</b>                 # update gems and Gemfile.lock
<b>bundle update</b> <em>gem</em>
<b>bundle update --source</b> <em>gem</em>
<br>
<b>bundle outdated</b>              # show which gems are outdated
<b>bundle outdated --strict</b>

