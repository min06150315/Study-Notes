# React에서 props와 관련된 중요한 개념 정리

## 1. props 기본 개념

- **props**는 부모 컴포넌트에서 자식 컴포넌트로 전달되는 데이터입니다.
- props는 **읽기 전용**이며, 자식 컴포넌트에서 이를 수정할 수 없습니다.
- 자식 컴포넌트에서는 props를 함수의 매개변수로 전달받아 화면을 렌더링하거나 동작을 수행합니다.

### 예시 (부모와 자식 컴포넌트):
```tsx
const ParentComponent = () => {
  const message = "Hello, World!";
  return <ChildComponent message={message} />;
};

type ChildComponentProps = {
  message: string;
};

const ChildComponent = ({ message }: ChildComponentProps) => {
  return <p>{message}</p>;
};
```

---

## 2. isRequired (PropTypes에서 필수 속성 지정)

- **PropTypes**를 사용하여 props가 필수인지 아닌지를 지정할 수 있습니다.
- `isRequired`는 PropTypes에서 사용되며, 해당 prop이 반드시 전달되어야 함을 나타냅니다.
- TypeScript에서는 `isRequired` 대신 **타입 시스템**을 통해 필수 속성을 정의합니다.

### PropTypes에서 isRequired 사용 예시:
```tsx
import PropTypes from 'prop-types';

const Greeting = ({ name, age }: { name: string, age: number }) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>You are {age} years old.</p>
    </div>
  );
};

Greeting.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number.isRequired,
};
```

---

## 3. Destructuring Assignment (구조 분해 할당)

- 구조 분해 할당은 객체나 배열에서 값을 추출하여 변수에 할당하는 문법입니다.
- React 컴포넌트에서 props를 더 간결하게 사용할 수 있습니다.

### 구조 분해 할당 사용 예시:
```tsx
type GreetingProps = {
  name: string;
  age: number;
};

const Greeting = ({ name, age }: GreetingProps) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>You are {age} years old.</p>
    </div>
  );
};
```

### 함수형 컴포넌트에서 구조 분해 할당:
```tsx
const Button = ({ label, onClick }: { label: string, onClick: () => void }) => {
  return <button onClick={onClick}>{label}</button>;
};
```

---

## 4. TypeScript에서 필수 속성 지정

- TypeScript에서는 props에 필수 속성을 지정할 때 **type**을 정의하여 명확하게 지정할 수 있습니다.
- 선택적 속성은 `?`를 붙여서 지정합니다.

### TypeScript에서 필수 속성 지정 예시:
```tsx
type GreetingProps = {
  name: string;  // 필수 속성
  age?: number;  // 선택적 속성
};

const Greeting = ({ name, age }: GreetingProps) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      {age && <p>You are {age} years old.</p>}
    </div>
  );
};
```

---

## 5. 기본값 설정 (defaultProps와 TypeScript에서 기본값 설정)

- **defaultProps**는 props에 기본값을 설정할 때 사용됩니다.
- TypeScript에서는 props의 기본값을 컴포넌트 내부에서 설정할 수 있습니다.
- 기본값을 설정할 때, 구조 분해와 함께 기본값을 지정할 수도 있습니다.

### defaultProps 사용 예시:
```tsx
const Button = ({ label }: { label: string }) => {
  return <button>{label}</button>;
};

Button.defaultProps = {
  label: 'Click me',
};
```

### TypeScript에서 기본값 설정 예시:
```tsx
const Button = ({ label = 'Click me' }: { label?: string }) => {
  return <button>{label}</button>;
};
```

---

## 6. PropTypes와 TypeScript의 차이점

| PropTypes                     | TypeScript                  |
|-------------------------------|-----------------------------|
| 런타임에 props의 타입 검사    | 컴파일 타임에 타입 검사     |
| JavaScript 환경에서 사용       | TypeScript 환경에서 사용    |
| `isRequired`로 필수 지정      | 타입 정의로 필수 지정       |

- PropTypes는 런타임에 props의 타입을 검사하는 라이브러리로, **JavaScript 환경**에서 유용합니다.
- TypeScript는 컴파일 타임에 타입을 검사하여, 더 강력한 타입 시스템을 제공합니다.

---

## 정리

1. **props**는 부모에서 자식 컴포넌트로 전달되는 읽기 전용 데이터입니다.
2. **isRequired**는 PropTypes에서 props를 필수로 설정할 때 사용되며, TypeScript에서는 타입 정의로 이를 처리합니다.
3. **구조 분해 할당**은 props를 간결하고 가독성 좋게 작성하는 데 유용합니다.
4. TypeScript에서는 **기본값 설정**을 defaultProps 없이 직접 지정할 수 있습니다.

이 모든 개념은 React 컴포넌트를 효율적으로 작성하고, 타입 안전성을 보장하는 데 도움이 됩니다.
