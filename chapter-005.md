---
title: create-react-app
seoTitle: create-react-app | ohoo
seoDescription: description for search engines
isFree: true
---


실제로 프로그램을 개발할 때는 리액트, 리액트 DOM, 바벨 이외에도 많은 도구들이 필요한데 이러한 도구들을 하나씩 따로 설치하고 설정하는 것은 매우 번거로운 일입니다. 그러므로 페이스북에서는 리액트 개발을 조금 더 간편하게 할 수 있도록 create-react-app이라는 툴체인을 제공합니다.

create-react-app은 개발 뿐만 아니라 리액트를 배우고 연습하는데도 매우 유용하므로 create-react-app를 설치하는 방법에 대해 설명해보겠습니다.

## 개발 환경 설정하기
```
// create-react-app 설치 
npm install -g create-react-app 
```

create-react-app을 설치합니다. -g는 전역 모듈로 설치하라는 의미입니다. create-react-app을 모든 디렉토리에서 사용할 수 있도록 전역 모듈로 설치하는 것이 좋습니다.
```
// 디렉토리 생성
mkdir 디렉토리이름 
```

우선 디렉토리를 만들어 줍니다. 리액트를 배우고 연습하는 과정에 생성되는 여러 개의 프로그램들을 하나로 관리하기 위한 목적이므로 이 과정은 생략해도 괜찮습니다. 
```
// 애플리케이션 생성
npx create-react-app 애플리케이션이름
```

npx create-react-app hello 명령을 실행하여 애플리케이션을 생성합니다. 모듈이 설치되어야 하므로 약간의 시간이 소요됩니다. 설치가 완료된 애플리케이션의 구성을 살펴보면 다음과 같습니다.

```
hello
|-- node_dules
|-- public
|  |-- favicon.ico
|  |-- index.html
|  |-- manifest.json
|-- src
|  |-- App.css
|  |-- App.js
|  |-- App.test.js
|  |-- index.css
|  |-- index.js
|  |-- logo.svg
|  |-- registerServiceWorker.js
|-- .gitignore
|-- package.json
|-- README.md
```

* node_dules: 설치된 노드 모듈이 들어있는 디렉토리
* public: 
* src: 애플리케이션의 소스코드
* .gitignore
* package.json
* README.md

```
cd 디렉토리이름/애플리케이션이름 혹은 cd 애플리케이션이름
```
```
// 개발 서버 시작하기
npm start
```





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



