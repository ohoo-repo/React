---
title: State
seoTitle: 상태(State)와 이벤트 처리 | React | ohoo
seoDescription: description for search engines
isFree: true
---


지금까지 다룬 컴포넌트는 상태가 없는(stateless) 컴포넌트였기 때문에 부모로부터 받은 속성을 그대로 전달하기만 했습니다. 하지만 웹 앱의 많은 부분은 사용자와의 상호 작용에 의해 변경되기도 합니다. 이러한 경우에는 속성(Props) 대신에 상태(State)를 사용해야 하며 이를 상태가 있는(stateful) 컴포넌트라고 부릅니다.

상태를 갖는 경우에는 함수형 컴포넌트 대신 class형 컴포넌트를 사용해야 합니다. 

상태 = 이벤트 ???

마우스를 클릭하거나 키보드를 조작할 때 상태는 변경됩니다. 

```
// 상태 초깃값 설정하기
constructor(props) {
  super(props);
  this.state = {
    이름: 값
  }
}

// 상태 변경하기
this.setState({
  이름: 값
})

// 상태 참조하기
this.state.
```



상태를 설명하기 위해 초단위로 시간이 변경되는 시계를 만들어보자
```
// 1
// App.js
import React from "react";
import Clock from "./Clock.js";

const App = () => {
  return (
    <div>
      <Clock />
    </div>
  );
};

export default App;

// Clock.js
import React from "react";

class Clock extends React.Component {
  render() {
    return (
      <div>
        <p>Hello!</p>
        <div>It is {new Date().toLocaleTimeString()}.</div>
      </div>
    );
  }
}

export default Clock;
```

```
// 2 초깃값 설정
// Clock.js

constructor(props) {
  super(props);
  this.state = {
    date: new Date()
  };
}
```

class와 render 사이에 위의 코드를 

```
// 3 상태 참조
<div>
  <p>Hello!</p>
  <div>It is {this.state.date.toLocaleTimeString()}.</div>
</div>
```

```
// 4 상태 변경
componentDidMount() {
  setInterval(() => {
    this.setState({ date: new Date() });
  }, 1000);
}
```

```
// 5
componentDidMount() {
  this.clockID = setInterval(() => {
    this.setState({ date: new Date() });
  }, 1000);
}

componentWillUnmount() {
  clearInterval(this.clockID);
}
```




componentDidMount와 componentWillUnmount 이외에도 다양한 라이프사이클 메서드가 존재함.





















