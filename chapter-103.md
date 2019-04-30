---
title: 간단한 예제:Todo 앱
seoTitle: 간단한 예제:Todo 앱 | React | ohoo
seoDescription: description for search engines
isFree: true
---


```
npx create-react-app todo
cd todo
npm start
```

```
// App.js
import React from "react";

class App extends React.Component {
  render() {
    return <div>Todo 앱 만들기</div>;
  }
}

export default App;

// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

App.js 파일의 코드를 위와 같이 변경하고 다음 3개의 파일을 삭제함

* App.css
* logo.svg
* serviceWorker.js



```
// index.css
background-color: #eeeeee;
```

index.css 파일의 body에 background-color 추가




```
// App.js
```

```
// TodoInput.js
```

```
// TodoList.js
```

```
// TodoItem.js
```
