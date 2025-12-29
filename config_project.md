Bước 1: gõ lệnh python -m venv venv
Bước 2: gõ lệnh source venv/Scripts/activate
Bước 3: tạo file requirements.txt, trong file thêm tên các thư viện muốn tải trong môi trường ảo
Bước 4: gõ lệnh pip install -r requirements.txt  
Bước 5: chọn select kernel

- Kiểm tra các thư viện đã tải chưa thì:

* Gõ lệnh pip show + tên thư viện or gõ lệnh pip list

- Notes : Nhớ kiểm tra đường dẫn trong file activate.bat để coi nó trỏ đúng đến môi trường ảo chưa thường thì sẽ trỏ chính xác nhưng nhiều khi di chuyển folder venv thì nó lại không cập nhập lại đường dẫn nên lỗi
