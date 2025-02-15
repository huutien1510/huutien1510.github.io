---
title : "Create IAM ROLE"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

## Create Role

Access IAM and create Role

![Preparation](/images/2.prerequisite/n1.png)

Select the service you want to use

![Preparation](/images/2.prerequisite/n2.png)

Assign **Lambda** policy to the role, choose the policy with full **Lambda** permissions.

![Preparation](/images/2.prerequisite/n3.png)

Assign **S3** policy to the role, choose the policy with full **S3** permissions.

![Preparation](/images/2.prerequisite/n4.png)

Assign **API GateWay** policy to the role, choose the policy with full **API GateWay** permissions.

![Preparation](/images/2.prerequisite/n5.png)

Assign **SNS** policy to the role.

![Preparation](/images/2.prerequisite/n6.png)

Assign the policy of **Transcribe** to the role.

![Preparation](/images/2.prerequisite/n7.png)

Assign the policy of **Translate** to the role.

![Preparation](/images/2.prerequisite/n8.png)

Get the role name **`Role-ws-2024`**.

![Preparation](/images/2.prerequisite/n9.png)

Check if the policies of the required services are complete. If so, complete the creation of the Role.

![Preparation](/images/2.prerequisite/n10.png)

![Preparation](/images/2.prerequisite/n11.png)

When you want to assign more policies to the created role, select the role to assign the policy to.

![Preparation](/images/2.prerequisite/n12.png)

Assign additional policies.

![Preparation](/images/2.prerequisite/n14.png)

Select the **Step Function** policy.

![Preparation](/images/2.prerequisite/n17.png)

**Create Role and assign service policies to completed role**.