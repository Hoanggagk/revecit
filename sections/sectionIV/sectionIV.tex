\section{Thiết lập mô phỏng và tham số thử nghiệm}
\label{sec:experimental-setup}

\subsection{Môi trường mô phỏng}

Quá trình huấn luyện và đánh giá bộ điều khiển PPO được thực hiện trong môi trường mô phỏng ProjectAirSim. Môi trường này cung cấp mô hình vật lý thời gian thực cho quadcopter, cho phép mô phỏng trạng thái chuyển động, cảm biến và tương tác động lực học của phương tiện trong không gian ba chiều.
Trong mô phỏng, quadcopter có cấu hình dạng chữ X với khối lượng thân xấp xỉ \(1.0\,\text{kg}\). Hệ thống động lực gồm bốn rotor bố trí đối xứng, khoảng cách theo hai trục thân là \(0.253\,\text{m}\). Mỗi rotor có đường kính \(0.2286\,\text{m}\) và tốc độ quay cực đại khoảng \(6396\,\text{vòng/phút}\). Hai rotor quay theo 
chiều kim đồng hồ và hai rotor quay ngược chiều kim đồng hồ nhằm cân bằng mô-men xoắn tổng thể. Các thông số khí động và lực nâng được thiết lập theo cấu hình mô phỏng sử dụng trong ProjectAirSim.

\subsection{Tham số huấn luyện PPO}

Các tham số huấn luyện chính của bộ điều khiển PPO được trình bày trong Bảng~\ref{tab:ppo-hyperparameters}.

\input{Table/table1.tex}
\subsection{Phương pháp tham chiếu}
Trong nghiên cứu này, chức năng MoveOnPath có sẵn trong ProjectAirSim được sử dụng làm phương pháp tham chiếu để đánh giá chất lượng điều khiển của tác nhân PPO. MoveOnPath thực hiện bám quỹ đạo waypoint dựa trên thuật toán carrot-following với cơ chế lookahead để dẫn hướng quadcopter dọc theo quỹ đạo\cite{b21}. Trong quá trình đánh giá, vận tốc đặt cho MoveOnPath được giới hạn trong khoảng \([-3,3]\,\text{m/s}\). Hai phương pháp được đánh giá trên cùng quỹ đạo tham chiếu, cùng cấu hình quadcopter và môi trường mô phỏng. Kết quả của MoveOnPath được sử dụng làm cơ sở đối chiếu với PPO thông qua thời gian hoàn thành quỹ đạo và các chỉ tiêu sai số bám.
\subsection{Tiêu chí đánh giá}

Chất lượng bộ điều khiển được đánh giá dựa trên ba chỉ tiêu chính: thời gian hoàn thành quỹ đạo, sai số căn phương trung bình và sai số tuyệt đối trung bình.

Gọi \(\mathbf{p}_k\) là vị trí quadcopter và \(\mathbf{p}^{\mathrm{ref}}_k\) là điểm gần nhất trên đường gấp khúc nối các waypoint tại mẫu thứ \(k\). Sai số bám quỹ đạo được định nghĩa là \(e_k=\lVert\mathbf{p}_k-\mathbf{p}^{\mathrm{ref}}_k\rVert_2\). RMSE và MAE 
được tính từ thời điểm quadcopter đạt waypoint đầu tiên đến khi hoàn thành waypoint cuối cùng; cùng quy tắc được áp dụng cho PPO và baseline. Giá trị RMSE được xác định bởi

\begin{equation}
\mathrm{RMSE}=\sqrt{\frac{1}{N}\sum_{k=1}^{N}e_k^2},
\end{equation}

trong khi MAE được tính theo

\begin{equation}
\mathrm{MAE}=\frac{1}{N}\sum_{k=1}^{N}e_k.
\end{equation}
