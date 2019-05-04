---
title: State
seoTitle: 상태(State)와 이벤트 처리 | React | ohoo
seoDescription: description for search engines
isFree: true
---


상태를 갖는 경우에는 함수형 컴포넌트 대신 class형 컴포넌트를 사용해야 합니다. 

상태 = 이벤트 ???

마우스를 클릭하거나 키보드를 조작할 때 상태는 변경됩니다. 

```
// 1
// index.js
import React from "react";
import ReactDOM from "react-dom";

function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById("root"));
}

setInterval(tick, 1000);
```

```
// 2
// index.js

import React from "react";
import ReactDOM from "react-dom";

function Clock(props) {
  return (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {props.date.toLocaleTimeString()}.</h2>
    </div>
  );
}

function tick() {
  ReactDOM.render(<Clock date={new Date()} />, document.getElementById("root"));
}

setInterval(tick, 1000);
```

```
// 3
// index.js
import React from "react";
import ReactDOM from "react-dom";

class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

function tick() {
  ReactDOM.render(<Clock date={new Date()} />, document.getElementById("root"));
}

setInterval(tick, 1000);
```

```
// 4
// index.js
import React from "react";
import ReactDOM from "react-dom";

class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date() };
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

ReactDOM.render(<Clock />, document.getElementById("root"));
```






## 상태
#### 초깃값 설정(constructor)
```
    // 초깃값 설정
    constructor(props) {
      super(props);
      this.state = {

      };
    }
```

```
import React from "react";

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      date: new Date()
    };
  }

  render() {
    return (
      <div>
        <p>Hello, world!</p>
        <p>{this.state.date.toLocaleTimeString()}</p>
      </div>
    );
  }
}

export default App;
```

상태의 경우에는 속성과 다르게 계속해서 변경되는데 지금 현재의 코드는 초기값만 가져오도록 작성되었기 때문에 처음 코드가 실행될 때의 시간에서 멈춰있음.

#### 상태 변경(setState)
```
...
class 컴포넌트이름 extends Component {

    // 초깃값 설정
    constructor(props) {
      ...
    }

    // 상태 변경
    a

render() {
...
```


```
import React from "react";

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      date: new Date()
    };
  }

  componentDidMount() {
    this.timerID = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.timerID);
  }

  tick() {
    this.setState({
      date: new Date()
    });
  }

  render() {
    return (
      <div>
        <p>Hello, world!</p>
        <p>{this.state.date.toLocaleTimeString()}</p>
      </div>
    );
  }
}

export default App;
```

