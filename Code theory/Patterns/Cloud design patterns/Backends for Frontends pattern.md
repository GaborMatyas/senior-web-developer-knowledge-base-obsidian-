# Backends for Frontends pattern


Create separate backend services to be consumed by specific frontend applications or interfaces. 

Maybe we have ONE Backend that can be Azure, AWS Lambda, etc.... it is connected to a web client frontend and a mobile native app. The two connected applications want to use different dataset segments from the same pool. One should handle all user information, and the other needs only a segment from the same information. If we change the sets of data on the different platforms, it could be harmful and impactful if we wanna use only one backend. 
This is the problem, that can be solved with BFF pattern. 

We can create a backend for desktop apps, and another one for mobile apps. We implement the Backend for desktop to return back the full information set of a user because the frontend needs it, and the backend for mobile native app will return a limited amount of data about the user, because the mobile app does not need everything. 
If we want to change the behavior of one of them, it does not impact the other one. 

If there is a service that is the same on both platforms, this service should be extracted into a separate service and used as a common point for the backends. 

The client specific logic should be in the backends, the business logic should be in the outer, separated, common service. 

If all of the frontends need the same amount of information and logic, there is no point to implement multiple backends, instead a single one can be used. 

The code duplication should be concerned, if multiple backend entities are created. 

Do not use this pattern when:
- you have only one platform, e.g.: mobile native app
- when all the frontend needs the same data and makes the same requests for the backend (it can be manageable with only one backend)


Related Patterns:
- [[Gateway Aggregation pattern]]
- [[Gateway Offloading pattern]]
- [[Gateway Routing pattern]]