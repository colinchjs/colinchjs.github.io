---
layout: post
title: "Using promises for generating and parsing CSV files in Javascript"
description: " "
date: 2023-10-26
tags: [references]
comments: true
share: true
---

CSV (Comma-Separated Values) files are commonly used for storing tabular data. JavaScript provides built-in support for generating and parsing CSV files using the `fs` module. However, working with CSV files asynchronously can be challenging.

In this article, we will explore how to use Promises in JavaScript to generate and parse CSV files asynchronously. Promises allow us to handle asynchronous operations in a more elegant and readable way.

## Generating a CSV File

To generate a CSV file using Promises, we can use the `fs` module and the `createWriteStream` function to create a writable stream to a file. We can then write the CSV content to the file using the stream's `write` method.

Here's an example of generating a CSV file using Promises:

```javascript
const fs = require('fs');

function generateCSVFile(data, filename) {
  return new Promise((resolve, reject) => {
    const stream = fs.createWriteStream(filename);

    stream.write('Name,Email\n');

    data.forEach((row) => {
      const csvRow = `${row.name},${row.email}\n`;
      stream.write(csvRow);
    });

    stream.end();

    stream.on('finish', () => {
      resolve();
    });

    stream.on('error', (err) => {
      reject(err);
    });
  });
}

// Usage
const data = [
  { name: 'John Doe', email: 'john@example.com' },
  { name: 'Jane Smith', email: 'jane@example.com' },
];

generateCSVFile(data, 'output.csv')
  .then(() => {
    console.log('CSV file generated successfully.');
  })
  .catch((err) => {
    console.error('Error generating CSV file:', err);
  });
```

In this example, the `generateCSVFile` function takes an array of data and a filename as arguments. It creates a writable stream to the specified file, writes the CSV header, and then writes each row of data as a CSV row. Finally, it resolves the Promise once the stream finishes writing and handles any errors.

## Parsing a CSV File

To parse a CSV file using Promises, we can use the `fs` module and the `createReadStream` function to create a readable stream from the CSV file. We can then listen for the `data` event to read the content of the CSV file chunk by chunk, and parse the data accordingly.

Here's an example of parsing a CSV file using Promises:

```javascript
const fs = require('fs');
const parse = require('csv-parse');

function parseCSVFile(filename) {
  return new Promise((resolve, reject) => {
    const stream = fs.createReadStream(filename);
    const parser = parse({ columns: true });

    stream.pipe(parser);

    const data = [];

    parser.on('readable', () => {
      let record;
      while ((record = parser.read())) {
        data.push(record);
      }
    });

    parser.on('end', () => {
      resolve(data);
    });

    parser.on('error', (err) => {
      reject(err);
    });
  });
}

// Usage
parseCSVFile('input.csv')
  .then((data) => {
    console.log('CSV file parsed successfully:', data);
  })
  .catch((err) => {
    console.error('Error parsing CSV file:', err);
  });
```

In this example, the `parseCSVFile` function takes a filename as an argument. It creates a readable stream from the specified file and sets up a CSV parser using the `csv-parse` library. The function listens for the `readable` event to read each record from the parser and pushes it into the `data` array. Finally, it resolves the Promise with the parsed CSV data.

## Conclusion

Promises provide a clean and concise way to handle asynchronous operations, such as generating and parsing CSV files, in JavaScript. By leveraging the `fs` module and appropriate libraries, we can easily generate and parse CSV files asynchronously, improving the performance and maintainability of our applications.

Remember to use `await` and `async` keywords when working with Promises in order to handle the results more efficiently.

#references 
[Node.js fs module documentation](https://nodejs.org/api/fs.html)
[csv-parse library documentation](https://csv.js.org/parse/)