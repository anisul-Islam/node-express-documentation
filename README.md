# My Node.js & Express.js Documentation

### Total Chapters are following

1. Node.js
   1. Introduction to the playlist
   2. Introduction to node.js
   3. Local Module
   4. Built-in module - fs module
   5. Built-in module - http module
   6. request, response, status code
   7. npm crash course
   8. http routing
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

### [1.6 request, response and status code](https://youtu.be/lHfnjUP-N4E)

- Example

  ```js
  // index.js file
  const http = require("http");

  const PORT = 3000;

  const server = http.createServer((req, res) => {
    res.writeHead(200, { "Content-Type": "text/plain" });
    res.write("welcome to the server");

    // if we want to return html as status
    // res.writeHead(200, { "Content-Type": "text/html" });
    // res.write("<h1>welcome to the server</h1>");

    res.end();
  });

  server.listen(PORT, () => {
    console.log(`server is running at http://localhost:${PORT}`);
  });
  ```

### [1.7 External modules | npm crash course](https://youtu.be/A8W1p8suw5I)

- first initialize npm with the command `npm init` then follow the instructions
- we can also use `npm init -y` command for ignoring the installation instructions
- npm packages : https://www.npmjs.com/
- Install https://www.npmjs.com/package/random-fruits-name package
  and follow the instructions

### [1.8 http routing](https://youtu.be/Vlk4UPzi6tc)

- initialize the npm `npm init -y`
- example is given below:

  ```html
  // index.html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>home</title>
    </head>
    <body>
      <nav>
        <ul>
          <li><a href="/">Home</a></li>
          <li><a href="/about">About</a></li>
          <li><a href="/contact">Contact</a></li>
        </ul>
      </nav>
      <main>
        <h1>welcome to home page</h1>
      </main>
    </body>
  </html>
  ```

  ```html
  // about.html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>about</title>
    </head>
    <body>
      <nav>
        <ul>
          <li><a href="/">Home</a></li>
          <li><a href="/about">About</a></li>
          <li><a href="/contact">Contact</a></li>
        </ul>
      </nav>
      <main>
        <h1>welcome to about page</h1>
      </main>
    </body>
  </html>
  ```

  ```html
  // contact.html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>contact</title>
    </head>
    <body>
      <nav>
        <ul>
          <li><a href="/">Home</a></li>
          <li><a href="/about">About</a></li>
          <li><a href="/contact">Contact</a></li>
        </ul>
      </nav>
      <main>
        <h1>welcome to contact page</h1>
      </main>
    </body>
  </html>
  ```

  ```html
  // error.html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>error</title>
    </head>
    <body>
      <nav>
        <ul>
          <li><a href="/">Home</a></li>
          <li><a href="/about">About</a></li>
          <li><a href="/contact">Contact</a></li>
        </ul>
      </nav>
      <main>
        <h1>page not found 404</h1>
      </main>
    </body>
  </html>
  ```

  ```js
  // index.js
  const http = require("http");
  const fs = require("fs");

  const PORT = 3000;

  const server = http.createServer((req, res) => {
    const handleReadFile = (fileName, statusCode) => {
      fs.readFile(fileName, (err, data) => {
        res.writeHead(statusCode, { "Content-Type": "text/html" });
        res.write(data);
        res.end();
      });
    };

    if (req.url === "/") {
      handleReadFile("index.html", 200);
    } else if (req.url === "/about") {
      handleReadFile("about.html", 200);
    } else if (req.url === "/contact") {
      handleReadFile("contact.html", 200);
    } else {
      handleReadFile("error.html", 404);
    }
  });

  server.listen(PORT, () => {
    console.log(`server is running at http://localhost:${PORT}`);
  });
  ```

- run the server `node index.js`
