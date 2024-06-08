# 📖 Node.js Interview Guide

## Table of Contents
1. [What is NodeJS?](#what-is-nodejs)
2. [Avoiding Callback Hells](#avoiding-callback-hells)
3. [Background or Worker Processes](#background-or-worker-processes)
4. [Why is NodeJS Single Threaded?](#why-is-nodejs-single-threaded)
5. [Types of API Functions in Node](#types-of-api-functions-in-node)
6. [Chaining in NodeJS](#chaining-in-nodejs)
7. [Streams in NodeJS](#streams-in-nodejs)
8. [Package.json](#packagejson)
9. [Module Exports](#module-exports)
10. [Security Implementations in NodeJS](#security-implementations-in-nodejs)
11. [URL Module](#url-module)
12. [Middleware](#middleware)
13. [Libuv](#libuv)
14. [Async.queue](#asyncqueue)
15. [Spawn vs Fork](#spawn-vs-fork)
16. [ExpressJS](#expressjs)
17. [Buffer Class](#buffer-class)
18. [Handling Child Threads](#handling-child-threads)
19. [Types of Streams](#types-of-streams)
20. [Exit Codes](#exit-codes)
21. [Cryptography in NodeJS](#cryptography-in-nodejs)
22. [Express App and Server Folder Separation](#express-app-and-server-folder-separation)
23. [Assert Module](#assert-module)
24. [Async_hooks Module](#asynchooks-module)
25. [Buffer Objects](#buffer-objects)
26. [Implementing Addons](#implementing-addons)
27. [Spawning Child Processes](#spawning-child-processes)
28. [Multi-core Systems](#multi-core-systems)
29. [Console Data Type](#console-data-type)
30. [Console Methods](#console-methods)
31. [Performing Cryptographic Functions](#performing-cryptographic-functions)
32. [Reading and Writing Files](#reading-and-writing-files)
33. [Global Objects](#global-objects)
34. [Asynchronous Network API](#asynchronous-network-api)
35. [OS Module Utilities](#os-module-utilities)
36. [Suitable Use Cases for NodeJS](#suitable-use-cases-for-nodejs)
37. [Unsuitable Use Cases for NodeJS](#unsuitable-use-cases-for-nodejs)
38. [Key Features of NodeJS](#key-features-of-nodejs)
39. [REPL in NodeJS](#repl-in-nodejs)
40. [CRUD Operations without Frameworks](#crud-operations-without-frameworks)
41. [NodeJS vs AJAX vs jQuery](#nodejs-vs-ajax-vs-jquery)
42. [EventEmitter in NodeJS](#eventemitter-in-nodejs)

---
## What is NodeJS?
Node.js is an open-source, cross-platform, JavaScript runtime environment that executes JavaScript code outside of a browser. It was created by Ryan Dahl.

## Avoiding Callback Hells
There are several ways to avoid callback hells:
1. Modularization: Break callbacks into independent functions.
2. Use a control flow library like async.
3. Use generators with Promises.
4. Use async/await.
```javascript
const fetchData = async () => {
  try {
    const data = await getDataFromAPI();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
};
```
## Background or Worker Processes
Worker processes are useful for tasks like sending emails or processing images. Options include RabbitMQ and Kafka.
```javascript
const { Worker } = require('worker_threads');

const worker = new Worker('./worker.js');

worker.on('message', message => {
  console.log(`Received message: ${message}`);
});

worker.postMessage('Start working');
```
## Why is NodeJS Single Threaded?
Node.js is single-threaded for async processing to achieve better performance and scalability under typical web loads compared to thread-based implementations.

## Types of API Functions in Node
1. Blocking functions - Execute synchronously.
2. Non-blocking functions - Execute asynchronously.
```javascript
// Blocking
const data = fs.readFileSync('/file.md');
console.log(data);

// Non-blocking
fs.readFile('/file.md', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```
## Chaining in NodeJS
Chaining connects the output of one stream to another, creating a chain of multiple stream operations.
```javascript
const fs = require('fs');
const zlib = require('zlib');

fs.createReadStream('file.txt')
  .pipe(zlib.createGzip())
  .pipe(fs.createWriteStream('file.txt.gz'));
```
## Streams in NodeJS
Streams allow reading from a source and writing to a destination continuously. There are four types:
1. Readable
2. Writable
3. Duplex
4. Transform
```javascript
{
  "name": "my-node-app",
  "version": "1.0.0",
  "main": "index.js",
  "dependencies": {
    "express": "^4.17.1"
  },
  "scripts": {
    "start": "node index.js"
  }
}
```
## Package.json
The package.json file is the manifest file containing the metadata of the project.
```javascript
{
  "name": "my-node-app",
  "version": "1.0.0",
  "main": "index.js",
  "dependencies": {
    "express": "^4.17.1"
  },
  "scripts": {
    "start": "node index.js"
  }
}
```
## Module Exports
Modules in Node.js encapsulate code into a single unit which can be used by shifting related functions into a single file.
```javascript
// math.js
function add(a, b) {
  return a + b;
}

module.exports = { add };

// app.js
const math = require('./math');
console.log(math.add(2, 3));
```
## Security Implementations in NodeJS
Key security implementations include authentications and error handling.
```javascript
const express = require('express');
const app = express();

const authMiddleware = (req, res, next) => {
  if (req.headers.authorization === 'secret-token') {
    next();
  } else {
    res.sendStatus(403);
  }
};

app.use(authMiddleware);

app.get('/', (req, res) => {
  res.send('Hello, authenticated user!');
});

app.listen(3000);
```
## URL Module
The URL module splits up a web address into readable parts.
```javascript
const URL = require('url');
const myURL = new URL('https://example.org:8000/foo');

console.log(myURL.hostname); // 'example.org'
console.log(myURL.port);     // '8000'
console.log(myURL.pathname); // '/foo'
```
## Middleware
Middleware captures logs, enables rate limits, routing, authentication, etc. Examples include body-parser and custom middleware.
```javascript
const express = require('express');
const app = express();

const loggerMiddleware = (req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
};

app.use(loggerMiddleware);

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(3000);
```
## Libuv
Libuv is a multi-platform support library for asynchronous I/O. Features include a full-featured event loop, file system events, asynchronous operations, and more.

## Async.queue
The async.queue function takes a Task Function and a Concurrency Value as input.
```javascript
const async = require('async');

const q = async.queue((task, callback) => {
  console.log('Processing task', task.name);
  callback();
}, 2);

q.push({name: 'task1'});
q.push({name: 'task2'});
q.push({name: 'task3'});
```
## Spawn vs Fork
- `spawn()`: Launches a new process without creating a new V8 instance.
- `fork()`: Creates a new V8 instance.
```javascript
const { spawn } = require('child_process');
const ls = spawn('ls', ['-lh', '/usr']);

ls.stdout.on('data', (data) => {
  console.log(`stdout: ${data}`);
});

ls.stderr.on('data', (data) => {
  console.error(`stderr: ${data}`);
});

ls.on('close', (code) => {
  console.log(`child process exited with code ${code}`);
});
```
## ExpressJS
Express.js is a framework for managing data flow between server and routes in server-side applications.
```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```
## Buffer Class
The Buffer class stores raw data similar to an array of integers, corresponding to raw memory allocation outside the V8 heap.
```javascript
const buf = Buffer.from('hello world', 'utf8');
console.log(buf.toString('hex'));
```
## Handling Child Threads
Node.js uses the `spawn()` method for asynchronous I/O tasks without exposing child threads. For threading, include the ChildProcess module.
```javascript
const { spawn } = require('child_process');
const child = spawn('node', ['child.js']);

child.stdout.on('data', (data) => {
  console.log(`stdout: ${data}`);
});
```
## Types of Streams
1. Readable: For reading data.
2. Writable: For writing data.
3. Duplex: For both reading and writing.
4. Transform: For modifying data.

## Exit Codes
Exit codes finish specific processes. Examples include:
- Uncaught fatal exception
- Fatal Error
- Internal JavaScript Evaluation Failure

## Cryptography in NodeJS
Node.js supports cryptography through the Crypto module for functionalities like cipher, decipher, sign, and verify functions.
```javascript
const crypto = require('crypto');

const hash = crypto.createHash('sha256');
hash.update('some data to hash');
console.log(hash.digest('hex'));
```
## Express App and Server Folder Separation
Separating app and server folders benefits include easier testing, better coverage metrics, flexible deployment, and cleaner code.
```javascript
```
## Assert Module
The assert module provides functions for verifying invariants.
```javascript
const assert = require('assert');

assert.strictEqual(1, 1); // No error thrown
assert.strictEqual(1, 2); // Throws AssertionError
```
## Async_hooks Module
The async_hooks module provides an API to track asynchronous resources.
```javascript
const async_hooks = require('async_hooks');
const fs = require('fs');

const asyncHook = async_hooks.createHook({
  init(asyncId, type, triggerAsyncId, resource) {
    fs.writeSync(
      1,
      `Hook init: asyncId: ${asyncId}, type: ${type}, trigger: ${triggerAsyncId}\n`
    );
  },
  destroy(asyncId) {
    fs.writeSync(1, `Hook destroy: asyncId: ${asyncId}\n`);
  },
});

asyncHook.enable();

require('net').createServer().listen(8080, () => {
  setTimeout(() => {
    console.log('server running');
  }, 10);
});
```
## Buffer Objects
Buffer objects represent binary data in the form of a sequence of bytes.
```javascript
const buf = Buffer.alloc(10);
console.log(buf);
```
## Implementing Addons
Three options:
1. N-API
2. nan direct use of internal V8
3. libuv

## Spawning Child Processes
Use `child_process.spawn()` for asynchronous process spawning without blocking the event loop.

## Multi-core Systems
Use the cluster module to utilize multiple cores by creating child processes that share server ports.
```javascript
const cluster = require('cluster');
const http = require('http');
const numCPUs = require('os').cpus().length;

if (cluster.isMaster) {
  for (let i = 0; i < numCPUs; i++) {
    cluster.fork();
  }

  cluster.on('exit', (worker, code, signal) => {
    console.log(`Worker ${worker.process.pid} died`);
  });
} else {
  http.createServer((req, res) => {
    res.writeHead(200);
    res.end('Hello World\n');
  }).listen(8000);
}
```
## Console Data Type
The console is an object.

## Console Methods
Examples include:
- `console.clear()`
- `console.error([data][, ...args])`
- `console.table(tabularData[, properties])`
```javascript
console.table([{ name: 'Alice', age: 25 }, { name: 'Bob', age: 30 }]);
```
## Performing Cryptographic Functions
The crypto module provides cryptographic functionality. Use `require('crypto')` to access it.

## Reading and Writing Files
The fs module provides an API for interacting with the file system.
```javascript
const fs = require('fs');

// Reading a file
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});

// Writing to a file
fs.writeFile('file.txt', 'Hello World', (err) => {
  if (err) throw err;
  console.log('File has been saved!');
});
```
## Global Objects
Examples include `__dirname`, `__filename`, `console`, `exports`, `global`, `module`, `process`, `require()`, etc.
```javascript
console.log(__dirname);
console.log(__filename);
```
## Asynchronous Network API
The net module provides an API for creating stream-based TCP or IPC servers and clients.
```javascript
const net = require('net');

const server = net.createServer((socket) => {
  socket.write('Echo server\r\n');
  socket.pipe(socket);
});

server.listen(1337, '127.0.0.1');
```
## OS Module Utilities
The os module provides OS-related utility methods and properties.
```javascript
const os = require('os');

console.log('Platform:', os.platform());
console.log('CPU architecture:', os.arch());
console.log('Number of CPUs:', os.cpus().length);
console.log('Total memory:', os.totalmem());
```
## Suitable Use Cases for NodeJS
- I/O bound applications
- Data streaming applications
- Data-intensive real-time applications (DIRT)
- JSON API-based applications
- Single-page applications

## Unsuitable Use Cases for NodeJS
Not suitable for CPU-heavy applications.
## Key Features of NodeJS
- Asynchronous event-driven I/O
- Fast code execution with V8 engine
- Single-threaded but highly scalable
- JavaScript library usage
- Active community
- No buffering
```javascript
```
## REPL in NodeJS
The REPL (Read Eval Print Loop) is an environment for reading, evaluating, printing, and looping commands.
```bash
$ node
> const x = 10;
> x + 20
30
```
## CRUD Operations without Frameworks
CRUD operations can be performed using the inbuilt http library.
```javascript
const http = require('http');
const url = require('url');
const querystring = require('querystring');

const server = http.createServer((req, res) => {
  const parsedUrl = url.parse(req.url);
  const parsedQuery = querystring.parse(parsedUrl.query);

  if (req.method === 'GET' && parsedUrl.pathname === '/resource') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Read operation' }));
  } else if (req.method === 'POST' && parsedUrl.pathname === '/resource') {
    res.writeHead(201, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Create operation' }));
  } else if (req.method === 'PUT' && parsedUrl.pathname === '/resource') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Update operation' }));
  } else if (req.method === 'DELETE' && parsedUrl.pathname === '/resource') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Delete operation' }));
  } else {
    res.writeHead(404, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ message: 'Not Found' }));
  }
});

server.listen(3000, () => {
  console.log('Server is listening on port 3000');
});

```
## NodeJS vs AJAX vs jQuery
- Node.js: Server-side platform.
- AJAX: Client-side scripting for dynamic content.
- jQuery: JavaScript library for easier development.

## EventEmitter in NodeJS
The EventEmitter class allows creating and handling custom events.
```javascript
const EventEmitter = require('events');
class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter();
myEmitter.on('event', () => {
  console.log('An event occurred!');
});
myEmitter.emit('event');

```

ref: [📖 Node.JS interview guide](nodejs-inteview-guide.pdf)