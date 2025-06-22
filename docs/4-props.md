#  props란?
props는 "properties(속성)"의 줄임말로, 부모 컴포넌트가 자식 컴포넌트에 값을 전달할 때 사용하는 객체입니다.<br/>
React에서 컴포넌트는 재사용 가능한 UI 블록이고, props는 이 컴포넌트에 동적인 데이터를 외부에서 주입하는 방법입니다.
<br/>
<br/>
## 예시코드
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Welcome name="Alice" />;
}
```
- App 컴포넌트는 Welcome 컴포넌트에 name="Alice"라는 **속성(prop)**을 전달합니다
- Welcome 컴포넌트는 props.name을 통해 그 값을 사용합니다.
- 결과 출력: Hello, Alice!
<br/>
<br/>

## 구조 분해 할당 사용하기 (Destructuring)
JSX에서는 보통 이렇게 더 간결하게 쓰기도 합니다
```jsx
function Welcome({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```
<br/>
<br/>

## 1. props로 함수(Function) 전달하기
부모가 자식에게 함수를 전달하면, 자식이 부모의 로직을 실행할 수 있어요.
```jsx
// 부모 컴포넌트
function Parent() {
  const handleClick = () => {
    alert("자식 컴포넌트에서 버튼 클릭됨!");
  };

  return <Child onButtonClick={handleClick} />;
}

// 자식 컴포넌트
function Child({ onButtonClick }) {
  return <button onClick={onButtonClick}>클릭</button>;
}
```
- 자식이 버튼을 클릭하면 부모의 handleClick 함수가 실행됩니다.
<br/>
<br/>

## 2. props의 기본값 설정 (defaultProps)
```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

Greeting.defaultProps = {
  name: "익명",
};

// 사용 예
<Greeting />  // 출력: Hello, 익명!
```
<br/>
<br/>

## 3. props로 조건부 렌더링 하기
```jsx
function Message({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <p>환영합니다!</p> : <p>로그인 해주세요.</p>}
    </div>
  );
}
```
<br/>
**사용 시**
```jsx
<Message isLoggedIn={true} />
```
<br/>
<br/>

## 4. props로 컴포넌트나 JSX 전달하기 (children)
```jsx
function Layout({ children }) {
  return <div className="box">{children}</div>;
}

// 사용 예
<Layout>
  <h2>타이틀</h2>
  <p>본문 내용</p>
</Layout>
```
위의 경우, <Layout> 안에 넣은 모든 JSX는 props.children으로 전달됩니다.
<br>
<br/>

## 5. props 타입 확인 (선택사항: TypeScript or PropTypes)
JS로 개발할 때는 prop-types 패키지를 써서 props 타입을 체크할 수 있어요
```jsx
import PropTypes from 'prop-types';

function Button({ label }) {
  return <button>{label}</button>;
}

Button.propTypes = {
  label: PropTypes.string.isRequired,
};
```
