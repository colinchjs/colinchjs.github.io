---
layout: post
title: "Using AJAX to fetch and display data from a SQL database in JavaScript"
description: " "
date: 2023-09-15
tags: [fetchButton, dataContainer]
comments: true
share: true
---

In today's web development world, **AJAX** (Asynchronous JavaScript and XML) plays a crucial role in fetching and displaying data from a server without refreshing the entire page. In this blog post, we will explore how to use AJAX to fetch and display data from a **SQL database** in JavaScript.

## Prerequisites

To follow along with this tutorial, you will need the following:

- A basic understanding of JavaScript.
- An SQL database (such as MySQL or PostgreSQL) already set up.
- A server-side language (such as PHP, Python, or Node.js) to handle the AJAX request and interact with the database.

## Step 1: Setting up the Database

First, let's set up our SQL database with some sample data. Create a table named `users` with the following columns: `id`, `name`, `email`, and `phone`. Insert some sample data into the table.

## Step 2: Creating the HTML Markup

Next, let's create an HTML file with a button and a container where we can display the fetched data. We will add an empty `div` element to hold the data.

```html
<!DOCTYPE html>
<html>
<head>
    <title>AJAX Database Fetch Example</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
</head>
<body>
    <button id="fetchButton">Fetch Data</button>
    <div id="dataContainer"></div>

    <script src="script.js"></script>
</body>
</html>
```

## Step 3: Writing the JavaScript Code

Create a new file named `script.js` and include it in the HTML file. In this JavaScript file, we will make an AJAX request to fetch data from the database and update the `dataContainer` HTML element with the fetched data.

```javascript
$(document).ready(function() {
    // When the button is clicked
    $("#fetchButton").on('click', function() {
        // Make an AJAX request to fetch data from the server
        $.ajax({
            url: "fetchData.php",
            method: "GET",
            dataType: "json",
            success: function(data) {
                // Clear the data container
                $("#dataContainer").empty();

                // Loop through the fetched data and display it in the container
                $.each(data, function(index, item) {
                    var userData = `<p>ID: ${item.id}</p>
                                    <p>Name: ${item.name}</p>
                                    <p>Email: ${item.email}</p>
                                    <p>Phone: ${item.phone}</p>`;

                    // Append the user data to the container
                    $("#dataContainer").append(userData);
                });
            },
            error: function() {
                console.log("Error fetching data.");
            }
        });
    });
});
```

## Step 4: Creating the Server-Side Code

Now let's create a server-side script to handle the AJAX request and interact with the SQL database. For this example, we will use PHP.

Create a PHP file named `fetchData.php` and include the following code:

```php
<?php
// Connect to the SQL database
$host = "localhost";
$username = "your_username";
$password = "your_password";
$dbname = "your_database";

$conn = new PDO("mysql:host=$host;dbname=$dbname", $username, $password);

// Fetch data from the 'users' table
$query = "SELECT * FROM users";
$statement = $conn->prepare($query);
$statement->execute();

// Fetch the data as JSON
$data = $statement->fetchAll(PDO::FETCH_ASSOC);
echo json_encode($data);
```

Make sure to replace `your_username`, `your_password`, and `your_database` with your own database credentials.

## Step 5: Testing the Application

Open the HTML file in your web browser, and when you click the "Fetch Data" button, the AJAX request will be sent to the server-side script (`fetchData.php`). The script will retrieve the data from the SQL database and return it as JSON. The JavaScript code will then update the `dataContainer` with the fetched data.

Congratulations! You have successfully used AJAX to fetch and display data from a SQL database using JavaScript.

#hashtags: AJAX #JavaScript #SQL #database