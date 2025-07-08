# Tăng cường dữ liệu cho phân đoạn ảnh siêu âm bằng mô hình U-Net

Dự án này tập trung nghiên cứu ảnh hưởng của các kỹ thuật tăng cường ảnh (data augmentation) dành riêng cho ảnh siêu âm, nhằm cải thiện hiệu quả phân đoạn u buồng trứng sử dụng kiến trúc U-Net.

---

## Nội dung các tệp

| Tên file | Mô tả |
|----------|------|
| `split_json.ipynb` | Chia tập dữ liệu huấn luyện và kiểm tra từ file JSON chứa annotation |
| `train_UNet_with_and_without_original_images.ipynb` | Huấn luyện mô hình U-Net với ảnh gốc, không áp dụng augmentation (baseline) |
| `train_UNet_with_and_without_depth_attenuation.ipynb` | Áp dụng hoặc không áp dụng kỹ thuật giảm cường độ (depth attenuation) |
| `train_UNet_with_and_without_gaussian_shadow.ipynb` | Thử nghiệm hiệu quả augmentation tạo bóng mờ Gaussian |
| `train_UNet_with_and_without_haze_artifact.ipynb` | Tạo hiện tượng sương mù (haze) trên ảnh siêu âm để tăng tính đa dạng |
| `train_UNet_with_and_without_speckle_reduction.ipynb` | Áp dụng kỹ thuật giảm nhiễu speckle phổ biến trong ảnh siêu âm |

---

## Mục tiêu

- Phân tích ảnh hưởng của từng kỹ thuật augmentation đối với hiệu quả phân đoạn
- So sánh hiệu năng giữa các mô hình với/không với từng kỹ thuật
- Tìm ra chiến lược tiền xử lý tối ưu cho dữ liệu siêu âm u buồng trứng

---

## Đánh giá

Mỗi mô hình được đánh giá dựa trên các chỉ số:
- **IoU** (Intersection over Union)
- **DSC** (Dice Similarity Coefficient)
- **Precision**
- **Recall**

---

## Bộ dữ liệu

- Dữ liệu sử dụng: **OTU2D – Ovarian Tumor Ultrasound Dataset**
- Dữ liệu bao gồm ảnh siêu âm định dạng `.png` và mask phân vùng/annotation

---

