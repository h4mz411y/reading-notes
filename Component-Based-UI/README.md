# Component Based UI

Component-based UI development encourages the team to design and develop components in a way that makes it easy for the website development company to reuse them in an efficient way. It becomes very easy for newbie developers or designers to understand the code. With a component-driven UI approach, components are documented well and shared with cross-teams, which helps them code faster and eliminate any possible delay. This way, the efficiency of the entire team is improved.

Not all the UX consulting services providers have a dedicated team of designers available to work only on the front-end portion. Many times, a developer is required to carry out the front-end design part. In such events, the component-driven UI approach greatly helps the developers. With the help of proper documentation, the design and development process becomes very easy for the small design consultancies. This, in the end, helps them scale their business without any hiccups.

* **A Simple Component**
React components implement a render() method that takes input data and returns what to display. This example uses an XML-like syntax called JSX. Input data that is passed into the component can be accessed by render() via this.props.

* **JSX** is optional and not required to use React. Try the Babel REPL to see the raw JavaScript code produced by the JSX compilation step.

* **A Stateful Component**
In addition to taking input data (accessed via this.props), a component can maintain internal state data (accessed via this.state). When a component’s state data changes, the rendered markup will be updated by re-invoking render().

* **An Application**
Using props and state, we can put together a small Todo application. This example uses state to track the current list of items as well as the text that the user has entered. Although event handlers appear to be rendered inline, they will be collected and implemented using event delegation.

* **A Component Using External Plugins**
React allows you to interface with other libraries and frameworks. This example uses remarkable, an external Markdown library, to convert the textarea value in real time.

## JSX 
JSX is an XML/HTML-like syntax used by React that extends ECMAScript so that XML/HTML-like text can co-exist with JavaScript/React code. The syntax is intended to be used by preprocessors (i.e., transpilers like Babel) to transform HTML-like text found in JavaScript files into standard JavaScript objects that a JavaScript engine will parse.

Basically, by using JSX you can write concise HTML/XML-like structures (e.g., DOM like tree structures) in the same file as you write JavaScript code, then Babel will transform these expressions into actual JavaScript code. Unlike the past, instead of putting JavaScript into HTML, JSX allows us to put HTML into JavaScript.

## Rendering an Element into the DOM

React element is the smallest renderable unit available in React. We can render such elements using the ReactDOM as described in the previous article. React elements are different from DOM elements as React elements are simple javascript objects and are efficient to create. React elements are the building blocks of any React app and should not be confused with React components which will be discussed in further articles.
Rendering an Element in React: In order to render any element into the Browser DOM, we need to have a container or root DOM element. It is almost a convention to have a div element with the id=”root” or id=”app” to be used as the root DOM element. Let’s suppose our index.html file has the following statement inside it.