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
Notebook creates the following tables:
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
