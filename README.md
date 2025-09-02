# 💰 ATM Cash Demand Forecasting and Management

## 📌 Giới thiệu

Dự án này nhằm xây dựng một hệ thống **dự báo nhu cầu tiền mặt tại ATM** và hỗ trợ **chiến lược tiếp quỹ tối ưu**. Thông qua các mô hình Machine Learning và phân tích dữ liệu chuỗi thời gian, dự án giúp ngân hàng và tổ chức tài chính:

* Giảm thiểu tình trạng thiếu hụt hoặc dư thừa tiền mặt tại ATM.
* Tối ưu chi phí vận hành (vận chuyển, bảo quản, quản lý tiền mặt).
* Nâng cao trải nghiệm khách hàng nhờ đảm bảo tính sẵn có của tiền mặt.

## 📂 Cấu trúc dự án

```
├── atm_cash_management_dataset.csv   # Dữ liệu đầu vào
├── predictive-atm-cash-management.ipynb   # Notebook chính
├── README.md                         # Mô tả dự án
├── requirements.txt                  # Thư viện cần thiết
```

## 📊 Dữ liệu

* **Date**: Ngày giao dịch
* **ATM\_ID**: Mã định danh ATM
* **Total\_Withdrawals**: Tổng số tiền rút
* **Total\_Deposits**: Tổng số tiền nạp
* **Previous\_Day\_Cash\_Level**: Mức tiền mặt còn lại từ ngày trước
* **Weather\_Condition, Location\_Type, Holiday\_Flag, Special\_Event\_Flag**: Các đặc trưng bổ sung
* **Cash\_Demand\_Next\_Day**: Nhu cầu tiền mặt ngày kế tiếp (biến mục tiêu)

## 🔎 Các bước thực hiện

1. **EDA (Exploratory Data Analysis)**

   * Phân tích phân phối rút/nạp tiền
   * Xác định tính thời vụ, xu hướng, ảnh hưởng của ngày trong tuần và ngày lễ

2. **Feature Engineering**

   * Tạo đặc trưng thời gian (tháng, quý, cuối tuần, ngày lễ...)
   * Tạo **lag features** và **rolling statistics**
   * Xử lý dữ liệu thiếu

3. **Chuẩn bị dữ liệu**

   * Chia train/test theo thời gian (80% train, 20% test)
   * Chuẩn hóa dữ liệu số và one-hot encoding dữ liệu phân loại

4. **Huấn luyện mô hình**

   * Sử dụng **LightGBM** cho dự báo
   * So sánh với các mô hình thống kê (ARIMA, SARIMA)
   * Đánh giá bằng RMSE, MAE, MAPE

5. **Chiến lược tiếp quỹ ATM**

   * Tính toán buffer dựa trên sai số dự báo
   * Đưa ra lượng tiền nạp khuyến nghị cho từng ATM theo ngày

6. **Trực quan hóa**

   * So sánh kết quả thực tế vs dự báo
   * Phân tích tầm quan trọng đặc trưng (feature importance)

## 📈 Kết quả

* Mô hình LightGBM cho kết quả tốt với sai số dự báo thấp.
* Xây dựng được cơ chế đề xuất lượng tiền nạp vào ATM theo ngày, giúp hạn chế thiếu hụt và dư thừa.

## 🛠️ Yêu cầu môi trường

File `requirements.txt`:

```txt
pandas
numpy
matplotlib
seaborn
scikit-learn
lightgbm
statsmodels
holidays
```

## 🚀 Hướng phát triển

* Tích hợp dữ liệu thời tiết và sự kiện thực tế theo từng địa phương.
* Kết hợp mô hình Deep Learning (LSTM, Transformer) để cải thiện độ chính xác.
* Triển khai thành API/ứng dụng để sử dụng trực tiếp trong hệ thống ngân hàng.

---

✍️ *Nguyễn Huy Hoàng*
