
# React: 클래스형 컴포넌트 vs 함수형 컴포넌트

React에서 **클래스형 컴포넌트**와 **함수형 컴포넌트**는 상태 관리, 라이프사이클 메서드, 그리고 문법적 차이에서 구별됩니다.

---

## 1. 클래스형 컴포넌트 (Class Component)

- ES6 클래스 문법을 사용해 작성됩니다.
- `React.Component`를 상속받아 상태 관리와 라이프사이클 메서드를 포함할 수 있습니다.

### 예제 코드
```jsx
import React, { Component } from 'react';

class MyClassComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  componentDidMount() {
    console.log('Component mounted!');
  }

  handleClick = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.handleClick}>Increment</button>
      </div>
    );
  }
}

export default MyClassComponent;
```

### 주요 특징
1. **상태 관리**: `this.state`와 `this.setState()`를 사용하여 상태 관리.
2. **라이프사이클 메서드**:
   - `componentDidMount`, `componentWillUnmount`, `shouldComponentUpdate` 등.
3. **문법**: 클래스 문법을 사용하여 컴포넌트를 정의.

---

## 2. 함수형 컴포넌트 (Functional Component)

- 간단한 함수로 정의되며, React 16.8 버전 이후 Hooks를 사용하여 상태 관리와 라이프사이클 기능을 지원합니다.

### 예제 코드
```jsx
import React, { useState, useEffect } from 'react';

const MyFunctionalComponent = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Component mounted!');
  }, []);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
};

export default MyFunctionalComponent;
```

### 주요 특징
1. **상태 관리**: `useState` Hook을 사용하여 상태 관리.
2. **라이프사이클 메서드**: `useEffect` Hook을 사용하여 생명주기 관리.
3. **문법**: 함수 형태로 정의되어 간결하고 읽기 쉬움.

---

## 3. 주요 차이점

| **항목**               | **클래스형 컴포넌트**               | **함수형 컴포넌트**            |
|------------------------|------------------------------------|--------------------------------|
| **상태 관리**           | `this.state`와 `this.setState` 사용 | `useState` Hook 사용           |
| **라이프사이클 메서드** | `componentDidMount`, `componentWillUnmount` 등 | `useEffect` Hook 사용          |
| **문법**                | 클래스 문법 (`class` 키워드 사용)  | 함수 문법 (`function` 또는 `const` 사용) |
| **컴포넌트 정의**        | `render()` 메서드 사용             | 바로 JSX 반환                 |
| **성능**                | 상태와 라이프사이클 처리 방식에 따라 다름 | 간결하고 성능 우수한 경우 많음 |
| **코드 복잡도**          | 복잡한 상태 관리 및 라이프사이클 관리 필요 | 간결하고 직관적임             |

---

## 4. 추가 사항

### React Hooks의 장점
- React 16.8 버전 이후 Hooks 도입으로 함수형 컴포넌트가 상태 관리 및 생명주기 관리를 효과적으로 처리 가능.
- `useReducer`, `useContext` 등을 활용하여 상태 관리 로직 분리 가능.

### 현재 트렌드
- 함수형 컴포넌트가 더 간결하고 읽기 쉬운 문법을 제공하기 때문에, **새로운 React 프로젝트에서는 함수형 컴포넌트를 주로 사용**.
- 클래스형 컴포넌트는 이전 프로젝트의 유지보수 또는 특정 상황에서 사용.

---

## 5. 요약

| **특징** | **클래스형 컴포넌트** | **함수형 컴포넌트** |
|----------|-----------------------|---------------------|
| **가독성** | 중간 | 높음 |
| **유연성** | 제한적 | 높음 (Hooks로 확장 가능) |
| **사용성** | 유지보수 중 (Legacy) | 새로운 표준 |

함수형 컴포넌트는 더 간결하고 직관적인 문법을 제공하며, **Hooks 도입 이후** 상태 관리와 라이프사이클을 처리하는 표준으로 자리 잡았습니다.
