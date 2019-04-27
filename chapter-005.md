---
title: 컴포넌트
seoTitle: 컴포넌트 | ohoo
seoDescription: description for search engines
isFree: true
---


## 컴포넌트란?
컴포넌트(Component)란 UI를 독립적이고 재사용이 가능한 부분으로 나눈 것을 말합니다. 단순히 디자인적으로만 분할한 것이 아니고 컴포넌트마다 각자의 기능을 갖고 있음. 각각의 컴포넌트가 결합하여 하나의 유기적인 프로그램을 만듬  

## 컴포넌트 
```
// React 엘리먼트
ReactDOM.render(
  <p>Hello world!</p>, 
  document.getElementById('root') 
)

// React 컴포넌트(함수형)
const helloWorld = () => {
  return <p>Hello world!</p>;
}

ReactDOM.render(
  helloWorld(), 
  document.getElementById('root') 
)

// React 컴포넌트(class형)
class HelloWorld extends React.Component{
  render() {
    return (
      <p>Hello world!</p>
    )
  }
}

ReactDOM.render(
  <HelloWorld/>, 
  document.getElementById('root') 
)
```

함수형 컴포넌트와 class형 컴포넌트의 차이점은 class형 컴포넌트에 상태(State)가 존재한다는 점입니다.




## 함수형 컴포넌트와 class형 컴포넌트
#### 함수형 컴포넌트
```
// App.js

import React from "react";

const Hello = props => {
  return <div>안녕하세요. {props.name}님</div>;
};

function App() {
  return (
    <div>
      <Hello name="나제영" />
      <Hello name="나제일" />
      <Hello name="나제이" />
    </div>
  );
}

export default App;
```

#### class형 컴포넌트    
```
// App.js

import React from "react";

const Hello = props => {
  return <div>안녕하세요. {props.name}님</div>;
};

class App extends React.Component {
  render() {
    return (
      <div>
        <Hello name="나이재" />
        <Hello name="선민식" />
        <Hello name="한소금" />
      </div>
    );
  }
}

export default App;
```

## props
```
import React from "react";

const Hello = props => {
  return <div>안녕하세요. {props.name}님</div>;
};

const Greeting = props => {
  return (
    <div>
      <div>인사하기</div>
      {props.children}
    </div>
  );
};

function App() {
  return (
    <Greeting>
      <Hello name="나이재" />
      <Hello name="선민식" />
      <Hello name="한소금" />
    </Greeting>
  );
}

export default App;
```


## propTypes
props에는 다양한 데이터 타입이 사용될 수 있는데 애플리케이션의 규모가 커지면 이를 관리하기 어려우므로 만일 다른 타입의 데이터가 전달된다면 코드를 작성하거나 실행할 때 이를 알려주는 것이 바람직함

```
npm i prop-types
```

```
Hello.propTypes = {
  name: PropTypes.string
}
```

```
// 속성이름만 되는지 다른 것도 되는지는 점차 살펴보자
컴포넌트이름.propTypes = {
  속성이름: PropTypes.string,
  속성이름: PropTypes.number,
  속성이름: PropTypes.boolean,
  속성이름: PropTypes.array,
  속성이름: PropTypes.object,
  속성이름: PropTypes.function,
  속성이름: PropTypes.symbol,
}
```

