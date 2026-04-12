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



4월1일

## 6. JSX로 마크업 작성하기

JSX를 사용하기 위해 기본 용어를 구분해서 이해해야 한다.

---

### Tag (태그)
HTML과 같은 마크업에서 요소를 표시하기 위한 개별 기호이다.  
예: `<div>`, `<li>`

---

### Element (엘리먼트)
DOM(Document Object Model)의 구성 단위로,  
"여는 태그 + 내용 + 닫는 태그" 전체를 의미한다.  
DOM 노드(node)라고도 한다.

예:
```html
<p>엘리먼트 설명</p>


Attribute (속성)

태그의 행동을 제어하거나, 엘리먼트에 추가적인 정보를 제공하는 요소이다.
태그 내부에 작성한다.

예:

<img src="image.png" />
Property (프로퍼티)

DOM 객체 내부에 존재하는 동적인 속성이다.
JavaScript를 통해 제어되며, 현재 상태를 나타낸다.

예:
사용자가 input 태그에 글자를 입력하면
input의 property(value)는 변경되지만,
HTML의 attribute(value)는 처음 값 그대로 유지된다.

정리
Tag → 요소를 나타내는 이름
Element → 태그 + 내용 전체
Attribute → 추가 정보 (HTML에 작성)
Property → 동적인 값 (JS에서 변경)






## 6. JSX로 마크업 작성하기

### 6.3 JSX 안에서 자바스크립트 사용하기

JavaScript를 JSX에서 사용하는 방법은 총 4가지가 있다.

---

### 1. 따옴표로 문자열 전달
문자열을 그대로 전달할 때 사용한다.

---

### 2. 중괄호로 변수 사용
중괄호 `{}`를 사용하여 JavaScript 변수를 JSX 안에서 사용할 수 있다.

---

### 3. 중괄호로 함수 호출
중괄호 `{}` 안에서 JavaScript 함수를 호출할 수 있다.

---

### 4. 중괄호로 객체 사용
중괄호 `{}`를 사용하여 JavaScript 객체를 JSX에 적용할 수 있다.

---

## 실습

위에서 설명한 방법을 간단한 실습으로 확인한다.

---

### Step 1

- UseJsx라는 컴포넌트를 생성한다.
- name 변수에 문자열을 저장한다.
- JSX에서 name 변수를 출력한다.
- App 컴포넌트에서 UseJsx를 호출하여 화면에 출력한다.

---

### 예시 코드

```jsx
export default function UseJsx() {
  const name = "React";

  return (
    <>
      <h1>Hello, {name}</h1>
    </>
  );
}






## 1. 개요

### JSX란 무엇인가?

JSX는 JavaScript를 확장한 문법으로,  
JavaScript 파일 안에서 HTML과 비슷한 형태의 마크업을 작성할 수 있도록 해준다.

---

### 특징

- JSX는 간결한 문법 덕분에 많은 React 개발자들이 선호한다.
- 컴포넌트를 작성하는 다양한 방법이 있지만 JSX가 가장 직관적이다.

---

### 기존 방식

- HTML, CSS, JavaScript는 일반적으로 분리된 파일로 관리된다.

---

### 변화

- 웹이 점점 더 인터랙티브해지면서  
  화면의 구조(HTML)와 동작(JavaScript)이 밀접하게 연결되었다.

---

### JSX의 장점

- JavaScript 안에서 HTML을 함께 작성할 수 있어 효율적이다.
- 로직과 UI를 함께 관리할 수 있다.

---

### 정리

- JSX = JavaScript + HTML 문법
- React에서 UI를 만들 때 사용하는 핵심 문법





## 6. JSX로 마크업 작성하기

### 6.3 JSX 안에서 자바스크립트 사용하기

JavaScript를 JSX에서 사용하는 방법은 총 4가지가 있다.

---

### 1. 따옴표로 문자열 전달
문자열을 그대로 JSX에 전달하는 방법이다.

---

### 2. 중괄호로 변수 사용
중괄호 `{}`를 사용하여 JavaScript 변수를 JSX 안에서 사용할 수 있다.

---

### 3. 중괄호로 함수 호출
중괄호 `{}` 안에서 JavaScript 함수를 호출할 수 있다.

---

### 4. 중괄호로 객체 사용
중괄호 `{}`를 사용하여 JavaScript 객체를 JSX에 적용할 수 있다.

---

## 실습

위에서 설명한 4가지 방법을 간단한 실습으로 확인한다.

---

### Step 1

- UseJsx라는 컴포넌트를 생성한다.
- name 변수에 문자열을 저장한다.
- JSX에서 name 변수를 함께 출력한다.
- App 컴포넌트에서 UseJsx를 호출하여 출력 결과를 확인한다.

---

### 예시 코드

```jsx
export default function UseJsx() {
  const name = "React";

  return (
    <>
      <h1>Hello, {name}</h1>
    </>
  );
}




## 6. JSX로 마크업 작성하기

### Step 3

UseJsx 컴포넌트에서 함수를 사용하여
요일을 추가로 출력한다.

---

### 설명

- 이번 단계에서는 날짜의 요일을 반환하는 함수를 사용한다.
- 함수의 내부 동작을 이해하기보다는,
  컴포넌트에서 함수를 호출하는 방법에 집중한다.

---

### 구현 내용

- name 변수와 함께 문자열을 출력한다.
- formatDate 함수를 정의하여 요일을 반환한다.
- JSX 내부에서 함수를 호출하여 결과를 출력한다.

---

### 예시 코드

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



## 📌 JSX로 마크업 작성하기

JSX에서는 값을 출력하는 방법이 크게 두 가지로 나뉜다.

---

### 1. 중괄호 `{}`를 사용한 표현

JSX 태그 내부에서 JavaScript 값을 출력할 때는 `{}`를 사용한다.

```jsx
<h1>Hello, {name}!</h1>
```

* `{name}`처럼 변수나 표현식을 사용할 수 있다.
* 문자열이 아닌 JavaScript 값을 넣을 때 사용한다.

---

### 2. 속성(Attribute)에 값 전달하기

태그의 속성에 값을 넣을 때도 `{}`를 사용할 수 있다.

```jsx
<img src={reactLogo} />
```

* `reactLogo`는 변수로 처리된다.
* 따옴표(`""`)를 사용하면 문자열로 인식된다.

---

### ⚠️ 잘못된 사용 예시

#### ❌ JSX 내부에서 중괄호 없이 변수 사용

```jsx
<h1>Hello, React!</h1>   // 변수 출력 불가
```

#### ❌ 태그 안에서 `{}` 없이 표현식 사용

```jsx
<{tag}>Hello, React!</{tag}>   // 동작하지 않음
```

#### ❌ 속성에 따옴표 사용 시 변수 인식 불가

```jsx
<img src="reactLogo" />
```

* `"reactLogo"`는 문자열로 처리됨
* 변수 값을 사용하려면 `{}` 필요

---

### ✅ 정리

* JSX에서 JavaScript 값을 사용할 때는 `{}` 사용
* 태그 내부와 속성 모두 `{}`로 변수 전달 가능
* 따옴표(`""`)는 문자열을 의미하므로 변수 사용 시 주의





## 📌 React Props 개요

React에서 컴포넌트는 **props(properties의 약자)** 를 통해 서로 데이터를 주고받는다.

---

### 🔹 props란?

* props는 컴포넌트 간 데이터를 전달하는 방법이다.
* 부모 컴포넌트 → 자식 컴포넌트로 데이터가 전달된다.
* HTML의 속성과 비슷한 형태로 사용된다.

```jsx
<Items name="여분 옷" isPacked={true} />
```

---

### 🔹 props의 특징

* 문자열뿐만 아니라 다양한 JavaScript 값을 전달할 수 있다.

  * 객체(Object)
  * 배열(Array)
  * 함수(Function)
* 읽기 전용(Read-only)으로, 자식 컴포넌트에서는 수정할 수 없다.

---

### 📚 학습 내용

* 컴포넌트에 props를 전달하는 방법
* 컴포넌트에서 props를 읽는 방법
* props의 기본값(default props) 설정 방법
* JSX를 props로 전달하는 방법
* 시간에 따라 props가 변경되는 방식 이해

---

### ✅ 정리

* props는 컴포넌트 간 데이터 전달 도구
* 부모 → 자식 방향으로만 데이터 전달 가능
* 다양한 타입의 값 전달 가능
* 읽기 전용이므로 직접 수정 불가




## 📌 Props의 데이터 전달

props는 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 역할을 한다.

---

### 🔹 props 전달 방식

React에서는 JSX 태그의 속성 형태로 데이터를 전달한다.

```jsx id="6s6k0y"
<Items name="여분 옷" isPacked={true} />
```

* `name`, `isPacked` → props로 전달되는 데이터
* HTML의 속성과 유사한 형태로 사용됨

---

### 🔹 HTML 속성과의 관계

React에서 props는 HTML 속성과 비슷하게 동작한다.

예를 들어 `<img>` 태그의 경우:

```jsx id="4u9plg"
<img src="image.png" alt="이미지" width="200" height="200" />
```

* `src`, `alt`, `width`, `height` 모두 props로 전달됨
* HTML에서 사용하는 속성과 동일한 방식으로 사용 가능

---

### 🔹 특징

* props는 JSX 태그를 통해 전달된다.
* HTML 표준 속성과 동일하게 사용할 수 있다.
* 사용자 정의 props도 자유롭게 추가 가능하다.

---

### ✅ 정리

* props는 부모 → 자식으로 데이터 전달
* JSX 속성 형태로 전달
* HTML 속성과 동일한 방식으로 사용 가능




## 📌 컴포넌트에 props 전달하기

React에서 props는 부모 컴포넌트와 자식 컴포넌트 간의 데이터 전달에 사용된다.

---

### 🔹 부모 컴포넌트 (Parent Component)

* 자식 컴포넌트를 JSX 안에서 포함(import 및 호출)한다.
* 자식 컴포넌트에 데이터를 props 형태로 전달한다.

```jsx id="6g2m1v"
<Items name="여분 옷" isPacked={true} />
```

---

### 🔹 자식 컴포넌트 (Child Component)

* 부모로부터 전달받은 props를 이용해 UI를 구성한다.
* 전달받은 데이터를 기반으로 화면을 렌더링한다.
* 독립적으로 재사용이 가능하다.

```jsx id="jvkm4f"
function Items({ name, isPacked }) {
  return <li>{name}</li>;
}
```

---

### 🔹 props의 특징

#### 1. 단방향 데이터 흐름

* 데이터는 항상 **부모 → 자식** 방향으로만 전달된다.

#### 2. 읽기 전용 (Read-only)

* 자식 컴포넌트는 전달받은 props를 직접 수정할 수 없다.

#### 3. 다양한 데이터 타입 전달 가능

* 문자열, 숫자뿐만 아니라
  객체(Object), 배열(Array), 함수(Function)도 전달 가능

---

### ✅ 정리

* 부모 컴포넌트가 props를 통해 데이터를 전달한다.
* 자식 컴포넌트는 props를 받아서 UI를 구성한다.
* props는 단방향 흐름이며 수정할 수 없다.



## 📌 Props로 객체 전달하기

앞에서는 문자열과 숫자를 props로 전달하는 방법을 학습하였다.
이번에는 여러 데이터를 하나로 묶어 **객체 형태로 전달하는 방법**을 학습한다.

---

### 🔹 객체 형태로 props 전달

여러 속성을 하나의 객체로 묶어서 전달할 수 있다.

```jsx
const imageInfo = {
  src: "reactLogo.png",
  alt: "React Logo"
};

<ChildComp imageInfo={imageInfo} width={100} height={100} />
```

---

### 🔹 자식 컴포넌트에서 사용

전달받은 객체의 속성에 접근하여 사용할 수 있다.

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

### 🔹 특징

* 여러 데이터를 하나의 객체로 묶어 전달 가능
* 코드의 가독성과 재사용성이 향상됨
* 필요한 값만 선택적으로 사용할 수 있음

---

### 🔹 기존 방식과의 차이

```jsx
// ❌ 개별 전달
<ChildComp src="reactLogo.png" alt="logo" />

// ✅ 객체 전달
<ChildComp imageInfo={imageInfo} />
```

---

### ⚠️ 주의사항

* 문자열이 아닌 객체는 반드시 `{}`로 감싸서 전달해야 한다.
* 객체 내부 값은 `객체명.속성` 형태로 접근한다.

---

### ✅ 정리

* 여러 데이터를 전달할 때는 객체로 묶는 것이 효율적
* props로 객체 전달 가능
* 자식 컴포넌트에서 필요한 값만 꺼내 사용



## 📌 실습 (Props 객체 전달 응용)

### 🔹 Step 6. 객체 형태로 props 전달

기존에는 `src`, `alt`를 각각 전달했지만,
이번에는 하나의 객체로 묶어서 전달한다.

---

#### ✅ 기존 방식 (개별 전달)

```jsx
<ChildComp 
  src={reactLogo} 
  alt="React" 
  width={100} 
  height={100} 
/>
```

---

#### ✅ 변경된 방식 (객체 전달)

```jsx
const imageInfo = {
  src: reactLogo,
  alt: "React"
};

<ChildComp 
  imageInfo={imageInfo} 
  width={100} 
  height={100} 
/>
```

---

#### 🔹 자식 컴포넌트

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

### 🔹 Step 7. 컴포넌트 재사용

같은 컴포넌트를 다른 데이터로 재사용할 수 있다.

```jsx
const viteImage = {
  src: "/public/vite.svg",
  alt: "vite"
};

<ChildComp 
  imageInfo={viteImage} 
  width={200} 
  height={200} 
/>
```

---

### 🔹 실습 결과

* 동일한 `ChildComp`를 다양한 데이터로 재사용 가능
* props를 통해 유연한 UI 구성 가능
* 객체 전달 방식으로 코드 구조 개선

---

### ✅ 정리

* 여러 속성은 객체로 묶어 전달하는 것이 효율적
* 컴포넌트 재사용성이 증가함
* props를 활용하면 다양한 UI를 쉽게 구현 가능





## 📌 Props의 기본값 지정

props는 부모 컴포넌트로부터 전달되지만,
값이 전달되지 않았을 경우 기본값을 설정할 수 있다.

---

### 🔹 기본값 설정 방법

함수 컴포넌트에서 매개변수 기본값을 사용하여 설정한다.

```jsx id="p2v5mj"
function ChildComp({ imageInfo, width, height = 300 }) {
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

* `height = 300` → 기본값 설정
* 부모에서 값을 전달하지 않으면 300이 사용됨

---

### 🔹 동작 방식

* props 값이 **없거나(undefined)** 전달되면 기본값 사용
* props 값이 **null 또는 0**이면 기본값이 적용되지 않음

---

### 🔹 사용 예시

```jsx id="d9mx1w"
const imageInfo = {
  src: "/public/vite.svg",
  alt: "vite"
};

<ChildComp imageInfo={imageInfo} width={200} />
```

* `height`를 전달하지 않았기 때문에 → 기본값 300 적용

---

### 🔹 실습 포인트

* `ChildComp`의 `height`에 기본값 300 설정
* `ParentComp`에서는 `imageInfo` 객체만 전달

---

### ✅ 정리

* props가 없을 경우 기본값 설정 가능
* 함수 매개변수에서 기본값 지정
* undefined일 때만 기본값 적용






JSX Spread 문법으로 Props 전달하기
📌 개념
여러 개의 props를 한 번에 전달할 때 JavaScript의 spread 문법 (...) 을 사용한다.
객체에 담긴 props를 펼쳐서 전달하는 방식이다.
const props = { name: "Kim", age: 20 };

<User {...props} />

👉 위 코드는 아래와 동일하다.

<User name="Kim" age={20} />
📌 사용 목적
1. Props Forwarding (props 전달 유지)
부모 컴포넌트에서 받은 props를 중간 컴포넌트를 거쳐 자식에게 그대로 전달할 때 유용하다.
function Parent(props) {
  return <Child {...props} />;
}
2. HTML 속성 확장
버튼, input 등에서 여러 속성을 한 번에 전달할 때 사용
const buttonProps = {
  onClick: handleClick,
  type: "button",
  disabled: false
};

<button {...buttonProps}>클릭</button>
3. Props가 많을 때
전달해야 할 props가 많으면 코드가 길어지므로 spread 문법으로 가독성을 높일 수 있다.
<Component {...props} />
⚠️ 주의사항
props를 무분별하게 spread하면 가독성이 떨어질 수 있음
어떤 값이 전달되는지 명확하지 않을 수 있음
필요한 경우에만 사용하는 것이 좋다
✅ 핵심 정리
...props → 객체를 펼쳐서 전달
코드 간결화 및 재사용성 증가
props forwarding에 매우 유용
남용 시 가독성 저하 주의



🧪 실습 - JSX Spread 문법 활용하기

📌 실습 목표
SpreadComp와 NameCard 컴포넌트를 생성한다.
객체 데이터를 spread 문법으로 props 전달하는 방법을 익힌다.

📌 Step 1. SpreadComp 컴포넌트 작성
userData 객체를 생성하고, 이를 NameCard 컴포넌트에 전달한다.
spread 문법을 사용하여 props를 한 번에 전달한다.



import NameCard from "./NameCard";

export default function SpreadComp() {
  const userData = {
    id: 1,
    name: "Tom",
    age: 25,
    job: "developer",
    location: "Seoul"
  };

  return (
    <NameCard {...userData} />
  );
}



📌 Spread 문법을 사용하지 않는 경우
각각의 props를 직접 전달해야 한다.

<NameCard 
  id={userData.id}
  name={userData.name}
  age={userData.age}
  job={userData.job}
  location={userData.location}
/>



📌 핵심 포인트
...userData → 객체의 모든 속성을 props로 전달
코드가 훨씬 간결해짐
props 개수가 많을수록 효율적
✅ 정리
spread 문법을 사용하면 반복적인 props 작성 없이 한 번에 전달 가능
유지보수성과 가독성이 향상됨
실제 프로젝트에서 매우 자주 사용되는 방식







⚠️ JSX Spread 문법 사용 시 주의사항
spread 문법은 매우 편리하지만, 무분별하게 사용하면 문제가 발생할 수 있다.
상황에 맞게 적절히 사용하는 것이 중요하다.
📌 주요 문제점
1. 가독성 저하 (Magic Props)
어떤 props가 전달되는지 한눈에 파악하기 어렵다.
코드만 보고 컴포넌트의 입력값을 이해하기 힘들어진다.


예시
<Profile {...userData} />
👉 어떤 값이 전달되는지 명확하지 않음



2. 불필요한 데이터 전달
객체 안의 모든 데이터가 전달되기 때문에
자식 컴포넌트에 필요 없는 값까지 전달될 수 있음
이는 성능 저하 또는 예상하지 못한 버그를 유발할 수 있다.


4. 우선순위 문제
spread 이후에 작성된 props가 기존 값을 덮어쓴다
<Profile {...userData} age={30} />
👉 userData.age 값이 있어도 최종 값은 age={30}이 적용됨



📌 정리
spread 문법은 편리하지만 신중하게 사용해야 한다
필요한 props만 명시적으로 전달하는 것도 중요
특히 협업 시 가독성을 고려해야 한다
✅ 핵심 요약
✔️ 코드 간결화 가능
❗ 가독성 저하 가능
❗ 불필요한 데이터 전달 위험
❗ props 덮어쓰기 주의



-----------------------------------------------------------------------------------------------------------------------------------------

4월8일
## 2.2 조건부 렌더링

React에서는 상황(조건)에 따라 다른 화면을 보여줄 수 있다.

이를 조건부 렌더링이라고 하며,
자바스크립트의 if문이나 삼항 연산자를 사용해서 구현한다.



예를 들어,
- 로그인 상태 → 환영 메시지 출력
- 비로그인 상태 → 로그인 안내 출력

처럼 조건에 따라 다른 UI를 보여줄 수 있다.

## 실습 - Spread 문법 사용

### Step 4
props를 spread(...) 형태로 전달하고,
컴포넌트에서는 각각의 변수로 받아서 사용할 수 있다.

예시:
<NameCard {...userData} />

→ userData 객체의 값들이 각각 props로 전달됨

---

### Step 5
spread 방식과 일반 props 전달 방식을 함께 사용할 수 있다.

예시:
<NameCard id={1} name="홍길동" {...userData} />

→ 일부는 직접 전달하고, 나머지는 spread로 전달 가능

---

### 정리
- spread(...) : 객체 데이터를 한 번에 전달
- 코드가 더 깔끔해지고 가독성이 좋아짐






## 2.2 조건부 렌더링

React에서는 조건에 따라 다른 화면을 출력할 수 있으며,
이를 조건부 렌더링이라고 한다.

자바스크립트의 if문이나 삼항 연산자를 사용하여
조건에 따라 JSX를 다르게 렌더링할 수 있다.

---

### 학습 내용

- 조건에 따라 다른 JSX를 반환하는 방법
- JSX를 조건에 따라 포함하거나 제외하는 방법
- React에서 자주 사용하는 조건문(if, 삼항 연산자 등)

---

### 예시

```jsx
function App({ isLogin }) {
  return (
    <>
      {isLogin ? <h1>환영합니다</h1> : <h1>로그인 해주세요</h1>}
    </>
  );
}



## 2.2.1 조건부로 JSX 반환하기 [실습]

### 실습 개요
조건부 렌더링을 연습하기 위해
“여행 짐 챙기기” 앱을 만든다.

여행 전에 짐을 잘 챙겼는지 확인할 수 있도록
리스트 형태로 출력하는 앱이다.

이 앱은 PackingList 컴포넌트가
Item 컴포넌트를 호출하여 구성된다.

---

### 실습 내용

- PackingList 컴포넌트를 생성하고 Item 컴포넌트를 호출한다.
- Item 컴포넌트는 name을 props로 받아 <li> 태그로 출력한다.
- App 컴포넌트에서 전체를 렌더링한다.
- 조건부 렌더링을 사용하여 체크 여부를 표시한다.

---

### 구조 예시

App → PackingList → Item

---

### 핵심 정리

- props로 데이터 전달
- 리스트 형태로 JSX 출력
- 조건에 따라 다른 UI 표시 (조건부 렌더링)



## 실습 - 여행 짐 리스트 만들기

### Step 1
PackingList 컴포넌트를 생성하고
간단한 리스트를 작성한다.

아직 기능 없이 단순히 <ul>, <li>를 사용해
짐 목록을 출력한다.

---

### Step 2
App.js(또는 App.jsx)에서
PackingList 컴포넌트를 호출하여 화면에 출력한다.

---

### Step 3
Items 컴포넌트를 생성하고,
props로 name을 받아 리스트 형태(<li>)로 반환한다.

---

### Step 4
PackingList 컴포넌트에서
Items 컴포넌트를 호출하고 name을 props로 전달한다.

---

### Step 5
Items 컴포넌트에서 if문을 사용하여
조건부 렌더링이 가능하도록 수정한다.

예: 짐을 챙겼으면 표시 추가

---

### Step 6
PackingList 컴포넌트에서
isPacked 값을 props로 전달하도록 수정한다.

---

### 전체 흐름

App → PackingList → Items

---

### 핵심 정리

- 컴포넌트 분리 (PackingList, Items)
- props로 데이터 전달
- 리스트 출력 (ul, li)
- 조건부 렌더링 적용 (if문)


📦 React 조건부 렌더링 (Conditional Rendering)

isPacked 값에 따라 리스트 아이템을 다르게 표시하는 간단한 예제입니다.

🧩 기능 설명
isPacked가 true이면
→ 체크 표시(✅) 또는 취소선 적용
false이면
→ 기본 텍스트만 출력
💻 코드 예제
1. 간단한 조건 처리
export default function Item({ name, isPacked }) {
  return <li>{name} {isPacked ? '✅' : ''}</li>;
}

👉 isPacked가 true일 때만 체크 표시가 추가됩니다.

2. JSX를 활용한 조건부 렌더링
export default function Item({ name, isPacked }) {
  return (
    <li>
      {isPacked ? (
        <del>
          {name} ✅
        </del>
      ) : (
        name
      )}
    </li>
  );
}

👉 isPacked가 true이면:

텍스트에 취소선(<del>) 적용
체크 표시 추가

👉 false이면:

이름만 출력
⚠️ 참고
삼항 연산자(condition ? A : B)를 사용하면 간단한 조건 처리가 가능합니다.
JSX에서 소괄호 ()는 필수는 아니지만 가독성을 위해 사용하는 것이 좋습니다.
📌 정리
조건에 따라 UI를 다르게 렌더링할 수 있다.
JSX 내부에서도 조건문 사용이 가능하다.
코드가 길어질수록 가독성을 고려해서 작성하는 것이 중요하다.


🧪 실습: React 조건부 렌더링

React에서 isPacked 값에 따라 UI를 다르게 출력하는 방법을 연습합니다.

💡 이모지 사용
Windows 기준: Win + . 를 눌러 이모지 입력 가능
💻 코드 예제
1️⃣ Step 7 - 간단한 조건 표시
// Items.jsx
export default function Items({ name, isPacked }) {
  return <li>{name} {isPacked ? '✅' : ''}</li>;
}
✔ 설명
isPacked가 true → ✅ 표시
false → 아무것도 표시하지 않음
삼항 연산자를 사용한 가장 기본적인 형태
2️⃣ Step 8 - JSX 조건부 렌더링
// Items.jsx
export default function Items({ name, isPacked }) {
  return (
    <li>
      {isPacked ? (
        <del>
          {name} ✅
        </del>
      ) : (
        name
      )}
    </li>
  );
}
✔ 설명
isPacked === true
<del> 태그로 취소선 적용
체크 표시 추가
isPacked === false
이름만 출력
⚠️ 참고 사항
JSX에서 소괄호 ()는 필수가 아님
하지만 코드가 길어질 경우 가독성을 위해 사용하는 것이 좋음
📌 핵심 정리
삼항 연산자로 조건부 렌더링 가능
JSX 안에서 태그까지 조건적으로 출력 가능
UI 상태에 따라 다양한 표현이 가능


♻️ 중복된 코드 제거하기

조건부 렌더링을 사용할 때, 불필요하게 반복되는 코드를 줄이는 방법을 학습합니다.

❓ 문제 상황

Step 8 코드에서 아래 부분을 보면:

{isPacked ? (
  <del>{name} ✅</del>
) : (
  name
)}

👉 name이 양쪽에서 반복되고 있음

💡 왜 중괄호 {}가 다를까?
<del>{name} ✅</del> → JSX 내부이므로 {} 필요
name → 이미 JSX 표현식 안이므로 {} 없이 사용 가능
✨ 개선 아이디어

중복을 줄이기 위해 구조를 단순화할 수 있음

<li>
  {isPacked ? <del>{name} ✅</del> : name}
</li>

또는 더 나아가면:

<li>
  {isPacked && <del>{name} ✅</del>}
  {!isPacked && name}
</li>
⚠️ 주의
삼항 연산자는 간단한 조건에 적합
조건이 많아지면 코드가 복잡해짐
🧠 실무 팁
조건문이 많아지면:
👉 컴포넌트 분리 추천
👉 가독성 우선으로 작성

예시:

function PackedItem({ name }) {
  return <del>{name} ✅</del>;
}
📌 핵심 정리
같은 값(name)이 반복되면 구조를 의심하기
JSX 안/밖에 따라 {} 사용 방식이 다름
복잡해지면 컴포넌트로 분리하는 것이 좋음



🔗 논리 연산자 AND (&&) 사용하기

React에서 조건부 렌더링을 할 때, 삼항 연산자 외에도 && 연산자를 사용할 수 있습니다.

💡 개념 설명
&&는 왼쪽 조건이 true일 때만 오른쪽을 실행
조건이 false이면 아무것도 렌더링되지 않음
💻 코드 예제
return (
  <li>
    {name} {isPacked && '✅'}
  </li>
);
✔ 동작 방식
isPacked === true
→ ✅ 출력됨
isPacked === false
→ 아무것도 출력되지 않음
⚙️ 동작 원리 (JavaScript)
true && '✅'   // → '✅'
false && '✅'  // → false

👉 React에서는 false, null, undefined를
렌더링하지 않음 (빈 공간 처리)

⚠️ 참고
간단한 조건 → && 사용 👍
복잡한 조건 → 삼항 연산자 사용 👍
🧠 핵심 정리
&&는 "조건이 맞을 때만 보여주기"에 최적
false일 경우 아무것도 렌더링되지 않음
짧고 간단한 UI 조건에 유용



🧠 변수에 조건부로 JSX 할당하기

조건부 렌더링이 복잡해질 경우, JSX를 변수에 담아서 처리하면 코드가 더 깔끔해집니다.

💡 개념 설명
if문 + 변수(let)를 사용해서 조건에 따라 값을 변경
마지막에 JSX에서 해당 변수를 출력
💻 코드 예제
export default function Item({ name, isPacked }) {
  let itemContent = name;

  if (isPacked) {
    itemContent = name + ' ✅';
  }

  return (
    <li>
      {itemContent}
    </li>
  );
}
✔ 동작 방식
기본값으로 name을 변수에 저장
isPacked === true이면
→ itemContent를 "name + ✅"로 변경
JSX에서 {itemContent} 출력
✨ 왜 사용하는가?
삼항 연산자나 &&가 복잡해질 때 유용
조건이 많아질수록 가독성이 좋아짐
일반 JavaScript 로직처럼 작성 가능
⚠️ 참고
let을 사용하면 변수 값을 재할당 가능
JSX 안에서는 {}를 사용해 변수 출력
🧠 핵심 정리
복잡한 조건 → 변수 + if문 사용 👍
JSX는 최대한 깔끔하게 유지
로직과 UI를 분리하면 가독성이 좋아짐


🧪 실습: 변수에 JSX를 할당한 후 렌더링하기

조건에 따라 JSX를 변수에 담고, 그 값을 렌더링하는 방법을 연습합니다.

💻 코드 예제
export default function Items({ name, isPacked }) {
  let itemContent = name;

  if (isPacked) {
    itemContent = <del>{name + ' ✅'}</del>;
  }

  return (
    <li>
      {itemContent}
    </li>
  );
}
✔ 동작 방식
기본값: itemContent = name
isPacked === true이면:
<del> 태그 적용 (취소선)
체크 표시(✅) 추가
JSX에서 {itemContent}를 렌더링
💡 핵심 포인트
JSX도 변수에 저장할 수 있음
if문을 사용하면 복잡한 조건을 깔끔하게 처리 가능
UI 코드(return)를 단순하게 유지할 수 있음
📌 정리
조건 로직 → JavaScript (if)
화면 출력 → JSX (return)
역할을 분리하면 코드가 더 읽기 쉬워짐




📋 리스트 렌더링 (List Rendering)

React에서는 여러 개의 데이터를 같은 형태로 반복해서 출력해야 하는 경우가 많습니다.

이럴 때 JavaScript의 배열 메서드를 사용하여 효율적으로 렌더링할 수 있습니다.

💡 개념 설명
배열 데이터를 기반으로 UI를 반복 생성
map() → 데이터를 JSX로 변환
filter() → 조건에 맞는 데이터만 선택
🧩 언제 사용하는가?
리스트 출력 (예: 상품 목록, 할 일 목록)
같은 구조의 컴포넌트를 여러 개 생성할 때
📚 학습 내용
✔ 1. map()을 사용한 리스트 렌더링
배열의 각 요소를 JSX로 변환
React에서 가장 기본적인 리스트 출력 방식
✔ 2. filter()를 사용한 조건부 렌더링
특정 조건에 맞는 데이터만 필터링
필요한 데이터만 화면에 출력 가능
✔ 3. key의 필요성
React에서 리스트 렌더링 시 필수 요소
각 요소를 구분하기 위한 고유 값
성능 최적화 및 올바른 UI 업데이트에 중요
🧠 핵심 정리
반복되는 UI → 배열 + map()
조건 필터링 → filter()
리스트 렌더링 시 key는 반드시 필요


📌 배열을 데이터로 렌더링하기

리스트 UI는 보통 데이터(배열)를 기반으로 만들어집니다.

💡 예시 (정적인 리스트)
<ul>
  <li>스파이더맨: 피터 파커</li>
  <li>아이언맨: 토니 스타크</li>
  <li>배트맨: 브루스 웨인</li>
  <li>슈퍼맨: 클라크 켄트</li>
  <li>헐크: 로버트 브루스 배너</li>
</ul>
❗ 문제점
현재 리스트는 하드코딩된 HTML
데이터가 바뀌면 직접 수정해야 함
재사용성과 유지보수성이 떨어짐
✅ 해결 방법

👉 데이터를 JavaScript 배열로 관리

const heroes = [
  { name: "스파이더맨", realName: "피터 파커" },
  { name: "아이언맨", realName: "토니 스타크" },
  { name: "배트맨", realName: "브루스 웨인" },
  { name: "슈퍼맨", realName: "클라크 켄트" },
  { name: "헐크", realName: "로버트 브루스 배너" }
];
🚀 핵심 아이디어
UI는 데이터로부터 생성되어야 한다
배열을 사용하면:
map() → 리스트 렌더링
filter() → 조건 필터링
🧠 핵심 정리
리스트의 본질은 데이터
정적인 HTML → 동적인 데이터 기반으로 변경
배열 + map()을 사용하면 효율적으로 렌더링 가능



🧪 실습: map()으로 리스트 렌더링하기

배열 데이터를 map() 함수를 사용하여 리스트 형태로 출력합니다.

💻 코드 예제
const heroes = [
  '스파이더맨: 피터 파커',
  '아이언맨: 토니 스타크',
  '배트맨: 브루스 웨인',
  '슈퍼맨: 클라크 켄트',
  '헐크: 로버트 브루스 배너'
];

export default function MovieHeroes() {
  const listHeroes = heroes.map(hero => <li>{hero}</li>);

  return (
    <section>
      <h1>영화 속 영웅들</h1>
      <ul>
        {listHeroes}
      </ul>
    </section>
  );
}
✔ 동작 방식
heroes 배열에 데이터 저장
map()을 사용하여 각 요소를 <li>로 변환
변환된 결과를 listHeroes 변수에 저장
JSX에서 {listHeroes}로 출력
💡 핵심 포인트
map()은 배열을 JSX 리스트로 변환하는 핵심 함수
반복되는 UI를 간단하게 생성 가능
데이터만 바꾸면 UI도 자동으로 변경됨
⚠️ 참고
실제 React에서는 각 <li>에 key가 필요함 (다음 단계에서 다룸)
🧠 정리
배열 → map() → JSX 리스트
반복 UI는 반드시 데이터 기반으로 작성
React에서 가장 많이 사용하는 패턴













