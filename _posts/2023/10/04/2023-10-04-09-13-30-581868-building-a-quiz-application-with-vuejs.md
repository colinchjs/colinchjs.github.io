---
layout: post
title: "Building a quiz application with Vue.js"
description: " "
date: 2023-10-04
tags: [prerequisites), setting]
comments: true
share: true
---

In this tutorial, we will learn how to build a quiz application using Vue.js. Vue.js is a JavaScript framework that makes it easy to build interactive user interfaces and single-page applications. By the end of this tutorial, you will be able to create a fully functional quiz application that allows users to answer questions and see their score.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Setting up the Project](#setting-up-the-project)
- [Creating the Quiz Component](#creating-the-quiz-component)
- [Displaying the Questions](#displaying-the-questions)
- [Handling User Input](#handling-user-input)
- [Calculating the Score](#calculating-the-score)
- [Conclusion](#conclusion)

## Prerequisites
To follow along with this tutorial, you will need the following:
- Basic knowledge of HTML, CSS, and JavaScript
- Node.js and npm installed on your machine
- Vue.js installed globally on your machine

## Setting up the Project
First, let's create a new Vue.js project using the Vue CLI. Open your terminal and run the following command:

```bash
vue create quiz-app
```

Choose the default preset and wait for the project to be created. Once done, navigate to the project directory and start the development server:

```bash
cd quiz-app
npm run serve
```

Now, you should be able to access the application at http://localhost:8080.

## Creating the Quiz Component
In the `src/components` directory, create a new file called `Quiz.vue`. This will be our main component for the quiz application. Inside the file, we will start by setting up the basic structure of the component.

```vue
<template>
  <div>
    <h1>Quiz Application</h1>
    <!-- Rest of the component -->
  </div>
</template>

<script>
export default {
  name: 'Quiz',
  data() {
    return {
      questions: [],
      currentQuestionIndex: 0,
      selectedOption: null,
      score: 0
    };
  },
  // Rest of the component
}
</script>

<style scoped>
/* Styles for the component */
</style>
```

In the template section, we have a simple HTML structure with a heading and a div that will contain the quiz questions. In the script section, we define the component name and initialize some data properties that we will use later.

## Displaying the Questions
Next, let's fetch the quiz questions from an API and display them in the component. We will make use of the `mounted` lifecycle hook to fetch the questions when the component is mounted.

```vue
<script>
export default {
  // Rest of the component
  mounted() {
    this.fetchQuestions();
  },
  methods: {
    async fetchQuestions() {
      try {
        const response = await fetch('https://api.example.com/questions');
        const data = await response.json();
        this.questions = data.questions;
      } catch (error) {
        console.error(error);
      }
    }
  }
}
</script>
```

In the `fetchQuestions` method, we make an asynchronous request to the quiz API using the Fetch API. Once we receive the response, we extract the question data and update the `questions` array. You can replace the API URL with your own quiz API or use a mock API for testing purposes.

Now, let's display the questions in the template section of the component:

```vue
<template>
  <div>
    <h1>Quiz Application</h1>
    <div v-if="questions.length > 0">
      <h2>{{ questions[currentQuestionIndex].question }}</h2>
      <!-- Options for the current question -->
      <button v-for="option in questions[currentQuestionIndex].options" :key="option.id" @click="selectOption(option.id)">
        {{ option.text }}
      </button>
    </div>
    <div v-else>
      <p>Loading questions...</p>
    </div>
  </div>
</template>
```

In the code above, we check if the `questions` array is populated before rendering the questions. If the array is empty, we display a loading message. Otherwise, we display the current question along with its options using a `v-for` loop.

## Handling User Input
Now, let's implement the logic to handle user input and move to the next question when an option is selected.

```vue
<script>
export default {
  // Rest of the component
  methods: {
    // Rest of the methods
    selectOption(optionId) {
      this.selectedOption = optionId;
      this.checkAnswer();
    },
    checkAnswer() {
      const currentQuestion = this.questions[this.currentQuestionIndex];
      if (currentQuestion.correctOption === this.selectedOption) {
        this.score++;
      }
      this.nextQuestion();
    },
    nextQuestion() {
      this.currentQuestionIndex++;
      this.selectedOption = null;
    }
  }
}
</script>
```

In the `selectOption` method, we store the selected option in the `selectedOption` property and call the `checkAnswer` method. In the `checkAnswer` method, we compare the selected option with the correct option for the current question. If they match, we increment the `score` property. Finally, we call the `nextQuestion` method to move to the next question and reset the `selectedOption`.

## Calculating the Score
To display the score at the end of the quiz, we can add a conditional rendering in the template section of the component.

```vue
<template>
  <div>
    <!-- Rest of the component -->
    <div v-if="currentQuestionIndex === questions.length">
      <h2>Quiz Completed!</h2>
      <p>Your Score: {{ score }}</p>
    </div>
  </div>
</template>
```

In the code above, we check if the `currentQuestionIndex` is equal to the length of the `questions` array to determine if all the questions have been answered. If true, we display a completion message along with the score.

## Conclusion
Congratulations! You have successfully built a quiz application using Vue.js. You learned how to fetch quiz questions from an API, display them in the component, handle user input, and calculate the score. Feel free to explore more complex features such as timers, multiple quizzes, and styling to enhance the application further.

Happy coding! 🚀

**#vuejs #quizapp**