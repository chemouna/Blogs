
# Open NLP

## Setence detection 
-  OpenNLP Sentence Detector can detect that a punctuation character marks the end of a sentence or not. 
 In this sense a sentence is defined as the longest white space trimmed character sequence between two punctuation With 

## Training Tool
OpenNLP has a command line tool which is used to train the models available from the model download page on various corpora. 
The data must be converted to the OpenNLP Sentence Detector training format. Which is one sentence per line.

## POS-tagging
also called grammatical tagging or word-category disambiguation, is the process of marking up a word in a text (corpus) 
as corresponding to a particular part of speech, based on both its definition and its context

In part-of-speech tagging by computer, it is typical to distinguish from 50 to 150 separate parts of speech for English. 
For example, NN for singular common nouns, NNS for plural common nouns, NP for singular proper nouns (see the POS tags used in the Brown Corpus).

## Part of speech
A part of speech (abbreviated form: PoS or POS) is a category of words (or, more generally, of lexical items)
which have similar grammatical properties. Words that are assigned to the same part of speech generally display similar behavior 
in terms of syntax—they play similar roles within the grammatical structure of sentences—and sometimes in terms of morphology, 
in that they undergo inflection for similar properties. Commonly listed English parts of speech are noun, verb, adjective, adverb, 
pronoun, preposition, conjunction, interjection, and sometimes numeral, article or determiner.


## Lemma 
is the canonical form, dictionary form, or citation form of a set of words (headword)[citation needed]. In English, 
for example, run, runs, ran and running are forms of the same lexeme, with run as the lemma. Lexeme, in this context, 
refers to the set of all the forms that have the same meaning, and lemma refers to the particular form that is chosen by 
convention to represent the lexeme. 

The process of determining the lemma for a given word is called lemmatisation

### Difference with Stem
Stem is the part of the word that never changes even when morphologically inflected; a lemma is the base form of the word. 
For example, from "produced", the lemma is "produce", but the stem is "produc-". This is because there are words such as production

Some lexemes have several stems but one lemma. For instance "to go" (the lemma) has the stems "go" and "went".
(The past tense is based on a different verb, "to wend". The "-t" suffix may be considered as equivalent to "-ed".)

### Lemmatisation
the process of grouping together the different inflected forms of a word so they can be analysed as a single item.
Document indexing software like Lucene[2] can store the base stemmed format of the word without the knowledge of meaning,
but taking into account the semantics of the word formation only. The stemmed word itself might not be a valid word: 'lazy', 
as seen in the example below, is stemmed by many stemmers to 'lazi'. This is because the purpose of stemming is not to produce 
the appropriate lemma – that is a more challenging task that requires knowledge of context. 

## Stem
a word has a single stem, namely the part of the word that is common to all its inflected variants.
A list of all the inflected forms of a stem is called its inflectional paradigm. The paradigm of the adjective tall is given below, and the stem of this adjective is tall.

tall (positive); taller (comparative); tallest (superlative)

### Stemming 
the process of reducing inflected (or sometimes derived) words to their word stem, base or root form—generally a written word form. 
Many search engines treat words with the same stem as synonyms as a kind of query expansion, a process called conflation.
Stemming programs are commonly referred to as stemming algorithms or stemmers.

A stemmer for English, for example, should identify the string "cats" (and possibly "catlike", "catty" etc.) as based on the root "cat", and "stems", 
"stemmer", "stemming", "stemmed" as based on "stem". A stemming algorithm reduces the words "fishing", "fished", and "fisher" to the root word, "fish". 
On the other hand, "argue", "argued", "argues", "arguing", and "argus" reduce to the stem "argu

There are two error measurements in stemming algorithms, overstemming and understemming. Overstemming is an error where two separate inflected words 
are stemmed to the same root, but should not have been—a false positive. Understemming is an error where two separate inflected words should be stemmed 
to the same root, but are not—a false negative. 

## Treebank
a parsed text corpus that annotates syntactic or semantic sentence structure. 
Treebanks are often created on top of a corpus that has already been annotated with part-of-speech tags.
In turn, treebanks are sometimes enhanced with semantic or other linguistic information. 



## Definition of some terms 
Corpora : In linguistics, a corpus (plural corpora) or text corpus is a large and structured set of texts (nowadays usually electronically stored and processed). 
They are used to do statistical analysis and hypothesis testing, checking occurrences or validating linguistic rules within a specific language territory. 


##  Clojure 


## TODO
http://www.cis.upenn.edu/~treebank/
https://en.wikipedia.org/wiki/Annotation
https://en.wikipedia.org/wiki/Natural_language_processing
https://en.wikipedia.org/wiki/Natural_Language_Toolkit
https://en.wikipedia.org/wiki/Speech_corpus
https://en.wikipedia.org/wiki/Computational_linguistics
https://en.wikipedia.org/wiki/Stochastic
http://lucene.apache.org/core/
https://en.wikipedia.org/wiki/Lucene
http://www-nlp.stanford.edu/links/statnlp.html#Taggers
https://github.com/ajerneck/nlp
https://opennlp.apache.org/documentation/manual/opennlp.html
https://writequit.org/blog/index.html%3Fp=365.html
http://blog.thedigitalgroup.com/sagarg/2015/10/30/open-nlp-name-finder-model-training/
