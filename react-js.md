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
``` js
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

### Day 14: React Context with useContext Hook

Recap of React Context and Provider/Consumer pattern
Explanation: Review the concept of React Context and how to use the Provider/Consumer pattern for sharing data across components.
Using the useContext hook for consuming context
Explanation: Introduce the useContext hook as a simpler and more concise way to consume context in functional components.
Example Code:
```js
import React, { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

const ThemeToggle = () => {
  const theme = useContext(ThemeContext);
  const toggleTheme = () => {
    // Toggle theme logic
  };

  return (
    <button onClick={toggleTheme}>
      Toggle Theme ({theme === 'light' ? 'Dark' : 'Light'})
    </button>
  );
};

const App = () => {
  return (
    <ThemeContext.Provider value="light">
      <ThemeToggle />
    </ThemeContext.Provider>
  );
};
```
Description: In this example, we create a ThemeContext using createContext and provide a default value of 'light'. The ThemeToggle component consumes the theme value using the useContext hook. When the toggleTheme function is called, the theme is toggled between 'light' and 'dark'. The current theme is displayed on the button.

### Day 15: Error Boundaries

Introduction to Error Boundaries
Explanation: Introduce the concept of Error Boundaries as a way to handle and gracefully display errors in React components.
Creating an Error Boundary component
Explanation: Discuss how to create an Error Boundary component using the static getDerivedStateFromError and componentDidCatch lifecycle methods.
Implementing an Error Boundary in a component hierarchy
Explanation: Explain how to wrap components in an Error Boundary to catch and handle errors within the component tree.
Example Code:

```js
import React, { Component } from 'react';

class ErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    // Log or handle the error
  }

  render() {
    if (this.state.hasError) {
      return <div>Something went wrong.</div>;
    }

    return this.props.children;
  }
}

const App = () => {
  return (
    <ErrorBoundary>
      <div>
        <h1>Welcome to My App</h1>
        <SomeComponent />
      </div>
    </ErrorBoundary>
  );
};
```
Description: In this example, we create an ErrorBoundary component that catches and handles errors within its child components. If an error occurs, the getDerivedStateFromError method updates the state to indicate that an error has occurred. The componentDidCatch method can be used to log or handle the error. The ErrorBoundary component displays a fallback message when an error is caught. The SomeComponent is wrapped in the ErrorBoundary to handle any potential errors that may occur within it.

### Day 16: React Testing with Jest and React Testing Library

Introduction to testing in React
Explanation: Provide an overview of the importance of testing in React applications and the benefits of using testing libraries.
Setting up Jest and React Testing Library
Explanation: Guide the participants through the setup process for Jest and React Testing Library in a React project.
Writing unit tests for React components
Explanation: Explain how to write unit tests using Jest and React Testing Library to test component rendering, user interactions, and state changes.
Example Code:
```js
import React from 'react';
import { render, fireEvent } from '@testing-library/react';
import Button from './Button';

describe('Button component', () => {
  test('renders the button correctly', () => {
    const { getByText } = render(<Button label="Click me" />);
    const buttonElement = getByText('Click me');
    expect(buttonElement).toBeInTheDocument();
  });

  test('calls the onClick handler when clicked', () => {
    const handleClick = jest.fn();
    const { getByText } = render(<Button label="Click me" onClick={handleClick} />);
    const buttonElement = getByText('Click me');
    fireEvent.click(buttonElement);
    expect(handleClick).toHaveBeenCalled();
  });
});
```
Description: In this example, we write unit tests for a Button component. The first test checks if the button is rendered correctly by using the getByText function from React Testing Library to find the button element with the specified label. The second test simulates a click event on the button using fireEvent.click and verifies that the onClick handler is called by using a mock function (jest.fn()) and the toHaveBeenCalled assertion.

### Day 17: React Component Composition and Reusability

Component composition and reusability
Explanation: Discuss the concept of component composition and how to create reusable components by composing smaller, modular components.
Props children pattern
Explanation: Introduce the props children pattern to pass components or elements as children to other components, allowing for flexible and dynamic compositions.
Example Code:

```js
import React from 'react';

const Card = ({ title, children }) => {
  return (
    <div className="card">
      <h2>{title}</h2>
      <div className="content">{children}</div>
    </div>
  );
};

const App = () => {
  return (
    <Card title="My Card">
      <p>This is the content of my card.</p>
    </Card>
  );
};
```
Description: In this example, we have a Card component that accepts a title prop and children as its content. The children prop allows any React elements or components to be passed as children to the Card component, enabling flexible composition. In the App component, we pass a paragraph element as the content of the Card component.

### Day 18: React Performance Optimization

React.memo for optimizing functional components
Explanation: Introduce the React.memo higher-order component to optimize functional components by preventing unnecessary re-renders.
useMemo for memoizing expensive computations
Explanation: Discuss how to use the useMemo hook to memoize expensive computations and avoid recomputing them on every render.
Example Code:

```js
import React, { useMemo } from 'react';

const ExpensiveComponent = ({ data }) => {
  // Expensive computation based on data
  const computedValue = useMemo(() => {
    // Expensive computation logic
    return compute(data);
  }, [data]);

  return <div>{computedValue}</div>;
};

const App = () => {
  const data = fetchData(); // Fetch data from an API

  return <ExpensiveComponent data={data} />;
};
```
Description: In this example, the ExpensiveComponent receives data as a prop and performs an expensive computation based on that data. By using the useMemo hook, we memoize the computed value and only recompute it when the data prop changes. This helps optimize performance by avoiding unnecessary computations on every render.

### Day 19: React and RESTful APIs

Fetching data from a RESTful API
Explanation: Discuss how to fetch data from a RESTful API using the fetch API or libraries like Axios in React.
Managing API data with state
Explanation: Explain how to manage API data using state in React components and handle loading, error, and success states.
Example Code:
```js
import React, { useState, useEffect } from 'react';

const UserList = () => {
  const [users, setUsers] = useState([]);
  const [isLoading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/users')
      .then((response) => response.json())
      .then((data) => {
        setUsers(data);
        setLoading(false);
      })
      .catch((error) => {
        setError(error);
        setLoading(false);
      });
  }, []);

  if (isLoading) {
    return <div>Loading...</div>;
  }

  if (error) {
    return <div>Error: {error.message}</div>;
  }

  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
};

const App = () => {
  return <UserList />;
};
```
Description: In this example, the UserList component fetches user data from a RESTful API using the fetch API. The component manages the loading, error, and success states using state variables. While the data is being fetched, a loading message is displayed. If an error occurs, an error message is displayed. Once the data is successfully fetched, it is rendered in an unordered list.

### Day 20: React Router for Routing in React Applications

Introduction to React Router
Explanation: Provide an overview of React Router and its importance in building multi-page React applications.
Setting up React Router
Explanation: Guide the participants through the setup process for React Router in a React project.
Basic routing and navigation
Explanation: Explain how to define routes and navigate between them using React Router's Route and Link components.
Example Code:
```js
import React from 'react';
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

const Home = () => <div>Home</div>;
const About = () => <div>About</div>;
const Contact = () => <div>Contact</div>;

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
          <li>
            <Link to="/contact">Contact</Link>
          </li>
        </ul>
      </nav>

      <Route path="/" exact component={Home} />
      <Route path="/about" component={About} />
      <Route path="/contact" component={Contact} />
    </Router>
  );
};
```
Description: In this example, we use React Router to define routes and navigation. The Router component sets up the routing context, and the Link component is used to create navigation links. The Route component defines the association between a route path and the corresponding component to render. Clicking on the navigation links changes the URL and renders the corresponding component.

### Day 21: React Forms and Form Validation (2)

Controlled components and form handling
Explanation: Discuss the concept of controlled components and how to handle form inputs using React's controlled component pattern.
Form submission and handling
Explanation: Explain how to handle form submission in React and perform actions such as sending data to a server or updating state.
Form validation using built-in and custom validators
Explanation: Introduce form validation techniques using built-in HTML5 validation attributes and custom validation functions.
Example Code:

```js
  import React, { useState } from 'react';

const LoginForm = () => {
  const [formData, setFormData] = useState({
    username: '',
    password: '',
  });
  const [errors, setErrors] = useState({});

  const handleInputChange = (event) => {
    const { name, value } = event.target;
    setFormData((prevFormData) => ({
      ...prevFormData,
      [name]: value,
    }));
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    const validationErrors = validateForm(formData);
    if (Object.keys(validationErrors).length === 0) {
      // Submit form data or perform other actions
    } else {
      setErrors(validationErrors);
    }
  };

  const validateForm = (data) => {
    let errors = {};

    if (data.username.trim() === '') {
      errors.username = 'Username is required';
    }

    if (data.password.trim() === '') {
      errors.password = 'Password is required';
    }

    return errors;
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label htmlFor="username">Username:</label>
        <input
          type="text"
          id="username"
          name="username"
          value={formData.username}
          onChange={handleInputChange}
        />
        {errors.username && <div className="error">{errors.username}</div>}
      </div>
      <div>
        <label htmlFor="password">Password:</label>
        <input
          type="password"
          id="password"
          name="password"
          value={formData.password}
          onChange={handleInputChange}
        />
        {errors.password && <div className="error">{errors.password}</div>}
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

const App = () => {
  return <LoginForm />;
};
```
Description: In this example, we create a simple login form using React. The form data is managed using state and the controlled component pattern. The handleInputChange function updates the form data state whenever the input values change. The handleSubmit function is called when the form is submitted and performs form validation using the validateForm function. If there are validation errors, the errors are displayed. Otherwise, the form data can be submitted or further actions can be performed.

### Day 22: React Hooks - useRef and useReducer

useRef hook for accessing DOM elements
Explanation: Introduce the useRef hook and its usage to access and interact with DOM elements in React.
useReducer hook for managing complex state
Explanation: Discuss the useReducer hook as an alternative to useState for managing complex state and actions in React.
Example Code:
```js
import React, { useRef, useReducer } from 'react';

const Counter = () => {
  const countRef = useRef(0);
  const [state, dispatch] = useReducer(counterReducer, 0);

  const counterReducer = (state, action) => {
    switch (action.type) {
      case 'INCREMENT':
        return state + 1;
      case 'DECREMENT':
        return state - 1;
      default:
        return state;
    }
  };

  const increment = () => {
    countRef.current += 1;
    console.log('Count:', countRef.current);
  };

  const decrement = () => {
    dispatch({ type: 'DECREMENT' });
  };

  return (
    <div>
      <button onClick={increment}>Increment (ref)</button>
      <button onClick={decrement}>Decrement (reducer)</button>
      <p>Count: {state}</p>
    </div>
  );
};

const App = () => {
  return <Counter />;
};
```
Description: In this example, we use the useRef hook to create a reference (countRef) and store the current count value. The increment function updates the count value by directly accessing and modifying the reference value. We also use the useReducer hook to manage the count state in a more complex scenario, where the count can be incremented or decremented using the dispatch function. The count value is displayed using the state variable.

### Day 23: React Context API

Introduction to React Context
Explanation: Provide an overview of React Context and its purpose in sharing data between components without prop drilling.
Creating a Context and Provider
Explanation: Explain how to create a context and its provider component to share data throughout the component tree.
Consuming Context with useContext
Explanation: Discuss how to consume the context using the useContext hook and access the shared data in nested components.
Example Code:

```js
import React, { useContext } from 'react';

const ThemeContext = React.createContext();

const App = () => {
  return (
    <ThemeContext.Provider value="dark">
      <Header />
      <Content />
    </ThemeContext.Provider>
  );
};

const Header = () => {
  const theme = useContext(ThemeContext);

  return (
    <header className={theme}>
      <h1>My App</h1>
    </header>
  );
};

const Content = () => {
  const theme = useContext(ThemeContext);

  return (
    <div className={theme}>
      <p>This is the content of the app.</p>
    </div>
  );
};
```
Description: In this example, we create a ThemeContext using React's createContext function. The App component serves as the provider of the context, wrapping the Header and Content components. The Header and Content components consume the context using the useContext hook, accessing the shared theme value. The className of the header and content elements dynamically change based on the theme value.
