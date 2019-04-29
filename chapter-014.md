---
title: 컴포넌트 반복
seoTitle: 컴포넌트 반복 | React | ohoo
seoDescription: description for search engines
isFree: true
---

```
// App.js
import React from "react";
import Todo from "./Todo.js";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>해야할 일</p>
        <Todo />
      </div>
    );
  }
}

export default App;

// Todo.js
import React from "react";

class Todo extends React.Component {
  render() {
    return (
      <ul>
        <li>운동</li>
        <li>리액트 공부</li>
        <li>방 정리</li>
      </ul>
    );
  }
}

export default Todo;
```

```
import React from "react";

class Todo extends React.Component {
  render() {
    const todos = ["운동", "리액트 공부", "방 정리"];
    const todoList = todos.map(todo => <li>{todo}</li>);

    return <ul>{todoList}</ul>;
  }
}

export default Todo;
```

```
import React from "react";

class Todo extends React.Component {
  render() {
    const todos = ["운동", "리액트 공부", "방 정리"];
    const todoList = todos.map((todo, index) => <li key={index}>{todo}</li>);

    return <ul>{todoList}</ul>;
  }
}

export default Todo;
```

```
import React from "react";

class Todo extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      todos: ["운동", "리액트 공부", "방 정리"]
    };
  }

  render() {
    const todoList = this.state.todos.map((todo, index) => (
      <li key={index}>{todo}</li>
    ));

    return <ul>{todoList}</ul>;
  }
}

export default Todo;
```


```
// 할 일 추가하기
import React from "react";

class Todo extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      todos: ["운동", "리액트 공부", "방 정리"]
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleClick = this.handleClick.bind(this);
  }

  handleChange(e) {
    this.setState({
      todo: e.target.value
    });
  }

  handleClick() {
    this.setState({
      todos: this.state.todos.concat(this.state.todo),
      todo: ""
    });
  }

  render() {
    const todoList = this.state.todos.map((todo, index) => (
      <li key={index}>{todo}</li>
    ));

    return (
      <div>
        <input value={this.state.todo} onChange={this.handleChange} />
        <button onClick={this.handleClick}>추가하기</button>
        <ul>{todoList}</ul>
      </div>
    );
  }
}

export default Todo;
```


```

```




