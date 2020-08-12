# Exploratory Analysis of Technology and Telecommunication Transcript
Many companies keep transcripts of conferences, tech talks, and quarterly earning calls
between company management, industry competitors, and analysts. These transcripts contain
useful information that can provide insight into business decisions, performance, and industry
competitors. However, reading numerous transcripts manually can be difficult and timeconsuming.
To aid businesses, I aim at using a transcript dataset containing 1,401 transcripts to
derive trends and common topics within these companies. The transcript dataset consists of
companies like Cisco, Intel, IBM, and Verizon transcripts, from 2002 through 2017.

## Notebooks
### generateTables.ipynb
The following 3 normalized tables were generated to represent the transcripts.
- __LIB.csv:__ The LIB table contains metadata information about all the transcripts. This file includes
file_id, file_name, company, title, date, and year.
- __TOKEN.csv:__ The OHCO indexing used for tokenizing the transcripts is: file_id, company, title,
speaker, sent_num, and token_num. Tokenization was completed using the NLTK
word_tokenize method. Tokens are lowercased and punctuations and blank spaces are
removed to get term string. Each term string is associated with a part of speech (POS) tag using
the NLTK pos_tag method.
- __VOCAB.csv:__ The VOCAB table consists of all unique terms that are present in the TOKEN table. It
includes a count of each term string, and if a term string is a number or a stop word. The stems
and POS tag is also present in this table.

### analysis.ipynb
  Using the annotated and vectorized tables, Principle Component Analysis (PCA), word2vec
Word Embedding, Sentiment Analysis, and Latent Dirichlet Allocation are constructed.
  A TFIDF (term frequency-inverse document frequency) representation of the TOKEN data is
created using a user-defined function (UDF) and saved as TFIDF.csv. The UDF is responsible for
creating the bag-of-words, TF, DF, IDF, and returning a TFIDF matrix. The table shares the same
term_id, term_str, and POS tag as the VOCAB table. Also, tfidf_sum_transcript is calculated for
each term.
- __PCA__:
PCA is constructed using sklearn decomposition PCA on the TFIDF matrix. The top 10
components were extracted and the PCA values were stored as LOADINGS.csv. The LOADINGS
table consists of term_id, term_str, and 10 PCA values.
- __word2vec Word Embedding__:
Using the genism package 100-dimensional vectors are created to represent each word. The
EMBEDDINGS.csv file contains the vector representation of words and 2-dimensional
coordinates generated for t-SNE analysis.
- __Sentiment Analysis__:
The sentiments associated with each term is computed using the salex NRC emotion lexicon
table. The SENTANALYSISVOCAB.csv file contains the polarity, anger, anticipation, disgust, fear,
joy, sadness, surprise, and trust associated with each word. This table contains the same terms
as the VOCAB table.
- __LDA__:
A 7 topic model was generated using 5000 terms and max iteration of 10, using sklearn
decomposition LatentDirichletAllocation. The topic distribution per document is stored as
DOCTOPIC.csv and the topic distribution per term is stored as TERMTOPIC.csv.
