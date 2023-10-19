---
description: TDD와 테스트 도구
---

# 5⃣ Test

## TDD

* 인터페이스와 스펙(기대값)이 있는, 자동화된 테스트를 위한 코드를 먼저 작성
* TDD cycle

1. red -> 실패
2. green -> 통과
3. refactor -> 수정

* 동작을 바꾸지 않고 설계를 바꾼다 = 스펙을 바꾸지 않고 코드를 바꾼다
* 작은 단계, 코드에서 피드백, 중복 제거
* ?? 의도를 찾아서 드러내기

> Jest를 이용한 TDD 예제 :  [https://github.com/ahastudio/til/blob/main/jest/20201204-simple-tdd-example.md](https://github.com/ahastudio/til/blob/main/jest/20201204-simple-tdd-example.md)

## Jest

페이스북에서 만든 테스팅 도구 [https://jestjs.io/](https://jestjs.io/)

Jest에서 TypeScript 사용하도록 jest.config.js 파일 작성

```
// jest.config.js
module.exports = {
	testEnvironment: 'jsdom',
	setupFilesAfterEnv: [
		'@testing-library/jest-dom/extend-expect',
	],
	transform: {
		'^.+\\.(t|j)sx?$': ['@swc/jest', {
			jsc: {
				parser: {
					syntax: 'typescript',	
					jsx: true,
					decorators: true,
				},
				transform: {	
					react: {
						runtime: 'automatic',
					},
				},
			},
		}],
	},
};
```

*   테스트 케이스 정의

    * test 함수에 expect에 스펙을 작성하여 개별 테스트를 나열한다

    ```jsx
    test('add', () => {
    	expect(add(1, 2)).toBe(3);
    	expect(add(1, 3)).toBe(4);
    });
    ```

    * ?? BDD 스타일 : 주체(테스트 대상) - 행위 중심으로 테스트 조직화

    ```jsx
    describe('add', () => {
    	it('returns sum of two numbers', () => {
    		expect(add(1, 2)).toBe(3);
    	});
    });
    ```

> given-when-then 템플릿 :  [https://github.com/ahastudio/til/blob/main/blog/2018/12-08-given-when-then.md](https://github.com/ahastudio/til/blob/main/blog/2018/12-08-given-when-then.md)
>
> ? RSpec

## React Testing Library

리액트 테스트를 쉽게하기 위함 [https://github.com/testing-library/react-testing-library](https://github.com/testing-library/react-testing-library)

* 사용자 입장에 가깝게 테스트, 테스트 시나리오 작성이 쉬움
* given when then 을 나열할 때는 초기화 주의

```
jest.clearAllMocks
```

* ? 외부의존성이 큰 코드
* &#x20;

