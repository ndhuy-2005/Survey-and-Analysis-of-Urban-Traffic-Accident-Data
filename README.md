# Khảo Sát và Phân Tích Dữ Liệu Tai Nạn Giao Thông Đô Thị Nhằm Nhận Diện Các Yếu Tố Rủi Ro và Mức Độ Nghiêm Trọng

> **Đồ án môn học:** Nhập môn Khoa học Dữ liệu (INDS331085_02)  
> **Trường Đại học Sư phạm Kỹ thuật TP. Hồ Chí Minh** — Khoa Công nghệ Thông tin  
> **Giảng viên hướng dẫn:** ThS. Lê Minh Tân  
> **Nhóm thực hiện (Nhóm 09):**  
> - Nguyễn Đình Huy — MSSV: 23110223  
> - Nguyễn Văn Minh — MSSV: 23110267  
> - Nguyễn Hoàng Anh — MSSV: 23110176  
>  
> *Tháng 06 năm 2026*

---

## 📌 Giới thiệu đề tài

Tai nạn giao thông đường bộ là vấn đề nghiêm trọng ảnh hưởng trực tiếp đến an toàn con người, tài sản và hạ tầng giao thông. Đồ án tập trung nghiên cứu, khảo sát và thực nghiệm phân tích trên **3 nguồn dữ liệu tai nạn giao thông công khai** với cơ chế thu thập, quy mô và đơn vị quan sát khác nhau:

1. **UK Road Safety Open Data (2020–2024):** Dữ liệu chuẩn police STATS19 với cấu trúc liên kết 3 bảng (*Collisions, Vehicles, Casualties*).
2. **US Accidents (2016–03/2023):** Dữ liệu quy mô lớn (>7.7 triệu bản ghi) ghi nhận traffic-impact severity, tọa độ GPS, hạ tầng và thời tiết tại Hoa Kỳ.
3. **Road Accidents Severity - Addis Ababa:** Dữ liệu phân loại đa lớp mức độ thương tích (*Slight Injury, Serious Injury, Fatal injury*) phục vụ xây dựng và đánh giá mô hình học máy.

---

## 🎯 Mục tiêu nghiên cứu

- **Mô tả & So sánh P/A/S:** Phân tích Target Population, Access Frame, Sample, đơn vị quan sát và rủi ro bias (under-reporting, source bias, missing data) của từng tập dữ liệu.
- **Tiền xử lý dữ liệu:** Chuẩn hóa kiểu dữ liệu, thời gian, xử lý missing-like/unknown, lọc miền hợp lệ và kiểm tra tính nhất quán giữa các bảng.
- **Phân tích khám phá (EDA):** Nhận diện các yếu tố ảnh hưởng (thời gian, điều kiện ánh sáng, thời tiết, loại va chạm, đối tượng tham gia giao thông) và phát hiện các vấn đề như class imbalance hay leakage.
- **Thực nghiệm Học máy Đối chứng:** Triển khai thuật toán **Decision Tree** trên PySpark để so sánh hai phiên bản dữ liệu:
  - **Basic Model:** Tiền xử lý cơ bản.
  - **Advanced Model:** Gộp category hiếm (rare grouping) + Oversampling phân tầng (square-root oversampling).
- **Đánh giá đa chiều:** Báo cáo Accuracy, Weighted F1, Macro F1, Per-class Recall/Precision, Confusion Matrix và Thời gian tính toán (Runtime trade-off).

---

## 🛠️ Công cụ & Môi trường thực hiện

- **Môi trường thực thi:** Apache Zeppelin / Jupyter Notebook (PySpark engine).
- **Ngôn ngữ & Thư viện:**
  - `PySpark` (`pyspark.sql`, `pyspark.ml`): Xử lý dữ liệu lớn, trích xuất thuộc tính, pipeline học máy.
  - `Matplotlib`, `Seaborn`: Trực quan hóa dữ liệu và kết quả thực nghiệm.
  - `Pandas`, `NumPy`: Thống kê bổ trợ và xuất báo cáo CSV.

---

## 📂 Cấu trúc Repository

```text
.
├── README.md                                  # File hướng dẫn tổng quan đề tài
├── Báo_cáo_Đồ_án_Nhóm_09.pdf                 # Báo cáo chi tiết đồ án (file PDF/Docx)
├── notebook/
│   └── 10_TRAFFIC_ACCIDENTS_PROJECT_FINAL.json # Notebook Apache Zeppelin chính của đồ án
├── data/
│   ├── raw/                                   # Nơi lưu trữ 3 dữ liệu thô (UK, US, Addis Ababa)
│   └── outputs/                               # Các tệp bảng kết quả CSV xuất từ notebook
│       ├── 00_initial_data_overview.csv
│       ├── 01_pas_comparison.csv
│       ├── 03_basic_processing_summary.csv
│       ├── 08_model_metrics_comparison.csv
│       ├── 09_per_class_metrics_comparison.csv
│       ├── 10_runtime_comparison.csv
│       └── 11_feature_importance_comparison.csv
└── figures/                                   # Biểu đồ và hình ảnh xuất ra phục vụ báo cáo
