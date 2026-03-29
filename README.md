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

React 프레임워크를 사용하지 않고 직접 React 앱을 개발하는 방법.
기존 프로젝트 일부에만 React를 연결하는 방법.
새로운 React 앱을 개발하는 경우의 설치 방법.
프로젝트를 생성해도 git은 직접해야 합니다.

-[구성요소 전]

부품을 사용할 수 있나요?
어떤 기능을 수행합니까?
유니버설이 포함되어 있습니까?
구성 요소 이름은 무엇으로 해야 할까요?
카페인에 대해 뭐라구요?
나의 첫 번째 구성 요소 구성 요소 만들기


















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





