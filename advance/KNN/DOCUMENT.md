# 1. KNN là gì?

**K-Nearest Neighbors (KNN)** là một thuật toán **Machine Learning có giám sát (supervised learning)**, dùng cho:

- **Classification (phân loại)**
- **Regression (hồi quy)**

👉 Ý tưởng:

> Một điểm dữ liệu mới sẽ được gán nhãn dựa trên **K điểm gần nó nhất** trong tập dữ liệu huấn luyện.

📌 KNN là **instance-based / lazy learning**

- Không học ra mô hình
- Chỉ lưu toàn bộ dữ liệu
- Dự đoán khi có dữ liệu mới

---

# 2. Trực giác (Intuition)

Giả sử:

- Bạn có dữ liệu người dùng: **tuổi – thu nhập – nghề**
- Một người mới xuất hiện
  ➡️ Hỏi: _“Người này giống ai nhất?”_

👉 Nhìn vào **K người gần nhất**

- Classification → bỏ phiếu (majority vote)
- Regression → lấy trung bình

---

# 3. Quy trình hoạt động của KNN

1. Chọn **K** (số hàng xóm)
2. Tính **khoảng cách** từ điểm mới đến tất cả điểm train
3. Sắp xếp theo khoảng cách
4. Lấy **K điểm gần nhất**
5. Dự đoán:

   - Classification → nhãn phổ biến nhất
   - Regression → trung bình (hoặc trung bình có trọng số)

---

# 4. Các loại khoảng cách (Distance Metrics)

### 4.1 Euclidean Distance (phổ biến nhất)

[
d(x,y)=\sqrt{\sum (x_i - y_i)^2}
]

✔️ Dữ liệu liên tục
❌ Nhạy với scale

---

### 4.2 Manhattan Distance

[
d(x,y)=\sum |x_i - y_i|
]

✔️ Khi dữ liệu có dạng lưới (grid)

---

### 4.3 Minkowski Distance

[
d(x,y)=\left(\sum |x_i-y_i|^p\right)^{1/p}
]

- p=1 → Manhattan
- p=2 → Euclidean

---

### 4.4 Cosine Distance

[
1 - \cos(\theta)
]

✔️ Text, NLP
✔️ Không quan tâm độ lớn, chỉ quan tâm hướng

---

# 5. KNN cho Classification

### Cách dự đoán

- Lấy **K điểm gần nhất**
- Đếm số lượng mỗi class
- Class nào nhiều nhất → kết quả

📌 Có thể dùng **weighted voting**:

- Điểm càng gần → trọng số càng cao

---

# 6. KNN cho Regression

### Cách dự đoán

- Trung bình giá trị của K neighbors
- Hoặc:
  [
  \hat{y}=\frac{\sum w_i y_i}{\sum w_i}
  ]

---

# 7. Chọn K như thế nào?

| K     | Hệ quả       |
| ----- | ------------ |
| K nhỏ | Overfitting  |
| K lớn | Underfitting |

📌 Thực tế:

- Dùng **cross-validation**
- Thường thử K = 3,5,7,9,…

---

# 8. Chuẩn hóa dữ liệu (RẤT QUAN TRỌNG)

KNN **phụ thuộc hoàn toàn vào khoảng cách**
➡️ **BẮT BUỘC scale dữ liệu**

### Các cách scale:

- Min-Max Scaling
- Standardization (Z-score)

❌ Không scale → feature lớn lấn át feature nhỏ

---

# 9. Độ phức tạp (Complexity)

### Training

- O(1) (chỉ lưu dữ liệu)

### Prediction

- O(n × d)

  - n: số mẫu
  - d: số feature

📌 Dataset lớn → chậm

---

# 10. Ưu điểm & Nhược điểm

### ✅ Ưu điểm

- Dễ hiểu, dễ cài
- Không cần training
- Hoạt động tốt với dataset nhỏ

### ❌ Nhược điểm

- Rất chậm với dataset lớn
- Tốn bộ nhớ
- Nhạy với noise
- Nhạy với scale

---

# 11. So sánh KNN với thuật toán khác

| Thuật toán          | Đặc điểm            |
| ------------------- | ------------------- |
| KNN                 | Dựa vào khoảng cách |
| Logistic Regression | Linear              |
| SVM                 | Tìm hyperplane      |
| Decision Tree       | Rule-based          |
| Naive Bayes         | Xác suất            |

---

# 12. KNN trong scikit-learn (Python)

```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

knn = KNeighborsClassifier(
    n_neighbors=5,
    metric='euclidean'
)
knn.fit(X_scaled, y)

y_pred = knn.predict(X_test_scaled)
```

---

# 13. Các biến thể của KNN

- **Weighted KNN**
- **Radius Neighbors**
- **Approximate KNN**
- **KD-Tree / Ball Tree**

---

# 14. Khi nào nên dùng KNN?

✔ Dataset nhỏ – trung bình
✔ Feature số
✔ Không cần model interpretability cao
❌ Dataset rất lớn
❌ Feature nhiều chiều (curse of dimensionality)

---

# 15. Các vấn đề thường gặp

- Curse of dimensionality
- Data imbalance
- Noise
- Feature irrelevant

---

# 16. Lộ trình học tiếp theo

Nếu bạn học ML bài bản:

1. KNN
2. Linear / Logistic Regression
3. Naive Bayes
4. Decision Tree
5. Random Forest
6. SVM
