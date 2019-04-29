---
title: 리액트
seoTitle: 리액트 | ohoo
seoDescription: description for search engines
isFree: true
---


웹 애플리케이션은 클라이언트 사이드 코드와 서버 사이드 코드로 구성되어 있습니다. 이들을 작성하기 위해서는 각각의 프로그램에 적합한 언어가 필요한데 클라이언트 사이드 언어로는 HTML, CSS, 자바스크립트가 

시간이 흐르면서 이들을 직접 사용하기 보다는 자바스크립트 기반의 프레임워크나 라이브러리를 사용하는 방향으로 바뀌었습니다. 

자바스크립트 기반의 프레임워크에는 Angular, Vue, Ember, Backbone,

[React](https://reactjs.org)는 페이스북이 자바스크립트로 만든 UI(User Interface) 라이브러리입니다. 공식 문서에 따르면 리액트는 컴포넌트를 기반으로 하고 있는데 컴포넌트(Component)란 UI를 구성하고 있는 독립적인 개체들로 뷰(시각적인 부분)와 동작(로직)이 조합되어 있는 것을 말합니다.

가상 DOM은 브라우저에 내장되어 있는 DOM과 별도로

리액트는 성능과 브라우저 간의 호환성을 위해 브라우저에 독립적인 DOM을 사용합니다.

* 프레임워크와 라이브러리
* 리액트의 DOM: 가상 DOM
* 리액트의 문법: JSX
* 새로운 개념: 컴포넌트
  
  
* 과거의 웹 앱  
HTML, CSS로 기본적인 코드를 작성한 다음 필요에 따라 자바스크립트로 HTML, CSS 코드를 수정
실제 DOM을 조작하면 전체 렌더 트리를 새로 생성함 그러므로 브라우저의 성능에 부정적인 영향을 미침.
DOM 조작을 최소화하는 것이 좋음

* 리액트로 만드는 웹 앱
가상 DOM을 사용하며 가상 DOM과 실제 DOM의 차이가 있는 부분만 업그레이드하므로 실제 DOM 조작이 상대적으로 적음
그러므로 과거에 HTML, CSS로 작성하던 부분을 리액트(자바스크립트)로 대체하게 됨.


웹 앱을 만드는데 중심적인 역할을 하는 것이 HTML에서 자바스크립트로 변경됨






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
