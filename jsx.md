# 2⃣ JSX

### JSX 특징

* JSX는 XML같은 ECMAScript(JavaScript)의 "문법확장"이다.
* JSX를 반드시 사용할 필요는 없다
* JSX는 React를 만들면서 나왔지만, 다른 프레임워크에서도 사용 가능하다.
* JavaScript로 변환하며, JavaScript와 1:1 매칭된다

### JSX 사용해보기

* 온라인 변환기 : [https://babeljs.io/](https://babeljs.io/)
  * 좌측에서 체크하거나 하단 add-plugin 에서 react-js 검색 후 추가하여 사용 가능

#### Example 1

```jsx
// JSX

<p>Hello, world!</p>
```

```
// JavaScript


```

* react가 아닌 다른 곳에 JSX를 사용하고 싶다면 상단에 /\* @jsx 다른곳 \*/ 주석 추가 할 경우
  * React.createElement 가 다른곳.createElement 로 변환

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
```

#### Example 3

```jsx
<Button type="submit">Send</Button> //함수
<button type="submit" onClick= {() => console.log('Clicked')}>Send</button> //기본 태그
변환후
```

```
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

* JSX : \_jsx 함수 제공
* Preact : h 함수 제공

#### VDOM (Virtual DOM)&#x20;

```markup
document.querySelector('.css-1').textContent = 'Hello';
document.querySelector('.css-1').innerHTML = '<ul><li>1</li></ul>';
```

* VDOM 과 internals

```
import ReactDOM from 'react-dom/client';
```

38:27
