---
title : "Create Lambda Notify"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 5.3.1 </b> "
---

## Create Lambda

Create function.

Enter the information as shown:

![Upload](/images/7.notify/n11.png)

**Create function**

![Upload](/images/7.notify/n12.png)

Paste the following code:

```python
import json
import http.client

def lambda_handler(event, context):
    api_url = "axwqwuuq1f.execute-api.us-east-1.amazonaws.com"
    resource = "/dev/notify"

    payload = json.dumps({"status": "completed"})
    headers = {
        'Content-Type': 'application/json'
    }

    try:
        conn = http.client.HTTPSConnection(api_url)
        conn.request("POST", resource, payload, headers)

        response = conn.getresponse()
        data = response.read()

        if response.status == 200:
            return {
                'statusCode': 200,
                'body': json.dumps({'status': 'completed', 'message': 'Notification sent!'})
            }
        else:
            return {
                'statusCode': response.status,
                'body': json.dumps({'status': 'failed', 'message': 'Failed to send notification'})
            }
    except Exception as e:
        print(f"Error sending notification: {e}")
        return {
            'statusCode': 500,
            'body': json.dumps({'status': 'error', 'message': 'Failed to send notification'})
        }
```

**Deloy**

Done creating lambda function to generate notification to frontend.

