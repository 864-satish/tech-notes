### Simple Nodejs/expres Server with profiling
    Steps to Creating a simple NodeJs server

1. package.json

```JSON
{
  "name": "nodejs-inspect",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```
1. app.js
```javaScript
const express = require('express');
const app = express();
const memory = []; // creating object in global scope

app.get('/', function (req, res) {
    res.send('Server is up!');
});
app.get('/cpu-time', function (req, res) {
    const start = Date.now();
    wait();
    const end = Date.now();
    const timeTaken = end - start;
    res.send(`Time took: ${timeTaken} milliseconds.`);
});
app.get('/memory', function (req, res) {
    memory.lenght = 0;
    const start = process.memoryUsage().heapUsed / 1024 / 1024;
    createObject();
    const end = process.memoryUsage().heapUsed / 1024 / 1024;
    const used = end - start;
    res.send(`Aprox memory used: ${Math.round(used * 100) / 100} MB.`);
});
app.listen(3000, function () {
    console.log('Example app listening on port 3000!');
});
function wait(num) {
    for (let i = 0; i <= 10000; i++)
        for (let j = 0; j <= 10000; j++);
}
function createObject() {
    for (let i = 0; i <= 100000; i++)
        memory.push({ index: i });
}
```
Now, start your application using the following command:

```
node --inspect app.js
```
Your debugging tool will be available in google chrome

Open [chrome://inspect/#devices](chrome://inspect/#devices)

There we have multiple options
1. profiler
2. memory
3. snapshot comparision


Ref articles: 
1. [Node js profiling](https://medium.com/@pra4mesh/debugging-cpu-time-and-memory-allocation-of-your-nodejs-application-238af9cbe01d)
2. [Simple profiling](https://nodejs.org/en/docs/guides/simple-profiling)
3. [Node js debugging](https://nodejs.org/en/docs/guides/debugging-getting-started/)
