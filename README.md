# BigData-Sentiment-tAnalysis
### Purpose of the Project

The primary objective of this project is to develop a sentiment analysis model to classify social media posts into positive or negative sentiments. By leveraging natural language processing (NLP) and machine learning techniques, the project aims to automate the analysis of large volumes of social media data, specifically tweets. This automated approach addresses the problem of manually analyzing social media data, which is both time-consuming and labor-intensive. The insights derived from sentiment analysis can help businesses, organizations, and individuals understand public opinion on various topics, brands, or events, thereby enabling informed decision-making and timely actions.

### Techniques Used

#### 1. Data Collection and Preprocessing
- *Data Source*: 
  - The sentiment140 dataset, containing 1.6 million tweets annotated as positive (4) or negative (0), was used. This dataset was extracted using the Twitter API.
  
- *Data Cleaning*:
  - *Handling Missing Values*: Addressing incomplete data entries and removing duplicates to prevent biases in the output.
  - *Removing Patterns*: URLs, mentions, and non-alphanumeric characters were removed using regular expressions.
  - *Text Normalization*: Converting text to lowercase and trimming whitespaces to standardize the data.

#### 2. Data Exploration and Visualization
- *Structure Examination*: 
  - Checking the number of rows and columns to understand the dataset’s structure.
  - *Distribution Analysis*: Counting the number of positive and negative tweets to ensure a balanced dataset.
  
- *Visualization*:
  - *Bar Chart*: Visualizing the sentiment distribution.
  - *Word Cloud*: Displaying the most frequent words in each sentiment category to understand common terms associated with positive and negative sentiments.

#### 3. Feature Engineering
- *Tokenization*:
  - Using RegexTokenizer to split text into individual words.
  
- *Stop Words Removal*:
  - Using StopWordsRemover to eliminate common words that do not contribute significant meaning to the text (e.g., "the", "and").
  
- *Vectorization*:
  - Using CountVectorizer to convert the filtered words into numerical features, creating a feature vector representation of the text data.
  
- *Label Encoding*:
  - Using StringIndexer to convert sentiment labels from their original format to numerical format for model training.

#### 4. Model Development
Three machine learning models were used for sentiment analysis:

- *Support Vector Machine (SVM)*:
  - Applied twice: once with stemming (reducing words to their base form) and once without stemming.
  - Results showed better accuracy without stemming and shorter execution time.
  
- *Logistic Regression*:
  - Also applied twice: once with stemming and once without stemming.
  - Both versions had similar accuracy, but the non-stemming model had better execution time.
  
- *Naive Bayes*:
  - Applied twice: once with stemming and once without stemming.
  - The model without stemming achieved the highest accuracy and had the shortest execution time.

#### 5. Model Training and Evaluation
- *Data Splitting*:
  - The dataset was split into training (80%) and testing (20%) sets using a fixed seed for reproducibility.
  
- *Pipeline Construction*:
  - A pipeline was created using the PySpark ML Pipeline API to encapsulate preprocessing and modeling steps.
  
- *Model Training*:
  - The pipeline was trained on the training data using the fit() method.
  
- *Model Evaluation*:
  - Predictions were made on the testing data using the trained model.
  - Performance was evaluated using the MulticlassClassificationEvaluator, measuring accuracy as the metric.

#### 6. Model Deployment
- *Model Saving*:
  - The trained model was saved to disk using the save() method.
  
- *New Data Classification*:
  - The saved model was loaded using PipelineModel.load().
  - New text data was processed using the same cleaning and preprocessing steps.
  - Sentiment predictions were made using the loaded model.

### Results and Analysis

The evaluation results showed that:

- *Naive Bayes without Stemming*: Achieved the highest accuracy (77.21%) with a runtime of 3 minutes.
- *Support Vector Machine without Stemming*: Achieved an accuracy of 77.16% with a runtime of 5 minutes.
- *Logistic Regression without Stemming*: Achieved an accuracy of 75.98% with a runtime of 5 minutes.
- Models with stemming generally took longer to execute and had slightly lower accuracy compared to their non-stemming counterparts, suggesting that stemming did not significantly improve performance for this sentiment analysis task.
