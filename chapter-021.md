---
title: 리액트처럼 생각하기
seoTitle: 리액트처럼 생각하기 | React | ohoo
seoDescription: description for search engines
isFree: true
---


리액트로 애플리케이션을 만드는 방법에 대해 알아보자

1. UI를 컴포넌트 계층 구조로 나누기
2. 리액트로 정적 버전 만들기
3. 최소한의 상태(state) 찾기
4. 상태의 위치 찾기
5. 역방향 데이터 흐름 찾기


## Step 1: UI를 컴포넌트 계층 구조로 나누기

* FilterableProductTable
  * SearchBar
  * ProductTable
    * ProductCategoryRow
    * ProductRow
