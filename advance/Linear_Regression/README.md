# 1. What is Linear Regression?

**Linear Regression (Hồi quy tuyến tính)** is a **supervised learning algorithm (thuật toán học có giám sát)** used to model the **relationship (mối quan hệ)** between:

- **Independent variables (biến độc lập / features)**
- **Dependent variable (biến phụ thuộc / target)**

It assumes this relationship can be approximated by a **linear function (hàm tuyến tính)**.

---

# 2. Mathematical Formulation

## 2.1 Simple Linear Regression (1 feature)

$$
y = wx + b
$$

Where:

- (y): predicted value (giá trị dự đoán)
- (x): input feature (đặc trưng đầu vào)
- (w): weight / coefficient (trọng số / hệ số)
- (b): bias / intercept (hệ số chặn)

---

## 2.2 Multiple Linear Regression (n features)

$$
y = w_1x_1 + w_2x_2 + \dots + w_nx_n + b
$$

Vector form:

$$
\hat{y} = \mathbf{X}\mathbf{w} + b
$$

---

# 3. Assumptions of Linear Regression (Các giả định)

Linear Regression works **correctly** only when these assumptions hold:

1. **Linearity (Tính tuyến tính)**
   Relationship between X and y is linear

2. **Independence (Tính độc lập)**
   Errors are independent

3. **Homoscedasticity (Phương sai không đổi)**
   Constant variance of errors

4. **Normality of errors (Sai số phân phối chuẩn)**

5. **No multicollinearity (Không đa cộng tuyến)**
   Features are not highly correlated

---

# 4. Loss Function (Hàm mất mát)

## Mean Squared Error (MSE – Sai số bình phương trung bình)

$$
\text{MSE} = \frac{1}{n}\sum (y_i - \hat{y}_i)^2
$$

Why squared?

- Penalizes large errors more
- Differentiable → good for optimization

Other variants:

- **RMSE (Căn MSE)**
- **MAE – Mean Absolute Error (Sai số tuyệt đối trung bình)**

---

# 5. How Do We Find the Best Line?

## 5.1 Normal Equation (Công thức chuẩn)

Closed-form solution:

$$
\mathbf{w} = (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}
$$

### Pros

- Exact solution
- No learning rate

### Cons

- Matrix inversion → slow
- Not scalable for large data

---

## 5.2 Gradient Descent (Hạ gradient)

Iterative optimization:

$$
w := w - \alpha \frac{\partial \text{Loss}}{\partial w}
$$

Where:

- (\alpha): learning rate (tốc độ học)

### Types

- **Batch Gradient Descent**
- **Stochastic Gradient Descent (SGD)**
- **Mini-batch Gradient Descent**

---

# 6. Interpretation of Coefficients

- (w_i):
  Change in y when (x_i) increases by 1 (keeping others constant)

- (b):
  Value of y when all x = 0

This makes Linear Regression **highly interpretable (dễ giải thích)**.

---

# 7. Evaluation Metrics (Chỉ số đánh giá)

## 7.1 R² Score (Hệ số xác định)

$$
R^2 = 1 - \frac{SS_{res}}{SS_{tot}}
$$

- Range: $(-∞, 1]$
- Measures explained variance

⚠️ High R² ≠ good model (can overfit)

---

## 7.2 Adjusted R²

Penalizes unnecessary features.

---

# 8. Overfitting & Underfitting

| Problem                       | Meaning           |
| ----------------------------- | ----------------- |
| **Underfitting (Thiếu khớp)** | Model too simple  |
| **Overfitting (Quá khớp)**    | Model too complex |

---

# 9. Regularization (Chuẩn hóa để chống overfitting)

## 9.1 Ridge Regression (L2)

$$
\text{Loss} = MSE + \lambda \sum w^2
$$

- Shrinks coefficients
- Does NOT set them to zero

---

## 9.2 Lasso Regression (L1)

$$
\text{Loss} = MSE + \lambda \sum |w|
$$

- Feature selection (chọn đặc trưng)
- Can make coefficients exactly zero

---

## 9.3 Elastic Net

Combination of L1 + L2

---

# 10. Feature Engineering (Xử lý đặc trưng)

- Feature scaling (Chuẩn hóa dữ liệu)

  - Standardization
  - Min-Max scaling

- Polynomial features (Đặc trưng đa thức)
- Interaction terms (Tương tác biến)

⚠️ Polynomial Regression is still **linear regression** (linear in parameters).

---

# 11. When NOT to Use Linear Regression?

Avoid when:

- Relationship is highly nonlinear
- Strong outliers
- Complex interactions
- Non-constant variance

Alternatives:

- Decision Trees
- Random Forest
- Neural Networks

---

# 12. Linear Regression in Machine Learning Pipeline

1. Data collection
2. Data cleaning
3. Feature engineering
4. Train-test split
5. Train model
6. Evaluate
7. Tune (regularization, features)

---

# 13. Typical Interview / Exam Questions

- Why squared loss?
- Difference between Ridge & Lasso?
- What happens when multicollinearity exists?
- Why scale features?
- When does Normal Equation fail?

---

# 14. Summary (Big Picture)

Linear Regression is:

- A **baseline model (mô hình nền tảng)**
- Easy to interpret
- Fast to train
- Foundation for many advanced models

Understanding Linear Regression deeply makes:

- Gradient Descent
- Regularization
- Neural Networks
  much easier to learn later.
