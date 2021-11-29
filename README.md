# My Node.js & Express.js Documentation

### Total Chapters are following

1. Node.js
   1. Introduction to the playlist
   2. Introduction to node.js
   3. Local Module
2. Express.js

<br />

## Chapter 1: Node.js

### [1.2 Introduction to Node.js & setup](https://youtu.be/36R0VXmX8i8)

#### What is Node.js & Why Node.js?

- Node.js is server side environment; not a programming language.
- It helps to manage files (create, open, read, write, delete and close) on the server.
- it supports asynchronous programming.
- it helps to collect form data.
- It helps to manage (add, modify, delete data) database.
- fullstack = front-end + back-end

#### Environment setup

- check node is already installed or not using the command: node --version
- [Node.js](https://nodejs.org/en/) download & install
- Editor: anything; I prefer [Visual Studio Code](https://code.visualstudio.com/)

### [1.3 Local module](https://youtu.be/n3F1kaOfyzw)

#### What is module? Types of module?

- Module is a set of functions or variables.
- 3 types of module.
  - local module (own created module)
  - built-in-modules (node.js own module)
  - External modules (3rd party module mainly managed by npm)
- example 1

  ```js
  // message.js
  const SUBJECT = "Node.js";

  const displayInfo = (name) => {
    console.log(`Welcome ${name}`);
  };

  module.exports = { SUBJECT, displayInfo };

  // index.js
  const message = require("./message");
  console.log(message.SUBJECT);
  message.displayInfo("Anisul Islam");
  ```

- example 2

  ```js
  // message.js

  const SUBJECT = "Node.js";
  // exports.SUBJECT = "Node.js";

  const displayInfo = (name) => {
    console.log(`Welcome ${name}`);
  };

  exports.SUBJECT = SUBJECT;
  exports.displayInfo = displayInfo;

  // index.js

  // following line will get everything from message module
  const message = require("./message");

  // following line will get separate items from message module
  const { SUBJECT, displayInfo } = require("./message");
  console.log(SUBJECT);
  displayInfo("anisul");
  ```

### [1.4 Built-in module - fs module](https://youtu.be/808jcN3c8MM)

- some of the common built-in module - http, url, fs, path
- example of fs module

  ```js
  const fs = require("fs");
  console.log(fs);

  // creating a file
  fs.writeFile("test.txt", "this is some demo text", (err) => {
    if (err) {
      console.log(err);
    } else {
      console.log("File is created successfully");
    }
  });

  // appending data to a file
  fs.appendFile("test.txt", "some extra text is added", (err) => {
    if (err) {
      console.log(err);
    } else {
      console.log("data is added successfully");
    }
  });

  // reading data from a file
  fs.readFile("test.txt", "utf-8", (err, data) => {
    if (err) {
      console.log(err);
    } else {
      console.log(data);
    }
  });

  // renaming an existing file
  fs.rename("test.txt", "test2.txt", (err) => {
    if (err) {
      console.log(err);
    } else {
      console.log("successfully renamed");
    }
  });

  // checking a file exsits or not
  fs.exists("test2.txt", (result) => {
    if (result) {
      console.log("file exists");
    } else {
      console.log("file does not exist");
    }
  });

  // deleting a file
  fs.unlink("test2.txt", (err) => {
    if (err) {
      console.log(err);
    } else {
      console.log("file is deleted successfully");
    }
  });
  ```

### [1.5 Built-in module - http module](https://youtu.be/PmLJO403hvc)

- Example of a node.js http server

  ```js
  const http = require("http");

  const PORT = 3000;

  const server = http.createServer((req, res) => {
    // res.end("welcome to the server");
    res.end("<h1>welcome to the server</h1>");
  });

  server.listen(PORT, () => {
    console.log(`server is running at http://localhost:${PORT}`);
  });
  ```
