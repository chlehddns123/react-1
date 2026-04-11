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













