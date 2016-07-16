[Distributed Representation of Sentences and Documents](https://cs.stanford.edu/~quocle/paragraph_vector.pdf)

* Brief:

This paper introduces the method for learning fixed length vector representation for variable sized text segments (paragraphs, phrases, documents etc.). It uses idea similar to word2vec paper. Through experiments they proof that the dense, low dimensional representation learnt from this method is better than the more popular 'bag-of-words' model.

* Method:

Authors describe two methods for learning vector representation of textual units : PV-DM (Distributed Memory model for Paragraph Vectors) and PV-DBOW (Distributed Bag Of Words model for Paragraph Vectors). They are analogous to CBOW and Skip-gram methods for learning word representations. 

In PV-DM model document vectors are learned through word prediction task. The task is : For a fixed size window from corpus, given the word vectors and the paragraph vectors indexed by Word Embedding and Paragraph embedding lookup table, predict the center word given the context word vectors and paragraph vectors. The vectors can be combined either through concatenation or through averaging. 

The parameters of the model are: Word embedding matrix W, Paragraph Embedding matrix V, softmax matrix U, softmax bias b. Training is done through backpropagation. For inferring paragraph vector of a new sentence a vector corresponding to the new paragraph is initialised randomly and then it is updated using Gradient Descent, while keeping other parameters fixed until convergence.

In PV-DBOW model word vectors again are learned through the task of word prediction. For a fixed size window, given the paragraph vector, predict the words in the window. Training is again through backpropagation and for inference, paragraph vector is learned through backprop. by keeping other paramters fixed. 

* Insights:
This paper presents a novel idea for paragraph vector learning which they prove to be better than bag-of-words. Since this is an unsupervised learning, the vectors learned can be used to variety of supervised tasks on documents like: prediction, topic modelling, similarity etc. 

This paper is also a very good demonstration of the fact that simple ideas sometimes work better than highly complex ideas. Some other vector representation schemes proposed by other authors like using parse trees (by Socher et. al), which dependes on parsing and learning representations from it, which is complex.

One shortcoming which I could think of in the paper is that the authors didn't compare their results with word vector averaging method. Word vector averaging is most intuitive extension of word vector model for paragraphs. And in many cases it performs very well, infact in a recent ICLR '16 paper it is shown that it even outperforms LSTMs. 

Other than that it's a very good paper with very intuitive idea.
