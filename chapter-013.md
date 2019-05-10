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
// App.js
import React from "react";
import NameInput from "./NameInput.js";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>이름을 입력하세요.</p>
        <NameInput/>
      </div>
    );
  }
}

export default App;

// NameInput.js
import React from "react";

class NameInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: ""
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleClick = this.handleClick.bind(this);
  }

  handleChange(e) {
    this.setState({ name: e.target.value });
  }

  handleClick() {
    alert(this.state.name);
    this.setState({ name: "" });
  }

  render() {
    return (
      <div>
        <input
          type="text"
          name="name"
          placeholder="이름을 입력하세요."
          value={this.state.name}
          onChange={this.handleChange}
        />
        <button type="button" onClick={this.handleClick}>
          click
        </button>
      </div>
    );
  }
}

export default NameInput;
```
