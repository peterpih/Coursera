**LensKit**: http://lenskit.org/  


Provided by University of Minnesota

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
Survivor bias - people stop going, lower scores disappear  
