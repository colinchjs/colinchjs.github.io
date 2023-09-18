---
layout: post
title: "Deploying Rollup.js bundle to popular hosting platforms like Netlify and Vercel"
description: " "
date: 2023-09-18
tags: [rollupjs, deployment]
comments: true
share: true
---

When it comes to deploying your Rollup.js bundle, popular hosting platforms like Netlify and Vercel provide seamless integration options. These platforms make it easy to deploy your static bundles and take advantage of various features they offer. In this blog post, we will walk through the steps to deploy a Rollup.js bundle on both Netlify and Vercel.

## Prerequisites
Before we begin, make sure you have the following prerequisites in place:

1. A Rollup.js project set up and configured.
2. A GitHub or GitLab repository for your project.

## Deploying with Netlify
Netlify is a popular hosting platform that offers simple and powerful hosting for static sites and applications.

### Step 1: Connect your GitHub/GitLab repository
1. Sign in to Netlify and click "New site from Git".
2. Connect your GitHub or GitLab repository that contains your Rollup.js project.

### Step 2: Configure build settings
1. Click on "Build & Deploy" in the Netlify dashboard.
2. Under "Build settings", click on "Edit settings".
3. Configure the build settings:
   - Set the "Build command" to build your Rollup.js bundle (e.g., `npm run build`).
   - Set the "Publish directory" to the folder where your bundled files are generated (e.g., `dist`).
   - Click "Save" to save the configuration.

### Step 3: Deploy your Rollup.js bundle
1. Click on "Deploy site" in the Netlify dashboard.
2. Netlify will automatically trigger a build using your configured build settings.
3. Once the build succeeds, your Rollup.js bundle will be deployed and accessible via the provided URL.

## Deploying with Vercel
Vercel, formerly known as Now, is a serverless deployment platform that offers a seamless deployment experience for static sites.

### Step 1: Connect your GitHub/GitLab repository
1. Sign in to Vercel and click "Import Project".
2. Select your GitHub or GitLab repository that contains your Rollup.js project.

### Step 2: Configure the project settings
1. Vercel will automatically detect your project's settings based on the detected framework.
2. Confirm the project settings and click "Deploy" to proceed.

### Step 3: Deploy your Rollup.js bundle
1. Vercel will start the deployment process.
2. Once the deployment is complete, your Rollup.js bundle will be live and accessible via the provided URL.

## Conclusion
Deploying a Rollup.js bundle to hosting platforms like Netlify and Vercel is a straightforward process that allows you to quickly publish your static projects. With their seamless integration and powerful features, these platforms make it easy to showcase your Rollup.js bundles to the world.

#rollupjs #deployment