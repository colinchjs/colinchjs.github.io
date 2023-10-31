---
layout: post
title: "Deploying JavaScript apps to Heroku using CI/CD"
description: " "
date: 2023-10-31
tags: []
comments: true
share: true
---

## Introduction
Deploying JavaScript applications to the web has become an essential step in the development process. One popular platform for hosting web applications is Heroku, which provides an easy way to deploy and scale apps. In this tutorial, we will guide you through deploying your JavaScript app to Heroku using Continuous Integration and Continuous Deployment (CI/CD) techniques.

## Prerequisites
Before starting with the deployment process, make sure you have the following:

- A JavaScript application
- A Heroku account and the Heroku CLI installed
- A version control system, such as Git

## Step 1: Set up your Heroku app
1. Log in to your Heroku account and create a new app.
2. Choose a unique name for your app and select the corresponding region.
3. Once the app is created, navigate to the "Deploy" tab in your Heroku dashboard.

## Step 2: Connect your app to Git
1. In the "Deployment method" section, select the "GitHub" option.
2. Connect your GitHub account and choose the repository that contains your JavaScript app.
3. Enable automatic deploys from this repository.

## Step 3: Set up CI/CD with Heroku
1. In the "Automatic deploys" section, click on "Enable Automatic Deploys".
2. Open your repository's settings and navigate to the "Webhooks" section.
3. Add a new webhook with the following details:
  - Payload URL: `https://api.heroku.com/apps/YOUR_APP_NAME/deployments`
  - Content type: `application/json`
  - Secret: Generate a random secret or use a tool like [random.org](https://www.random.org/strings/)
  - Events: Select "Let me select individual events" and choose "Push" and "Pull Request" events.
4. Save the webhook and make note of the secret for later use.

## Step 4: Set up CI/CD pipeline
To set up a CI/CD pipeline, you can use a service like GitHub Actions or CircleCI. Here, we will demonstrate using GitHub Actions.

1. In your repository, navigate to the "Actions" tab and click on "Set up a workflow yourself" or choose an existing workflow template.
2. Update the workflow configuration file (e.g., `.github/workflows/main.yml`) with the following:

```yaml
name: Deploy to Heroku

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: 14

    - name: Install dependencies and build
      run: |
        npm ci
        npm run build

    - name: Deploy to Heroku
      uses: akhileshns/heroku-deploy@v3.12.12
      with:
        heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
        heroku_app_name: YOUR_APP_NAME
        heroku_email: YOUR_EMAIL

```

3. Commit and push the workflow file to trigger the CI/CD pipeline.

## Conclusion
By following these steps, you can easily deploy your JavaScript app to Heroku using CI/CD techniques. This ensures that your app is automatically deployed whenever changes are made to your repository, saving you time and effort. With the power of Heroku and CI/CD, your app can be up and running in no time!

# References
- [Heroku Dev Center](https://devcenter.heroku.com/)
- [GitHub Actions](https://docs.github.com/en/actions)