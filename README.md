# Vietnamese Aspect-Based Sentiment Analysis (ABSA) 🇻🇳

## 📌 Giới thiệu (Introduction)
Dự án phân tích cảm xúc theo khía cạnh (ABSA) cho lĩnh vực Nhà hàng tại Việt Nam, sử dụng bộ dữ liệu **VLSP 2018**.
Dự án tập trung giải quyết vấn đề **Mất cân bằng dữ liệu (Data Imbalance)** bằng kỹ thuật **Back-Translation** và mô hình **PhoBERT**.

## 📂 Cấu trúc dự án
* `1_EDA_and_Data_Prep.ipynb`: Phân tích dữ liệu, minh chứng mất cân bằng và thử nghiệm EDA.
* `2_Baseline_Training.ipynb`: Huấn luyện mô hình gốc (Baseline) -> Kết quả F1-Score thấp ở lớp Negative.
* `3_Final_Model_BackTranslation.ipynb`: Tăng cường dữ liệu bằng Dịch ngược (Back-Translation) và Huấn luyện lại -> Cải thiện Recall cho lớp Negative.

## 📊 Kết quả thực nghiệm (Results)
| Metric | Baseline (Imbalanced) | Final (Balanced) | Cải thiện |
| :--- | :---: | :---: | :---: |
| **Recall (Negative)** | 35.2% | **50.9%** | 🚀 **+15.7%** |
| **F1-Score (Neutral)**| 49.0% | **57.5%** | 🔼 +8.5% |

## 🛠 Công nghệ sử dụng
* Python, PyTorch
* HuggingFace Transformers (PhoBERT)
* Streamlit (Demo App)
