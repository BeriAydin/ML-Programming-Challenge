# Machine Learning Challenge - Exam HT24

## 📌 Overview
This project is part of the HT24 Machine Learning exam challenge. The task is to train a classifier using a labeled dataset and predict the labels for an evaluation dataset. The accuracy of our predictions on the held-out evaluation set determines our final score in the challenge.

## 📂 Dataset
- **TrainOnMe.csv**: Labeled training data with features `x1, x2, ..., x13` and labels `y`.
- **EvaluateOnMe.csv**: Unlabeled test dataset for inference.
- **EvaluationGT.csv**: Ground truth labels (released after the exam for self-evaluation).

## 🏗️ Project Structure
├── main.py           # Main script for training & evaluation
├── TrainOnMe.csv     # Training dataset
├── EvaluateOnMe.csv  # Evaluation dataset
├── labels.txt        # Predicted labels output (for submission)
├── README.md         # This document


## 📊 Model Selection Strategy
After testing multiple classifiers, **Random Forest with PCA** was selected as the best model based on cross-validation accuracy.

### **Preprocessing & Feature Engineering**
- **One-Hot Encoding**: Applied to categorical features.
- **Standard Scaling**: Applied before PCA.
- **PCA**: Applied to numerical features to remove redundancy and improve model performance.

### **Classifiers Evaluated**
| Model                | Accuracy  |
|----------------------|----------|
| Random Forest (PCA) | **84.82%** |
| Decision Tree (PCA) | 77.52% |
| Logistic Regression (PCA, 10 components) | 58.84% |
| SVM (PCA, 10 components) | 65.61% |
| kNN (PCA, 7 components) | 56.66% |
| Naïve Bayes (No PCA) | 66.21% |

Final Model: **Random Forest with PCA**, achieving an accuracy of **84.82%** on the held-out dataset.

## 🔧 Customization
If you want to experiment with different models, modify `main.py`:
```python
classifiers = {
    "Random Forest": (RandomForestClassifier(), True, None),
    "SVM": (SVC(), True, 10),
    "kNN": (KNeighborsClassifier(), True, 7)
}
```

## 🎯 Conclusion
This project successfully applied **machine learning techniques** to classify data and achieve a accuracy of **84.82%**. The best-performing model Random Forest was selected based on **cross-validation scores**.