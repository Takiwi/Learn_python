# Tổng quan về Radius Neighbors

Radius Neighbors (hay Radius-based Neighbors) là một thuật toán học máy có giám sát, tương tự như K-Nearest Neighbors (KNN), nhưng thay vì tìm kiếm một số lượng cố định K láng giềng gần nhất, nó tìm kiếm tất cả các điểm dữ liệu nằm trong một bán kính (radius) cố định xung quanh điểm dữ liệu mới.

---

## 1. Cách hoạt động

1.  **Xác định bán kính (radius):** Chọn một giá trị `r` (radius) làm ngưỡng khoảng cách.
2.  **Tính khoảng cách:** Từ một điểm dữ liệu mới, tính khoảng cách đến tất cả các điểm trong tập dữ liệu huấn luyện.
3.  **Tìm láng giềng:** Thu thập tất cả các điểm dữ liệu nằm trong phạm vi bán kính `r` đã cho.
4.  **Thực hiện dự đoán:**
    *   **Đối với bài toán Phân loại:** Điểm dữ liệu mới được gán vào lớp **phổ biến nhất** trong số các láng giềng tìm được.
    *   **Đối với bài toán Hồi quy:** Giá trị dự đoán là **trung bình** (hoặc trung vị) của các giá trị của các láng giềng tìm được.

---

## 2. Ưu điểm và Nhược điểm

### Ưu điểm

*   **Ổn định hơn với dữ liệu có mật độ không đồng đều:** Không giống như KNN, nơi mà `K` láng giềng có thể rất xa nhau ở những vùng dữ liệu thưa thớt, Radius Neighbors đảm bảo rằng các láng giềng luôn nằm trong một phạm vi nhất định.
*   **Có thể loại bỏ nhiễu hiệu quả hơn:** Bằng cách chọn một bán kính phù hợp, có thể bỏ qua các điểm quá xa hoặc nhiễu.
*   **Không cần chọn K:** Chỉ cần chọn `radius`, có thể trực quan hơn trong một số trường hợp.

### Nhược điểm

*   **Nhạy cảm với việc lựa chọn bán kính:** Việc chọn `r` quá lớn hoặc quá nhỏ có thể ảnh hưởng lớn đến hiệu suất.
    *   `r` quá lớn: có thể bao gồm quá nhiều điểm không liên quan, dẫn đến overgeneralization.
    *   `r` quá nhỏ: có thể không tìm thấy đủ láng giềng (hoặc không tìm thấy điểm nào), đặc biệt ở vùng dữ liệu thưa thớt.
*   **Vấn đề với "không tìm thấy láng giềng":** Nếu không có điểm dữ liệu nào nằm trong bán kính `r` thì không thể đưa ra dự đoán.
*   **Chi phí tính toán cao:** Tương tự KNN, cần tính toán khoảng cách đến tất cả các điểm dữ liệu trong tập huấn luyện.
*   **Lời nguyền số chiều (Curse of Dimensionality):** Hiệu suất giảm khi số chiều dữ liệu tăng cao.

---

## 3. So sánh với KNN

| Đặc điểm           | K-Nearest Neighbors (KNN)                     | Radius Neighbors (RN)                         |
| :----------------- | :-------------------------------------------- | :-------------------------------------------- |
| **Tiêu chí tìm láng giềng** | Số lượng `K` láng giềng gần nhất            | Tất cả láng giềng trong bán kính `r`           |
| **Tham số chính**  | `K` (số lượng láng giềng)                      | `r` (bán kính)                               |
| **Dự đoán ở vùng thưa thớt** | Luôn tìm `K` láng giềng (có thể rất xa) | Có thể không tìm thấy láng giềng nào hoặc tìm thấy ít  |
| **Độ ổn định**     | Kém ổn định hơn ở vùng mật độ không đều      | Ổn định hơn ở vùng mật độ không đều           |
| **Độ phức tạp**    | Tính toán khoảng cách đến `K` điểm           | Tính toán khoảng cách đến tất cả điểm trong `r` |

---

## 4. Ứng dụng

Radius Neighbors được sử dụng trong các trường hợp tương tự như KNN, đặc biệt khi cần kiểm soát chặt chẽ hơn về khoảng cách vật lý của các láng giềng. Nó có thể hữu ích trong các bài toán yêu cầu các dự đoán cục bộ và khi mật độ dữ liệu có sự biến động lớn.
