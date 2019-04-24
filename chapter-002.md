---
title: 엘리먼트
seoTitle: 엘리먼트 | ohoo
seoDescription: description for search engines
isFree: true
---

엘리먼트

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


