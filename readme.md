### 1. Class Components
A class component with state and lifecycle methods.

```jsx
// src/ClassComponent.js
import React, { Component } from 'react';

class ClassComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  componentDidMount() {
    console.log('Component did mount');
  }

  componentDidUpdate() {
    console.log('Component did update');
  }

  componentWillUnmount() {
    console.log('Component will unmount');
  }

  handleIncrement = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <h1>Class Component</h1>
        <p>Count: {this.state.count}</p>
        <button onClick={this.handleIncrement}>Increment</button>
      </div>
    );
  }
}

export default ClassComponent;
```
### 2. Functional Components
A simple functional component with props.

```jsx
// src/FunctionalComponent.js
import React from 'react';

const FunctionalComponent = ({ message }) => {
  return (
    <div>
      <h1>Functional Component</h1>
      <p>{message}</p>
    </div>
  );
};

export default FunctionalComponent;
```
### 3. Hooks: useState and useEffect
Using useState and useEffect hooks in a functional component.

```jsx
// src/HooksComponent.js
import React, { useState, useEffect } from 'react';

const HooksComponent = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Component did mount/update');
    return () => {
      console.log('Component will unmount');
    };
  }, [count]);

  const handleIncrement = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h1>Hooks Component</h1>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>Increment</button>
    </div>
  );
};

export default HooksComponent;
```
### 4. Event Handling
Handling events in React.

```jsx
// src/EventHandlingComponent.js
import React from 'react';

const EventHandlingComponent = () => {
  const handleClick = () => {
    alert('Button clicked!');
  };

  return (
    <div>
      <h1>Event Handling</h1>
      <button onClick={handleClick}>Click Me</button>
    </div>
  );
};

export default EventHandlingComponent;
```
### 5. Forms
Handling forms and controlled components.

```jsx
// src/FormComponent.js
import React, { useState } from 'react';

const FormComponent = () => {
  const [name, setName] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Hello, ${name}`);
    setName('');
  };

  return (
    <form onSubmit={handleSubmit}>
      <h1>Form Handling</h1>
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Enter your name"
      />
      <button type="submit">Submit</button>
    </form>
  );
};

export default FormComponent;
```
### 6. Lists and Keys
Rendering a list of items.

```jsx
// src/ListComponent.js
import React from 'react';

const ListComponent = () => {
  const items = ['Item 1', 'Item 2', 'Item 3'];

  return (
    <div>
      <h1>List Rendering</h1>
      <ul>
        {items.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
};

export default ListComponent;
```
### 7. Conditional Rendering
Conditionally rendering elements.

```jsx
// src/ConditionalRenderingComponent.js
import React, { useState } from 'react';

const ConditionalRenderingComponent = () => {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  const toggleLogin = () => {
    setIsLoggedIn(!isLoggedIn);
  };

  return (
    <div>
      <h1>Conditional Rendering</h1>
      {isLoggedIn ? <p>Welcome back!</p> : <p>Please log in.</p>}
      <button onClick={toggleLogin}>
        {isLoggedIn ? 'Logout' : 'Login'}
      </button>
    </div>
  );
};

export default ConditionalRenderingComponent;
```
### 8. Context
Using React Context for state management.

```jsx
// src/MyContext.js
import React, { createContext, useContext, useState } from 'react';

const MyContext = createContext();

const MyProvider = ({ children }) => {
  const [value, setValue] = useState('Hello from context!');

  return (
    <MyContext.Provider value={{ value, setValue }}>
      {children}
    </MyContext.Provider>
  );
};

const ContextComponent = () => {
  const { value, setValue } = useContext(MyContext);

  return (
    <div>
      <h1>Context API</h1>
      <p>{value}</p>
      <button onClick={() => setValue('New value from context!')}>Change Value</button>
    </div>
  );
};

const AppWithContext = () => {
  return (
    <MyProvider>
      <ContextComponent />
    </MyProvider>
  );
};

export default AppWithContext;
```
### Putting it All Together
Make sure to import and render these components in your App.js to see them in action.

```jsx
// src/App.js
import React from 'react';
import ClassComponent from './ClassComponent';
import FunctionalComponent from './FunctionalComponent';
import HooksComponent from './HooksComponent';
import EventHandlingComponent from './EventHandlingComponent';
import FormComponent from './FormComponent';
import ListComponent from './ListComponent';
import ConditionalRenderingComponent from './ConditionalRenderingComponent';
import AppWithContext from './MyContext';

const App = () => {
  return (
    <div>
      <ClassComponent />
      <FunctionalComponent message="Hello from props!" />
      <HooksComponent />
      <EventHandlingComponent />
      <FormComponent />
      <ListComponent />
      <ConditionalRenderingComponent />
      <AppWithContext />
    </div>
  );
};

export default App;
```
This setup should give you a comprehensive understanding of various React features and how to implement them in your applications.
