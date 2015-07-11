#Compare File Directories
```
list.files(\<path=\>, \<pattern=\>,\<all.files=\>, no)
```
- arguments
  + **path=** (".") path name
  + **pattern=** (NULL) filter file names
  ```
  pattern="*.jpg"
  ```
  + **all.files=** (FALSE) TRUE=include hidden files
  + **full.name=** (FALSE) TRUE=prepend relative path
  + **recursive=** (FALSE) TRUE=recurse directory tree
  + **ignore.case=** (FALSE) pattern matching case sensitive
  + **include.dirs=** (FALSE) should subdirs be included in recursive listing
  + **no..=** (FALSE) should "." and ".." be excluded from non-recursive listing
  
  ### Get two directories and compare the names
```
a <- c(dir(), "/")
a <- a[file.info(a)$isdir == TRUE]
a
```
```
path1 <- a[90]
path2 <- a[120]
```
```
list1 <- list.files(path=path1)
list2 <- list.files(path=path2)
matched <- list1 %in% list2
sum(matched)
matchedNames <- list1[matched]
```
create subdirectory in path1 andmove matched files there
```
pathMatched <- paste0(path1, "/matched/")
dir.create(paste0(path1,pathMatched))

n = length(matchedNames)
for (i in 1:n){
  file.rename(from=paste0(path1, matchedNames[i]), to=paste0(pathMatched, matchedNames[i]))
}
```

  
  
  
