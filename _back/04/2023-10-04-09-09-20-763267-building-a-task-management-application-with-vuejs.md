---
layout: post
title: "Building a task management application with Vue.js"
description: " "
date: 2023-10-04
tags: [introduction, setting]
comments: true
share: true
---

In this tutorial, we will learn how to build a task management application using the popular JavaScript framework Vue.js. With Vue.js, we can create dynamic and responsive user interfaces for web applications. Let's get started!

## Table of Contents
1. [Introduction to Vue.js](#introduction-to-vuejs)
2. [Setting Up the Project](#setting-up-the-project)
3. [Creating the Task Component](#creating-the-task-component)
4. [Implementing Task Functionality](#implementing-task-functionality)
5. [Styling the Application](#styling-the-application)
6. [Conclusion](#conclusion)

## Introduction to Vue.js

Vue.js is a progressive JavaScript framework that allows us to build user interfaces for web applications. It focuses on the view layer and provides a simple and flexible syntax to create interactive and reusable components. Vue.js is lightweight, easy to learn, and has a growing community.

## Setting Up the Project

To begin, make sure you have Node.js installed on your system. You can check the version of Node.js by running the command `node -v` in your terminal. If Node.js is not installed, go to the official Node.js website and follow the installation instructions.

Next, open your terminal and navigate to the directory where you want to create your project. Run the following command to create a new Vue.js project using the Vue CLI:

```bash
vue create task-management-app
```

This command will create a new directory named `task-management-app` with all the necessary files and dependencies for your Vue.js project.

## Creating the Task Component

Now that our project is set up, let's create our first component - the Task component. Components are the building blocks of a Vue.js application and allow us to encapsulate reusable UI elements. 

Inside the `src/components` directory, create a new file called `Task.vue`. Open the file and add the following code:

```vue
<template>
  <div class="task">
    <input type="checkbox" v-model="completed">
    <label>{{ task }}</label>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      completed: false
    };
  }
};
</script>

<style scoped>
.task {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.task label {
  margin-left: 10px;
  font-size: 16px;
}
</style>
```

In this code, we define a Task component with a template containing an input checkbox and a label. We also define a data property `completed` that keeps track of the task's completion status. The `task` prop is used to display the task's name.

## Implementing Task Functionality

Now that we have our Task component, let's implement the functionality to add and display tasks in our application. Open the `src/App.vue` file and replace its contents with the following code:

```vue
<template>
  <div class="app">
    <h1>Task Management</h1>
    <input v-model="newTask" @keydown.enter="addTask">
    <div v-for="(task, index) in tasks" :key="index">
      <task :task="task"></task>
    </div>
  </div>
</template>

<script>
import Task from "./components/Task.vue";

export default {
  components: {
    Task
  },
  data() {
    return {
      newTask: "",
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.tasks.push(this.newTask);
        this.newTask = "";
      }
    }
  }
};
</script>

<style scoped>
.app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
}

input {
  width: 100%;
  height: 40px;
  border: 1px solid #ddd;
  padding: 5px 10px;
  margin-bottom: 10px;
}

input:focus {
  outline: none;
}

@media (max-width: 767px) {
  .app {
    padding: 10px;
  }

  h1 {
    font-size: 20px;
    margin-bottom: 10px;
  }

  input {
    height: 30px;
    margin-bottom: 5px;
  }
}
</style>
```

In this code, we set up the main App component, which contains a title, an input field to add new tasks, and a loop that renders the Task component for each task in the `tasks` array. The `addTask` method is called when the Enter key is pressed, adding the new task to the `tasks` array.

## Styling the Application

To make our application visually appealing, we have added some CSS styles to the App and Task components. Feel free to customize the styles according to your preference.

## Conclusion

Congratulations! You have successfully built a task management application using Vue.js. We covered the basics of Vue.js components, data binding, and event handling. Vue.js provides many more advanced features, so be sure to explore the documentation to extend your application further.

#vuejs #webdevelopment