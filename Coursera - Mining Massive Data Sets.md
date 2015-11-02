**Power Iteration**: http://www.codeskulptor.org/#user40_7DWAfop9GV_1.py  

###MapReduce
**Classic Model of Computing** single cpu and memory  
**Cluster Architecture** multiple cpus  

**Cluster Computing Challenges**
1. Node Failure - single node fails once per 1000 days, 3000 modes will fail 3 nodes per day (on average)

How to store the data persistently across failures?  
How to deal with node failure during long computation?  

2. Network bottleneck  
3. Distributed programming is hard!  

***Solution***
1. Store data redundantly on multiple nodes
    a) Distributed file system, ie Google GFS, Hadoop HDFS  
    b) Data is rarely update in place, usually through appends - Write Once, Read Many, Append Occassionally
    c) Data kept in chunks across multiple **Chunk Servers** (usually 2x or 3x most common)  
    d) Chunks are kept on different servers  
    e) Chunk servers also act as compute servers, does computation on the local chunk  
    f) **Master Node** (Name Node in Hadoop HDFS)  
        a) Takes care of coordination  
    g) **Client Library**  
    
2. Move computation close to data, avoid moving data around  
3. Simple programming model  

###Map Reduce Computational Model
**Word Count Problem**: File too large to fit in memory
  1) Use **Hash Table** will produce some data compression  
  2) Word count pairs too large to fit in memory, use file system
  3) Map Reduce
    a) **Map** term for each record (text line), produces a **key*
    b) Group by key
    c) **Reduce** aggregate, summarize, filter, or transform  
    
**Mapfunction** produces (key, value) paires  
1) **Map**
2) Group By Key
3) **Reduce**  

#Map -> Group by key -> Reduce


**Distributed processing** can help speed things up    
  a) all tuples with the same key, end up at the same Reduce node  
  b) implemented using sequential scans of disk  
      

###How many **M** map tasks and **R** reduce tasks?
***Rules of Thumb:***  
1) Make **M** much larger than the number of nodes in the cluster  
2) One DFS chunk per map is common  
3) Improves dynamic load balancing and speeds up recovery from worker failures

4) Usually **R** is smaller than **M**  


###Refinements
**Combiners**
**[ Mapper -> Combiner ] -> [ Shuffle ] -> [ Reducer ]**  
Usually **Combiner** is same as **Reducer** but on a single node  
**Combiner** only works if the **Reducer** function is commutative and associative  

**Partition Function**

**Implementations**
**Google MapReduce** uses Google File System (GFS), internal to Google  
**Hadoop** - open source implemented in Java, uses HDFS, download: http://lucene.apache.org/hadoop  
**Hive**, **Pig** provide SQL-like abstractions above Hadoop Map-Reduce layer  

#Analysis Of Large Graphs
Web as a graph, **web pages** are nodes, **hyper link** edges  

**Challenges of web search**
Whom to trust??
Trustworthy pages may point to each other  

What is the best way to query "newspaper"?  
Pages that know about newspaper may point to many newspapers  

#PageRank
**Flow Model**

**Stochastic Adjacency Matrix**

Power Iteration: http://www.codeskulptor.org/#user40_7DWAfop9GV_1.py
**Power Iteration with beta**: http://www.codeskulptor.org/#user40_7DWAfop9GV_2.py  
http://www.codeskulptor.org/#user40_7DWAfop9GV_6.py


#Similar Sets
Finding textual data that is similar
###Shingling
false positives and false negatives  
***k-shingle*** a sequence of **k** concsecutive characters (white space is considered a character)  
Usually k =5..10  
Changing words or moving entire paragraphs will only effect the boundary shingles  
Shingles can be further hashed into **tokens**  

###Minhashing

###Locality Sensitive Hashing

###Jaccard Similarities
size of the intersection of 2 sets divided by the size of their union  
```
rows are books
columns are customers
each book a customer has has a '1' otherwise '0'
compare the books owned by two different customers
if they both have 3 books and the total number of books is 15
then Jaccard similarity is 3/15
```
###MinHashing
Example:  
```
                   P1  P2
1) 1 | 0 | 1 | 0   3   4      p1.1  0 | 1 | 0 | 1
2) 1 | 0 | 0 | 1   4   2      p1.2  2 | 1 | 2 | 1   each value is the iteration #
3) 0 | 1 | 0 | 1   7   1                            when no 0's minhash is done
4) 0 | 1 | 0 | 1   6   3      p2.1  0 | 1 | 0 | 1
5) 0 | 1 | 0 | 1   1   6      p2.2  2 | 1 | 0 | 1 
6) 1 | 0 | 1 | 0   2   7      p2.3  2 | 1 | 0 | 1
7) 1 | 0 | 1 | 0   5   5      p2.4  2 | 1 | 4 | 1
```
