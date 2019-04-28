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


```
import React from "react";

const App = () => {
  return (
    <div>
      <p>Hello world!</p>
    </div>
  );
}

export default App;
```

함수형 컴포넌트는 화살표 함수를 사용해서 표현할 수도 있습니다.


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





## 컴포넌트의 중첩?
```
import React from "react";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>Hello world!</p>
        <p>Hello world!</p>
        <p>Hello world!</p>
        <p>Hello world!</p>
        <p>Hello world!</p>
      </div>
    );
  }
}

export default App;
```

동일한 내용을 표시하는 엘리먼트가 여러 개 있다고 생각해봅시다. 이 때 만일 "Hello world!" 대신 "안녕하세요!"를 나타내려고 한다면 모든 엘리먼트를 수정해야 한다는 단점이 있습니다. 이를 해결하는 방법은 2가지가 있는데 하나는 변수를 사용하는 것이고 다른 하나는 컴포넌트를 사용하는 것입니다.

#### 변수
```
import React from "react";

const hello = "Hello world!";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>{hello}</p>
        <p>{hello}</p>
        <p>{hello}</p>
        <p>{hello}</p>
        <p>{hello}</p>
      </div>
    );
  }
}

export default App;
```

#### 컴포넌트
```
// App.js
import React from "react";
import Hello from "./Hello.js";

class App extends React.Component {
  render() {
    return (
      <div>
        <Hello/>
        <Hello/>
        <Hello/>
        <Hello/>
        <Hello/>
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
      <p>Hello world!</p>
    );
  }
}

export default Hello;
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





