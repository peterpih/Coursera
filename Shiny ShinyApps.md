Login at: **www.shinyapps.io/coursera**  
(Create account using GitHub account)  


useful link:  http://cran.r-project.org/bin/windows/Rtools/  

```
install.packages('devtools')                      # install devtools
install.packages('RCurl')
devtools::install_github('rstudio/shinyapps')     # install shinyapps

                                                  # authorize computer (not shown here)

library(shinyapps)                                # deploy
shinyapps::deployApp('path/to/your/app')
```
