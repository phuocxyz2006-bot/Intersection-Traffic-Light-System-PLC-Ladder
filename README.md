# Intersection-Traffic-Light-System
# 🚦 Hệ Thống Đèn Giao Thông Ngã Tư (TIA Portal)

Dự án thiết kế và lập trình điều khiển hệ thống đèn giao thông ngã tư sử dụng PLC Siemens và giao diện giám sát HMI/WinCC. Hệ thống cho phép người dùng tùy chỉnh thời gian sáng của các đèn trực tiếp trên màn hình và có đồng hồ đếm lùi trực quan.

---

## 📌 1. Cấu Trúc Phần Cứng
* **Thiết bị điều khiển:** PLC Siemens S7-1200, dòng **CPU 1215C AC/DC/Rly**[cite: 12].
* **Giao diện:** Thiết kế mô phỏng trên nền tảng WinCC/HMI[cite: 13].

---

## 💻 2. Cấu Trúc Chương Trình (Program Blocks)
Toàn bộ logic điều khiển, định thời và xử lý tín hiệu của hệ thống được viết gọn gàng trong khối tổ chức chính:
* **`Main [OB1]`**: Vòng quét chính của PLC thực thi toàn bộ chương trình đèn giao thông[cite: 12].

---

## 🏷️ 3. Quản Lý Biến Nội Bộ (PLC Tags)
Các biến trong chương trình được phân chia vào các bảng Tag (Tag tables) theo đúng chức năng để dễ quản lý và debug[cite: 12]:
* **`INPUT [2]`**: Chứa các biến ngõ vào vật lý hoặc nút nhấn điều khiển (ví dụ: Start, Reset)[cite: 12].
* **`OUTPUT [7]`**: Chứa các biến ngõ ra điều khiển các đèn tín hiệu thực tế[cite: 12].
* **`MEMORY [8]`**: Các biến nhớ trung gian để lưu trạng thái bước chạy của hệ thống[cite: 12].
* **`SETTING [8]`**: Lưu trữ các thông số thời gian được cài đặt từ HMI[cite: 12].
* **`XUNG [12]`**: Quản lý các biến bộ đếm (Timer), tạo xung nhịp định thời và đếm lùi thời gian[cite: 12].
* **`Default tag table [38]`**: Bảng chứa các tag mặc định hệ thống tự sinh ra[cite: 12].

---

## 🖥️ 4. Giao Diện Giám Sát SCADA/HMI
<img width="1016" height="745" alt="image" src="https://github.com/user-attachments/assets/0d0e695c-20a1-44c0-beff-a8521b3e11f6" />
Giao diện điều khiển trung tâm được thiết kế trực quan với màn hình **ĐÈN GIAO THÔNG NGÃ TƯ**[cite: 13], bao gồm các khu vực chức năng chính:

* **Bảng Cài Đặt (Settings):** Cho phép người vận hành nhập thông số thời gian trực tiếp[cite: 13]:
  * **Time đèn xanh:** Cài đặt thời gian sáng đèn xanh (đơn vị: giây)[cite: 13].
  * **Time đèn đỏ:** Cài đặt thời gian sáng đèn đỏ (đơn vị: giây)[cite: 13].
* **Nút Nhấn & Cảnh Báo (Controls):** 
  * Nút **`Start`**: Khởi động chu trình đèn[cite: 13].
  * Nút **`Reset`**: Đặt lại hệ thống về trạng thái ban đầu[cite: 13].
  * Đèn báo **`Run`**: Hiển thị trạng thái hệ thống đang hoạt động[cite: 13].
* **Mô Phỏng Trực Quan (Animation):**
  * Hiển thị mô hình ngã tư với 4 trụ đèn độc lập[cite: 13].
  * Mỗi trụ đèn có 3 cụm đèn màu (Đỏ, Vàng, Xanh) đi kèm với **bảng LED đếm lùi** (hiển thị 2 chữ số `##`) cho từng màu tương ứng[cite: 13].

---

## 🚀 5. Hướng Dẫn Mô Phỏng
1. Mở project bằng phần mềm TIA Portal.
2. Khởi động **S7-PLCSIM** để mô phỏng CPU 1215C.
3. Chạy mô phỏng màn hình HMI.
4. Nhập thời gian cho Đèn Xanh và Đèn Đỏ tại phần **BẢNG CÀI ĐẶT**.
5. Nhấn **Start** để quan sát chu trình đèn chuyển màu và đồng hồ đếm lùi tương ứng trên các ngã tư.
