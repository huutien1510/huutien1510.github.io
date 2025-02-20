---
title : "Set Lambda Upload Video"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1.1 </b> "
---


In this step, we will create a lambda to generate the presigned URL.

## Create Lambda

Go to the AWS Lambda Console and select Create function.

![Upload](/images/4.uploadvideo/n.png)

Fill in the information as below:

![Upload](/images/4.uploadvideo/n1.png)

{{% notice note %}}
You can choose another language if you are not familiar with Python. Choose the arm 64 architecture for more support.

{{% /notice %}}

Select the previously created role **``WorkshopFCJ``**.

![Upload](/images/4.uploadvideo/n2.png)

**Create function**

After creating the function, proceed to code to create the video upload url.

Paste the following code and press Deloy to deploy the Lambda code.

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

Create a function url, here you can replace it with an API for the frontend to call. For this workshop, we will use the function url for the frontend to call.

You can learn more about Function URLs: [Creating and managing Lambda function URLs](https://docs.aws.amazon.com/lambda/latest/dg/urls-configuration.html)

![Upload](/images/4.uploadvideo/n4.png)

Choose NONE so that Lambda will not perform IAM authentication for requests to your function URL. The URL endpoint will be public unless you implement your own authorization logic in your function.

![Upload](/images/4.uploadvideo/n5.png)

Selecting **BUFFERED** will limit the upload file size to *6MB*

![Upload](/images/4.uploadvideo/n6.png)

Select **Save**

![Upload](/images/4.uploadvideo/n7.png)

Once you have the Lambda url, the frontend can call the lambda to get the presigned URL and proceed with the upload.

With Lambda, when uploading videos, time out may occur. Therefore, reset the time out for lambda.

{{% notice info %}}
3s is the default time out for Lambda and 15m is the maximum time out that can be set for lambda. In addition, the default Memory is 128MB and the default Storage is 512MB. You can set the memory and storage.
{{% /notice %}}

![Upload](/images/4.uploadvideo/n8.png)

Set the time out.

![Upload](/images/4.uploadvideo/n9.png)

Select **Save**

{{% notice info %}}
Using Lambda is suitable for light work that is not too heavy because it will easily lead to timeout due to the timeout time of Lambda Function being limited to 15 minutes. Therefore, if you use it, you need to optimize it to suit Lambda Function.
{{% /notice %}}