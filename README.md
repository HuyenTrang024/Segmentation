# Phân đoạn ảnh siêu âm bằng mô hình U-Net kết hợp tăng cường dữ liệu chuyên biệt

Dự án này triển khai hệ thống phân đoạn khối u buồng trứng từ ảnh siêu âm bằng mô hình U-Net. Để cải thiện hiệu suất và độ tổng quát của mô hình, chúng tôi áp dụng cả các kỹ thuật tăng cường dữ liệu **thông thường** và **chuyên biệt cho ảnh siêu âm** trong quá trình huấn luyện.

---

## 🎯 Mục tiêu

Ảnh siêu âm là công cụ chẩn đoán phổ biến trong lâm sàng do chi phí thấp và độ an toàn cao. Tuy nhiên, chúng thường gặp vấn đề về nhiễu, độ tương phản kém và bóng âm. Việc tăng cường dữ liệu hợp lý giúp mô hình học được tốt hơn trong môi trường thực tế.

---

## 🏗️ Kiến trúc mô hình

Mô hình sử dụng kiến trúc U-Net cổ điển:

- **Encoder**: Convolution → ReLU → MaxPooling
- **Bottleneck**
- **Decoder**: Transposed Convolution + Skip Connection
- **Output**: 1 kênh (mặt nạ nhị phân), dùng hàm sigmoid

---

## 🔁 Tăng cường dữ liệu (Data Augmentation)

### ✅ Các kỹ thuật tăng cường dữ liệu cơ bản:
- Lật ngang / dọc
- Xoay ngẫu nhiên
- Phóng to / thu nhỏ

### 🩺 Các kỹ thuật tăng cường chuyên biệt cho ảnh siêu âm:
- **Nhiễu Gaussian (Gaussian Noise)**  
- **Mô phỏng nhiễu speckle (Speckle Noise)**
- **Hiệu ứng mờ/haze** – mô phỏng ảnh siêu âm độ tương phản thấp
- **Biến dạng đàn hồi (Elastic Deformation)** – mô phỏng rung động đầu dò
- **Bóng âm (Acoustic Shadow Augmentation)** – mô phỏng hiệu ứng vật lý


