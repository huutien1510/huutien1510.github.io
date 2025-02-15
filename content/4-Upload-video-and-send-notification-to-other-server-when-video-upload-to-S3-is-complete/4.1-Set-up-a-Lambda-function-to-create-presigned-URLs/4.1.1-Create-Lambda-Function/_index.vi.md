---
title : "Cài đặt Lambda tải lên video"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 4.1.1 </b> "
---


Bước này ta sẽ tạo một lambda để thực hiện sinh ra presigned URL.

## Tạo Lambda

Truy cập Bảng điều khiển AWS Lambda và chọn Tạo function.

![Upload](/images/4.uploadvideo/n.png)

Điền thông tin như bên dưới:

![Upload](/images/4.uploadvideo/n1.png)

{{% notice note %}}
Bạn có thế chọn ngôn ngữ khác nếu không quen với Python. Chọn kiến trúc arm 64 để được các nhiều hổ trợ hơn.
{{% /notice %}}

Chọn role đã tạo ở trước đó **``Role-ws-2024``**.

![Upload](/images/4.uploadvideo/n2.png)

Chọn **Create function**

Đã tạo xong function tiến hành code để thực hiện tạo url upload video.

Dán đoan code sau và ấn Deloy để triển khai code Lambda.

```python
import json
import boto3
import os

s3 = boto3.client('s3')

def lambda_handler(event, context):
    bucket_name = 'upload-object-ws-2024'
    folder_name = 'Video'
    file_name = event.get('fileName', 'video-default.mp4')
    file_type = 'video/mp4'


    s3_key = f"{folder_name}/{file_name}"

    try:

        s3.delete_object(Bucket=bucket_name, Key=s3_key)


        presigned_url = s3.generate_presigned_url('put_object',
                                                  Params={
                                                      'Bucket': bucket_name,
                                                      'Key': s3_key,
                                                      'ContentType': file_type
                                                  },
                                                  ExpiresIn=300)

        return {
            'statusCode': 200,
            'body': json.dumps({
                'uploadURL': presigned_url,
                'message': 'Pre-signed URL generated successfully'
            })
        }

    except s3.exceptions.NoSuchKey:
        
        presigned_url = s3.generate_presigned_url('put_object',
                                                  Params={
                                                      'Bucket': bucket_name,
                                                      'Key': s3_key,
                                                      'ContentType': file_type
                                                  },
                                                  ExpiresIn=300)

        return {
            'statusCode': 200,
            'body': json.dumps({
                'uploadURL': presigned_url,
                'message': 'File not found, pre-signed URL generated successfully'
            })
        }
    
    except Exception as e:
        return {
            'statusCode': 500,
            'body': json.dumps({
                'message': 'Error generating pre-signed URL',
                'error': str(e)
            })
        }
```

![Upload](/images/4.uploadvideo/n3.png)

Tạo function url, ở đây bạn có thể thay thế bằng cách dùng API để frontend gọi đến. Còn với workshop này thì sẽ sử dụng luôn function url để frontend gọi.

Có thể tìm hiểu thêm về Function URL: [Creating and managing Lambda function URLs](https://docs.aws.amazon.com/lambda/latest/dg/urls-configuration.html)

![Upload](/images/4.uploadvideo/n4.png)

Chọn NONE để Lambda sẽ không thực hiện xác thực IAM đối với các yêu cầu tới URL chức năng của bạn. Điểm cuối URL sẽ được công khai trừ khi bạn triển khai logic ủy quyền của riêng mình trong hàm của mình.

![Upload](/images/4.uploadvideo/n5.png)

Chọn **BUFFERED** sẽ giới hạn khích thước file tải lên là *6MB*

![Upload](/images/4.uploadvideo/n6.png)

Chọn **Save**

![Upload](/images/4.uploadvideo/n7.png)

Sau khi đã có url của Lambda thì frontend có thể gọi đến lambda để lấy presigned URL và tiến hành upload.

Với Lambda khi thực hiện việc upload video có thể xảy ra time out. Vì thế sẽ thực hiện cài đặt lại time out cho lambda.

{{% notice info %}}
3s là thời gian time out mặc định của Lambda và 15m là time out lớn nhất có thể cài đặt cho lambda. Thêm nữa Memory mặc định là 128MB và Storage mặc định là 512MB. Có thể cái đặt cho memory và storage.
{{% /notice %}}

![Upload](/images/4.uploadvideo/n8.png)

Cài đặt time out.

![Upload](/images/4.uploadvideo/n9.png)

Chọn **Save**

{{% notice info %}}
Việc sử dụng Lambda phù hợp cho công việc nhẹ không quá nặng vì sẽ dễ dẫn đến timeout do thời gian timeout của Lambda Function giới hạn 15 phút. Vì thế nếu sử dụng bạn cần tới ưu thêm để phù hợp với Lambda Function.
{{% /notice %}}