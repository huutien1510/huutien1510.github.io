---
title : "Lambda Translate"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 5.2.1 </b> "
---


## Tạo Lambda

Thực hiện tạo function.

Nhập các thông tin như hình:

![Upload](/images/6.translate/n.png)

Chọn **Create function**

![Upload](/images/6.translate/n1.png)

Dán đoạn code sau:

```python
import json
import boto3

s3_client = boto3.client('s3')
translate_client = boto3.client('translate')

def lambda_handler(event, context):

    source_bucket = 'ws-file-sub-video'
    source_key = 'subtitle.vtt'
    
    destination_bucket = 'ws-translate'
    destination_key = 'translated_subtitle.vtt'
    

    
    vtt_file = s3_client.get_object(Bucket=source_bucket, Key=source_key)
    vtt_content = vtt_file['Body'].read().decode('utf-8')
    
    
    txt_content = convert_vtt_to_txt(vtt_content)
    
    
    translated_text = translate_text(txt_content, 'en', 'vi')
    
    
    s3_client.put_object(
        Bucket=destination_bucket, 
        Key=destination_key, 
        Body=translated_text
    )
    
    return {
        'statusCode': 200,
        'body': json.dumps('Translation complete and uploaded to S3!')
    }

def convert_vtt_to_txt(vtt_content):
    lines = vtt_content.splitlines()
    txt_content = []
    for line in lines:
        txt_content.append(line.strip())
    return '\n'.join(txt_content)

def translate_text(text, source_lang, target_lang):
    response = translate_client.translate_text(
        Text=text,
        SourceLanguageCode=source_lang,
        TargetLanguageCode=target_lang
    )
    return response['TranslatedText']
```

Cuối cùng chọn **Deloy**


Đã hoàn thành tạo lambda function để tạo Translate job.