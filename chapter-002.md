---
title: 가상 DOM과 엘리먼트
seoTitle: 가상 DOM과 엘리먼트 | ohoo
seoDescription: description for search engines
isFree: true
---


기존의 웹 앱은 HTML, CSS로 기본적인 코드를 작성한 다음 자바스크립트로 원하는 부분을 수정하는 방식으로 만들어 졌습니다. 이러한 일은 DOM이라는 개념이 있기 때문에 가능할 수 있었는데 실제로 DOM을 조작하면 전체 렌더 트리를 새로 생성하므로 성능적인 면에서는 비효율적인 방식이었습니다. 그러므로 리액트는 가상 DOM이라는 개념을 도입하여 매번 DOM을 조작하지 않고 가상 DOM과 실제 DOM의 차이가 있는 부분만 업그레이드하는 방식으로 변경했습니다. 이러한 방식은 기존에 DOM의 조작을 최소화해야 했던 것과 다르게 얼마든지 DOM 조작을 자유롭게 할 수 있도록 하였습니다. 이로 인해 과거에 HTML로 작성되던 많은 부분이 자바스크립트로 대체되었습니다.

이제 가상 DOM을 사용하는 방식에 대해 배워보겠습니다.

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


```
<div id="root"></div>
```

이것은 "root" DOM 노드이며 이 노드 안의 모든 것들은 React DOM에 의해 관리됩니다. 


## virtual DOM 생성하기
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

#### 리액트 엘리먼트 중첩

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

리액트 엘리먼트는 HTML 엘리먼트와 같이 중첩이 가능합니다. 위의 코드 박스는 p 엘리먼트를 div 엘리먼트로 감싼 것을 나타냅니다. 이 예제에서는 전부 2개의 엘리먼트 밖에 없지만 실제로 프로그램을 작성하게 되면 이보다 훨씬 많은 수의 


















