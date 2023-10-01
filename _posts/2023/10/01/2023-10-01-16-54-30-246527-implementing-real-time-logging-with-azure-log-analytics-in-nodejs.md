---
layout: post
title: "Implementing real-time logging with Azure Log Analytics in Node.js"
description: " "
date: 2023-10-01
tags: [azure, loganalytics]
comments: true
share: true
---

As developers, we know how important it is to have a robust logging mechanism in our applications. It helps us track errors, troubleshoot issues, and monitor the overall health of our systems. Azure Log Analytics provides a powerful logging and monitoring solution, and in this tutorial, we will learn how to implement real-time logging with Azure Log Analytics in a Node.js application.

## Prerequisites
Before we begin, make sure you have the following:

- Node.js and npm installed on your machine.
- An Azure account with access to Azure Log Analytics.
- An existing Node.js application that you want to integrate with Azure Log Analytics.

## Step 1: Install the Azure Monitor SDK
To get started, we need to install the Azure Monitor SDK for Node.js. Open your terminal and run the following command:

```shell
npm install @azure/monitor-query
```

This will install the necessary dependencies to interact with Azure Log Analytics.

## Step 2: Create a Log Analytics Workspace
Next, we need to create a Log Analytics workspace in Azure. Follow these steps:

1. Login to the Azure Portal.
2. Click on **Create a resource** and search for **Log Analytics**.
3. Click on **Log Analytics** and then click on the **Create** button.
4. Provide the required details like workspace name, subscription, resource group, and region.
5. Click on **Review + Create** and then **Create** to create the workspace.

Make a note of the **Workspace ID** and **Primary Key** as we will need them in the next step.

## Step 3: Initialize the Azure Monitor client
In your Node.js application, initialize the Azure Monitor client by passing your workspace ID and primary key. Insert the following code at the relevant section of your codebase:

```javascript
const { LogsQueryClient } = require("@azure/monitor-query");

const logAnalyticsClientId = '<YOUR_WORKSPACE_ID>';
const logAnalyticsClientKey = '<YOUR_PRIMARY_KEY>';

const logsClient = new LogsQueryClient({
  logAnalyticsClientId,
  logAnalyticsClientKey
});
```

Replace `<YOUR_WORKSPACE_ID>` and `<YOUR_PRIMARY_KEY>` with the values obtained from the Log Analytics workspace.

## Step 4: Send logs to Azure Log Analytics
Now that we have set up the Azure Monitor client, we can start sending logs to Azure Log Analytics. Here's an example of how you can send logs:

```javascript
// Your code

try {
  // Your logic
} catch (error) {
  // Log the error to Azure Log Analytics
  logsClient.queryLogs({
    query: `AzureDiagnostics | where OperationName == "MyOperation" | extend Message = "An error occurred: ${error.message}" | project Message`
  });
}
```

In the `catch` block of your code, you can send the error message to Azure Log Analytics using the `queryLogs` method from the Azure Monitor client. Customize the query based on your requirements.

## Step 5: Query logs in Azure Log Analytics
To view the logs in Azure Log Analytics, follow these steps:

1. Go to the Azure Portal and navigate to your Log Analytics workspace.
2. In the left menu, click on **Logs** under **General**.
3. Write your desired query in the query editor and click on **Run**.

You can use the full power of Azure Log Analytics query language to filter, sort, and analyze your logs.

Congratulations! You have successfully implemented real-time logging with Azure Log Analytics in your Node.js application. This will enable you to monitor and analyze your logs, and gain valuable insights into your application's performance and health.

#azure #loganalytics