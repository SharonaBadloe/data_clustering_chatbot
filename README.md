# Clustering data based on sentence vectors

# Files
All filepaths in the notebooks are relative to the filestructure within this github repository. 
- Directory - data: contains original and processed data
- Directory - results: contains 1 excel sheet for each found cluster
- Preprocessing: contains the first preprocessing steps in this pipeline
- Contains code for EDA and saves some stats for visualization
- EDA: data visualization dashboard (.JPG)
- sentence_bert.ipynb: vectorizing and clustering with BERT and KMeans
- word2vec.ipynb: vectorizing and clustering with word2vec and Kmeans

# Task:
Clustering customer support data based on similar sentences for the creation of a chatbot.

# Method
- Data preprocessing: SpaCy + DataPurifier + Stanza
- Sentence vectorizing algorithms: Sentence Bert vs. Word2Vec
- Clustering algorithm: Kmeans

# Other helpful algorithms
Another useful algorithm that was not used in this project is LDA, or Latent Dirichlet Allocation. This is a topic modelling algorithm that is widely used with good results. A topic according to this algorithm is a selection of dominant keywords that are related. Together these key words form a topic. LDA find the distribution of each topic in a document, and also calculate the proportion of each topic in relation to each other. In this way, the dominant topic + keywords can be found in each document, and over a collection of documents.

# Found clusters
- Cluster 1: 'Please provide us with more details so we can investigate this issue further'
- Cluster 2: 'We will gladly help you'
- Cluster 3: 'Send us a note at the following link'
- Cluster 4: 'Thank you for reaching out!'
- Cluster 5: 'Please DM us your contact information'
- Cluster 6: 'We are very sorry to hear that'
- Cluster 7:  Flight issues
- Cluster 8:  Refund request
- Cluster 9:  Order problems
- Cluster 10: Internet connection

# Conclusion
For both models, it was considerably harder to spot patterns in the customer replies than it was for the employee replies. This makes sense when looking at the data/ You an easily see that the employee replies are very well structured and a lot more predictable, formal and gramatically correct. The customer questions have a wider range of vocabulary. They also use more slang, emoticons and interpunction to express how they are feeling. These variations in language can be very confusing for a language model. The Kmeans algorithm performed well but as expected, the performance was highly reliant upon the amount of clusters, the way the data was preprocessed, and the vector representation. 

Overal BERT did better at grouping sentences together that aren't worded the same but are still related. BERT was also better at spotting common employee responses in this regard. Since BERT is good at spotting patterns in the context of an entire sentence, and the employee responses are very structured, the employee clusters turned out quite coherent. 

Word2Vec was better than BERT at spotting common customer questions however. Word2Vec generally only grouped sentences with really similar wording together, which worked well for spotting some customer questions. Since BERT is able to take so much context into consideration, it will look for more than just similar words. Because of this, the unstructured customer questions seemed very confusing for BERT. The questions were grouped together in ways that were unhelpfully unrelated because of this. In the future, it would be interesting to play with more features for Word2Vec, such as topic keywords as a binary or predicate information. It would also be interesting to see how BERT does with just the sentence vectors, without the cosine similarity matrix. 
