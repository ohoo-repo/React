---
title: 스타일링:MUI
seoTitle: 스타일링:MUI | React | ohoo
seoDescription: description for search engines
isFree: true
---



```
// with npm
npm install @material-ui/core

// with yarn
yarn add @material-ui/core
```

npm 혹은 yarn으로 MUI 설치하기
설치가 완료되면 package.json 파일의 dependencies에서 @material-ui/core가 있는지 확인
있다면 성공적으로 설치된 것임.

## 컴포넌트 사용하기
Material-UI에서 제공하는 컴포넌트를 사용하고 싶다면 Component Demos에서 어떤 컴포넌트가 제공되는지 찾아봄
우리는 Button 컴포넌트를 사용할 

```
// MUI 컴포넌트 사용 전
import React from "react";

class App extends React.Component {
  render() {
    return (
      <div>
        <button>확인</button>
      </div>
    );
  }
}

export default App;

// MUI 컴포넌트 사용 후
import React from "react";
import Button from "@material-ui/core/Button";

class App extends React.Component {
  render() {
    return (
      <div>
        <Button>확인</Button>
      </div>
    );
  }
}

export default App;
```

모듈을 추가하고 컴포넌트 이름을 대문자로 바꿔주면 됨

## 꾸미기
만일 CSS를 적용하고 싶다면 

```
// 꾸미기 전

// 꾸미기 후
import React from "react";
import { withStyles } from "@material-ui/core/styles";

const styles = {
  button: {
    backgroundColor: "blue"
  }
};

class App extends React.Component {
  render() {
    return (
      <div>
        <button className={this.props.classes.button}>확인</button>
      </div>
    );
  }
}

export default withStyles(styles)(App);
```


## 간단한 예제
```
import React from "react";
import { withStyles } from "@material-ui/core/styles";
import { Button, Card } from "@material-ui/core";

const styles = {
  button: {
    backgroundColor: "grey",
    margin: 10
  },
  card: {
    padding: 30,
    maxWidth: 480,
    margin: "auto"
  }
};

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      todos: ["운동", "리액트 공부", "방 정리"],
      todo: ""
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleClick = this.handleClick.bind(this);
    this.handleDoubleClick = this.handleDoubleClick.bind(this);
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

  handleDoubleClick(index) {
    const { todos } = this.state;
    this.setState({
      todos: [...todos.slice(0, index), ...todos.slice(index + 1, todos.length)]
    });
  }

  handleRemove() {
    this.setState({
      todos: []
    });
  }

  render() {
    const todoList = this.state.todos.map((todo, index) => (
      <li key={index} onDoubleClick={() => this.handleDoubleClick(index)}>
        {todo}
      </li>
    ));

    const { classes } = this.props;

    return (
      <div>
        <Card className={classes.card}>
          <div>
            <input value={this.state.todo} onChange={this.handleChange} />
            <Button className={classes.button} onClick={this.handleClick}>
              추가하기
            </Button>
            <Button className={classes.button} onClick={this.handleRemove}>
              전체 제거하기
            </Button>
          </div>
          <div>
            <ul>{todoList}</ul>
          </div>
        </Card>
      </div>
    );
  }
}

export default withStyles(styles)(App);
```











