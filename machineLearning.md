https://www.geeksforgeeks.org/machine-learning/machine-learning-interview-questions/

https://adilshamim8.medium.com/65-machine-learning-interview-questions-2025-2fde3a358dc9

1.  What do you understand by Machine Learning (ML) and how does it differ from artificial intelligence (AI) and Data Science?
 algorithms to identify patterns from data -> prediction and decision

2. What is overfitting and underfitting in machine learning and how can it be avoided?
overfitting -> high accuracy in training data, poor performance in test data
not only learns the true patterns in the training data but aslo memorizes the noise or random fluctuations.
early stop -> even the training accuracy still increasing
Regularization -> L2, l1
Cross-Validation -> k-fold validation
dropout 
simpler moder
underfitting -> too simple not capture the underlying patterns in the data, poor accuracy in train and test data
use a more complex model
add relavent features
reduce regularization
train longer

3. What is Regularization?
 reduce the model complexity and prevent overfitting by adding a penalty term to the loss function.
 L1, L2, elastic net(l1 + l2), dropout(neural network)

4. Explain Lasso and Ridge Regularization. How do they help in Elastic Net Regularization?
L1 -> absolute value of the model's weights
L2 -> the square of the model's weights
elastic net -> l1 + l2 especially the features are correlated

5. What are different Model Evaluation Techniques in Machine Learning?
 -> modle to assess how  well it perfoms on unseen data
test-train-split
cross-validation
confusion matrix
Accuracy: Proportion of correct predictions over total predictions.
Precision: Here correct positive predictions are divided by Total predicted positives.
Recall (Sensitivity): Here correct positive predictions are divided by Total actual positives.
F1-Score: Harmonic mean of precision and recall. It balances precision and recall.
ROC Curve & AUC: Measures model’s ability to distinguish between classes. Here AUC is area under the ROC curve.
Loss Functions (for Regression/Classification): Quantifies prediction error to optimize model. It can include: Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), etc.

6. Explain Confusion Matrix.
                    predicted positive          predicted negative
actual positive     TP                              FN
actual negative     FP                              TN

used in metrics like Accuracy, Precision, Recall, F1-Score

7. What is the difference between precision and recall? How F1 combines both?

precison = TP / (TP + FP)
Example: In spam detection, high precision means most emails marked as spam are truly spam.

Recall = TP / (Tp  + FN)
Example: In disease detection, high recall means most sick patients are correctly identified.

F1-score = 2 * (precision * recall) / (precision + recall)



