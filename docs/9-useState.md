# useState
useState는 컴포넌트 내부에서 데이터(상태)를 저장하고, 그 값을 변경할 수 있게 해주는 함수입니다.
<br/>
<br/>

## 필요한 이유
React 컴포넌트는 기본적으로 props만 받아서 렌더링을 합니다. 그러나 사용자 입력, 버튼 클릭, API 호출 등으로 데이터가 바뀌어야 할 때, 그 데이터를 저장하고 관리하려면 state가 필요합니다.<br/>
함수형 컴포넌트에서는 예전엔 state를 쓸 수 없었지만, React 16.8 이후부터 useState라는 훅을 통해 상태 사용이 가능해졌습니다.

## 기본 사용법
```jsx
import React, { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>카운트: {count}</p>
      <button onClick={() => setCount(count + 1)}>증가</button>
    </div>
  );
}
```
- count: 현재 상태 값
- setCount: 상태를 변경하는 함수
- useState(0): 초기 상태는 0
