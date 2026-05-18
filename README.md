# 📘 Git & React 수업 정리

> 최신 날짜 기준으로 위에서 아래 순으로 정리한 README.md 입니다.

---



# 📘 React 수업 정리 (5월 13일)

## 📌 학습 주제
- React 컴포넌트 분리
- 이벤트 핸들러(Event Handler)
- props 전달
- CSS Module 사용
- `onClick` 이벤트 처리
- 이벤트 버블링(Event Bubbling)
- `stopPropagation()` 사용

---

# 1️⃣ Toolbar 컴포넌트 만들기

## 📂 파일 구조 예시

```plaintext
src
 ┣ components
 ┃ ┣ ButtonCom
 ┃ ┃ ┣ ButtonCom.jsx
 ┃ ┃ ┣ ButtonCom.module.css
 ┃ ┣ ToolBar.jsx
 ┣ assets
 ┃ ┣ sample.mp4



----------------------------------------------------






📌 Toolbar.jsx


import { handlePlay, handleStop } from "./handle";
import ButtonCom from "./ButtonCom";
import style from "./ButtonCom.module.css";

import sampleVideo from "../../assets/sample.mp4";

export default function Toolbar() {
  return (
    <>
      <nav>
        <ButtonCom
          message="videoPlayer"
          handle={handlePlay}
          style={style.myButton}
        >
          Play
        </ButtonCom>

        <ButtonCom
          message="videoPlayer"
          handle={handleStop}
          style={style.myButton}
        >
          Stop
        </ButtonCom>
      </nav>

      <section>
        <video src={sampleVideo} controls width="350" />
      </section>
    </>
  );
}

----------------------------------------------




2️⃣ props 전달
📌 예시

<ButtonCom handle={handlePlay}>


✅ 설명
handlePlay 함수를 props로 전달
버튼 클릭 시 함수 실행



----------------------------------------------------------






3️⃣ children 사용
📌 예시

Play

✅ 설명
컴포넌트 태그 사이 내용은 children으로 전달됨




-------------------------------------------


4️⃣ CSS Module 사용
📌 Bubble.module.css

.title {
  font-size: 30px;
  font-weight: bold;
}

.button {
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
}




📌 CSS Module 불러오기

import style from "./Bubble.module.css";





📌 스타일 적용

<h1 className={style.title}>Bubble</h1>

✅ 특징
클래스 이름 충돌 방지
컴포넌트별 스타일 관리 가능
유지보수가 쉬움


5️⃣ 이벤트 핸들러(Event Handler)
📌 onClick 사용
<button onClick={() => alert("버튼 클릭")}>
  클릭
</button>
✅ 설명
버튼 클릭 시 이벤트 실행
화살표 함수 사용 가능
6️⃣ 이벤트 버블링(Event Bubbling)
📌 Bubble.jsx
function Button({ onClick, children }) {
  return (
    <button
      className={style.button}
      onClick={(e) => {
        e.stopPropagation();
        onClick();
      }}
    >
      {children}
    </button>
  );
}
7️⃣ stopPropagation()
📌 사용 방법
e.stopPropagation();
✅ 역할
이벤트 전파 중지
부모 요소로 이벤트 전달 차단
8️⃣ 이벤트 버블링 예시
📌 부모(nav) 이벤트
<nav onClick={() => alert("네비게이션바 클릭")}></nav>
📌 버튼 이벤트
<Button onClick={() => alert("버튼 클릭")}>
  버튼
</Button>
📌 결과 비교
🔹 stopPropagation() 사용 전
버튼 클릭
버튼 이벤트 실행
부모(nav) 이벤트도 실행

➡ alert 2개 실행

🔹 stopPropagation() 사용 후
버튼 클릭
버튼 이벤트만 실행

➡ alert 1개만 실행

📚 수업 핵심 정리
개념	설명
props	부모 → 자식 데이터 전달
children	컴포넌트 태그 사이 내용
onClick	클릭 이벤트 처리
CSS Module	컴포넌트 전용 CSS
Event Bubbling	이벤트가 부모로 전파됨
stopPropagation	이벤트 전파 차단
🎯 최종 요약

이번 수업에서는 React의 이벤트 처리 방식과 CSS Module 사용 방법을 학습했다.

특히:

onClick 이벤트 처리
props를 이용한 함수 전달
이벤트 버블링(Event Bubbling)
stopPropagation()

개념이 핵심이었다.

또한 CSS Module을 통해 컴포넌트별 스타일을 안전하게 관리하는 방법도 배웠다.




# 📅 2026-04-29 — React 웹 개발: 컴포넌트와 스타일링

## 😀 목차
- 컴포넌트 기반 개발
- 스타일링 방식
- CSS Module
- 버튼 컴포넌트
- 이벤트 핸들러
- 이벤트 객체
- 이벤트 처리 방식

---

## 1. 컴포넌트 기반 개발

React 웹 개발은 컴포넌트(Component) 단위로 구성됩니다.

### ✔ id 와 class 차이

#### `id`
- 특정 요소에만 사용
- 거의 사용하지 않음 ❌

#### `class`
- 여러 요소에 재사용 가능
- 권장 방식 ✅

### ✔ 핵심 내용
- `class` 기반 설계가 유지보수에 유리
- 재사용 가능한 컴포넌트 설계 중요

---

## 2. 스타일링 방식

### 2-1. 일반 CSS

```css
.button {
  background: blue;
  color: white;
}
```

```jsx
import './styles.css';

<button className="button">Click</button>
```

#### ✔ 장점
- 간단함

#### ❌ 단점
- 클래스 충돌 가능

---

### 2-2. 인라인 스타일

```jsx
<button style={{ backgroundColor: 'blue', color: 'white' }}>
```

#### ✔ 장점
- 빠르게 작성 가능

#### ❌ 단점
- 가독성 낮음
- 유지보수 어려움

---

### 2-3. CSS-in-JS

대표 라이브러리:
- Styled Components
- Emotion
- JSS

#### ✔ 장점
- 스타일 충돌 방지

#### ❌ 단점
- 추가 학습 필요

---

### 2-4. CSS 프레임워크

```jsx
<button className="bg-blue-500 text-white px-4 py-2">
```

대표 예시:
- Tailwind CSS
- Bootstrap
- Bulma

#### 👉 최근 추세
- Tailwind CSS 사용 증가

---

## 3. CSS Module

```jsx
import styles from './Button.module.css';

<button className={styles.button}>
```

### ✔ 특징
- 컴포넌트별 스타일 관리 가능
- 클래스 이름 자동 생성
- 스타일 충돌 방지

---

## 4. 버튼 컴포넌트

```jsx
export default function Button() {
  return <button>Click</button>;
}
```

```css
.button {
  background: blue;
  padding: 10px;
}
```

```jsx
<button className={styles.button}>Click</button>
```

---

## 5. 이벤트 핸들러

```jsx
function handleClick() {
  alert("클릭됨!");
}

<button onClick={handleClick}>Click</button>
```

---

## 6. 이벤트 객체

```jsx
event.stopPropagation();
```

---

## 7. 이벤트 처리 방식

```jsx
onClick={handleClick}   // ⭕
onClick={handleClick()} // ❌
```

---

## ✅ 최종 정리

### 추천 스타일링 순서
1. CSS Module ⭐
2. Tailwind CSS
3. CSS-in-JS
4. 일반 CSS
5. 인라인 스타일

### 핵심 내용
- 컴포넌트 기반 개발
- 스타일 재사용 중요
- 이벤트는 함수 형태로 전달
- 유지보수 고려 필수

---

# 📅 2026-04-08 — React 조건부 렌더링 & 리스트 렌더링

## 1. 조건부 렌더링 (Conditional Rendering)

React에서는 조건에 따라 다른 UI를 출력할 수 있습니다.

### ✔ 구현 방법
- if 문
- 삼항 연산자
- 논리 연산자 `&&`

### ✔ 예시

```jsx
function App({ isLogin }) {
  return (
    <>
      {isLogin ? <h1>환영합니다</h1> : <h1>로그인 해주세요</h1>}
    </>
  );
}
```

---

## 2. Props 전개 문법 (Spread)

```jsx
<NameCard {...userData} />
```

### ✔ 특징
- 객체 데이터를 한 번에 전달 가능

---

## 3. 조건부 UI 변경

```jsx
export default function Item({ name, isPacked }) {
  return <li>{name} {isPacked ? '✅' : ''}</li>;
}
```

---

## 4. AND 연산자 활용

```jsx
<li>
  {name} {isPacked && '✅'}
</li>
```

---

## 5. if 문 활용

```jsx
export default function Item({ name, isPacked }) {
  let itemContent = name;

  if (isPacked) {
    itemContent = <del>{name + ' ✅'}</del>;
  }

  return <li>{itemContent}</li>;
}
```

---

## 6. 리스트 렌더링

```jsx
const heroes = [
  '스파이더맨: 피터 파커',
  '아이언맨: 토니 스타크',
  '배트맨: 브루스 웨인'
];

export default function MovieHeroes() {
  const listHeroes = heroes.map(hero => <li>{hero}</li>);

  return (
    <ul>
      {listHeroes}
    </ul>
  );
}
```

### ✔ 핵심 내용
- `map()` : 리스트 생성
- `filter()` : 조건 필터링
- `key` : 필수 속성

---

# 📅 2026-04-01 — React JSX & Props 학습 정리

## 1. JSX 개요

### ✔ JSX란?
JavaScript 안에서 HTML 형태의 UI를 작성할 수 있는 문법

> JavaScript + HTML

---

## 2. JSX에서 JavaScript 사용

```jsx
export default function UseJsx() {
  const name = "React";

  function formatDate(date) {
    return new Intl.DateTimeFormat("en-US", {
      weekday: "long",
    }).format(date);
  }

  return (
    <>
      <h1>Hello, {name}!</h1>
      <p>Today is {formatDate(new Date())}</p>
    </>
  );
}
```

---

## 3. Props 개요

### ✔ Props란?
컴포넌트 간 데이터를 전달하는 방법

> 부모 → 자식 전달

---

## 4. Props 사용 예시

### 부모 컴포넌트

```jsx
<Items name="여벌 옷" isPacked={true} />
```

### 자식 컴포넌트

```jsx
function Items({ name, isPacked }) {
  return <li>{name}</li>;
}
```

---

## 5. Spread 문법

```jsx
const props = { name: "Kim", age: 20 };

<User {...props} />
```

---

# 📅 2026-03-25 — React 컴포넌트 & JSX

## 1. Vite에서 SWC가 사라진 이유

### SWC
- Rust 기반 컴파일러
- Babel 대체 목적
- TypeScript → JavaScript 변환

### Oxc
- ESLint + Prettier + TypeScript 기능 통합
- SWC보다 빠른 성능
- 정적 분석 강화

---

## 2. React 컴포넌트 기본 구조

```jsx
export default function Profile() {
  return (
    <>
    </>
  );
}
```

---

## 3. 컴포넌트 분리

### Profile.jsx

```jsx
export default function Profile() {
  return <img src="..." />;
}
```

### App.jsx

```jsx
import Profile from "./Profile";

export default function App() {
  return <Profile />;
}
```

---

## 4. JSX 규칙

1. 하나의 부모 요소로 감싸기
2. 모든 태그 닫기
3. camelCase 사용

예시:

```jsx
backgroundColor
```

---

## 5. Export 방식

### Default Export

```jsx
export default function A() {}
import A from "./A";
```

### Named Export

```jsx
export function A() {}
import { A } from "./A";
```

---

# 📅 2026-03-18 — React 프로젝트

## React 프로젝트 설치 방법

- React 프레임워크 없이 직접 개발
- 기존 프로젝트에 React 연결
- 새로운 React 앱 생성
- Git 저장소 직접 생성 가능

---

## 컴포넌트 개념

- 컴포넌트란 무엇인가
- 어떤 역할을 하는가
- 컴포넌트 이름 규칙
- 첫 번째 컴포넌트 만들기

---

# 📅 2026-03-11 — Git & Node.js 기초

## Git 학습 목표

### [초급]

```bash
git init
git add .
git commit -m "설명"
```

### 원격 저장소 연결

```bash
git remote add origin URL
```

---

## [고급]

### 학습 목표
- Pull Request(PR)
- 충돌 해결
- Git 히스토리 관리

### 중요 개념
- Git 히스토리 정리
- 협업 방식 이해

---

## Git 명령어

```bash
git pull
git cherry-pick
git reset --soft HEAD~1
git revert
git reflog
```

---

## .gitignore

Git 버전 관리에서 제외할 파일을 정의하는 설정 파일

```gitignore
node_modules/
.env
dist/
```

---

## Node.js

### 특징
- 2009년 Ryan Dahl 발표
- 비동기 처리 가능
- JavaScript 풀스택 개발 가능
- npm 패키지 사용 가능
- 서버 개발에 적합

---

## React 등장 이전과 이후

### React 이전
- HTML / CSS / JS 분리
- DOM 직접 조작
- 유지보수 어려움

### React 이후
- 상태(State) 기반 UI
- DOM 직접 조작 감소
- 컴포넌트 기반 개발

---

## React 핵심 개념

### ✔ 상태(State)
현재 UI 상태를 저장하는 데이터

### ✔ 렌더링(Rendering)
상태 변경 시 UI를 다시 그리는 과정

---

## React 핵심 철학

> UI를 컴포넌트 단위로 나누고  
> 레고 블록처럼 조립하여 개발한다.




