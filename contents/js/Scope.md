# Javascript, Variable and Scope?
기본적으로 자바스크립트는 ECMAScript 언어 명세를 따르고 있다. 이 [명세 8장](https://www.ecma-international.org/ecma-262/8.0/index.html#sec-executable-code-and-execution-contexts)의 실행코드와 실행컨텍스트 부분에서 스코프에 관한 동작 방식을 확인할 수 있습니다.

간단하게 Scope란?, JavaScript 내에서 변수나 함수, 혹은 객체에 대한 범위를 지정해주기 위해 사용됩니다.
JavaScript(ES6)는 Function level과 Block Level, Lexical Scope 규칙을 따릅니다.

## Variables
모든 프로그래밍 언어에는 변수가 존재 합니다. 프로그래밍은 이러한 변수를 기반으로 문제를 해결하는 것입니다.

변수가 갖는 특징은 항상 메모리를 차지한다는 것입니다. 어떠한 물리적 기계가 이해할 수 있는 언어로 구성된 프로그래밍 언어들은 항상 어딘가 물리적 저장소에 저장되어 있어야 합니다.
저장되는 방식과 처리되는 방식에 따라 다양한 명칭이 나누어지지만, 변수는 항상 메로리를 차지합니다.

그렇다면, 자바스크립트에서는 변수를 어떻게 선언하고 사용해야 할까요?

## 선언과 할당
자바스크립트의 변수를 만들기 위해서는 선언과 할당에 대해서 알고 넘어가야 합니다.

#### Declaring
자바스크립트에서는 var 키워드를 이용하여 변수를 선언합니다. es6 이후에는 const와 let으로 변경되었지만, 결국 스코프가 달라진 것 외에는 var와 같습니다.

```js
// es5 이전
var a;
// es6
const b;
let c;
```

- [Babel PlayGround](https://babeljs.io/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=Q&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2&prettier=false&targets=&version=6.26.0&envVersion=)

> 자바스크립트가 가장 많이 사용되는 프론트엔드에서는 Babel이란 라이브러리를 사용합니다. 자바스크립트는 브라우저에서 컴파일되어 사용되는데, 브라우저에 구현된 JavaScript 방식에 따라 달리지기 때문입니다.
이러한 문제들을 인식되면서 자바스크립트 표준(ECMA)정립과 브라우저의 호환성을 위한 움직임이 있었습니다. 브라우저의 호환성을 위해 JavaScript의 상위버전을 하위버전으로 바꾸어주는 transpiler 역할을 담당합니다.

#### Assignment
자바스크립트에서는 `=` operator을 이용하여 할당을 합니다.

```js
a = 5;
b = 'variable';
c = false;
```

> 자바스크립트에서는 not defined와 undefined를 구별해야 합니다. 이 둘은 선언과 할당으로 쉽게 구분할 수 있습니다.
간단히 설명하면, not defined는 변수를 선언하지 않은 것, undefined는 선언은 되었으나 할당되지 않은 상태입니다.

## Type
자바스크립트는 느슨한 타입 (loosely typed) 언어, 혹은 동적 (dynamic) 언어이다. 그 말은, 변수의 타입을 미리 선언할 필요가 없다는 뜻이다.
타입은 프로그램이 처리되는 과정에서 자동으로 파악(추론)될 것이다. 또한 그 말은 같은 변수에 여러 타입의 값을 넣을 수 있다는 뜻이다.(스크립트 언어의 특징)

[MDN - 자바스크립트의 자료형](https://developer.mozilla.org/ko/docs/Web/JavaScript/Data_structures)을 참고하시면 타입 마스터.

> 주의사항 : 비트 마스킹(bit masking) 기법으로 한 숫자 안에 여러 Boolean 값을 저장하는데도 쓸 수 있다. 일반적으로 이런 방법은 나쁜 방법이지만, 자바스크립트에서는 (Boolean 값의 배열이나 Boolean 값들을 이름있는 속성들로 가지는 객체 같은) Boolean 덩어리를 나타낼 다른 방법이 없다. => number와 boolean의 구별 방법에 대한 어려움.

```js
var a = {};
var func = function(b) {
  b = (b.a = 1);
  b.b = 2;
}
func(a);
console.log(a); // ??
```

## Hoisting
호이스팅은 JavaScript에서 실행 콘텍스트(특히 생성 및 실행 단계)가 어떻게 동작하는가에 대한 일반적인 생각으로 여겨집니다. 하지만 호이스팅은 오해로 이어질 수 있습니다. 예를 들어, 호이스팅을 변수 및 함수 선언이 물리적으로 작성한 코드의 상단으로 옮겨지는 것으로 가르치지만, 실제로는 그렇지 않습니다. 변수 및 함수 선언은 컴파일 단계에서 메모리에 저장(Refer)되지만, 코드에서 입력한 위치와 정확히 일치한 곳에 있습니다.

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

## References
- [ECMA - Executable Code and Execution Contexts](https://www.ecma-international.org/ecma-262/8.0/index.html#sec-executable-code-and-execution-contexts)
- [MDN - Hoistring](https://developer.mozilla.org/ko/docs/Glossary/Hoisting)
- [MDN - 자바스크립트의 자료형](https://developer.mozilla.org/ko/docs/Web/JavaScript/Data_structures)
- [TOAST - 자바스크립트의 스코프와 클로저](https://medium.com/@khwsc1/%EB%B2%88%EC%97%AD-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%8A%A4%EC%BD%94%ED%94%84%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%80-javascript-scope-and-closures-8d402c976d19)
- [TOAST - 자바스크립트의 스코프와 클로저](https://meetup.toast.com/posts/86)
- [Value vs. Reference in Javascript](https://codeburst.io/explaining-value-vs-reference-in-javascript-647a975e12a0)
- [Zell Liew - 자바스크립트 스코프와 클로저](http://dmitrysoshnikov.com/ecmascript/chapter-4-scope-chain/)
