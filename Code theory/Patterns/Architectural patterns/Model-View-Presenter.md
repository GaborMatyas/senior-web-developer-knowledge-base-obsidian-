# Model-View-Presenter


This is an evolution or variation of the [[Model-View-Controller]] pattern.
The MVP pattern is a great pattern for desktop applications.
The three important components: ![[model-view-presenter.png]]
## Pros
These are the same just like in the [[Model-View-Controller#Pros|MVC]].

## Cons
- Presenters can become bloated just like Controller in the [[Model-View-Controller#Pros|MVC]].
- This is/was a good pattern for Desktop applications, but less popular nowadays because the [[Model View View Model (MVVM)]] pattern can be a more powerful solution for desktop apps. 

## Model


## View
The user interacts with the view which passes on commands or events to the presenter. 


## Presenter
After the input passes on a command or an event to hee presenter then it  manipulates the model and tells the view which data to display where.


## There are two variations of the MVP
### Passive view
If all the UI logic is in the presenter and the view has no notion of the model.

### Supervising controller
On the other hand, the UI could contain all the necessary details on how to render the model and we would use the presenter for more complex logic. This is more common these days because the current state of UI technology and markup languages allow us to put quite a bit of logic in the UI. 