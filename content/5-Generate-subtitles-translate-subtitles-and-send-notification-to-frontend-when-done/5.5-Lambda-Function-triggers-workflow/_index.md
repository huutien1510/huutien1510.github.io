---
title : "Create a Lambda Function that triggers a Step Function"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

In this step, we will create a lambda to trigger the Step Function.

## Create function.

Fill in the information as shown:

![Upload](/images/10.callstepfun/n.png)

Select **Create function**

Paste the following code and select **Deloy**:

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

**stateMachineArn** is the value of the ARN of the Step Function created in the previous step.

![Upload](/images/8.stepfun/n7.png)

Set the trigger for the lambda to be the created SNS.

![Upload](/images/10.callstepfun/n2.png)

Select the information as follows:

![Upload](/images/10.callstepfun/n3.png)

Select **Add**

So the Lambda has been successfully created with the trigger being SNS.

![Upload](/images/10.callstepfun/n4.png)