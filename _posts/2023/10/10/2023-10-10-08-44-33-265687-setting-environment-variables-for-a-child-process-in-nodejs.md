---
layout: post
title: "Setting environment variables for a child process in Node.js"
description: " "
date: 2023-10-10
tags: []
comments: true
share: true
---

When working with Node.js, you might need to spawn child processes to execute external commands or run sub-processes. In some cases, you may need to pass environment variables to these child processes. In this article, we will explore how to set environment variables for a child process in Node.js.

## Table of Contents
- [Using the `spawn` method with environment variables](#using-the-spawn-method-with-environment-variables)
- [Using the `exec` method with environment variables](#using-the-exec-method-with-environment-variables)
- [Conclusion](#conclusion)

## Using the `spawn` method with environment variables

Node.js provides the `child_process` module, which allows us to spawn child processes. The `spawn` method of this module enables us to execute commands in a new process.

To set environment variables for a child process using `spawn`, we can pass an `env` object as one of the options to the `spawn` method. The `env` object should contain the necessary environment variable key-value pairs.

Here's an example:

```javascript
const { spawn } = require('child_process');

const child = spawn('echo', ['Hello, World!'], { env: { MESSAGE: 'Custom message' } });

child.stdout.on('data', (data) => {
  console.log(`Child process output: ${data}`);
});
```

In the above code, we are spawning a child process to execute the `echo` command with the argument `"Hello, World!"`. We are also passing an `env` object to the `spawn` method with a custom environment variable `MESSAGE`.

## Using the `exec` method with environment variables

Another way to execute a command in a child process is by using the `exec` method from the `child_process` module. This method allows us to run a command in a shell and provides more flexibility compared to `spawn`.

To set environment variables for a child process using `exec`, we can use the `env` parameter. The `env` parameter expects an object containing the environment variable key-value pairs.

Here's an example:

```javascript
const { exec } = require('child_process');

const command = 'echo $MESSAGE';
const env = { MESSAGE: 'Custom message' };

exec(command, { env }, (error, stdout, stderr) => {
  if (error) {
    console.error(`Error occurred: ${error.message}`);
    return;
  }

  console.log(`Child process output: ${stdout}`);
});
```

In the above code, we use the `exec` method to run the command `echo $MESSAGE` in a shell. We pass the `env` object containing our custom environment variable `MESSAGE`.

## Conclusion

Setting environment variables for child processes in Node.js can be achieved using either the `spawn` or `exec` method from the `child_process` module. By passing an `env` object with the required environment variable key-value pairs, you can control and customize the environment variables for the child processes.