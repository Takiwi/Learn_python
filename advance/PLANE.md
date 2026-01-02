# 🧭 ROADMAP HỌC SCIKIT-LEARN (ĐÃ BIẾT NUMPY + PANDAS)

---

## 🔹 GIAI ĐOẠN 0 – Tư duy ML (2–3 ngày)

👉 Cái này cực quan trọng, nhiều người bỏ qua

### Cần hiểu:

- Supervised vs Unsupervised Learning
- Classification vs Regression
- Overfitting / Underfitting
- Train / Validation / Test
- Data Leakage là gì

📌 Output:

- Biết **khi nào dùng thuật toán nào**
- Đọc được pipeline ML

---

## 🔹 GIAI ĐOẠN 1 – Workflow chuẩn sklearn (Tuần 1)

### 1.1 Cấu trúc code ML chuẩn

```python
model = Model()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

### 1.2 Các bước phải nắm

- `train_test_split`
- `.fit()`, `.predict()`, `.score()`

### 1.3 Thực hành

- Iris dataset
- Wine dataset

📌 Thuật toán:

- `LinearRegression`
- `LogisticRegression`

🎯 Output:

> Chạy trơn tru 1 bài ML từ A → Z

---

## 🔹 GIAI ĐOẠN 2 – Preprocessing & Feature (Tuần 2)

### 2.1 Missing values

- `SimpleImputer`

### 2.2 Scaling (rất quan trọng)

- `StandardScaler`
- `MinMaxScaler`

### 2.3 Encoding

- `OneHotEncoder`
- `LabelEncoder` (chỉ dùng cho y)

### 2.4 Feature Selection

- `SelectKBest`
- `VarianceThreshold`

🎯 Bài tập:

- Dataset có cả số + chữ
- So sánh **có scale vs không scale**

---

## 🔹 GIAI ĐOẠN 3 – Thuật toán cốt lõi (Tuần 3)

### 3.1 Classification

- KNN
- SVM
- Decision Tree
- Random Forest

### 3.2 Regression

- Ridge / Lasso
- SVR
- RandomForestRegressor

📌 So sánh:

- Bias vs Variance
- Model đơn giản vs phức tạp

🎯 Output:

> Biết **vì sao model này tốt hơn model kia**

---

## 🔹 GIAI ĐOẠN 4 – Evaluation & Validation (Tuần 4)

### 4.1 Classification metrics

- Accuracy
- Precision / Recall
- F1-score
- Confusion Matrix
- ROC-AUC

### 4.2 Regression metrics

- MAE / MSE / RMSE
- R²

### 4.3 Cross Validation

- `KFold`
- `StratifiedKFold`
- `cross_val_score`

🎯 Output:

> Không còn đánh giá model sai cách ❌

---

## 🔹 GIAI ĐOẠN 5 – Pipeline & Production mindset (Tuần 5)

### 5.1 Pipeline

```python
Pipeline([
  ("scaler", StandardScaler()),
  ("model", LogisticRegression())
])
```

### 5.2 ColumnTransformer

- Numeric pipeline
- Categorical pipeline

📌 Tại sao quan trọng?

- Tránh data leakage
- Deploy được model

🎯 Output:

> Code ML **chuẩn production**

---

## 🔹 GIAI ĐOẠN 6 – Hyperparameter Tuning (Tuần 6)

### 6.1 GridSearchCV

### 6.2 RandomizedSearchCV

📌 Hiểu:

- Hyperparameter vs parameter
- Overfitting khi tuning

🎯 Output:

> Biết tối ưu model đúng cách

---

## 🔹 GIAI ĐOẠN 7 – Mini Projects (BẮT BUỘC)

### Project 1 – Classification

- Predict khách hàng churn
- Spam email
- Titanic survival

### Project 2 – Regression

- House price prediction
- Student score prediction

📌 Yêu cầu:

- EDA (pandas)
- Preprocessing
- Pipeline
- Evaluation
- Report kết quả

---

# 🧠 Cheat Sheet – Học thế nào cho hiệu quả?

✅ 70% thời gian **code**
✅ Luôn hỏi: _"Model này sai ở đâu?"_
❌ Không học deep learning vội

---

# 🚀 Sau khi xong lộ trình này bạn có thể:

- Tự làm ML project
- Hiểu paper ML cơ bản
- Chuyển sang:

  - XGBoost / LightGBM
  - Deep Learning
  - MLOps
