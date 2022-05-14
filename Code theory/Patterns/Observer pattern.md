# Observer pattern

*'The _Observer_ pattern offers a subscription model in which objects subscribe to an event and get notified when the event occurs. This pattern is the cornerstone of event driven programming, including JavaScript. The Observer pattern facilitates good object-oriented design and promotes loose coupling.'*

If a subscriber should know ones the observable is changed. 
This pattern moves from the Poll architecture to a Pull architecture. 

Poll: Ask the observed object, whether its state has changed.
Pull: The observed object pushes the data when it has changed. Whenever a change has happened, its responsibility to push the changed data to all of its observers. 

The essence of this, is that the Observable should know its Observers/Subscribers. 
It is one to many relationship/dependency. (1 observable - many observers)

When building web apps you end up writing many event handlers. Event handlers are functions that will be notified when a certain event fires. These notifications optionally receive an event argument with details about the event (for example the x and y position of the mouse at a click event).

The event and event-handler paradigm in JavaScript is the manifestation of the Observer design pattern. Another name for the Observer pattern is Pub/Sub, short for Publication/Subscription.

The `Click` object represents the Subject. The `clickHandler` function is the subscribing Observer. This handler subscribes, unsubscribes, and then subscribes itself while events are firing. It gets notified only of events #1 and #3.

Notice that the `fire` method accepts two arguments. The first one has details about the event and the second one is the context, that is, the `this` value for when the eventhandlers are called. If no context is provided `this` will be bound to the global object (window).
```js
function Click() {
    this.handlers = [];  // observers
}

Click.prototype = {

    subscribe: function (fn) {
        this.handlers.push(fn);
    },

    unsubscribe: function (fn) {
        this.handlers = this.handlers.filter(
            function (item) {
                if (item !== fn) {
                    return item;
                }
            }
        );
    },

    fire: function (o, thisObj) {
        var scope = thisObj || window;
        this.handlers.forEach(function (item) {
            item.call(scope, o);
        });
    }
}

function run() {

    var clickHandler = function (item) {
        console.log("fired: " + item);
    };

    var click = new Click();

    click.subscribe(clickHandler);
    click.fire('event #1');
    click.unsubscribe(clickHandler);
    click.fire('event #2');
    click.subscribe(clickHandler);
    click.fire('event #3');
}
```