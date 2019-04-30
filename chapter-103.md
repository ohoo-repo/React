---
title: 간단한 예제:Todo 앱
seoTitle: 간단한 예제:Todo 앱 | React | ohoo
seoDescription: description for search engines
isFree: true
---


```
npx create-react-app todo
cd todo
npm start
```

```
// App.js
import React from "react";

class App extends React.Component {
  render() {
    return <div>Todo 앱 만들기</div>;
  }
}

export default App;

// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

App.js 파일의 코드를 위와 같이 변경하고 다음 3개의 파일을 삭제함

* App.css
* logo.svg
* serviceWorker.js



```
// index.css
background-color: #eeeeee;
```

index.css 파일의 body에 background-color 추가


## 구조
```
|-- App.js
|  |-- TodoInput.js
|  |-- TodoList.js
|  |  |-- TodoItem.js
```

## 만들기
```
// App.js
import React from "react";
import TodoInput from "./TodoInput.js";
import TodoList from "./TodoList.js";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>Todo 앱 만들기</p>
        <TodoInput />
        <TodoList />
      </div>
    );
  }
}

export default App;
```

```
// TodoInput.js
import React from "react";

class TodoInput extends React.Component {
  render() {
    return (
      <div>
        <p>TodoInput</p>
      </div>
    );
  }
}

export default TodoInput;
```

```
// TodoList.js
import React from "react";
import TodoItem from "./TodoItem.js";

class TodoList extends React.Component {
  render() {
    return (
      <div>
        <p>TodoList</p>
        <TodoItem />
      </div>
    );
  }
}

export default TodoList;
```

```
// TodoItem.js
import React from "react";

class TodoItem extends React.Component {
  render() {
    return (
      <div>
        <p>TodoItem</p>
      </div>
    );
  }
}

export default TodoItem;
```

## Material-UI 추가
```
npm install @material-ui/core
```


#### Material-UI 컴포넌트 사용
```
// App.js
import React from "react";
import TodoInput from "./TodoInput.js";
import TodoList from "./TodoList.js";

import { Card } from "@material-ui/core";

class App extends React.Component {
  render() {
    return (
      <div>
        <Card>
          <p>Todo 앱 만들기</p>
          <TodoInput />
          <TodoList />
        </Card>
      </div>
    );
  }
}

export default App;
```

```
import Card from '@material-ui/core/Card';
import { Card } from "@material-ui/core";
```

둘 중 어느 것을 사용해도 결과는 동일함.

```
import Card from '@material-ui/core/Card';
import Button from '@material-ui/core/Button';
import Input from '@material-ui/core/Input';

import { Card, Button, Input } from "@material-ui/core";
```

하지만 만일 사용할 컴포넌트의 수가 증가할 경우 하단과 같은 방법이 더 간편함


#### CSS 추가

```
// App.js
import React from "react";
import TodoInput from "./TodoInput.js";
import TodoList from "./TodoList.js";

import { withStyles } from "@material-ui/core/styles";
import { Card } from "@material-ui/core";

const styles = {
  card: {
    maxWidth: 600,
    marginTop: 40,
    margin: "auto",
    padding: 60
  }
};

class App extends React.Component {
  render() {
    return (
      <div>
        <Card className={this.props.classes.card}>
          <p>Todo 앱 만들기</p>
          <TodoInput />
          <TodoList />
        </Card>
      </div>
    );
  }
}

export default withStyles(styles)(App);
```

```
class App extends React.Component {
  render() {
    const { classes } = this.props;

    return (
      <div>
        <Card className={classes.card}>
          <p>Todo 앱 만들기</p>
          <TodoInput />
          <TodoList />
        </Card>
      </div>
    );
  }
}
```

## Props 추가

## TodoInput
```
// TodoInput.js
import React from "react";
import { TextField, Button } from "@material-ui/core";

class TodoInput extends React.Component {
  render() {
    return (
      <div>
        <p>TodoInput</p>
        <TextField variant="outlined" />
        <Button>추가</Button>
        <Button>전체 삭제</Button>
      </div>
    );
  }
}

export default TodoInput;
```

```
import React from "react";

import { withStyles } from "@material-ui/core/styles";
import { TextField, Button } from "@material-ui/core";

const styles = {
  input: {
    height: 20
  },
  button: {
    margin: 10,
    backgroundColor: "#eeeeee"
  }
};

class TodoInput extends React.Component {
  render() {
    const { classes } = this.props;

    return (
      <div>
        <p>TodoInput</p>
        <TextField variant="outlined" className={classes.input} />
        <Button className={classes.button}>추가</Button>
        <Button className={classes.button}>전체 삭제</Button>
      </div>
    );
  }
}

export default withStyles(styles)(TodoInput);
```


## TodoList
```
// TodoList.js
import React from "react";
import TodoItem from "./TodoItem.js";

class TodoList extends React.Component {
  render() {
    return (
      <div>
        <TodoItem name="운동하기" />
        <TodoItem name="리액트 공부하기" />
        <TodoItem name="방 정리하기" />
      </div>
    );
  }
}

export default TodoList;

// TodoItem.js
import React from "react";

class TodoItem extends React.Component {
  render() {
    return (
      <div>
        <p>{this.props.name}</p>
      </div>
    );
  }
}

export default TodoItem;
```


```
// TodoList.js
import React from "react";
import TodoItem from "./TodoItem.js";

class TodoList extends React.Component {
  render() {
    const todos = ["운동", "리액트 공부", "방 정리"];
    const todoList = todos.map(todo => <TodoItem name={todo} />);

    return <div>{todoList}</div>;
  }
}

export default TodoList;
```



```
// TodoList.js
import React from "react";
import TodoItem from "./TodoItem.js";

class TodoList extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      todos: ["운동", "리액트 공부", "방 정리"]
    };
  }

  render() {
    const todoList = this.state.todos.map((todo, index) => (
      <TodoItem key={index} name={todo} />
    ));

    return <div>{todoList}</div>;
  }
}

export default TodoList;
```

```
// 초기 상태를 App.js로 이동
// App.js
import React from "react";
import TodoInput from "./TodoInput.js";
import TodoList from "./TodoList.js";

import { withStyles } from "@material-ui/core/styles";
import { Card } from "@material-ui/core";

const styles = {
  card: {
    maxWidth: 600,
    marginTop: 40,
    margin: "auto",
    padding: 60
  }
};

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      todos: ["운동하기", "리액트 공부", "방 정리"]
    };
  }

  render() {
    const { classes } = this.props;

    return (
      <div>
        <Card className={classes.card}>
          <p>Todo 앱 만들기</p>
          <TodoInput />
          <TodoList todos={this.state.todos} />
        </Card>
      </div>
    );
  }
}

export default withStyles(styles)(App);

// TodoList.js
import React from "react";
import TodoItem from "./TodoItem.js";

class TodoList extends React.Component {
  render() {
    const todoList = this.props.todos.map((todo, index) => (
      <TodoItem key={index} name={todo} />
    ));

    return <div>{todoList}</div>;
  }
}

export default TodoList;
```


```

```
