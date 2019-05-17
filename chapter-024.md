---
title: 리스트와 키
seoTitle: 리스트와 키 | React | ohoo
seoDescription: description for search engines
isFree: true
---


```
import React from "react";

function Hello(props) {
  return (
    <div>
      <p>Hello, {props.name}!</p>
      <p>저는 {props.age}살입니다.</p>
      <p>저는 {props.title}의 저자입니다.</p>
    </div>
  );
}

const persons = [
  {
    id: 0,
    name: "나제한",
    age: 28,
    book: {
      title: "하버드가기"
    }
  },
  {
    id: 1,
    name: "나제인",
    age: 17,
    book: {
      title: "서울대가기"
    }
  }
];

function App() {
  return (
    <div>
      {persons.map(person => (
        <Hello
          key={person.id}
          name={person.name}
          age={person.age}
          title={person.book.title}
        />
      ))}
    </div>
  );
}

export default App;
```




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
// 전체 삭제하기
import React from "react";

class Todo extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      todos: ["운동", "리액트 공부", "방 정리"]
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleClick = this.handleClick.bind(this);
    this.handleRemove = this.handleRemove.bind(this);
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

  handleRemove() {
    this.setState({
      todos: []
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
        <button onClick={this.handleRemove}>제거하기</button>
        <ul>{todoList}</ul>
      </div>
    );
  }
}

export default Todo;
```

```
// 하나씩 삭제하기
import React from "react";

class Todo extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      todos: ["운동", "리액트 공부", "방 정리"],
      todo: ""
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleClick = this.handleClick.bind(this);
    this.handleDoubleClick = this.handleDoubleClick.bind(this);
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

  handleDoubleClick(index) {
    const { todos } = this.state;
    this.setState({
      todos: [...todos.slice(0, index), ...todos.slice(index + 1, todos.length)]
    });
  }

  render() {
    const todoList = this.state.todos.map((todo, index) => (
      <li key={index} onDoubleClick={() => this.handleDoubleClick(index)}>
        {todo}
      </li>
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


