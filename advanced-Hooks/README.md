# Using a State Reducer with Hooks

* End user does an action
* Dev calls dispatch
* Hook determines the necessary changes
* Hook calls dev's code for further changes 👈 this is the inversion of control part
* Hook makes the state changes
Links to an external site.
```js
function useToggle() {
  const [on, setOnState] = React.useState(false)

  const toggle = () => setOnState(o => !o)
  const setOn = () => setOnState(true)
  const setOff = () => setOnState(false)

  return {on, toggle, setOn, setOff}
}

function Toggle() {
  const {on, toggle, setOn, setOff} = useToggle()

  return (
    <div>
      <button onClick={setOff}>Switch Off</button>
      <button onClick={setOn}>Switch On</button>
      <Switch on={on} onClick={toggle} />
    </div>
  )
}

function App() {
  return <Toggle />
}

ReactDOM.render(<App />, document.getElementById('root'))
Now, let's say we wanted to adjust the <Toggle /> component so the user couldn't click the <Switch /> more than 4 times in a row unless they click a "Reset" button:

function Toggle() {
  const [clicksSinceReset, setClicksSinceReset] = React.useState(0)
  const tooManyClicks = clicksSinceReset >= 4

  const {on, toggle, setOn, setOff} = useToggle()

  function handleClick() {
    toggle()
    setClicksSinceReset(count => count + 1)
  }

  return (
    <div>
      <button onClick={setOff}>Switch Off</button>
      <button onClick={setOn}>Switch On</button>
      <Switch on={on} onClick={handleClick} />
      {tooManyClicks ? (
        <button onClick={() => setClicksSinceReset(0)}>Reset</button>
      ) : null}
    </div>
  )
}
```
Links to an external site.Cool, so an easy solution to this problem would be to add an if statement in the handleClick function and not call toggle if tooManyClicks is true, but let's keep going for the purposes of this example.
How could we change the useToggle hook, to invert control in this situation? Let's think about the API first, then the implementation second. As a user, it'd be cool if I could hook into every state update before it actually happens and modify it, like so:

```js
function Toggle() {
  const [clicksSinceReset, setClicksSinceReset] = React.useState(0)
  const tooManyClicks = clicksSinceReset >= 4

  const {on, toggle, setOn, setOff} = useToggle({
    modifyStateChange(currentState, changes) {
      if (tooManyClicks) {
        // other changes are fine, but on needs to be unchanged
        return {...changes, on: currentState.on}
      } else {
        // the changes are fine
        return changes
      }
    },
  })

  function handleClick() {
    toggle()
    setClicksSinceReset(count => count + 1)
  }

  return (
    <div>
      <button onClick={setOff}>Switch Off</button>
      <button onClick={setOn}>Switch On</button>
      <Switch on={on} onClick={handleClick} />
      {tooManyClicks ? (
        <button onClick={() => setClicksSinceReset(0)}>Reset</button>
      ) : null}
    </div>
  )
}
```
So that's great, except it prevents changes from happening when people click the "Switch Off" or "Switch On" buttons, and we only want to prevent the from toggling the state.

Hmmm... What if we change modifyStateChange to be called reducer and it accepts an action as the second argument? Then the action could have a type that determines what type of change is happening, and we could get the changes from the toggleReducer which would be exported by our useToggle hook. We'll just say that the type for clicking the switch is TOGGLE.
```js
function Toggle() { const [clicksSinceReset, setClicksSinceReset] = React.useState(0) const tooManyClicks = clicksSinceReset >= 4

const {on, toggle, setOn, setOff} = useToggle({ reducer(currentState, action) { const changes = toggleReducer(currentState, action) if (tooManyClicks && action.type === 'TOGGLE') { // other changes are fine, but on needs to be unchanged return {...changes, on: currentState.on} } else { // the changes are fine return changes } }, })

function handleClick() { toggle() setClicksSinceReset(count => count + 1) }

return (

Switch Off Switch On {tooManyClicks ? ( <button onClick={() => setClicksSinceReset(0)}>Reset ) : null}
) }

```
Nice! This gives us all kinds of control. One last thing, let's not bother with the string 'TOGGLE' for the type. Instead we'll have an object of all the change types that people can reference instead. This'll help avoid typos and improve editor autocompletion (for folks not using TypeScript):
 
```js
function Toggle() { const [clicksSinceReset, setClicksSinceReset] = React.useState(0) const tooManyClicks = clicksSinceReset >= 4

const {on, toggle, setOn, setOff} = useToggle({ reducer(currentState, action) { const changes = toggleReducer(currenState, action) if (tooManyClicks && action.type === actionTypes.toggle) { // other changes are fine, but on needs to be unchanged return {...changes, on: currentState.on} } else { // the changes are fine return changes } }, })

function handleClick() { toggle() setClicksSinceReset(count => count + 1) }

return (

Switch Off Switch On {tooManyClicks ? ( <button onClick={() => setClicksSinceReset(0)}>Reset ) : null}
) }

```
