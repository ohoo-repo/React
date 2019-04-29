---
title: 간단한 예제:현재 시간 나타내기
seoTitle: 간단한 예제:현재 시간 나타내기 | React | ohoo
seoDescription: description for search engines
isFree: true
---


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
    this.clock = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.clock);
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
