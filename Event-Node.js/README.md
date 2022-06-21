# Event-Driven Programming in Node.js

* Node.js makes extensive use of events which is one of the reasons behind its speed when compared to other similar technologies. Once we start a Node.js server, it initializes the variables and functions and then listens for the occurrence of an event.

* Event-driven programming is used to synchronize the occurrence of multiple events and to make the program as simple as possible. The basic components of an Event-Driven Program are:

* A callback function ( called an event handler) is called when an event is triggered.
An event loop that listens for event triggers and calls the corresponding event handler for that event.
A function that listens for the triggering of an event is said to be an ‘Observer’. It gets triggered when an event occurs. Node.js provides a range of events that are already in-built. These ‘events’ can be accessed via the ‘events’ module and the EventEmitter class. Most of the in-built modules of Node.js inherit from the EventEmitter class

* **EventEmitter**: The EventEmitter is a Node module that allows objects to communicate with one another. The core of Node’s asynchronous event-driven architecture is EventEmitter. Many of Node’s built-in modules inherit from EventEmitter.

* The idea is simple – emitter objects send out named events, which trigger listeners that have already been registered. Hence, an emitter object has two key characteristics:

* **Emitting name events:** The signal that something has happened is called emitting an event. A status change in the emitting object is often the cause of this condition.
Registering and unregistering listener functions: It refers to the binding and unbinding of the callback functions with their corresponding events.
Event-Driven Programming Principles:

* A suite of functions for handling the events. These can be either blocking or non-blocking, depending on the implementation.
Binding registered functions to events.
When a registered event is received, an event loop polls for new events and calls the matching event handler(s).