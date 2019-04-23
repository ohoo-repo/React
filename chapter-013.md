---
title: 라이프사이클
seoTitle: 라이프사이클(Lifecycle) | React | ohoo
seoDescription: description for search engines
isFree: true
---

* 라이프사이클 메서드 : 선택적
  * 컴포넌트 마운트에 의해 호출
  * 컴포넌트에서 다루는 데이터의 변화에 따라 호출
  * 오류 핸들링에 사용됨
  
## 컴포넌트 마운트
마운트란 새로운 리액트 컴포넌트가 DOM에 배치되는 것
언마운트란 리액트 컴포넌트가 DOM에서 제거되는 것

* componentWillMount
* componentDidMount
* componentWillUnmount


## 데이터 업데이트
업데이트란 컴포넌트의 속성(Props) 또는 상태(State)가 변경되는 것

* componentWillReceiveProps
* shouldComponentUpdate
* componentWillUpdate
* componentDidUpdate

#### componentWillReceiveProps
```
componentWillReceiveProps(nextProps)
```

#### shouldComponentUpdate
```
shouldComponentUpdate(nextProps, nextState)
```

#### componentWillUpdate
```
componentWillUpdate(nextProps, nextState)
```

#### componentDidUpdate
```
componentDidUpdate(prevProps, prevState)
```



## 오류 처리

* componentDidCatch

#### componentDidCatch
```
componentDidCatch(error, info)
```







