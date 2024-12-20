# Twitter Analysis of NU and Nahdlatul Ulama: Data Transformation for In-Depth Understanding

## 1. Introduction
In recent years, social media has become the primary platform for individuals and organizations to interact, share ideas, and shape public opinion. One of the most dominant social media platforms is Twitter, now rebranded as X.com. On this platform, topics related to various social, political, cultural, and religious issues are often discussed. One of the organizations frequently discussed is Nahdlatul Ulama (NU), the largest Islamic organization in Indonesia. As a religious organization, NU has a significant influence on social, cultural, and political life in Indonesia.

It is important to study how the public on social media talks about NU and Nahdlatul Ulama, especially to understand how perceptions of the organization are formed in the digital public sphere. Therefore, this study aims to analyze public sentiment toward NU and Nahdlatul Ulama on X.com. In this study, a total of 3,322 tweets related to NU and Nahdlatul Ulama were collected from <b>May to July 2024</b>. The collected data is analyzed using various data processing techniques and machine learning algorithms to identify public sentiment, conversation trends, and emerging opinions about the organization.

Through this analysis, deeper insights are expected regarding how the public views NU and Nahdlatul Ulama and how social media platforms play a role in shaping these perceptions. The analysis process involves several key stages, including data cleaning, sentiment analysis, and data classification using the Support Vector Machine (SVM) algorithm.

## 2. Discussion

### a. Data Processing
Before conducting sentiment analysis and classification, the first stage is data cleaning. This stage is crucial for removing irrelevant elements that could interfere with the analysis results. Data cleaning starts with using regular expressions (regex) techniques to remove elements such as usernames, punctuation, emoticons, numbers, and links that are commonly found in tweets. The purpose of this cleaning is to reduce noise in the data so that only relevant information remains for analysis.

After cleaning, case folding is performed to convert all text into lowercase. This ensures uniformity and consistency in the text format, facilitating subsequent analysis. The next step involves tokenization using the NLTK (Natural Language Toolkit) library. Tokenization is the process of breaking the text into individual words called tokens. This step is crucial for analyzing each word in the tweet separately.

After tokenization, slang words are normalized to their formal forms. For example, commonly used slang or abbreviations are converted into standard forms based on the Indonesian lexicon dictionary. The next step is stopword removal. Stopwords are common words in sentences that do not carry significant semantic value, such as "dan" (and), "atau" (or), and "di" (in). Removing stopwords is important for filtering out words that do not contribute to sentiment analysis.

The final stage in data processing is stemming. Stemming is performed using the Sastrawi library, which helps to remove affixes and reduce words to their root forms. For example, the word "berbicara" (speaking) is reduced to "bicara" (speak). This process helps to reduce word redundancy with similar meanings. After stemming, the results are reconstructed into complete sentences. Of the 3,322 initial tweets, after cleaning and processing, 3,110 tweets remain relevant and ready for further analysis.

### b. Sentiment Analysis
After the data is processed, the next step is sentiment analysis. In this study, sentiment analysis is performed using the TextBlob library. TextBlob is a Python library that calculates the sentiment polarity of text. This sentiment polarity indicates how positive, negative, or neutral a piece of text is. Specifically, the polarity is calculated on a scale from -1.0 to +1.0, where -1.0 indicates highly negative sentiment, 0 indicates neutral sentiment, and +1.0 indicates highly positive sentiment.

However, since TextBlob only supports English, the texts originally written in Indonesian need to be translated first. The translation process is carried out using the Google Translate library (googletrans). Each tweet detected in Indonesian is translated into English, and the translation results are stored in a new column called "english". In this way, all texts can be analyzed using TextBlob, even though the original texts are in Indonesian.

Once the translation is completed, sentiment labeling is performed on the "english" column using the sentiment method from TextBlob. Based on the polarity values calculated by TextBlob, tweets are categorized into three sentiment types: positive if the polarity is > 0.0, negative if the polarity is < 0.0, and neutral if the polarity is = 0.0. After labeling, the "english" column is deleted as it is no longer needed. Of the total 3,110 tweets analyzed, the results show that 49.8% of tweets have a neutral sentiment, 33.9% have a positive sentiment, and 16.3% have a negative sentiment. These results provide a general overview of how the public talks about NU and Nahdlatul Ulama on social media.

![Result Centiment Analyze](https://github.com/cholilfayyadl/Text-Preprocessing-Sentiment-Analysis/blob/main/Supplementary%20Files/Centiment%20Result.png)

### c. Sentiment Classification with Support Vector Machine (SVM)
After sentiment analysis, the next step is to classify tweets into sentiment categories using a machine learning algorithm. In this study, the Support Vector Machine (SVM) algorithm is used, which is a popular algorithm for text classification. Before classifying the data, feature weighting is performed using the Term Frequency-Inverse Document Frequency (TF-IDF) method. TF-IDF is used to assign weights to words in tweets based on their frequency in the document and how rare they are across the entire dataset.

After feature weighting, the data is divided into two parts: training data and test data. This division is done with several proportion comparisons, namely 20:80, 30:70, and 40:60, referring to the division between training and test data. The division is done using the train_test_split function from the sklearn library. After the data is divided, the SVM model is trained with a linear kernel to classify sentiment based on the weighted features.

In the first test with a 20:80 ratio, the model achieved an accuracy of 64.24%. Out of 618 test data, 397 predictions were correct, with a precision of 63.49%, recall of 64.24%, and F1 score of 62.55%. The confusion matrix showed that the model could recognize neutral sentiment better than other sentiments, although there were still significant errors in predicting negative and positive sentiments.

In the second test with a 30:70 ratio, the model's accuracy slightly decreased to 59.98%. Out of 927 test data, 556 predictions were correct, with a precision of 59.90%, recall of 59.98%, and F1 score of 56.41%. Although the model's performance decreased, it still performed better in recognizing neutral sentiment, but struggled to differentiate negative sentiment.

In the final test with a 40:60 ratio, the model recorded an accuracy of 61.73%. Out of 1,236 test data, 763 predictions were correct, with a precision of 62.76%, recall of 61.73%, and F1 score of 59.53%. The confusion matrix showed that the model was more accurate in predicting neutral sentiment, but had a higher error rate for negative and positive sentiments.

![Data Confusion20x80](https://github.com/cholilfayyadl/Text-Preprocessing-Sentiment-Analysis/blob/main/Supplementary%20Files/Data%20Test/confusion%20matrix-20%25-80%25.png)

### d. Model Performance Evaluation
Overall, the SVM model used in this study showed a tendency to perform better in recognizing neutral sentiment compared to negative and positive sentiments. This may be because neutral sentiment is more frequently found in the dataset and is easier to predict. However, the model's difficulty in distinguishing between negative and positive sentiment highlights the need for further improvements in data preprocessing, feature selection, and model parameter tuning. Nonetheless, the results of this analysis provide valuable insights into how the public interacts with and forms opinions about NU and Nahdlatul Ulama on Twitter.

## 3. Conclusion
This study has successfully analyzed public sentiment toward NU and Nahdlatul Ulama on X.com using various data analysis techniques, including data cleaning, sentiment analysis using TextBlob, and sentiment classification using the Support Vector Machine (SVM) algorithm. The analysis results show that the majority of conversations on Twitter about NU and Nahdlatul Ulama tend to be neutral, with most tweets having a positive sentiment and a small proportion having a negative sentiment. The SVM model used showed better performance in classifying neutral sentiment, although there were still challenges in distinguishing negative and positive sentiments.

The results of this study provide important insights into public perceptions of NU and Nahdlatul Ulama on social media and demonstrate how sentiment analysis and machine learning techniques can be used to understand public opinion on social media platforms. To improve model performance, further optimization in preprocessing, feature engineering, and model parameters is needed. This study also opens up opportunities for further research that can explore the trends in conversations about religious organizations on social media and their role in shaping public opinion.
