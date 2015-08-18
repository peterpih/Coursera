Reference paper: 'Dates and Times Made Easy with lubridate'  

| Unfortunately, due to different date and time representations, this lesson is only guaranteed to work with an  
| "en_US.UTF-8" locale. To view your locale, type Sys.getlocale("LC_TIME").  

this_day <- today()  

year(this_day)  
month(this_day)  
day(this_day)  

wday()  


###date-times

now()  

arrive <-with_tz(arrive, tzone="Asia/Hong_Kong")  
last_time <- mdy("June 17, 2008", tz="Singapore")  
how_long <-new_interval(last_time, arrive)  
as.period(how_long)  

