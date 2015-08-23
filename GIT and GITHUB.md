[gh-pages How To](#gh-pages-how-to)

useful link: 
http://www.codeproject.com/Articles/457305/Basic-Git-Command-Line-Reference-for-Windows-Users
  
  

##Git Bash Commands &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[link to Git commands](#github-section)
**Clone a local repository using Git on PC**
```{R}
# First create the repository in GitHub
$ cd <directory you want the repository to be in>
$ git clone https://github.com/peterpih/<repository name>
```
alternatively you can do this on PC (these steps will aso create a README.md file):
```{R}
# cd <directory>
echo "# 09_DevelopingDataProducts >> README.md"
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/peterpih/09_DevelopingDataProducts.git
git push -u origin master
```

**Change the name of a directory(branch)**
```{R}
rm --ignore-fail-on-non-empty .git
git init
git remote add origin https://github.com/peterpih/09_DevelopingDataProducts.git
git push -u origin master
```

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
```{R}
$ git pull
$ git status
$ git push
```

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

<div id='gh-pages-how-to'>
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

***Another way using git**  
Push html pages to master branch  
```
git push origin master
```
Now create a gh-pages branch (GitHub-pages)
```
git branch gh-pages
git checkout gh-pages
git puch origin gh-pages
```
This will create a gh-pages branch on github  
Also, create a push a .nojekyll file which avoids some of the fancy html in github
```
touch .nojekyll
git add .nojekyll
git commit -m "adding .nojekyll"
git push origin gh-pages
```
**To view the webpage, the url is**:  
http://\<github username\>.github.io/\<repo name\>/\<presentation name\>.html  

**To keep the master and gh-pages branches in sync**:  
http://concord-consortium.github.io/developer-notes/automating-gh-pages-integration.html  


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
