---
title : "Transcribe"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---
S
Using Lambda Function to create Transcribe job with AWS Transcribe will provide two sub file formats for video, SRT and VTT (WebVTT). For this workshop, we will use VTT format.

VTT is the following format:

00:00:00.469 --> 00:00:02.880
The BMW crew is the world leading

Also use Lambda Function to delete the Transcribe job when it is done.

## Content:

- [Create Lambda Function](./5.1-Lambda-Transc/)