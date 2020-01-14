# itod
This repository contains an implementation of a hybrid method for analyzing word senses: based on Word Sense Induction (WSI) results we perform Word Sense Disambiguation (WSD). 

Original datasets we use are in the folder '**data**', the folder '**preprocessed**' contains outputs of the notebook 'Preparing datasets', and results of different steps from the notebook "WSI to WSD" are included in the folder '**results**'. **Each folder contains a more detailed description of its content**.

### WSI vs WSD 

The purpose of WSI is to analyze the corpus and cluster contexts of a target word that have a similar meaning, without knowing how many and which senses the target word has. The senses themselves are not identified, i.e. all contexts of the target word in the identified cluster should have the same sense but we don't know which sense that is.

In WSD, on the contrary, the senses of the target word are known in advance, and the goal is to identify which sense the target word has in the new given context.

Our algorithm combines these two tasks: clusters of contexts for potentially ambiguous words are matched automatically with dictionary definitions that are consequently used as cluster labels in WSD.

### The Algorithm 

The proposed algorithm takes a set of contexts as an input and returns the most suitable dictionary definition. This allows the users to understand which sense the cluster of contexts has, with no need for manual evaluation. As a result, the interpretability of WSI increases.

1. Clusters of contexts for target words are represented as sets of keywords. Under "keywords" we understand context markers, the most important ones for identifying the sense of a target word.
2. Keywords of each cluster are matched with dictionary definitions of a target word. Here, two approaches are possible:
   - Baseline: is based on the overlap of keywords and words in the definition
   - Proposed approach: compares distributional vectors of keywords and definitions. 
 
In more detail, in the proposed approach sets of keywords and words from definitions are represented as vectors in n-dimensional space. For each set of keywords its mean vector is calculated and compared with mean vectors of definitions. The definition whose vector has the biggest cosine value with the keywords' vector is chosen.

For vector operations, we use the Word2Vec Skipgram model made available by the RusVectores project. It is trained on the National Russian Corpus and Wikipedia dump of December 2018 containing 788 millions of words and almost 250000 distinct words. 300-dimensional vectors were trained on the corpus annotated with POS tags ("Universal Tags"), and with the window size 2.

### WSD 

Now, WSD itself can also be performed - the user can get the dictionary definition for the sense in which the word is used in the given context. It is performed as follows:

A new context of a target word is represented as a vector and given to a classifier. The classifier chooses the best cluster for this context basing on cluster centroids and returns the dictionary definition associated with this cluster at the previous step. 
