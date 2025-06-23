# 라이프사이클(Lifecycle)이란?
컴포넌트가 화면에 나타나고, 업데이트되고, 사라질 때까지의 과정을 의미합니다.<br/>
클래스 컴포넌트와 함수형 컴포넌트에 따라 다르게 설명되지만, 기본 흐름은 동일합니다.
<br/>
<br/>

**마운트(Mount)**: 컴포넌트가 처음 생성되어 DOM에 추가되는 시점
**업데이트(Update)**: props 또는 state가 변경되어 컴포넌트가 다시 렌더링되는 시점
**언마운트(Unmount)**: 컴포넌트가 DOM에서 제거되는 시점
<br/>
<br/>

## 함수형 컴포넌트에서의 라이프사이클 (Hooks 사용)
함수형 컴포넌트에서는 useEffect를 활용해 라이프사이클 기능을 구현합니다.
<br/>
<br/>

### 마운트 시
```jsx
useEffect(() => {
  console.log("마운트됨");
}, []);
```
<br/>
<br/>

### 업데이트 시 (특정 값이 변경될 때)
```jsx
useEffect(() => {
  console.log("count 변경됨");
}, [count]);
```
<br/>
<br/>

### 언마운트 시
```jsx
useEffect(() => {
  const timer = setInterval(() => console.log("작동 중"), 1000);

  return () => {
    clearInterval(timer);
    console.log("언마운트됨: 타이머 정리");
  };
}, []);
```
