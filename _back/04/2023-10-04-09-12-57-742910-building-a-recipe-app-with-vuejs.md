---
layout: post
title: "Building a recipe app with Vue.js"
description: " "
date: 2023-10-04
tags: [setup)]
comments: true
share: true
---

In this tutorial, we will learn how to build a recipe application using Vue.js. Vue.js is a popular and lightweight JavaScript framework that allows us to create dynamic and interactive web applications with ease. By the end of this tutorial, you will have a fully functioning recipe app that allows users to view, search, and add new recipes.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Creating the Recipe Component](#creating-the-recipe-component)
- [Displaying Recipe Data](#displaying-recipe-data)
- [Adding Search Functionality](#adding-search-functionality)
- [Adding New Recipe Form](#adding-new-recipe-form)
- [Conclusion](#conclusion)

## Prerequisites
To follow along with this tutorial, you will need to have the following:

- Basic knowledge of HTML, CSS, and JavaScript
- Node.js and npm (Node Package Manager) installed on your system
- Vue CLI installed globally (you can install it by running `npm install -g @vue/cli`)

## Setup
1. Start by creating a new Vue.js project using the Vue CLI. Open your terminal and run the following command:
```
vue create recipe-app
```

2. Choose the default preset and wait for the project to be created.

3. Navigate to the project folder:
```
cd recipe-app
```

4. Start the development server:
```
npm run serve
```

5. Open your browser and visit `http://localhost:8080` to see the default Vue.js app.

## Creating the Recipe Component
First, let's create a new component to handle the display of recipes. 

1. Inside the `src` folder, create a new folder named `components`.

2. Inside the `components` folder, create a new file called `Recipe.vue`.

3. Open `Recipe.vue` and add the following code:
```vue
<template>
  <div>
    <h2>{{ recipe.title }}</h2>
    <p>{{ recipe.description }}</p>
    <ul>
      <li v-for="ingredient in recipe.ingredients" :key="ingredient">{{ ingredient }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    recipe: {
      type: Object,
      required: true
    }
  }
}
</script>

<style>
/* Add custom styles for the recipe component */
</style>
```

## Displaying Recipe Data
Now, let's update the `App.vue` component to display the recipe data.

1. Open `App.vue` and replace the existing code with the following:
```vue
<template>
  <div>
    <h1>Welcome to the Recipe App</h1>
    <div v-for="recipe in recipes" :key="recipe.id">
      <recipe :recipe="recipe"></recipe>
    </div>
  </div>
</template>

<script>
import Recipe from './components/Recipe.vue';

export default {
  components: {
    Recipe
  },
  data() {
    return {
      recipes: [
        {
          id: 1,
          title: 'Delicious Pancakes',
          description: 'A simple and tasty pancake recipe.',
          ingredients: ['Flour', 'Milk', 'Eggs', 'Sugar', 'Butter']
        },
        {
          id: 2,
          title: 'Spaghetti Bolognese',
          description: 'A classic Italian pasta dish.',
          ingredients: ['Spaghetti', 'Ground Beef', 'Tomatoes', 'Onions', 'Garlic']
        }
      ]
    }
  }
}
</script>
```

## Adding Search Functionality
We can enhance our recipe app by adding search functionality.

1. Add the following data property and method to the `App.vue` component:
```vue
data() {
  return {
    recipes: [...],
    searchQuery: ''
  }
},
computed: {
  filteredRecipes() {
    return this.recipes.filter(recipe => recipe.title.toLowerCase().includes(this.searchQuery.toLowerCase()));
  }
}
```

2. Update the recipe loop in the template to use `filteredRecipes` instead of `recipes`:
```vue
<div v-for="recipe in filteredRecipes" :key="recipe.id">
```

3. Add an input field for the search query in the template:
```vue
<input v-model="searchQuery" type="text" placeholder="Search recipes">
```

## Adding New Recipe Form
Finally, let's add a form to allow users to add new recipes to our app.

1. Add the following data property and method to the `App.vue` component:
```vue
data() {
  return {
    recipes: [...],
    searchQuery: '',
    newRecipe: {
      title: '',
      description: '',
      ingredients: ''
    }
  }
},
methods: {
  addRecipe() {
    const ingredients = this.newRecipe.ingredients.split(',').map(ingredient => ingredient.trim());
    const recipe = {
      id: this.recipes.length + 1,
      title: this.newRecipe.title,
      description: this.newRecipe.description,
      ingredients: ingredients
    };
    this.recipes.push(recipe);
    this.newRecipe.title = '';
    this.newRecipe.description = '';
    this.newRecipe.ingredients = '';
  }
}
```

2. Add the form markup and the `addRecipe` method to the template:
```vue
<form @submit.prevent="addRecipe">
  <input v-model="newRecipe.title" type="text" placeholder="Recipe Title" required>
  <textarea v-model="newRecipe.description" placeholder="Recipe Description" required></textarea>
  <input v-model="newRecipe.ingredients" type="text" placeholder="Ingredients (separated by commas)" required>
  <button type="submit">Add Recipe</button>
</form>
```

## Conclusion
Congratulations! You have successfully built a recipe app using Vue.js. You learned how to create components, display data, implement search functionality, and add new recipes to your app. Feel free to enhance the app further by adding more features like editing and deleting recipes. Happy coding!

*[#VueJS](https://example.com/vuejs) [#RecipeApp](https://example.com/recipeapp)*