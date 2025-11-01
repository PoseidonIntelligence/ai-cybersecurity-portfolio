# AI Spam Detection  
This project implements an email spam detection system using machine learning to classify incoming messages as spam or ham. It demonstrates data preprocessing, feature engineering, model selection, and evaluation metrics.  

## Project Overview  
- **Objective**: Build a classifier that can automatically distinguish spam from legitimate emails. This is crucial for reducing phishing attempts and unwanted marketing.  
- **Methodology**: Use natural language processing to clean and tokenize text, extract features, and train ML models like Naive Bayes, Support Vector Machines, or neural networks. Evaluate performance with metrics like accuracy, precision, recall, F1‑score and ROC‑AUC ([github.com](https://github.com/Apaulgithub/oibsip_taskno4)).  
- **Dataset**: Use a public email dataset (e.g., Enron or SpamAssassin) containing labeled messages. Preprocess by removing stop words and punctuation, and convert to numerical vectors via techniques such as TF‑IDF or word embeddings ([www.geeksforgeeks.org](https://www.geeksforgeeks.org/nlp/detecting-spam-emails-using-tensorflow-in-python/)).  

## Setup  
1. Clone this repository and navigate to the `ai-spam-detection` directory.  
   ```  
   git clone https://github.com/PoseidonIntelligence/ai-cybersecurity-portfolio.git  
   cd ai-cybersecurity-portfolio/ai-spam-detection  
   ```  
2. Install Python dependencies (e.g., pandas, scikit‑learn, TensorFlow) using pip:  
   ```  
   pip install -r requirements.txt  
   ```  
3. Run the training script to train the model on the dataset:  
   ```  
   python train_spam_classifier.py  
   ```  

## Example Usage  
Here's a simplified Python example using scikit‑learn's Multinomial Naive Bayes to classify new emails.  
```python  
# Import necessary libraries  
import pandas as pd  
from sklearn.model_selection import train_test_split  
from sklearn.feature_extraction.text import TfidfVectorizer  
from sklearn.naive_bayes import MultinomialNB  
from sklearn.metrics import accuracy_score  

# Load dataset of emails and labels  
data = pd.read_csv('emails.csv')  # 'text' and 'label' columns  

# Split dataset into training and test sets  
X_train, X_test, y_train, y_test = train_test_split(data['text'], data['label'], test_size=0.2, random_state=42)  

# Convert text to TF-IDF features  
vectorizer = TfidfVectorizer(stop_words='english')  
X_train_vec = vectorizer.fit_transform(X_train)  
X_test_vec = vectorizer.transform(X_test)  

# Train the Naive Bayes classifier  
classifier = MultinomialNB()  
classifier.fit(X_train_vec, y_train)  

# Predict on test data  
y_pred = classifier.predict(X_test_vec)  

# Evaluate accuracy  
acc = accuracy_score(y_test, y_pred)  
print(f"Model accuracy: {acc:.2%}")  
```  
This script reads a dataset of emails, splits them into training and test sets, vectorizes the text using TF‑IDF, trains a Naive Bayes classifier, and computes the accuracy. In a real deployment, you would save the trained model and use it to classify incoming messages in your mail pipeline.  

## Real‑World Scenario  
Imagine a corporate mail server that processes thousands of messages every day. By integrating this spam detection model, the server can filter spam before it reaches employees’ inboxes. This reduces phishing risks and saves time spent sorting unwanted mail.  

## Fun Fact  
The term **“spam”** for unsolicited messages comes from a Monty Python sketch where a restaurant offers a menu full of Spam canned meat. The repetitive chorus of “Spam, Spam, Spam” is analogous to how unwanted emails flood our inboxes.  

## Future Directions  
As AI advances, spam detection systems are moving beyond simple text features toward transformers and deep learning models that understand context and semantics. Future research might incorporate federated learning to train spam filters across multiple organizations without sharing sensitive data, enhancing privacy and adaptability. 
