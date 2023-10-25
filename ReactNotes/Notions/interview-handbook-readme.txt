 
  1. ** What is Conditional Rendering? **

  means we can render many thing to the UI but on the basis of condition as if true render this part else
  render this part eg. showing loading... and error

  function App(props){
    const {loading , error ,Data} = props
    if(loading){
      return <div> Loading ...</div>
    }else{
      return <div>{Data}<div/>
    }
  }

  2. ** Explain how lists work in React? **
  means simple when we have data in state and we map over that data and show in div
  const [data,setData]=useState([])

  {data.map((ele)=>{
    return (
      <div key={ele.id}>
         <li>
            <ul>{ele.name}</ul>
         </li>
      </div>
    )
  })}

  3. ** what is virtual dom and how it works? **
  is the exact copy of real dom react has this functionality to use this virtual dom and eg counter
  when we increase the count the state gets updates from 0-1 so the virtual dom make the copy of that 
  on every change and then it compare it withe the previouse one and update the dom onny that parts 
  gets rerender not the whole dom this processes is called reconsilation


  4. React.memo()
  React.memo is a higher-order component (HOC) provided by React that can be used to memoize functional 
  components.

  import React from 'react';

const MyComponent = React.memo(({ prop1, prop2 }) => {
  return (
    <div>
      {prop1} - {prop2}
    </div>
  );
});

In the example above, MyComponent is wrapped with React.memo.
 This means that if the props prop1 and prop2 do not change, the component will not re-render.

 React.memo is typically used to optimize the rendering of functional components.
React.useMemo is used to optimize expensive computations or operations inside a component.

React.memo takes two parameters:

The component you want to memoize.
An optional function for customizing how props are compared. This function is typically named arePropsEqual.


6. What are the different ways to apply useEffect?

without dependency array
with empty dependency array
with dependency array and value inside this 
without cleanup function

7. ** How does Routing work with react? **
install react router dom 
wrap App inside the BrowserRouter
import {Routes,route} from 'react-router-dom"

<Routes>
   <Route path="/about" element={<About />} />
</Routes>

in Navber to navigate 
<Link to="/about">About</Link>


8.  What is SSR and CSR?
Server-Side Rendering (SSR):
SSR is a technique where the server generates the initial HTML content for a webpage and sends 
it to the client. This means that when a user requests a page, the server processes the request,
 fetches any necessary data, and then generates the full HTML content of the page

 Client-Side Rendering (CSR):
 CSR is a technique where the server sends a minimal HTML file to the client, which includes links to 
 JavaScript files. The client's browser then downloads and executes the JavaScript to render the page.

 9.  ** What are the lifecycle methods in class components? **

 import React from "react";

class Product extends React.Component {
    // Mounting Phase: constructor
    constructor() {
        super();
        this.state = {
            name: "Shampoo",
            price: 200,
            show: false
        };
        console.log('Constructor executed'); // Mounting Phase
    }

    render() {
        console.log('Render executed'); // Mounting Phase and Updating Phase
        return (
            <div>
                <h1>This is a product component.</h1>
                <h3>Name: {this.state.name}</h3>
                <h3>Price: {this.state.price}</h3>
            </div>
        );
    }
}

export default Product;


10. ** What is a pure component? **
A pure component in React is a class component that extends React.PureComponent instead of React.Component.
 It's a performance optimization feature provided by React.

 import React, { PureComponent } from 'react';

class PureExample extends PureComponent {
  render() {
    console.log('Render executed');
    return <div>{this.props.value}</div>;
  }
}

export default PureExample;

In this example, PureExample is a pure component. It automatically 
implements a shallow shouldComponentUpdate and will only re-render if the value prop changes.



11. ** How do you use Profiler? **
The React Profiler is a component that provides a way to measure the render performance of a React application. 
It helps you identify which parts of your application are causing performance bottlenecks.

import { Profiler } from 'react';

<Profiler id="myApp" onRender={callback}>
  {/* wrap Your application components */}
</Profiler>

function onRender(id, phase, actualDuration, baseDuration, startTime, commitTime, interactions) {
  console.log({
    id,
    phase,
    actualDuration,
    baseDuration,
    startTime,
    commitTime,
    interactions
  });
}


{
  id: "myApp",
  phase: "mount",
  actualDuration: 11.56ms,
  baseDuration: 10.34,
  startTime: 11234.12,
  commitTime: 11245.68,
  interactions: []
}

By using the Profiler, you can get insights into the rendering performance of
 your React application and identify areas that may need optimization.


12. ** Can you create a tree structure and explain how the state management will be designed for 
a game like tic tac toe? **

{
  board: [
    [null, null, null],
    [null, null, null],
    [null, null, null]
  ],
  currentPlayer: 'X',
  winner: null,
  isDraw: false,
  isGameOver: false
}


13. ** What are side effects? **

Making Network Requests: Sending HTTP requests to a server and receiving responses is a side effect
 because it involves an interaction with an external system.

Modifying State in a Redux Store: In Redux or similar state management systems, actions
 dispatched to the store that cause a state change are considered side effects.

Console Logging: Logging information to the console is a side effect because it's 
an interaction with the environment.

Using setTimeout or setInterval: These functions cause delays or repeated execution, which are side effects.

14. ** What are thunks? Why do you need them? **

Thunks are a way to handle asynchronous actions in Redux. They are functions that allow you to
 delay the dispatch of an action, or to dispatch only if certain conditions are met.
How Thunks Work:
Thunk Middleware:To use thunks in Redux, you need to apply the thunk middleware.
 This middleware intercepts action dispatches and handles functions (thunks) in addition
  to regular action objects.

import thunk from 'redux-thunk';
import { createStore, applyMiddleware } from 'redux';
import rootReducer from './reducers';

const store = createStore(rootReducer, applyMiddleware(thunk));

The most popular middleware for this purpose is redux-thunk.

15.** What does lazy loading mean? **
Lazy loading is a valuable technique for optimizing web performance, particularly for 
content-rich websites and applications.
Images:
In lazy loading of images, the images that are not immediately visible in the viewport 
are not loaded when the page first loads. Instead, a placeholder (like a small, low-resolution
 version of the image or a loading spinner) is displayed. When the user scrolls down and the
  image becomes visible in the viewport, then it is loaded.

 16. ** Can you write react without jsx? **
  yes 
  import React from 'react';

class MyComponent extends React.Component {
  render() {
     return React.createElement('div', null,
      React.createElement('h1', null, 'Hello, World!'),
      React.createElement('p', null, 'This is a React component without JSX.')
    );
  }
}

export default MyComponent;


JSX syntax

import React from 'react';

class MyComponent extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, World!</h1>
        <p>This is a React component with JSX.</p>
      </div>
    );
  }
}

export default MyComponent;


16. ** What are pure functions? **
 A pure function, given the same input, will always return the same output. 
 It doesn't rely on external state or data that can change over time.
 No Side Effects: A pure function doesn't modify any data outside its scope 
 (e.g., it doesn't change global variables or mutate its input arguments).
  It only operates on its input and returns a new value.

  function add(a, b) {
  return a + b;
}
This function is pure because it always returns the same result for the same inputs, 
and it doesn't have any side effects.

let total = 0;

function impureAdd(a) {
  total += a;
  return total;
}

The impureAdd function is not pure because it modifies the total variable outside its scope.
 It also doesn't always return the same output for the same input due to the changing state of total.


 17. ** Why do we spread the state or return a new object in reducers? **
Certainly! In a Redux reducer, we return a new object (using {}) to ensure that we're not 
directly modifying the existing state.
 return {
  ...state,
  counter: state.counter + 1
};

{} creates a new object. This is like giving birth to a brand new state.

...state spreads out all the properties from the existing state into the new object. 
It's like making a copy of the current state.

counter: state.counter + 1 sets the counter property in the new object to the updated value.
 This is the specific change we're making.


18. ** ** 
In Redux, dispatchers take only actions that are plain JavaScript objects because it enforces a clear
 and structured way of communicating intentions to change the state of the application. 


 19. ** What happens when you pass a function into a dispatcher? **
 store.dispatch(() => {
  console.log('This is a function being dispatched');
});

In this case, without any middleware to handle functions, you will likely encounter an error.
 Redux's dispatcher expects to receive plain action objects, not functions.
 
 If you're using middleware like Redux Thunk, passing a function into the dispatcher is allowed.
  Redux Thunk intercepts the action before it reaches the reducer. If the action is a function,
   Redux Thunk will execute it.


   20. ** Can you write your own middleware instead of thunks? **

   const loggingMiddleware = store => next => action => {
  // Log information about the action
  console.log(`Action Type: ${action.type}`);

  if (action.payload) {
    console.log(`Payload:`, action.payload);
  }

  // Pass the action to the next middleware or the reducer
  return next(action);
};

export default loggingMiddleware;

const store = createStore(rootReducer, applyMiddleware(loggingMiddleware));

21. ** What is useSelector and useDispatch? **
import {useSelector,useDispatch} from 'react-redux'

 const {isAuth}=useSelector((store)=>store.authReducer)
   console.log('auth',isAuth)

   useSelector is a hook provided by the React-Redux library, which is commonly used with 
   Redux to extract and select slices of state from the Redux store

 const dispatch=useDispatch()

 const handleIncrement = () => {
    dispatch({ type: 'INCREMENT_COUNTER' });
  };

  useDispatch is particularly useful when you want to trigger actions directly from a functional 
  component without needing to pass down action creators through props.

22. ** What is the use of Provider? **

import {Provider} from 'react-redux'
   <Provider store={store}>
      <App />
    </Provider>

 The Provider is a component provided by the React-Redux library that allows you to make
  the Redux store available to the entire React application. It's a higher-order component 
  that wraps around your root component to ensure that all components within the application 
  can access the Redux store .  