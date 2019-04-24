---
title: JSX
seoTitle: JSX | ohoo
seoDescription: description for search engines
isFree: true
---


리액트 엘리먼트를 생성할 때마다 React.createElement를 반복적으로 적어야 하는 불편함.
JSX를 쓰자!

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

JSX란? 자바스크립트를 확장한 문법

JSX는 자바스크립트의 변형된 형태이므로 JSX로 작성된 프로그램을 브라우저에서 렌더링하려면 JSX를 자바스크립트로 바꿔주는 트랜스파일러가 필요함. 
