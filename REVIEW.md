# Phản biện bài báo

**Submission:** 21  
**Tiêu đề:** Ứng dụng thuật toán PPO trong điều khiển quadcopter bám quỹ đạo

## Review 1

### Đánh giá tổng thể

**Điểm:** 2 (accept)

### Nội dung phản biện

Nhóm tác giả đề xuất một giải pháp điều khiển cấp cao cho thiết bị bay bốn cánh (quadcopter) ứng dụng thuật toán Học tăng cường sâu (Deep Reinforcement Learning - DRL) Proximal Policy Optimization (PPO). Báo cáo phản biện này đánh giá toàn diện công trình dựa trên tính cấp thiết, giá trị khoa học, tính đúng đắn về mặt lý thuyết điều khiển, phương pháp thực nghiệm và khả năng ứng dụng thực tế.

### Câu hỏi và kiến nghị

1. Hình 2. vector hành động gồm 04 thành phần nhưng trong Thiết kế PPO theo 03 thành phần?
2. MoveOnPath và PPO là các thuật toán điều khiển hay là bộ điều khiển hay là phương pháp điều khiển? Trong bài báo tác giả dùng "Bộ điều khiển PPO" so sánh với "Phương pháp MoveOnPath".
3. Quỹ đạo mô phỏng được thiết lập cụ thể thế nào (Tọa độ bắt đầu, kết thúc, các điểm mốc chính)? Từ đó xác định quỹ đạo tham chiếu (ref) theo trục X, Y, Z để đối sánh với kết quả của các thuật toán điều khiển.
4. Các tác giả có thử nghiệm với các quỹ đạo phức tạp hơn để khẳng định ưu điểm của PPO không? (quỹ đạo xoắn ốc, quỹ đạo hình số 8)
5. Kết quả mô phỏng Hình 6 cho thấy góc Roll, Pitch ở bộ điều khiển PPO dao động rất lớn (+25, -20) so với phương pháp MoveOnPath (+4, -4). Điều này sẽ khiến Quadcopter rung lắc mạnh trong thực tế. Như vậy bộ điều khiển PPO tốt hơn về tốc độ, độ chính xác quỹ đạo, nhưng kém hơn về độ ổn định? Thực tế dao động của các góc như vậy sẽ dẫn tới dao động về vị trí X, Y, Z.

### Phản hồi của tác giả đối với câu hỏi 2

Nhóm tác giả cảm ơn Reviewer đã chỉ ra sự chưa thống nhất về cấp độ thuật ngữ. Trong bản sửa đổi, hai đối tượng được so sánh đều được gọi chung là **phương pháp điều khiển**, cụ thể là **phương pháp điều khiển dựa trên PPO** và **phương pháp điều khiển MoveOnPath**.

PPO là thuật toán học tăng cường được sử dụng để cập nhật mạng Actor và Critic trong quá trình huấn luyện, không đồng nhất với toàn bộ phương pháp điều khiển. Sau huấn luyện, chính sách Actor của PPO ánh xạ trạng thái 15 chiều thành ba lệnh vận tốc theo hệ tọa độ NED. Các lệnh này được chuyển tới bộ điều khiển bay tích hợp trong ProjectAirSim để thực hiện các vòng điều khiển cấp thấp. Cấu trúc gồm chính sách Actor sinh lệnh vận tốc cấp cao và bộ điều khiển bay tích hợp thực hiện điều khiển cấp thấp được gọi chung là **phương pháp điều khiển dựa trên PPO**.

Đối tượng tham chiếu trong thí nghiệm là **phương pháp điều khiển MoveOnPath**, được triển khai bằng cách gọi chức năng MoveOnPath có sẵn trong ProjectAirSim. Carrot-following chỉ được dùng để mô tả cơ chế lookahead của chức năng MoveOnPath; bài báo không tuyên bố đã triển khai độc lập một phương pháp điều khiển Carrot-following khác.

Nhóm tác giả đã thống nhất cách gọi này trong phần tóm tắt, giới thiệu, thiết kế phương pháp, thiết lập thử nghiệm, chú thích hình, bảng kết quả và kết luận. Do đó, bản sửa đổi không còn so sánh “bộ điều khiển PPO” với “phương pháp MoveOnPath”, cũng không xem thuật toán PPO và chức năng MoveOnPath là hai thuật toán điều khiển cùng cấp.

### Kiến nghị

1. Điều chỉnh bổ sung hàm phạt vận tốc góc ở công thức (5) để nâng cao tính ổn định của Quadcopter.
2. Làm rõ quỹ đạo tham chiếu của mô phỏng thực nghiệm.
3. Thử nghiệm với các quỹ đạo phức tạp hơn (nếu được) để khẳng định chất lượng của bộ điều khiển PPO so với bộ điều khiển theo phương pháp MoveOnPath.

## Review 2

### Đánh giá tổng thể

**Điểm:** 1 (weak accept)

### Nội dung phản biện

Bài báo xây dựng và đánh giá tác nhân điều khiển quadcopter bám quỹ đạo trên cơ sở áp dụng thuật toán PPO và huấn luyện trong môi trường ProjectAirSim.

Hiệu quả của phương pháp đưa ra trong bài báo được đánh giá so sánh với phương pháp MoveOnPath. Kết quả mô phỏng đã khẳng định phương pháp của bài báo cho chất lượng điều khiển quadcopter bám quỹ đạo tốt hơn phương pháp tham chiếu MoveOnPath.

Cần chỉnh sửa các số liệu theo cách viết của Tiếng Việt.
