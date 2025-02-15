---
title : "Translate"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

Use Lambda to call AWS Translate to translate subtitles taken from the ws-file-sub-video bucket.

And AWS Translate translates files up to *20MB* in *text (.txt), HTML (.html), Word (.docx), Excel (.xlsx), PowerPoint (.pptx) and XLIFF 1.2 (.xlf)* formats and supports up to *1,000,000 files* at a time. Amazon Translate provides output content as files. The file format for each output file matches the input file format.

However, when using it as a subtitle for a video, you can use lambda to convert the output file format of Amazon Translate to .vtt format while also converting the subtitle file format from .vtt to .txt to match the input format of Amazon Translate.

This workshop will translate from English to Vietnamese.

## Contents:

- [Create Lambda Function](./6.1-Lambda-Transl/)