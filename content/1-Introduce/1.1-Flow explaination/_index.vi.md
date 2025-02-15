---
title : "Giải thích luồng"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1.1 </b> "
---

## Giải thích luồng chạy hệ thống

Trong hình bên dưới, đây là kiến trúc và luồng vận hành. Đầu tiến người dùng sẽ truy cập vào website tĩnh được lưu và host trong s3. Khi người dùng thực hiện hành động upload video lên sẽ gọi đến Lambda Function(Upload Video) để thực hiện việc upload video vào trong S3 để lưu trữ. Có một đối tượng được thêm vào S3 hoàn thành. SNS phát thông báo đén các dịch vụ khác trong hệ thống, ở đây làm Lambda Function(Call Step Function) điều này khích hoạt các quy trình xử lý tiếp theo một cách tự động. Khi Lambda Function(Call Step Function) được khích hoạt trigger là SNS thì sẽ thực hiện việc gọi đến Step Function để thực hiện luồng công việc từ tạo phụ đề từ việc trích video lấy phụ đề và thực hiện dịch phụ đề đó. Chi tiết luồng công việc trong Step Function sẽ diễn ra như sau:
- Đầu tiên sẽ gọi Lambda Function(Create job Transcribe), lambda function sẽ thực hiện việc lấy vidoe đã được người dùng tải vào S3 ban đầu sau đó tiến hành khởi tạo công việc của Transcribe là cấu hình TranscriptionJobName, Media(là video được lưu trong s3), MediaFormat(định dạng của viddeo), LanguageCode(Ngôn ngữ của video), Subtitles(định dạng file phụ đề .vtt), OutputBucketName. Kế tiếp là Trancribe tiến hành thực hiện công việc đã được tạo, lưu file kết quả vào S3.
- Tiếp theo sau khi đã hoàn thành việc tạo phụ đề thì bước kế tiếp là gọi đến Lambda Function(Create job Translate from video subtitles) để thực hiện lấy file phụ đề của video vừa được tạo và khởi tạo công việc cho Translate. Sau đó Translate sẽ thực hiện công việc được tạo và lưu file kết quả vào S3.
- Cuối cùng khi các công việc chính đã hoàn thành thì sẽ gọi Lambda Function cuối cùng để gợi API Gateway để gửi thông báo đã hoàn thành xong phụ đề để phía fronted thực hiện phát video có kèm phụ đã được xử lý.

![s1](/images/1.Introduce/architec.png)
