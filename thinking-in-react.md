# 3⃣ Thinking in React



React로 웹페이지 만드는 방법

React로 생각하기 - 컴포넌트

Thinking in React : [https://react.dev/learn/thinking-in-react](https://react.dev/learn/thinking-in-react)

1. 컴포넌트의 계층구조 (컴포넌트 트리)
2. React의 정적인 버전 만들기

### 내용

#### 데이터 준비

*   Mockup 준비 &#x20;

    디자인 예시로, 기능이 크게 변경되지 않음
*   JSON 데이터를 사용함

    REST API : GET, POST, PUT/PATCH, DELETE (CRUD)

    GraphQL : Query(Read), Mutation(Command: Create, Update, Delete), Subscription(Event)
* React는 선언형(HTML과 유사한 모양의 DSL을 사용)으로 UI를 구성, 선언형으로 구성할 경우 데이터 변화를 반영
* JSON 개요 : [https://www.json.org/json-ko.html](https://www.json.org/json-ko.html)

#### 컴포넌트 쪼개기

1. 일단 코드 작성
2. 자를 수 있는 부분 함수 추출
3. 애매한 경우 분리했다가, inline로 합치기도 함

SRP -> 단일 책임 원칙으로, 모든 클래스는 하나의 책임만 가진다고함

마크업,CSS, 자바스크립트를 컴포넌트로 결합하여 재사용

[https://react.dev/learn/your-first-component](https://react.dev/learn/your-first-component)&#x20;

#### Props 사용

* 컴포넌트를 연결할 때 사용
*   객체, 배열, 함수 등 모든 자바스크립트 값 전달 가능

    [https://react.dev/learn/passing-props-to-a-component](https://react.dev/learn/passing-props-to-a-component)

Thinking in React : [https://react.dev/learn/thinking-in-react](https://react.dev/learn/thinking-in-react)

3. 작지만 완벽한, UI 상태의 표현 찾기
4. 위 내용을 어디에 둘지 결정하기
5. inver data flow 넣기

### React의 State

* 변경을 다루기 위한 요소
* Re-rendering : 컴포넌트 상태가 바뀌면 하위 컴포넌트 다시 렌더링
* DRY : 반복은 뺄 것
* SSOT

#### React State 조건

* 변경되지 않는 것 제외
* props로 다루는 것은 제외함
*  계산 가능한 것 제외



