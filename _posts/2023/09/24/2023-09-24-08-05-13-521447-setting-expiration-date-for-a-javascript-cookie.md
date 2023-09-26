---
layout: post
title: "Setting expiration date for a JavaScript cookie"
description: " "
date: 2023-09-24
tags: [cookies]
comments: true
share: true
---
    // Function to set cookie expiry date
    function setCookieWithExpiry(cookieName, cookieValue, days) {
        // Get current date and time
        var currentDate = new Date();
        
        // Calculate expiry date
        var expiryDate = new Date(currentDate.getTime() + (days * 24 * 60 * 60 * 1000));
        
        // Convert expiry date to UTC string format
        var expiryDateString = expiryDate.toUTCString();
        
        // Set the cookie with expiry date
        document.cookie = cookieName + "=" + cookieValue + "; expires=" + expiryDateString;
    }
    
    // Usage example
    setCookieWithExpiry("myCookie", "example value", 7);
</script>

#JavaScript #cookies