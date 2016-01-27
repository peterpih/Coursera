[Ruby Upgrade](https://github.com/rbenv/rbenv/issues/285)
<pre>
ruby --version            # show the ruby version  

rbenv versions            # shows the versions of ruby available  

rbenv install 2.2.4       # install specific version  
                          # if not available try upgrading ruby-build  

brew upgrade ruby-build   # upgrade

rbenv install 2.2.4       # install specific version

rbenv global 2.2.4        # set default version number
</pre>
<pre>
Had a problem that `rbenv` could not see `bundle`  
Ran `bundle` from ~/rbenv/versions/.../bin and it was fixed
</pre>
