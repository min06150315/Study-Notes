# ESLint와 Prettier

## 1. ESLint (코드 품질 검사 도구)

### 개념
- ESLint는 정적 코드 분석 도구로, JavaScript 및 TypeScript 코드에서 문법 오류, 잠재적 버그, 불필요한 코드 등을 찾아내고, 코딩 규칙을 적용합니다.
- 코드 품질을 높이고, 팀이 정의한 규칙을 지키도록 강제하는 데 중점을 둡니다.

### 주요 기능
- **문법 오류 및 버그 탐지**: 코드에서 발생할 수 있는 잠재적인 오류를 미리 파악합니다.
- **규칙 기반 검사**: 팀 내 코드 규칙(예: 변수명 규칙, 함수 호출 순서 등)을 강제하여 일관성을 유지합니다.
- **자동 수정**: 일부 오류는 자동으로 수정할 수 있습니다.

### 코드 예시
#### 사용되지 않은 변수 (no-unused-vars)
```javascript
const a = 10;  // ESLint 오류: a는 사용되지 않음
console.log('Hello World');
```
ESLint는 사용되지 않은 변수 `a`를 오류로 표시하고, 이를 제거하거나 사용하도록 경고합니다.

#### == 대신 === 사용 (eqeqeq)
```javascript
if (a == 10) {
  console.log('a is 10');  // ESLint 오류: == 대신 ===를 사용
}
```
ESLint는 `==` 대신 `===`를 사용하도록 강제합니다. 올바른 코드는 다음과 같습니다:
```javascript
if (a === 10) {
  console.log('a is 10');
}
```

#### Prop Types 미사용 (react/prop-types)
```javascript
function MyComponent(props) {
  return <div>{props.name}</div>;  // ESLint 오류: propTypes를 정의해야 함
}
```
React 컴포넌트에서 Prop Types를 사용하지 않으면 `react/prop-types` 규칙에 의해 경고가 발생할 수 있습니다. 이를 해결하려면 Prop Types를 추가해야 합니다:
```javascript
import PropTypes from 'prop-types';

function MyComponent(props) {
  return <div>{props.name}</div>;
}

MyComponent.propTypes = {
  name: PropTypes.string.isRequired,
};
```

---

## 2. Prettier (코드 포맷팅 도구)

### 개념
- Prettier는 코드 스타일을 일관되게 유지하는 도구입니다.
- 팀 내에서 코드 스타일 규칙을 일일이 논의하지 않고, Prettier가 자동으로 코드를 정리하여 스타일의 일관성을 보장합니다.

### 주요 기능
- **자동 포맷팅**: 코드를 작성한 후, Prettier가 자동으로 코드 스타일을 정리합니다.
- **일관된 코드 스타일 유지**: 여러 개발자가 함께 작업하더라도 코드 스타일에 차이가 나지 않도록 보장합니다.
- **형식만 수정**: 코드의 기능적인 부분은 건드리지 않고, 스타일만 수정합니다.

### 코드 예시
#### 자동 공백 추가 및 포맷팅
```javascript
function greet(name){console.log("Hello, " + name);}
greet('Alice');
```
Prettier는 위 코드를 자동으로 포맷하여 다음과 같이 변환합니다:
```javascript
function greet(name) {
  console.log('Hello, ' + name);
}

greet('Alice');
```

#### 따옴표 스타일 변경
```javascript
const greeting = "Hello, world!";
```
Prettier는 설정에 따라 작은따옴표로 변환할 수 있습니다:
```javascript
const greeting = 'Hello, world!';
```

#### 마지막 항목 뒤에 콤마 추가
```javascript
const fruits = [
  'apple',
  'banana',
  'cherry'
];
```
Prettier는 `trailingComma` 설정에 따라 마지막 항목 뒤에도 콤마를 추가할 수 있습니다:
```javascript
const fruits = [
  'apple',
  'banana',
  'cherry',
];
```

---

## 3. ESLint와 Prettier 통합

### 개념
- ESLint와 Prettier는 서로 보완적인 역할을 합니다.
- ESLint는 코드의 품질과 문법을 검사하고, Prettier는 코드의 스타일을 일관되게 유지합니다.
- 두 도구를 함께 사용하면 코드 품질과 스타일을 동시에 관리할 수 있습니다.

### 설정 예시
#### ESLint와 Prettier를 통합하여 사용하기
`eslint-config-prettier`와 `eslint-plugin-prettier`를 설치하여 ESLint가 Prettier의 규칙을 검사하도록 설정할 수 있습니다.

**.eslintrc.json 설정 예시**
```json
{
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier"
  ],
  "plugins": ["react", "@typescript-eslint", "prettier"],
  "rules": {
    "prettier/prettier": "error",  // Prettier 규칙 위반 시 오류 발생
    "react/prop-types": "off",
    "@typescript-eslint/explicit-module-boundary-types": "off"
  }
}
```

### 통합된 코드 예시
```javascript
const greet = (name) => {
  console.log(`Hello, ${name}`);
};

greet('Alice');
```
위 코드는 ESLint로 품질 검사를 받고, Prettier로 포맷팅이 되어 일관된 스타일과 오류 없는 코드를 유지합니다.

---

## 결론
- **ESLint**는 코드 품질과 규칙 준수를 관리하는 도구입니다.
- **Prettier**는 코드 스타일을 자동으로 일관되게 유지하는 도구입니다.
- 두 도구는 서로 보완적으로 작동하며, 품질 검사와 스타일 포맷팅을 동시에 관리할 수 있습니다.
- ESLint는 코드의 문법적 오류를, Prettier는 코드의 스타일을 담당하여 개발자가 더 나은 코드를 작성할 수 있도록 돕습니다.
