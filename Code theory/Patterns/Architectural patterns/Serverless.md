# Serverless


## Pros
- It scales easily. The platform can spin up a new instance from a function if it is has a higher load than usual. 
- The usage of third-party platforms can reduce the cost of the development and operation. 
- A new function implementation and deployment are fairly easy so it is ideal for experimenting with new ideas. 

## Cons
- When you pick a vendor, you have to work together their constrains. (e.g.: a vendor might stop supporting a specific version of a framework that you are using)
- It can be hard to switch vendors. 
- It is tricky the manage the state in memory. e.gl: one instance stores the variable `X` with the value `1`. If we want to increase the value, we hardly can be sure that the increased value will be available in the next instances where we are connecting, for example from our mobile. 
- Cold start: The first invocation of a function takes longer because the platform must spin up a new container. Once it is running, however, the subsequent invocations perform better. 


## Backend as a service
You still have your own application with your own business logic but you use many third-party services for other concerns. These can be cloud services for [[Authentication|authentication]], logging, database or anything else. 

## Function as a service
It consists of multiple instances of code functions. These run in short live containers. These containers can contain any state because often, they live for just a few invocations. The containers are managed by a third-party vendor and often these functions integrate with many other services provided by that vendor (database, messaging system, logging system).
If the container receives an HTTP request, it will invoke for example the `main` fucntion that handles this request. This function can be a simple nodeJS function that receives an event object as parameter. 
