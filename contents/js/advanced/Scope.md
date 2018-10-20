# Javascript, Scope?
간단하게 Scope란?, JavaScript 내에서 변수나 함수, 혹은 객체에 대한 범위를 지정해주기 위해 사용됩니다.
JavaScript(ES6)는 Function level과 Block Level, Lexical Scope 규칙을 따릅니다.

이러한 스코프 영역에 알고가기 위해서는 `변수`에 대해서 읽어보고 오시기 바랍니다.

## Scope
자바스크립트에서 스코프란 어떤 변수들에 접근할 수 있는지를 정의합니다. 스코프엔 두 가지 종류가 있는데요, 전역 스코프(global scope)와 지역 스코프(local scope)가 있습니다.

#### Scope Level
자바스크립트는 전통적으로 함수 레벨 스코프를 지원해왔고, 얼마 전까지만 해도 블록 레벨 스코프는 지원하지 않았다. 하지만 가장 최신 명세인 ES6(ECMAScript 6)부터 블록 레벨 스코프를 지원하기 시작했습니다.

## Function Level Scope
자바스크립트에서 var키워드로 선언된 변수나, 함수 선언식으로 만들어진 함수는 `함수 레벨 스코프`를 갖는다. 즉, `함수 내부 전체에서 유효한 식별자`가 된다.

아래 코드는 아무런 문제없이 blue를 출력한다.
```js
function printScope() {
	if (true) {
		var color = 'blue';
		const blockColor = 'red'; // const, let
	}
	console.log(color); // blue
	console.log(blockColor); // blockColor is not defined
}
printScope();
```

만약, color가 블록 레벨 스코프였다면, color는 if문이 끝날 때 파괴되고 console.log에서 정의되지 않았다는 에러메세지를 보여줍니다.(blockColor와 같이 말입니다.)
하지만, `var`는 함수 레벨 스코프이기 때문에 `printScope` 함수 내부 어디에서든 에러 발생 없이 참조할 수 있다.

## 블록 레벨 스코프
ES6의 let, const키워드는 블록 레벨 스코프 변수를 만들어 준다

## - Hoisting
호이스팅은 JavaScript에서 실행 콘텍스트(특히 생성 및 실행 단계)가 어떻게 동작하는가에 대한 일반적인 생각으로 여겨집니다. 이러한 호이스팅의 이해는 오해로 이어질 수 있습니다.
예를 들어, 호이스팅을 변수 및 함수 선언이 물리적으로 작성한 코드의 상단으로 옮겨지는 것으로 가르치지만, 실제로는 그렇지 않습니다.

`변수 및 함수 선언은 컴파일 단계에서 메모리에 저장`되지만, 코드에서 입력한 위치와 정확히 일치한 곳에 있습니다.

```js
function catName(name) {
  console.log("My cat's name is " + name);
}

catName("Tigger");
```

```js
catName("Chloe");

function catName(name) {
  console.log("My cat's name is " + name);
}
```

## Outro
기본적으로 자바스크립트는 ECMAScript 언어 명세를 따르고 있습니다.
특히, Scope에 관련된 내용을 참고하고 싶으신 분들은 [ECMA - 명세 8장](https://www.ecma-international.org/ecma-262/8.0/index.html#sec-executable-code-and-execution-contexts)의 실행코드와 실행컨텍스트 부분에서 동작 방식을 확인할 수 있습니다.

## References
- [ECMA - Executable Code and Execution Contexts](https://www.ecma-international.org/ecma-262/8.0/index.html#sec-executable-code-and-execution-contexts)
- [MDN - Hoistring](https://developer.mozilla.org/ko/docs/Glossary/Hoisting)
- [MDN - 자바스크립트의 자료형](https://developer.mozilla.org/ko/docs/Web/JavaScript/Data_structures)
- [Medium - 스코프와 클로저란 무엇인가?](https://medium.com/@khwsc1/%EB%B2%88%EC%97%AD-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%8A%A4%EC%BD%94%ED%94%84%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%80-javascript-scope-and-closures-8d402c976d19)
- [TOAST - 자바스크립트의 스코프와 클로저](https://meetup.toast.com/posts/86)
- [Zell Liew - 자바스크립트 스코프와 클로저](http://dmitrysoshnikov.com/ecmascript/chapter-4-scope-chain/)
