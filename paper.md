\documentclass[conference]{IEEEtran}
\IEEEoverridecommandlockouts
% The preceding line is only needed to identify funding in the first footnote. If that is unneeded, please comment it out.
\usepackage{cite}
% UTF-8 input and T5 font encoding are required for Vietnamese text.
\usepackage[utf8]{inputenc}
\usepackage[T5]{fontenc}
\usepackage{amsmath,amssymb,amsfonts}
\usepackage{algorithmic}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{textcomp}
\usepackage{xcolor}
\usepackage{placeins}
\usepackage{float}
\def\BibTeX{{\rm B\kern-.05em{\sc i\kern-.025em b}\kern-.08em
    T\kern-.1667em\lower.7ex\hbox{E}\kern-.125emX}}
\begin{document}

\renewcommand{\figurename}{Hình}
\renewcommand{\tablename}{Bảng}
\renewcommand{\IEEEkeywordsname}{Keywords}
\renewcommand{\refname}{Tài liệu tham khảo}

\title{Ứng dụng thuật toán PPO trong điều khiển quadcopter bám quỹ đạo }

\author{\IEEEauthorblockN{1\textsuperscript{st} Phạm Thị Lý}
\IEEEauthorblockA{\textit{Khoa Điện - Điện tử} \\
\textit{Trường Đại học Giao thông Vận tải}\\
Hà Nội, Việt Nam \\
email: ptlydk@utc.edu.vn}
\and
\IEEEauthorblockN{2\textsuperscript{nd} Nguyễn Vinh Hoàng}
\IEEEauthorblockA{\textit{Khoa Điện - Điện tử} \\
\textit{Trường Đại học Giao thông Vận tải}\\
Hà Nội, Việt Nam \\
email: Vinhhoang2001k60@gmail.com}

}

\maketitle

\begin{abstract}
Bài báo này trình bày phương pháp điều khiển bám quỹ đạo waypoint cho quadcopter ứng dụng thuật toán Proximal 
Policy Optimization (PPO). Tác nhân PPO được xây dựng theo kiến trúc Actor--Critic, với trạng thái đầu vào 
gồm sai lệch vị trí tới waypoint hiện tại và kế tiếp, vận tốc tuyến tính, tư thế và vận tốc góc của quadcopter; 
đầu ra của chính sách là các lệnh vận tốc theo hệ tọa độ North--East--Down. Hàm phần thưởng gồm bốn thành phần: phần thưởng đạt waypoint, phần phạt vi phạm điều kiện an toàn, phần thưởng tiếp cận waypoint và phần thưởng căn chỉnh hướng vận tốc. Tác nhân được huấn luyện, đánh giá trong môi trường ProjectAirSim trên quỹ đạo hình vuông gồm chuỗi 
waypoint và phương pháp MoveOnPath sử dụng thuật toán carrot-following được sử dụng làm  tham chiếu. Kết quả mô phỏng cho thấy tác nhân PPO học cách điều khiển quadcopter bám quỹ đạo thành công
,và có đáp ứng vị trí nhanh hơn và đạt sai số bám quỹ đạo thấp hơn phương pháp tham chiếu trong điều kiện khảo sát. Tuy nhiên, đáp ứng tư thế của PPO biến 
lớn hơn  đặc biệt tại các vị trí cần quadcopter chuyển hướng.
\end{abstract}

\begin{IEEEkeywords}
quadcopter, bám quỹ đạo, học tăng cường sâu, Proximal Policy Optimization, ProjectAirSim
\end{IEEEkeywords}

\input{sections/Introduction/introduction.tex}
\input{sections/sectionII/sectionII.tex}
\input{sections/sectionIII/sectionIII.tex}
\input{sections/sectionIV/sectionIV.tex}
\input{sections/sectionV/sectionV.tex}
\input{sections/SectionVI/sectionVI.tex}
\input{sections/Reference/Reference.tex}
\end{document}
