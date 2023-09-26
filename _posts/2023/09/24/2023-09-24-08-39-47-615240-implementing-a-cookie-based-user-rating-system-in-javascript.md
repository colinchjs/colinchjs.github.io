---
layout: post
title: "Implementing a cookie-based user rating system in JavaScript"
description: " "
date: 2023-09-24
tags: [cookies]
comments: true
share: true
---

In this blog post, we will explore how to implement a cookie-based user rating system using JavaScript. This system allows users to rate content and stores their ratings on their browser's cookies. Let's get started!

## Prerequisites
To follow along with this implementation, you should have a basic understanding of HTML, CSS, and JavaScript.

## Setting Up the HTML
First, let's set up the basic HTML structure for our rating system. We will create a container div that will contain the ratings and a set of star icons representing different rating options.

```html
<div id="rating-container">
    <i class="far fa-star"></i>
    <i class="far fa-star"></i>
    <i class="far fa-star"></i>
    <i class="far fa-star"></i>
    <i class="far fa-star"></i>
</div>
```

## Adding CSS Styles
Next, let's add some CSS styles to make the ratings visually appealing. We will use [Font Awesome](https://fontawesome.com/) for the star icons.

```html
<style>
    .far.fa-star {
        cursor: pointer;
        color: grey;
    }
    
    .fas.fa-star {
        cursor: pointer;
        color: gold;
    }
</style>
```

## Implementing the JavaScript Logic
Now, let's dive into the JavaScript code that will handle the rating functionality. We will use Event Listeners to capture user clicks on the star icons.

```javascript
<script>
    const stars = document.querySelectorAll('.fa-star');

    function setRating(rating) {
        stars.forEach((star, index) => {
            star.classList.toggle('fas', index < rating);
            star.classList.toggle('far', index >= rating);
        });
    }

    stars.forEach((star, index) => {
        star.addEventListener('click', () => {
            const rating = index + 1;
            setRating(rating);

            // Save the rating in a cookie
            document.cookie = `rating=${rating}; expires=Wed, 01 Jan 2022 00:00:00 UTC; path=/`;
        });
    });
</script>
```

In the code above, we first select all the star icons using `document.querySelectorAll('.fa-star')`. 

The `setRating()` function is responsible for updating the star icons based on the user's selection. It uses the `toggle()` method to add or remove the 'fas' and 'far' classes to display the appropriate filled or empty star icons.

We then add an event listener to each star icon, capturing the user's click. Inside the event listener, we retrieve the rating based on the star's index. We update the rating display using the `setRating()` function, and finally, we save the rating in a cookie using `document.cookie`.

## Retrieving the User Rating
To retrieve the user's rating when they visit the website again, you can use the following JavaScript code:

```javascript
<script>
    function getCookieValue(name) {
        const cookieArr = document.cookie.split(';');

        for (let i = 0; i < cookieArr.length; i++) {
            const cookiePair = cookieArr[i].split('=');
            if (name === cookiePair[0].trim()) {
                return cookiePair[1];
            }
        }

        return null;
    }

    const savedRating = getCookieValue('rating');
    
    if (savedRating) {
        setRating(Number(savedRating));
    }
</script>
```

The `getCookieValue()` function retrieves the value of a specific cookie. It splits the cookies by ';', then by '=', and checks if the cookie name matches the desired name.

We then call `getCookieValue('rating')` to retrieve the saved rating, and if it exists, we pass it to the `setRating()` function to update the star icons accordingly.

## Conclusion
By following the steps outlined in this blog post, you can implement a cookie-based user rating system in JavaScript. Users will be able to rate content, and their ratings will be stored on their browser's cookies. This simple system can be a valuable addition to any website, providing user feedback and engagement.

Give it a try and enhance your website's interactivity with this user rating system!

#javascript #cookies