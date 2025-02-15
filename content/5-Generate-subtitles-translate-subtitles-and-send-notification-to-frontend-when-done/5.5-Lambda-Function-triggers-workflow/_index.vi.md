---
title : "Tạo Lambda Function kích hoạt Step Function"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Ở bước này sẽ tạo một lambda để kích hoạt Step Function.

## Tạo function.

Điền các thông tin như hình:

![Upload](/images/10.callstepfun/n.png)

Chọn **Create function**

Dán code sau và chon **Deloy**:

```python
import uuid
import boto3
import json

step_function_client = boto3.client('stepfunctions')

def lambda_handler(event, context):
    execution_name = str(uuid.uuid4())
    try:
        response = step_function_client.start_execution(
            stateMachineArn='arn:aws:states:us-east-1:092730711177:stateMachine:MyStateMachine-v47qbhrm7',
            name=execution_name,
            input=json.dumps({"key": "value"})
        )
        return {
            'statusCode': 200,
            'body': json.dumps('Step Function started successfully!')
        }
    except Exception as e:
        return {
            'statusCode': 500,
            'body': json.dumps(f'Failed to start Step Function: {str(e)}')
        }
```

![Upload](/images/10.callstepfun/n1.png)

**stateMachineArn** là giá trị chứ ARN của Step Function đã tạo ở bước trước.

![Upload](/images/8.stepfun/n7.png)

Cài đặt trigger cho lambda là SNS đã tạo.

![Upload](/images/10.callstepfun/n2.png)

Chọn thông tin như sau:

![Upload](/images/10.callstepfun/n3.png)

Chọn **Add**

Vậy đã tạo thành công Lambda với trigger là SNS.

![Upload](/images/10.callstepfun/n4.png)
