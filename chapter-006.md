---
title: 컴포넌트
seoTitle: 컴포넌트 | ohoo
seoDescription: description for search engines
isFree: true
---



컴포넌트(Component)란 UI를 독립적이고 재사용이 가능한 부분으로 나눈 것을 말합니다. 단순히 디자인적으로만 분할한 것이 아니고 컴포넌트마다 각자의 기능을 갖고 있으며 각각의 컴포넌트가 결합하여 하나의 유기적인 프로그램을 만듭니다. 

컴포넌트는 함수형 컴포넌트와 class형 컴포넌트가 있습니다. 함수형 컴포넌트와 class형 컴포넌트의 차이점은 class형 컴포넌트에 상태(State)가 존재한다는 점입니다.


## 함수형 컴포넌트와 class형 컴포넌트
#### 함수형 컴포넌트
```
// App.js

import React from "react";

function App() {
  return (
    <div>
      <p>Hello world!</p>
    </div>
  );
}

export default App;
```

#### class형 컴포넌트    
```
// App.js

import React from "react";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>Hello world!</p>
      </div>
    );
  }
}

export default App;
```





#### 컴포넌트의 중첩
```
// App.js

import React from "react";

const Hello = props => {
  return <div>안녕하세요.</div>;
};

class App extends React.Component {
  render() {
    return (
      <div>
        <Hello/>
        <Hello/>
        <Hello/>
      </div>
    );
  }
}

export default App;
```

