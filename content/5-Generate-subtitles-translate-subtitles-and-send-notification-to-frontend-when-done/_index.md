---
title : "Generate subtitles translate subtitles and send notification to user interface when done"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

In this step, we will create Lambda Functions to perform the main tasks of this workshop.

- Lambda Function to initialize Transcribe job
- Lambda Function to initialize Translate job
- Lambda Function to notify FrontEnd when the above tasks are completed.

Next, we will create a workflow from the created Lambda Functions so that the execution takes place automatically using Step Function.

To activate Step Function, we need to create another Lambda Function to call to activate Step Function when uploading video to S3 is complete.

### Contents 

- [Set up Lambda Function to initialize Transcribe job](5.1-Lambda-Function-initializes-Transcribe-job/) 
- [Set up Lambda Function to initialize Translate job](5.2-Lambda-Function-initializes-Translate-job/) 
- [Set up Lambda Function to notify to FrontEnd](5.3-Lambda-Function-send-notification-to-FrontEnd/) 
- [Set up Step Function](5.4-Assemble-the-components-of-a-workflow-with-Step-Function/) 
- [Set up a Lambda Function that triggers Step Function operations](5.5-Lambda-Function-triggers-workflow/)