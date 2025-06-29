# useEffect
useEffect는 컴포넌트가 렌더링된 이후 특정 작업(예: 데이터 가져오기, 구독, DOM 조작 등)을 수행할 수 있게 해주는 함수입니다.
<br/>
<br/>

## 기본문법
```jsx
import React, { useEffect } from 'react';

useEffect(() => {
  // 이 안에 실행하고 싶은 코드 작성
});
```
<br/>
<br/>

## 사용예시
**1.마운트 시 한번만 실행**
```jsx
useEffect(() => {
  console.log("컴포넌트가 처음 마운트됨");
}, []); // 빈 배열 => 한 번만 실행
```
- 두 번째 인자로 빈 배열 []을 넣으면, 컴포넌트가 처음 화면에 나타날 때만 실행됩니다.
<br/>
<br/>

**2.특정 값이 바뀔 때만 실행**
```jsx
useEffect(() => {
  console.log("count가 바뀜!");
}, [count]);
```
- 배열 안에 count가 있으면, count 값이 바뀔 때마다 effect가 실행됩니다.
<br/>
<br/>

**3.특정 값이 바뀔 때만 실행**
```jsx
useEffect(() => {
  console.log("count가 바뀜!");
}, [count]);
```
- 배열 안에 count가 있으면, count 값이 바뀔 때마다 effect가 실행됩니다.
<br/>
<br/>

**4.마운트 시 정리(clean-up)**
```jsx
useEffect(() => {
  const timer = setInterval(() => {
    console.log("타이머 동작 중");
  }, 1000);

  return () => {
    clearInterval(timer); // 컴포넌트가 사라질 때 정리
    console.log("타이머 정리");
  };
}, []);
```
- useEffect 안에서 return으로 함수를 반환하면, 컴포넌트가 언마운트되거나 effect가 다시 실행되기 전에 정리(clean-up) 작업이 수행됩니다.
<br/>
<br/>

## 언제 useEffect를 써야 하나요?
- API 요청(fetch)
- 이벤트 리스너 추가/제거
- 타이머/인터벌 설정
- 외부 라이브러리 연동
- 브라우저 DOM 직접 조작

## 주의할 점
- 무한 루프에 주의: 상태를 바꾸는 코드를 useEffect 안에 쓰고, 의존성 배열을 잘못 설정하면 계속 렌더링이 반복될 수 있습니다.
- 의존성 배열을 정확하게 작성하지 않으면 원하는 시점에 실행되지 않거나, 원하지 않는 시점에 실행될 수 있어요.
