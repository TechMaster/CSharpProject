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

*Gợi ý:*
- Tạo bộ dữ liệu mẫu trước, một số folder
- Làm bằng tay từng bước một trước, sau khi làm thủ công xong, mới chuyển sang viết code
- Hãy dùng phương pháp đệ quy ```treelist(string folder_path, int level)``` hoặc ```treelist(string folder_path, string pad_str)```
- Chú ý dùng ký tự đặc biệt trong [bảng mã ASCII](https://www.asciitable.com/) để vẽ pipe.



# Bài 2: Nén file âm nhạc Flac sang mp3
Flac là chuẩn nén loss less, giữ nguyên chất lượng âm nhạc từ đầu thu. Mp3 là chuẩn nén lossy, chất lượng âm thanh bị suy hao (không sắc nét) nhưng bù lại dung lượng file giảm gần 1/10 so với Flac.

Công cụ để nén file Flac xuống mp3 là [FFmpeg](https://www.ffmpeg.org/).

Yêu cầu: thầy Cường có một thư mục chưa cực nhiều file flac, dung lượng khoảng 20Gb. Máy nghe nhạc Sony Walkman của thầy Cường lại không chơi được định dạng Flac ngoài ra, máy nghe nhạc chỉ có dung lượng 4GB, hãy viết ứng dụng console bằng C# nén tất cả những file Flac sang mp3 với yêu cầu như sau:
1. Không xoá những file Flac
2. Chuyển những file mp3 sau khi nén xong ra thư mục riêng, nhưng cấu trúc đường dẫn tương đối phải như ban đầu
3. Tốc độ nén càng nhanh càng tốt
4. Nếu có lỗi thì phải ghi ra file log.txt đường đến file bị lỗi.

*Gợi ý*
1. Việc convert flac sang mp3 phải dùng ứng dụng FFmpeg. Ứng dụng này sẽ chạy ở một process riêng. Thời gian convert có thể lâu do đó nên dùng kỹ thuật queue và multi-thread.
2. Nên quét tất cả các file flac rồi cho vào một queue, mỗi phần tử là một struct chứa têntên file flac cần convert. Cần thêm một biến trạng thái để mô tả tiến độ convert: 
  - chưa convert
  - đang convert
  - convert xong
  - convert lỗi
