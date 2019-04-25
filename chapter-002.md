---
title: 가상 DOM과 엘리먼트
seoTitle: 엘리먼트 | ohoo
seoDescription: description for search engines
isFree: true
---


```
<!DOCTYPE>
<html>

  <head>
    <meta charset="utf-8" />
    <script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
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

리액트와 리액트 DOM을 사용하려면 head의 script 태그로 자바스크립트 파일을 읽어 들이고 body의 script 태그에 리액트 프로그램을 작성하면 됩니다. 위의 코드에서는 ReactDOM.render()와 React.createElement()를 사용하여 "Hello world!"라는 문장을 출력하는 간단한 프로그램을 만들어 보았습니다.  

HTML과 자바스크립트 코드를 제외
React.createElement()는 자바스크립트에서 DOM에 대해 배울 때 보았던 document.createElement()와 비슷하다고 생각하면 됩니다. 하지만 document.createElement()와 달리 React.createElement()는 가상의 DOM 트리를 생성합니다. 

ReactDOM.render()는 

## 가상 DOM
DOM이란 Document Object Model의 줄임말로 HTML, XML, SVG 같은 문서를 제어하는 API를 말합니다. DOM은 이 문서들을 DOM 트리 
브라우저의 DOM과 다르게 리액트 DOM은 가상의 DOM(virtual DOM)입니다. 코드를 변경할 경우 DOM 트리를 바로 

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

React 엘리먼트는 리액트 앱을 구성하는 가장 작은 빌딩 블럭이며 이 엘리먼트들이 모여 컴포넌트를 구성합니다. 

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


