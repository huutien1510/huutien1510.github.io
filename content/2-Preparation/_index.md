---
title : "Preparation"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

First need to create IAM Role.

{{% notice info %}}
You need to create 1 Linux instance on the public subnet and 1 Window instance on the private subnet to perform this lab.
{{% /notice %}}

**IAM Role** is a feature that enhances security on AWS. An IAM Role can be temporarily assigned to IAM Users and AWS resources within (internal) or outside (external) your account.

### Content
  - [Create IAM Role](./2.1-CreateIAMRole/)