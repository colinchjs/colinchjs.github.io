---
layout: post
title: "Implementing a cookie consent banner in JavaScript"
description: " "
date: 2023-09-24
tags: [cookie, f8f8f8]
comments: true
share: true
---

In today's digital landscape, websites often rely on the use of cookies to enhance user experience and gather important analytics. However, with the emphasis on user privacy and data protection, it has become crucial for websites to obtain consent from visitors before placing cookies on their devices. In this blog post, we will explore how to implement a cookie consent banner using JavaScript.

## What is a Cookie Consent Banner?

A cookie consent banner is a message displayed on a website that informs visitors about the use of cookies and asks for their consent. This banner typically includes a brief explanation of cookies, a link to the website's privacy policy, and buttons to accept or decline the use of cookies.

## How to Implement a Cookie Consent Banner

To implement a cookie consent banner, follow these steps:

**Step 1: Create the HTML Markup**
```html
<div id="cookie-banner">
    <p>This website uses cookies to ensure you get the best experience. By continuing to browse the site, you are agreeing to our use of cookies. <a href="/privacy-policy">Learn more</a></p>
    <button id="cookie-accept">Accept</button>
    <button id="cookie-decline">Decline</button>
</div>
```

**Step 2: Style the Banner**
```css
#cookie-banner {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: #f8f8f8;
    padding: 20px;
    text-align: center;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    z-index: 9999;
}

#cookie-banner p {
    margin: 0;
}

#cookie-accept {
    background-color: #4caf50;
    color: white;
    border: none;
    padding: 10px 20px;
    margin-right: 10px;
    cursor: pointer;
}

#cookie-decline {
    background-color: #f44336;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
}
```

**Step 3: Handle the User Interactions**
```javascript
window.onload = function() {
    var cookieBanner = document.getElementById('cookie-banner');
    var acceptButton = document.getElementById('cookie-accept');
    var declineButton = document.getElementById('cookie-decline');

    acceptButton.addEventListener('click', function() {
        cookieBanner.style.display = 'none';
        setCookie('cookie_consent', 'true', 365);
    });

    declineButton.addEventListener('click', function() {
        cookieBanner.style.display = 'none';
        setCookie('cookie_consent', 'false', 365);
    });

    function setCookie(name, value, days) {
        var expires = '';
        if (days) {
            var date = new Date();
            date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
            expires = '; expires=' + date.toUTCString();
        }
        document.cookie = name + '=' + (value || '') + expires + '; path=/';
    }
};
```

**Step 4: Check Consent on Page Load**
```javascript
window.onload = function() {
    var consent = getCookie('cookie_consent');
    if (consent === 'true') {
        // Code to execute if consent is given
    } else if (consent === 'false') {
        // Code to execute if consent is declined
    } else {
        var cookieBanner = document.getElementById('cookie-banner');
        cookieBanner.style.display = 'block';
    }

    function getCookie(name) {
        var cookieName = name + '=';
        var decodedCookie = decodeURIComponent(document.cookie);
        var cookieArray = decodedCookie.split(';');
        for (var i = 0; i < cookieArray.length; i++) {
            var cookie = cookieArray[i];
            while (cookie.charAt(0) === ' ') {
                cookie = cookie.substring(1);
            }
            if (cookie.indexOf(cookieName) === 0) {
                return cookie.substring(cookieName.length, cookie.length);
            }
        }
        return '';
    }
};
```

## Conclusion

Implementing a cookie consent banner is a crucial step towards ensuring compliance with data protection regulations and respecting user privacy. By following the steps outlined in this blog post, you can easily add a cookie consent banner using JavaScript. Remember to customize the banner's design and functionality to align with your website's branding and privacy policy.

#javascript #webdevelopment