useful link: 
http://www.codeproject.com/Articles/457305/Basic-Git-Command-Line-Reference-for-Windows-Users
  
  

##Git Bash Commands &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Github commands are here](#github-section)

### Push files back to repository
```{R}
$ git status  (will tell you the status of the commits)
$ git add <file name>  or git add . (for everything)
$ git commit -m <message for commiting>
$ git push
```

If there is a conflict with other changes on GitHub first "pull" changes, then "push"
```{R}
$ git pull
$ git status
$ git push
``` 
<div id='github-section'>
#Github Commands

### Create a repository on GitHub
- Click New (upper right hand corner)
- Choose "Repository"
- Enter Name of new repository
- Select "Add README.md"
- Click "Submit"

### Delete a repository on Github
- Click on repository
- Click on Settings icon (right hand column)
- Click on Delete Repository, at bottom of page

### Clone a local repository using Git on PC
- cd to directory above where repository will be
```{R}
$ git clone https://github.com/peterpih/<repository name>
```
