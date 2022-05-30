# NodeJS


## What is NodeJs?
It allows you to run Javascript code on the server or on anz machine. This is a Javascript runtime so we can run the code outside of the browser. 

[[server-side|What NodeJs can and can not do]]

The V8 engines compiles JS code to machine code. It adds features to Javascript that are not available in the browser, for example it can reach the file system. 

## Web server
When the script has started, parsed the code, the functions and variables have been registered...the [[browser-side#Event loop|Event loop]] keeps on running as long as there are event listeners registered. Such a listener is the listen function of an instentiated node.js server. For example the `process.exit()` function can terminate the application. 

When the `fs` module is used to reach the file system, e.g.: the writeFile function is not handled by the event loop, only the callback that should be run once an error or a completed task event is fired. 
Such an expensive function like writeFile is sent to the Worker Pool, that is also be managed by NodeJS. 

## Worker Pool
It is responsible for all the heavy lifting. Almost completly detached from the Javascript code. It runs on different Threads. Once a worker is done, it will trigger the callback for the file operation for example. 

- [[Exports in NodeJs]]
- [[Different Module Formats]]