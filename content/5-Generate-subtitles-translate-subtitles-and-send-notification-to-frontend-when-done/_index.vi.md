---
title : "Tạo phụ đề, dịch phụ đề và gửi thông báo đến FrontEnd khi hoàn tất"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

Trong bước này, chúng ta sẽ thực hiện tạo ra các Lambda Function để thực hiện các công việc chính của workshop này.

- Lambda Function để khởi tạo Transcribe job
- Lambda Function để khởi tạo Translate job
- Lambda Function để thông báo đến FrontEnd khi các việc trên hoàn tất.

Tiếp đó sẽ tạo luồng cồn việc từ các lambda Function đã tạo để việc thực thi diễn ra một cách tự động bằng Step Function.

Để khích hoạt Step Function thì cần tạo thêm một Lambda Function để gọi đến khích hoạt Step Function khi việc tải video lên S3 hoàn tất.

### Nội dung

- [Thiết lập Lambda Function khởi tạo Transcribe job](5.1-Lambda-Function-initializes-Transcribe-job/)
- [Thiết lập Lambda Function khởi tạo Translate job](5.2-Lambda-Function-initializes-Translate-job/) 
- [Thiết lập Lambda Function thông báo đến FrontEnd](5.3-Lambda-Function-send-notification-to-FrontEnd/)
- [Thiết lập Step Function](5.4-Assemble-the-components-of-a-workflow-with-Step-Function/)
- [Thiết lập Lambda Function khích hoạt Step Function](5.5-Lambda-Function-triggers-workflow/)

