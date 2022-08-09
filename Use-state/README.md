# HOOKS


### What are Hooks in Reactjs?
Hooks are functions that let you “hook into” React state and lifecycle features from function components. Hooks don't work inside classes — they let you use React without classes.


With Hooks, you can extract stateful logic from a component so it can be tested independently and reused. Hooks allow you to reuse stateful logic without changing your component hierarchy. This makes it easy to share Hooks among many components or with the community.

Hooks make React so much better because you have simpler code that implements similar functionalities faster and more effectively.

## State Hook

In a class, by setting this.state to { age: 0 } in the constructor, we initialize the age state to 0.

```js
class Sample extends React.Component {
  constructor(props) {
    super(props);
   this.state = {
     age: 0
   };
 }
```

Since we are not using this.state inside the functional component, we have to call the useState hook directly through our functional component.


```js
import React, { useState } from 'react';
function Sample() {
  // Initialize a new state variable called  "age"
  const [age, setAge] = useState(0);
```

Here we have introduced a new way to use the useState Hook from React.

UseState to be using the same functionality given in a class by this.state. This enables to maintain a local state in a functional component.

Here, in this case, the state does not have to be an entity, unlike classes. Hence we can hold a number or a string.

For example, If we wanted to store two different state values, we have to call the useState() twice.

According to the given scenario, we’ll call setAge with a new value when the user clicks. Instead of using this.setState and this.state.age, we can simply set a new value using the setAge function and add 1 to the current age value.

Then React will re-render the Sample component, passing the new age value to it.