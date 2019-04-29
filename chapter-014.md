---
title: 컴포넌트 반복
seoTitle: 컴포넌트 반복 | React | ohoo
seoDescription: description for search engines
isFree: true
---

```
// App.js
import React from "react";
import Fruit from "./Fruit.js";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>과일의 종류</p>
        <Fruit />
      </div>
    );
  }
}

export default App;

// Fruit.js
import React from "react";

class Fruit extends React.Component {
  render() {
    return (
      <ul>
        <li>딸기</li>
        <li>망고</li>
        <li>자몽</li>
        <li>레몬</li>
        <li>포도</li>
      </ul>
    );
  }
}

export default Fruit;
```

```
import React from "react";

class Fruit extends React.Component {
  render() {
    const fruits = ["딸기", "망고", "자몽", "레몬", "포도"];
    const fruitList = fruits.map(fruit => <li>{fruit}</li>);

    return <ul>{fruitList}</ul>;
  }
}

export default Fruit;
```

```
import React from "react";

class Fruit extends React.Component {
  render() {
    const fruits = ["딸기", "망고", "자몽", "레몬", "포도"];
    const fruitList = fruits.map((fruit, index) => (
      <li key={index}>{fruit}</li>
    ));

    return <ul>{fruitList}</ul>;
  }
}

export default Fruit;
```

```
import React from "react";

class Fruit extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      fruits: ["딸기", "망고", "자몽", "레몬", "포도"]
    };
  }

  render() {
    const fruitList = this.state.fruits.map((fruit, index) => (
      <li key={index}>{fruit}</li>
    ));

    return <ul>{fruitList}</ul>;
  }
}

export default Fruit;
```










