---
title : "Tạo phụ đề và dịch phụ đề cho video với AWS Transcribe và AWS Translate"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---

### Tổng quan

 Khi xem một video bằng ngôn ngữ không quen thuộc hoặc không biết ngôn ngữ đó, bạn sẽ cần có phụ đề được dịch sang ngôn ngữ mà bạn hiểu. Đáp ứng nhu cầu này, chúng ta sẽ sử dụng kết hợp các dịch vụ mà AWS cung cấp để thực hiện việc tạo phụ đề và dịch phụ đề cho video. Sau cùng sẽ có được một video kèm theo phụ đề đã được dịch sang một ngôn ngữ quen thuộc giúp cho việc xem và hiểu nội dung của video dễ dàng hơn.
### Mục tiêu của Workshop hướng đến 
 Từ một video tiếng Anh và không có phụ đề, sau khi được xử lý để trích xuất phụ đề và dịch phụ đề sang tiếng Việt, kết thúc quá trình, chúng ta sẽ có một video hoàn chỉnh bằng tiếng Việt.
### Hạn chế của Worrkshop
 Tuy nhiên với Workshop này vẫn còn nhược điểm mà sau khi thực hiện Workshop sẽ thấy được là:
 - Quá trình upload video lên s3 chưa được tối ưu tốt, dẫn đến việc upload video diễn ra lâu và với video có thời lướng lớn thì quá trình này diễn ra lâu hơn nữa.
 - Nhận diện ngôn ngữ của video còn hạn chế, chỉ có video với ngôn ngữ tiếng anh.
 - Dịch phụ đề chỉ có từ tiếng anh sang tiếng việt.
### Hướng phát triển và cải tiến Workshop
 - Tối ưu hoá quá trình upload video
 - Hỗ trợ phụ đề và dịch phụ đề đa ngôn ngữ.


#### Nội dung

 1. [Giới thiệu.](1-introduce/)
 2. [Các bước chuẩn bị.](2-Preparation/)
 3. [Cài đặt S3.](3-Setup-S3/)
 4. [Tải video lên S3 và thông báo hoàn tất.](4-Upload-video-and-send-notification-to-other-server-when-video-upload-to-S3-is-complete/)
 5. [Tạo phụ đề, dịch và gửi thông báo.](5-Generate-subtitles-translate-subtitles-and-send-notification-to-frontend-when-done/)
 6. [Chạy thử trang web.](6-Test-website/)
 7. [Xoá tài nguyên.](6-Clean-Up-Resources/)
