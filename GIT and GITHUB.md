useful link: 
http://www.codeproject.com/Articles/457305/Basic-Git-Command-Line-Reference-for-Windows-Users
  
  

##Git Bash Commands &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Github commands are here](#github-section)
###Clone a local repository using Git on PC**
```{R}
$ cd <directory you want the repository to be in>
$ git clone https://github.com/peterpih/<repository name>
```
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
- 

### Delete a repository on Github
- Click on **repository name**
- Click on **Settings** icon (right hand column)
- Click on **Delete Repository** at bottom of page

