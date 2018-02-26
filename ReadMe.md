# Bài tập thực hành dành cho lớp thực tập C#

## Yêu cầu chung
1. Code dự án cần đẩy lên github có đầy đủ ghi chú (comment), mô tả dự án. Chỉ push code lên github khi đã chạy kiểm thử kỹ.
2. Mỗi project cần có một file ReadMe.md tóm tắt các thông tin:
  - Yêu cầu bài toán là gì? Copy lại từ giảng viên
  - Cách chạy ứng dụng
  - Mô tả kiến trúc ứng dụng hay những phần cốt lõi thuật toán
  - Nếu sử dụng thư viện ngoài quan trọng cần ghi chú và cung cấp đường link
3. Nếu cần hãy vẽ diagram sử dụng LucidChart hoặc PowerPoint Draw

# Bài 1: Liệt kê thư mục và file
Trong Linux có một ứng dụng nổi tiếng có tên là tree để liệt kê toàn bộ thư mục và thư mục con + file
```
$ tree .
.
├── ReadMe.md
└── folderA
    ├── demo.cs
    ├── folderAA
    │   └── file.cs
    └── util.cs
```
Hãy viết một ứng dụng bằng C# nhận vào tham số là đường dẫn thư mục sau đó liệt kê toàn bộ nội dung thư mục đó.
Chú ý nếu tham số là
- . liệt kê thư mục hiện thời
- .. liệt kê thư mục cha
- ~ liệt kê thư mục người dùng 