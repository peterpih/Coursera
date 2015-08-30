http://slidify.github.io/dcmeetup/demos/interactive/  

###Installing
```{R}
# 1) Install devtools
install.packages("devtools")
library(devtools)

# 2) Install slidify
# install_github("ramnathv/slidify")
install_github('ramnathv/slidify', ref = github_pull(425))    # this seems to be some sort of patch
                                                              # https://github.com/ramnathv/slidify/issues/373
install_github("ramnathv/slidifyLibraries")

# 3) load slidify
library(slidify)
```

Change working directory to where you want it, and then:  
```{R}
author("project name")
```
Will create a skeleton document

```{R}
slidify("index.Rmd")

library(knitr)
browseURL("index.html")
```

###Publishing

Publishing to Github is as easy as running publish from inside the slide directory. You need to have git installed on your system, create an empty github repo and ssh access set up for github.

```{R}
publish(user = "USER", repo = "REPO")
```
