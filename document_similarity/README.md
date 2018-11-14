For document similarity, we have implemented two methods.

1. Bag-of-words model : 
	Early state-of-the-art document representations were based on the bag-of-words model, which represent input documents as a fixed-length vector. For example, the two documents
(1) John likes to watch movies. Mary likes movies too.
(2) John also likes to watch football games.
are used to construct a length 10 list of words
["John", "likes", "to", "watch", "movies", "Mary", "too", "also", "football", "games"]
so then we can represent the two documents as fixed length vectors whose elements are the frequencies of the corresponding words in our list
(1) [1, 2, 1, 1, 2, 1, 1, 0, 0, 0]
(2) [1, 1, 1, 1, 0, 0, 0, 1, 1, 1]
Now, to find the similarity between the above given documents, we calculate the cosine_similarity between the above two vectors.
	Bag-of-words models are surprisingly effective but still lose information about word order. Bag of n-grams models consider word phrases of length n to represent documents as fixed-length vectors to capture local word order but suffer from data sparsity and high dimensionality.

2. Paragraph Vector, aka gensim Doc2Vec :
	The straightforward approach of averaging each of a text's words' word-vectors creates a quick and crude document-vector that can often be useful. However, Le and Mikolov in 2014 introduced the Paragraph Vector, which usually outperforms such simple-averaging.

	The basic idea is: act as if a document has another floating word-like vector, which contributes to all training predictions, and is updated like other word-vectors, but we will call it a doc-vector. Gensim's Doc2Vec class implements this algorithm.
