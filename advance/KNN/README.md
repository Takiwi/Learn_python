# Tổng quan về thuật toán K-Nearest Neighbors (KNN)

**K-Nearest Neighbors (KNN)** là một trong những thuật toán học máy đơn giản và dễ hiểu nhất, thuộc nhóm học có giám sát (Supervised Learning). Nó có thể được sử dụng cho cả bài toán **phân loại (Classification)** và **hồi quy (Regression)**.

Ý tưởng cốt lõi của KNN là: _Một đối tượng sẽ được phân loại dựa trên "những người hàng xóm" gần nhất của nó_.

---

## 1. KNN hoạt động như thế nào?

Thuật toán KNN còn được gọi là "lazy learning" (học lười) vì nó không thực sự "học" một mô hình từ dữ liệu huấn luyện. Thay vào đó, nó lưu trữ toàn bộ tập dữ liệu và thực hiện tính toán tại thời điểm dự đoán.

Quy trình dự đoán cho một điểm dữ liệu mới bao gồm các bước sau:

1.  **Chọn số láng giềng (K):** Xác định một số nguyên dương `K`, là số lượng hàng xóm gần nhất sẽ được xem xét.
2.  **Tính khoảng cách:** Tính toán khoảng cách từ điểm dữ liệu mới đến **tất cả** các điểm trong tập dữ liệu huấn luyện. Các độ đo khoảng cách phổ biến bao gồm:
    - **Khoảng cách Euclidean:** Khoảng cách đường chim bay (phổ biến nhất).
    - **Khoảng cách Manhattan:** Khoảng cách theo các trục tọa độ.
    - **Khoảng cách Minkowski:** Dạng tổng quát của Euclidean và Manhattan.
3.  **Tìm K láng giềng gần nhất:** Sắp xếp các khoảng cách đã tính theo thứ tự tăng dần và chọn ra `K` điểm dữ liệu có khoảng cách nhỏ nhất.
4.  **Thực hiện dự đoán:**
    - **Đối với bài toán Phân loại:** Điểm dữ liệu mới sẽ được gán vào lớp **phổ biến nhất** (chiếm đa số) trong số `K` láng giềng.
    - **Đối với bài toán Hồi quy:** Giá trị dự đoán cho điểm dữ liệu mới sẽ là **trung bình** (hoặc trung vị) của các giá trị của `K` láng giềng.

![KNN Visualization](https://upload.wikimedia.org/wikipedia/commons/e/e7/KnnClassification.svg)
_Minh họa: Với K=3, điểm dữ liệu mới (sao) được phân loại là tam giác. Với K=5, nó được phân loại là hình vuông._

---

## 2. Các khái niệm quan trọng

### a. Chọn giá trị K

Việc chọn `K` là rất quan trọng và ảnh hưởng lớn đến kết quả của mô hình:

- **K quá nhỏ:** Mô hình sẽ rất nhạy cảm với nhiễu (noise) và các điểm ngoại lệ. Điều này có thể dẫn đến **overfitting** (mô hình quá khớp với dữ liệu huấn luyện và hoạt động kém trên dữ liệu mới).
- **K quá lớn:** Mô hình có thể bỏ qua các đặc điểm cục bộ và trở nên quá tổng quát. Điều này có thể dẫn đến **underfitting** (mô hình quá đơn giản, không nắm bắt được xu hướng của dữ liệu).

**Làm thế nào để chọn K?**

- **Quy tắc ngón tay cái:** `K` thường được chọn là căn bậc hai của tổng số điểm dữ liệu (`K = sqrt(N)`).
- **Thử nghiệm:** Thử các giá trị `K` khác nhau và chọn giá trị cho kết quả tốt nhất trên tập dữ liệu kiểm thử (validation set).
- **Số lẻ:** Trong các bài toán phân loại nhị phân (2 lớp), `K` thường được chọn là một số lẻ để tránh trường hợp số phiếu bầu bằng nhau.

### b. Chuẩn hóa dữ liệu (Feature Scaling)

KNN rất nhạy cảm với thang đo của các đặc trưng. Nếu một đặc trưng có phạm vi giá trị lớn hơn nhiều so với các đặc trưng khác, nó sẽ lấn át và ảnh hưởng lớn đến kết quả tính toán khoảng cách.

**Ví dụ:** Một đặc trưng là `lương` (từ 10,000 đến 100,000) và một đặc trưng là `tuổi` (từ 20 đến 60). Khoảng cách sẽ bị chi phối bởi `lương`.

Do đó, việc **chuẩn hóa dữ liệu** (ví dụ: đưa tất cả các đặc trưng về cùng một thang đo từ 0 đến 1) trước khi áp dụng KNN là một bước cực kỳ quan trọng.

---

## 3. Ưu điểm và Nhược điểm

### Ưu điểm

- **Đơn giản, dễ hiểu:** Logic của thuật toán rất trực quan.
- **Dễ triển khai:** Không đòi hỏi nhiều công sức để code.
- **Không cần giai đoạn huấn luyện:** Vì là "lazy learning", nó không tốn thời gian để xây dựng mô hình.
- **Linh hoạt:** Dễ dàng áp dụng cho cả bài toán phân loại và hồi quy.

### Nhược điểm

- **Chi phí tính toán cao khi dự đoán:** Phải tính khoảng cách đến tất cả các điểm dữ liệu, làm cho nó chậm với các tập dữ liệu lớn.
- **Cần nhiều bộ nhớ:** Phải lưu trữ toàn bộ tập dữ liệu.
- **Nhạy cảm với các đặc trưng không liên quan:** Các đặc trưng "rác" có thể làm nhiễu kết quả tính khoảng cách.
- **Lời nguyền số chiều (Curse of Dimensionality):** Hiệu suất của KNN giảm đáng kể khi số lượng đặc trưng (số chiều) tăng lên. Trong không gian nhiều chiều, khái niệm "gần" trở nên khó xác định.

---

## 4. Ứng dụng thực tế

KNN được sử dụng trong nhiều lĩnh vực:

- **Hệ thống gợi ý (Recommendation Systems):** Gợi ý sản phẩm/phim dựa trên những người dùng có sở thích tương tự.
- **Nhận dạng mẫu:** Nhận dạng chữ viết tay, nhận dạng khuôn mặt.
- **Tài chính:** Dự đoán khả năng vỡ nợ của khách hàng.
- **Y tế:** Chẩn đoán bệnh dựa trên các triệu chứng của những bệnh nhân tương tự.
- **Phân loại văn bản.**
