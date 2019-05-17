---
title: 라이프사이클
seoTitle: 라이프사이클(Lifecycle) | React | ohoo
seoDescription: description for search engines
isFree: true
---


라이프사이클이란 표현 그대로 생애 주기를 말하며 일반적으로 사람이 태어나서 죽는 일련의 과정을 설명하고자 할 때 많이 사용되는 단어입니다. 리액트에서는 컴포넌트가 생성, 갱신, 제거되는 과정을 설명할 때 라이프사이클이라는 표현을 사용하는데 컴포넌트의 라이프사이클은 마운팅, 업데이팅, 언마운팅으로 분류될 수 있습니다. 각각의 단계에 따라서 다음과 같은 메서드들이 존재합니다.

* 마운팅
  * constructor()
  * static getDerivedStateFromProps()
  * render()
  * componentDidMount()
* 업데이팅
  * static getDerivedStateFromProps()
  * shouldComponentUpdate()
  * render()
  * getSnapshotBeforeUpdate()
  * componentDidUpdate()
* 언마운팅

마운팅에 대해 조금 더 자세히 설명하자면 새로운 리액트 컴포넌트, 즉 새롭게 생성된 컴포넌트가 DOM에 추가되는 것을 말합니다. 언마운팅은 마운팅에 반대되는 개념으로 컴포넌트가 DOM에서 제거되는 것을 의미합니다. 마지막으로 업데이팅은 컴포넌트의 속성이나 상태가 변경되는 것을 의미합니다.


초기의 마운트와 그 이후의 업데이트

* 라이프사이클 메서드 : 선택적
  * 컴포넌트 마운트에 의해 호출
  * 컴포넌트에서 다루는 데이터의 변화에 따라 호출
  * 오류 핸들링에 사용됨
  
  
## 마운팅
다음의 메서드들은 컴포넌트의 인스턴스가 생성되어 DOM에 추가될 때 호출됩니다.

#### constructor()
```
constructor(props)
```

리액트에서 constructor는 다음과 같이 2가지 용도로 사용됩니다. 

* 상태의 초깃값 설정
* 이벤트 핸들러 바인딩

constructor는 리액트가 마운트되기 전에 호출되며 constructor를 실행할 때 super(props)를 호출해야 합니다.

```
constructor(props) {
  super(props);
  
  // 상태의 초깃값 설정
  this.state = { 이름: 값 };
  
  // 이벤트 핸들러 바인딩
  this.handleClick = this.handleClick.bind(this);
}
```

#### static getDerivedStateFromProps()
```
static getDerivedStateFromProps(props, state)
```



#### render()
```
render()
```

render 메서드는 class형 컴포넌트의 유일한 필수 메서드입니다.

render 메서드가 호출될 때 render 메서드는 this.props와 this.state를 검토하고 다음 유형 중 하나를 return해야 합니다.

* 리액트 엘리먼트
* 배열과 fragment
* portal
* 문자열과 숫자
* 논리값 혹은 null

render() 함수는 순수 함수여야 합니다. 조금 더 자세히 말하자면 render() 함수는 컴포넌트의 상태를 변경하지 않고, render() 함수가 호출될 때마다 동일한 결과를 return하며, 브라우저와 직접 상호 작용하지 않아야 된다는 것을 의미합니다.

브라우저와 상호 작용하고 싶다면 componentDidMount()나 다른 라이프사이클 메서드에서 그 작업을 수행해야 합니다.

#### componentDidMount()


## 업데이팅


static getDerivedStateFromProps()
shouldComponentUpdate()
render()
getSnapshotBeforeUpdate()
componentDidUpdate()

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

## 언마운팅

componentWillUnmount()


## 오류 처리

static getDerivedStateFromError()
componentDidCatch()


#### componentDidCatch
```
componentDidCatch(error, info)
```







