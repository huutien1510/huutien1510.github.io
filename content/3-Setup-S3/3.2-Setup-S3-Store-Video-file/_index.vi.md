---
title : "Thiết lập S3 để lưu tệp video"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 3.2 </b> "
---


## Tạo Bucket

Tạo Bucket để lưu file các bước đầu giống với Tạo Bucket để lưu file code của web, tuy nhiêu sẽ không cấu hình Static website hosting.

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n.png)

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n1.png)

Để quản lý file Video được gọn hơn thì, ta sẽ tao một floder trong bucket.

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n2.png)

Tạo floder với tên **`Video`**

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n3.png)

Chọn **Create folder**

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n4.png)

Do các object của bucket này sẽ được truy cập trông qua lambda và api nên cần cấu hình thêm CORS.

Cross-origin resource sharing (CORS) xác định cách để các ứng dụng web của khách hàng được tải trong một miền tương tác với các tài nguyên trong một miền khác. [CORS](https://docs.aws.amazon.com/AmazonS3/latest/userguide/enabling-cors-examples.html?icmpid=docs_amazons3_console)

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n5.png)

Dán đoạn code sau:

```json
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "PUT",
            "GET",
            "DELETE"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": [
            "ETag"
        ]
    }
]
```

*"AllowedHeaders": [ "*" ]* là danh sách các tiêu đề HTTP mà trình duyệt có thể gửi trong một yêu cầu từ các nguồn khác (cross-origin request). Dấu * cho phép tất cả các tiêu đề HTTP

*"AllowedMethods": ["PUT", "GET", "DELETE"]* là danh sách các phương thức HTTP được phép khi gửi yêu cầu đến S3 từ các nguồn khác.

*"AllowedOrigins": [ "*" ]* là danh sách các nguồn (origin) được phép truy cập vào S3 bucket. Dấu * có nghĩa là mọi nguồn gốc đều được phép truy cập, tức là cho phép tất cả các trang web từ bất kỳ domain nào thực hiện yêu cầu đến S3 bucket.

*"ExposeHeaders": ["ETag"]* là danh sách các tiêu đề HTTP mà trình duyệt có thể truy cập từ phản hồi của S3. ETag là một tiêu đề HTTP cho phép trình duyệt biết phiên bản của một tệp, thường được sử dụng để xác định sự thay đổi của tài nguyên.

Cuối cùng chọn **Save changes**