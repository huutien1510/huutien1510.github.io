---
title : "Flow explaination"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1.1 </b> "
---
## System Flow Explanation

In the figure below, this is the architecture and operation flow. First, the user will access the static website saved and hosted in s3. When the user performs the action of uploading a video, it will call the Lambda Function (Upload Video) to upload the video to S3 for storage. There is an object added to S3 completed. SNS sends a notification to other services in the system, here doing Lambda Function (Call Step Function) this triggers the next processing steps automatically. When the Lambda Function (Call Step Function) is activated, the trigger is SNS, it will call the Step Function to perform the workflow from creating subtitles from extracting videos to get subtitles and translating those subtitles. The detailed workflow in Step Function will take place as follows:
- First, call Lambda Function (Create job Transcribe), lambda function will perform the task of getting the video that the user has initially uploaded to S3, then proceed to initialize the Transcribe job by configuring TranscriptionJobName, Media (video saved in s3), MediaFormat (video format), LanguageCode (video language), Subtitles (subtitle file format .vtt), OutputBucketName. Next, Trancribe will perform the created job, save the result file to S3.
- Next, after completing the subtitle creation, the next step is to call Lambda Function (Create job Translate from video subtitles) to perform the task of getting the subtitle file of the newly created video and initialize the job for Translate. Then Translate will perform the created job and save the result file to S3.
- Finally, when the main tasks are completed, the last Lambda Function will be called to prompt the API Gateway to send a notification that the subtitles are complete so that the fronted side can play the video with the processed subtitles.

![s1](/images/1.Introduce/architec.png)