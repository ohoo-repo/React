---
title: create-react-app
seoTitle: create-react-app | ohoo
seoDescription: description for search engines
isFree: true
---


## 프로젝트 생성하기
```
mkdir 디렉토리이름
npx create-react-app 프로젝트이름
cd 디렉토리이름/프로젝트이름
npm start
```

그냥 설치하면 최상위 폴더의 하위 폴더로 설치되므로 연습용 폴더를 만든 다음 설치하는 것을 추천함.

바벨이랑 웹팩이 모두 설치되어 있으므로 신경쓸 것이 없어


```
<!DOCTYPE >
<html>
  <head>
    <meta charset="utf-8" />
    <script src="https://unpkg.com/react@15/dist/react.min.js"></script>
    <script src="https://unpkg.com/react-dom@15/dist/react-dom.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.38/browser.min.js"></script>
  </head>

  <body>
    <div id="root"></div>
    <script type="text/babel">
      class App extends React.Component {
        render() {
          return (
            <div>
              <p>Hello world!</p>
              <p>Hello world!</p>
            </div>
          );
        }
      }
      ReactDOM.render(<App />, document.getElementById("root"));
    </script>
  </body>
</html>
```

```
// App.js(함수형)
import React from "react";

const App = () => {
  return (
    <div>
      <p>Hello World!</p>
      <p>Hello World!</p>
    </div>
  );
};

export default App;
```

```
// App.js(class형)
import React from "react";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>Hello World!</p>
        <p>Hello World!</p>
      </div>
    );
  }
}

export default App;
```



