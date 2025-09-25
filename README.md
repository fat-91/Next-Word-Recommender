# Next-Word Recommendation System with GUI

This project implements a **next-word recommender system** designed to predict the most likely next word in a given sentence or phrase.  
The system leverages natural language processing (NLP) techniques to train and evaluate a language model, with a particular focus on **perplexity** as the evaluation metric.  
A **Graphical User Interface (GUI)** is also included to allow users to interact with the model in real time, making it both practical and user-friendly.

---

##  Data Preparation and Model Evaluation

### Data Extraction and Cleaning
The `sentence_text` column from the dataset was extracted and converted into a list of sentences.  

This conversion was necessary to facilitate further processing and analysis. Notably, no additional cleaning steps were applied at this stage in order to preserve the raw structure of the text data.

---

### Data Splitting
To evaluate the model's performance effectively and avoid overfitting, the dataset was split into **training** and **testing** sets.  
This step is critical for assessing the model's ability to generalize to unseen data.  

The splitting was performed using the `train_test_split` function from the `sklearn.model_selection` module, with an **80/20 split ratio**.

---

### Model Evaluation
To evaluate performance, two functions were implemented to calculate **perplexity**—one for the training dataset and one for the testing dataset.  

- **Perplexity** is a key metric for language models, quantifying how well the model predicts the next word.  
- Lower perplexity values indicate better predictive performance.  

This approach ensures that the model’s performance is measured on both seen (**training**) and unseen (**testing**) data, providing a clear view of its **generalization capability**.

---

##  Additional Cleaning Scenarios
To explore the impact of preprocessing on the model’s performance, two additional cleaning scenarios were tested:

### 1. Lemmatization with Stop Word Removal
- **Approach**: The text was lemmatized (reducing words to their base form), and stop words (e.g., "is", "the", "and") were removed.  
- **Interpretation**:  
  - This is not ideal for a next-word prediction model.  
  - Stop words are essential for maintaining grammatical flow.  
  - Removing them disrupts context, while lemmatization may obscure natural word forms (e.g., "summarizing" vs. "summarize"), reducing prediction accuracy.

### 2. Lemmatization without Stop Word Removal
- **Approach**: The text was lemmatized, but stop words were retained.  
- **Interpretation**:  
  - Retaining stop words helps preserve grammatical structure.  
  - However, lemmatization still alters word forms (e.g., "running" → "run"), which can lead to predictions that don’t align with real user input.

---

##  Graphical User Interface (GUI)
As part of the project, a **Graphical User Interface (GUI)** was developed to make the model more accessible.  
The GUI allows users to input a sentence and receive real-time predictions for the next word.

- Built in **Python**  
- Implemented in a separate file: `gui.py`  
- Uploaded alongside this report  

### Features:
- Input a sentence or phrase  
- View predicted next word(s) instantly  
- Interact with the model through an intuitive and visually appealing interface  

---

