---
title : "Transcribe"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---


Sử dụng Lambda Function để tạo Transcribe job với AWS Transcribe sẽ cũng cấp hai định dạng fiel sub cho video là SRT và VTT (WebVTT). Với workshop này sẽ sử dụng định dạng VTT.

VTT là định dạng sau:
00:00:00.469 --> 00:00:02.880
The BMW crew is the world leading

Đồng thời sử dụng Lambda Function để thực hiện xoá Transcribe job khi đã thực hiện xong.

## Nội dung:

- [Tạo Lambda Function](./5.1-Lambda-Transc/)

