---
title: 이벤트 핸들링
seoTitle: 이벤트 핸들링 | React | ohoo
seoDescription: description for search engines
isFree: true
---


```
// HTML 요소의 이벤트 핸들러 속성
<div onclick="이벤트 핸들러()">클릭</div>

// 리액트
<div onclick={이벤트 핸들러}>클릭</div>
```


```
// 1 
// App.js
import React from "react";
import Like from "./Like.js";

const App = () => {
  return (
    <div>
      <Like />
    </div>
  );
};

export default App;

// Like.js
import React from "react";

class Like extends React.Component {
  render() {
    return (
      <div>
        <div>0</div>
        <button>좋아요</button>
      </div>
    );
  }
}

export default Like;
```
 
 
```
// 2. 초깃값 설정
constructor(props) {
  super(props);
  this.state = {
    like: 0
  };
}
```

```
// 3. 상태 참조
<div>
  <div>{this.state.like}</div>
  <button>좋아요</button>
</div>
```

```
// 4 이벤트 처리
// button 컴포넌트에 이벤트 핸들러 추가
// 이벤트 핸들러 정의
// 이벤트 핸들러 바인딩

// Like.js
import React from "react";

class Like extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      like: 0
    };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState({
      like: this.state.like + 1
    });
  }

  render() {
    return (
      <div>
        <div>{this.state.like}</div>
        <button onClick={this.handleClick}>좋아요</button>
      </div>
    );
  }
}

export default Like;
```


```
// 이벤트를 최상위 컴포넌트에서 관리
// App.js
import React from "react";
import Like from "./Like.js";

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      like: 0
    };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState({
      like: this.state.like + 1
    });
  }

  render() {
    return (
      <div>
        <Like like={this.state.like} handleClick={this.handleClick} />
      </div>
    );
  }
}

export default App;

// Like.js
import React from "react";

class Like extends React.Component {
  render() {
    return (
      <div>
        <div>{this.props.like}</div>
        <button onClick={this.props.handleClick}>좋아요</button>
      </div>
    );
  }
}

export default Like;
```


## 이벤트 객체
















