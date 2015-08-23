Login at: **www.shinyapps.io/coursera**  
(Create account using GitHub account)  


useful link:  http://cran.r-project.org/bin/windows/Rtools/  

###Install Shiny
```
install.packages('devtools')                      # install devtools
install.packages('RCurl')
devtools::install_github('rstudio/shinyapps')     # install shinyapps

library(shiny)
library(shinyapps)                                # runApp() is in here

                                                  # authorize computer (not shown here)
```
###Deploy to shinyio
```{R}
library(shinyapps)                                # load deployApp()
shinyapps::deployApp('path/to/your/app')          # deployApp() deploys the current app in current directory
```
