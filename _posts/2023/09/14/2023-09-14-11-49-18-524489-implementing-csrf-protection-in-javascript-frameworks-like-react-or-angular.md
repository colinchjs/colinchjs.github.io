---
layout: post
title: "Implementing CSRF protection in JavaScript frameworks like React or Angular"
description: " "
date: 2023-09-14
tags: [CSRF, JavaScriptFrameworks]
comments: true
share: true
---

CSRF (Cross-Site Request Forgery) attacks pose a significant security risk for web applications. To mitigate this risk, it's crucial to implement CSRF protection in your JavaScript frameworks like React or Angular.

## What is CSRF Protection?

CSRF attacks occur when an attacker tricks a user into unintentionally executing unwanted actions on a vulnerable web application. This is done by leveraging the trust that websites have in a user's browser. To protect against CSRF attacks, you need to ensure that server requests originated from your own web application and not from an external source.

## How to Implement CSRF Protection in React and Angular

Both React and Angular provide mechanisms to implement CSRF protection. Here are the steps to do it in each framework:

### React

1. Install the `csurf` package using your package manager of choice: 
```
npm install csurf
```
2. Set up a middleware in your server to generate and validate CSRF tokens. For example, using Express.js:

   ```javascript
   const csrf = require('csurf');
   const csrfProtection = csrf({ cookie: true });

   app.use(csrfProtection);
   ```

3. Include the CSRF token in your React application's forms. In your form components, access the token from the server and set it as a value for a hidden input field. For example:

   ```jsx
   import React from 'react';
   import { useForm } from 'react-hook-form';

   function MyForm() {
     const { register } = useForm(); // register from react-hook-form

     // Access the CSRF token from the server
     const csrfToken = document.querySelector('meta[name="csrf-token"]').getAttribute('content');

     return (
       <form>
         <input type="hidden" name="_csrf" value={csrfToken} ref={register()} />
         {/* ... other form fields */}
       </form>
     );
   }
   ```

4. Send the CSRF token along with the requests made by your React application. Include a custom header, such as `X-CSRF-Token`, in your AJAX requests or set it as a default header using a library like Axios.

### Angular

1. Configure your backend server to generate and validate CSRF tokens. This step depends on the server-side framework you're using. For example, in Node.js with Express.js:
   
   ```javascript
   const csurf = require('csurf');
   const csrfProtection = csurf({ cookie: true });

   app.use(csrfProtection);
   ```

2. Include the CSRF token in your Angular application's requests. To do this, you can create a custom Angular HttpInterceptor that intercepts outgoing HTTP requests and adds the CSRF token to the headers. Here's an example:

   ```typescript
   import { Injectable } from '@angular/core';
   import { HttpInterceptor, HttpRequest, HttpHandler, HttpEvent } from '@angular/common/http';
   import { Observable } from 'rxjs';

   @Injectable()
   export class CsrfInterceptor implements HttpInterceptor {
     intercept(request: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
       const csrfToken = document.querySelector('meta[name="csrf-token"]').getAttribute('content');
       const modifiedRequest = request.clone({ setHeaders: { 'X-CSRF-Token': csrfToken } });
       return next.handle(modifiedRequest);
     }
   }
   ```

   Don't forget to add this interceptor to your Angular module's providers.

## Conclusion

Implementing CSRF protection in your JavaScript frameworks like React and Angular is essential for ensuring the security of your web applications. By following the provided steps, you can significantly reduce the risk of CSRF attacks and protect your users' data. #CSRF #JavaScriptFrameworks