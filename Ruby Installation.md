[Ruby Upgrade](https://github.com/rbenv/rbenv/issues/285)
<pre>
<b>ruby --version</b>            # show the ruby version  

<b>rbenv versions</b>            # shows the versions of ruby available  

<b>rbenv install</b> <em>2.2.4</em>       # install specific version  
                          # if not available try upgrading ruby-build  

<b>brew upgrade ruby-build</b>   # upgrade

<b>rbenv install</b> <em>2.2.4</em>       # install specific version

<b>rbenv global</b> <em>2.2.4</em>        # set default version number
</pre>
<pre>
Had a problem that `rbenv` could not see `bundle`  
Ran `bundle` from ~/rbenv/versions/.../bin and it was fixed
</pre>
