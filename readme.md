# SQS - Lambda - DynamoDB Table

## Things to do:

### Set region:  
+ Region: eu-west-1

### Accountnumber
+ Note your AWS account number: _ACCOUNT NUMBER_

### Create DDB Table:  
+ Name: ProductVisits  
+ Partition key: ProductVisitKey

### Create SQS Queue:  
+ Name: ProductVisitsDataQueue  
+ Type: Standard

Note the Queue URL: https://sqs.eu-west-1.amazonaws.com/ACCOUNTNUMBER/ProductVisitsDataQueue

### Create Lambda function  
+ Name: productVisitsDataHandler  
+ Runtime: Node.js 12.x  
+ Role: create new role from templates  
   - Role name: lambdaRoleForSQSPermissions  
   - Add policy templates: "Simple microservice permissions" and "Amazon SQS poller permissions"  
+ From actions menu in front of function code heading upload a zip file (DCTProductVisitsTracking.zip)

## Action

1. Go to AWS CLI and send messages:
   AWS CLI Command:
   ```bash
   Aws sqs send-message --queue-url https://sqs.eu-west-1.amazonaws.com/ACCOUNT NUMBER/ProductVisitsDataQueue --message-body file://message-body-1.json
   ```  
   Modify: Queue name and file name
   
2. Post message 1 and 2
3. open your queue in the console and find the posted messages
4. find out dydnamodb database is still empty

## Continue

Go back to SQS and open "ProductVisitsDataQueue"  
On the SQS Queue configure Lambda function trigger and specify Lambda function:  
+ Name: productVisitsDataHandler

## Action

1. Go to AWS CLI and send messages:
   ```bash
   Aws sqs send-message --queue-url https://sqs.eu-west-1.amazonaws.com/ACCOUNT NUMBER/ProductVisitsDataQueue --message-body file://message-body-3.json
   ```  
   Modify: Queue name and file name

2. Post message 3 and 4
3. open your queue in the console and find the Queue is empty
4. find out Dynamodb database is filled with data
