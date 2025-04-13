## Map of documentation
**DATA** -- email_spam.csv, preprocessed_data.csv

**OUTPUT** -- evaluation_metrics.png, LF_confusion_matrix.png, RF_confusion_matrix.png

**SCRIPTS** -- preprocessing_and_analysis.ipynb, more_EDA.ipynb, model_building.ipynb

ProjectMotivationArticle

## Instructions for reproducing results
1. Access 'email_spam.csv' via DATA folder. 
2. The variable we are trying to classify is 'type'. The remaining variables will be eventually eliminated from the data set after preprocessing.
   
_Preprocessing:_

3. Remove all instances of \n from 'text'
4. Count all instances of punctuation in 'text' that indicate the end of a sentence, store as 'text_sentences'
5. Remove all punctuation from 'text' and make everything lowercase
6. Split 'text' on spaces to obtain a list of words for each email
7. Count number of words per email in 'text', store as 'text_words'
8. Remove words in 'text' that occurred >50 times
9. Save a series including words occurring in 'text' between 10 and 50 times
10. Add dummy variables representing presence of each word in the series back into the original data set
11. Repeat steps 5-7 with 'title'
12. Remove words in 'title' that occurred >10 times
13. Save a series including words occurring in 'title' between 2 and 10 times
14. Add dummy variables representing presence of each word in the series back into the original data set
15. Drop 'text' and 'title' columns from the data set
    
_Random Forest model:_

16. Set y as 'type' and X as all other variables in the data set
17. Define the pipeline:
- Initialize scaler to standardize all predictors to be centered at 0
- Perform PCA with n_components set to 0.8
- Initialize Random Forest Classifier and set a random state
18. Perform 5-fold cross validation on the pipeline with scoring set to accuracy
19. Use cross validation prediction to predict the y values
20. Calculate accuracy, precision, recall, f1, ROC, and AUC metrics
21. Fit the pipeline on the entire data set to get the final model and PCA information
22. Create a confusion matrix to visualize the results
    
_Logistic Regression model:_

23. Set y as 'type' and X as all other variables in the data set
24. Define the pipeline:
- Initialize scaler to standardize all predictors to be centered at 0
- Perform PCA with n_components set to 0.8
- Initialize Logistic Regression and set a random state
25. Perform 5-fold cross validation on the pipeline with scoring set to accuracy
26. Use cross validation prediction to predict the y values
27. Calculate accuracy, precision, recall, f1, ROC, and AUC metrics
28. Fit the pipeline on the entire data set to get the final model and PCA information
29. Create a confusion matrix to visualize the results
