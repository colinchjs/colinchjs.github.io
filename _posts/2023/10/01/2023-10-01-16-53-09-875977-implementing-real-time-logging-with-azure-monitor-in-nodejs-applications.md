---
layout: post
title: "Implementing real-time logging with Azure Monitor in Node.js applications"
description: " "
date: 2023-10-01
tags: [AzureMonitor, Node]
comments: true
share: true
---

Logging is an essential part of any application as it helps developers monitor application behavior, troubleshoot issues, and gain insights into how the application is being used. In cloud-based applications, a common approach for logging is using Azure Monitor. Azure Monitor provides a centralized logging and monitoring solution for applications running on the Azure platform.

In this blog post, we will explore how to implement real-time logging with Azure Monitor in Node.js applications. We will use Azure Monitor's Log Analytics workspace to collect and analyze logs.

## Setting up Azure Monitor

Before we start implementing logging in our Node.js application, we need to set up Azure Monitor and create a Log Analytics workspace. Here are the steps to follow:

1. Create an Azure account if you don't have one already.
2. Navigate to the Azure portal.
3. Search for "Log Analytics workspaces" in the search bar and open the Log Analytics workspaces page.
4. Click on the "Add" button to create a new workspace.
5. Provide a name for your workspace, select the desired subscription, resource group, and region.
6. Review the other settings and click on "Review + create".
7. Once the workspace is created, note down its **Workspace ID** and **Primary Key** as we will need them later.

## Installing the Azure Monitor Node.js SDK

Now that we have our workspace set up, let's install the Azure Monitor Node.js SDK in our Node.js application. The SDK provides the necessary APIs to send logs to Azure Monitor.

To install the SDK, open your command prompt and navigate to your project's directory. Run the following command:

```shell
npm install @azure/applicationinsights --save
```

## Configuring the Azure Monitor SDK

To configure the Azure Monitor SDK, we need to provide our workspace ID and primary key. In your Node.js application, create a new file called `monitor.js` and add the following code:

```javascript
const appInsights = require('applicationinsights');
appInsights.setup('<YOUR_WORKSPACE_ID>').setSendLiveMetrics(true);
appInsights.defaultClient.context.tags[appInsights.defaultClient.context.keys.cloudRoleInstance] = 'YOUR_APP_NAME';
appInsights.defaultClient.context.tags[appInsights.defaultClient.context.keys.cloudRole] = 'YOUR_APP_ROLE';
appInsights.start();
```

Replace `<YOUR_WORKSPACE_ID>` with your actual workspace ID. Additionally, change `'YOUR_APP_NAME'` and `'YOUR_APP_ROLE'` to meaningful names for your application.

## Logging events

Now that we have configured the Azure Monitor SDK, we can start logging events from within our Node.js application. Here's an example of how to log an event:

```javascript
const appInsights = require('applicationinsights');
const logger = appInsights.defaultClient;

function logEvent(message) {
  logger.trackEvent({ name: 'CustomEvent', properties: { message } });
}
```

In the above example, we log a custom event named "CustomEvent" with a `message` property. We can customize the name of the event and include additional properties as needed.

## Viewing logs in Azure Monitor

With logging configured and events being logged from our Node.js application, we can view and analyze the logs in Azure Monitor. To do this, follow the steps below:

1. Go to the Azure portal and navigate to your Log Analytics workspace.
2. In the workspace, click on "Logs" in the left menu.
3. Use the query editor to write queries and filter logs as needed.
4. Explore the various features of Azure Monitor, such as visualizations and alerts, to gain insights from the logs.

## Conclusion

Implementing real-time logging with Azure Monitor in Node.js applications is a crucial step in monitoring and troubleshooting your applications. Azure Monitor provides a powerful solution for collecting, analyzing, and visualizing logs from your application. By following the steps outlined in this blog post, you'll be able to integrate Azure Monitor into your Node.js applications and gain valuable insights into your application's behavior. #AzureMonitor #Node.js