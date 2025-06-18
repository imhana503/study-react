# ✨ 2단계: JSX 문법

## JSX란?

- JavaScript + XML
- HTML처럼 보이지만 JavaScript 코드임
- React.createElement(...)로 변환됨

## 주요 규칙

1. 하나의 부모 태그로 감싸야 함
2. class → className, for → htmlFor
3. 중괄호 `{}`로 JS 값 출력
4. 조건부 렌더링 가능

## 예시 코드

```jsx
const name = "React";

function App() {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>{name === "React" ? "환영합니다" : "다시 시작"}</p>
    </div>
  );
}
