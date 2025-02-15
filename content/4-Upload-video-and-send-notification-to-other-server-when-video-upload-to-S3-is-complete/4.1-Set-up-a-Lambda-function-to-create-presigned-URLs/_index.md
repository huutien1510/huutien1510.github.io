---
title : "Set Up lambda"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---


To upload videos to s3, in this workshop we will use Lambda to upload videos to S3 using presigned URLs.

A presigned URL is a URL that you can provide to your users to grant temporary access to a specific S3 object. Using the URL, users can read and write objects (or update existing objects). The URL contains specific parameters set by the application you install. Presigned URLs use three parameters to limit access to users:

- Bucket: Contains objects - where the object is located.

- Key: The name of the object.

- Expires: the duration of the URL.

Use Lambda to create a Presigned URL. And we use a single file to upload, so the challenge limit will be *5GB*

Alternatively, you can upload videos faster by using multiupload combined with presigned URLs. Then the uploaded video will be split into smaller parts for uploading.

### Content:

- [Create Lambda Function](./4.1-Create-Lambda/)