---
title: Next.js
seoTitle: Next.js | React | ohoo
seoDescription: description for search engines
isFree: true
---


* Next.js의 특징
  * 서버 사이드 렌더링
  * 코드 스플리팅
  * 클라이언트 사이드 라우팅
  * 핫 모듈 대체
  * 바벨과 웹팩 커스터마이즈
  * Express 또는 노드 HTTP 서버와 사용


## 설치
```
npm i next
```

```
{
  "scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start"
  }
}
```

package.json 파일에 위와 같은 스크립트를 추가하세요.

```
function Home() {
  return <div>Welcome to Next.js!</div>;
}

export default Home;
```

pages라는 디렉토리를 만들고 그 안의 index.js 파일에 위의 코드를 입력하세요.

```
npm run dev 또는 yarn dev
```

둘 중 하나를 실행하고 주소창에 http://localhost:3000를 입력합니다.

## 자동적인 코드 스플리팅
## CSS
## 정적인 파일
## \<head\>
## 데이터 가져오기와 컴포넌트 라이프사이클
#### 상태가 있는 컴포넌트
상태, 라이프사이클 그리고 초깃값 설정이 필요할 때는 React.Component를 export할 수 있습니다.  

페이지가 로드될 때 데이터를 로드하려면 비동기 정적 메서드인 getInitialProps를 사용하세요. getInitialProps는 자바스크립트의 일반 객체로 바뀌는 모든 것을 비동기적으로 가져옵니다. 

getInitialProps로부터 반환된 데이터는 서버 렌더링시 연결됩니다. getInitialProps로부터 반환된 객체가 Date, Map, Set을 사용하지 않은 일반 객체인지 확인하세요.

초기 페이지 로딩시 getInitialProps는 서버에서만 실행됩니다. getInitialProps는 Link 컴포넌트를 통해 다른 경로로 이동하거나 라우팅 API를 사용할 때만 클라이언트에서 실행됩니다.

#### 상태가 없는 컴포넌트
  
## 라우팅
