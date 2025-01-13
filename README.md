# Stay or Stray: Forecasting Credit Card Customer Loyalty

## Objective

A bank is experiencing a notable decline in credit card user retention, crucially affecting its revenue derived from numerous associated fees. My objective is to perform an in-depth analysis of customer data and construct a sophisticated classification model. This model should proficiently predict which customers are inclined to terminate their credit card services and elucidate the underlying reasons for such behavior. These insights will empower the organization to strategically enhance its service offerings and implement effective customer retention strategies.

## Topics
- Pandas
- Numpy
- Matplotlib
- Exploratory Data Analysis (EDA)
- Data Cleaning
- Inferential Statistics
- Correlation and Relationships
- Model Building (Ensemble Methods)

## Model Selection and Performance Enhancement Techniques
Initial Experimentation

The initial models used were:

- Bagging Classifier
- Random Forest
- Decision Tree
- AdaBoost
- Gradient Boost
- XGBoost
- Logistic Regression

Initially, no hyperparameters were tuned, and the models were evaluated in their default configurations to observe baseline performance. 
Among these, AdaBoost and Logistic Regression demonstrated superior generalization on the validation set.

### Hyperparameter Tuning with GridSearchCV
To enhance model performance, GridSearchCV was applied to fine-tune hyperparameters for all models except XGBoost. 

The tuned models included:

- Bagging Classifier
- Bagging Classifier with base_estimator=LogisticRegression
- Random Forest (with and without class weights)
- AdaBoost
- Gradient Boost


### Addressing Class Imbalance
Class imbalance was tackled using two approaches:

- Synthetic Minority Oversampling Technique (SMOTE): Synthetic data points were generated for the minority class.
- Random Undersampling: Data from the majority class was undersampled to balance the dataset.

These techniques were applied to evaluate their impact on model performance.

### Hyperparameter Tuning with RandomizedSearchCV
For the best-performing models identified earlier, RandomizedSearchCV was utilized for further optimization. 

Models tested included:

- Decision Tree (tuned)
- Decision Tree With oversampled data
- Decision Tree With undersampled data
- Bagging Classifier
- AdaBoost Classifier
- Ada Boost With oversampled data

### Final Model Selection Process
Models were evaluated based on accuracy, precision, recall, and F1-score. 

The following models stood out for their performance:

- Decision Tree using RandomizedSearchCV with undersampled data
- AdaBoost using RandomizedSearchCV with oversampled data

### Final Model Choice
The AdaBoost Classifier using RandomizedSearchCV with oversampled data was chosen as the final model due to its:

- High recall on the validation set (94.71%), indicating strong performance in minimizing false negatives.
- Robust generalization without overfitting to the training data.
- Excellent precision and F1-score, consistent with training metrics.

The best model identified was **AdaBoost Classifier using RandomizedSearchCV with oversampled data**, which achieved a recall score of 93.59% on the test dataset.

### Practical Impact
This model is particularly suitable for scenarios requiring a strong recall metric, such as predicting customer churn. It ensures:

- Minimal false negatives, meaning customers unlikely to churn are rarely misclassified.
- Reliable performance on unseen test/production data.
