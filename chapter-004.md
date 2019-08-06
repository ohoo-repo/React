---
title: 컴포넌트
seoTitle: 컴포넌트 | ohoo
seoDescription: description for search engines
isFree: true
---



```
// 컴포넌트
const Hello = () => {
  return <p>Hello!</p>;
};
      
ReactDOM.render(
  <div>
    <Hello />
    <Hello />
    <Hello />
  </div>,
  document.getElementById("root")
);
```

## 컴포넌트
* 컴포넌트의 정의

컴포넌트(Component)란 UI를 독립적이고 재사용이 가능한 부분으로 나눈 것을 말합니다. 단순히 디자인적으로만 분할한 것이 아니고 컴포넌트마다 각자의 기능을 갖고 있으며 각각의 컴포넌트가 결합하여 하나의 유기적인 프로그램을 만듭니다. 

* 종류

컴포넌트는 함수형 컴포넌트와 class형 컴포넌트가 있습니다. 함수형 컴포넌트와 class형 컴포넌트의 차이점은 class형 컴포넌트에 상태(State)가 존재한다는 점입니다.


## 함수형 컴포넌트와 class형 컴포넌트
함수형 컴포넌트와 class형 컴포넌트 중 어느 것을 사용해도 결과는 동일함


```
// 함수형 컴포넌트
const Hello = () => {
  return <p>Hello!</p>;
};
```
  
```
// class형 컴포넌트
class Hello extends React.Component {
  render() {
    return <p>Hello!</p>;
  }
}
```





## 컴포넌트 추출
HTML 코드와 자바스크립트 코드를 분리. 그리고 더 많은 노드 모듈 필요.
create-react-app을 사용하자

```
const Hello = () => {
  return <p>Hello!</p>;
};

const App = () => {
  return (
    <div>
      <Hello />
      <Hello />
      <Hello />
    </div>
  );
};

ReactDOM.render(<App />, document.getElementById("root"));
```



## UI 표현하기
```
|-- App.js
|  |-- Header.js
|  |-- Main.js
|  |  |-- 
|  |  |-- 
|  |-- Footer.js
```

```
// App.js
import React from "react";
import Header from "./Header.js";
import Main from "./Main.js";
import Footer from "./Footer.js";

class App extends React.Component {
  render() {
    return (
      <div>
        <Header/>
        <Main/>
        <Footer/>
      </div>
    );
  }
}

export default App;

// Header.js
import React from "react";

class Header extends React.Component {
  render() {
    return (
      <p>Header</p>
    );
  }
}

export default Header;

// Main.js
import React from "react";

class Main extends React.Component {
  render() {
    return (
      <p>Main</p>
    );
  }
}

export default Main;

// Footer.js
import React from "react";

class Footer extends React.Component {
  render() {
    return (
      <p>Footer</p>
    );
  }
}

export default Footer;
```





