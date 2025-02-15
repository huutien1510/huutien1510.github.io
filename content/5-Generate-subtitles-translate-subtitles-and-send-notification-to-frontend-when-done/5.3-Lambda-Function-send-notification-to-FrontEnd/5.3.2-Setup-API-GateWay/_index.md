---
title : "Create API Gateway"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 5.3.2 </b> "
---

Go to the API gateway control page and select create API

![Upload](/images/7.notify/n.png)

Use Rest API (public).

![Upload](/images/7.notify/n1.png)

Get the following information:

![Upload](/images/7.notify/n2.png)

Create resource.

{{% notice note %}}
/ is the root directory where resources will be created.
{{% /notice %}}

![Upload](/images/7.notify/n3.png)

Enter Resource name **``notify``**.

![Upload](/images/7.notify/n4.png)

Create Method.

![Upload](/images/7.notify/n5.png)

Select the correct Lambda to perform notification to the frontend.

![Upload](/images/7.notify/n6.png)

Enable CORS.

{{% notice note %}}
Select the resource that has the newly created method to enable CORS.

{{% /notice %}}

![Upload](/images/7.notify/n7.png)

Select the value fields.

![Upload](/images/7.notify/n8.png)

Deploy the API with an optional name: **``dev``**.

![Upload](/images/7.notify/n9.png)

Get the API url.

![Upload](/images/7.notify/n10.png)

With this Url, paste it into the api_url value section in the Lambda-Notify code. And at the same time provide the API to the frontend.