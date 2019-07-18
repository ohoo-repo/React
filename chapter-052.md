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

useState는 Hook입니다. 우리는 함수형 컴포넌트에 내부 상태를 추가하기 위해 useState를 호출합니다. 이 상태(state)는 컴포넌트가 다시 렌더링되어도 유지됩니다. useState은 현재의 상태 값과 그것을 업데이트 하는 함수를 반환합니다.
