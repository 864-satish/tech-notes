## Memory leaks in NodeJs: causes and way ahead
### Types of memoery leaks
1. Javascript leaks
2. Native leaks
3. System level leaks
4. V8 Garbage collector itsesf is leaking memory

Common practices to avoid javascript memory leaks
1. Always clear Event emmiters 
    ```javaScript
    const listenerToRemove = (data) => {
        console.log('This listener will be removed');
    };
    myEmitter.on('specific_event', listenerToRemove);

    // To remove the listener:
    myEmitter.removeListener('specific_event', listenerToRemove);
    ```

2. Always clear timers [e.g setTimeout]
    ```javaScript
    const timeoutId = setTimeout(() => {
    console.log("This will be cleared!");
    }, 3000);

    // Clear the timer after 1 second
    clearTimeout(timeoutId, 1000);
    ```
3. Never define Global variables
4. Check for Looping references or recursive links

ref: [YouTube: Node offial memeory leak talk](https://www.youtube.com/watch?v=hliOMEQRqf8)


### Tools and commands to debug memory leak

- Using garbage collector
    ```node --gc_trace node app.js```

- Node js inpector 
    - ```node --inspect app.js```
    - ```NODE_OPTIONS="--inspect" node app.js```

- Using node inspector [3rd party]
    commands available
    ```bash
    node-inspect -v
    node-inspect app.js
    node --inspect-brk app.js
    ```
    for TypeScript
    ```node --inspect-brk -r ts-node/register app.ts```

- Using google chrome dev tools
    open chrome://inspect avaialbel tools
    - memeory snapshot comparison
    - profiling

    NOTE: Both inpector available in chrome dedicated node js dev 
    ```chrome://inspect```
- Using pm2 instances [few comands]
    ```bash
    npx pm2 app.js
    npx pm2 monit
    npx pm2 status
    npx pm2 stop
    ```


### Load / ab testing node applicatioon
#### Using apache benchmark: ab
- Avaialble comand
    ```
    load test: ab -k -c200 -10000000 http://localhost:8080/ 
    ```
    Flags refrence
    - -k : keep alive
    - -c : set  concurrency [200 request simultaneously]
    - -n10000000: Set request load [10 million request will be made]


### Module avaialble for debugging memeory leaks
1. memeoryUsage

    e.g 
    ```javascript
    const numeral  = require('numeral);

    setInterval(() => {
        const {rss, heapTotal} = process.memeoryUsage();
        console.log(
            'rss', numeral(rss).format('0.0.ib)),
            'heapTotal',  numeral.(heapTotal).format('0.0.ib')
        );
    }, 5000)
    //rss:  resident set size
    //heapTotal = total space avaialble for Javascript object external or heap used
    ```
2. heapsnaphot (node --inspec)
3. heapDump
4. heap-profile (Okay  production)
5. llmd (Low level memeory debugging)

Ref video: [Debugging Node.js in Production](https://www.youtube.com/watch?v=O1YP8QP9gLA)