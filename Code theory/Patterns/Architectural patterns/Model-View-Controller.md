# Model-View-Controller (MVC)


## Pros
- It has a great separation of concerns, all pieces have well defined responsibilities. 
- It can be developed in parallel. One developer can write the UI part(view) and another the model. 
- Popular in web frameworks. 

## Cons
- Controllers can become bloated...e.g.: with caching, input validation, business logic....to fix this issue we can extract caching for example to a different layer and add some business logic to the model itself. 


## Model
The model is where the data of the application is managed. It receives input from the controller. 

## Controller:
It receives user input and communicates this to the model in such a way, that the model can understand it. E.g.: middlewares in express.js, routes

## View
It is responsible for presenting the model to the user. 