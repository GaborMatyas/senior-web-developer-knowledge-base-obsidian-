# Browser-side
It was invented originaly to change the content dynamically on a webpage.  

## What CAN do 
1. Manipulate the HTML code, CSS
1. Send background HTTP requests and much more

## What can NOT do in browser-side
1. Can not reach the local filesystem
1. Interact with the operating system

## [[Embed Javascript to HTML]]

## Browser APIs
These are the communication bridges between JavaScript and C++ Logic built into the Browser. 


## Event loop
This is not part of the JavaScript engine but of modern Browsers like Google Chrome and helps us with asyncronous code. (with event listeners, like click listeners).
Even when the call stack is empty and all syncronous code is done, the event listeners still need to be alive and active to respond user actions, like button clicks. 

The event loop pings the Javascript engine whenever a new event is being fired. 