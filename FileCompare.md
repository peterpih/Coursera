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
  
  ### Get two directorirs and compare the names
  ```
  path1 <- "C:/Pics iPhone 20150212"
  path2 <- "C:/Pics iPhone 20150501"
  list1 <- list.files(path=path1)
  list2 <- list.files(path=path2)
  found <- list1 %in% list2
  ```
  
  
  
