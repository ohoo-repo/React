---
title: 가상 DOM과 엘리먼트
seoTitle: 가상 DOM과 엘리먼트 | ohoo
seoDescription: description for search engines
isFree: true
---


DOM(Document Object Model)이란 객체 구조를 생성하여 문서에 접근하거나 문서를 제어하는 API를 말합니다. 예를 들면 자바스크립트로 HTML 문서를 제어하려면 HTML 문서에 접근해야 하는데 이들은 서로 다른 언어이므로 직접적으로 접근할 수가 없습니다. 그러므로 DOM은 이 문서를 분석해서 문서의 구조와 동일한 객체 구조를 생성합니다. 이 객체 구조는 나뭇가지가 뻣어있는 모습을 갖고 있기 때문에 DOM 트리(tree)라고 부르며 DOM 트리를 구성하는 각각의 객체들은 노드(node)라고 부릅니다.

브라우저 DOM과 다르게 리액트 DOM은 가상의 DOM(virtual DOM)입니다. 코드를 변경할 경우 브라우저 DOM 트리가 바로 변경되는 것이 아니라 가상의 DOM을 변경시킨다음 가상의 DOM과 일치하도록 실제 DOM(브라우저 DOM)을 업데이트합니다.




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

리액트와 리액트 DOM을 사용하려면 head의 script 태그로 자바스크립트 파일을 읽어 들이고 body의 script 태그에 리액트 프로그램을 작성하면 됩니다. 위의 코드에서는 "Hello world!"라는 문장을 출력하는 간단한 프로그램을 만들어 보았습니다.  

전체 코드에서 HTML과 자바스크립트 코드를 제외하고 나면 React.createElement() 메서드와 ReactDOM.render() 메서드 남는데 React.createElement()는 가상의 DOM 트리를 **생성**하고 ReactDOM.render()는 생성된 DOM 트리를 **렌더링**하는 역할을 합니다.




```
<div id="root"></div>
```

이것은 "root" DOM 노드이며 이 노드 안의 모든 것들은 React DOM에 의해 관리됩니다. 


## DOM 트리 생성하기
```
React.createElement(type, [props], [...children])
```

리액트에서는 DOM 트리를 생성하기 위해 React.createElement()를 사용합니다. React.createElement()의 첫 번째 매개변수로는 문자열로 된 HTML 태그와 리액트 컴포넌트가 사용될 수 있으며 리액트 컴포넌트는

(함수 또는 class), React.Fragment 컴포넌트가 들어갈 수 있습니다.


#### 문자열로 된 HTML 태그
```
// p 엘리먼트 생성하기
ReactDOM.render(
  React.createElement('p', null, 'Hello world!'),
  document.getElementById('root')
)
```

React 엘리먼트는 리액트 앱을 구성하는 가장 작은 빌딩 블럭이며 이 엘리먼트들이 모여 컴포넌트를 구성합니다. 

```
// 브라우저 DOM
document.createElement('엘리먼트 이름')
document.createAttribute('속성 이름')
document.createTextNode('텍스트')
```

React.createElement()는 브라우저 DOM의 document.createElement()와 유사하지만 약간의 차이가 있습니다. 

#### 리액트 컴포넌트
```
// 컴포넌트 생성하기
class App extends React.Component {
  render() {
    return(
      React.createElement('p', null, 'Hello world!')
    )
  }
}

ReactDOM.render(
  React.createElement(App, null),
  document.getElementById('root')
)
```




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




## DOM 트리 렌더링하기

```
ReactDOM.render(React 엘리먼트, document.getElementById('root'));
```

React 엘리먼트를 "root" DOM 노드에 렌더링하려면 React 엘리먼트와 "root" DOM 노드를 ReactDOM.render() 메서드에 전달합니다.

React DOM은 React 엘리먼트와 일치하도록 DOM을 업데이트합니다.

```
ReactDOM.render(element, container[, callback])
```

'React DOM(가상 DOM)을 만들어서 렌더링한다'

