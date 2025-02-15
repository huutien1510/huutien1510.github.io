---
title : "Tạo IAM Role"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

## Tạo Role

Truy cập vào IAM và tạo Role

![Preparation](/images/2.prerequisite/n1.png)

Chọn service cần dùng

![Preparation](/images/2.prerequisite/n2.png)

Gán policy của **Lambda** cho role, chọn policy với đầy đủ các của **Lambda**.

![Preparation](/images/2.prerequisite/n3.png)

Gán policy của **S3** cho role, chọn policy với đầy đủ các quyền của **S3**.

![Preparation](/images/2.prerequisite/n4.png)

Gán policy của **API GateWay** cho role, chọn policy với đầy đủ các quyền của **API GateWay**.

![Preparation](/images/2.prerequisite/n5.png)

Gán policy của **SNS** cho role.

![Preparation](/images/2.prerequisite/n6.png)

Gán policy của **Transcribe** cho role.

![Preparation](/images/2.prerequisite/n7.png)

Gán policy của **Translate** cho role.

![Preparation](/images/2.prerequisite/n8.png)

Nhận tên role **`Role-ws-2024`**.

![Preparation](/images/2.prerequisite/n9.png)

Kiểm tra lại policy của các service cần đã đủ chưa. Nếu đủ thì hoàn thành tạo Role.

![Preparation](/images/2.prerequisite/n10.png)

![Preparation](/images/2.prerequisite/n11.png)

Khi muốn gán thêm policy cho role đã tạo thì chọn role cần gán policy.

![Preparation](/images/2.prerequisite/n12.png)

Gán thêm policy.

![Preparation](/images/2.prerequisite/n14.png)

Chọn policy **Step Function**.

![Preparation](/images/2.prerequisite/n17.png)

**Tạo Role và gán các policy của service cho role đã hoàn thành**.


