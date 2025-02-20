---
title : "Setup SNS"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

With SNS used to send notifications when a new video is uploaded to S3. SNS broadcasts notifications to other services in the system (in wrkshop, lambda), ensuring that all relevant components are notified of the new event. This triggers the video processing process automatically and promptly.

## Create SNS

Go to the Amazon SNS Console and enter the topic name **`video-procesing-topic`**, then select Next step.

![Upload](/images/9.sns/n.png)

Select **Standard**, then select **Create topic**.

![Upload](/images/9.sns/n1.png)

Go to the newly created SNS and select **edit**

![Upload](/images/9.sns/n2.png)

### Policy settings

{{% notice note %}}
Add a comma after the enclosed curly brackets to add another policy code.

{{% /notice %}}

![Upload](/images/9.sns/n3.png)

Paste the following code:

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

**ARN of the Topic** is replaced with the ARN of the SNS currently configured.

![Upload](/images/9.sns/n4.png)

**ARN of the S3 Bucket** is replaced with the ARN of the input bucket, which is the bucket containing the uploaded video file.

![Upload](/images/9.sns/n5.png)

Select **Save changes**

In order for SNS to know that an object is saved to the bucket, additional settings must be made in the input bucket.

Go to the input bucket **upload-video-workshop-fcj**. Select **Properties**.

![Upload](/images/9.sns/n6.png)

Fill in the information as follows:

![Upload](/images/9.sns/n7.png)

![Upload](/images/9.sns/n8.png)

Finally select **Save changes**