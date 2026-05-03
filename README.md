# 학번: 202130233
# 이름: 최동운

REACT-1수업

3월11일

### Git의 학습 방법
- [초급을 위한 필수 명령어]
    - git init
    - git add .
    - git commit -m "설명"
    - git remote add origin URL

- [고급]
    - Pull Request(PR), 충돌 해결, Git 기록 정리 등의 학습이 목표
    - 이 단계에서는 "*Git 히스토리를 정리하는 법과 PR를 활용한 협업*"이 중요
- [고급을 위한 명령어]
    - git pull request
    - git fetcch-pick <commit-id>
    - git reset --soft HEAD~1
    - git revert <commit-id>
    - git reflog
### .gitignore
- Git 버전 관리에서 제외할 파일이나 디렉터리 목록을 정의하는 설정 파일
- .gitignore 파일 생성후 필요한 파일을 입력

### Node.js
- 라이언 달은 2009년 Node.js를 발표
- 비동기 논 블로킹 방식으로 고성능 처리 가능
- javascript 풀스택 개발 가능
- 활발한 생태계 : npm을 통해 다양한 패키지 사용 가능

- 경량 서버 개발에 적합
- 실시간 데이터 처리가 강력
#### React 이전과 이후의 개발 방식의 차이
* 이전
1. HTML과 CSS를 이용하여 화면을 만들고 
2. JavaScript로 DOM을 직접 조작
3. 특정 이벤트 발생 -> 필요한 부분만 수정
4. 화면이 복잡해질 수록 수정과 DOM 추적이 어려워짐
* 이후(React가 나온 이후)
1. 화면을 직접 고치지 않고 state를 바꾸면, 화면은 다시 계산됨 -> DOM을 조작하지 않고 렌더링을 함
    - React에서 렌더링이란 "현재 상태(state)를 기준으로 UI를 다시 계산하는 과정
2. 개발자는 DOM을 어떻게 고칠지를 고민하지 말고, 상태가 무엇인지만 정의하면 됨
#### 공식 문서에서 소개하는 React
- React를 잘 쓴다는 것은 상태와 렌더링의 관계를 명확하게 설명할 수 있고, 사용할 수 있는것
1. 왜 이 상태(state)가 여기 있어야 하는지 설명할 수 있어야함
2. 왜 이 컴포넌트가 다시 렌더링 되는지를 설명할 수 있어야 함
3. 왜 effect가 필요한지 혹은 필요 없는지를 설명할 수 있어야 함
#### React를 잘 쓴다는 것의 의미
- UI를 컴포넌트 단위로 개발해서 레고를 조립하듯이 완성


_________________________________________________________________________________________


3월18일
###React 프로젝트

-[삽입 방법]

-React 프레임워크를 사용하지 않고 직접 React 앱을 개발하는 방법.
-기존 프로젝트 일부에만 React를 연결하는 방법.
-새로운 React 앱을 개발하는 경우의 설치 방법.
-프로젝트를 생성해도 git은 직접해야 합니다.

-[구성요소 전]

-부품을 사용할 수 있나요?
-어떤 기능을 수행합니까?
-유니버설이 포함되어 있습니까?
-구성 요소 이름은 무엇으로 해야 할까요?
-카페인에 대해 뭐라구요?
-나의 첫 번째 구성 요소 구성 요소 만들기



_________________________________________________________________________________________

2026-03-25

###Vite에서 SWC가 사라진 이유

-SWC (Speedy Web Compiler)

-Rust 기반으로 만들어진 고속 컴파일러
-Babel을 대체하기 위함
-TypeScript → JavaScript 변환(트랜스파일링)에 강점
-Next.js 등 최신 프레임워크에서 사용
-Oxc (Oxidation Compiler)

-ESLint, Prettier, TypeScript 기능까지 통합하려는 차세대 도구
-파싱 속도가 SWC보다 훨씬 빠름 (최대 3배 이상)
-린팅/정적 분석 성능이 매우 뛰어남

----------------------------------------------------------------------------

React 컴포넌트

```jsx
export default function Profile() {
    return(
        <>
        </>
    )
}
```


###컴포넌트 분리와 사용

(예시)

// 분리
```jsx
// Profile.jsx
export default function Profile() {
    return <img src="..."/>
}


// 사용
// App.jsx
import Profile from "./Profile"

export default function App() {
    return <Profile/>
}
```


-[컴포넌트 작성 규칙]

-생성 과정 - 파일명과 컴포넌트 이름을 동일하게 맞추기 - export default 또는 export 사용 - 함수 내부에서 JSX 반환

-[사용 방법]
-import로 불러오기
-<컴포넌트명/> 형태로 사용

----------------------------------------------------------------------------------------------------------------------------------------

-[컴포넌트 중첨 (Nesting)]

-컴포넌트 안에서 다른 컴포넌트 사용하는 구조

(예시)

```jsx
function Gallery() {
    return (
        <>
            <Profile/>
            <Profile/>
        </>
    )
}
```

-컴포넌트 안에 선언이 아니라 컴포넌트를 호출해서 사용하는 것
---------------------------------------------------------------------------------------------------------------------------------------------------


-[React 렌더링 구조]

-컴포넌트 → App.jsx → main.jsx → index.html
-대문자 = 컴포넌트, 소문자 = HTML


-------------------------------------------------

-[Export 방식 차이]

```javascript
// Default Export
export default function A() {}
import A from "./A"

-이름 변경 가능
-파일당 1개만 가능


-[Named Export]
// Named Export
export function A() {}
import { A } from "./A"
```
-이름 반드시 동일
-여러 개 export 가능


-[다양한 import 방식]

```javascript
import { A } from "./file"
import { A, B } from "./file"
import { A as C } from "./file"
import * as All from "./file"
```

-[Named Export 추천 이유]
-이름이 강제되어 협업 시 혼동 감서
-리팩토링 시 안전
-트리 쉐이킹(Tree Shaking)에 유리


---------------------------------------------------------------------------------------------



-[JSX 개념 정리]

-JSX란?
JavaScript 안에서 HTML처럼 UI를 작성할 수 있게 해 주는 문법

-[JSX 규칙 3가지]
1.반드시 하나의 부모 요소로 감싸기
2.모든 태그는 닫기
3.속성은 camelCase 사용 ex) <img className="icon" />



-[JSX를 사용하는 이유]

-기존 방식
-HTML / CSS / JS 분리
-React 방식
-UI와 로직이 강하게 연결됨


-[Key Takeaways]

-1.React는 컴포넌트 기반 구조
-2.JSX를 사용해 UI를 직관적으로 작성
-3.Named Export가 협업에 유리
-4.Vite는 점점 더 빠른 Rust 기반 도구(Oxc 등)로 발전 중

--------------------------------------------------------------------------------------------------------------



# 📅 4월 1일 - React JSX & Props 학습 정리

---

## 📌 1. JSX 개요

### ✔ JSX란?

JSX는 **JavaScript 안에서 HTML 형태의 코드를 작성할 수 있는 문법**이다.

👉 JavaScript + HTML

### ✔ 특징

* UI와 로직을 함께 작성 가능
* 코드가 직관적이고 가독성이 좋음
* React에서 UI를 만들 때 핵심적으로 사용됨

---

## 📌 2. 기본 개념 정리

| 개념        | 설명                       |
| --------- | ------------------------ |
| Tag       | `<div>`, `<li>` 같은 요소 이름 |
| Element   | 태그 + 내용 전체               |
| Attribute | HTML 속성 (`src`, `alt` 등) |
| Property  | JS에서 변경되는 동적 값           |

---

## 📌 3. JSX에서 JavaScript 사용

### ✔ 4가지 방법

1. 문자열 전달
2. `{}`로 변수 사용
3. `{}`로 함수 호출
4. `{}`로 객체 사용

---

### ✔ 예시 코드

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

## 📌 4. JSX 문법 핵심

### ✔ 변수 출력

```jsx
<h1>Hello, {name}</h1>
```

### ✔ 속성에 값 전달

```jsx
<img src={reactLogo} />
```

### ✔ 주의사항

* `{}` 없이 변수 사용 ❌
* `" "` 사용 시 문자열로 인식됨
* JSX 안에서는 반드시 `{}` 사용

---

## 📌 5. Props 개요

### ✔ props란?

컴포넌트 간 데이터를 전달하는 방법

👉 부모 → 자식 방향

---

### ✔ 특징

* 읽기 전용 (수정 불가)
* 다양한 타입 전달 가능 (문자열, 객체, 함수 등)
* HTML 속성과 유사한 형태

---

## 📌 6. Props 사용 방법

### ✔ 부모 컴포넌트

```jsx
<Items name="여분 옷" isPacked={true} />
```

### ✔ 자식 컴포넌트

```jsx
function Items({ name, isPacked }) {
  return <li>{name}</li>;
}
```

---

## 📌 7. 객체로 Props 전달

### ✔ 예시

```jsx
const imageInfo = {
  src: "reactLogo.png",
  alt: "React Logo"
};

<ChildComp imageInfo={imageInfo} width={100} height={100} />
```

### ✔ 자식 컴포넌트

```jsx
function ChildComp({ imageInfo, width, height }) {
  return (
    <img 
      src={imageInfo.src}
      alt={imageInfo.alt}
      width={width}
      height={height}
    />
  );
}
```

---

## 📌 8. Props 기본값

```jsx
function ChildComp({ imageInfo, width, height = 300 }) {
  return <img src={imageInfo.src} width={width} height={height} />;
}
```

👉 값이 없을 때 기본값 적용

---

## 📌 9. Spread 문법

### ✔ 개념

객체를 펼쳐서 props로 전달

```jsx
const props = { name: "Kim", age: 20 };

<User {...props} />
```

👉 아래와 동일

```jsx
<User name="Kim" age={20} />
```

---

### ✔ 사용 목적

* props forwarding
* 코드 간결화
* 여러 props 한 번에 전달

---

### ✔ 예시

```jsx
<NameCard {...userData} />
```

---

## ⚠️ Spread 사용 시 주의

* 어떤 값이 전달되는지 확인 어려움
* 불필요한 데이터 전달 가능
* props 덮어쓰기 가능

```jsx
<Profile {...userData} age={30} />
```

👉 age 값이 덮어쓰기 됨

---

## 📌 10. 핵심 정리

* JSX는 React의 핵심 문법 (JS + HTML)
* `{}`를 사용해 JavaScript 값 사용
* props는 컴포넌트 간 데이터 전달 도구
* 객체 형태로 props 전달 가능
* spread 문법으로 코드 간결화 가능
* 단, 가독성과 사용 목적을 고려해야 함

---

## 🚀 느낀 점

* JSX를 통해 UI와 로직을 함께 작성하는 방식이 인상적이었다.
* props를 활용하면 컴포넌트를 재사용하기 쉬워진다.
* spread 문법은 편리하지만 상황에 맞게 사용하는 것이 중요하다.




-----------------------------------------------------------------------------------------------------------------------------------------

# 📅 4월 8일 - React 학습 정리

---

## 📌 1. 조건부 렌더링 (Conditional Rendering)

React에서는 **조건에 따라 다른 UI를 출력**할 수 있으며, 이를 *조건부 렌더링*이라고 한다.

### ✔ 구현 방법

* `if문`
* `삼항 연산자 (condition ? A : B)`
* `논리 연산자 (&&)`

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

## 📌 2. Spread 문법

객체 데이터를 한 번에 props로 전달할 때 사용한다.

### ✔ 예시

```jsx
<NameCard {...userData} />
```

👉 객체의 모든 값이 props로 전달됨

```jsx
<NameCard id={1} name="홍길동" {...userData} />
```

👉 직접 전달 + spread 함께 사용 가능

---

## 📌 3. 조건부 렌더링 활용 (짐 리스트 예제)

### ✔ 기능

* `isPacked` 값에 따라 UI 변경

### ✔ 기본 코드

```jsx
export default function Item({ name, isPacked }) {
  return <li>{name} {isPacked ? '✅' : ''}</li>;
}
```

### ✔ JSX 활용

```jsx
export default function Item({ name, isPacked }) {
  return (
    <li>
      {isPacked ? <del>{name} ✅</del> : name}
    </li>
  );
}
```

---

## 📌 4. 다양한 조건 처리 방법

### ✔ 1. AND 연산자

```jsx
<li>
  {name} {isPacked && '✅'}
</li>
```

👉 조건이 true일 때만 출력

---

### ✔ 2. 변수 활용 (if문)

```jsx
export default function Item({ name, isPacked }) {
  let itemContent = name;

  if (isPacked) {
    itemContent = <del>{name + ' ✅'}</del>;
  }

  return <li>{itemContent}</li>;
}
```

👉 복잡한 조건일 때 가독성 ↑

---

## 📌 5. 리스트 렌더링 (List Rendering)

React에서는 배열 데이터를 기반으로 UI를 반복 생성한다.

### ✔ 핵심 개념

* `map()` → 리스트 생성
* `filter()` → 조건 필터링
* `key` → 각 요소 구분 (필수)

---

### ✔ 예시

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

---

## 📌 6. 핵심 정리

* 조건부 렌더링으로 UI를 상황에 맞게 변경 가능
* 삼항 연산자, &&, if문을 상황에 맞게 사용
* props로 데이터 전달
* 배열 + map()으로 리스트 렌더링
* key는 반드시 필요

---

## 🚀 느낀 점

* JSX 안에서도 다양한 조건 처리가 가능하다는 점이 인상적이었다.
* 코드가 길어질수록 가독성을 고려하는 것이 중요하다.
* 데이터 기반으로 UI를 만드는 것이 React의 핵심이라는 것을 이해했다.


__________________________________________________________________________________________________

4월29일

📘 React 웹 개발: 컴포넌트 & 스타일링 정리
📌 목차
1. 컴포넌트 개발과 스타일 세팅
2. 스타일링 방식
3. 로컬 스타일링 (CSS Module)
4. 버튼 컴포넌트 구현
5. 이벤트 핸들러
6. 이벤트 전파
7. 컴포넌트 이벤트 처리
1. 컴포넌트 개발과 스타일 세팅
1-1. 컴포넌트 개발
웹 개발은 컴포넌트 단위로 구성됨
구조 설계 시 선택자 사용:
id → 특정 요소 (거의 사용 안 함)
class → 여러 요소에 공통 적용 (주로 사용)

👉 중요

JavaScript에서 id 선택자는 효율성이 떨어져 잘 사용하지 않음
유지보수 & 재사용성을 위해 class 중심 설계

👉 실무 팁

직접 만들기보다 외부 컴포넌트 활용 (생산성 ↑)
1-2. 스타일 세팅과 중괄호
JSX에서 스타일은 {} 사용 → 객체 형태
<button style={{ backgroundColor: 'blue' }}>

👉 하지만 문제점:

{} 안에 또 {} → 가독성 ↓
유지보수 어려움

❗ React에서는 권장하지 않음 (특히 큰 프로젝트)

1-3. 카멜 케이스 vs 파스칼 케이스
방식	설명
camelCase	backgroundColor
PascalCase	BackgroundColor

👉 JSX 스타일에서는 camelCase 사용 필수

style={{ backgroundColor: 'blue' }}
2. 스타일링 방식
📌 전체 방식 정리
일반 CSS
인라인 스타일
CSS-in-JS
CSS 프레임워크
CSS Module (React 권장)
2-1. 일반 CSS
.button {
  background: blue;
  color: white;
}
import './styles.css';

<button className="button">Click</button>
👍 장점
쉽고 직관적
👎 단점
전역 충돌 발생 가능
유지보수 어려움
2-2. 인라인 스타일
<button style={{ backgroundColor: 'blue', color: 'white' }}>
👍
빠름
조건부 스타일 가능
👎
재사용성 낮음
유지보수 어려움
2-3. CSS-in-JS

대표 라이브러리:

styled-components
emotion
JSS
👍
컴포넌트 단위 관리
자동 클래스 생성 (충돌 방지)
동적 스타일링 가능
👎
번들 사이즈 증가
학습 필요
2-4. CSS 프레임워크

대표:

Tailwind CSS
Bootstrap
Bulma
<button className="bg-blue-500 text-white px-4 py-2">
👍
빠른 개발
디자인 통일
👎
클래스 길어짐
가독성 저하

👉 최근 트렌드: Tailwind 많이 사용

3. 로컬 스타일링 (CSS Module)
3-1. 개념
컴포넌트 단위 스타일 관리
클래스 이름 자동 해싱 → 충돌 방지
import styles from './Button.module.css';

<button className={styles.button}>
3-2. 특징
파일명: Button.module.css
전역이 아닌 로컬 스코프
변수처럼 사용 가능

👉 권장:

클래스 기반 스타일링
태그 선택자 사용 최소화
3-3. 장점
유지보수 쉬움
재사용성 높음
충돌 없음

👉 폴더 구조 예시

components/
 └── Button/
      ├── Button.jsx
      ├── Button.module.css
      └── index.js
4. 버튼 컴포넌트 구현
4-1. 기본 생성
export default function Button() {
  return <button>Click</button>;
}
4-2. 스타일 적용
.button {
  background: blue;
  padding: 10px;
}
<button className={styles.button}>Click</button>
4-3. 스타일 관리
글로벌 CSS → 초기 설정용
컴포넌트 스타일 → module 사용

👉 혼동 방지:

항상 module 기반 스타일 추천
5. 이벤트 핸들러
5-1. 개념
사용자 행동(클릭 등)에 반응하는 함수
function handleClick() {
  alert("클릭됨!");
}
<button onClick={handleClick}>Click</button>
5-2. 특징
이벤트 발생 시 실행
사용자 인터랙션 처리

👉 활용 예:

로그인
결제
데이터 변경
6. 이벤트 전파
6-1. 개념
이벤트가 부모 → 자식 / 자식 → 부모로 전달됨

👉 예:

버튼 클릭 → 부모 컴포넌트까지 전달
6-2. 중요 포인트
이벤트 흐름 이해 필수
필요 시 전파 제어 가능
event.stopPropagation();
7. 컴포넌트 이벤트 처리
7-1. 이벤트 설정
<button onClick={handleClick}>

👉 주의:

() 붙이면 즉시 실행됨 ❌
함수 이름만 전달해야 함 ⭕
7-2. 핸들러 정의
function handleClick() {
  console.log("클릭");
}

👉 위치:

컴포넌트 내부 (권장)
또는 외부 모듈
7-3. 이벤트 전달
<Button onClick={handleClick} />

👉 핵심:

함수 자체를 전달
실행은 컴포넌트 내부에서 발생
🚀 최종 정리
✅ React 스타일링 추천 순서
CSS Module ⭐ (가장 추천)
Tailwind CSS
CSS-in-JS
일반 CSS
인라인 스타일 (최소 사용)
✅ 핵심 포인트
컴포넌트 기반 개발 필수
스타일은 로컬화
이벤트는 함수로 전달
유지보수 & 재사용성 최우선










