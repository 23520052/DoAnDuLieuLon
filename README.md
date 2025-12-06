# 🇻🇳 PHÂN TÍCH CẢM XÚC THEO KHÍA CẠNH (ABSA) CHO TIẾNG VIỆT
## ASPECT-BASED SENTIMENT ANALYSIS FOR VIETNAMESE WITH BALANCED DATA AUGMENTATION

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-ee4c2c.svg)
![Colab](https://img.shields.io/badge/Google-Colab-orange.svg)
![Model](https://img.shields.io/badge/Model-PhoBERT-yellow.svg)

---

## 📌 Giới thiệu (Introduction)
Đây là đồ án môn học **Big Data**, tập trung giải quyết bài toán **Phân tích cảm xúc theo khía cạnh (Aspect-Based Sentiment Analysis - ABSA)** cho lĩnh vực Nhà hàng tại Việt Nam.

Dự án sử dụng bộ dữ liệu chuẩn **VLSP 2018** và mô hình ngôn ngữ **PhoBERT**. Mục tiêu chính của đề tài là giải quyết vấn đề **Mất cân bằng dữ liệu (Data Imbalance)** nghiêm trọng (lớp Tiêu cực quá ít) bằng kỹ thuật tăng cường dữ liệu **Back-Translation (Dịch ngược)**.

### 🎯 Mục tiêu
1.  Minh chứng tác động tiêu cực của dữ liệu mất cân bằng đối với mô hình AI.
2.  Áp dụng kỹ thuật Back-Translation (Việt -> Anh -> Việt) để sinh dữ liệu chất lượng cao cho các lớp thiểu số.
3.  Cải thiện khả năng phát hiện bình luận tiêu cực (Negative Recall) cho doanh nghiệp.

---

## 📂 Cấu trúc dự án (Project Structure)
Dự án được chia thành 4 Sổ tay (Notebooks) theo quy trình thực nghiệm khoa học:

* **`1_EDA_Data_Preparation.ipynb`**:
    * Phân tích khám phá dữ liệu (EDA).
    * Vẽ biểu đồ minh chứng sự mất cân bằng (Positive chiếm ~76%, Negative chỉ ~7%).
    * Thử nghiệm phương pháp EDA (Easy Data Augmentation) và đánh giá sơ bộ.

* **`2_Baseline_Training.ipynb`**:
    * Huấn luyện mô hình gốc (Baseline) trên dữ liệu mất cân bằng.
    * **Kết quả:** F1-Score và Recall của lớp Negative rất thấp (mô hình học vẹt theo lớp đa số).

* **`3_Final_Model_Training.ipynb`**:
    * Thực hiện kỹ thuật **Back-Translation** để cân bằng lại dữ liệu.
    * Huấn luyện lại mô hình PhoBERT trên dữ liệu đã cân bằng.
    * Lưu model (`Model_Final`) vào Google Drive.

* **`4_Demo_Application.ipynb`**:
    * Ứng dụng Demo giao diện web sử dụng **Streamlit**.
    * Cho phép người dùng nhập câu bình luận và chọn khía cạnh để phân tích thời gian thực.

---

## 📊 Kết quả thực nghiệm (Results)

Sau khi áp dụng kỹ thuật Tăng cường dữ liệu (Back-Translation), mô hình đã có sự cải thiện vượt bậc, đặc biệt là khả năng nhận diện các bình luận tiêu cực (Negative).

| Chỉ số (Metric) | Baseline (Gốc) | Final Model (Back-Translation) | Mức độ cải thiện |
| :--- | :---: | :---: | :---: |
| **Recall (Negative)** | 35.2% | **50.9%** | 🚀 **+15.7%** |
| **F1-Score (Neutral)** | 49.0% | **57.5%** | 🔼 +8.5% |
| **Macro F1-Score** | 0.57 | **0.61** | ✅ Tăng độ ổn định |

> **Nhận xét:** Việc tăng chỉ số Recall cho lớp Negative từ 35% lên 51% có ý nghĩa thực tiễn lớn, giúp doanh nghiệp giảm thiểu việc bỏ sót các khiếu nại của khách hàng.

---

## 🛠 Hướng dẫn chạy Demo (How to run)

Dự án được thiết kế để chạy hoàn toàn trên **Google Colab**.

### Bước 1: Chuẩn bị
1.  Clone repository này hoặc tải các file `.ipynb` về.
2.  Upload bộ dữ liệu VLSP 2018 vào Google Drive (theo đường dẫn trong code).

### Bước 2: Huấn luyện mô hình
* Chạy lần lượt sổ tay `1`, `2`, `3` để tái hiện quá trình huấn luyện.
* Sau khi chạy xong sổ tay `3`, model sẽ được lưu tại Google Drive: `/content/drive/My Drive/ABSA_Project/Model_Final`.

### Bước 3: Chạy Web Demo (Streamlit)
1.  Mở sổ tay `4_Demo_Application.ipynb`.
2.  Đăng ký tài khoản miễn phí tại [Ngrok Dashboard](https://dashboard.ngrok.com) để lấy **Authtoken**.
3.  Dán Authtoken vào dòng code tương ứng trong sổ tay.
4.  Chạy toàn bộ code (Run All).
5.  Truy cập vào đường link `*.ngrok-free.app` được tạo ra để trải nghiệm App.
   
## 📂 Dữ liệu (Dataset)
Dự án bao gồm thư mục `dataset/` chứa:
* **Dữ liệu gốc VLSP 2018:** Dùng để chạy Baseline.
* **Dữ liệu Back-Translation (`.csv`):** Dữ liệu đã được tăng cường, dùng để huấn luyện Final Model (giúp tiết kiệm thời gian tiền xử lý).

> **Lưu ý:** Khi chạy trên Google Colab, vui lòng upload toàn bộ file trong thư mục `dataset` này vào thư mục dự án trên Google Drive của bạn.
---

## 📚 Tài liệu tham khảo
* **Dataset:** VLSP 2018 (Aspect Based Sentiment Analysis).
* **Base Model:** [VinAI/PhoBERT](https://github.com/VinAIResearch/PhoBERT).
* **Technique:** Google Translate API for Back-Translation.

---
*Đồ án thực hiện bởi Mai Lan Anh*
