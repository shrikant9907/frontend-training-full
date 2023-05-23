### Day 1: Introduction to React.js

What is React.js?

React.js is a JavaScript library for building user interfaces. It allows developers to create reusable UI components and efficiently update and render those components as the underlying data changes. React.js follows a component-based approach, where the UI is divided into modular components that can be easily composed together.
Setting up a development environment (Node.js, npm, create-react-app)

Install Node.js and npm to manage dependencies.
Use the create-react-app tool to quickly set up a new React.js project with the necessary configuration and folder structure.
React components and JSX syntax

Learn about React components, which are the building blocks of a React application.
Understand JSX, a syntax extension for JavaScript that allows you to write HTML-like code within your JavaScript code.
Rendering elements

Explore how to render React elements to the DOM.
Use ReactDOM.render() to render a React component to a specified container element.
Example Code:
```js
import React from 'react';
import ReactDOM from 'react-dom';

const App = () => {
  return <h1>Hello, React!</h1>;
};

ReactDOM.render(<App />, document.getElementById('root'));
```

### Day 2: Components and Props

Functional components vs. class components

Understand the difference between functional components and class components in React.
Functional components are simple functions that return JSX, while class components are JavaScript classes that extend the React.Component class.
Props: passing data to components

Learn how to pass data from a parent component to a child component using props.
Props are read-only and allow you to customize the behavior or appearance of a component.
Component composition and reusability

Explore how to compose React components by nesting them within other components.
Reusable components help maintain a modular and scalable codebase.
Example Code:
```js
import React from 'react';

const Greeting = (props) => {
  return <h1>Hello, {props.name}!</h1>;
};

const App = () => {
  return (
    <div>
      <Greeting name="John" />
      <Greeting name="Jane" />
    </div>
  );
};
```

### Day 3: State and Lifecycle

State and its importance in React

Understand the concept of state in React.
State represents the mutable data within a component and is used to manage component behavior and reactivity.
Class component state and setState method

Learn how to define and update state in a class component.
Use the setState() method to update the state and trigger a re-render of the component.
Lifecycle methods (componentDidMount, componentDidUpdate, componentWillUnmount)

Explore the lifecycle methods available in React class components.
componentDidMount is called after the component is rendered for the first time, componentDidUpdate is called after a component's update, and componentWillUnmount is called before a component is removed from the DOM.
Example Code:
```js
import React, { Component } from 'react';

class Timer extends Component {
  constructor(props) {
    super(props);
    this.state = { seconds: 0 };
  }

  componentDidMount() {
    this.timerId = setInterval(() => {
      this.setState((prevState) => ({
        seconds: prevState.seconds + 1,
      }));
    }, 1000);
  }

  componentWillUnmount() {
    clearInterval(this.timerId);
  }

  render() {
    return <div>Seconds: {this.state.seconds}</div>;
  }
}
```

### Day 4: Handling Events

Event handling in React

Learn how to handle events in React components.
React uses synthetic events that wrap the native browser events and provide a consistent interface across different browsers.
Binding event handlers

Understand the importance of binding event handlers in React.
Ensure that the correct value of 'this' is maintained when the event handler is called.
State updates through event handlers

Update component state based on user interactions within event handlers.
Modify the state using this.setState() to trigger a re-render and reflect the updated state in the UI.
Example Code:
```js
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  incrementCount() {
    this.setState((prevState) => ({ count: prevState.count + 1 }));
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.incrementCount()}>Increment</button>
      </div>
    );
  }
}
```

### Day 5: Conditional Rendering

Conditional rendering in React
Explanation: Introduce conditional rendering techniques in React to conditionally display components or elements based on certain conditions.
The ternary operator and logical && operator for conditional rendering
Explanation: Discuss how to use the ternary operator (? :) and logical && operator to conditionally render elements or components.
Example Code:
```js
import React from 'react';

const Greeting = (props) => {
  return (
    <div>
      {props.isLoggedIn ? (
        <h1>Welcome back, {props.name}!</h1>
      ) : (
        <h1>Please log in.</h1>
      )}
    </div>
  );
};

const App = () => {
  const user = {
    name: 'John',
    isLoggedIn: true,
  };

  return <Greeting name={user.name} isLoggedIn={user.isLoggedIn} />;
};
```
Description: In this example, the Greeting component conditionally renders different greetings based on the isLoggedIn prop value. If isLoggedIn is true, it displays a welcome message with the user's name. Otherwise, it displays a message prompting the user to log in.

### Day 6: Lists and Keys
Rendering lists in React
Explanation: Discuss how to render dynamic lists of items in React using arrays and the map method.

The concept of keys in React and their importance
Explanation: Explain the importance of using unique keys when rendering lists in React to help React identify and efficiently update list items.

Example Code:
```js
import React from 'react';

const TodoList = (props) => {
  const todos = props.todos.map((todo) => <li key={todo.id}>{todo.text}</li>);

  return <ul>{todos}</ul>;
};

const App = () => {
  const todos = [
    { id: 1, text: 'Buy groceries' },
    { id: 2, text: 'Clean the house' },
    { id: 3, text: 'Walk the dog' },
  ];

  return <TodoList todos={todos} />;
};
```
Description: In this example, we have an array of todos containing objects with an id and text property. The TodoList component uses the map method to iterate over the todos array and render a list of <li> elements with the corresponding text. Each list item has a unique key assigned to it, which helps React efficiently update the list when changes occur.

### Day 7: Forms in React

Handling forms in React
Explanation: Discuss how to handle form inputs and manage their state in React, including capturing user input and updating component state accordingly.
Controlled components and uncontrolled components
Explanation: Explain the concepts of controlled components (where form inputs are controlled by React state) and uncontrolled components (where form inputs are handled by the DOM).
Example Code:
```js
import React, { useState } from 'react';

const LoginForm = () => {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Submitted:', username, password);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
        placeholder="Username"
      />
      <input
        type="password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
        placeholder="Password"
      />
      <button type="submit">Login</button>
    </form>
  );
};

const App = () => {
  return <LoginForm />;
};
```
Description: In this example, the LoginForm component manages the state of username and password using the useState hook. The form inputs are controlled components, where their values are tied to the component state. The handleSubmit function is called when the form is submitted, preventing the default form submission behavior and logging the entered username and password to the console.

### Day 8: Styling in React

Styling options in React (inline styles, CSS classes, CSS-in-JS libraries)
Explanation: Discuss various approaches for styling React components, including inline styles, applying CSS classes, and using CSS-in-JS libraries like styled-components or emotion.
Conditional styling based on state or props
Explanation: Explain how to conditionally apply styles to components based on their state or props, allowing dynamic styling in React.
Example Code:
```js
import React from 'react';

const Button = (props) => {
  const buttonStyles = {
    backgroundColor: props.primary ? 'blue' : 'gray',
    color: 'white',
    padding: '10px 20px',
    borderRadius: '5px',
  };

  return (
    <button style={buttonStyles}>
      {props.primary ? 'Primary Button' : 'Secondary Button'}
    </button>
  );
};

const App = () => {
  return (
    <div>
      <Button primary />
      <Button />
    </div>
  );
};
```
Description: In this example, the Button component uses inline styles to conditionally apply different styles based on the primary prop. If primary is true, the button will have a blue background and display "Primary Button". Otherwise, it will have a gray background and display "Secondary Button".

### Day 9: React Router

Introduction to React Router
Explanation: Introduce React Router as a popular library for handling routing and navigation in React applications.
Setting up routes and rendering components
Explanation: Discuss how to set up routes in React Router and render the appropriate components based on the URL.
Navigation between routes using links and programmatic navigation
Explanation: Explain how to create links using the <Link> component and perform programmatic navigation using the history object or hooks like useHistory.
Example Code:
```js
import React from 'react';
import { BrowserRouter as Router, Switch, Route, Link } from 'react-router-dom';

const Home = () => {
  return <h1>Home Page</h1>;
};

const About = () => {
  return <h1>About Page</h1>;
};

const App = () => {
  return (
    <Router>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
        </ul>
      </nav>
      <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
      </Switch>
    </Router>
  );
};
```
Description: In this example, we set up routes using Router, Switch, and Route components from React Router. The <Link> components create navigation links, and based on the URL, the corresponding component (Home or About) will be rendered.

### Day 10: State Management with React Context

Introduction to React Context
Explanation: Introduce React Context as a mechanism for managing state across components without prop drilling.
Creating a context and providing values
Explanation: Discuss how to create a context and provide values to it, making the values accessible to components that consume the context.
Consuming context values using context API or useContext hook
Explanation: Explain how to consume context values in components using the context API (Consumer component) or the useContext hook.
Example Code:
```js
import React, { createContext, useContext } from 'react';

const UserContext = createContext();

const DisplayUsername = () => {
  const user = useContext(UserContext);

  return <h1>Welcome, {user.username}!</h1>;
};

const App = () => {
  const user = {
    username: 'JohnDoe',
  };

  return (
    <UserContext.Provider value={user}>
      <DisplayUsername />
    </UserContext.Provider>
  );
};
```
Description: In this example, we create a context called UserContext using createContext. The DisplayUsername component consumes the user context using the useContext hook and displays the username. The user object is provided as the value to the UserContext.Provider, making it accessible to the consuming components.
  
### Day 11: React Hooks

Introduction to React Hooks
Explanation: Introduce React Hooks as a way to add state and other React features to functional components without using class components.
useState: Managing state in functional components
Explanation: Discuss how to use the useState hook to add and manage state in functional components.
useEffect: Performing side effects in functional components
Explanation: Explain how to use the useEffect hook to perform side effects, such as data fetching, subscribing to events, or updating the DOM, in functional components.
Example Code:
```js
import React, { useState, useEffect } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

const App = () => {
  return <Counter />;
};
```
Description: In this example, the Counter component uses the useState hook to add state to track the count value. The useEffect hook is used to update the document title whenever the count value changes. Clicking the "Increment" button updates the count state and triggers the effect.

### Day 12: React Forms and Validation

Controlled components and form handling
Explanation: Review controlled components and how to handle form inputs and their state in React.
Form validation with state and conditional rendering
Explanation: Discuss form validation techniques using state and conditional rendering to display error messages or disable the submit button.
Example Code:
```js
import React, { useState } from 'react';

const LoginForm = () => {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');
  const [isFormValid, setFormValid] = useState(false);

  const handleUsernameChange = (e) => {
    setUsername(e.target.value);
  };

  const handlePasswordChange = (e) => {
    setPassword(e.target.value);
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    // Perform form submission logic
  };

  useEffect(() => {
    setFormValid(username !== '' && password !== '');
  }, [username, password]);

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={username}
        onChange={handleUsernameChange}
        placeholder="Username"
      />
      <input
        type="password"
        value={password}
        onChange={handlePasswordChange}
        placeholder="Password"
      />
      <button type="submit" disabled={!isFormValid}>
        Submit
      </button>
    </form>
  );
};

const App = () => {
  return <LoginForm />;
};
```
Description: In this example, the LoginForm component manages the state of username, password, and isFormValid using the useState hook. The form inputs are controlled components, and their values are updated via the handleUsernameChange and handlePasswordChange functions. The form submission is handled by the handleSubmit function, which is triggered when the submit button is clicked. The isFormValid state determines whether the submit button is enabled or disabled based on the input values.

### Day 13: React Component Lifecycle

Understanding the React component lifecycle
Explanation: Provide an overview of the different phases in the React component lifecycle, including mounting, updating, and unmounting.
Class component lifecycle methods
Explanation: Explore the class component lifecycle methods, such as componentDidMount, componentDidUpdate, and componentWillUnmount, and their purposes.
Example Code:
``` 
import React, { Component } from 'react';

class Timer extends Component {
  constructor(props) {
    super(props);
    this.state = { seconds: 0 };
  }

  componentDidMount() {
    this.timerId = setInterval(() => {
      this.setState((prevState) => ({ seconds: prevState.seconds + 1 }));
    }, 1000);
  }

  componentWillUnmount() {
    clearInterval(this.timerId);
  }

  render() {
    return <div>Seconds: {this.state.seconds}</div>;
  }
}

const App = () => {
  return <Timer />;
};
```

Description: In this example, the Timer class component uses the componentDidMount method to start a timer that increments the seconds state every second using setInterval. The componentWillUnmount method is used to clear the timer when the component is about to be unmounted. The current value of seconds is displayed in the render method.

###