---
title: Props
seoTitle: Props | ohoo
seoDescription: description for search engines
isFree: true
---


```
import React from "react";

function App() {
  return (
    <div>
      <p>Hello, 나제한!</p>
      <p>Hello, 나제인!</p>
      <p>Hello, 나제아!</p>
      <p>Hello, 나제이!</p>
      <p>Hello, 나제준!</p>
    </div>
  );
}

export default App;
```

##  함수형 컴포넌트와 class형 컴포넌트
#### 함수형 컴포넌트
```
import React from "react";

function Hello(props) {
  return <p>Hello, {props.name}!</p>;
}

function App() {
  return (
    <div>
      <Hello name="나제한" />
      <Hello name="나제인" />
      <Hello name="나제아" />
      <Hello name="나제이" />
      <Hello name="나제준" />
    </div>
  );
}

export default App;
```

#### class형 컴포넌트
```
// App.js
import React from "react";
import Hello from "./Hello.js";

class App extends React.Component {
  render() {
    return (
      <div>
        <Hello name="나제이"/>
        <Hello name="나제일"/>
        <Hello name="나제준"/>
        <Hello name="나제현"/>
        <Hello name="나제환"/>
      </div>
    );
  }
}

export default App;

// Hello.js
import React from "react";

class Hello extends React.Component {
  render() {
    return (
      <p>Hello {this.props.name}!</p>
    );
  }
}

export default Hello;
```


## props를 변수로 나타내기
```
import React from "react";

function Hello(props) {
  return <p>Hello, {props.name}!</p>;
}

const name = "나제한";

function App() {
  return (
    <div>
      <Hello name={name} />
      <Hello name="나제인" />
      <Hello name="나제아" />
    </div>
  );
}

export default App;
```

## props이 여러 개일 때
```
import React from "react";

function Hello(props) {
  return <p>Hello, {props.name}!</p>;
}

const person = {
  name: "나제한"
};

function App() {
  return (
    <div>
      <Hello name={person.name} />
      <Hello name="나제인" />
      <Hello name="나제아" />
    </div>
  );
}

export default App;
```
```
import React from "react";

function Hello(props) {
  return (
    <div>
      <p>Hello, {props.name}!</p>
      <p>저는 {props.age}살입니다.</p>
      <p>저는 {props.title}의 저자입니다.</p>
    </div>
  );
}

const person = {
  name: "나제한",
  age: 28,
  book: {
    title: "하버드가기"
  }
};

function App() {
  return (
    <div>
      <Hello name={person.name} age={person.age} title={person.book.title} />
      <Hello name="나제인" />
      <Hello name="나제아" />
    </div>
  );
}

export default App;
```






## props의 값
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

props의 값으로 문자열, 숫자, 변수 뿐만 아니라 불린, 배열, 객체, 함수도 가능함.
추가로 조금 특별한 props 값이 있는데 바로 children임.




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
