---
title: Hook 살펴보기
seoTitle: Hook 살펴보기 | React | ohoo
seoDescription: description for search engines
isFree: true
---

Hook은 이전 버전과 호환됩니다. 이 페이지는 기존의 리액트 사용자들에게 Hook에 대한 간단한 소개를 제공하며 이 소개는 빠르게 진행될 것입니다. 혼동되는 부분은 노락색 박스를 참고하면 됩니다.


## State Hook
이 예시는 버튼을 클릭하면 값이 증가하는 counter를 렌더링합니다.
```
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

useState는 Hook입니다. 우리는 함수형 컴포넌트에 내부 상태를 추가하기 위해 useState를 호출합니다. 이 상태(state)는 컴포넌트가 다시 렌더링되어도 유지됩니다. useState은 현재 상태의 값과 그것을 업데이트 하는 함수를 하나의 쌍으로 반환합니다. 여러분은 이 함수를 이벤트 핸들러 혹은 다른 곳에서 호출할 수 있습니다. 그것은 기존의 상태와 새로운 상태를 합치지 않는다는 점을 제외하고는 class의 this.setState과 비슷합니다.

useState의 유일한 인수는 초기 상태입니다. counter는 0부터 시작하기 때문에 위의 예시에서 초기 상태는 0입니다. this.state와 다르게 여기에서 상태는 객체일 필요가 없습니다. 필요하다면 객체를 사용해도 됩니다. 초기 상태 인수는 첫 번째 렌더링에서만 사용됩니다.


#### 여러 상태 변수 선언하기
여러분은 하나의 컴포넌트에서 여러 개의 State Hook을 사용할 수 있습니다.
```
function ExampleWithManyStates() {
  // Declare multiple state variables!
  const [age, setAge] = useState(42);
  const [fruit, setFruit] = useState('banana');
  const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
  // ...
}
```

배열 비구조화 구문은 useState을 호출하여 선언한 상태 변수에 다른 이름들을 제공합니다. 이 이름들은 useState API의 일부가 아닙니다. 대신 리액트는 여러분이 useState을 여러 번 호출하면 렌더링될 때마다 동일한 순서로 그것을 호출합니다. 왜 이렇게 동작하는지 언제 이것이 유용한지에 대해 나중에 알아보겠습니다.


#### 근데 Hook은 무엇인가요?




-----

* 내장 Hook
  * useState
  * useEffect
  * useContext
  * useReducer
* 커스텀 Hook







































