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

## 가상 DOM

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

```
ReactDOM.render(element, container[, callback])
```

```
// 리액트 엘리먼트 생성하기
React.createElement(type, [props], [...children])
```

type은 문자열로 된 태그 이름, 리액트 컴포넌트(함수 또는 class), React.Fragment 컴포넌트가 될 수 있음.

```
// 중첩
<script type="text/javascript">
  ReactDOM.render(
    React.createElement('div', null,
      React.createElement('p', null, 'Hello world!')
    ),
    document.getElementById('root')
  )
</script>
```

```
<script type="text/javascript">
  ReactDOM.render(
    React.createElement('div', null,
      React.createElement('p', null, 'Hello world!'),
      React.createElement('p', null, 'Hello world!'),
      React.createElement('p', null, 'Hello world!')
    ),
    document.getElementById('root')
  )
</script>
```







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
