# AI Critique

Trong bài tập này, em đã sử dụng AI để sinh ra các test plan, phân tích hệ thống và đề xuất cải thiện hiệu năng từ file jtl, sinh diagram cho Continuous Performance Testing. Khi em sử dụng, em có kết luận sau:

Điểm cộng: AI có thể tự động sinh ra các test plan jmx tương đối tốt với các cấu hình cần thiết, và đồng thời đưa ra một số kết luận về hiệu năng hệ thống và một số đề xuất để cải thiện hiệu năng.

Điểm trừ: AI bọc lộ ra những điểm trừ khá lớn. Lỗi thứ nhất AI đã sinh file jmx lỗi do cấu trúc phức tạp của file xml của JMeter, cụ thể là file cấu hình load testing bị sai ở một phần xml khiến cho em không thể đưa file jmx vào JMeter, mà phải tự sửa thủ công ở phần bị lỗi đó. Lỗi thứ hai là AI đã sinh sai assertion message ở phần checkout do đặc tả API không nói rõ message là gì. Lỗi thứ ba là cấu hình sai API endpoint ở phần search khi AI chỉ cho search keyword là parameter trong khi không để ý dấu `?` của endpoint. Lỗi thứ tư là AI cấu hình thinking time của load, stress, endurance không chuẩn khi AI đã cấu hình response time gần giống một người thường hơn mô tả một người chuyên dùng e-commerce. Lỗi thứ năm là kết luận sai như dùng 0% error rate để đánh giá tổng thể sự chắc chắn của hệ thống mà không biết cấu hình test ra sao, kết luận sai về việc hệ thống chạy nhanh hơn khi spike so với load và cho rằng thời gian phản hồi 153ms là do thiếu index. Về đề xuất, AI đã đưa ra đề xuất hiệu năng thừa (prepared statements cho sqlite). Lỗi cuối cùng là AI sinh ra diagram nhưng có một số bước anti-pattern so với chuẩn workflow

Kết luận: Chỉ dùng AI để sinh template artifacts, nhưng human review vẫn là trên hết
