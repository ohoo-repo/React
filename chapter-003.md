---
title: JSX
seoTitle: JSX | ohoo
seoDescription: description for search engines
isFree: true
---


리액트 엘리먼트를 생성할 때마다 React.createElement를 반복적으로 적어야 하는 것은 매우 불편한 일입니다. 그래서 리액트에서는 자바스크립트의 문법을 확장한 JSX를 사용합니다. 리액트를 사용한다고 해서 반드시 JSX를 사용해야 하는 것은 아니지만 JSX를 사용하면 작성해야 할 코드의 양이 줄어들며 보기에도 깔끔하다는 장점이 있기 때문에 JSX를 사용하기를 추천합니다. 참고로 앞으로의 예제들은 JSX를 사용해서 작성합니다.

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

React.createElement() 메서드를 사용해서 작성했던 코드를 JSX로 다시 작성해 보았습니다. JSX는 얼핏 보면 HTML같이 생겼지만 실제로는 HTML이 아닌 자바스크립트의 변형된 문법일 뿐입니다. 그러므로 HTML과 JSX에는 몇 가지 차이점이 있는데 그 차이점은 다음과 같습니다.

우선 JSX는 속성(attribute)을 작성하는 방법이 다릅니다. HTML에서는 속성을 작성할 때 속성이름 = "속성값" 

속성의 이름은 캐멀케이스 방식으로 적어주어야 합니다.
HTML의 속성 중 대부분이 그대로 사용되지만 그 중에서 class 속성과 for 속성은 자바스크립트의 예약어와 일치하기 때문에 className과 htmlFor로 변경해서 사용합니다.
속성 값의 기본값이 설정된 경우 속성 값을 생략하고 속성 이름만 적을 수 있습니다.
변수 값을 속성 값으로 대신 사용할 수 있습니다. 이 때는 따옴표가 아닌 중괄호로 감싸줍니다.
빈 요소는 반드시 닫아 주어야 합니다.
HTML 태그 이외에 사용자 정의 태그를 사용할 수 있습니다. 우리는 이것을 컴포넌트라고 부르며 컴포넌트에 대한 설명은 해당 부분에서 자세히 하도록 하겠습니다.

* 속성
  * 캐멀케이스
  * class와 for
  * 속성 이름만 쓰기
  * {}
* 빈 요소 반드시 닫기
* 컴포넌트

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

## 트랜스파일러와 바벨
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.38/browser.min.js"></script>
```

JSX는 앞서 이야기 했듯이 HTML처럼 생겼지만 자바스크립트입니다. 하지만 JSX는 순수한 자바스크립트가 아니기 때문에 브라우저나 Node.js는 JSX를 직접 읽어 들이지 못합니다. 그러므로 JSX로 작성된 코드를 순수한 자바스크립트로 변화해주는 과정이 필요한데 이 때 사용되는 도구를 트랜스파일러라고 합니다. 주로 사용되는 트랜스파일러로는 바벨이 있는데 앞서 리액트와 리액트 DOM을 사용하기 위해 외부의 자바스크립트 파일을 읽어들였듯이 바벨을 사용하려면 역시나 파일이 필요합니다.

```
<script type="text/babel">...</script>
```



## JSX 문법

#### 태그 닫기
태그를 반드시 닫아줌
```
// HTML
<br>

// JSX
<br/>
```

## 속성
```
const a = <input type="text" value="입력값" />;

const inputValue = '입력값';
const a = <input type="text" value={inputValue} />;
```

#### class 속성과 for 속성
HTML의 class 속성과 for 속성은 JSX에서 className과 htmlFor로 


JSX는 자바스크립트의 변형된 형태이므로 JSX로 작성된 프로그램을 브라우저에서 렌더링하려면 JSX를 자바스크립트로 바꿔주는 트랜스파일러가 필요합니다. 


#### 예약어
#### 주석
#### 대소문자 구별



