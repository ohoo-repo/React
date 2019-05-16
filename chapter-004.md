---
title: 컴포넌트
seoTitle: 컴포넌트 | ohoo
seoDescription: description for search engines
isFree: true
---


```
ReactDOM.render(
  <p>Hello world!</p>
  <p>Hello world!</p>
  <p>Hello world!</p>, 
  document.getElementById('root') 
)
```

만일 동일한 리액트 엘리먼트를 하나 더 표시하고 싶다면 기존의 p 엘리먼트 밑에 또 다른 p 엘리먼트를 추가해줍니다. 이러한 경우 화면에 표시되던 문장이 사라지게 되는데 이는 오류가 발생했기 때문입니다. 

```
ReactDOM.render(
  <div>
    <p>Hello world!</p>
    <p>Hello world!</p>
    <p>Hello world!</p>
  </div>, 
  document.getElementById('root') 
)
```

이 문제를 해결하기 위해서는 p 엘리먼트들을 div 엘리먼트로 감싸주면 됩니다. 이는 HTML과 다르게 리액트에서는 반드시 하나의 엘리먼트로 나머지 엘리먼트들을 감싸주어야 하기 때문입니다. 

## 엘리먼트의 반복

이번에는 p 엘리먼트의 내용을 변경한다고 가정해봅시다. "Hello world!"를 "Hello!"로 변경하려면 모든 엘리먼트를 하나하나 수정해주어야 합니다. 위의 예제에서는 엘리먼트가 3개이지만 만일 100개의 앨리먼트로 이뤄진 프로그램이라면 이를 모두 수정하는 일은 매우 번거로운 작업이 될 것입니다. 이 문제를 해결하는 방법은 p 엘리먼트의 내용을 변수로 처리하는 방법과 컴포넌트를 사용하는 방법이 있습니다. 


동일한 내용을 표시하는 엘리먼트가 여러 개 있다고 생각해봅시다. 이 때 만일 "Hello world!" 대신 "안녕하세요!"를 나타내려고 한다면 모든 엘리먼트를 수정해야 한다는 단점이 있습니다. 이를 해결하는 방법은 2가지가 있는데 하나는 변수를 사용하는 것이고 다른 하나는 컴포넌트를 사용하는 것입니다.

```
// 변수
const hello = "Hello!";

ReactDOM.render(
  <div>
    <p>{hello}</p>
    <p>{hello}</p>
    <p>{hello}</p>
  </div>,
  document.getElementById("root")
);
```

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





