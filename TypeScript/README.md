
# TypeScript

TypeScript는 JavaScript의 상위 집합(Superset)으로, JavaScript에 정적 타입 시스템을 추가한 프로그래밍 언어입니다. 주요 개념은 다음과 같습니다:

## 주요 개념

### 1. 정적 타입 검사 (Static Type Checking)
TypeScript의 가장 큰 특징은 타입을 명시적으로 정의할 수 있다는 점입니다. 변수, 함수 인자, 반환값 등에 타입을 지정함으로써 컴파일 타임에 오류를 미리 잡을 수 있습니다. 
JavaScript는 동적 타입 언어인데 반해, TypeScript는 코드 작성 시 타입 오류를 방지하고, 더 안전한 코드를 작성할 수 있도록 도와줍니다.

### 2. 타입 주석 (Type Annotations)
TypeScript에서는 변수와 함수에 타입을 명시적으로 지정할 수 있습니다. 예를 들어:

```typescript
let name: string = "Alice";
function add(a: number, b: number): number {
  return a + b;
}
```

### 3. 인터페이스 (Interfaces)
TypeScript는 객체의 구조를 정의하는 `interface`를 지원합니다. 이를 통해 객체나 클래스의 형태를 명확하게 정의할 수 있습니다.

```typescript
interface Person {
  name: string;
  age: number;
}

const person: Person = {
  name: "Alice",
  age: 25
};
```

### 4. 클래스 (Class)와 상속 (Inheritance)
TypeScript는 JavaScript의 클래스 문법을 확장하여, 정적 타입을 포함한 클래스를 정의할 수 있습니다. 또한, 클래스 간 상속도 지원합니다.

```typescript
class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

class Dog extends Animal {
  bark() {
    console.log("Woof!");
  }
}
```

### 5. 제네릭 (Generics)
TypeScript는 제네릭을 지원하여 코드의 재사용성을 높이고, 타입 안전성을 유지할 수 있습니다. 제네릭은 함수나 클래스에서 사용할 수 있는 타입을 동적으로 정의할 수 있게 해줍니다.

```typescript
function identity<T>(arg: T): T {
  return arg;
}
```

### 6. 타입 추론 (Type Inference)
TypeScript는 타입을 명시적으로 지정하지 않아도, 변수나 함수의 반환값에 대해 타입을 자동으로 추론할 수 있습니다. 이는 코드 작성이 간편하게 만들어줍니다.

### 7. ES6+ 기능 지원
TypeScript는 최신 JavaScript 기능을 지원합니다. 예를 들어:
- 화살표 함수
- 비구조화 할당
- async/await

또한, ES6 이상의 기능을 TypeScript에서 미리 사용하고, ES5 이하로 컴파일하여 브라우저 호환성 문제를 해결할 수 있습니다.

## TypeScript의 장점
TypeScript는 JavaScript와 완전히 호환되며, 기존의 JavaScript 코드를 TypeScript로 점진적으로 변환할 수 있어, 기존 프로젝트에서 도입하기 용이합니다.
