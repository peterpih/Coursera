###If connection times out, may be due to firewall  
Run `ssh -T git@github.com`, if it times out, need to connect using `http:` protocol.  

###Useful links
[gitref.org](http://gitref.org)  
[Git Basics Getting a Git Repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)  
[git-scm.com docs](https://git-scm.com/docs)  
[Git Fetch and Merge](http://longair.net/blog/2009/04/16/git-fetch-and-merge/)  
[How to update a GitHub forked repository](http://stackoverflow.com/questions/7244321/how-to-update-a-github-forked-repository)   
[Git Branching - Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)  
[Git Guide](http://rogerdudler.github.io/git-guide/)  
[Git Reference](http://gitref.org/remotes/)

###Some Thoughts:
Think of **origin** not as where the code is now, but where it came from ie the **origin** of a river

#TOC
[Typical Work Flow](#work-flow-section)  
[File Commands](#file-section)  
[Repo and Branch Commands](#repo-branch-section)  
[Rename Local and Remote Branches](#rename=local-remote-branches-section)
[Where Is Current Origin?](#where-is-current-origin-section)  
[GitHub](#github-section)  
[gh-pages](#gh-pages-how-to-section)  

<div id="work-flow-section">
###Typical git command flow
<pre>
<b>git checkout</b> <em>feature_branch</em>        # change branch to feature_branch
...
<b>git status</b>                         # shows status of branch
<b>git add -A</b>                         # add modified and untracked files to staging area
<b>git commit -m</b> <em>comment</em>              # make a commit, comment on one line

--- SHOW ---

<b>git show HEAD</b>

--- PUSHING ----

<b>git push</b> <em>origin feature_branch</em>          # push the commits from feature_branch to remote origin
<b>git push -f</b> <em>origin feature_branch</em>       # force push to origin

                                        #push directly to Heroku
<b>git push heroku</b> <em>feature_branch:master</em>   # push to master branch on heroku to start install
</pre>

While on feature_branch, when ready to push to master branch, check for conflicts:  
<pre>
<b>git checkout</b> <em>branch</em>           # on to feature branch
<b>git merge master</b>              # merge from master to check for conflicts
...                           # resolve any conflicts if necessary
<b>git checkout master</b>           # change back to master
<b>git merge</b> <em>branch</em>              # there will be no comflicts at this point
</pre>

[making a pull request](https://www.atlassian.com/git/tutorials/making-a-pull-request/example)  example  
We use the <b>Fork Workflow</b> method  

<div id="file-section">
###File commands
<pre>
--- ADD --- <em>to staging</em>

<b>git add</b> <em>file-name</em>              # add a file to staging area
<b>git add</b> <em>file1, file2, file3</em>   # add multiple files to staging area
<b>git add .</b>                     # add <b>modified only</b> files to staging area
<b>git add -A</b>                    # add <b>modified and untracked</b> files to staging area

--- RESET ---

<b>git reset</b>                     # remove all files from staging area, before commit(ting)
<b>git reset</b> <em>file-name</em>            # remove filename from staging area
<b>git reset</b> <em>revhash</em>             # roll back to revhash commit

--- COMMIT ---

<b>git commit -m</b> <em>commit_text</em>     # one line commit comment
<b>git commit</b>                    # will open text editor for commenting

--- MERGE ---

<b>git merge</b> <em>branch_to_merge</em>

--- REMOVE (delete) --- <em>from staging, files must be staged</em>

<b>git rm -f</b> <em>filename</em>            # delete file and/or remove tracked deleted files from staging
<b>git rm --cached</b> <em>filename</em>      # remove from staging area (does not delete underlying file)
                              # in case accidentally added
<b>git reset</b> <em>filename</em>

--- CHECKOUT --- <em>go back to version at last commit</em>

<b>git checkout</b> <em>filename</em>        # restore previous file version from last commit
<b>git checkout HEAD</b> <em>filename</em>

<b>git checkout</b> <em>branch</em>          # switch to <em>branch</em>

--- SHOW ---

<b>git show</b> <em>revhash</em>            # show changes in a particular hash (hash from git log)
<b>git show</b> <em>revhash:filename</em>  

--- DIFFERENCE ---

<b>git diff</b>
<b>git diff --staged</b>
<b>git diff</b> <em>file-name</em>           # show difference between modified and staging area

--- RENAME --- <em>a file</em>

<b>git mv</b> <em>from-file  to-file</em>

--- LOG --- <em>show changes between two different branches</em>

<b>git log</b>
<b>git log -p</b>                    # difference between the last two commits
<b>git log -p -2</b>                 # last 2 lines
<b>git log --one-line</b>            # show each commit on one line
<b>git log --stat</b>
<b>git log --pretty=oneline</b>       #single line summary
<b>git log --pretty=format:"%h - %an, %ar : %s"</b>
<b>git log --since=2.weeks</b>
<b>git log -S</b><em>function_name</em>     # search logs for string <function name>
<b>git log --graph --oneline --decorate --all</b>       # makes a graph of the branches
</pre>

<div id="repo-branch-section">
###For Repositories and Branches
<pre>
<b>cd</b> <em>working-directory</em>
<b>git init</b>                      # initialize an existing local working_directory

<b>git init</b> <em>working-directory</em>  # initialize and create a local working_directory


--- <b>STATUS</b> --- <em>show status of files in working tree</em>

<b>git status</b>                    # tracked, untracked, modified, staged
<b>git status -s</b>                 # short form: M-modified, A-staged(added), ??-untracked

--- CLONE ---

<b>git clone</b> <em>remote-name</em> <em>local-directory</em>

#---BRANCH---

<b>git branch -l</b>               # show local branches
<b>git branch -a</b>               # show all branches, local and remote
<b>git branch -d</b> <em>branch</em>        # delete a <branch>
<b>git branch -D</b> <em>branch</em>        # forcefully delete <branch>
<b>git branch -m</b> <em>current-name new-name</em>

#---SHOW-BRANCH---     
<a href="https://robots.thoughtbot.com/compare-commits-between-git-branches">compare commits between git branches</a>
<b>git show-branch</b> <em>branch</em> <b>origin/master</b>

#---REMOTE---

<b>git remote -v</b>                 # list remote repos

                              # add remote repo connections
<b>git remote add</b> <em>origin</em> <b>git@github.com:</b><em>user-name</em><b>/</b><em>repo-name</em>
<b>git remote add</b> <em>origin</em> <b>https://github.com/</b><em>user-name</em><b>/</b><em>repo-name</em>

<b>git remote rm</b> <em>origin</em>          # remove remote connection

<b>git remote add</b> <em>fff</em> <b>git@github.com:</b><em>user-name</em><b>/</b><em>githhub-reponame</em>
<b>git fetch</b> <em>fff</em>
<b>git pull</b>

#---CHECKOUT--- <em>switch branches</em>

<b>git checkout</b> <em>master</em>                 # switch branches
<b>git checkout -b</b> <em>my-branch-name</em>      # do checkout and create new branch
<b>git checkout</b> <em>revhash file</em>           # restore a file from commit tag ####### (seven digits)

#---RESET--- reset a branch

<b>git reset</b>                       # unstage any staged files
<b>git reset --hard HEAD^</b>          # resets current branch to last commit and removes last commit from history
<b>git reset --hard HEAD~2</b>         # resets last 2 commits
<b>git reset --hard fff/master</b>

#--- <a href="https://git-scm.com/book/en/v1/Git-Tools-Stashing"><b>STASH</b></a> --- <em>push a branch onto a saved stack</em>

<b>git stash</b>                       # creates a stash  
<b>git stash save</b>  
<b>git stash save</b> <em>description</em>  

<b>git stash apply</b>                 # apply most recent stash
<b>git stash apply stash@{2}</b>       # apply second stash

<b>git stash list</b>                  # lists stashes  

<b>git stash drop stash@{0}</b>        # delete first stash
<b>git stash drop stash@{1}</b>        # delete second stash

</pre>
###[Updating local master from origin master](http://stackoverflow.com/questions/501407/is-there-a-git-merge-dry-run-option)
<pre>
<b>cd</b> <em>local-repo</em>
<b>git checkout master</b>

<b>git fetch</b> <em>repo-name</em> <b>master</b>   <em>( repo-name usually origin or phran )</em>
<b>git merge-base FETCH_HEAD master</b>
<b>git merge-tree</b> <em>mergebase</em> <b>master FETCH_HEAD</b>
      <em>( where mergebase is the hexcidecimal id merge-base printed in previous step )</em>
      <em>( search for <b><<</b> or <b>>></b> for conflicts )*</em>
</pre>

###Initializing Repository from PC

goto directory above where you want the project
<pre>
<b>git new</b> <em>project-name</em>
<b>cd</b> <em>project-name</em>
                    # with a preexisting directory, start here
<b>git init</b>            # initialize
</pre>

At this point, the \<project name\> repository needs to be created on GiutHub  
Set the upstream name
Then **fetch** from the GitHub to get the README.md file
<pre>
<b>git status</b>                    # have a look
<b>git add -A</b>                    # add all files
<b>git commit -m</b> <em>"first commit"</em>
<b>git pull https://github.com/</b><em>username</em><b>/</b><em>project name</em><b>.git</b>
git push --set-upstream https://github.com/<username>/<project name>.git master
</pre>
<div id="where-is-current-origin-section">
###Change Origin Repository
from: http://blog.aplikacja.info/2010/08/switch-origin-of-your-git-repository/  

Where is the current **origin**  
<pre>
  <b>git remote -v</b>
      origin	git@github.com:phran/forever-family-foundation.git (fetch)
      origin	git@github.com:phran/forever-family-foundation.git (push)

  <b>git remote rm origin</b>
  <b>git remote -v</b>
  <b>git remote add origin git@github.com:peterpih/forever-family-foundation</b>
  <b>git remote -v</b>
      origin	git@github.com:peterpih/forever-family-foundation (fetch)
      origin	git@github.com:peterpih/forever-family-foundation (push)

  <b>git config master.remote origin</b>
  <b>git config master.merge refs/heads/master</b>
  <b>git status</b>

  <em>then either</em>
  <b>git push --set-upstream origin master</b>
      -or-
  <b>git push --set-upstream origin master -force</b>
</pre>

<div id="rename-local-remote-branches-section">
###Rename local and remote branches  
from: https://gist.github.com/lttlrck/9628955  
<pre>
git branch -m old_branch new_branch         # Rename branch locally    
git push origin :old_branch                 # Delete the old branch    
git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote
</pre>

[gh-pages How To](#gh-pages-how-to)

useful link: 
[Basic Git Command Line Reference for Windows Users](http://www.codeproject.com/Articles/457305/Basic-Git-Command-Line-Reference-for-Windows-Users)  
useful video: http://www.git-tower.com/learn/git/videos/installing-configuring-git?channel=cli#start  
branching and merging:  
[Merging A Pull Request](https://help.github.com/articles/merging-a-pull-request/)  
[Create A New Branch And Merge Branches](https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches)  

git and poshgit (has credentials link): https://gist.github.com/pcurylo/6575385  
<pre>
<b>git</b> <em>parameter</em> <b>--help</b>
</pre>
###GitHub Flow
Useful link: https://guides.github.com/introduction/flow/  

GitHub staging:
- **Create a branch**
  - When you're working on a project, you're going to have a bunch of different features or ideas in progress at any given time – some of which are ready to go, and others which are not. Branching exists to help you manage this workflow. When you create a branch in your project, you're creating an environment where you can try out new ideas. Changes you make on a branch don't affect the master branch, so you're free to experiment and commit changes, safe in the knowledge that your branch won't be merged until it's ready to be reviewed by someone you're collaborating with.
- **Add commits**
  - Once your branch has been created, it's time to start making changes. Whenever you add, edit, or delete a file, you're making a commit, and adding them to your branch. This process of adding commits keeps track of your progress as you work on a feature branch. Commits also create a transparent history of your work that others can follow to understand what you've done and why. Each commit has an associated commit message, which is a description explaining why a particular change was made. Furthermore, each commit is considered a separate unit of change. This lets you roll back changes if a bug is found, or if you decide to head in a different direction.
  - closing issues via commit messgaes: https://help.github.com/articles/closing-issues-via-commit-messages/
- **Open a pull request**
  - Pull Requests initiate discussion about your commits. Because they're tightly integrated with the underlying Git repository, anyone can see exactly what changes would be merged if they accept your request. You can open a Pull Request at any point during the development process: when you have little or no code but want to share some screenshots or general ideas, when you're stuck and need help or advice, or when you're ready for someone to review your work. By using GitHub's @mention system in your Pull Request message, you can ask for feedback from specific people or teams, whether they're down the hall or ten time zones away.
- **Discuss and review your code**
  - Once a Pull Request has been opened, the person or team reviewing your changes may have questions or comments. Perhaps the coding style doesn't match project guidelines, the change is missing unit tests, or maybe everything looks great and props are in order. Pull Requests are designed to encourage and capture this type of conversation. You can also continue to push to your branch in light of discussion and feedback about your commits. If someone comments that you forgot to do something or if there is a bug in the code, you can fix it in your branch and push up the change. GitHub will show your new commits and any additional feedback you may receive in the unified Pull Request view.
- **Deploy**
  - Once your pull request has been reviewed and the branch passes your tests, you can deploy your changes to verify them in production. If your branch causes issues, you can roll it back by deploying the existing master into production.
- **Merge**
  - Now that your changes have been verified in production, it is time to merge your code into the master branch. Once merged, Pull Requests preserve a record of the historical changes to your code. Because they're searchable, they let anyone go back in time to understand why and how a decision was made.


##Git Bash Commands &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[link to Git commands](#github-section)
**Clone a local repository using Git on PC**
<pre>
<em>First create the repository in GitHub</em>
<b>cd</b> <em>directory_you_want_the_repository_to_be_in</em>
<b>git clone https://github.com/peterpih/</b><em>repository name</em>
</pre>
alternatively you can do this on PC (these steps will aso create a README.md file):
<pre>
<b>cd</b> <em>directory</em>
<b>echo</b> <em>"# 09_DevelopingDataProducts >> README.md"</em>
<b>git init</b>
<b>git add README.md</b>
<b>git commit -m</b> <em>"first commit"</em>
<b>git remote add origin https://github.com/peterpih/09_DevelopingDataProducts.git</b>
<b>git push -u origin master</b>
<pre>

**Change the name of a directory(branch)**
<pre>
<b>rm --ignore-fail-on-non-empty .git</b>
<b>git init</b>
<b>git remote add origin https://github.com/peterpih/09_DevelopingDataProducts.git</b>
<b>git push -u origin master</b>
</pre>

**delete the **.git** file in the PC directory**

### Push files back to repository
- **git status**
- **git add**
  + **git reset** will reset any **add**ed files before **commit**
- **git commit**
  + **git pull** for updates if necessary first
- **git push**
```{R}
$ git status (will tell you the status of the files: new, modified, deleted hilited in red
$ git add <file name>  or git add -A (for everything)
$ git status (will  hilite the added files in green which need to be committed)
$ git commit -m <message for commiting>
$ git status (message will say "use git push to commit your changes")
$ git push
```
If the **push is rejected**, it is because there have been other updates to the branch on GitHub  
You will need to **git pull** first so changes are merged, and the **git push**  
<pre>
$ <b>git pull</b>
$ <b>git status</b>
$ <b>git push</b>
</pre>
<pre>
<b>git diff</b> <em>file-name</em>
<b>git difftool</b> <em>file-name</em>

<b>git add</b> <em>file-name</em>               # add a new file to the repository to be tracked
<b>git rm</b> <em>file-name</em>                # delete a file

<b>git log</b>                          # shows history
<b>git log --stat</b>                   # show which files were changed
<b>git log --p</b>                      # shows the changes

<b>.git/info/exclude</b>                # ignore file for only local repository
</pre>
At any one time, only one branch is currently active, this is the **checked out** branch, or **HEAD** branch  
Move from one branch to another using **checkout**  

###Restore a previous file version
http://schacon.github.io/git/git-checkout.html  


<div id='github-section'>
#Github Commands

### Create a repository on GitHub

- Select **Repositories** tab
- Click **New** (upper right hand corner)
- Enter **Repository name**
- Enter **Description** of repository
- Select **Public**
- Select **initialize repository with a README**
- Click **Create repository**

After the repository is created, click the **+** after the repository name to create a file

- Enter **.gitignore**
- Click **Commit**

### Delete a repository on Github
- Click on **repository name**
- Click on **Settings** icon (right hand column)
- Click on **Delete Repository** at bottom of page

<div id='gh-pages-how-to-section'>
###gh-pages in GitHub  

**github.io url generator**: http://drastudio.github.io/url-generator/  

The project submission instructions suggest that you can make it easier for reviewers to see your finished html output by setting up a "gh-pages" branch in your Github repository.  That will automatically create a web site for the repo on github.io, with your html page properly displayed.  

Note this is entirely *optional* -- the reviewer can download or clone your repo, and open your html page locally in their browser.  So, if it's optional, why do it?  Several reasons:  First, it is easier for the reviewer just to click a link and see your html page.  Second, hosting web sites on github.io is increasingly popular, and it might be useful for other projects.  Third:  Free web site.  Let me repeat:  Free web site.  No hosting fees.  Fourth:  Your free web site is under revision control on github.com, so backup is not a problem.  

The setup for a gh-pages site for this project is actually simple.  If you look at the assorted videos and posts about it, or even Github's own instructions, they will be (much) more complex than you need.  That is because our case is very simple -- we just want everything in the repo to be made available on github.io.  The more complex case that most videos / posts are describing is when you want to have a special "about this project" web site, that doesn't just include the entire repo.  

The short version of this how-to is:  

1) In your project repository, create a gh-pages branch that is just the same as the master branch.  
2) Push the gh-pages branch to Github.  
3) Wait about 5 minutes.  Poof!  Your web site is available on github.io!  

So...follow on below for the "detailed" instructions, broken up into pieces:  

1) How to make your gh-pages branch...  
    a) using git commands in your local repo.  
    b) right on Github itself.  
2) How to maintain the gh-pages branch if you make changes to your project after creating the branch.  

Plus some "extras":  

3) A few other files you can provide to help people find things in your repo and github.io site.  
4) Some notes on git, Github, and revision control.  

***Another way using git***  
Push html pages to master branch  
<pre>
<b>git push</b> <em>origin</em> <b>master</b>
</pre>

###Now create a gh-pages branch (GitHub-pages)
<pre>
<b>git branch gh-pages</b>
<b>git checkout gh-pages</b>
<b>git push origin gh-pages</b>
</pre>

This will create a gh-pages branch on github  
Also, create and push a .nojekyll file which avoids some of the fancy html in github
<pre>
<b>touch .nojekyll</b>
<b>git add .nojekyll</b>
<b>git commit -m</b> <em>"adding .nojekyll"</em>
<b>git push origin gh-pages</b>
</pre>

**To view the webpage, the url is**:  
<b>http://</b><em>github-username</em><b>.github.io/</b><em>repo-name</em><b>/</b><em>presentation-name</em><b>.html</b>  

**To keep the master and gh-pages branches in sync**:  
[Automating gh pages integration](http://concord-consortium.github.io/developer-notes/automating-gh-pages-integration.html)  


###Authorization to see repo characterisitics (from quiz excercise)  
```
library(httr)
oauth_endpoints("github")
myapp <- oauth_app("github", "448a5d91fcf0aa2e656a")

github_token <- oauth2.0_token(oauth_endpoints("github"), myapp)
gtoken <- config(token = github_token)
req <- GET("https://api.github.com/users/jtleek/repos", config(token = github_token))
stop_for_status(req)
json1 = content(req)
json1[[5]]$created_at

download.file("https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv", "ss06hid.csv")
data <- read.csv("ss06hid.csv")
```
