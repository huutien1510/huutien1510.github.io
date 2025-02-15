---
title : "Cài đặt Step Function"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---


Step Function sẽ giúp xây dựng workflow kết nối các Lambda như : Lambda-Transcribe, Lambda-Translate, Lambda-Notify đã tạo ở các bước trước.

## Cài đặt

Đến trang điều khiển cảu Step Function và Get started.

![Upload](/images/8.stepfun/n.png)

Chọn các service cần thiết.

{{% notice note %}}
Chọn một service cần dùng rồi kéo vào vị trí **Drag first state here**. Với các service tiếp theo kéo vào và để ở trí bên dưới service trước đó.
{{% /notice %}}

![Upload](/images/8.stepfun/n1.png)

Cài đặt chi tiết cho từng service.

+ **Lambda - Transcribe.**

![Upload](/images/8.stepfun/n2.png)

{{% notice info %}}
Chọn đúng Function name khớp với từng lambda service mà bạn đang cài đặt.
{{% /notice %}}

+ **Lambda - Translate.**

![Upload](/images/8.stepfun/n3.png)

+ **Lambda - Notify.**

![Upload](/images/8.stepfun/n4.png)

Cài đặt time out cho worlflow để tránh khi thời gian chạy vướt quá thời gian cài đặt thì worlflow sẽ thực hiện không thành công các công việc tiếp theo trong step function.

![Upload](/images/8.stepfun/n5.png)

Với mỗi lần chạy worlflow trong một step function nó tạo ra một **Excutions** và nếu Excutions bị time out thì có thể thực hiện chạy lại Excutions đó.

Có bảng liệt kế các Excutions  có thông tin liên quan đến Excutions.

![Upload](/images/8.stepfun/n6.png)

Cuối cùng sẽ copy ARN của step function này để thực hiện gọi đến Step Function bằng lambda ở bước tiếp theo.

![Upload](/images/8.stepfun/n7.png)