---
title : "Tải video lên và gửi thông báo đến service khác khi quá trình tải video lên S3 hoàn tất"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

Trong bước này, chúng ta sẽ thực hiện tạo Lambda Function sinh Presigned URL để thực hiện việc tải video lên S3. Khi video đã được tải lên S3 sẽ sử dụng SNS để thông báo hoàn thành tải video lên cho các service khác tiếp sau thực hiện công việc của nó.

### Nội dung

- [Thiết lập Lambda Function](4.1-Set-up-a-Lambda-function-to-create-presigned-URLs/)
- [Thiết lập SNS](4.2-Setup-SNS/) 

