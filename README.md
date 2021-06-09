# CS 522 hate speech project
## Evaluating the effectiveness of GPT-2 generated hate speech for SVM and BERT hate speech classification

### Problem Statement

The aim is to see if using GPT-2 generated data to train a predictive hate speech model will improve the accuracy of the model. 

### Methodology

The models we built use SVM and BERT. We compared the effects of different amounts of GPT-2 generated data on the accuracy of the model. This project was completed in python and run on google Colab. In order to utilize the data sets properly, much cleaning and pre-processing was done on them, such as removing emojis, fixing grammar, and removing excessive punctuation.

Input sizes of 200, 500, 1000, and 2000, were used to train BERT and SVM model experiments. For each experiment, 2 models were created. One model took in purely original input data, and the other took in text that had been generated using the base 200 rows of data. For example, for a set of 1000 rows, 200 would be original data and 800 would be GPT-2 generated data. The input were randomly selected from the original data set.

The models were tested on rows from the data set that had been partitioned off and unused during the training phase.

### Data set used
https://www.kaggle.com/mrmorj/hate-speech-and-offensive-language-dataset

This data set contained over 24000 tweets that were classified into hate speech, offensive language, or neither.

### GPT-2
Generative Pre-trained Transformer 2 is basically a model that has been trained to learn relationships between words using a large amount of language data from the web. The model is able to take a sequence of words as input and create human-like text that is supposed to be a continuation of the inputted text.

### SVM
Support Vector Machine essentially creates a line (or hyperplane) that divides and classifies the data. It makes sure that this line is as far away as possible from each of the closest data points on either side in order to find the best line. Tuning parameters include: C (higher C means higher accuracy for the training model), Gamma (higher Gamma means more influence from the points closer to the hyperplane than those further away). SVM is not specialized for NLP and does not contain its own dictionary.

### BERT
Bidirectional Encoder Representations from Transformers is a natural language processor. It takes text and learns contextual relations between the words in order to make predictions. BERT employs 2 strategies in its training: Masked LM (MLM), and Next Sequence Prediction (NSP). In MLM, BERT masks some percentage of the words getting fed into the trainer and then tries to predict those masked words based on what it has seen. This makes BERT more robust to noise. In NSP, pairs of sentences are sent as input. Part of the input pairs are sequential sentences (one follows the other and they are connected in some way), while the other part of input pairs has 2 disconnected sentences. BERT learns to predict if the second sentence in the pair is the subsequent sentence in the original document. BERT comes with its own corpus of words since it has already been trained.

### Is Generated Text Effective For Training?
What we discovered is that GPT-2 generated text actually does improve the accuracy of the models we built using SVM and BERT by about 5% - 15% over different , given that the input to GPT-2 is sufficiently processed. Another finding is that BERT out performs SVM in almost all classification categories by at least 10% for all input sizes. If we had more time we would have performed more rigorous testing with larger data sets and repeated the experiment with another random distribution of data as the input, but because of our current results, we would recommend companies looking to train hate speech classifiers to consider using GPT-2 generated data as it is more cost effective than scraping their own data on the web.

### Tools used
Python (ipynb),
Numpy,
SVM,
BERT,
GPT-2, 
Microsoft Excel


