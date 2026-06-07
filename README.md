# Ứng Dụng Edge Computing Nhận Diện Cử Chỉ Tay (0-9) Sử Dụng FOMO & WebAssembly

Dự án cuối kỳ môn học Mạng Cảm Biến – Thực hiện xây dựng và triển khai mô hình học máy thu gọn (TinyML) tại biên để nhận diện các cử chỉ tay từ số 0 đến 9 từ dữ liệu hình ảnh camera theo thời gian thực.

---

## 1. Thành Viên Thực Hiện
* **Họ và tên:** Phạm Hữu Tài  
* **Mã số sinh viên:** N23DCCI065  
* **Trường:** Học Viện Công Nghệ Bưu Chính Viễn Thông (PTIT)

---

## 2. Kiến Trúc Hệ Thống & Mô Hình AI
Hệ thống được thiết kế theo cơ chế hoạt động của **Edge Computing** (Xử lý tại biên):
1.  **Thu thập dữ liệu:** Thu thập hình ảnh cử chỉ tay (0-9) trực tiếp thông qua camera.
2.  **Xử lý tại biên:** Sử dụng kiến trúc mạng **MobileNet V2 (bottleneck with residual)** kết hợp thuật toán **FOMO (Fast Objects, More Objects)** để tối ưu hóa tốc độ và dung lượng bộ nhớ.
3.  **Biên dịch tối ưu:** Mô hình được tối ưu hóa qua **EON™ Compiler (RAM optimized)** và xuất dưới dạng gói **WebAssembly (WASM)** giúp ứng dụng chạy mượt mà ngay trên môi trường Browser và Node.js mà không cần giao tiếp với máy chủ đám mây.

### Thông số hiệu năng trên thiết bị biên (On-device performance):
* **Thời gian suy luận (Inferencing time):** ~67 ms
* **Bộ nhớ RAM đỉnh (Peak RAM Usage):** 255.2 KB
* **Bộ nhớ Flash (Flash Usage):** 81.4 KB
* **Độ chính xác (F1 Score):** 67.1%

---

## 3. Mô Tả Cấu Trúc Thư Mục
Kho lưu trữ mã nguồn bao gồm các thành phần chính sau:

```text
├── browser/
│   ├── index.html        # Giao diện hiển thị Live Demo trên trình duyệt web
│   ├── edge-impulse-standalone.js # Thư viện wrapper kết nối API của Edge Impulse
│   └── edge-impulse-wave.wasm     # Mô hình AI đã được biên dịch sang mã máy WebAssembly
├── node/
│   ├── app.js            # Mã nguồn chạy suy luận bằng dòng lệnh qua Node.js
│   └── package.json      # Khai báo các thư viện phụ thuộc của môi trường Node
└── README.md             # Tài liệu hướng dẫn dự án 
