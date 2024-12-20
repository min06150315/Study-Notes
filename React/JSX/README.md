# React에서의 JSX

**JSX(JavaScript XML)** 는 JavaScript 코드 안에서 HTML을 작성할 수 있는 문법 확장입니다. JSX는 React 컴포넌트를 정의할 때 주로 사용되며, HTML과 JavaScript 코드가 혼합된 형태를 띕니다. 이는 React에서 UI를 정의할 때 직관적인 문법을 제공하는 중요한 기능입니다.

## JSX의 주요 특징

### 1. HTML과 유사한 문법
JSX는 HTML 구조와 비슷한 문법을 사용하지만, 실제로는 JavaScript로 변환됩니다. 

```jsx
const element = <div>hello world</div>;
```

### 2. 컴파일 과정
JSX는 브라우저가 이해할 수 없는 문법이기 때문에, Babel과 같은 트랜스파일러를 사용하여 JavaScript로 변환됩니다.

```jsx
const element = <h1>Hello, world!</h1>;
// 위 JSX는 아래와 같이 변환됩니다.
const element = React.createElement('h1', null, 'Hello, world!');
```

### 3. 속성(Props)
JSX에서는 HTML 태그의 속성처럼 React 컴포넌트에 props를 전달할 수 있습니다.

```jsx
const element = <MyComponent name="John" age={30} />;
```

### 4. 중괄호 `{}` 사용
JSX 내에서 JavaScript 표현식을 삽입하려면 중괄호 `{}`를 사용합니다.

```jsx
const name = "Alice";
const element = <h1>Hello, {name}!</h1>;
```

### 5. 컴포넌트 구조화
JSX는 React 컴포넌트를 구조화하는 데 유용하며, 다른 컴포넌트를 호출하여 UI의 재사용성을 높일 수 있습니다.

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return <Welcome name="Sara" />;
}
```

### 6. 조건부 렌더링
JSX에서는 JavaScript 논리 연산자를 사용하여 조건부 렌더링을 할 수 있습니다.

```jsx
const isLoggedIn = true;
const element = isLoggedIn ? <UserGreeting /> : <GuestGreeting />;
```

### 7. 클래스 이름
JSX에서는 HTML의 `class` 대신 `className`을 사용해야 합니다. 이는 `class`가 JavaScript의 예약어이기 때문입니다.

```jsx
const element = <div className="container">Hello</div>;
```

### 8. 스타일
JSX에서는 인라인 스타일을 객체 형식으로 작성할 수 있습니다. 스타일 속성은 camelCase로 작성해야 합니다.

```jsx
const style = {
  backgroundColor: 'blue',
  color: 'white',
};
const element = <div style={style}>Styled Div</div>;
```

## JSX의 장점

1. **가독성**: HTML과 JavaScript를 혼합한 코드로 UI를 정의할 수 있어, 코드의 가독성과 유지보수성이 높습니다.
2. **React의 효율적인 렌더링**: JSX는 React가 UI를 효율적으로 업데이트할 수 있도록 돕는 최적화된 코드로 변환됩니다.
3. **동적 표현**: JavaScript와 함께 사용할 수 있어, 동적인 UI 업데이트가 가능합니다.

## JSX의 제한 사항

1. **중괄호**: JSX에서 JavaScript 표현식을 사용할 때 중괄호 `{}`로 감싸야 하므로, HTML 속성 안에 JavaScript를 넣을 때 불편할 수 있습니다.
2. **단일 루트 엘리먼트**: JSX 내에서는 하나의 루트 엘리먼트만 반환할 수 있기 때문에 여러 엘리먼트를 반환하려면 `div`로 감싸거나 `React.Fragment`를 사용해야 합니다.

---

JSX는 React의 강력한 특성 중 하나로, 컴포넌트 기반 개발에 적합한 문법을 제공합니다.
