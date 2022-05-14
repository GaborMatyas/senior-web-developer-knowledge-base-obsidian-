# Model View View Model (MVVM)


The Model-View-ViewModel pattern or MVVM is a pattern that works well when you have advanced data binding support. In MVVM, we have three separated components, the Model, the View, and a ViewModel in between.

The MVVM pattern is a great pattern for desktop applications and mobile applications if your platform supports the necessary data binding techniques. With MVVM just like Model-View-presenter, you can achieve a clean separation of concerns, which also makes the application easier to test. MVVM is a powerful pattern, but it can be overkill for some simple applications. The data binding is also harder to debug. If some piece of data binding doesn't work, you'll have more difficulty figuring out what is wrong exactly. And finally, just like the [[Model-View-Presenter]] pattern, desktop applications are often being replaced with web applications using web technology.

## Model
The Model contains our business logic and data, and the ViewModel interacts with it. 

## View
The special part is that we connect the View to the ViewModel by using advanced data binding techniques. This allows us to write a lot less code. The last step is that the user interacts with the View. Thanks to two way data binding, the user's interactions are passed on to the ViewModel, and any updates in the ViewModel are seamlessly passed back to the View. 

## ViewModel


