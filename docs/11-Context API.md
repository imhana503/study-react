# Context API
컴포넌트 트리 전체에 데이터를 전역적으로 공유할 수 있게 해주는 기능입니다.<br/>
주로 prop drilling(깊은 props 전달) 문제를 해결하기 위해 사용됩니다.
<br/>
<br/>

## 기본 개념
React에서 데이터를 컴포넌트 간에 전달할 때 일반적으로 props를 사용합니다.<br/>
하지만 컴포넌트 트리가 깊을 경우, 중간 컴포넌트들이 필요하지 않은 데이터를 계속 전달해야 하는 문제가 생깁니다.<br/>
이를 해결하기 위해 Context API를 사용하면, 데이터를 전역처럼 사용하면서 특정 컴포넌트에만 필요한 데이터를 바로 전달할 수 있습니다.
<br/>
<br/>

## 사용 방법
**1. Context 생성**
```jsx
import React, { createContext } from 'react';

const ThemeContext = createContext(); // 기본값을 넣을 수도 있음
```
<br/>
<br/>

**2. Provider로 감싸기**
```jsx
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}
```
<br/>
<br/>

**3. Consumer 또는 useContext로 사용**
**Consumer 사용**
```jsx
function Toolbar() {
  return (
    <ThemeContext.Consumer>
      {value => <div>현재 테마는 {value}입니다.</div>}
    </ThemeContext.Consumer>
  );
}
```
**useContext Hook 사용 (더 간결)**
```jsx
import { useContext } from 'react';

function Toolbar() {
  const theme = useContext(ThemeContext);
  return <div>현재 테마는 {theme}입니다.</div>;
}
```
<br/>
<br/>

## 언제 Context를 사용해야 하나?
- 전역 설정 값 (예: 테마, 다크모드)
- 로그인 상태 (AuthContext)
- 다국어 지원 (i18n) 설정
- 전역 알림 또는 모달 상태
  
하지만 모든 상태를 Context로 관리하는 것은 비효율적일 수 있습니다.<br/>
복잡한 상태 관리는 Redux, Zustand, Recoil 같은 상태 관리 라이브러리를 사용하는 것이 더 나을 수 있습니다.
<br/>
<br/>

## 요약
| 특징    | 설명                                        |
| ----- | ----------------------------------------- |
| 목적    | 전역 상태 관리                                  |
| 주요 구성 | `createContext`, `Provider`, `useContext` |
| 장점    | prop drilling 방지                          |
| 단점    | 상태 변경 시 모든 하위 컴포넌트 리렌더링 가능성               |
