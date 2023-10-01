---
layout: post
title: "Implementing real-time logging with AWS CloudFormation in Node.js"
description: " "
date: 2023-10-01
tags: [techblog, CloudFormation]
comments: true
share: true
---

Logging is an essential part of application development and monitoring. It helps developers identify and debug issues, track user activity, and gain insights into the application's performance. In this blog post, we will explore how to implement real-time logging using AWS CloudFormation and Node.js.

## Prerequisites

Before we proceed, please ensure you have the following set up:

- An AWS account
- AWS CLI installed and configured
- Node.js installed on your local machine

## Step 1: Create an Amazon CloudWatch Logs Group

We will start by creating an Amazon CloudWatch Logs group to store our logs. Open your terminal and run the following command:

```bash
aws logs create-log-group --log-group-name MyLogGroup
```

Replace `MyLogGroup` with a name for your log group.

## Step 2: Create a CloudFormation Stack

Next, we will create a CloudFormation stack to provision the necessary resources for our logging system. Create a new file called `logging-stack.yaml` and add the following code:

```yaml
Resources:
  LoggingFunction:
    Type: AWS::Serverless::Function
    Properties:
      CodeUri: ./
      Handler: index.handler
      Runtime: nodejs14.x
      Timeout: 30
      FunctionName: MyLoggingFunction
      Events:
        CloudWatchLogsEvent:
          Type: CloudWatchLogs
          Properties:
            LogGroupName: MyLogGroup
```

Save the file and run the following command in your terminal:

```bash
aws cloudformation create-stack --stack-name MyStack --template-body file://logging-stack.yaml
```

Replace `MyStack` with a name for your CloudFormation stack.

## Step 3: Create a Lambda function

In this step, we will create a Lambda function that will process and forward the logs to our CloudWatch log group. Create a new file called `index.js` and add the following code:

```javascript
exports.handler = async (event) => {
  console.log('Received new logs:', event);

  // Process the logs and perform any necessary actions

  return {
    statusCode: 200,
    body: JSON.stringify({ message: 'Logs processed successfully' }),
  };
};
```

Save the file and run the following command in your terminal to deploy the Lambda function:

```bash
aws lambda create-function --function-name MyLoggingFunction --runtime nodejs14.x --handler index.handler --role MyLambdaRole --code ZipFile=fileb://index.js
```

Replace `MyLoggingFunction` with a name for your Lambda function and `MyLambdaRole` with the ARN of an IAM role that allows the Lambda function to write logs to CloudWatch Logs.

## Step 4: Test the logging system

Now that we have set up our logging system, let's test it out. Modify the `index.js` file to add a log statement:

```javascript
exports.handler = async (event) => {
  console.log('Received new logs:', event);

  console.log('This is a test log.');

  return {
    statusCode: 200,
    body: JSON.stringify({ message: 'Logs processed successfully' }),
  };
};
```

Save the file and run the following command to update the Lambda function:

```bash
aws lambda update-function-code --function-name MyLoggingFunction --zip-file fileb://index.js
```

Now, trigger the Lambda function by invoking it manually or via an event source. You should see the log statement in the CloudWatch Logs group you created earlier in Step 1.

## Conclusion

In this blog post, we learned how to implement real-time logging using AWS CloudFormation and Node.js. Logging is an essential part of any application, and with this setup, you can easily capture and analyze logs in real-time using the powerful features of Amazon CloudWatch.

#techblog #AWS #CloudFormation #Nodejs