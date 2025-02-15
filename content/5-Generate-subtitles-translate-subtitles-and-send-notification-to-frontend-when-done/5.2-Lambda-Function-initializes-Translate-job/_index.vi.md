---
title : "Translate"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---


Sử dụng Lambda để gọi AWS Translate thực hiện dịch phụ đề được lấy trong bucket ws-file-sub-video.
Và AWS Translate dịch file tối đã là *20MB* với định dạng *text (.txt), HTML (.html), Word (.docx), Excel (.xlsx), PowerPoint (.pptx) and XLIFF 1.2 (.xlf)* và hỗ trợ tối đa *1,000,000 file* cùng một đợt. Amazon Translate cung cấp nội dung đầu ra dưới dạng tệp. Định dạng tệp cho mỗi tệp đầu ra khớp với định dạng tệp đầu vào.
Tuy nhiên khi sử dụng làm phụ đề cho video được đơn giản hơn thì có thể dùng lambda để chuyển đổi định dạng file đầu ra của Amazon Translate thành định dạng .vtt đồng đợi là cũng chuyển đổi định dạng file phụ đề từ .vtt sang .txt để đúng định dạng đầu vào của Amazon Translate.

Workshop này sẽ thực hiện dịch từ ngôn ngữ tiếng anh sang tiếng việt.


## Nội dung:

- [Tạo Lambda Function](./6.1-Lambda-Transl/)

