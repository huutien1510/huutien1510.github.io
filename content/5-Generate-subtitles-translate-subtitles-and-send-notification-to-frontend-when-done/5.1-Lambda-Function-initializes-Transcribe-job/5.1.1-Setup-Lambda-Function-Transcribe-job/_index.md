---
title : "Lambda Transcribe"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 5.1.1 </b> "
---

## Create Lambda

Create function.

Enter the information as shown:

![Upload](/images/5.transcribe/n.png)

Select **Create function**

![Upload](/images/5.transcribe/n1.png)

Paste the following code:

```python
import json
import boto3
import time

s3 = boto3.client('s3')
transcribe = boto3.client('transcribe')

def lambda_handler(event, context):

    bucket_name = 'upload-object-ws-2024'
    video_key = 'Video/video-default.mp4'
    output_bucket = 'ws-file-sub-video'
    
    job_name = "subtitle"
    media_uri = f"s3://{bucket_name}/{video_key}"

    try:

        response = s3.list_objects_v2(Bucket=output_bucket)
        

        if 'Contents' in response:
            delete_keys = [{'Key': obj['Key']} for obj in response['Contents']]
            s3.delete_objects(
                Bucket=output_bucket,
                Delete={
                    'Objects': delete_keys,
                    'Quiet': True
                }
            )
    except Exception as e:
        return {
            'statusCode': 500,
            'body': json.dumps(f'Error deleting old files: {str(e)}')
        }
    try:
        s3.delete_objects(Bucket='ws-translate', Delete={'Objects': [{'Key': 'translated_subtitle.vtt'}]})
    except Exception as e:
        print(f"Error deleting old file: {e}")
    

    response = transcribe.start_transcription_job(
        TranscriptionJobName=job_name,
        Media={'MediaFileUri': media_uri},
        MediaFormat='mp4',
        LanguageCode='en-US',
        Subtitles={'Formats': ['vtt']},
        OutputBucketName=output_bucket
    )
    

    while True:
        job = transcribe.get_transcription_job(TranscriptionJobName=job_name)
        if job['TranscriptionJob']['TranscriptionJobStatus'] in ['COMPLETED', 'FAILED']:
            break
        time.sleep(5)
    

    if job['TranscriptionJob']['TranscriptionJobStatus'] == 'COMPLETED':
        transcribe.delete_transcription_job(TranscriptionJobName=job_name)
        return {
            'statusCode': 200,
            'body': json.dumps('Transcription completed successfully and job deleted!')
        }
    else:
        return {
            'statusCode': 500,
            'body': json.dumps('Transcription failed!')
        }
```

Finally select **Deloy**

Done creating lambda function to create Transcribe job.