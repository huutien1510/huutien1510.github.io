---
title : "Cài đặt SNS"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

Với SNS sử dụng để gửi thông báo khi có video mới được tải lên S3. SNS phát thông báo tới các dịch vụ khác trong hệ thống (trong wrkshop là lambda), đảm bảo rằng tất cả các thành phần liên quan đều được thông báo về sự kiện mới. Điều này kích hoạt quy trình xử lý video một cách tự động và kịp thời.

## Tạo SNS

Đi tới Bảng điều khiển Amazon SNS và nhập tên chủ đề **`video-procesing-topic`**, sau đó chọn Next step.

![Upload](/images/9.sns/n.png)

Chọn **Standard**, sau đó chọn **Create topic**.

![Upload](/images/9.sns/n1.png)

Vào SNS vừa tạo chọn **edit**

![Upload](/images/9.sns/n2.png)

### Cài đặt policy

{{% notice note %}}
Thêm dấu phẩy sau giấu ngoặc nhọn được khoanh vùng để thêm đoạn code policy khác.
{{% /notice %}}

![Upload](/images/9.sns/n3.png)

dán đoạn code sau:

```json
{
	"Sid": "S3 notification to SNS",
	"Effect": "Allow",
	"Principal": {
		"Service": "s3.amazonaws.com"
	},
	"Action": "sns:Publish",
	"Resource": "<ARN of the Topic>",
	"Condition": {
		"ArnLike": {
			"AWS:SourceArn": "<ARN of the S3 Bucket>"
		}
	}
}
```

**ARN of the Topic** thay bằng ARN của SNS đang cấu hình.

![Upload](/images/9.sns/n4.png)

**ARN of the S3 Bucket** thay bằng ARN của bucket đầu vào là bucket chứa file video được upload.

![Upload](/images/9.sns/n5.png)

Chọn **Save change**

Để SNS có thể biết có một object được lưu vào bucket thì sẽ phải cài đặt thêm ở bucket đầu vào.

Đến bucket đầu vào **upload-object-ws-2024**. Chọn **Properties**.

![Upload](/images/9.sns/n6.png)

Điền thông tin như sau:

![Upload](/images/9.sns/n7.png)

![Upload](/images/9.sns/n8.png)

Cuối cùng chọn **Save changes**






