+++
author = "Udara Bibile"
authorImage = "/img/udarabibile.png"
title = "Introduction to React Hooks"
date = "2019-07-19"
description = "Giving superpowers to functional components"
tags = ["sql", "css", "html"]
categories = ["database", "syntax"]
images  = ["img/2019/react-hooks.png"]
type = "post"
aliases = ["migrate-from-jekyl"]
+++

From **React’s version 16.8.0**, Hooks are introduced to make functional components more useful.

<figure>
  <img class="image featured" src="/img/2019/class-functional-component.png" alt="" style="width:100%" >
  <figcaption style="text-align:center">React: Class Component vs Functional Component.</figcaption>
</figure>

<mark>TODO: MAKE MORE WIDTH</mark>

In React, **class components** are **stateful and smart**, being state is attached to it and kept persistent through renders. Then **functional components** were **stateless and dumb** components, having nor state nor logic attached to it.

As an example, class component can have `state`, and it could be manipulated using lifecycle methods such as `constructor`, `componentDidMount` and such. However, functional component only accepts `props` from its parent, and renders accordingly. It wouldn’t keep internal `state` value, that would be persistent through renders, but rather renders according to whatever passed through `props`.

In complex React application, there is parent *class component* keeping track of state, and manipulate state according to business logic. Afterwards child *functional components* are passed props, and used only for rendering purpose. These wouldn’t have any persistent state in it, and just used to break down complex components into segments.

```
<DigitalWatch>
Parent class component with state, and business logic to count time.

→ <TimeView time={this.state.time}>
Child functional component only with props and just rendering props.
```
<hr/>

React Hooks enable **functional components to attach local state with it, and React will preserve this state between re-renders**. Thereby this will allow React to be used without classes.

> However, we often can’t break complex components down any further because the logic is stateful and can’t be extracted to a function or another component.</p>
> — <cite>Dan Abramov[^1]</cite>

[^1]: Extracted from [medium article](https://medium.com/@dan_abramov/making-sense-of-react-hooks-fdbde8803889).

<br/>
As given, it’ll reduce usage of complex class components with all logic in it. Rather some of this business logic will be passed to its child functional component. This refactored functional components will have its functionality attached with it, so would act as reusable small components.

**Let's get started with hooks**: (Note that hooks doesn’t work inside classes.)

<hr/>

### State Hook

```
import React, { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}> Add </button>
      <button onClick={() => setCount(count - 1)}> Remove </button>
    </div>
  );
}
```

State hook here, just introduce **`this.State`** and **`this.setState`** to functional components. This `useState` returns value, its accessor and is initiated at the start: **`const [state, setState] = useState(initialState);`**. Thereby in retrospective, in contrast to class components by `Constructor`, and state manipulated functions such as *handleIncrease* which was bind to `this` scope.

Moreover state hook can be initiated for many types:

```
const [num, setNum] = useState(10);
const [name, setName] = useState('default');
const [obj, setObj] = useState([{ text: 'this is object' }]);
```

<hr/>

### Effect Hook

Effect hook here, is used to perform side effects in functional components. From familiar user cases, it could be considered combination of methods: **`componentDidMount`**, **`componentDidUpdate`**, and **`componentWillUnmount`**. So when React renders (updates the DOM including first render) component, this hook becomes applied. Typical use cases for effect hooks are data fetching, managing subscriptions and dealing with manual DOM changes.

#### Effect Hook without cleanup

Here at each time this functional component renders (including first render and subsequent re-renders due to `count` change) will execute effect hook function. In this instance it’ll perform side effect of manual DOM change by manipulating external element.

```
import React, { useState, useEffect } from 'react';

function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
     document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}> Click </button>
    </div>
  );
}
```

#### Conditional execution of effect hook










<br/><br/><br/><br/>

<mark>TODO: MAKE DARK THEME<mark>
<br/><br/>

