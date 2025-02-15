---
title : "Upload-video-and-send-notification-to-other-service-when-video-upload-to-S3-is-complete"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

In this step, we will create a Lambda Function to generate a Presigned URL to upload the video to S3. Once the video has been uploaded to S3, it will use SNS to notify the completion of the video upload for other services to continue to perform their work.

### Contents 

- [Set up Lambda Function](4.1-Set-up-a-Lambda-function-to-create-presigned-URLs/) 
- [Setup SNS](4.2-Setup-SNS/)