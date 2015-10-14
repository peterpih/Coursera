**LensKit**: http://lenskit.org/  
Provided by University of Minnesota

[Content Based Reccomender Systems)(#content-based-reccommender-section)

<div id="content-based-reccommender-section>
###Content Based Rccommender Systems
**Keyword Vector**  
description can be in projected in keyword vector space as can user preference  
cosine appoaches 1 as angle gets small  
https://en.wikipedia.org/wiki/Vector_space_model  
https://en.wikipedia.org/wiki/Generalized_vector_space_model  

Representing keyword vector:  
1. simple - yes(1) or no(0) to each keyword  
2. occurance - number of times a keyword is used to discribe  
3. TFIDF -  inverse document frequency measures scarcity  

When to normailize vector: when you want it to be equally weighted, when not many observations  

**Compupting Predictions**
**prediction** is the **cosine** of the angle between two vectors: feature vector and user vector  
Compute the dot product of two normailized vectors: multiply corresponding elements, add and take square root  
Using unnormalized vectors, divide by the product of the the two lengths  
Cosine ranges between -1 and 1 or 0 and 1 (if all positive, 1 is better  

Keyword vectors can not handle interdepencies, ie I like 



###Domain of Reccommendation
What's being reccomended?  
  - Matching people to people  
  - Sequences of music  
  - Reccommend new items? Known items?  
  
Purpose of reccommendation
  - Buy
  - Consume
  - Education
  - Build community
  
Reccommendation Context  

Personalization  

7. Interface
8. Recommendation Algorithms
  - Non-Personalized Summary Statistics
  - Content Based Filtering
    - Information Filtering
    - Knowledge-Based
  - Collaborative Filtering
    - User-User
      - Select neighborhood of similar taste people (variant: select people you know/trust)
    - Item-Item
      - Precompute similarity amoung items
      - Use own ratings to triangulate for reccomendations
    - Dimensionality Reduction
      - Intuition: taste creates a lower dimenionality matrix
      - Compress and use a taste representation
  - Other
    - Critique / Interview Based
    - Hybrid Based

#Basic Model
  1. People
  2. Items
  3. Ratings
  4. (Community)

###Non Personal Recommenders  
**Averages** a blunt instrument  
**Product Associations** - products that are related together  
  - what people bought at the same time, not good for follow up  
  - time windows - what people bought within a time window
**Ephemerally Personalized** reccomendation - people doing x basically will do y  

**How scores change over time**  
Self selection - only people interested will vote  
Survivor bias - people stop going, lower scores disappear, giving upward bias of scoring  

###Predictions and Reccomendations
Reccomendations are suggestions 
  - pros: provides set of good choices  
  - cons: can stop exploring if perceived to be top-n, will stop when less relevent  
Predictions involve accuracy and more precision  
  - pros: helps quinatify, how much would you like it, how accurate  
  - cons: provides something falsifiable, can be wrong  

###Scale and Normalization
Aggregate Preferences  
  - Average rating, upvote proporation, 
  - Net upvotes (Reddit), shows popularity, doesn't show controversy
  - Likes (Facebook)  
  - Histogram  

Why not use rating as score?
  - data is too sparse  
  - may be old  
  - maye want to bias toward local interntionally  

Ranking consideration  
  - How confident are you in the ranking?  
  - risk aversion, what if wrong?  

Confidence Intervals  

###TFIDF
Motivation behind TFIDF is the failure of search engines  
Things to consider:  
1. How often does the term appear in the document  
2. Not all terms are equally relevent  

###TFIDF Weighting** = Term Frequency * Inverse Document Frequency  
**Term Frequency** - how often does the term appear in the document  
**Inverse Document Frequency** - inverse of how many documents have a term in it, rarity is good usually:  
```
log (# documents) / (# documents with term)
```
keywords - metadata  
tags - descriptive phrases applied by the community  
Automatically demotes stop words
TFIDF fails when the document itself does not contain the necessary term  

BM25 (aka Okapi BM25)  

Problems with TFIDF:  
1. Phrases and n-grams, adjacency  
2. Significance within a document, ie title, heading, paragraph  
3. General document authority: Page ranks (are other documents linked to it)  
4. Implied content ie links  

