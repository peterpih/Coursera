###Gemfile.lock

Great explaination of Gemfile.lock: 
http://stackoverflow.com/questions/6927442/what-is-the-difference-between-gemfile-and-gemfile-lock-in-ruby-on-rails

Bascially,Gemfile.loc records the **exact** version used, Gemfile records preferences ie "~>"  

###Always version control Gemfile.lock

###Bundler
'''
bundle install                # install a gem in this scope (vs gem install <gem>
bundle install <gem>
bundle update                 # update gems and Gemfile.lock
bundle update <gem>
bundle update --source <gem>

bundle outdated
bundle outdated --strict
'''
