---
layout: post
title: "Handling JWT token invalidation on password changes or account deactivation"
description: " "
date: 2023-10-03
tags: [authentication]
comments: true
share: true
---

When working with JSON Web Tokens (JWT) for authentication in your web application, it is essential to handle token invalidation properly. One common scenario to consider is when a user changes their password or deactivates their account. In such cases, you need to invalidate the existing JWT tokens associated with the user to prevent unauthorized access.

## Why Invalidate JWT Tokens?

JWT tokens provide a stateless way to authenticate users. Once issued, JWT tokens are valid until they expire or are manually revoked. If a user changes their password or deactivates their account, it's critical to invalidate their existing tokens to ensure they no longer have access to protected resources.

## Two Approaches to Token Invalidation

There are two common approaches to handle token invalidation on password changes or account deactivation:

### 1. Blacklisting Approach

In this approach, you maintain a centralized blacklist of invalidated tokens. When a user changes their password or deactivates their account, you add their token(s) to the blacklist. Every time a JWT token is presented for authentication, you check if it exists in the blacklist. If it does, you reject the token and deny access.

### 2. Expiry Time Approach

In this approach, you set a short expiration time for JWT tokens (e.g., a few minutes) and rely on token expiration to invalidate previous tokens. When a user changes their password or deactivates their account, any previously issued tokens will soon expire and become invalid.

## Implementing Token Invalidation

To implement token invalidation on password changes or account deactivation, you need to update your authentication logic accordingly. Here's a high-level overview of the steps involved:

1. When a user changes their password or deactivates their account, mark their account as deactivated or set a flag indicating the password change.
2. If using the blacklisting approach:
   - Maintain a centralized database or cache to store blacklisted tokens.
   - When a user changes their password or deactivates their account, add their existing token(s) to the blacklist.
   - Before allowing access, check if the presented token exists in the blacklist.
3. If using the expiry time approach:
   - Set a short expiration time for JWT tokens, such as 5 to 10 minutes.
   - Whenever a user changes their password or deactivates their account, any previously issued tokens will soon expire and become invalid.

Whichever approach you choose, it is crucial to update your authentication logic to handle token invalidation properly. Additionally, consider using a secure token storage mechanism to mitigate any potential security risks.

#jwt #authentication