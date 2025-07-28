# Satria Data: Big Data Challenge 2024

## About the Competition
### Satria Data
The organization of the Statistika Ria dan Festival Sains Data (SATRIA DATA) reflects the Ministry of Education, Culture, Research, and Technology’s support for the advancement of statistics and data science as academic disciplines. Additionally, this event aims to act as a catalyst for building collaborative networks between universities and industry applications.

### Big Data Challenge
The Big Data Challenge (BDC) is a competition designed to generate recommended solutions to real-world problems through analytical, mathematical, and statistical approaches. The problems presented in the competition are real business, operational, or strategic issues faced by the organizing partners. These partners may come from government institutions, research bodies, private companies, non-governmental organizations (NGOs), academic institutions, or other organizations that agree to participate in the competition. Problem-solving is carried out using statistical, analytical, and machine learning techniques based on data. Although not limited to these, the types of analytical problems in the competition typically include:
a. Event prediction and/or forecasting
b. Optimization
c. Clustering

In 2024, the Big Data Challenge focuses on Natural Language Processing (NLP) to analyze tweets on the social media platform Twitter. The text data revolves around one main topic: Indonesia’s 2024 General Election. Participants are required to classify user tweets related to the election into the following 8 categories:
1. Sumber Daya Alam (Natural Resources)
2. Politik (Politics)
3. Demografi (Demographics)
4. Pertahanan dan Keamanan (Defense and Security)
5. Ideologi (Ideology)
6. Sosial Budaya (Socio-Culture)
7. Ekonomi (Economy)
8. Geografi (Geography)

## Metodologi
### 1. Preprocessing Data
Data cleaning was performed using the following steps:
- Text standardization: convert to lowercase, remove punctuation and emojis (using the emoji library).
- Remove Indonesian stopwords (from Sastrawi).
- Use TweetTokenizer from NLTK for social media-specific tokenization.
- Use regex to remove usernames, hyperlinks, and words like “RT”/“retweet”.
- IndoNLP was used to handle slang and elongated words (replace_word_elongation).
- Manual filtering: remove names of political figures (Anies, Ganjar, Prabowo, etc.) as they do not provide useful information for topic classification.
After cleaning, stemming and lemmatization were applied to the data using the Sastrawi library for Indonesian-language stemming.

### 2. Modelling
The dataset was split into training and testing sets, then converted to a TensorDataset. The model used was BERT (indobenchmark/indobert-base-p1) with the BertForSequenceClassification architecture. Class imbalance was addressed using class_weight, and evaluation was done using balanced accuracy score. DistilBERT was also tested and showed better results due to its lighter architecture, which reduced the risk of overfitting.

## Results
The final result achieved an accuracy of 41% when submitted to the Satria Data Big Data Challenge competition portal.
