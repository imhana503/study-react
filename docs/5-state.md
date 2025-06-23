#  state?
- 컴포넌트 내부에서 관리하는 값(데이터)
- 사용자의 행동이나 시스템 이벤트에 따라 변할 수 있는 상태 정보
- state가 바뀌면 React가 자동으로 컴포넌트를 다시 그려줌(렌더링)
<br/>
<br/>

## 예시
예를 들어, 버튼을 누를 때마다 숫자가 증가하는 앱이라면,
- state 상태 = 현재 숫자 값 (예: 0, 1, 2...)
- 사용자가 버튼을 누르면 state가 바뀜 → React는 그걸 감지하고 화면도 업데이트
<br/>
<br/>

## 예시코드
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0); // count = state 상태

  return (
    <div>
      <p>현재 숫자: {count}</p>
      <button onClick={() => setCount(count + 1)}>숫자 증가</button>
    </div>
  );
}
```
- 여기서 count는 state 상태입니다.
- 버튼을 누르면 setCount를 통해 상태를 바꾸고, React가 자동으로 화면을 다시 보여줍니다.
<br/>
<br/>

## 요약
"state 상태"는 컴포넌트가 현재 어떤 상황인지 기억하고, 그 상황에 따라 화면을 보여주는 역할을 합니다.
