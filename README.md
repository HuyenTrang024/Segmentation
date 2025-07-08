# Phân đoạn ảnh siêu âm buồng trứng bằng mô hình U-Net kết hợp tăng cường dữ liệu chuyên biệt

Dự án này triển khai một hệ thống phân đoạn ảnh siêu âm phục vụ cho việc chẩn đoán khối u buồng trứng, sử dụng mô hình U-Net – một kiến trúc mạng nơ-ron phổ biến trong lĩnh vực phân đoạn ảnh y tế. Điểm nổi bật của dự án nằm ở việc kết hợp U-Net với một quy trình tăng cường dữ liệu chuyên biệt cho ảnh siêu âm, từ đó nâng cao độ chính xác và khả năng khái quát hóa của mô hình trong môi trường lâm sàng thực tế.

---

## Mục tiêu

Ảnh siêu âm là một trong những phương thức chẩn đoán phổ biến, có chi phí thấp và không xâm lấn. Tuy nhiên, ảnh siêu âm thường bị ảnh hưởng bởi nhiễu, bóng âm, và các hiện tượng vật lý gây giảm chất lượng hình ảnh, khiến việc phân đoạn vùng tổn thương trở nên khó khăn. Dự án này nhằm xây dựng một mô hình phân đoạn chính xác, có khả năng hoạt động ổn định ngay cả khi dữ liệu đầu vào có chất lượng thấp hoặc không đồng nhất. Thông qua việc kết hợp giữa kiến trúc mạng mạnh mẽ và các kỹ thuật tăng cường dữ liệu mô phỏng đặc điểm thực tế của ảnh siêu âm, chúng tôi kỳ vọng mô hình sẽ hỗ trợ tốt cho các bác sĩ trong quá trình phân tích và chẩn đoán bệnh.

---

## Kiến trúc mô hình

Mô hình sử dụng kiến trúc U-Net cổ điển – được thiết kế đặc biệt cho các tác vụ phân đoạn ảnh y tế. U-Net bao gồm hai phần chính: nhánh mã hóa (encoder) và nhánh giải mã (decoder), được kết nối bằng các liên kết tắt (skip connections). Nhánh encoder giúp trích xuất các đặc trưng từ ảnh đầu vào thông qua các lớp convolution và pooling, trong khi nhánh decoder dần phục hồi độ phân giải bằng cách sử dụng các lớp upsampling và convolution. Việc sử dụng skip connection giúp bảo tồn thông tin vị trí và chi tiết, rất quan trọng đối với phân đoạn chính xác trong ảnh y tế.

Mô hình đầu ra là một bản đồ mặt nạ nhị phân, đánh dấu các vùng nghi ngờ khối u, sử dụng hàm kích hoạt sigmoid ở lớp cuối để cho xác suất thuộc về vùng cần phân đoạn.

---

## Tăng cường dữ liệu

Một trong những yếu tố quan trọng giúp mô hình hoạt động tốt trên dữ liệu ảnh siêu âm là việc áp dụng các kỹ thuật tăng cường dữ liệu phù hợp. Trong dự án này, chúng tôi áp dụng kỹ thuật:

### Tăng cường dữ liệu chuyên biệt cho ảnh siêu âm:


Các kỹ thuật cơ bản như lật ngang, xoay ảnh, thay đổi độ sáng không mô phỏng được hiện tượng phản xạ mà đầu dò máy siêu âm nhận được do đó tôi áp dụng các kỹ thuật tăng cường mô phỏng các hiện tượng vật lý xảy ra trong ảnh siêu âm thực tế:
- **Nhiễu Gaussian** để mô phỏng tín hiệu nhiễu điện tử.
- **Nhiễu speckle** – một dạng nhiễu phổ biến trong siêu âm do sự phản xạ không đều của sóng âm.
- **Hiệu ứng haze/mờ**, mô phỏng ảnh có độ tương phản kém, thường gặp ở bệnh nhân có mô mềm dày.
- **Bóng âm** (acoustic shadow) – mô phỏng vùng tối phía sau các vật thể cản âm như xương hoặc sỏi.
  
Link dowload OTU2D dataset: https://lnk.ink/y5gk1
| **Tổng số ảnh** | **Huấn luyện (Train)** | **Kiểm tra (Test)** | **Xác thực (Validation)** |
|------------------|-------------------------|-----------------------|-----------------------------|
| 1469             | 1177                    | 147                   | 147                         |


Số lượng theo loại u buồng trứng

| STT | Loại u buồng trứng                | Tổng ảnh | Train | Validation |
|-----|-----------------------------------|----------|-------|------------|
| 1   | Chocolate cyst                    | 336      | 226   | 110        |
| 2   | Mucinous cystadenoma              | 104      | 71    | 33         |
| 3   | High-grade serous cystadenoma     | 53       | 38    | 15         |
| 4   | Ovary normal                      | 267      | 180   | 87         |
| 5   | Simple cyst                       | 66       | 47    | 19         |
| 6   | Theca cell tumor                  | 88       | 57    | 31         |
| 7   | Teratoma                          | 336      | 228   | 108        |
| 8   | Serous cystadenoma                | 219      | 153   | 66         |
|     | **Tổng cộng**                     | **1469** | **1000** | **469**    |

---


