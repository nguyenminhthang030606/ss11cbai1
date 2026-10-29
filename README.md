Warehouse Safety Validation System
Giới thiệu
Chương trình mô phỏng hệ thống kiểm định an toàn nhập kho trong Warehouse Management System (WMS) của Rikkei Logistics.

Hệ thống thực hiện kiểm tra các điều kiện an toàn trước khi cho phép pallet hàng hóa được nhập lên một ô kệ trong kho.

Quy tắc nghiệp vụ
1. Quy tắc tải trọng kho
Tải trọng tối đa cho phép trên mỗi ô kệ:

500 kg
Điều kiện hợp lệ:

current_weight_kg + item.weight_kg <= 500
Nếu vượt quá:

Từ chối nhập kho
2. Quy tắc kho lạnh
Nếu kệ thuộc khu vực kho lạnh:

is_cold_storage = 1
Thì nhiệt độ bảo quản của kiện hàng phải nằm trong khoảng:

[-18°C ; 5°C]
Nếu nằm ngoài khoảng trên:

Từ chối nhập kho
Cấu trúc dữ liệu
PalletItem
Thuộc tính	Kiểu dữ liệu
pallet_id	int
weight_kg	float
temp_celsius	float
WarehouseShelf
Thuộc tính	Kiểu dữ liệu
shelf_id	int
is_cold_storage	int
current_weight_kg	float
Chức năng
Kiểm tra nhiệt độ kho lạnh.
Kiểm tra tải trọng tối đa của kệ.
In thông báo lỗi khi vi phạm quy định.
Cho phép hoặc từ chối nhập kho.
Biên dịch chương trình
GCC
gcc main.c -o warehouse
Chạy chương trình
./warehouse
Ví dụ đầu vào
Kệ:
ID = 101
Loại = Kho lạnh
Tải trọng hiện tại = 400 kg

Pallet:
ID = 5001
Trọng lượng = 150 kg
Nhiệt độ = 12°C
Kết quả mong đợi
[LOI KHO LANH]
=> KET QUA: [TU CHOI]
Do:

Nhiệt độ 12°C nằm ngoài khoảng cho phép.
Tổng tải trọng sau nhập kho là 550 kg vượt giới hạn 500 kg.
