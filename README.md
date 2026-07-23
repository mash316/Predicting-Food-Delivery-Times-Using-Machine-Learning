Project title:
Predicting Food Delivery Times Using Machine Learning
Semester : Summer2025
Department: CSE
Course Code : CSE422
Section : 02
ARTIFICIAL INTELLIGENCE
Group No : 12
ID Name
22101407 Md. Tanvir Haque Shitab
24341171 Masrur Hoque
Table of Contents:
2
Serial Topic Page
1 Introduction 3
2 Dataset description 3-5
3 Dataset pre-processing 5-6
4 Dataset splitting 6
5 Model training & testing 6
6 Model selection/Comparison analysis 6-10
7 Conclusion 11
Introduction
This project focuses on predicting food delivery times based on various influencing
factors such as distance, weather conditions, traffic levels, delivery type, and courier
experience. The aim is to classify whether an order will arrive on time or late using
multiple machine learning approaches. Models applied include Logistic Regression,
Decision Tree, Naive Bayes, and a Neural Network, along with KMeans clustering for
unsupervised learning. The motivation is to improve delivery efficiency, optimize
logistics planning, and enhance customer satisfaction by identifying potential delays in
advance.
Dataset description
Source: Food_delivery_times
Dataset details:
The dataset contains 8 input features:
● Distance_km (quantitative)
● Weather (categorical)
● Traffic_Level (categorical)
● Time_of_Day (categorical)
● Vehicle_Type (categorical)
● Preparation_Time_min (quantitative)
● Courier_Experience_yrs (quantitative)
● Order_ID (identifier, not useful for prediction)
The target feature is Delivery_Speed (categorical: Fast, Average, Slow).
Total Data Points: 1000 rows
This is a classification problem because the output variable (Delivery_Speed) is
categorical.
Encoding Needed for categorical variables like Weather and Traffic_Level(One hot
encoding). So they can be processed by machine learning algorithms.
3
Correlation between features :
The correlation heatmap shows that the strongest relationship is between Distance_km
and Delivery_Speed (0.28), indicating that longer distances are more likely to result in
slower deliveries. Preparation_Time_min also has a slight positive correlation (0.12) with
delivery speed, meaning higher preparation times tend to delay orders.
Courier_Experience_yrs shows a weak negative correlation (–0.06), suggesting that more
experienced couriers usually deliver faster.
Other features, such as Weather, Traffic_Level, and Time_of_Day, have very low
correlations with delivery speed, and correlations among independent features are
minimal. This indicates that multicollinearity is not an issue, which is beneficial for
predictive modeling.
4
Imbalanced Dataset
The bar chart reveals that the dataset is not perfectly balanced in terms of the target
feature Delivery_Speed. The majority of deliveries fall under the “Average” category,
while “Fast” and “Slow” deliveries occur less frequently. This imbalance suggests that
models may become biased toward predicting “Average” delivery unless stratified
sampling or balancing techniques are applied.
Dataset pre-processing
1. Handling Null/ Missing Values: The dataset had some missing values in both
numerical and categorical features.
For numerical columns (Distance_km, Preparation_Time_min, Courier_Experience_yrs),
missing values were replaced with the median to avoid distortion from outliers.
For categorical columns (Weather, Traffic_Level, Time_of_Day, Vehicle_Type), missing
values were replaced with the most frequent category (mode) to preserve the overall
distribution.
5
2. Encoding Categorical Variables: Since machine learning algorithms require
numerical inputs, categorical features were transformed using One-Hot Encoding.
Example: For Weather, categories such as Clear, Rainy, Foggy, Windy were converted
into separate binary columns (Weather_Clear, Weather_Rainy, etc.).
Feature Scaling: To ensure that all features contribute equally to model training,
scaling was applied:
StandardScaler: Used for most models (Logistic Regression, Neural Networks),
transforming features to have mean = 0 and standard deviation = 1.
MinMaxScaler: Applied for Naive Bayes, ensuring values lie in the [0,1] range as
required for probability-based calculations.
Order_ID column was dropped as it was not useful for prediction .
Dataset Splitting
The dataset was split into training and testing sets in an 80:20 ratio. The split was
stratified, ensuring a balanced distribution of the target classes across both sets.
Model training & testing
The following machine learning models were implemented using sklearn:
1. Logistic Regression – used as a baseline classifier with class balancing.
2. Naive Bayes – applied after MinMax scaling to handle categorical-style data.
3. Neural Network – implemented with TensorFlow/Keras for higher accuracy.
4. KMeans Clustering – applied as an unsupervised method to discover groupings in
the dataset.
Model selection/Comparison analysis
The comparison of Logistic Regression, Naive Bayes, and Neural Network models for
predicting delivery speed shows that Logistic Regression achieved the best overall
performance. It had the highest accuracy (81.5%) and the top AUC score (0.94), making
6
it the most reliable model for this dataset. The Neural Network followed closely with an
accuracy of 80.5% and an AUC of 0.93, showing strong predictive power but requiring
more computational resources. Naive Bayes performed the weakest, with an accuracy of
55.0% and an AUC of 0.72, indicating difficulties in distinguishing between delivery
speed classes.
Confusion Matrix:
Logistic Regression
7
Naive Bayes
Neural Network
8
Accuracy comparison:
ROC–AUC Analysis: Logistic Regression achieved the highest AUC (0.94), followed
closely by the Neural Network (0.93), while Naive Bayes performed the weakest with an
AUC of 0.72.
9
Precision, Recall, and F1-Score Comparison: Logistic Regression achieved the best
overall balance with precision 0.81, recall 0.85, and F1-score 0.82. The Neural Network
performed closely with similar values, while Naive Bayes lagged behind with much
lower recall (0.41) and F1-score (0.39).
KMeans Clustering results: KMeans formed three clusters that partially aligned with
the true delivery speed labels. While some overlap exists between classes, the clustering
still revealed meaningful groupings, with centroids capturing the main distributions. This
shows that unsupervised learning can identify patterns, but it is less accurate than
supervised models.
10
Conclusion:
This project aimed to predict food delivery times using factors such as distance,
preparation time, courier experience, weather, and traffic with different machine learning
models. After preprocessing the dataset through handling missing values, encoding
categorical features, and applying scaling, three supervised models Logistic Regression,
Naive Bayes, and Neural Network along with KMeans clustering were evaluated.
Logistic Regression emerged as the most reliable model, offering the best balance across
accuracy, precision, recall, and F1-score. The Neural Network also performed strongly
but required more computational effort, while Naive Bayes struggled due to its
independence assumptions. KMeans revealed some group patterns but was less effective
than supervised methods.
These results highlight the importance of careful model selection in predictive analytics.
Logistic Regression’s robustness makes it well-suited for this task, while Neural
Networks remain a strong alternative. Overall, the project shows how machine learning
can support food delivery services in improving efficiency and customer satisfaction.
11
