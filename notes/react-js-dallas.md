#### April 12, 2016 : : Call-Em-All
- - - - - - - - - -

7:35

- FP / ES6
  - "body shaming for arrow functions"
  - =>
  - `const add = x => y => x + y`
- Destructuring
  - const { x } = obj
  - const x = obj.x
- Map does not mutate the original array, returns a new array
- Reduce
  - (accum, val) => accum
  - `[1,2,3].reduce(x,y) => x + y  // 6`
- Immutability
  - ImmutableJS
  - Structural sharing of each object
  - `const x = { greeting: 'hi' }`
  - `x.greeting = 'hi' // bad`
  - `Object.assign({}, x, { greeting: 'hi' }) // good`
- Speed: maximize for developer time
- "Simple Made Easy" video, Rich Hickey
- use Transducers (Ramda)
  - always 1-to-1


- - - - - - - - -

- setState
  - this.state === getInitialState
- this.refs isn't used as much anymore -- go _controlled_


```js
export default App extends Component {

  constructor(props) {
    super(props)
    this.state = {
      text: 'hello',
      todos: []
    }

    handleChange = ({ target: { value } }) => {
      this.setState({ text: value})
    }

    onEnter = ({ keyCode}) => {
      if (keyCode === 13 && this.state.text ) {
        this.setState(
          { todos: [...this.state.todos, this.state.text],
            text: ''
          }, () => {
            console.log(this.state.todos)
          }
        )
      }
    }

    render() {
      return (
        <div>
          <div>TODOS</div>
          <TextField
            value={this.state.text}
            onInput={this.handleChange
            onKeyDown={this.onEnter}}
          />
          <ul>
            {this.state.todos.map(todo => <li>{todo}</li>)}
          </ul>
        </div>
      )
    }
  }
}

```

REDUX
- it's okay to use stateless components, if you're using 'connect' (sp?) -- gives you shouldComponentUpdate for free via wrapping presentational components.
- mapStateToProps
- mapDispatchToProps
- Point: keeping all state in a tree which we dispatch actions on and push props down to presentation layer.
- `export default connect(mapStateToProps, mapDispatchToProps)(App)`
- At all different from a container?
- flux pattern
- type & payload -> reducer

```js
// actions.js
import constants from './constants'

export const handleTextFieldInput = input => {
  return {
    type: HANDLE_TEXT_FIELD_INPUT
    payload:
  }
}

export const createNewTodo = () => {
  return {
    type: CREATE_NEW_TODO
    payload:
  }
}

export const handleTodoClick = input => {
  return {
    type: HANDLE_TODO_CLICK
    payload:
  }
}

```
- "none of this is really boilerplate"
- the cruft came from flux implementations
- many went out of business after Redux landed

```js
// constants.js

export const HANDLE_TEXT_FIELD_INPUT = 'HANDLE_TEXT_FIELD_INPUT'
export const CREATE_NEW_TODO = 'CREATE_NEW_TODO'
export const HANDLE_TODO_CLICK = 'HANDLE_TODO_CLICK'

```

```js
// reducer.js

const initialState ={
  text: '',
  todos: []
}

export const todoReducer(state = initialState, { type, payload }) {
  switch (type) {
    case 'HANDLE_TEXT_FIELD_INPUT'
      return {
        ...state,
        text: payload
      }
    case 'CREATE_NEW_TODO'
      return {
        text: '',
        todos: [...state.todos, state.text ]
      }
    case 'HANDLE_TODO_CLICK'
      return state
    default
      return state
  }
}



```
- the callback function that is returned to reduce
- "reducing over entire state to make changes"


- Immutable.js
- Tries
- Shared structure, saves reference to old object structure, creates a new lookup underneath it
- functional paradigm around the library / API
-
