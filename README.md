
### **Data Preparation and Model Evaluation**

#### **Data Extraction and Cleaning**

The sentence\_text column from the dataset was extracted and converted into a list of sentences using the following code:

sentences \= df\['sentence\_text'\].tolist()

This conversion was necessary to facilitate further processing and analysis. Notably, no additional cleaning steps were applied at this stage to preserve the raw structure of the text data.

#### **Data Splitting**

To evaluate the model's performance effectively and avoid overfitting, the dataset was split into training and testing sets. This step is critical for assessing the model's ability to generalize to unseen data. The splitting was performed using the `train_test_split` function from the `sklearn.model_selection` module, with an 80/20 split ratio. 

from sklearn.model\_selection import train\_test\_split

\# Split into train and test sets (80% training, 20% testing)  
train\_sentences, test\_sentences \= train\_test\_split(sentences, test\_size=0.2, random\_state=42)

\# Check sizes of the resulting sets  
print(f"Training sentences: {len(train\_sentences)}")  
print(f"Testing sentences: {len(test\_sentences)}")

#### **Model Evaluation**

To evaluate the performance of the model, two functions were implemented to calculate perplexity—one for the training dataset and one for the testing dataset. Perplexity is a key metric for language models, as it quantifies how well the model predicts the next word. Lower perplexity values indicate better model performance.  
The functions were designed to compute perplexity for both datasets, allowing for a comprehensive comparison of the model's performance on seen (training) and unseen (testing) data. This approach ensures that the model's generalization capability is thoroughly assessed.

#### **Additional Cleaning Scenarios**

To explore the impact of text preprocessing on the model's performance, two additional cleaning scenarios were tested:

1. **Lemmatization with Stop Word Removal**:  
   

In this case, the text was lemmatized (reducing words to their base forms) and stop words (e.g., "is", "the", "and") were removed. This approach is often used in tasks like topic modeling or information retrieval, where the focus is on identifying key concepts rather than grammatical structure.

**Interpretation**: For a next-word recommender or word expectation model, this approach is not ideal. Stop words are essential for maintaining the grammatical flow of sentences, and their removal can disrupt the context needed for accurate predictions. Additionally, lemmatization can obscure the specific forms of words that users are likely to type next (e.g., "summarizing" vs. "summarize"), leading to less accurate recommendations.

2. **Lemmatization without Stop Word Removal**:  
   

In this case, the text was lemmatized, but stop words were retained. This approach preserves the grammatical structure of sentences while reducing words to their base forms.

**Interpretation**: While retaining stop words helps maintain context, lemmatization can still be problematic for next-word prediction. Users often type specific word forms (e.g., "running" instead of "run"), and lemmatization may lead to predictions that do not match the user's intent. This can reduce the model's effectiveness in real-world applications.

### **Graphical User Interface (GUI) Implementation**

As part of the project requirements, a Graphical User Interface (GUI) was developed to visualize and interact with the results of the next-word recommendation model. The GUI provides a user-friendly way to input text and receive real-time predictions for the next word, enhancing the usability and accessibility of the model.  
The GUI was implemented using Python and is included in a separate file named `gui.py`, which will be uploaded alongside this report in a zip file. The interface allows users to:

1. Input a sentence or phrase.  
2. View the model's predicted next word(s) in real-time.  
3. Interact with the model in an intuitive and visually appealing manner.
