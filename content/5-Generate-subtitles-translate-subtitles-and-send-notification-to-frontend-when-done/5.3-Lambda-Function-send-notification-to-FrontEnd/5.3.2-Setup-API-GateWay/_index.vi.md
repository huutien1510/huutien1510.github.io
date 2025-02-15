---
title : "Tạo API GateWay"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.3.2 </b> "
---


Đến trang điều khiển của API gateway chọn create API

![Upload](/images/7.notify/n.png)

Sử dụng Rest API (public).

![Upload](/images/7.notify/n1.png)

Nhận thông tin như sau:

![Upload](/images/7.notify/n2.png)

Tạo resource.

{{% notice note %}}
/  là thư mục gốc sẽ tạo các resouce trong đây.
{{% /notice %}}

![Upload](/images/7.notify/n3.png)

Nhập Resource name **``notify``**.

![Upload](/images/7.notify/n4.png)

Tạo Method.

![Upload](/images/7.notify/n5.png)

Chọn đúng Lambda thực hiện thông báo đến frontend.

![Upload](/images/7.notify/n6.png)

Bật CORS.

{{% notice note %}}
Chọn vào resource chứa method vừa tạo đề bật CORS.
{{% /notice %}}

![Upload](/images/7.notify/n7.png)

Chọn các trường giá trị.

![Upload](/images/7.notify/n8.png)

Triển khai API với tên tuỳ chọn: **``dev``**.

![Upload](/images/7.notify/n9.png)

Lấy url API.

![Upload](/images/7.notify/n10.png)

Với Url này sẽ dán vào phần giá trị api_url trong code của Lambda-Notify.Và đồng thời cấp  API cho frontend.