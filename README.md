# Hyperparamter-Turning
Value of K for KNN vs.  Cross-Validated Accuracy

## Author
Jason Carpenter

## Overview
This project demonstrates hyperparameter tuning using the Iris dataset from `sklearn.datasets`. The goal is to determine the optimal value of `k` for the K-Nearest Neighbors (KNN) algorithm using cross-validation and GridSearchCV.

## Dataset
The Iris dataset is loaded from `sklearn.datasets`.

## Methodology
1. **Load the Iris Dataset**:
   - The dataset is loaded using `sklearn.datasets.load_iris()`.

2. **Cross-Validation**:
   - We use `scikit-learn`'s `cross_val_score` with `cv=10`, which means 10-fold cross-validation.
   - Note: We do not use the following book codes from page 619:
     ```python
     kfold = KFold(n_splits=10, random_state=11, shuffle=True)
     scores = cross_val_score(estimator=knn, X=iris.data, y=iris.target, cv=kfold)
     ```
   - Instead, we use:
     ```python
     k_range = range(1, 31)
     for k in k_range:
         knn = KNeighborsClassifier(n_neighbors=k)
         scores = cross_val_score(knn, X, y, cv=10)
     ```

3. **Determine Optimal `k`**:
   - The optimal `k` value is determined by evaluating the cross-validated accuracy for `k` values ranging from 1 to 31.
   - Two graphs are plotted:
     - `knn-1.jpg`: Value of K for KNN vs. Cross-Validated Accuracy
     - `knn2-1.jpg`: Another relevant plot for analysis

4. **GridSearchCV**:
   - GridSearchCV is used to confirm that `k=13` is the optimal parameter.

## Results
- The optimal value of `k` is determined and visualized through the plots.
- GridSearchCV confirms `k=13` as the optimal parameter.

## License
- This project is licensed under the MIT License
