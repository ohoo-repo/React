---
title: Hook 소개
seoTitle: Hook 소개 | React | ohoo
seoDescription: description for search engines
isFree: true
---

Hook은 리액트 버전 16.8에 새로 추가되었습니다. Hook을 사용하면 class를 작성하지 않고 state와 다른 리액트의 기능들을 사용할 수 있습니다.
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

useState는 Hook에서 처음 배우게 될 함수입니다. 위의 예시는 단지 맛보기에 불과하므로 아직 이해가 되지 않더라도 걱정하지 마세요.

여러분은 다음 페이지에서부터 Hook에 대해 배우게 될 것입니다. 이번 페이지에서는 리액트에서 Hook을 사용해야 하는 이유와 Hook을 사용해 훌륭한 애플리케이션을 만드는 방법에 대해 배워볼 것입니다.


## Video Introduction
2018년 리액트 컴퍼런스에서 Sophie Alpert와 Dan Abramov는 Hook을 소개했고 뒤이어 Ryan Florence는 Hook을 사용해 애플리케이션을 리팩토링하는 방법에 대해 설명했습니다.


## No Breaking Changes





















