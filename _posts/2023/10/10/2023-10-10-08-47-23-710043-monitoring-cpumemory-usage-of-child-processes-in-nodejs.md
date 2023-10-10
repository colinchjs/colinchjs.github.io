---
layout: post
title: "Monitoring CPU/memory usage of child processes in Node.js"
description: " "
date: 2023-10-10
tags: [NodeJS, ChildProcesses]
comments: true
share: true
---

As your Node.js applications become more complex, you may find the need to utilize child processes to perform computationally intensive tasks or execute external commands. While this allows for better utilization of system resources, it also introduces the challenge of monitoring the CPU and memory usage of these child processes.

In this article, we will explore how to monitor the CPU and memory usage of child processes in Node.js using the built-in `child_process` module and external tools like `pidusage` and `pm2`.

## Table of Contents
- [Using the child_process Module](#using-the-child_process-module)
- [Monitoring CPU Usage](#monitoring-cpu-usage)
- [Monitoring Memory Usage](#monitoring-memory-usage)
- [External Tools](#external-tools)
- [Conclusion](#conclusion)
- [References](#references)

## Using the child_process Module

The `child_process` module in Node.js provides a way to spawn additional processes outside of the main Node.js event loop. By utilizing the `exec`, `execFile`, or `spawn` methods, you can create child processes to perform various tasks.

To monitor the CPU and memory usage of these child processes, you can leverage the `pid` (Process ID) returned by the `spawn` method.

## Monitoring CPU Usage

To monitor the CPU usage of a child process, you can use the `pidusage` module. This module provides an easy way to retrieve the CPU usage of a process using its PID.

Here's an example of how to use `pidusage` to monitor the CPU usage of a child process:

```javascript
const { spawn } = require('child_process');
const pidusage = require('pidusage');

const child = spawn('your-command');

// Get the PID of the child process
const pid = child.pid;

// Monitor the CPU usage every second
setInterval(() => {
  pidusage.stat(pid, (err, stat) => {
    if (err) {
      console.error(err);
    } else {
      console.log(`CPU usage: ${stat.cpu}%`);
    }
  });
}, 1000);
```
In this example, we spawn a child process using the `spawn` method and obtain its PID. We then use `pidusage` to retrieve the CPU usage of the child process every second.

## Monitoring Memory Usage

Similarly, you can monitor the memory usage of a child process using the `pidusage` module. The `pidusage` module provides a `memory` property in the `stat` object, which represents the memory usage of a process in bytes.

Here's an example of how to use `pidusage` to monitor the memory usage of a child process:

```javascript
const { spawn } = require('child_process');
const pidusage = require('pidusage');

const child = spawn('your-command');

// Get the PID of the child process
const pid = child.pid;

// Monitor the memory usage every second
setInterval(() => {
  pidusage.stat(pid, (err, stat) => {
    if (err) {
      console.error(err);
    } else {
      console.log(`Memory usage: ${Math.round(stat.memory / 1024 / 1024)} MB`);
    }
  });
}, 1000);
```

In this example, we spawn a child process and retrieve its PID. We then use `pidusage` to retrieve the memory usage of the child process every second. We convert the memory usage from bytes to megabytes for better readability.

## External Tools

Apart from using the `pidusage` module, you can also utilize external tools like `pm2` to monitor the CPU and memory usage of child processes in Node.js. `pm2` is a process manager for Node.js applications that provides powerful monitoring capabilities.

To monitor child processes using `pm2`, you can simply start your child process with `pm2` and use the `pm2 monit` command to view the CPU and memory usage in real-time.

## Conclusion

Monitoring the CPU and memory usage of child processes in Node.js is crucial when dealing with computationally intensive tasks or external commands. By leveraging the `child_process` module and external tools like `pidusage` and `pm2`, you can keep track of the resource usage of your child processes.

Remember to analyze the monitoring data and make necessary optimizations to ensure optimal performance and resource utilization.

## References

- [Node.js - child_process](https://nodejs.org/api/child_process.html)
- [pidusage](https://github.com/soyuka/pidusage)
- [pm2](https://pm2.keymetrics.io/)

## #NodeJS #ChildProcesses