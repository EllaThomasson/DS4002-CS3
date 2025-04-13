Map of documentation
DATA -- email_spam.csv, preprocessed_data.csv, Data Appendix.pdf

OUTPUT -- evaluation_metrics.png, LF_confusion_matrix.png, RF_confusion_matrix.png

SCRIPTS -- preprocessing_and_analysis.ipynb, more_EDA.ipynb, model_building.ipynb

README.md

LICENSE.md

Instructions for reproducing results
Access 'email_spam.csv' via DATA folder.
The variable we are trying to classify is 'type'. The remaining variables will be eventually eliminated from the data set after preprocessing.
Preprocessing:

Remove all instances of \n from 'text'
Count all instances of punctuation in 'text' that indicate the end of a sentence, store as 'text_sentences'
Remove all punctuation from 'text' and make everything lowercase
Split 'text' on spaces to obtain a list of words for each email
Count number of words per email in 'text', store as 'text_words'
Remove words in 'text' that occurred >50 times
Save a series including words occurring in 'text' between 10 and 50 times
Add dummy variables representing presence of each word in the series back into the original data set
Repeat steps 5-7 with 'title'
Remove words in 'title' that occurred >10 times
Save a series including words occurring in 'title' between 2 and 10 times
Add dummy variables representing presence of each word in the series back into the original data set
Drop 'text' and 'title' columns from the data set
Random Forest model:

Set y as 'type' and X as all other variables in the data set
Define the pipeline:
Initialize scaler to standardize all predictors to be centered at 0
Perform PCA with n_components set to 0.8
Initialize Random Forest Classifier and set a random state
Perform 5-fold cross validation on the pipeline with scoring set to accuracy
Use cross validation prediction to predict the y values
Calculate accuracy, precision, recall, f1, ROC, and AUC metrics
Fit the pipeline on the entire data set to get the final model and PCA information
Create a confusion matrix to visualize the results
Logistic Regression model:

Set y as 'type' and X as all other variables in the data set
Define the pipeline:
Initialize scaler to standardize all predictors to be centered at 0
Perform PCA with n_components set to 0.8
Initialize Logistic Regression and set a random state
Perform 5-fold cross validation on the pipeline with scoring set to accuracy
Use cross validation prediction to predict the y values
Calculate accuracy, precision, recall, f1, ROC, and AUC metrics
Fit the pipeline on the entire data set to get the final model and PCA information
Create a confusion matrix to visualize the results
