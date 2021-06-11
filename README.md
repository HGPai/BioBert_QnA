# BioBert_QnA
A biomedical question and answering system based on BERT

What is BERT?

In 2018 Google released an open-source Transformers based Natural Language Processing technique called Bidirectional Encoder Representations from Transformers
or commonly called <b>BERT</b>. The advantage of BERT is that it processes words in relation to all other words in the sentence instead of looking at them one-by-one.
That's why its called Bidirectional. BERT can be used for the common NLP tasks such as Text classification, Named Entity Recognition, Question and Answering, 
Semantic Similarity etc. 


## How BERT is applied to Question & Answering task

A Question & Answering dataset would contain a question and a sample paragraph of the answer where the BERT eventually learns to pick from. The question and the 'context'
are tokenized and converted into vectors. They are then fed into the model along with their 'Position embeddings'. The model learns from these values and recreates the 
answer by predicting the start and end positions of the 'supposed' answer.

For the Biomedical Question & Answering task, we'll be using the BioASQ dataset. 


### BERT Input Format
For the QA task, BERT is fed with the tokenized vectors created by combining question and the reference text. the vectors begin with `[CLS]` token to indicate classification 
task. The question and the reference text are separated by a `[SEP]` token. BERT also uses 'Attention Mask' to differentiate the question from the context. 

### Final Classifier
For the QA task, BERT generates the answer by predicting the start and end positions of the token

![Start Token Classification](/start_token_classification.png?raw=true "Start Token Classification")

BERT returns two kinds of output - Sequence output and Pooled output. For token classification, the sequence output is used. After passing the sequence output through 
a Dense layer. It is then flattened to a 1 dimensional array and applied with a Softmax function to produce probability distribution of vectors. The vector that produces
the highest probability is identified as the respective token. This process is applied to Start and End tokens.


![End Token Classification](/end_token_classification.png?raw=true "End Token Classification")


