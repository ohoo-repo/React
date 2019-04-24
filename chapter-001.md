---
title: 리액트
seoTitle: 리액트 | ohoo
seoDescription: description for search engines
isFree: true
---

## 리액트란?
[React](https://reactjs.org)는 페이스북이 자바스크립트로 만든 UI(User Interface) 라이브러리입니다. 공식 문서에 따르면 리액트는 컴포넌트를 기반으로 하고 있는데 컴포넌트(Component)란 UI를 구성하고 있는 기능적인 개체들로 뷰(시각적인 부분)와 동작(로직)이 조합되어 있는 것을 말합니다.

가상 DOM은 브라우저에 내장되어 있는 DOM과 별도로

리액트는 성능과 브라우저 간의 호환성을 위해 브라우저에 독립적인 DOM을 사용합니다.

* 프레임워크와 라이브러리



## 간단한 프로그램
```
<!DOCTYPE>
<html>

  <head>
    <meta charset="utf-8" />
    <script src="https://unpkg.com/react@15/dist/react.min.js"></script>
    <script src="https://unpkg.com/react-dom@15/dist/react-dom.min.js"></script>
  </head>

  <body>
    <div id="root"></div>
    <script type="text/javascript">
      ReactDOM.render(
        React.createElement('p', null, 'Hello world!'),
        document.getElementById('root')
      )
    </script>
  </body>

</html>
```

## 가상 DOM
```
<div id="root"></div>
```

이것은 "root" DOM 노드이며 이 노드 안의 모든 것들은 React DOM에 의해 관리됩니다. 
```
ReactDOM.render(React 엘리먼트, document.getElementById('root'));
```

React 엘리먼트를 "root" DOM 노드에 렌더링하려면 React 엘리먼트와 "root" DOM 노드를 ReactDOM.render() 메서드에 전달합니다.

React DOM은 React 엘리먼트와 일치하도록 DOM을 업데이트합니다.

```
ReactDOM.render(element, container[, callback])
```

'React DOM(가상 DOM)을 만들어서 렌더링한다'






## create-react-app

```
// create-react-app 설치
npm install create-react-app
```

```
npx create-react-app 디렉터리이름
cd my-app
npm start
```

App.js를 수정하고 command+S를 누르면 수정된 부분이 화면에 반영됨
