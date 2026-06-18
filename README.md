# Phân tích Dữ liệu Bán lẻ: Dominick's Finer Foods (1989-1994)

## Giới thiệu
Đề tài này thực hiện phân tích chuyên sâu về dữ liệu bán lẻ cấp cửa hàng (store-level) của chuỗi siêu thị Dominick's Finer Foods tại khu vực Chicago trong giai đoạn 1989-1994. Nghiên cứu tập trung vào việc hiểu rõ các yếu tố ảnh hưởng đến doanh thu, hành vi tiêu dùng, hiệu quả của các chiến lược khuyến mãi và tác động của môi trường cạnh tranh.

## Mục tiêu nghiên cứu
* **Khám phá dữ liệu (EDA):** Phân tích xu hướng doanh thu tổng thể, tính mùa vụ (seasonality) và phân bổ doanh thu theo nhóm hàng (category). Các yêu tố bên ngoài và yếu tố nội tại ảnh hưởng đến doanh thu sản phẩm.
* **Phân khúc cửa hàng:** Sử dụng thông tin về vị trí và đặc điểm nhân khẩu học để phân cụm các cửa hàng (scluster), từ đó xây dựng các chiến lược vận hành phù hợp cho từng nhóm.
* **Mô hình hóa:** Xây dựng mô hình dự báo doanh thu dựa trên các đặc trưng về giá, khuyến mãi, yếu tố thời tiết và sự cạnh tranh.
* **Kiểm định giả thuyết:** Đánh giá tác động của các chiến dịch coupon, áp lực cạnh tranh đến doanh thu theo từng phân khúc cửa hàng, sự ảnh hưởng của thị trường cạnh tranh và sự ảnh hưởng của xu hướng doanh thu trong quá khứ.

## Dữ liệu
Dữ liệu được trích xuất từ Kilts Center (Đại học Chicago Booth), bao gồm:
* **Thông tin bán hàng:** Doanh thu tuần, doanh số theo nhóm hàng (category sales), sử dụng coupon.
* **Thông tin cửa hàng:** Vị trí (lat/long), phân cụm cửa hàng (scluster), dữ liệu nhân khẩu học khu vực.
* **Dữ liệu bổ trợ:** Thông tin thời tiết (nhiệt độ, lượng mưa) được thu thập bổ sung dựa trên tọa độ cửa hàng.

## Kết quả đạt được
* **Hiểu biết về cấu trúc doanh thu:** Xác định các nhóm hàng chủ lực (Grocery, Meat, Produce, v.v.) đóng góp vào doanh thu theo nguyên tắc Pareto (80/20).
* **Mô hình dự báo:** Mô hình LightGBM cho thấy hiệu năng tốt nhất với các chỉ số đánh giá (MAE, RMSE, R²) vượt trội so với các mô hình cơ sở (Ridge/Naive baseline).
* **Insight về cạnh tranh:** Chứng minh rằng tác động của đối thủ cạnh tranh không đồng nhất mà phụ thuộc mạnh mẽ vào phân khúc cửa hàng (cluster).
* **Tác động thời tiết:** Phân tích ảnh hưởng của các mức độ mưa (rain_level) đến lượt khách và doanh thu tại cửa hàng.
* **Tác động của sự  kiện giảm giá:** Phân tích sự ảnh hưởng của các sự kiện giảm giá
* **Phân tích sự ảnh hưởng của xu hướng doanh thu trong quá khứ**

## Các công cụ và kỹ thuật sử dụng
* **Ngôn ngữ:** Python
* **Thư viện chính:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `lightgbm`, `scikit-learn`.
* **Kỹ thuật:** Phân tích chuỗi thời gian, phân cụm (clustering), Bootstrap CI, hồi quy và mô hình học máy.

## Hướng phát triển
* Kiểm định sâu hơn về ảnh hưởng của "store dominance" và "category mix".
* Đánh giá mô hình trên các giai đoạn thời gian khác nhau để đảm bảo tính ổn định.
* Thử nghiệm các interaction features có kiểm soát giữa `scluster × category`, `scluster × weather`, `competition × scluster` và `coupon × category`.

---
*Nghiên cứu này dựa trên dữ liệu lịch sử và tập trung vào các quan hệ liên hệ/dự báo, chưa khẳng định các mối quan hệ nhân quả tuyệt đối.*
