# 2⃣ JSX

### JSX 특징

* JSX는 XML같은 ECMAScript(JavaScript)의 **문법확장**이다.
* JSX를 반드시 사용할 필요는 없다
* JSX는 React를 만들면서 나왔지만, 다른 프레임워크에서도 사용 가능하다.
* JavaScript로 변환하며, JavaScript와 1:1 매칭된다
* JSX는 html이 아니다
* [facebook의 JSX 소개](https://facebook.github.io/jsx/)
* [React 공식문서의 JSX 소개](https://ko.reactjs.org/docs/introducing-jsx.html)
* [Babel, JSX, 그리고 빌드 과정들](https://ko.reactjs.org/docs/faq-build.html)
* [JSX 이해하기](https://ko.reactjs.org/docs/jsx-in-depth.html)

### JSX 사용해보기

* 온라인 변환기 : [https://babeljs.io](https://babeljs.io/)/repl
  * 좌측에서 체크하거나 하단 add-plugin 에서 react-jsx 검색 후 @babel/plugin-transform-react-jsx를 추가하여 사용 가능

#### Example 1

```jsx
// JSX

<p>Hello, world!</p>
```

```
// JavaScript
React.createElement("p", null, "Hello, world!");

```

* react가 아닌 다른 곳에 JSX를 사용하고 싶다면 상단에 /\* @jsx Bla \*/ 주석 추가 할 경우 **React.createElement 대신** Bla 사용

#### Example 2

```jsx
function Greeting({ name }) {
  return (
     <p> Hello, {name}!</p>
  );
}
<Greeting name="world" age="13" age2={13} age2={{"key":"value"}} />
```

```
function Greeting({
  name
}) {
  return /*#__PURE__*/React.createElement("p", null, " Hello, ", name, "!");
}
/*#__PURE__*/React.createElement(Greeting, {
  name: "world",
  age: "13",
  age2: 13,
  age2: {
    "key": "value"
  }
});
```

* javascript의 object는 key value 쌍의 모음

#### Example 3

```jsx
<Button type="submit">Send</Button>; //함수
<button type="submit" onClick= {() => console.log('Clicked')}>Send</button> //기본 태그
```

```
React.createElement(Button, {
  type: "submit"
}, "Send"); //함수
React.createElement("button", {
  type: "submit",
  onClick: () => console.log('Clicked')
}, "Send"); //기본 태그
```

#### Example 4

```jsx
// React.Fragment 나 div 를 사용해서 구분지어 줄 수 있음(; 와 같은 역할)
<React.Fragment>
    <p>Hello, world!</p>
    <Button type="submit">Send</Button>
</ React.Fragment>
```

```javascript
/*rumtime automatic*/
import { jsx as _jsx } from "react/jsx-runtime";
import { jsxs as _jsxs } from "react/jsx-runtime";
/*#__PURE__*/_jsxs(React.Fragment, {
  children: [/*#__PURE__*/_jsx("p", {
    children: "Hello, world!"
  }), /*#__PURE__*/_jsx(Button, {
    type: "submit",
    children: "Send"
  })]
});
```

* 좌측 optiotion 에서 react runtime을 automatic으로 변경해서 사용하기도 함

#### Example 5

```jsx
<div>
	<p>Count: 
		{' '}
		{count}
		!
	</p>
	<button type="button" onClick={() => setCount(count + 1)}>Increase</button>
</div>
```

```javascript
```

### React Element

* JSX 왜 사용할까&#x20;
  * 사용하기 쉬움 (syntex sugar)
* createElement
  * DOM 트리를 구성하는 것과 비슷하게, react 트리(노드)를 갱신하는데 사용함

```markup
const element = document.createElement('div');
element.classList = ['test', 'wow'].join(' ');
element.appendChild(document.createElement('p'));
```

* 참고고
  * [JSX 없이 사용하는 React](https://ko.reactjs.org/docs/react-without-jsx.html)
  * [createElement](https://beta.reactjs.org/reference/react/createElement)
* JSX : \_jsx 함수 제공
* Preact : h 함수 제공
  * [\_jsx](https://reactjs.org/blog/2020/09/22/introducing-the-new-jsx-transform.html)
  * [h()](https://preactjs.com/guide/v10/api-reference/#h--createelement)

#### VDOM (Virtual DOM)&#x20;

```markup
document.querySelector('.css-1').textContent = 'Hello';
document.querySelector('.css-1').innerHTML = '<ul><li>1</li></ul>';
```

* VDOM : 다른 컴포넌트에 영향을 주지 않고 재조정하여 동기화하는 것

```
import ReactDOM from 'react-dom/client';
```

* [VDOM (Virtual DOM)](https://ko.reactjs.org/docs/faq-internals.html)
* [재조정 (Reconciliation)](https://ko.reactjs.org/docs/reconciliation.html)
* React Developer Tools : 크롬 확장팩, 컴포넌트 관계, strict mode

```typescript
소스코드 -> App.tsx 수정후 chrome 개발자 모드에서 확인 가능
```

*   [react devtools extensions](https://github.com/facebook/react/tree/main/packages/react-devtools-extensions)

    → [Strict Mode](https://ko.reactjs.org/docs/strict-mode.html)를 쓰지 않으면 경고함.
* 선언적 API, 선언적 UI >> 찾아보기
* 적절한 빠르기로 코드를 생성하고, 적절하게 유지보수를 가능하게 함 > 최적화
* 변경사항 비교를 위해 key를 잡아줌
* 변경사항을 비교하는 방법은 상황에 따라 효율성을 고민해야함
