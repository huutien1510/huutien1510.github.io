---
title : "Set up S3 to save video files"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

## Create Bucket

Create a Bucket to save files, the first steps are similar to Create a Bucket to save web code files, however, Static website hosting will not be configured.

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n.png)

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n1.png)

To manage Video files more neatly, we will create a folder in the bucket.

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n2.png)

Create folder with name **`Video`**

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n3.png)

Select **Create folder**

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n4.png)

Since the objects of this bucket will be accessed through lambda and api, additional CORS configuration is required.

Cross-origin resource sharing (CORS) defines how client web applications loaded in one domain interact with resources in another domain. [CORS](https://docs.aws.amazon.com/AmazonS3/latest/userguide/enabling-cors-examples.html?icmpid=docs_amazons3_console)

![Sep-Up-S3](/images/3.setupS3/3.2.ima/n5.png)

Paste the following code:

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

*"AllowedHeaders": [ "*" ]* is a list of HTTP headers that the browser can send in a request from other sources (cross-origin request). The * allows all HTTP headers

*"AllowedMethods": ["PUT", "GET", "DELETE"]* is a list of HTTP methods that are allowed when making requests to S3 from other sources.

*"AllowedOrigins": [ "*" ]* is a list of origins that are allowed to access the S3 bucket. The * means that all origins are allowed, which means that all websites from any domain are allowed to make requests to the S3 bucket.

*"ExposeHeaders": ["ETag"]* is a list of HTTP headers that the browser can access from the S3 response. ETag is an HTTP header that tells the browser the version of a file, often used to identify changes to a resource.

Finally select **Save changes**