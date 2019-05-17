---
title: 리스트와 키
seoTitle: 리스트와 키 | React | ohoo
seoDescription: description for search engines
isFree: true
---


map() 함수


```
import React from "react";

const Hello = props => {
  return <p>Hello! {props.customer}</p>;
};

const App = () => {
  return (
    <div>
      <Hello customer="나제일" />
      <Hello customer="나제준" />
      <Hello customer="나제한" />
    </div>
  );
};

export default App;
```


```
import React from "react";

const Hello = props => {
  return <p>Hello! {props.customer}</p>;
};

const customer = "나제일";

const App = () => {
  return (
    <div>
      <Hello customer={customer} />
      <Hello customer="나제준" />
      <Hello customer="나제한" />
    </div>
  );
};

export default App;
```

속성을 변수로 나타낼 수 있음

```
import React from "react";

const Hello = props => {
  return <p>Hello! {props.customer}</p>;
};

const customers = ["나제일", "나제준", "나제한"];

const App = () => {
  return (
    <div>
      {customers.map(customer => (
        <Hello customer={customer} />
      ))}
    </div>
  );
};

export default App;
```

배열과 map() 함수를 사용하면 됨

콘솔 창을 열어보면 다음과 같은 메세지가 표시됨
```
Warning: Each child in a list should have a unique "key" prop.
```

key 속성을 넣어주라는 이야기
name 속성 위에 key 속성을 추가하자

키(Key)는 어떤 항목이 변경, 추가, 제거되었는지 리액트가 식별할 수 있게 도와주는 역할을 합니다. 배열 내의 엘리먼트를 식별할 수 있도록 엘리먼트에 키 속성을 추가해야 합니다.

```
{customers.map(customer => (
  <Hello customer={customer} key={index}/>
))}
```

#### 키를 추가하는 방법 3가지

* index
*
*

```
import React from "react";

const Hello = props => {
  return <p>Hello! {props.customer}</p>;
};

const customers = [
  {
    id: 1,
    name: "나제일"
  },
  {
    id: 2,
    name: "나제준"
  },
  {
    id: 3,
    name: "나제한"
  }
];

const App = () => {
  return (
    <div>
      {customers.map(customer => (
        <Hello customer={customer.name} key={customer.id} />
      ))}
    </div>
  );
};

export default App;
```







