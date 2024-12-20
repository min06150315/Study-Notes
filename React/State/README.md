# React에서 State 관리 개념 정리

React에서 `state`는 컴포넌트의 상태를 관리하는 객체입니다. 상태는 컴포넌트의 렌더링에 영향을 미치며, 변경될 경우 React는 해당 컴포넌트를 다시 렌더링하여 UI를 업데이트합니다. 주로 사용자 입력, 서버 응답, UI 인터랙션에 따라 변경됩니다.

---

## 1. 클래스형 컴포넌트에서 state 사용

- 클래스형 컴포넌트에서 `state`는 `this.state`로 정의되며, 상태를 변경하려면 `this.setState()` 메서드를 사용합니다.

### 예시:
```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}
```

---

## 2. 함수형 컴포넌트에서 state 사용 (useState 훅)

React 16.8부터 함수형 컴포넌트에서도 상태를 관리할 수 있는 `useState` 훅이 도입되었습니다. 함수형 컴포넌트에서는 `useState`를 사용하여 상태를 정의하고, 상태를 변경할 수 있는 함수를 반환받습니다.

### 예시:
```jsx
import { useState } from 'react';

const MyComponent = () => {
  const [count, setCount] = useState(0); // 초기 값 0

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};
```

### useState의 동작
- `useState`는 초기 상태 값을 인수로 받습니다.
- 상태 변수와 상태를 업데이트하는 함수를 **배열**로 반환합니다.
  - 첫 번째 요소: 상태 변수 (`count`)
  - 두 번째 요소: 상태를 업데이트하는 함수 (`setCount`)

---

## 3. 상태 변경과 리렌더링

- `setState` 또는 `useState`의 상태 변경 함수가 호출되면, React는 해당 컴포넌트를 다시 렌더링하여 UI를 업데이트합니다.
- 상태 변경은 **비동기적으로** 일어나며, 여러 상태 변경 함수가 연속적으로 호출되면 React는 이를 일괄 처리하여 효율적으로 리렌더링합니다.

---

## 4. 상태 객체

상태는 복잡한 데이터 구조일 수도 있습니다. 예를 들어, 상태가 객체일 경우 `setState` 또는 `useState`로 객체를 업데이트할 수 있습니다.

### 예시:
```jsx
const MyComponent = () => {
  const [user, setUser] = useState({ name: 'Alice', age: 30 });

  const updateName = () => {
    setUser(prevState => ({ ...prevState, name: 'Bob' }));
  };

  return (
    <div>
      <p>Name: {user.name}</p>
      <p>Age: {user.age}</p>
      <button onClick={updateName}>Change Name</button>
    </div>
  );
};
```
- 객체를 업데이트할 때는 **불변성**을 유지하기 위해 `prevState`를 사용하여 기존 상태를 복사하고 필요한 부분만 변경합니다.

---

## 5. 상태 관리 방법

React에서 상태는 컴포넌트 내부에서 관리되거나, 글로벌 상태 관리 도구를 사용하여 여러 컴포넌트에서 공유될 수 있습니다.

### 글로벌 상태 관리 도구:
- Context API
- Redux
- Recoil
- Zustand 등

---

## 정리

1. **상태**는 컴포넌트의 동적 데이터를 표현합니다.
2. 상태를 변경하면 React는 해당 컴포넌트를 리렌더링합니다.
3. 함수형 컴포넌트에서는 `useState` 훅을 사용하여 상태를 관리합니다.
4. 상태는 객체나 배열 등 다양한 형태로 관리할 수 있으며, 이를 업데이트할 때는 **불변성을 지키는 것**이 중요합니다.

이 모든 개념은 React 컴포넌트를 효율적으로 작성하고, 상태 관리를 명확하게 수행하는 데 도움을 줍니다.
