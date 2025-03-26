
# Dự án Dự đoán Ung thư Phổi bằng Machine Learning

## Mục tiêu
Dự án này nhằm xây dựng một pipeline xử lý dữ liệu và mô hình học máy (MLPClassifier) để dự đoán khả năng mắc ung thư phổi dựa trên dữ liệu khảo sát bệnh nhân. Qua đó, chúng ta đánh giá hiệu năng của mô hình và kiểm thử bằng các chỉ số đánh giá khác nhau.

## Nội dung chính của dự án

### 1. Đọc và Khám phá Dữ liệu
- **Dữ liệu**: File `survey lung cancer.csv` chứa các thông tin về bệnh nhân với các biến:
  - `GENDER`: Giới tính (MAN = 1, WOMAN = 0).
  - `AGE`: Tuổi.
  - `SMOKING`, `YELLOW_FINGERS`, `ANXIETY`, `PEER_PRESSURE`, `CHRONIC DISEASE`, `FATIGUE`, `ALLERGY`, `WHEEZING`, `ALCOHOL CONSUMING`, `COUGHING`, `SHORTNESS OF BREATH`, `SWALLOWING DIFFICULTY`, `CHEST PAIN`.
  - `LUNG_CANCER`: Nhãn mục tiêu (0: Không ung thư, 1: Ung thư phổi).
- **Tiền xử lý**:
  - Đọc dữ liệu, kiểm tra thông tin (df.info(), df.describe()).
  - Loại bỏ các bản ghi trùng lặp.
  - Mã hóa nhãn cho biến `GENDER` và `LUNG_CANCER` bằng LabelEncoder.
  
### 2. Khám phá Phân bố & Tương quan
- Vẽ các biểu đồ phân bố, boxplot, countplot để xem tỷ lệ của các lớp trong `LUNG_CANCER`.
- Vẽ ma trận tương quan bằng heatmap để xác định các biến có mối liên quan mạnh với `LUNG_CANCER`.
- Tạo biến tương tác, ví dụ: `ANXYELFIN = ANXIETY * YELLOW_FINGERS`, để khám phá ảnh hưởng kết hợp của các biến.

### 3. Cân bằng Dữ liệu
- Sử dụng ADASYN để cân bằng số lượng mẫu giữa các lớp (ung thư và không ung thư).

### 4. Xây dựng Mô hình
- **Tách dữ liệu**: Phân chia dữ liệu thành tập huấn luyện và tập kiểm tra (test_size=0.25, random_state=0).
- **Huấn luyện mô hình**:  
  Sử dụng `MLPClassifier` của PyTorch (hoặc scikit-learn) để huấn luyện mô hình dựa trên các biến đã xử lý.
- **Lưu mô hình**: Lưu mô hình đã huấn luyện thành file (vd: `saved_model.pth`).

### 5. Đánh giá và Kiểm thử Mô hình
- **Đánh giá trên tập kiểm tra**:
  - In báo cáo đánh giá mô hình (classification_report) bao gồm các chỉ số Accuracy, Precision, Recall, F1-score.
  - Vẽ ma trận nhầm lẫn (Confusion Matrix) bằng heatmap.
- **Kiểm thử với K-Fold Cross Validation (10-fold)**:
  - Tính toán độ chính xác trung bình của mô hình qua 10 fold.

#### Ví dụ Kết quả:
- **Tập kiểm tra**: Tổng số mẫu: 122.
- **Độ chính xác**: Khoảng 95% (116/122 mẫu đúng).
- **Ma trận nhầm lẫn** cho thấy số lượng FP (False Positive) và FN (False Negative) nhỏ.
- Cross validation cho thấy độ ổn định của mô hình.

### 6. Kết luận và Nhận xét
- Mô hình MLPClassifier cho kết quả phân loại rất khả quan với độ chính xác cao và số lỗi dự đoán thấp.
- Việc cân bằng dữ liệu và tạo biến tương tác (như ANXYELFIN) đã giúp cải thiện hiệu năng của mô hình.
- Dự án cung cấp một cơ sở để phát triển thêm các mô hình phức tạp hơn hoặc triển khai ứng dụng thực tế.

## Hướng dẫn Chạy Dự án
1. **Clone Repository**:
   ```bash
   git clone https://github.com/your_username/lung-cancer-prediction.git
   cd lung-cancer-prediction
   ```
2. **Mở Notebook**:  
   Chạy file notebook (ví dụ: `lung_cancer_prediction.ipynb`) trên Google Colab hoặc Jupyter Notebook.
3. **Cập nhật Đường dẫn**:  
   Nếu cần, chỉnh sửa đường dẫn đến file `survey lung cancer.csv`.
4. **Chạy toàn bộ Pipeline**:  
   Từ tiền xử lý dữ liệu, khám phá, huấn luyện mô hình cho đến đánh giá, bạn sẽ thấy kết quả hiển thị trên notebook.

## Yêu cầu Cài đặt
- Python 3.7+
- Thư viện: pandas, numpy, matplotlib, seaborn, scikit-learn, imblearn
- (Nếu dùng PyTorch, đảm bảo cài đặt phiên bản phù hợp nếu có phần huấn luyện bằng PyTorch.)

## Tài liệu Tham khảo
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [Imbalanced-learn Documentation](https://imbalanced-learn.org/)
- [PyTorch Documentation](https://pytorch.org/)

## Liên hệ
Nếu có thắc mắc hoặc góp ý, vui lòng mở issue trên GitHub hoặc liên hệ qua email: thanh.van19062004@gmail.com


### Hướng dẫn Sử dụng README này:
1. Tạo file mới có tên `README.md` trong repository của bạn.
2. Sao chép nội dung trên và dán vào file `README.md`.
3. Lưu, commit và push lên GitHub.

Mẫu README này cung cấp thông tin tổng quan về dự án, quá trình tiền xử lý, xây dựng và kiểm thử mô hình, cùng với các kết quả chính. Bạn có thể điều chỉnh nội dung cho phù hợp với dự án của mình.
