# Cấu trúc dự án

Dự án này chứa mã nguồn LaTeX của bài báo IEEE về ứng dụng thuật toán PPO trong điều khiển quadcopter bám quỹ đạo.

## Cây thư mục

```text
revecit/
├── .gitignore                        # Danh sách tệp không đưa lên GitHub
├── paper.tex                         # Tệp LaTeX chính, ghép toàn bộ bài báo
├── paper.md                          # Bản Markdown dễ đọc của toàn bộ bài báo
├── REVIEW.md                         # Nội dung phản biện của bài báo
├── sections/                         # Nội dung từng phần của bài báo
│   ├── Introduction/
│   │   ├── introduction.tex          # Phần I: Giới thiệu
│   │   └── introduction.md           # Bản Markdown phục vụ chỉnh sửa
│   ├── sectionII/
│   │   ├── sectionII.tex             # Phần II: Xây dựng bài toán
│   │   └── sectionII.md              # Bản Markdown phục vụ chỉnh sửa
│   ├── sectionIII/
│   │   ├── sectionIII.tex            # Phần III: Thiết kế bộ điều khiển PPO
│   │   └── sectionIII.md             # Bản Markdown phục vụ chỉnh sửa
│   ├── sectionIV/
│   │   ├── sectionIV.tex             # Phần IV: Thiết lập mô phỏng và thử nghiệm
│   │   └── sectionIV.md              # Bản Markdown phục vụ chỉnh sửa
│   ├── sectionV/
│   │   ├── sectionV.tex              # Phần V: Kết quả
│   │   └── sectionV.md               # Bản Markdown phục vụ chỉnh sửa
│   ├── SectionVI/
│   │   ├── sectionVI.tex             # Phần VI: Kết luận
│   │   └── sectionVI.md              # Bản Markdown phục vụ chỉnh sửa
│   └── Reference/
│       ├── Reference.tex             # Danh mục tài liệu tham khảo
│       └── Reference.md              # Bản Markdown phục vụ chỉnh sửa
├── Figure/                            # Hình ảnh được sử dụng trong bài báo
│   ├── image.png
│   ├── image2.png
│   ├── Picture1.png
│   ├── Picture11.png
│   ├── Picture 2a.png
│   ├── Picture 2b.png
│   ├── Picture 3a.png
│   ├── Picture 3b.png
│   ├── Picture 4a.png
│   └── Picture 4b.png
├── Table/                             # Các bảng LaTeX được chèn vào bài báo
│   ├── table1.tex                    # Tham số huấn luyện PPO
│   └── table2.tex                    # Bảng kết quả đánh giá
├── paper.pdf                          # Bản PDF được tạo khi biên dịch
├── paper.aux                          # Tệp phụ trợ của LaTeX
├── paper.bbl                          # Dữ liệu tài liệu tham khảo đã xử lý
├── paper.fdb_latexmk                  # Dữ liệu theo dõi của latexmk
├── paper.fls                          # Danh sách tệp được dùng khi biên dịch
├── paper.log                          # Nhật ký biên dịch
├── paper.synctex.gz                   # Dữ liệu đồng bộ giữa mã nguồn và PDF
└── *.bak                              # Các bản sao lưu của tệp LaTeX
```

## Quan hệ giữa các tệp

`paper.tex` là điểm bắt đầu của dự án. Tệp này khai báo mẫu `IEEEtran`, các gói LaTeX, tiêu đề, tác giả và lần lượt nạp nội dung trong `sections/` bằng lệnh `\input{...}`.

Các phần nội dung sử dụng:

- Hình ảnh trong `Figure/` thông qua `\includegraphics{...}`.
- Bảng trong `Table/` thông qua `\input{Table/table1.tex}` và `\input{Table/table2.tex}`.
- Tài liệu tham khảo được viết trực tiếp trong `sections/Reference/Reference.tex` bằng môi trường `thebibliography`.

## Quy ước chỉnh sửa

- Chỉnh cấu hình chung, tiêu đề, tác giả hoặc thứ tự các phần trong `paper.tex`.
- `paper.md` là bản trình bày toàn bộ bài báo theo Markdown để đọc trên GitHub; LaTeX không tự đọc các thay đổi trong tệp này.
- Chỉnh nội dung bài báo trong tệp `.tex` tương ứng thuộc `sections/`.
- Các tệp `.md` trong `sections/` trình bày nội dung của tệp `.tex` cùng tên theo định dạng dễ đọc trên GitHub. LaTeX không tự đọc các tệp này, vì vậy thay đổi cần được đồng bộ lại vào tệp `.tex` trước khi biên dịch.
- Chỉnh dữ liệu bảng trong `Table/` và thay hình trong `Figure/`.
- Không chỉnh trực tiếp `paper.pdf`, các tệp phụ trợ biên dịch hoặc các tệp `*.bak`.
- Giữ nguyên chữ hoa, chữ thường và khoảng trắng trong đường dẫn vì mã nguồn đang tham chiếu đúng theo các tên hiện tại.

