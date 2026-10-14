#  YÊU CẦU ĐẦU RA:

## Phần 1: So sánh

##  Bảng so sánh hai toán tử 
(a) Toán tử  “>”  
+ Về cơ chế hoạt động trong PowerShell: có chức năng tạo mới tệp hoặc ghi đè toàn bộ nội dung cũ bằng nội dung mới được xuất ra. 

+ rủi ro mất dữ liệu: có rủi ro mất dữ liệu cực kỳ cao 

+ ngữ cảnh sử dụng thực tế: dùng toán tử > để làm mới tệp báo cáo mỗi khi chạy. (ca sáng hoặc các kịch bản chạy một lần )

+ encoding file đầu ra: mặc định mã hóa tệp theo định dạng UTF-8, điều này có thể gây lỗi hiển thị ký tự (hiển thị sai font hoặc ô vuông) nếu mở bằng các công cụ hoặc trình soạn thảo không hỗ trợ chuẩn UTF-8. 

(b) Toán tử “>>” : 

+ Về cơ chế hoạt động trong PowerShell:có chức năng ghi nối tiếp nội dung mới vào cuối tệp hiện có mà không làm mất đi các dữ liệu đã được ghi trước đó. 

+ rủi ro mất dữ liệu:hoàn toàn an toàn trước rủi ro ghi đè dữ liệu cũ 

+ ngữ cảnh sử dụng thực tế:bắt buộc phải dùng toán tử >> để tích lũy toàn bộ dữ liệu qua các mốc thời gian khác nhau. (hệ thống 24/7 hoặc kịch bản ghi lỗi liên tục)

+ encoding file đầu ra: nên mặc định sử dụng mã hóa UTF-, đòi hỏi người dùng phải lưu ý khi chọn công cụ đọc tệp nhật ký để tránh lỗi hiển thị. 

## Phần 2: Lựa chọn

Giải pháp tối ưu: Sử dụng lệnh Add-Content thay vì dùng toán tử >> thông thường để vừa đảm bảo tính năng ghi nối tiếp, vừa kiểm soát được chuẩn mã hóa tiếng Việt rõ ràng. Cụ thể, cú pháp tối ưu là: Add-Content -Path daily_report.txt -Value $ket_qua -Encoding utf8.

Lập luận lý do:

Yêu cầu bài toán đặt ra là ghi nhật ký lỗi phát sinh liên tục trong ngày, do đó cơ chế nối tiếp dữ liệu là bắt buộc để không làm mất các bản ghi cũ qua các mốc thời gian khác nhau.
