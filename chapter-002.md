---
title: JSX
seoTitle: JSX | ohoo
seoDescription: description for search engines
isFree: true
---


리액트 엘리먼트를 생성할 때마다 React.createElement를 반복적으로 적어야 하는 불편함.
JSX를 쓰자!

JSX란 자바스크립트의 문법을 확장한 을 말합니다. 리액트를 사용한다고 해서 반드시 JSX를 사용해야 하는 것은 아니지만 JSX를 사용하면 좀 더 효율적으로 프로그래밍을 할 수 있습니다. 

```
// 자바스크립트
ReactDOM.render(
  React.createElement('p', null, 'Hello world!'),
  document.getElementById('root')
)

// JSX
ReactDOM.render(
  <p>Hello world!</p>, 
  document.getElementById('root') 
)
```

JSX는 언뜻 보면 HTML같이 생겼으며 HTML과 유사한 점도 많지만 

```
<!DOCTYPE>
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
      ReactDOM.render(
        <p>Hello world!</p>, 
        document.getElementById('root') 
      )
    </script>
  </body>

</html>
```

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.38/browser.min.js"></script>
```

```
<script type="text/babel">...</script>
```

```
// 중첩
<script type="text/babel">
  ReactDOM.render(
    <div>
      <p>Hello world!</p>
    </div>, 
    document.getElementById('root') 
  )
</script>
```

```
<script type="text/babel">
  ReactDOM.render(
    <div>
      <p>Hello world!</p>
      <p>Hello world!</p>
      <p>Hello world!</p>
    </div>, 
    document.getElementById('root') 
  )
</script>
```

```
<script type="text/babel">
 const hello = "Hello world!"
  ReactDOM.render(
  <div>
    <p>{hello} 1</p>
    <p>{hello} 2</p>
    <p>{hello} 3</p>
  </div>, document.getElementById('root') )
</script>
```



JSX는 자바스크립트의 변형된 형태이므로 JSX로 작성된 프로그램을 브라우저에서 렌더링하려면 JSX를 자바스크립트로 바꿔주는 트랜스파일러가 필요합니다. 






