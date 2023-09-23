---
layout: post
title: "Implementing a cookie-based ad delivery system in JavaScript"
description: " "
date: 2023-09-24
tags: []
comments: true
share: true
---

With the growing popularity of online advertising, publishers need effective ways to deliver targeted ads to their users. One commonly used method is implementing a cookie-based ad delivery system. In this blog post, we will explore how you can implement such a system using JavaScript.

## What are Cookies?

Cookies are small pieces of data that websites store on a user's browser. They are often used to remember information about the user and provide a personalized browsing experience. In the context of ad delivery, cookies can be used to track user preferences and deliver relevant ads.

## Steps to Implement a Cookie-Based Ad Delivery System

### 1. Set up the HTML Structure

To begin, let's create a simple HTML structure to display the ad slots on your website:

```html
<div id="ad-slot1"></div>
<div id="ad-slot2"></div>
<div id="ad-slot3"></div>
```

### 2. Create the Ad Delivery Script

Next, let's implement the JavaScript code that will handle the ad delivery system:

```javascript
// Function to display targeted ad
function displayAd(adSlot) {
    // Check if there is a targeted ad for this slot
    if (document.cookie.includes(adSlot)) {
        // If a targeted ad exists, display it
        const adData = getAdData(adSlot);
        // Render the ad on the webpage
        adSlot.innerHTML = `<a href="${adData.link}">
            <img src="${adData.image}" alt="${adData.alt}" />
        </a>`;
    } else {
        // If no targeted ad, display a default ad
        adSlot.innerHTML = `<a href="https://example.com">
            <img src="default-ad-image.png" alt="Default Ad" />
        </a>`;
    }
}

// Function to get ad data from cookies
function getAdData(adSlot) {
    // Extract the ad data from the cookie
    const cookie = document.cookie
        .split('; ')
        .find((row) => row.startsWith(`${adSlot}=`))
        .split('=')[1];
    // Parse and return the ad data as an object
    return JSON.parse(decodeURIComponent(cookie));
}
```

### 3. Set the Ad Cookies

Now, you need to set the ad cookies on the user's browser. This can be done when the user interacts with your website or landing page. For example:

```javascript
// Set ad cookies when user interacts with the website
function setUserPreferences() {
    // Set a sample ad data for ad slot1
    const adData = {
        link: "https://example.com/product1",
        image: "ad-image1.png",
        alt: "Ad for Product 1"
    };
    
    // Set the ad data in a cookie
    document.cookie = `ad-slot1=${encodeURIComponent(JSON.stringify(adData))}; expires=Fri, 31 Dec 2022 23:59:59 GMT; path=/`;
    
    // ...
    // Set ad data for other ad slots if needed
    // ...
    
    // Refresh the ad slots to deliver targeted ads
    displayAd(document.getElementById("ad-slot1"));
    // ...
    // Refresh other ad slots
    // ...
}
```

### 4. Display the Ads

Finally, call the `displayAd()` function for each ad slot on your webpage to display the ads:

```javascript
// Display the ads on page load
window.addEventListener("load", () => {
    displayAd(document.getElementById("ad-slot1"));
    displayAd(document.getElementById("ad-slot2"));
    displayAd(document.getElementById("ad-slot3"));
});
```

## Conclusion

Implementing a cookie-based ad delivery system in JavaScript can greatly enhance the user experience and increase the effectiveness of online advertising. By using cookies to track user preferences and deliver targeted ads, publishers can ensure that their ads reach the right audience.

Remember to handle user privacy and adhere to relevant regulations when collecting and using cookies.