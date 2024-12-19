
# TypeScript vs JavaScript

## 1. 정적 타입 시스템 (Static Typing)
- **JavaScript**:
  - JavaScript는 **동적 타입** 언어입니다. 변수의 타입은 실행 중에 결정됩니다.
  ```javascript
  let x = 5;   // x는 숫자
  x = 'hello'; // x는 이제 문자열
  ```

- **TypeScript**:
  - TypeScript는 **정적 타입** 언어로, 변수의 타입을 명시적으로 정의할 수 있습니다.
  ```typescript
  let x: number = 5;   // x는 숫자
  x = 'hello'; // 오류: 'hello'는 문자열이고 x는 숫자
  ```

## 2. 타입 추론 (Type Inference)
- **JavaScript**:
  - JavaScript는 변수의 타입을 명시적으로 지정할 필요 없이 실행 시 추론됩니다.

- **TypeScript**:
  - TypeScript는 변수에 초기값을 할당할 때 **타입 추론**을 통해 자동으로 타입을 결정합니다.
  ```typescript
  let num = 5;  // TypeScript는 num을 number로 추론
  num = 'hello'; // 오류: 'hello'는 string이고 num은 number여야 합니다.
  ```

## 3. 인터페이스 (Interface)와 타입 (Type)
- **JavaScript**:
  - JavaScript는 객체의 구조나 타입을 명시적으로 정의할 수 없습니다.
  
- **TypeScript**:
  - TypeScript는 **인터페이스 (Interface)**와 **타입 (Type)**을 사용하여 객체나 함수의 구조를 명확하게 정의할 수 있습니다.
  ```typescript
  interface User {
    name: string;
    age: number;
  }

  const user: User = { name: 'Alice', age: 30 };
  user.age = 'thirty'; // 오류: 'thirty'는 number여야 합니다.
  ```

## 4. 클래스와 상속 (Class & Inheritance)
- **JavaScript**:
  - JavaScript는 **클래스**와 **상속**을 지원합니다. 그러나 타입에 대한 명확한 정의가 없습니다.

- **TypeScript**:
  - TypeScript는 **타입 선언**을 추가하여 클래스와 상속을 정의할 때 타입을 명시할 수 있습니다.
  ```typescript
  class Animal {
    name: string;

    constructor(name: string) {
      this.name = name;
    }

    speak(): void {
      console.log(`${this.name} makes a sound`);
    }
  }

  class Dog extends Animal {
    constructor(name: string) {
      super(name);
    }

    speak(): void {
      console.log(`${this.name} barks`);
    }
  }

  const dog = new Dog('Rex');
  dog.speak(); // 'Rex barks'
  ```

## 5. 함수의 타입 정의 (Function Typing)
- **JavaScript**:
  - JavaScript에서는 함수의 매개변수와 반환값에 대한 타입을 명시하지 않으며, 이는 런타임에 결정됩니다.

- **TypeScript**:
  - TypeScript에서는 **함수의 매개변수**와 **반환값**에 대한 타입을 명시적으로 정의할 수 있습니다.
  ```typescript
  function add(a: number, b: number): number {
    return a + b;
  }

  add(5, '10'); // 오류: 두 번째 매개변수는 number여야 합니다.
  ```

## 6. 제너릭 (Generics)
- **JavaScript**:
  - JavaScript에서는 제너릭 개념이 없습니다.

- **TypeScript**:
  - TypeScript는 **제너릭 (Generics)**을 지원하여 함수나 클래스가 다양한 타입을 유연하게 처리할 수 있습니다.
  ```typescript
  function identity<T>(value: T): T {
    return value;
  }

  let output = identity<string>('Hello'); // T는 string으로 추론
  ```

## 7. 타입 안전성 (Type Safety)
- **JavaScript**:
  - JavaScript는 타입 검사를 하지 않기 때문에, 실행 중에 타입 오류가 발생할 수 있습니다.

- **TypeScript**:
  - TypeScript는 **타입 안전성**을 보장하며, 컴파일 타임에 타입 검사를 수행하여 타입이 맞지 않으면 오류를 발생시킵니다.
  ```typescript
  let name: string = 'Alice';
  name = 5; // 오류: '5'는 string이 아닙니다.
  ```

## 8. 모듈 시스템 (Module System)
- **JavaScript**:
  - JavaScript는 **ES 모듈**을 지원하지만, CommonJS 스타일 모듈도 여전히 많이 사용됩니다.

- **TypeScript**:
  - TypeScript는 **ES 모듈**을 완벽하게 지원하며, 타입 정의를 함께 가져와 사용할 수 있습니다.
  ```typescript
  import * as _ from 'lodash';

  _.cloneDeep([1, 2, 3]); // 타입 안전성을 제공하면서 lodash 사용 가능
  ```

## 결론
- **JavaScript**는 동적 타이핑 언어로 더 유연하지만, **TypeScript**는 정적 타입 시스템을 통해 코드의 안전성을 높이고 오류를 사전에 방지할 수 있습니다. TypeScript는 JavaScript의 모든 기능을 포함하면서 타입 시스템을 통해 코드 품질을 향상시키는 데 큰 도움이 됩니다.
