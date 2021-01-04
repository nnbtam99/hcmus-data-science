1. **Câu hỏi**: Dự đoán nhiệt độ của Thành phố Hồ Chí Minh trong 1 ngày tới dựa trên các thông tin thời tiết của `N` ngày trước đó.
2. Nếu trả lời được câu hỏi thì khi đó ta sẽ có một mô hình dự đoán thời tiết đơn giản, có thể dự đoán trên máy tính với phần cứng nhỏ hơn (thay vì chạy các máy mainframe siêu tốn tài nguyên như các mô hình vật lý).
3. Thu thập dữ liệu bằng cách parse HTML từ trang [World Weather Online](https://www.worldweatheronline.com/ho-chi-minh-city-weather-history/vn.aspx)
Dữ liệu được lấy từ 1/1/2009 đến ngày 21/12/2020.
4. Tổng quan dữ liệu thu thập được: Gồm 4369 dòng và 11 cột. Dữ liệu cần dữ đoán là cột Mean (Nhiệt độ trung bình). Tỷ lệ train : test ~ 85:15
5. Ý nghĩa của từng cột:

    - Date: Ngày tháng năm 
    - Weather: Thời tiết chung trong ngày (kiểu dữ liệu phân loại)
    - Mean: Nhiệt độ trung bình trong ngày (đơn vị °c)
    - Max: Nhiệt độ lớn nhất trong ngày (đơn vị °c)
    - Min: Nhiệt độ nhỏ nhất trong ngày (đơn vị °c)
    - Wind: Vận tốc gió trong ngày (đơn vị km/h)
    - Direction: Hướng gió trong ngày (kiểu dữ liệu phân loại)
    - Rain: Lượng mưa trung bình trong ngày (đơn vị mm)
    - Humidity: Độ ẩm trung bình trong ngày (đơn vị %) 
    - Cloud: Độ bao phủ của mây trong ngày (đơn vị %)
    - Pressure: Áp suất trung bình trong ngày (đơn vị mb)

6. Tự đánh giá:
- Kết quả: Ta có được một Ensemble Model dựa trên Linear Regression và SVR để có thể dự đoán nhiệt độ của một ngày khi biết trước các thông tin như: nhiệt độ trung bình (Mean), nhiệt độ lớn nhất (Max), nhiệt độ thấp nhất (Min), tốc độ gió (Wind), lượng mưa (Rain), áp suất (Pressure), độ che phủ của mấy( Cloud) của `n=3` ngày trước đó. 
- Thiếu sót: 
    + Model dự đoán vẫn còn chênh lệch so với nhiệt độ thật. 
- Hướng phát triển: 
	+ Phân tích các features kỹ hơn để có thể chọn được những features tốt nhất cho model.
	+ Crawl thêm nhiều dữ liệu từ các nguồn khác nhau để model được huấn luyện tốt hơn.
	+ Khai thác thêm tính chu kỳ của thời tiết qua các năm. 
7. Phân công công việc:
- [Huỳnh Văn Tú](https://github.com/tuhyn): Crawl data, EDA, modelling, viết report.
- [Nguyễn Ngọc Băng Tâm](https://github.com/nnbtam99): preprocessing, EDA, modelling, evaluation, soạn poster.
8. Hướng dẫn chạy các file notebook:
- Bước 1: chạy file `CrawlData.ipynb` để crawl data từ Web và lưu lại data vào file `weather.csv` và `weather_full_df.csv`
- Bước 2: chạy file `PredictionTemperature.ipynb` để tiến hành load data & preprocessing, EDA, modelling and evaluation.




