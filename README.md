# Phân Tích Và Dự Đoán Chi Phí Điều Trị Bệnh Nhân Bằng Machine Learning

## Giới thiệu

Đây là đồ án môn **Khoa học dữ liệu** với mục tiêu phân tích dữ liệu bệnh nhân và xây dựng mô hình Machine Learning để dự đoán chi phí điều trị dựa trên các chỉ số sức khỏe.

Dự án giúp tìm hiểu quy trình khoa học dữ liệu từ tiền xử lý dữ liệu, phân tích khám phá dữ liệu (EDA), xây dựng mô hình dự đoán đến đánh giá kết quả.

---

## Thành viên

- Phạm Tuấn Phong : 30%
- Phạm Khánh Duy : 70%

Trường Đại học Công nghệ

---

## Câu hỏi nghiên cứu

**Làm thế nào để sử dụng các chỉ số sức khỏe của bệnh nhân để dự đoán chi phí điều trị bằng Machine Learning?**

---

## Dataset

Bộ dữ liệu sử dụng:

- Synthetic Healthcare Dataset
- 500 bệnh nhân
- 11 thuộc tính ban đầu

### Các thuộc tính chính

| Thuộc tính | Mô tả |
|------------|--------|
| Age | Tuổi |
| Gender | Giới tính |
| BMI | Chỉ số khối cơ thể |
| Blood_Pressure | Huyết áp |
| Cholesterol_Level | Cholesterol |
| Smoker | Hút thuốc |
| Diabetic | Tiểu đường |
| Diagnosis | Chẩn đoán bệnh |
| Admission_Date | Ngày nhập viện |
| Discharge_Date | Ngày xuất viện |
| Treatment_Cost | Chi phí điều trị |

---

## Tiền xử lý dữ liệu

Các bước tiền xử lý:

### 1. Chuyển đổi ngày tháng

- Admission_Date → datetime
- Discharge_Date → datetime

### 2. Tính thời gian lưu viện

```python
Length_of_Stay = Discharge_Date - Admission_Date
```

### 3. Tách huyết áp

Ví dụ:

```text
120/80
```

thành:

```text
Systolic_BP = 120
Diastolic_BP = 80
```

### 4. Mã hóa dữ liệu

Áp dụng One-Hot Encoding cho:

- Gender
- Smoker
- Diabetic
- Diagnosis

---

## Phân tích dữ liệu khám phá (EDA)

### Chi phí điều trị trung bình theo bệnh

Kết quả cho thấy:

- Heart Disease có chi phí điều trị trung bình cao nhất.
<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/a4e4407c-465a-4308-9f89-f0ed1d241e28" />


### Tỷ lệ hút thuốc

- Khoảng 47% bệnh nhân hút thuốc.
  <img width="481" height="504" alt="image" src="https://github.com/user-attachments/assets/8a7a92cd-fbc7-4e51-bb7d-9e40ead0fd37" />


### BMI và chi phí điều trị

- BMI cao thường đi kèm chi phí điều trị cao hơn.
<img width="704" height="470" alt="image" src="https://github.com/user-attachments/assets/ca324417-5db0-4c11-9b37-992c74d405f3" />

---

## Xây dựng mô hình

### Thuộc tính đầu vào

- Age
- BMI
- Cholesterol_Level
- Smoker
- Diabetic
- Diagnosis
- Length_of_Stay
- Systolic_BP
- Diastolic_BP

### Biến mục tiêu

```python
Treatment_Cost
```

### Chia tập dữ liệu

```python
train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

## Thuật toán sử dụng

### Linear Regression

```python
from sklearn.linear_model import LinearRegression
```

### Random Forest Regressor

```python
from sklearn.ensemble import RandomForestRegressor
```

---

## Đánh giá mô hình

Các chỉ số sử dụng:

### Mean Absolute Error (MAE)

```python
mean_absolute_error(y_test, predictions)
```

### R² Score

```python
r2_score(y_test, predictions)
```

---

## Kết quả

Mô hình có thể:

- Học được xu hướng chung của dữ liệu.
- Dự đoán chi phí điều trị cho bệnh nhân mới.

Tuy nhiên:

- Sai số vẫn còn tương đối lớn.
  <img width="685" height="449" alt="image" src="https://github.com/user-attachments/assets/22058c4c-f7c1-46d1-bff5-315c7bad6b80" />

- Có thể cải thiện bằng cách:
  - Thu thập thêm dữ liệu thực tế.
  - Feature Engineering.
  - Sử dụng các mô hình nâng cao hơn.

---

## Ví dụ dự đoán

```python
patient = {
    "Age": 55,
    "BMI": 30,
    "Cholesterol_Level": 220,
    "Length_of_Stay": 8,
    "Systolic_BP": 120,
    "Diastolic_BP": 80,
    "Smoker_Yes": 1,
    "Diabetic_Yes": 0
}
```

Kết quả:

```text
Predicted Treatment Cost ≈ 3003 USD
```

---

## Công nghệ sử dụng

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Jupyter Notebook

---

## Cấu trúc thư mục

```text
├── data/
│   └── synthetic_healthcare_data.csv
│
├── notebook/
│   └── healthcare_prediction.ipynb
│
└── README.md
```

---

## Hướng phát triển

- Thu thập dữ liệu bệnh viện thực tế.
- Xây dựng API dự đoán.
- Phát triển ứng dụng Web.
- Tích hợp Digital Twin cho bệnh nhân.

---

## License

Dự án phục vụ mục đích học tập và nghiên cứu.
