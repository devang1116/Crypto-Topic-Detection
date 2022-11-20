# Crypto-Topic-Detection

## The project determines whether or not a message is talking about crypto/web3 or not . 

In this problem statement ie. Crypto Topic Detection the machine learning model has to determine whether or not a particular problem statment is related to CryptoCurrency , Blockchain , Web3 , etc. It involves the use of <b> Natural Language Processing , Word Embedding , Topics Modeling , BagOfWords , Sentence Similarity</b> in great detail.

I have used multiple datasets ie. <b>term_def.csv , term_abb.csv , sport_results.csv , news_results.csv , art_results.csv , music_results.csv and food_results.csv</b>.

I have made use of multiple libraries mainly those are <b>nltk , spacy , pyLDAvis , pandas , gensim </b> , etc.

First of all i've imported dataset term_def and got all the sentences from the dataset into another Dataframe to simplify our work. Then we preprocess the data removing unwanted spaces , punctuations , special charecters , links and empty columns from the dataset using our User Defined function. Further on we perform <b>Tokenization</b> : (breaking down the text into tokens) , <b>Stemming</b> : (removing the prefixes and suffixes to obtain the root word) , <b>Lemmatisation</b> : (grouping together different inflected forms of a word into a base word called lemma) and create a new column for these newly created tokens. Then we create a large dictionary from all these tokens from the entire dataset and create a <b>Corpus</b> : (collection of authentic text or audio organized into datasets) from the BagOfWords or Dictionary created prior . Further we perform Topic Modeling : (analyzes text data to determine cluster words for a set of documents) on the Corpus of words and the Dictionary using the <b>Latent Dirichlet Allocation</b> : (generative statistical model that explains a set of observations through unobserved groups, and each group explains why some parts of the data are similar) algorithm which models the entire corpus into topics and sub topics based on the context of the words and the occurences in the particular context of Corpus which gives a list of topics and subtopics which we append into a single list of topics modeled . We then also add terms from term_def.csv to the list of topics modeled or BagOfWords for Crypto adding to the number of topics previously present there getting us the final BagOfWords .

I've then created a test dataset of 1500 from multiple such as sport_results.csv , news_results.csv , art_results , music_results and food_results.csv which does not contain any crypto related textual data so we create a new column 'labels' and mark it as Disimilar as these wont contain any Crypto related data and respectively use crypto_results.csv which contains crypto related textual data so we create a new column 'labels' and mark it as Similar as these  contain any Crypto related data. Further a new column predict will be created which will be pre assigned with '.'. Then a User Defined similarity score ie. <b>CoSine similarity</b> : (measure of similarity between two non-zero vectors of an inner product space that measures the cosine of the angle between them) will generate a score between an individual sentence and the BagOfWords created earlier . I have then determined a threshold value over which a sentence is termed as Similar otherwise it is termed as Disimilar and assign them specifically to the predict column of testData for each sentence.

Futher iterating the entire testData we determine the AccuracyScore by determing the correct predictions which we get by checking if the 'labels' column and 'predict' colummn are same which is accuracy variable , then generate AccuracyScore by dividing the right predictions by the overall rows.
