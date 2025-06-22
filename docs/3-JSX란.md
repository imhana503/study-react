#  JSX란?
JSX (JavaScript XML)는 JavaScript 코드 안에서 HTML 같은 문법을 사용할 수 있게 해주는 문법 확장(Syntax Extension)입니다.
<br/>
<br/>
## 예시코드
```jsx
const element = <h1>Hello, world!</h1>;
```
<br/>
<br/>

## JSX를 사용하는 이유
JSX는 UI를 구성할 때 코드 가독성과 생산성을 높여줍니다. <br/>
일반적으로 HTML과 JavaScript를 분리해서 작업하던 방식보다, JSX를 사용하면 컴포넌트 중심의 UI 구조를 더 직관적으로 표현할 수 있습니다.
<br/>
<br/>

## JSX 실제 동작 설명
JSX는 브라우저에서 직접 실행되지 않습니다. <br/>
Babel 같은 트랜스파일러가 JSX 코드를 React.createElement() 호출로 변환해 줍니다.
``jsx
const element = <h1>Hello</h1>;
``
변환되면 다음과 같은 JavaScript가 됩니다.
```javascript
const element = React.createElement('h1', null, 'Hello');
```
즉, **JSX는 단순히 React 요소를 생성하는 문법적 설탕(Syntax Sugar)**입니다.
<br/>
<br/>

## JSX 문법의 몇 가지 특징
1.반드시 하나의 부모 요소로 감싸야 함
```jsx
// 올바른 예
return (
  <div>
    <h1>Title</h1>
    <p>Paragraph</p>
  </div>
);
```
2.HTML 속성과 다르게 표기하는 경우가 있음
- class → className
- for → htmlFor
- 자바스크립트 표현식은 {}로 감쌈
<br/>
<br/>

## 간단 예제 전체 코드
```jsx
const name = "React";
return <h1>Hello, {name}</h1>;
```
<br/>
<br/>

## JSX 요약
| 항목    | 설명                                       |
| ----- | ---------------------------------------- |
| JSX란? | JavaScript 안에서 HTML처럼 코드를 작성할 수 있게 하는 문법 |
| 장점    | 가독성 향상, UI 구조를 코드로 쉽게 표현                 |
| 내부 동작 | `React.createElement()`로 변환됨             |
| 특징    | 하나의 부모 요소, 속성은 camelCase, 표현식은 `{}` 사용   |




