# Giới thiệu

Quadcopter ngày càng được ứng dụng trong nhiều nhiệm vụ như kiểm tra cơ sở hạ tầng, nông nghiệp thông minh, và tìm kiếm cứu nạn \[1, 2, 3\]. Trong các ứng dụng này, khả năng bám theo quỹ đạo xác định trước là một yêu cầu quan trọng đối với quá trình vận hành tự động. Tuy nhiên, điều khiển bám quỹ đạo quadcopter vẫn là một bài toán khó do hệ có động lực học phi tuyến, nhiều biến trạng thái liên kết, và đặc tính thiếu dẫn động \[4, 5\].

Nhiều phương pháp điều khiển đã được nghiên cứu cho bài toán này, bao gồm PID và các biến thể \[6\], LQR \[7\], điều khiển dự báo mô hình \[8\], điều khiển trượt, và các phương pháp phi tuyến bền vững \[9, 10\]. Các phương pháp này có thể đạt chất lượng bám tốt trong những điều kiện phù hợp, nhưng thường yêu cầu mô hình động lực học hoặc quá trình thiết kế và hiệu chỉnh tham số điều khiển tương ứng với từng cấu hình hệ thống.

Học tăng cường sâu (Deep Reinforcement Learning, DRL) cung cấp một hướng tiếp cận khác, trong đó chính sách điều khiển được hình thành thông qua quá trình tương tác giữa tác nhân và môi trường thay vì xây dựng trực tiếp luật điều khiển từ mô hình hệ thống. Các nghiên cứu gần đây đã khảo sát DRL cho điều khiển và bám quỹ đạo quadcopter, bao gồm điều khiển tối ưu không mô hình \[11\], so sánh các thuật toán không mô hình cho điều khiển tư thế và bám quỹ đạo \[12\], triển khai điều khiển thời gian thực dựa trên DRL \[13\], cũng như các phương pháp dựa trên DDPG \[14, 15\] và SAC \[16\]. Các kết quả này cho thấy DRL có khả năng xử lý không gian hành động liên tục và là một hướng tiếp cận phù hợp cho các bài toán điều khiển UAV.

Trong nhóm các thuật toán Actor–Critic dành cho không gian hành động liên tục, DDPG \[17\], TD3 \[18\], SAC \[19\], và Proximal Policy Optimization (PPO) \[20\] là những phương pháp được sử dụng phổ biến. Trong nghiên cứu này, PPO được lựa chọn để xây dựng chính sách điều khiển bám quỹ đạo waypoint cho quadcopter trong môi trường ProjectAirSim. Tác nhân sử dụng trạng thái chuyển động của phương tiện và thông tin tương đối tới waypoint hiện tại và kế tiếp để sinh lệnh vận tốc theo ba trục của hệ tọa độ North–East–Down (NED). Hàm phần thưởng gồm bốn thành phần: phần thưởng đạt waypoint, phần phạt vi phạm điều kiện an toàn, phần thưởng tiếp cận waypoint và phần thưởng căn chỉnh hướng vận tốc.

Các đóng góp chính của nghiên cứu gồm:

- Xây dựng tác nhân PPO cho bài toán bám quỹ đạo waypoint của quadcopter với không gian trạng thái 15 chiều và đầu ra là lệnh vận tốc theo hệ tọa độ NED.

- Thiết kế hàm phần thưởng gồm phần thưởng đạt waypoint, phần phạt vi phạm điều kiện an toàn, phần thưởng tiếp cận waypoint và phần thưởng căn chỉnh hướng vận tốc.

- Đánh giá chất lượng điều khiển quadcopter bám quỹ đạo của tác nhân PPO thông qua thời gian hoàn thành, RMSE, và MAE, đồng thời sử dụng MoveOnPath trong ProjectAirSim làm phương pháp tham chiếu.
