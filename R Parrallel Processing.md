[R Parallel](#r-parallel-section)  
[Parallel Benchmarking](#parallel-benchmarking-section)  
[Amazon EC2](#amazon-ec2-section)  

<div id='r-parallel-section'>
###R Parallel Package
A technique I found useful when completing this class was to make use of parallel computing. Most modern computers will have multiple cores. This allows multiple things to be computed at the same time. By enabling and setting parallel processing in R, it will split up the computation task into several segments, and delegate them to different cores/threads in your computer processor to run simultaneously.  

If you are using the functions provided by the caret package, then they already have the option to make use of parallel processing on by default. All you have to do is set up and register parallel processing in your R session before calling the training function.  

```{R}
#install.packages("doParallel")
library(doParallel)
registerDoParallel(cores=2)
```

If your computer supports multi-threading within each core, then the cores argument will actually represent the number of threads you will assign, and not just the number of physical cores. So, if you have a Quad core computer, and each core is capable of 2 threads, then you could set cores=8. However, you might not want to do so for this assignment, for reasons that will be discussed next. 

**Balancing number of cores, and memory usage:**

In theory, the more cores/threads you enlist to perform the training process, the quicker it will get done. However, With each core/thread that you enlist, you will also incur a certain amount of additional memory usage. We will be dealing with some big datasets for the assignment. This data set will have to be loaded separately for each core that we enlist. The more cores/threads we enlist, the more memory usage we use up.  

If you had an unlimited amount of memory, then you could simply set cores to the maximum number of threads that your computer is capable of, and get the training process done in the quickest possible time.  

However, you might only have something like 4, 8 or 16 gigs of RAM on your computer. If the training process requires more memory than you have in RAM, then it will be forced to make use of SWAP memory. This is essentially a portion of space reserved on your hard drive. When your RAM overflows, it moves some of the data to this SWAP space. Unfortunately this seriously slows things down, especially with the large datasets we are dealing. It means that large chunks of data are constantly having to move back and forth between the hard drive and RAM for short periods of usage before having to be returned to SWAP space to make memory for other data that another core needs.  

As such, you might get better performance from using a smaller number of cores/threads. Essentially what you want to do is make use of the most number of cores/threads without using up all your RAM.  

On my quad-core computer, with two threads per core, and 8Gigs of RAM, the most number of cores I could get away with using before overflowing into SWAP memory was 2. Although it is possible that I could have gotten away with 3 if I had closed some extra applications on my computer.  

<div id='parallel-benchmarking-section'>
###Parallel Benchmarking  
For those interested in benchmarking their rigs, I did find this R-Script on http://librestats.com/2012/03/15/a-no-bs-guide-to-the-basics-of-parallelization-in-r/ for benchmarking the time dependence of running a simulation with 1, 4, and 8 workers.  

Running this code, I noted a 2X reduction in increasing workers from 1 to 4.  However the improvement from increasing workers from 4-8 cores was only about 20%.  I thought I had a reasonably fast rig i7-4800MQ with 32G installed memory; Win 7-64 on SSD drives.  Absolute time was about 400s on 1 core to about 200s on 4 cores.  Of course, I didn't SAVE the results, hence about 20% recollection error.  However, Windows is known for code bloat, so its possible that there are other "features" of Windows that is harming my code performance.  (Any of you recall the aphorism "Dogs crawl under fences.  Software crawls under Windows!"?)  

The interesting thing is that the author of the R-Blogger Post claimed performance times of   
```
avg      runtime cores
[1,] 0.666452 8.395   1
[2,] 0.665846 2.876   4
[3,] 0.666336 2.553   8
```
Code snippet:  

```{R}
#########################################
# ---------------------------------------
# Libraries
# ---------------------------------------
#########################################

library(doParallel)

#########################################
# ---------------------------------------
# Functions
# ---------------------------------------
#########################################

# One simulation of the Monty Hall game
onerun <- function(.){ # Function of no arguments
    doors <- 1:3
    prize.door <- sample(doors, size=1)
    choice <- sample(doors, size=1)
    
    if (choice==prize.door) return(0) else return(1) # Always switch
}

# Many simulations of Monty Hall games
MontyHall <- function(runs, cores=detectCores()){
    require(parallel)
    # clusterApply() for Windows
    if (Sys.info()[1] == "Windows"){
        cl <- makeCluster(cores)
        runtime <- system.time({
            avg <- mean(unlist(clusterApply(cl=cl, x=1:runs, fun=onerun)))
        })[3]
        stopCluster(cl) # Don't forget to do this--I frequently do
        
        # mclapply() for everybody else
    } else {
        runtime <- system.time({
            avg <- mean(unlist(mclapply(X=1:runs, FUN=onerun, mc.cores=cores)))
        })[3]
    }
    return(list(avg=avg, runtime=runtime))
}

#########################################
# ---------------------------------------
# Outputs
# ---------------------------------------
#########################################

run1 <- rbind(c(MontyHall(1e6, cores=1), "cores"=1))
run2 <- rbind(c(MontyHall(1e6, cores=4), "cores"=4))
run3 <- rbind(c(MontyHall(1e6, cores=8), "cores"=8))
rbind(run1, run2, run3)
```


<div id='amazon-ec2-section'>
###Amazon EC2
One thing I would recommend, if you are very short on time and can afford it, is using an Amazon EC2 instance.  

Setup is quick if you have experience with EC2. Here is a source for an Rstudio Amazon Machine Image (AMI).  

http://www.louisaslett.com/RStudio_AMI/  

I ran this image on a c4.8xlarge EC2 at 36 vCPUs and 60GiB RAM (the most powerful computational platform available to consumers) for only ~$2 per hour. Machines with lower power are even more inexpensive within the realm of USD.  

I was able to create a RandomForest model on 60% of the training set (using crossvalidation and without limiting branches or variables) in 100 seconds.  

For reference, the Monty Hall benchmark above scores like this on the c4.8xlarge:  
```
     avg      runtime cores
[1,] 0.667074 7.391   1    
[2,] 0.666616 2.179   4    
[3,] 0.66685  1.265   8    
[4,] 0.665899 1.012   36  
```
My own laptop's benchmark scores are this:  
```
     avg      runtime cores
[1,] 0.666007 571.51  1   
[2,] 0.667609 534.08  2  
```

So, this particular benchmark takes 0.2% of the time on c4.8xlarge vs my laptop.  

I'm honestly blown away by how inexpensive this solution is, and how powerful. I also had no stability issues, which did plague my own laptop as I built complex models.  
