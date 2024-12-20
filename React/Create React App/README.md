# React와 Create React App

## 1. Create React App (CRA)

**Create React App(CRA)** 는 React 애플리케이션을 시작할 때 사용할 수 있는 도구로, 웹팩(Webpack), Babel, ESLint, Jest 등과 같은 개발 도구들을 자동으로 설정해줍니다. CRA는 기본적인 설정을 빠르게 해주어, 개발자는 애플리케이션에만 집중할 수 있게 도와줍니다.

### CRA 사용 방법
- **Node.js**가 설치되어 있어야 합니다.
- 새로운 React 프로젝트를 생성하려면 다음 명령어를 사용합니다:

```bash
npx create-react-app my-app
```
- 위 명령어는 `create-react-app` 템플릿을 다운로드하고, 새로운 React 프로젝트를 생성합니다.

---

## 2. npm (Node Package Manager)

**npm**은 Node.js의 패키지 관리자입니다. JavaScript 및 Node.js 프로젝트의 의존성 관리와 패키지 설치에 주로 사용됩니다.

### 주요 기능
1. **패키지 설치**: 라이브러리나 패키지를 설치하고 관리합니다.
   ```bash
   npm install <package-name>
   ```
2. **스크립트 실행**: `package.json` 파일에 정의된 스크립트를 실행할 수 있습니다.
   ```bash
   npm run dev
   ```
3. **의존성 관리**: 프로젝트의 의존성 목록을 `package.json` 파일에 기록하여 다른 개발자들이 동일한 환경에서 작업할 수 있도록 합니다.

---

## 3. npx (Node Package eXecute)

**npx**는 npm의 실행 도구로, 패키지를 설치하지 않고도 임시로 실행할 수 있게 도와줍니다.

### 주요 특징
- 최신 버전의 패키지를 바로 실행합니다.
- 패키지를 로컬에 설치하지 않고 실행할 수 있습니다.

### 사용 예시
```bash
npx create-react-app my-app
```
`npx`는 패키지 실행을 위한 최신 버전을 항상 사용하도록 보장합니다.

---

## 4. Yarn

**Yarn**은 npm을 대체하는 또 다른 패키지 관리자입니다. 속도, 안정성, 그리고 보안 등을 강화한 기능을 제공합니다.

### 주요 기능
1. **빠른 속도**: Yarn은 캐싱을 통해 패키지 설치 속도를 대폭 향상합니다.
2. **정확한 의존성 관리**: `yarn.lock` 파일을 사용하여 프로젝트의 의존성을 정확히 일치시킵니다.

### 사용 예시
```bash
yarn add <package-name>
```

---

## 5. Node.js

**Node.js**는 JavaScript를 서버 사이드에서도 실행할 수 있게 해주는 런타임 환경입니다.

### 주요 특징
- **V8 JavaScript 엔진 기반**: 빠르고 효율적인 코드 실행.
- **서버 사이드 애플리케이션 개발**: 비동기 처리와 이벤트 기반 프로그래밍 지원.

React 애플리케이션 개발 시, Node.js는 주로 개발 도구와 서버 사이드 렌더링(SSR) 환경에서 사용됩니다.

---

## 6. Vite

**Vite**는 빠른 빌드 도구이자 개발 서버로, 최신 웹 개발 환경에 최적화된 도구입니다.

### 주요 특징
1. **핫 모듈 교체(HMR)**: 코드 변경 시 빠르게 업데이트하여 개발 속도 향상.
2. **빠른 빌드**: ES 모듈을 기반으로 하여 빌드 속도가 빠릅니다.
3. **가벼운 설정**: 간단한 설정으로 시작 가능.

### Vite 사용 방법
1. **Vite 프로젝트 생성**:
   ```bash
   npm create vite@latest my-vite-app --template react-ts
   ```
2. **Vite 실행**:
   ```bash
   cd my-vite-app
   npm install
   npm run dev
   ```

---

## 요약
- **Create React App (CRA)**: React 애플리케이션 시작 도구로, 빠르게 기본 설정을 제공합니다.
- **npm**: Node.js의 패키지 관리자이며, 의존성 설치와 관리에 사용됩니다.
- **npx**: 패키지를 설치하지 않고 실행할 수 있는 도구로, 최신 버전을 자동 실행합니다.
- **Yarn**: 빠르고 안정적인 패키지 관리자입니다.
- **Node.js**: JavaScript 런타임 환경으로, 서버 사이드 개발에 사용됩니다.
- **Vite**: 빠른 빌드와 개발 서버를 제공하며, React 프로젝트에서 빠른 개발 환경을 제공합니다.
