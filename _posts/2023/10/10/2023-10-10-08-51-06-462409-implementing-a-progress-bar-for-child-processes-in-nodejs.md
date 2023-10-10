---
layout: post
title: "Implementing a progress bar for child processes in Node.js"
description: " "
date: 2023-10-10
tags: [nodejs, progress]
comments: true
share: true
---

In Node.js, child processes can be used to run external commands or scripts in a separate process. Often, these child processes might take some time to complete, making it useful to have a progress bar to indicate the progress of the task being executed.

In this blog post, we will explore how to implement a progress bar for child processes in Node.js using the `readline` module.

## Table of Contents
- [Setting up the project](#setting-up-the-project)
- [Creating the progress bar](#creating-the-progress-bar)
- [Updating the progress](#updating-the-progress)
- [Running the child process](#running-the-child-process)
- [Summary](#summary)

## Setting up the project

Before we dive into implementing the progress bar, let's set up a new Node.js project. Create a new directory for the project and navigate to it in your terminal. Then, initialize a new Node.js project by running the following command:

```
$ npm init -y
```

Next, install the `readline` module by running:

```
$ npm install readline
```

## Creating the progress bar

To create the progress bar, we will use the `readline` module, which provides an interface for reading lines from a readable stream, such as `process.stdout`.

Create a new file called `progressBar.js` and add the following code:

```javascript
const readline = require('readline');

class ProgressBar {
  constructor(total) {
    this.total = total;
    this.current = 0;
    this.rl = readline.createInterface({
      input: process.stdin,
      output: process.stdout,
    });
  }

  update() {
    this.current++;
    this.rl.clearLine();
    this.rl.cursorTo(0);
    this.rl.write(`Progress: ${Math.round((this.current / this.total) * 100)}%`);
  }

  complete() {
    this.rl.close();
  }
}

module.exports = ProgressBar;
```

In the `ProgressBar` class, we initialize the `readline` interface with `process.stdin` and `process.stdout`. The `update` method is used to update the progress bar by clearing the line, moving the cursor to the beginning of the line, and writing the updated progress percentage. The `complete` method is used to close the readline interface when the process is complete.

## Updating the progress

Next, let's create a separate file called `progressExample.js` to demonstrate how to use the progress bar. Add the following code:

```javascript
const ProgressBar = require('./progressBar');

const totalTasks = 10;
const progressBar = new ProgressBar(totalTasks);

// Simulating a long-running task
function simulateTask() {
  return new Promise((resolve) => {
    setTimeout(resolve, 1000);
  });
}

async function runTasks() {
  for (let i = 0; i < totalTasks; i++) {
    await simulateTask();
    progressBar.update();
  }

  progressBar.complete();
}

runTasks();
```

In this example, we create a `ProgressBar` instance, specifying the total number of tasks to be completed. We then define a `simulateTask` function that returns a promise to simulate a long-running task.

The `runTasks` function iterates over a given number of tasks, waits for each task to complete using `simulateTask`, and then updates the progress bar using `progressBar.update`. Finally, we call `progressBar.complete` to close the progress bar interface.

## Running the child process

To use the progress bar with a child process, we can modify the `runTasks` function in `progressExample.js` to execute a child process command. Here's an example:

```javascript
const { exec } = require('child_process');

async function runTasks() {
  for (let i = 0; i < totalTasks; i++) {
    await new Promise((resolve) => {
      exec('some-command', (err) => {
        if (err) {
          console.error(err);
        }
        resolve();
      });
    });

    progressBar.update();
  }

  progressBar.complete();
}

runTasks();
```

Replace `'some-command'` with the command you wish to execute as a child process.

## Summary

In this blog post, we learned how to implement a progress bar for child processes in Node.js. We used the `readline` module to create an interface for updating and displaying the progress bar. The progress bar can be useful for providing feedback and indicating the progress of long-running tasks or child processes.

Remember to install the `readline` module before running the code. Feel free to customize the progress bar's appearance and functionality to fit your specific requirements.

#nodejs #progress-bar