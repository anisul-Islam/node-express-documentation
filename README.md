# My Node.js & Express.js Documentation

### Total Chapters are following

1. Node.js
   1. Introduction to node.js
   2. Local Module
1. Express.js

<br />

## Chapter 1: Node.js

### [1.1 Introduction to Node.js & setup](https://youtu.be/36R0VXmX8i8)

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

### [1.2 Local module](https://youtu.be/n3F1kaOfyzw)

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
