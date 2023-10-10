---
layout: post
title: "Handling standard input/output/error in a child process in Node.js"
description: " "
date: 2023-10-10
tags: [nodejs, childprocess]
comments: true
share: true
---

Running child processes in Node.js is a common requirement when working with external programs or running system commands. When executing a child process, you may need to handle the standard input/output/error streams of the child process.

In this tutorial, we will explore how to handle standard input/output/error for a child process in Node.js.

## Table of Contents
- [Inheriting Parent Process' Streams](#inheriting-parent-process-streams)
- [Setting Custom Streams](#setting-custom-streams)
- [Handling Standard Input](#handling-standard-input)
- [Handling Standard Output](#handling-standard-output)
- [Handling Standard Error](#handling-standard-error)
- [Conclusion](#conclusion)

## Inheriting Parent Process' Streams

By default, when executing a child process in Node.js, the child process inherits the standard input/output/error streams of its parent process. This means that the child process can read input from the parent process and write output or error messages to the parent process.

Here's an example of how to create a child process and inherit the parent process' streams:

```javascript
const { spawn } = require('child_process');

const child = spawn('ls', ['-la']);

child.stdout.on('data', (data) => {
  console.log(`Child process stdout: ${data}`);
});

child.stderr.on('data', (error) => {
  console.error(`Child process stderr: ${error}`);
});

child.on('close', (code) => {
  console.log(`Child process exited with code ${code}`);
});
```

In the above example, we spawn a child process to run the `ls -la` command, which lists the files and directories in the current directory. We attach event listeners to the child process's `stdout`, `stderr`, and `close` events. This allows us to handle the standard output, standard error, and exit code of the child process, respectively.

## Setting Custom Streams

In some cases, you may want to set custom streams for the child process, rather than inheriting the parent's streams. For example, you might want to redirect the standard output of the child process to a file, or read standard input from a file.

To set custom streams for a child process, you can use the `stdio` option when spawning the child process. The `stdio` option accepts an array of I/O configurations.

Here's an example of how to set a custom stream for the standard output of a child process:

```javascript
const { spawn } = require('child_process');
const fs = require('fs');

const stdout = fs.createWriteStream('output.txt');
const child = spawn('ls', ['-la'], { stdio: ['ignore', stdout, 'ignore'] });

child.on('close', (code) => {
  console.log(`Child process exited with code ${code}`);
});
```

In the above example, we create a write stream using Node.js' `fs` module and pass it as a custom stream for the standard output of the child process. This redirects the output of the child process to the specified file (`output.txt`).

## Handling Standard Input

To provide standard input to a child process, you can write to the `stdin` property of the child process. This allows you to send input data to the child process programmatically.

Here's an example of how to provide standard input to a child process:

```javascript
const { spawn } = require('child_process');

const child = spawn('grep', ['hello']);

child.stdout.on('data', (data) => {
  console.log(`Child process stdout: ${data}`);
});

child.on('close', (code) => {
  console.log(`Child process exited with code ${code}`);
});

// Writing to standard input
child.stdin.write('hello world\n');
child.stdin.end();
```

In the above example, we spawn a child process to run the `grep hello` command, which searches for the word "hello" in the input. We write the input "hello world" to the child process's `stdin` and then close the input stream.

## Handling Standard Output

In the previous examples, we used the `stdout` event of the child process to handle the standard output. However, you can also retrieve the standard output as a buffer using the `stdout` property.

Here's an example of how to retrieve the standard output as a buffer:

```javascript
const { spawnSync } = require('child_process');

const result = spawnSync('ls', ['-la']);

console.log(`Standard output: ${result.stdout.toString()}`);
```

In the above example, we use `spawnSync` instead of `spawn` to run the child process synchronously. We retrieve the standard output as a buffer using the `stdout` property of the `result` object and convert it to a string using the `toString()` method.

## Handling Standard Error

Similar to handling standard output, you can handle standard error by attaching an event listener to the `stderr` event of the child process.

Here's an example of how to handle the standard error:

```javascript
const { spawn } = require('child_process');

const child = spawn('echo', ['hello world'], { stdio: ['pipe', 'pipe', 'pipe'] });

child.stderr.on('data', (error) => {
  console.error(`Child process stderr: ${error}`);
});

child.on('close', (code) => {
  console.log(`Child process exited with code ${code}`);
});
```

In the above example, we spawn a child process to run the `echo` command with the argument "hello world". Since the `echo` command does not produce an error, the `stderr` event will not be triggered. However, if the child process encounters an error, you can handle it by attaching an event listener to the `stderr` event.

## Conclusion

Handling standard input/output/error for a child process in Node.js allows us to integrate external programs or interact with system commands seamlessly. By inheriting the parent process' streams or setting custom streams, we can control the flow of data between the child process and the parent process.

Remember to carefully handle standard input, standard output, and standard error based on your requirements to ensure efficient communication with child processes.

#nodejs #childprocess