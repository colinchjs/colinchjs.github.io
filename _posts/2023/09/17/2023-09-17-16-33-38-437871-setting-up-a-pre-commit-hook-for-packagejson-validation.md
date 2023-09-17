---
layout: post
title: "Setting up a pre-commit hook for package.json validation"
description: " "
date: 2023-09-17
tags: [techblogs, nodejs]
comments: true
share: true
---

In software development, it is important to maintain the integrity of our codebase and ensure that the project dependencies are properly managed. One way to achieve this is to set up a pre-commit hook that validates the `package.json` file before any commits are made. This will help catch errors and prevent uploading of incorrect or incomplete package configurations.

## Prerequisites

Before setting up the pre-commit hook, make sure you have the following:

- [Node.js](https://nodejs.org) installed on your machine
- A version control system (e.g., Git) initialized in your project directory

## Steps

Follow these steps to set up a pre-commit hook:

1. Open your project directory in the terminal or command prompt.

2. Install the `husky` package by running the following command:

   ```sh
   npm install husky --save-dev
   ```

   This package helps manage Git hooks in a Node.js project.

3. Open the `package.json` file in your project directory.

4. Locate the `scripts` section in the `package.json` file and add the following script:

   ```json
   "scripts": {
     "precommit": "npm test"
   }
   ```

   This script specifies the command to be executed before each commit, which in this case is running the tests. You can modify this script to suit your needs.

5. Open the terminal or command prompt again and run the following command to initialize the Git hook:

   ```sh
   npx husky install
   ```

6. Finally, run the command below to enable the pre-commit hook:

   ```sh
   npx husky add .husky/pre-commit "npm run precommit"
   ```

   This will create a `.husky` directory in your project root, which contains the pre-commit hook.

## Testing the Pre-commit Hook

To test your pre-commit hook, make changes in your project and try to commit them. The pre-commit hook will automatically run the specified script (in this case, `npm test`) before allowing the commit to proceed. If any errors or warnings are detected, the commit will be aborted and you will need to fix the issues before committing again.

Remember to regularly update the tests and script in the `precommit` section of the `package.json` file as your project evolves.

Setting up a pre-commit hook for `package.json` validation helps ensure that your project's dependencies are correctly configured before every commit. This helps maintain a stable and error-free codebase, improving the overall quality and reliability of your software.

#techblogs #nodejs