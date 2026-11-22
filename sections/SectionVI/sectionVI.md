\section{Kết luận}
\label{sec:conclusion}
Bài báo đã xây dựng và đánh giá tác nhân điều khiển quadcopter bám quỹ đạo được xây dựng dựa trên thuật toán PPO và huấn luyện trong môi trường ProjectAirSim. Tác nhân sử dụng trạng thái 15 chiều để sinh lệnh vận tốc theo hệ tọa độ NED và được 
huấn luyện với hàm phần thưởng gồm phần thưởng hoàn thành waypoint, phạt vi phạm điều kiện an toàn, phần thưởng tiếp cận waypoint và phần thưởng hiệu chỉnh hướng vận tốc. Kết quả huấn luyện cho thấy phần thưởng tăng theo quá trình huấn luyện và đạt ổn định, 
điều này cho thấy tác nhân đã học chính sách phù hợp và cho phép quadcopter hoàn thành quỹ đạo hình vuông gồm 40 waypoint. Trong điều kiện mô phỏng được khảo sát, PPO hoàn thành quỹ đạo trong 17.34 s so với 36.34 s của MoveOnPath, 
đồng thời giảm RMSE từ 0.186 m xuống 0.105 m và MAE từ 0.160 m xuống 0.073 m. Sai số RMSE theo cả ba trục cũng thấp hơn phương 
pháp tham chiếu, cho thấy tác nhân PPO đã học được chính sách sinh lệnh vận tốc phù hợp với nhiệm vụ bám quỹ đạo được thiết lập. 
Tuy nhiên, đáp ứng tư thế của tác nhân PPO có biến thiên lớn hơn tại một số vị trí quadcopter chuyển hướng. Các nghiên cứu tiếp theo sẽ tập trung cải thiện độ ổn định của 
đáp ứng tư thế, đồng thời đánh giá chính sách trên các quỹ đạo, điều kiện nhiễu và môi trường hoạt động đa dạng hơn trước khi xem xét triển khai trên hệ thống thực.
