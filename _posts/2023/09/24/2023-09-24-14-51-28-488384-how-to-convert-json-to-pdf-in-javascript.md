---
layout: post
title: "How to convert JSON to PDF in JavaScript."
description: " "
date: 2023-09-24
tags: [JSON]
comments: true
share: true
---

In this tutorial, we will learn how to convert JSON data to a PDF file using JavaScript. JSON (JavaScript Object Notation) is a popular data format used to send and receive data over the internet. 

To accomplish this task, we will be using a JavaScript library called [pdfmake](http://pdfmake.org/), which provides a simple and powerful way to generate PDF files dynamically in the browser.

## Prerequisites
To follow along with this tutorial, you should have a basic understanding of JavaScript and be familiar with JSON data structures. Additionally, you will need access to a text editor and a web browser.

## Steps

### 1. Setting up the project

Create a new HTML file and open it in your text editor. At the top of the file, add the following script tag to include the pdfmake library:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.68/pdfmake.min.js"></script>
```

### 2. Creating JSON Data

Next, create a JavaScript object that represents the JSON data you want to convert to PDF. For example, let's consider a simple JSON object representing a list of books:

```javascript
const books = [
  { title: "The Great Gatsby", author: "F. Scott Fitzgerald", year: 1925 },
  { title: "To Kill a Mockingbird", author: "Harper Lee", year: 1960 },
  { title: "Pride and Prejudice", author: "Jane Austen", year: 1813 }
];
```

### 3. Generating PDF

Now we can generate a PDF document using the pdfmake library. Below is an example function that takes the JSON data and creates a PDF with a table displaying the JSON contents:

```javascript
function generatePDF(data) {
  const documentDefinition = {
    content: [
      { text: "Books List", style: "header" },
      {
        style: "table",
        table: {
          body: [
            ["Title", "Author", "Year"],
            ...data.map(book => [book.title, book.author, book.year])
          ]
        }
      }
    ],
    styles: {
      header: {
        fontSize: 18,
        bold: true,
        alignment: "center"
      },
      table: {
        margin: [0, 15, 0, 15]
      }
    }
  };
  
  pdfMake.createPdf(documentDefinition).open();
}

// Call the function with the JSON data
generatePDF(books);
```

### 4. Testing the Result

Save the HTML file and open it in your web browser. You should see a "Books List" PDF document open, displaying the table of book information.

## Conclusion

In this tutorial, we have learned how to convert JSON data to a PDF file using JavaScript and the pdfmake library. This can be useful when you need to generate printable reports or documents dynamically in a web application. Remember to ensure you have the necessary permissions and comply with any licensing requirements when using third-party libraries.

#JavaScript #JSON #PDF