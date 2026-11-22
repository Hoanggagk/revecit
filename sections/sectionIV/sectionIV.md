# Thiết lập mô phỏng và tham số thử nghiệm

## Môi trường mô phỏng

Quá trình huấn luyện và đánh giá bộ điều khiển PPO được thực hiện trong môi trường mô phỏng ProjectAirSim. Môi trường này cung cấp mô hình vật lý thời gian thực cho quadcopter, cho phép mô phỏng trạng thái chuyển động, cảm biến và tương tác động lực học của phương tiện trong không gian ba chiều. Trong mô phỏng, quadcopter có cấu hình dạng chữ X với khối lượng thân xấp xỉ $1.0\,\text{kg}$. Hệ thống động lực gồm bốn rotor bố trí đối xứng, khoảng cách theo hai trục thân là $0.253\,\text{m}$. Mỗi rotor có đường kính $0.2286\,\text{m}$ và tốc độ quay cực đại khoảng $6396\,\text{vòng/phút}$. Hai rotor quay theo chiều kim đồng hồ và hai rotor quay ngược chiều kim đồng hồ nhằm cân bằng mô-men xoắn tổng thể. Các thông số khí động và lực nâng được thiết lập theo cấu hình mô phỏng sử dụng trong ProjectAirSim.

## Tham số huấn luyện PPO

Các tham số huấn luyện chính của bộ điều khiển PPO được trình bày trong Bảng [1](#tab:ppo-hyperparameters).

| **Tham số**                       | **Giá trị**        |
|:----------------------------------|:-------------------|
| Tổng số timestep huấn luyện       | $500{,}000$        |
| Số timestep tối đa mỗi episode    | $400$              |
| Chu kỳ điều khiển $\Delta t$      | $0.05\,\text{s}$   |
| Tần suất cập nhật PPO             | $2000$ timestep    |
| Tốc độ học của actor              | $3 \times 10^{-4}$ |
| Tốc độ học của critic             | $1 \times 10^{-3}$ |
| Số epoch cập nhật $K$             | $5$                |
| Hệ số chiết khấu $\gamma$         | $0.99$             |
| Tham số GAE $\lambda$             | $0.95$             |
| Hệ số clipping $\epsilon$         | $0.2$              |
| Độ lệch chuẩn hành động ban đầu   | $1.0$              |
| Độ lệch chuẩn hành động tối thiểu | $0.1$              |
| Bước giảm độ lệch chuẩn           | $0.01$             |
| Chu kỳ giảm độ lệch chuẩn         | $50$ episode       |
| Số nơ-ron mỗi lớp ẩn              | $64$               |
| Số lớp ẩn Actor/Critic            | $2$                |
| Hàm kích hoạt                     | Tanh               |

Các siêu tham số huấn luyện PPO {#tab:ppo-hyperparameters}

## Phương pháp tham chiếu

Trong nghiên cứu này, chức năng MoveOnPath có sẵn trong ProjectAirSim được sử dụng làm phương pháp tham chiếu để đánh giá chất lượng điều khiển của tác nhân PPO. MoveOnPath thực hiện bám quỹ đạo waypoint dựa trên thuật toán carrot-following với cơ chế lookahead để dẫn hướng quadcopter dọc theo quỹ đạo\[21\]. Trong quá trình đánh giá, vận tốc đặt cho MoveOnPath được giới hạn trong khoảng $[-3,3]\,\text{m/s}$. Hai phương pháp được đánh giá trên cùng quỹ đạo tham chiếu, cùng cấu hình quadcopter và môi trường mô phỏng. Kết quả của MoveOnPath được sử dụng làm cơ sở đối chiếu với PPO thông qua thời gian hoàn thành quỹ đạo và các chỉ tiêu sai số bám.

## Tiêu chí đánh giá

Chất lượng bộ điều khiển được đánh giá dựa trên ba chỉ tiêu chính: thời gian hoàn thành quỹ đạo, sai số căn phương trung bình và sai số tuyệt đối trung bình.

Gọi $\mathbf{p}_k$ là vị trí quadcopter và $\mathbf{p}^{\mathrm{ref}}_k$ là điểm gần nhất trên đường gấp khúc nối các waypoint tại mẫu thứ $k$. Sai số bám quỹ đạo được định nghĩa là $e_k=\lVert\mathbf{p}_k-\mathbf{p}^{\mathrm{ref}}_k\rVert_2$. RMSE và MAE được tính từ thời điểm quadcopter đạt waypoint đầu tiên đến khi hoàn thành waypoint cuối cùng; cùng quy tắc được áp dụng cho PPO và baseline. Giá trị RMSE được xác định bởi

$$
\mathrm{RMSE}=\sqrt{\frac{1}{N}\sum_{k=1}^{N}e_k^2},
$$

trong khi MAE được tính theo

$$
\mathrm{MAE}=\frac{1}{N}\sum_{k=1}^{N}e_k.
$$
